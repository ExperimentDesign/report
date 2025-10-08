# Capítulo VI: Product Verification & Validation

## 6.1. Testing Suites & Validation

### 6.1.1. Core Entities Unit Tests

Los Core Entities Unit Tests son fundamentales en el desarrollo de software porque aseguran la calidad y el correcto comportamiento de las entidades clave, evitando fallos y haciendo más sencillo el mantenimiento del código. En nuestro caso, se implementaron pruebas unitarias con xUnit y FluentAssertions.

**1.Classroom service Tests**
 Para el agregado Classroom, se validó que el constructor inicialice correctamente Name, Description, TeacherId y deje Resources vacío; que UpdateName y UpdateDescription ignoren valores nulos o vacíos y solo apliquen cambios válidos; y que UpdateTeacherId mantenga el valor cuando es null o cuando la validación externa verifyProfile falla, actualizándolo únicamente cuando dicha validación retorna true.

![Foto](/assets/chapter6/UnitTests/1.png) 

**2.Reservation service Tests**

Esta prueba verifica que al construir una Reservation a partir de un CreateReservationCommand se asignen correctamente todos los campos del dominio: el Title, el rango temporal (Start/End) encapsulado en el value object ReservationDate, y los identificadores AreaId y TeacherId. Con ello aseguramos el contrato entre la capa de aplicación (comandos) y el modelo de dominio: si cambia la firma del comando o la inicialización de los value objects, la prueba falla de inmediato, evitando errores silenciosos al crear reuniones.

![Foto](/assets/chapter6/UnitTests/2.png) 

**3.Meetings service Tests**

Se prueba que en el agregado Meeting, el constructor con primitivas y el basado en CreateMeetingCommand mapeen correctamente todos los campos (Title, Description, Date, StartTime, EndTime) y los value objects AdministratorId y ClassroomId. Además, se prueba que los métodos de actualización mantengan las invariantes del dominio: UpdateTitle/UpdateDescription ignoran nulos o vacíos y solo aplican cambios válidos, UpdateDate y UpdateTime actualizan selectivamente fecha/inicio/fin, y UpdateAdministrator/UpdateClassroom solo cambian cuando el ID es provisto y pasa la validación externa. Con ello se asegura el contrato entre comandos y dominio, y se previenen estados inconsistentes en la programación de reuniones.

![Foto](/assets/chapter6/UnitTests/3.png) 

**4.Teachers Profile service Tests**

Se validó que TeacherProfile mapee correctamente el AdministratorId tanto con el constructor de primitivas como desde CreateTeacherProfileCommand (usando su firma posicional completa). Al centrarnos en el atributo público expuesto por el agregado, estas pruebas verifican el contrato entre la capa de aplicación y el dominio y detectan cambios incompatibles en la firma del comando o en el mapeo del agregado.

![Foto](/assets/chapter6/UnitTests/4.png) 

**5.Accounts service Tests**

Se validó que el constructor de Account asigne Username y PasswordHash y convierta correctamente el rol desde texto a ERoles, lanzando excepción ante valores inválidos; se comprobó el estilo fluido de UpdateUsername y UpdatePasswordHash (devuelven la misma instancia y actualizan los campos); el constructor por defecto deja propiedades nulas y el rol en su valor por defecto; y, vía reflexión, que PasswordHash esté anotado con [JsonIgnore], garantizando que no se serialice accidentalmente. Con ello se cubren reglas clave de creación, actualización y privacidad del agregado de identidad.

![Foto](/assets/chapter6/UnitTests/5.png) 

**6.Meetings controller Tests**

Las dos pruebas unitarias validan el comportamiento del endpoint DELETE /api/v1/meetings/{id} del MeetingsController. En la primera, se “moquea” IMeetingCommandService.Handle(DeleteMeetingCommand) para que complete sin excepciones (flujo feliz) y se verifica que el controlador responda 200 Ok, que el mensaje incluya el id y que el servicio se invoque exactamente una vez. En la segunda, se simula que Handle lanza una ArgumentException (reunión no encontrada) y el test comprueba que el controlador devuelva 404 NotFound con el mensaje correspondiente

![Foto](/assets/chapter6/UnitTests/6.png) 

### 6.1.2. Core Integration Tests

Las Core Integration Tests son clave para verificar que los controladores se relacionen de forma correcta con otros componentes del sistema, como servicios y bases de datos. Al contemplar escenarios de fallo, estas pruebas aseguran que el sistema gestione imprevistos de manera adecuada y devuelva los códigos de estado correspondientes. Con ello se mejora la experiencia de usuario, se simplifica la depuración y se impulsa la construcción de un software confiable y de alta calidad.

**1. Pruebas de integración de ReportRepository con SQLite**

Se ejecutaron pruebas de integración sobre el repositorio ReportRepository usando AppDbContext con SQLite en memoria para validar la persistencia y las consultas reales. Los casos cubren: FindByIdAsync (recupera un reporte insertado), FindAllAsync (devuelve el total de registros) y FindAllByResourceIdAsync (filtra correctamente por el value object ResourceId). Estas pruebas ejercitan mapeos EF, restricciones NOT NULL y LINQ.

![Foto](/assets/chapter6/IntegralTests/1.png) 

**2.Pruebas de integración de Reservations controller**

Este conjunto verifica que los endpoints públicos de reservas respondan correctamente y devuelvan el formato esperado. A través de un HttpClient de pruebas, se llama a GET /api/v1/reservations y GET /api/v1/areas/1/reservations, comprobando que ambos regresen 200 OK y que el cuerpo sea un arreglo JSON.

![Foto](/assets/chapter6/IntegralTests/2.png) 

**3.Pruebas de integración para Meeting controller**

El MeetingsEndpointsTests valida los endpoints de reuniones usando un ApiFactory (WebApplicationFactory) y HttpClient sobre un servidor en memoria. Cubre los flujos principales del controlador: creación de reuniones (respuesta 201/OK y forma del recurso), validaciones de campos requeridos (400), obtención/listado, actualización y eliminación. Para aislar el comportamiento del controlador se inyectan servicios falsos (fakes) de comandos/queries, permitiendo afirmar códigos de estado y el shape del JSON sin depender de la capa de datos.

![Foto](/assets/chapter6/IntegralTests/3.png) 


### 6.1.3. Core Behavior-Driven Development
Las pruebas Behavior-Driven Development (BDD) en EduSpace, realizadas con SpecFlow, permiten validar el comportamiento del sistema desde la perspectiva del usuario final, utilizando lenguaje natural para describir escenarios reales.

<div align="center">
<img src="/assets/chapter6/systemTests/US.png" alt="US" width="500">
</div>

#### Inicio de sesión como profesor

<div align="center">
<img src="/assets/chapter6/systemTests/US06.png" alt="US06" width="500">
</div>

#### Inicio de sesión administrador

<div align="center">
<img src="/assets/chapter6/systemTests/US07.png" alt="US07" width="500">
</div>

#### Registro de información personal del docente

<div align="center">
<img src="/assets/chapter6/systemTests/US08.png" alt="US08" width="500">
</div>

#### Registro de información de acceso del docente

<div align="center">
<img src="/assets/chapter6/systemTests/US09.png" alt="US09" width="500">
</div>

#### Registro de espacios compartidos

<div align="center">
<img src="/assets/chapter6/systemTests/US11.png" alt="US11" width="500">
</div>

### 6.1.4. Core System Tests

Esta sección presenta las pruebas realizadas para validar las funcionalidades principales del sistema, como la accesibilidad, el registro, el inicio de sesión y la gestión de información. Las pruebas se ejecutaron con Selenium para simular la interacción de los usuarios y asegurar que cada flujo funcione correctamente. De esta manera, se garantizó una experiencia fluida, segura y acorde con los requisitos definidos en las historias de usuario.

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US01** | Accesibilidad de la aplicación en diferentes dispositivos | Como visitante, quiero que la aplicación se adapte a diferentes dispositivos para que pueda acceder a la plataforma desde cualquier lugar y en cualquier momento. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_01.png" alt="US01" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US02** | Encontrar información del propósito de la aplicación | Como visitante, quiero saber sobre el propósito de la aplicación para entender qué beneficios y funcionalidades ofrece y decidir si es adecuada para mis necesidades. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_02.png" alt="US02" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US03** | Visualización de imágenes y gráficos relevantes | Como visitante, quiero que las imágenes y gráficos en la landing page sean de alta calidad y relevantes para captar mi interés. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_03.png" alt="US03" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US04** | Tipografía cómoda y agradable estéticamente | Como visitante, quiero que la tipografía en la landing page sea legible y estéticamente agradable para facilitar la lectura y la navegación. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_04.png" alt="US04" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US05** | Registro como Administrador | Como administrador, quiero registrarme en la aplicación web, para hacer uso de las características disponibles. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_05.png" alt="US05" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US06** | Inicio de sesión como profesor | Como profesor, quiero iniciar sesión en la aplicación, para acceder a las funcionalidades específicas para docentes. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_06.png" alt="US06" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US07** | Inicio de sesión administrador | Como administrador, quiero iniciar sesión en la aplicación, para gestionar la administración de ambientes y recursos. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_07.png" alt="US07" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US08** | Registro de información personal del docente | Como administrador, quiero registrar la información personal del docente, para tener una base de datos actualizada. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_08.png" alt="US08" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US09** | Registro de información de acceso del docente | Como administrador, quiero registrar la información de acceso del docente, para que puedan iniciar sesión en la plataforma web. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_09.png" alt="US09" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US10** | Registro de salones | Como administrador, quiero registrar los salones de la institución, para que puedan ser gestionados y asignados en la plataforma web. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_10.png" alt="US10" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US11** | Registro de espacios compartidos | Como administrador, quiero registrar los espacios compartidos, para que puedan ser gestionados en la plataforma web. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_11.png" alt="US11" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US13** | Registro de recursos | Como administrador, quiero registrar los recursos de los salones de clase, para mantener un inventario actualizado y optimizar la gestión de los recursos disponibles. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_13.png" alt="US13" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US14** | Registro de hora y lugar de la reunión | Como administrador, quiero registrar la hora y lugar de la reunión, para asegurar que todos los participantes tengan la información correcta sobre la reunión. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_14.png" alt="US14" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US15** | Registro de invitados de la reunión | Como administrador, quiero invitar a docentes a la reunión, para asegurarme de que los participantes necesarios estén presentes. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_15.png" alt="US15" width="500">
</div>

---

| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US17** | Registrar docente encargado de un salón de clase | Como administrador, deseo registrar qué docente está encargado de cada salón de clase, para asignar responsabilidades y mejorar la gestión de los espacios. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_17.png" alt="US17" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US18** | Actualizar docente encargado de un salón de clase | Como administrador, quiero actualizar qué docente está encargado de cada salón de clase, para reflejar cambios en la asignación de responsabilidades. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_18.png" alt="US18" width="500">
</div>

---


| **ID** | **Título** | **Descripción** |
|:------:|:-----------|:----------------|
| **US20** | Visualización de espacios compartidos | Como docente, quiero visualizar los espacios disponibles para poder planificar actividades, reuniones o clases adicionales. |

<div align="center">
<img src="/assets/chapter6/systemTests/us_20.png" alt="US20" width="500">
</div>

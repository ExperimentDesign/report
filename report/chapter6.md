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

### 6.1.4. Core System Tests

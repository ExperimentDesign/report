# Capítulo VII: DevOps Practices

## 7.1. Continuous Integration

### 7.1.1. Tools and Practices
En el ámbito del desarrollo y pruebas de software, es esencial contar con herramientas y métodos que
aseguren tanto la calidad del código como la productividad del equipo. En nuestro proceso de trabajo,
empleamos una variedad de herramientas que optimizan tanto la creación como la validación de la
funcionalidad y el comportamiento previsto de la aplicación. Estas herramientas abarcan distintas fases
del ciclo de vida del software, desde la escritura del código hasta la ejecución de pruebas y la
automatización de tareas.

Seguimos las metodologías de Desarrollo Orientado por Comportamiento (BDD) y Desarrollo Orientado
por Pruebas (TDD) para asegurar que nuestras soluciones no solo cumplan con los requerimientos del
cliente, sino que también mantengan altos niveles de calidad técnica. Algunas de las herramientas
principales que utilizamos son:

| **Herramienta** | **Tipo** | **Descripción** | **Propósito** |
|------------------|----------|-----------------|----------------|
| **J Unit** | Herramienta para pruebas (TDD) | Es un programa que ayuda a probar pequeñas partes de aplicaciones en Java. | Hace más fácil crear y ejecutar pruebas para asegurarse de que las funciones de los componentes funcionen como deberían. |
| **Mockito** | Herramienta de simulaciones (TDD) | Permite crear versiones simuladas de otros componentes para hacer pruebas sin usar las versiones reales. | Imitar cómo se comportan objetos externos, lo cual es útil para hacer pruebas de forma efectiva. |


### 7.1.2. Build & Test Suite Pipeline Components

Para garantizar la calidad y confiabilidad del software, hemos implementado una pipeline de construcción y pruebas automatizada que 
integra múltiples componentes especializados. Esta pipeline ejecuta secuencialmente diferentes tipos de pruebas y validaciones, asegurando que cada cambio en el código cumpla con los estándares establecidos antes de su despliegue.

## 7.2. Continuous Delivery

Su objetivo es el de automatizar la integración y pruebas del código, manteniendo todo listo para un
despliegue cuando sea necesario.

### 7.2.1. Tools and Practices

**Tools:**

Github Actions/GitLab Cli: Son herramientas que te permiten automatizar todo el pipeline de
CI/CD, pero en el caso de Continuous Delivery, podemos configurar una etapa donde el
despliegue final sea manual. Esto asegura que el software está listo, pero no se despliega
automáticamente, pues esa es función del Continuous Deployment.

Github Issues: Se usan para gestionar el proceso de aprobación del despliegue. Puedes configurar un
sistema donde, después de la validación del pipeline, un administrador o gerente de proyecto
debe revisar y aprobar el despliegue a producción.

**Practices (Prácticas)**

Feature Branching y Merge Requests:

Al igual que en Continuous Deployment, las nuevas funcionalidades o cambios se desarrollan en
ramas separadas. Sin embargo, en Continuous Delivery, el código se fusiona a una rama estable
después de pasar pruebas automáticas, pero el despliegue a producción puede requerir una
aprobación manual.

Pipeline de Validación en Staging:

Antes de desplegar a producción, los cambios suelen pasar por un entorno de staging, donde el
código se valida en condiciones similares a las de producción. Aquí, el equipo puede ejecutar
pruebas manuales o recibir retroalimentación de usuarios clave antes del despliegue definitivo.

Despliegue Semiautomático:

El pipeline prepara la aplicación para ser desplegada, pero el despliegue final solo se realiza
cuando un desarrollador o administrador lo aprueba. Esto es clave en Continuous Delivery, donde
no se automatiza completamente el despliegue en producción.

Aprobación Manual:

Antes de hacer el despliegue en producción, el pipeline puede requerir que un responsable del
proyecto revise los resultados de las pruebas y apruebe el despliegue. Esto reduce el riesgo de
lanzar código no deseado en producción.

Rollback Manual:

Aunque el pipeline puede estar configurado para realizar rollbacks automáticos en caso de
errores graves, en Continuous Delivery, los rollbacks suelen ser manuales y controlados por el
equipo de operaciones o desarrollo.


### 7.2.2. Stages Deployment Pipeline Components

Integración Continua (CI):

Al hacer un commit en una rama de desarrollo, el pipeline ejecuta pruebas automáticas y valida
que la aplicación esté lista para ser desplegada. Este paso garantiza que el código siempre esté
en un estado "desplegable".

Validación en Staging:

Una parte importante es tambien la validación del código en un entorno de staging antes de
desplegar a producción. Aquí se simulan escenarios de producción y se pueden realizar pruebas
adicionales, incluyendo pruebas manuales, de carga o seguridad.

Despliegue Manual:

Aunque el código puede estar preparado para su despliegue automático, el paso final del
despliegue requiere la aprobación de una persona. Esto permite una mayor supervisión antes de
afectar a los usuarios finales.

Monitoreo y Feedback:

El pipeline de CD incluye herramientas de monitoreo y análisis que permiten observar cómo el
nuevo código afecta el rendimiento de la aplicación antes de hacer el despliegue completo.

Aprobación del Despliegue:

En este componente, el pipeline queda en espera hasta que un desarrollador, administrador o
equipo de operaciones apruebe el despliegue a producción.


## 7.3. Continuous deployment

El objetivo de Continuous Deployment (CD) es que los cambios aprobados en el código pasen
automáticamente desde el desarrollo hasta la producción, garantizando que cada nueva versión sea
entregada sin intervención manual, siempre y cuando pase todas las pruebas de validación.

### 7.3.1. Tools and Practices

En este apartado, se detallan las herramientas y prácticas que aseguran un despliegue automatizado y
confiable en producción.

**Tools (Herramientas):**

* GitHub Actions o GitLab CI: Para automatizar el pipeline de CI/CD. Estas herramientas permiten
configurar workflows que incluyen la ejecución de pruebas y el despliegue automático a
diferentes entornos (desarrollo, staging, producción).

* Railway: Esta plataforma se encargará del despliegue automatizado del backend desarrollado en Spring Boot, 
ofreciendo integración continua, escalabilidad y herramientas de monitoreo que facilitan la gestión del entorno de ejecución.

* Netlify: Para el frontend desarrollado en Angular, Netlify permite realizar despliegues automáticos desde el repositorio, 
garantizando velocidad, seguridad y soporte para configuraciones personalizadas de dominio y rutas.

* Aiven: Como plataforma para la base de datos MySQL, Aiven ofrece una gestión completamente automatizada con soporte para copias de seguridad, alta disponibilidad y escalabilidad,
asegurando la estabilidad y el rendimiento del servicio de datos.

**Feature Branching:**

* Utilizamos una estrategia de ramas en Git donde los desarrolladores trabajan en nuevas
funcionalidades dentro de ramas separadas. Una vez completadas y probadas, estas ramas se
fusionan a la rama develop, que es la encargada de gestionar los despliegues a producción.
* Commit-based deployment (Despliegue basado en commits): Cada vez que se realiza un
commit en la rama develop, el pipeline de CI/CD se activa automáticamente para ejecutar los
procesos de construcción, pruebas y despliegue. Esta rama es la que usamos para que los
cambios se desplieguen directamente, manteniendo el flujo de trabajo ágil y automatizado.
* Rollback automático: En caso de detectar fallos en producción después del despliegue, el
pipeline está configurado para realizar un rollback automático, restaurando la versión anterior
del software y notificando al equipo sobre el error. Esto garantiza estabilidad y una rápida
recuperación de fallos

### 7.3.2. Production Deployment Pipeline Components

**Componentes del Pipeline de la Base de Datos (Aiven):**

Este apartado describe los componentes que forman parte del pipeline de despliegue a producción para la base de datos MySQL gestionada en Aiven.

1. Gestión de Migraciones Automáticas:
Al realizar cambios en el modelo de datos del backend (Spring Boot), las migraciones se aplican automáticamente en la base de datos alojada en Aiven. Spring Boot sincroniza las modificaciones de las entidades con la estructura de la base de datos, garantizando coherencia entre el código y los datos.

2. Backup y Restauración Automática:
Aiven crea copias de seguridad automáticas de la base de datos antes de cada actualización crítica. Esto permite restaurar el estado anterior de la base de datos en caso de fallos durante la migración o el despliegue, evitando pérdida de información.

3. Monitoreo y Alertas de Rendimiento:
Aiven ofrece paneles de monitoreo en tiempo real que permiten analizar métricas de rendimiento, consultas lentas o errores. En caso de detectar anomalías, se generan alertas automáticas para que el equipo de desarrollo pueda intervenir de inmediato.

4. Validación del Esquema:
Tras las migraciones, se ejecutan pruebas automatizadas de validación de esquema, comprobando que las tablas, columnas y relaciones fueron creadas o modificadas correctamente según el nuevo modelo de datos.

5. Despliegue Continuo:
Una vez completadas y validadas las migraciones, los cambios se aplican automáticamente en el entorno de producción de Aiven, asegurando un flujo de trabajo continuo y sin interrupciones.

**Componentes del Pipeline del Backend (Railway para Spring Boot):**

1. Integración Continua:
Cuando se realiza un commit en la rama principal o de desarrollo, Railway detecta los cambios y construye automáticamente el backend desarrollado en Spring Boot utilizando Maven.

2. Construcción y Despliegue Automatizado:
Railway genera la imagen del backend, instala las dependencias necesarias y realiza el despliegue de forma automatizada en su infraestructura de ejecución, garantizando coherencia entre los entornos de desarrollo y producción.

3. Gestión de Variables de Entorno:
Railway facilita la configuración segura de las variables de entorno (como credenciales o endpoints de la base de datos Aiven), evitando su exposición directa en el código fuente.

4. Monitoreo y Escalabilidad:
Una vez desplegada la aplicación, Railway ofrece herramientas de monitoreo de logs, consumo de recursos y tráfico, además de permitir la escalabilidad automática para adaptarse a la demanda.

5. Despliegue Continuo:
Cada nuevo cambio validado se despliega automáticamente en el entorno de producción, manteniendo un ciclo de integración y entrega continua (CI/CD).

**Componentes del Pipeline del Frontend (Netlify para Angular):**

1. Compilación del Frontend:
Al detectar un nuevo commit en el repositorio, Netlify ejecuta automáticamente el proceso de compilación del proyecto Angular en modo producción, optimizando los recursos para su despliegue.

2. Ejecución de Pruebas Automatizadas:
Antes del despliegue, Netlify puede ejecutar pruebas unitarias y de integración continua (E2E) para garantizar que la interfaz funciona correctamente y que no existen errores en el build.

3. Despliegue en Netlify:
Si las pruebas se completan exitosamente, Netlify publica automáticamente la nueva versión de la aplicación en su red de entrega de contenido (CDN), garantizando una distribución global rápida y segura.

4. Gestión de Caché y Versionado:
Netlify invalida la caché automáticamente tras cada despliegue, asegurando que los usuarios siempre reciban la versión más reciente de la aplicación sin necesidad de actualizaciones manuales.

5. Monitoreo y Registro:
Netlify ofrece herramientas de monitoreo del estado del sitio y registros de despliegue que permiten rastrear errores, tiempos de respuesta y rendimiento del frontend.
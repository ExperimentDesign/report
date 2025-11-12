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

| **Herramienta** | **Tipo** | **Descripción**                                                                                          | **Propósito** |
|-----------------|----------|----------------------------------------------------------------------------------------------------------|----------------|
| **X Unit**      | Herramienta para pruebas (TDD) | Es un programa que ayuda a probar pequeñas partes de aplicaciones en C#.                                 | Hace más fácil crear y ejecutar pruebas para asegurarse de que las funciones de los componentes funcionen como deberían. |
| **Cucumber**    | Herramienta para pruebas (BDD) | Permite escribir pruebas en un lenguaje sencillo que todos pueden entender.                              | Facilita la colaboración entre desarrolladores y no desarrolladores al definir cómo debería comportarse el software. |

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

* Railway: Esta plataforma se encargará del despliegue automatizado del backend desarrollado en .net, 
ofreciendo integración continua, escalabilidad y herramientas de monitoreo que facilitan la gestión del entorno de ejecución.

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
Al realizar cambios en el modelo de datos del backend , las migraciones se aplican automáticamente en la base de datos alojada en Aiven. Se sincroniza las modificaciones de las entidades con la estructura de la base de datos, garantizando coherencia entre el código y los datos.

2. Backup y Restauración Automática:
Aiven crea copias de seguridad automáticas de la base de datos antes de cada actualización crítica. Esto permite restaurar el estado anterior de la base de datos en caso de fallos durante la migración o el despliegue, evitando pérdida de información.

3. Monitoreo y Alertas de Rendimiento:
Aiven ofrece paneles de monitoreo en tiempo real que permiten analizar métricas de rendimiento, consultas lentas o errores. En caso de detectar anomalías, se generan alertas automáticas para que el equipo de desarrollo pueda intervenir de inmediato.

4. Validación del Esquema:
Tras las migraciones, se ejecutan pruebas automatizadas de validación de esquema, comprobando que las tablas, columnas y relaciones fueron creadas o modificadas correctamente según el nuevo modelo de datos.

5. Despliegue Continuo:
Una vez completadas y validadas las migraciones, los cambios se aplican automáticamente en el entorno de producción de Aiven, asegurando un flujo de trabajo continuo y sin interrupciones.

**Componentes del Pipeline del Backend (Railway para .Net):**

1. Integración Continua:
Cuando se realiza un commit en la rama principal o de desarrollo, Railway detecta los cambios y construye automáticamente el backend desarrollado en .net.

2. Construcción y Despliegue Automatizado:
Railway genera la imagen del backend, instala las dependencias necesarias y realiza el despliegue de forma automatizada en su infraestructura de ejecución, garantizando coherencia entre los entornos de desarrollo y producción.

3. Gestión de Variables de Entorno:
Railway facilita la configuración segura de las variables de entorno (como credenciales o endpoints de la base de datos Aiven), evitando su exposición directa en el código fuente.

4. Monitoreo y Escalabilidad:
Una vez desplegada la aplicación, Railway ofrece herramientas de monitoreo de logs, consumo de recursos y tráfico, además de permitir la escalabilidad automática para adaptarse a la demanda.

5. Despliegue Continuo:
Cada nuevo cambio validado se despliega automáticamente en el entorno de producción, manteniendo un ciclo de integración y entrega continua (CI/CD).

**Componentes del Pipeline del Frontend (Railway para Vue):**

1. Compilación del Frontend:
Al detectar un nuevo commit en el repositorio, Railway ejecuta automáticamente el proceso de compilación del proyecto Vue en modo producción, optimizando los recursos para su despliegue.

2. Ejecución de Pruebas Automatizadas:
Antes del despliegue, Railway puede ejecutar pruebas unitarias y de integración continua (E2E) para garantizar que la interfaz funciona correctamente y que no existen errores en el build.

3. Despliegue en Netlify:
Si las pruebas se completan exitosamente, Railway publica automáticamente la nueva versión de la aplicación en su red de entrega de contenido (CDN), garantizando una distribución global rápida y segura.

4. Gestión de Caché y Versionado:
Railway invalida la caché automáticamente tras cada despliegue, asegurando que los usuarios siempre reciban la versión más reciente de la aplicación sin necesidad de actualizaciones manuales.

5. Monitoreo y Registro:
Railway ofrece herramientas de monitoreo del estado del sitio y registros de despliegue que permiten rastrear errores, tiempos de respuesta y rendimiento del frontend.

## 7.4. Continuous monitoring

El monitoreo continuo tiene como objetivo garantizar la disponibilidad, rendimiento y estabilidad del sistema en producción, detectando de manera temprana cualquier anomalía que pueda afectar la experiencia del usuario o la operación del negocio.
A través de herramientas de observabilidad, se recopilan métricas, logs y trazas que permiten identificar y resolver incidencias rápidamente.

### 7.4.1. Tools and Practices

Algunas herramientas y prácticas que se emplearán para llevar a cabo un monitoreo continuo y eficaz en
nuestra aplicación, son las siguientes:

**Tools**

| Herramienta       | Tipo                         | Descripción                                                                                                                    | Propósito                                                                           |
|-------------------| ---------------------------- |--------------------------------------------------------------------------------------------------------------------------------| ----------------------------------------------------------------------------------- |
| **Prometheus**    | Monitoreo de métricas        | Sistema open source que recopila y almacena métricas en tiempo real, ideal para monitorear servicios backend y bases de datos. | Detectar anomalías en el rendimiento del backend y base de datos (Railway + Aiven). |
| **Grafana**       | Visualización de métricas    | Plataforma que se integra con Prometheus para generar dashboards interactivos.                                                 | Visualizar métricas clave de CPU, memoria, peticiones HTTP, latencia, etc.          |
| **New Relic / Datadog** | Observabilidad integral      | Ofrece trazabilidad completa del sistema (APM), logs, alertas y monitoreo de experiencia de usuario.                           | Supervisar la salud de los servicios y detectar errores en tiempo real.             |
| **Railway**       | Monitoreo de frontend        | Servicio integrado de Railway que analiza el tráfico y rendimiento del sitio sin necesidad de scripts externos.                | Analizar rendimiento, tráfico y comportamiento del frontend Vue.                    |
| **Google Lighthouse** | Auditoría de rendimiento web | Evalúa la accesibilidad, SEO, performance y buenas prácticas del sitio web.                                                    | Mejorar la experiencia del usuario y la optimización del frontend.                  |
| **Aiven Metrics Dashboard** | Monitoreo de base de datos   | Panel nativo que muestra métricas de MySQL, rendimiento de consultas y estado de las conexiones.                               | Identificar cuellos de botella en la base de datos y optimizar rendimiento.         |

**Practices**

* Monitoreo centralizado: Todas las métricas (backend, frontend y base de datos) se unifican en Grafana para una visualización global del sistema.

* Métricas clave (KPI):

   * Tasa de error de API

   * Tiempo promedio de respuesta

    * Tiempos de carga del frontend

   * Uso de CPU/memoria en Railway

   * Latencia de consultas MySQL (Aiven)

* Auditorías automáticas: Lighthouse se ejecuta periódicamente (por ejemplo, mediante GitHub Actions) para detectar degradaciones de rendimiento o accesibilidad.



### 7.4.2. Monitoring Pipeline Components

Un pipeline de monitoreo constante integra diversas etapas que ayudan a mantener la calidad y el
rendimiento de una aplicación. Estas etapas incluyen la recopilación de datos, el almacenamiento, el
análisis y la visualización. Herramientas como Google Lighthouse juegan un papel
fundamental en este proceso, ofreciendo evaluaciones complementarias que permiten entender y mejorar
la experiencia del usuario.
Google Lighthouse es ideal para realizar auditorías de calidad en sitios web, proporcionando análisis
detallados de accesibilidad, buenas prácticas, SEO y rendimiento. Esta herramienta permite a los equipos
identificar problemas que impactan la experiencia del usuario, tales como tiempos de carga y cambios
de diseño.

### 7.4.3. Alerting Pipeline Components

El sistema de alertas garantiza una respuesta inmediata ante incidentes mediante notificaciones automáticas.

| Componente                  | Descripción                                                                                                                    |
|-----------------------------| ------------------------------------------------------------------------------------------------------------------------------ |
| **Prometheus Alertmanager** | Define reglas de alerta (por ejemplo, “latencia > 1s” o “errores 5xx > 5%”) y envía notificaciones a los canales configurados. |
| **Grafana Alerts**          | Permite crear alertas visuales directamente desde los paneles, integradas con Slack, Discord o correo electrónico.             |
| **Railway**                 | Supervisa el uptime del sitio y genera notificaciones cuando la aplicación frontend está inaccesible.                          |
| **Aiven Alerts**            | Envía alertas automáticas por correo o Slack ante caídas o alto uso de recursos en MySQL.                                      |



### 7.4.4. Notification Pipeline Components

En un pipeline de notificaciones es esencial para comunicar de forma automática los resultados de las
pruebas y el estado del pipeline. Jenkins juega un papel fundamental en este proceso, ya que permite
configurar notificaciones detalladas sobre el progreso y los resultados de cada fase del pipeline de
pruebas

Con Jenkins, las notificaciones pueden configurarse para que se envíen automáticamente al finalizar
cada build o etapa del pipeline, informando sobre el éxito o fallo de las pruebas, el tiempo de ejecución
y los problemas específicos encontrados. Esto permite que el equipo reciba alertas en tiempo real sobre
cualquier incidente o fallo en las pruebas, facilitando una respuesta inmediata. Jenkins también permite
generar reportes detallados y automatizar el envío de resúmenes periódicos, proporcionando una visión
completa del estado de calidad del software en cada ciclo de pruebas.



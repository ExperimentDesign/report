<p align="center">
  <img src="./assets/logo-upc.png" alt="Logo de UPC" width="25%">
</p>

<div align="center">

# Universidad Peruana de Ciencias Aplicadas

## Carrera de Ingeniería de Software

Ciclo: 2025 - 02

Curso: Diseño de Experimentos de Ingeniería de Software

NRC: 7505

Profesor: Noriega Melendez, Julio Manuel

“Informe de TP”

Startup: EduSpace

Producto:

| Integrantes                        | Código     |
| ---------------------------------- | ---------- |
| Andrés Alberto Torres García       | U202220528 |
| Piero Alberto Velarde Luyo         | U20211A620 |
| Marllely Anahi Arias Segil         | U202223984 |
| Luciana Celeste Sanchez Silva      | U202215979 |
| Alejandro Franklin Mendoza Vergara | U202312343 |

Octubre 2025

</div>

# **Registro de Versiones del Informe**

| Versión | Fecha | Autor              | Descripción de modificación                                                                                                                                                                                          |
| ------- | ----- | ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.0     | 17/09 | Equipo de Eduspace | Se comienza el proyecto con el Capítulo I: Introducción, Capítulo II: Requirements Elicitation & Analysis, Capítulo III: Requirements Specification, Capítulo IV: Product Design, Capítulo V: Product Implementation |
| 2.0     | 02/10 | Equipo de Eduspace | Se agregó el Capítulo VI: Product Verification & Validation y Capítulo VII: DevOps Practices                                                                                                                         |

# **Project Report Collaboration Insights**

# **Student Outcome**

<p align ="justify">
<strong> ABET – EAC - Student Outcome 4 </strong> <br>
Criterio: <em> La capacidad de reconocer responsabilidades éticas y
profesionales en situaciones de ingeniería y hacer juicios informados, que deben
considerar el impacto de las soluciones de ingeniería en contextos globales, económicos,
ambientales y sociales.</em><br>
En el siguiente cuadro se describe las acciones realizadas y enunciados de
conclusiones por parte del grupo, que permiten sustentar el haber alcanzado el logro
del ABET – EAC - Student Outcome 4.</p>

| Criterio Específico                                                                                                                                                               | Acciones Realizadas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Conclusiones                                                                                                                                                                                                                                                                                                                                               |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Student Outcome 4 – Proyecto de gestión de espacios educativos**<br><br>**Criterio 1** – Reconoce responsabilidad ética y profesional en situaciones de ingeniería de software. | **Integrante: Andres Torres**<br>Acción realizada: Aplicó buenas prácticas en el control de versiones (uso de ramas y commits descriptivos) para asegurar trazabilidad y responsabilidad en el desarrollo.<br><br>**Integrante: Piero Velarde**<br>Acción realizada: Documentó de manera clara la API del backend para que otros desarrolladores puedan mantener el sistema de manera ética y profesional.<br><br>**Integrante: Marllely Arias**<br>Acción realizada: Implementó validaciones de datos en el frontend para garantizar que la información de los usuarios no sea manipulada de forma indebida.<br><br>**Integrante: Luciana Sanchez**<br>Acción realizada: Respetó las licencias de librerías y frameworks utilizados, evitando el uso de software no autorizado.<br><br>**Integrante: Alejandro Mendoza**<br>Acción realizada: Realizó pruebas de seguridad en la aplicación móvil para proteger la información sensible de los usuarios.                                                        | El equipo demostró responsabilidad ética y profesional mediante el cumplimiento de estándares de desarrollo seguro, documentación transparente, uso adecuado de recursos de terceros y compromiso con la protección de los datos de los usuarios. Esto asegura que el sistema de gestión de espacios educativos se construya de forma íntegra y confiable. |
| **Criterio 2** – Emite juicios informados considerando el impacto de las soluciones de ingeniería de software en contextos globales, económicos, ambientales y sociales.          | **Integrante: Andres Torres**<br>Acción realizada: Analizó el impacto social positivo del sistema, al permitir un uso más eficiente de los espacios educativos y mejorar la experiencia de estudiantes y docentes.<br><br>**Integrante: Piero Velarde**<br>Acción realizada: Evaluó el impacto económico, diseñando la solución de forma que reduzca costos de operación en la gestión de reservas y mantenimiento de aulas.<br><br>**Integrante: Marllely Arias**<br>Acción realizada: Consideró la accesibilidad en la interfaz, asegurando que el software sea inclusivo y usable por un público diverso.<br><br>**Integrante: Luciana Sanchez**<br>Acción realizada: Valoró el impacto ambiental al digitalizar procesos de reserva, reduciendo el uso de papel y trámites físicos.<br><br>**Integrante: Alejandro Mendoza**<br>Acción realizada: Revisó la escalabilidad y la capacidad de adaptación del sistema a nivel global, considerando su posible aplicación en distintas instituciones educativas. | El equipo emitió juicios informados sobre el alcance del sistema, valorando no solo la funcionalidad técnica, sino también su contribución social, económica y ambiental. El software desarrollado muestra un impacto positivo al promover eficiencia, accesibilidad, sostenibilidad y posibilidades de adaptación a diferentes contextos educativos.      |

# **Contenido**

## Tabla de Contenidos

# Índice

## [Capítulo I: Introducción](#capitulo-i-introduccion)

- [1.1. Startup Profile](#11-startup-profile)
  - [1.1.1. Descripción de la Startup](#111-descripcion-de-la-startup)
  - [1.1.2. Perfiles de integrantes del equipo](#112-perfiles-de-integrantes-del-equipo)
- [1.2. Solution Profile](#12-solution-profile)
  - [1.2.1. Antecedentes y problemática](#121-antecedentes-y-problematica)
  - [1.2.2. Lean UX Process](#122-lean-ux-process)
    - [1.2.2.1. Lean UX Problem Statements](#1221-lean-ux-problem-statements)
    - [1.2.2.2. Lean UX Assumptions](#1222-lean-ux-assumptions)
    - [1.2.2.3. Lean UX Hypothesis Statements](#1223-lean-ux-hypothesis-statements)
    - [1.2.2.4. Lean UX Canvas](#1224-lean-ux-canvas)
- [1.3. Segmentos objetivo](#13-segmentos-objetivo)

## [Capítulo II: Requirements Elicitation & Analysis](#capitulo-ii-requirements-elicitation--analysis)

- [2.1. Competidores](#21-competidores)
  - [2.1.1. Análisis competitivo](#211-analisis-competitivo)
  - [2.1.2. Estrategias y tácticas frente a competidores](#212-estrategias-y-tacticas-frente-a-competidores)
- [2.2. Entrevistas](#22-entrevistas)
  - [2.2.1. Diseño de entrevistas](#221-diseno-de-entrevistas)
  - [2.2.2. Registro de entrevistas](#222-registro-de-entrevistas)
  - [2.2.3. Análisis de entrevistas](#223-analisis-de-entrevistas)
- [2.3. Needfinding](#23-needfinding)
  - [2.3.1. User Personas](#231-user-personas)
  - [2.3.2. User Task Matrix](#232-user-task-matrix)
  - [2.3.3. User Journey Mapping](#233-user-journey-mapping)
  - [2.3.4. Empathy Mapping](#234-empathy-mapping)
  - [2.3.5. As-is Scenario Mapping](#235-as-is-scenario-mapping)
- [2.4. Ubiquitous Language](#24-ubiquitous-language)

## [Capítulo III: Requirements Specification](#capitulo-iii-requirements-specification)

- [3.1. To-Be Scenario Mapping](#31-to-be-scenario-mapping)
- [3.2. User Stories](#32-user-stories)
- [3.3. Product Backlog](#33-product-backlog)
- [3.4. Impact Mapping](#34-impact-mapping)

## [Capítulo IV: Product Design](#capitulo-iv-product-design)

- [4.1. Style Guidelines](#41-style-guidelines)
  - [4.1.1. General Style Guidelines](#411-general-style-guidelines)
  - [4.1.2. Web Style Guidelines](#412-web-style-guidelines)
  - [4.1.3. Mobile Style Guidelines](#413-mobile-style-guidelines)
    - [4.1.3.1. iOS Mobile Style Guidelines](#4131-ios-mobile-style-guidelines)
    - [4.1.3.2. Android Mobile Style Guidelines](#4132-android-mobile-style-guidelines)
- [4.2. Information Architecture](#42-information-architecture)
  - [4.2.1. Organization Systems](#421-organization-systems)
  - [4.2.2. Labeling Systems](#422-labeling-systems)
  - [4.2.3. SEO Tags and Meta Tags](#423-seo-tags-and-meta-tags)
  - [4.2.4. Searching Systems](#424-searching-systems)
  - [4.2.5. Navigation Systems](#425-navigation-systems)
- [4.3. Landing Page UI Design](#43-landing-page-ui-design)
  - [4.3.1. Landing Page Wireframe](#431-landing-page-wireframe)
  - [4.3.2. Landing Page Mock-up](#432-landing-page-mock-up)
- [4.4. Mobile Applications UX/UI Design](#44-mobile-applications-uxui-design)
  - [4.4.1. Mobile Applications Wireframes](#441-mobile-applications-wireframes)
  - [4.4.2. Mobile Applications Wireflow Diagrams](#442-mobile-applications-wireflow-diagrams)
  - [4.4.3. Mobile Applications Mock-ups](#443-mobile-applications-mock-ups)
  - [4.4.4. Mobile Applications User Flow Diagrams](#444-mobile-applications-user-flow-diagrams)
- [4.5. Mobile Applications Prototyping](#45-mobile-applications-prototyping)
  - [4.5.1. Android Mobile Applications Prototyping](#451-android-mobile-applications-prototyping)
  - [4.5.2. iOS Mobile Applications Prototyping](#452-ios-mobile-applications-prototyping)
- [4.6. Web Applications UX/UI Design](#46-web-applications-uxui-design)
  - [4.6.1. Web Applications Wireframes](#461-web-applications-wireframes)
  - [4.6.2. Web Applications Wireflow Diagrams](#462-web-applications-wireflow-diagrams)
  - [4.6.3. Web Applications Mock-ups](#463-web-applications-mock-ups)
  - [4.6.4. Web Applications User Flow Diagrams](#464-web-applications-user-flow-diagrams)
- [4.7. Web Applications Prototyping](#47-web-applications-prototyping)
- [4.8. Domain-Driven Software Architecture](#48-domain-driven-software-architecture)
  - [4.8.1. Software Architecture Context Diagram](#481-software-architecture-context-diagram)
  - [4.8.2. Software Architecture Container Diagrams](#482-software-architecture-container-diagrams)
  - [4.8.3. Software Architecture Components Diagrams](#483-software-architecture-components-diagrams)
- [4.9. Software Object-Oriented Design](#49-software-object-oriented-design)
  - [4.9.1. Class Diagrams](#491-class-diagrams)
  - [4.9.2. Class Dictionary](#492-class-dictionary)
- [4.10. Database Design](#410-database-design)
  - [4.10.1. Relational/Non-Relational Database Diagram](#4101-relationalnon-relational-database-diagram)

## [Capítulo V: Product Implementation](#capitulo-v-product-implementation)

- [5.1. Software Configuration Management](#51-software-configuration-management)
  - [5.1.1. Software Development Environment Configuration](#511-software-development-environment-configuration)
  - [5.1.2. Source Code Management](#512-source-code-management)
  - [5.1.3. Source Code Style Guide & Conventions](#513-source-code-style-guide--conventions)
  - [5.1.4. Software Deployment Configuration](#514-software-deployment-configuration)
- [5.2. Product Implementation & Deployment](#52-product-implementation--deployment)
  - [5.2.1. Sprint Backlogs](#521-sprint-backlogs)
  - [5.2.2. Implemented Landing Page Evidence](#522-implemented-landing-page-evidence)
  - [5.2.3. Implemented Frontend-Web Application Evidence](#523-implemented-frontend-web-application-evidence)
  - [5.2.4. Acuerdo de Servicio - SaaS](#524-acuerdo-de-servicio---saas)
  - [5.2.5. Implemented Native-Mobile Application Evidence](#525-implemented-native-mobile-application-evidence)
  - [5.2.6. Implemented RESTful API and/or Serverless Backend Evidence](#526-implemented-restful-api-andor-serverless-backend-evidence)
  - [5.2.7. RESTful API Documentation](#527-restful-api-documentation)
  - [5.2.8. Team Collaboration Insights](#528-team-collaboration-insights)
- [5.3. Video About-the-Product](#53-video-about-the-product)

## [Capítulo VI: Product Verification & Validation](#capitulo-vi-product-verification--validation)

- [6.1. Testing Suites & Validation](#61-testing-suites--validation)
  - [6.1.1. Core Entities Unit Tests](#611-core-entities-unit-tests)
  - [6.1.2. Core Integration Tests](#612-core-integration-tests)
  - [6.1.3. Core Behavior-Driven Development](#613-core-behavior-driven-development)
  - [6.1.4. Core System Tests](#614-core-system-tests)

## [Capítulo VII: DevOps Practices](#capitulo-vii-devops-practices)

- [7.1. Continuous Integration](#71-continuous-integration)
  - [7.1.1. Tools and Practices](#711-tools-and-practices)
  - [7.1.2. Build & Test Suite Pipeline Components](#712-build--test-suite-pipeline-components)
- [7.2. Continuous Delivery](#72-continuous-delivery)
  - [7.2.1. Tools and Practices](#721-tools-and-practices)
  - [7.2.2. Stages Deployment Pipeline Components](#722-stages-deployment-pipeline-components)
- [7.3. Continuous Deployment](#73-continuous-deployment)
  - [7.3.1. Tools and Practices](#731-tools-and-practices)
  - [7.3.2. Production Deployment Pipeline Components](#732-production-deployment-pipeline-components)

### [Conclusiones](/report/chapter5/chapter-5.md#conclusiones)

### [Bibliografía](/report/chapter5/chapter-5.md#bibliografía)

### [Anexos](/report/chapter5/chapter-5.md#anexos)

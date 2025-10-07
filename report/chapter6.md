# Capítulo VI: Product Verification & Validation

## 6.1. Testing Suites & Validation

### 6.1.1. Core Entities Unit Tests

Los Core Entities Unit Tests son fundamentales en el desarrollo de software porque aseguran la calidad y el correcto comportamiento de las entidades clave, evitando fallos y haciendo más sencillo el mantenimiento del código. En nuestro caso, se implementaron pruebas unitarias con xUnit y FluentAssertions.

**1.Classroom aggregate Tests**
 Para el agregado Classroom, se validó que el constructor inicialice correctamente Name, Description, TeacherId y deje Resources vacío; que UpdateName y UpdateDescription ignoren valores nulos o vacíos y solo apliquen cambios válidos; y que UpdateTeacherId mantenga el valor cuando es null o cuando la validación externa verifyProfile falla, actualizándolo únicamente cuando dicha validación retorna true.

![Foto](/assets/chapter6/UnitTests/1.png) 

**2.Reservation Entity Tests**
Estas pruebas aseguran que una reservación sea consistente y mantenga sus invariantes, antes de integrarlo con infraestructura o controladores.

![Foto](/assets/chapter6/COREUNITTEST/2.jpg) 

### 6.1.2. Core Integration Tests

Las Core Integration Tests son clave para verificar que los controladores se relacionen de forma correcta con otros componentes del sistema, como servicios y bases de datos. Al contemplar escenarios de fallo, estas pruebas aseguran que el sistema gestione imprevistos de manera adecuada y devuelva los códigos de estado correspondientes. Con ello se mejora la experiencia de usuario, se simplifica la depuración y se impulsa la construcción de un software confiable y de alta calidad.

**1.**

### 6.1.3. Core Behavior-Driven Development

### 6.1.4. Core System Tests

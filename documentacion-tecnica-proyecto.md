# Documentación técnica del proyecto plex-tac-api-servicios

## 1. Propósito y alcance general
El proyecto `plex-tac-api-servicios` es una API REST modular para la gestión de servicios y configuraciones, orientada a la integración con sistemas empresariales y la automatización de procesos. Incluye módulos como el "Configurador de Agrupador de Tareas" y otros servicios, permitiendo persistencia flexible (DB2 y JSON) y documentación automática con Swagger/OpenAPI.

## 2. Estructura de paquetes y organización de archivos
- `src/main/java/com/globalhitss/tijuana/plex/servicios/`
  - `configasignacion/`: Módulo para configuración de agrupador de tareas
    - `controller/`: Controladores REST
    - `facade/`: Interfaces y facades para persistencia
    - `model/`: Modelos de datos específicos
  - Otros módulos y servicios pueden seguir la misma estructura
- `src/test/java/com/globalhitss/tijuana/plex/servicios/`
  - `configasignacion/controller/`: Tests unitarios para controladores de configuración
  - `controller/`: Tests unitarios para controladores generales
- `src/main/resources/`
  - `configasignacion-data/`: Archivos JSON de prueba y YAML OpenAPI
  - `application.properties`: Configuración global y perfiles
- `docs/`: Documentación y prompts

## 3. Descripción de los endpoints REST
Ejemplo de endpoints del módulo Configurador de Agrupador de Tareas:
- `/api/config/categorias`: Listado de categorías
- `/api/config/tipos-orden`: Tipos de orden por categoría
- `/api/config/etapas-excluidas`: Etapas excluidas por categoría
- `/api/config/modalidad`: Configuración de modalidad
- `/api/config/openapi-yaml`: Descarga del YAML OpenAPI

Todos los endpoints están documentados con Swagger/OpenAPI y visibles en `/swagger-ui.html`. Otros módulos pueden definir sus propios endpoints siguiendo la misma convención.

## 4. Explicación de la persistencia
La persistencia se alterna mediante perfiles de Spring:
- Perfil `json`: Usa archivos JSON de prueba en `configasignacion-data/`.
- Perfil `db2`: Usa base de datos DB2 vía JDBC.
Configura el perfil activo en `application.properties` con `spring.profiles.active`.

## 5. Guía para agregar nuevos módulos, endpoints o modelos
- Crear un nuevo paquete bajo `servicios/`.
- Definir modelos en `model/` y documentarlos con `@Schema`.
- Crear interfaces y facades en `facade/`.
- Implementar controladores en `controller/` y documentar endpoints con `@Operation`, `@ApiResponse`, etc.
- Agregar datos de prueba en un subdirectorio de `resources/`.

## 6. Uso de anotaciones Swagger/OpenAPI
- Todos los endpoints y modelos deben tener anotaciones Swagger/OpenAPI.
- La documentación se genera automáticamente y es visible en `/swagger-ui.html`.

## 7. Instrucciones para compilar, ejecutar y probar el proyecto

- **Compilar:**
  - `mvn clean compile` (solo compila, no ejecuta pruebas)
  - `mvn clean package` (compila y empaqueta, ejecuta solo pruebas unitarias)
  - `mvn clean install` (compila, ejecuta pruebas unitarias y deja el artefacto en el repo local)
  - `mvn clean install -Pintegration-tests` (compila, ejecuta unitarias e integración)
- **Compilar sin tests:** `mvn clean install -DskipTests`
- **Ejecutar:** `mvn spring-boot:run`
- **Cambiar perfil de persistencia:** Edita `spring.profiles.active` en `application.properties` (`json` o `db2`)
- **Probar endpoints:** Usa Swagger UI o herramientas como Insomnia/Postman
- **Configurar base de datos:** Ajusta los parámetros en `application.properties` para DB2

### 7.1. Pruebas Unitarias

### 7.1. Pruebas Unitarias e Integración

El proyecto incluye cobertura de tests unitarios y de integración:

- **Unitarias:**
  - Clases terminan en `*Test.java` (ejemplo: `PlexTacControllerUnitTest.java`)
  - Se ejecutan por defecto con cualquier comando Maven (`test`, `package`, `install`)
- **Integración:**
  - Clases terminan en `*IT.java` o `*IntegrationTest.java` (ejemplo: `PlexTacControllerIntegrationTest.java`)
  - Se ejecutan solo si activas el perfil: `mvn clean install -Pintegration-tests`

**Comandos útiles:**
- Solo unitarias: `mvn clean install`
- Unitarias + integración: `mvn clean install -Pintegration-tests`
- Solo compilar: `mvn clean compile`
- Solo empaquetar: `mvn clean package`
- Saltar tests: `mvn clean install -DskipTests`


## 9. Buenas prácticas y recomendaciones

- Mantén la separación entre módulos y no reutilices modelos o clases de otros módulos.
- Documenta siempre con Swagger/OpenAPI.
- Usa perfiles para alternar entre persistencias y para separar pruebas unitarias e integración.
- Agrega datos de prueba para facilitar el desarrollo y pruebas.
- Sigue la estructura de paquetes recomendada para nuevos módulos.
- **Testing:**
  - Escribe tests unitarios para todos los endpoints nuevos (`*Test.java`)
  - Escribe tests de integración para flujos completos (`*IT.java` o `*IntegrationTest.java`)
  - Usa `@WebMvcTest` para tests de controladores sin cargar toda la aplicación
  - Mockea dependencias con `@MockBean` para aislar la lógica del controlador
  - Asegura que los mocks retornen datos coherentes con el comportamiento esperado del endpoint
  - Verifica que todos los tests pasen antes de hacer commit (`mvn test`)
  - Ejecuta integración solo cuando lo requieras (`-Pintegration-tests`)
  - Los reportes de tests se generan en `target/surefire-reports/` (unitarias) y `target/failsafe-reports/` (integración)

**Dependencias de testing:**
- `spring-boot-starter-test`: Framework de testing de Spring Boot
- JUnit 5: Framework de pruebas unitarias
- Mockito: Framework de mocking
- MockMvc: Simulación de peticiones HTTP

## 8. Referencias a archivos de configuración, datos de prueba y documentación adicional
- `application.properties`: Configuración global y perfiles
- `configasignacion-data/`: JSON de prueba y YAML OpenAPI
- `docs/`: Prompts y documentación

## 9. Buenas prácticas y recomendaciones
- Mantén la separación entre módulos y no reutilices modelos o clases de otros módulos.
- Documenta siempre con Swagger/OpenAPI.
- Usa perfiles para alternar entre persistencias.
- Agrega datos de prueba para facilitar el desarrollo y pruebas.
- Sigue la estructura de paquetes recomendada para nuevos módulos.

## 10. Historial de cambios relevantes y consideraciones de mantenimiento
- Documenta los cambios relevantes en `docs/`.
- Mantén la estructura modular y extensible.
- Actualiza la documentación técnica ante cambios importantes.
- Revisa y elimina archivos duplicados o en desuso para evitar confusión.

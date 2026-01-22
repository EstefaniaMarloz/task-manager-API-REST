# Task Manager API

API REST en Java con Spring Boot para gestionar tareas (CRUD). Proyecto pensado como ejemplo profesional para mostrar buenas prácticas:
Capas (controller/service/repository), validación, manejo de errores, pruebas, Docker, Docker Compose y pipeline de CI.

Tecnologías
- Java 17
- Spring Boot (Web, Data JPA, Validation)
- PostgreSQL
- Maven
- Docker & Docker Compose
- JUnit 5, Mockito, Testcontainers (tests)
- GitHub Actions (CI)

Características
- Endpoints CRUD para Task
- Validaciones de entrada
- DTOs y separación de capas
- Manejo centralizado de errores
- Dockerfile + docker-compose para ejecución local con Postgres
- Pipeline CI que ejecuta tests y build

Quickstart (con Docker)
1. Copia el repositorio.
2. Ejecuta:
   - docker-compose up --build
3. La API estará en: http://localhost:8080
   - DB PostgreSQL en el servicio `db`, puerto 5432 (interno)

Quickstart (local con Maven + Postgres local)
1. Configura una base de datos PostgreSQL y actualiza `src/main/resources/application.yml` o usa variables de entorno:
   - SPRING_DATASOURCE_URL
   - SPRING_DATASOURCE_USERNAME
   - SPRING_DATASOURCE_PASSWORD
2. Ejecuta:
   - mvn clean package
   - java -jar target/task-manager-api-0.0.1-SNAPSHOT.jar

Endpoints principales
- GET /api/tasks               — listar tareas (paginado opcional)
- GET /api/tasks/{id}          — obtener tarea por id
- POST /api/tasks              — crear tarea
- PUT /api/tasks/{id}          — actualizar tarea
- DELETE /api/tasks/{id}       — eliminar tarea

Ejemplos curl
- Crear:
  curl -X POST http://localhost:8080/api/tasks \
    -H "Content-Type: application/json" \
    -d '{"title":"Comprar leche","description":"Leche y huevos","completed":false}'
- Obtener:
  curl http://localhost:8080/api/tasks
- Actualizar:
  curl -X PUT http://localhost:8080/api/tasks/1 \
    -H "Content-Type: application/json" \
    -d '{"title":"Comprar leche y pan","description":"Actualizar detalle","completed":false}'
- Eliminar:
  curl -X DELETE http://localhost:8080/api/tasks/1

Tests
- mvn test
El proyecto incluye tests unitarios y de integración (Testcontainers para Postgres).

CI
- Se incluye un workflow de GitHub Actions que ejecuta build y tests en cada PR/commit.

Buenas prácticas incluidas
- README detallado
- Dockerfile y docker-compose
- Tests automatizados
- Manejo de errores y respuestas REST consistentes
- Licencia MIT

Contacto
- Francisca Estefania Martinez Lozano
-Email: fany.marloz@gmail.com
-LinkedIn: https://www.linkedin.com/in/estefaniaml/

Licencia
- MIT (archivo LICENSE incluido)

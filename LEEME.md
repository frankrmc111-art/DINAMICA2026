# Config Server + Microservicio de Catálogo

## Abrir en IntelliJ IDEA
File → Open → seleccionar el `pom.xml` de esta carpeta (raíz) → "Open as Project".
Se cargan los dos módulos: `ms-config-server` y `ms-catalogo-service`.
Activar: Settings → Build → Compiler → Annotation Processors → *Enable annotation processing* (Lombok).
Requiere JDK 17+.

## Antes de ejecutar
1. PostgreSQL en localhost:5432 (usuario `postgres`, clave `123456`) y crear la BD:
   `CREATE DATABASE ms_catalogo;`
2. Subir `config-data/ms-catalogo-service-development.yml` a la carpeta `config-data/` de la rama `main`
   de tu repositorio de GitHub. Si usas otro repo, cambia `spring.cloud.config.server.git.uri`
   en `ms-config-server/src/main/resources/application.yml`.

## Orden de ejecución
1. `MsConfigServerApplication` (puerto 7070) → http://localhost:7070/ms-catalogo-service/development (root / 123456)
2. `MsCatalogoServiceApplication` (puerto 8081)
3. Swagger: http://localhost:8081/doc/swagger-ui.html

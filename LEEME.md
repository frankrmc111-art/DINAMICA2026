# Config Server + Microservicio de Catálogo

## Abrir en IntelliJ IDEA
1. **File → Open** → seleccionar el `pom.xml` de esta carpeta raíz:
   `C:\Users\yoloxd\.gemini\antigravity\scratch\ms-catalogo-proyecto\pom.xml`
2. Seleccionar **"Open as Project"**.
3. Se cargarán automáticamente los dos módulos: `ms-config-server` y `ms-catalogo-service`.
4. Activar: **Settings → Build, Execution, Deployment → Compiler → Annotation Processors** → marcar **Enable annotation processing** (para Lombok).

## Estado de la Base de Datos
- PostgreSQL 18 en `localhost:5432` con usuario `postgres` y clave `yoloxd`.
- Base de datos `ms_catalogo` ya creada y operativa.

## Orden de ejecución
1. **`MsConfigServerApplication`** (puerto `7070`):
   - Verificar en navegador: http://localhost:7070/ms-catalogo-service/development (credenciales: `root` / `123456`)
2. **`MsCatalogoServiceApplication`** (puerto `8081`):
   - Al iniciar se conecta al Config Server y a la BD PostgreSQL.
3. **Swagger UI**:
   - http://localhost:8081/doc/swagger-ui.html
   - http://localhost:8081/v3/api-docs

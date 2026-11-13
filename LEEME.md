# Config Server + Eureka + Gateway + Microservicio de Catálogo

## Abrir en IntelliJ IDEA
1. **File → Open** → seleccionar el `pom.xml` de esta carpeta raíz.
2. Seleccionar **"Open as Project"**.
3. IntelliJ cargará los 4 módulos: `ms-config-server`, `ms-eureka-server`, `ms-catalogo-service`, `ms-gateway-server`.
4. Activar: **Settings → Build → Compiler → Annotation Processors → Enable annotation processing** (Lombok).

## Requisitos
- JDK 17+, Maven, PostgreSQL 18 en localhost:5432 (usuario `postgres`, clave `yoloxd`)
- Base de datos `ms_catalogo` ya creada.

## Orden de ejecución
1. **`MsConfigServerApplication`** (puerto `7070`)
2. **`MsEurekaServerApplication`** (puerto `8761`) → Panel: http://localhost:8761
3. **`MsCatalogoServiceApplication`** (puerto `8081`) → Swagger: http://localhost:8081/doc/swagger-ui.html
4. **`MsGatewayServerApplication`** (puerto `8080`)

## Probar vía Gateway
- `GET  http://localhost:8080/categoria`
- `POST http://localhost:8080/categoria`  body: `{"nombre": "Electrónica"}`
- `GET  http://localhost:8080/ms-catalogo-service/categoria`  (discovery locator)

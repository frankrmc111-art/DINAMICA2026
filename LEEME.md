# Microservicios: Config Server + Eureka + Gateway + Catálogo (PostgreSQL) + Productos (MySQL)

## Repositorio en GitHub
- **URL:** https://github.com/frankrmc111-art/DINAMICA2026.git
- **Configuración centralizada:** carpeta `config-data/`

## Abrir en IntelliJ IDEA
1. **File → Open** → seleccionar el `pom.xml` de esta carpeta raíz.
2. Seleccionar **"Open as Project"**.
3. IntelliJ cargará los 5 módulos:
   - `ms-config-server` (7070)
   - `ms-eureka-server` (8761)
   - `ms-catalogo-service` (8081 - PostgreSQL)
   - `ms-producto-service` (8082 - MySQL)
   - `ms-gateway-server` (8080)
4. Activar: **Settings → Build → Compiler → Annotation Processors → Enable annotation processing** (Lombok).

## Bases de Datos
- **PostgreSQL 18** en localhost:5432 (usuario `postgres`, clave `yoloxd`, BD `ms_catalogo`)
- **MySQL 8.0** en localhost:3306 (usuario `root`, clave `yoloxd`, BD `ms_producto`)

## Orden de ejecución
1. **`MsConfigServerApplication`** (puerto `7070`) → Lee configs desde GitHub.
2. **`MsEurekaServerApplication`** (puerto `8761`) → Panel Eureka: http://localhost:8761
3. **`MsCatalogoServiceApplication`** (puerto `8081`) → Swagger: http://localhost:8081/doc/swagger-ui.html
4. **`MsProductoServiceApplication`** (puerto `8082`) → Swagger: http://localhost:8082/doc/swagger-ui.html
5. **`MsGatewayServerApplication`** (puerto `8080`)

## Rutas a través del Gateway (puerto 8080)
- **Catálogo:**
  - `GET /categoria`
  - `POST /categoria`  body: `{"nombre": "Electrónica"}`
  - `GET /ms-catalogo-service/categoria` (discovery locator)
- **Productos:**
  - `GET /producto`
  - `POST /producto`  body: `{"nombre": "Laptop Gamer", "precio": 4500.0, "stock": 10, "descripcion": "Core i7 16GB"}`
  - `GET /ms-producto-service/producto` (discovery locator)

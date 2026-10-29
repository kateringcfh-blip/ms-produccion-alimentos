# MsProduccionAlimentos.Api

Microservicio de Producción de Alimentos — parte del proyecto **NurTricenter** (Diplomado de Arquitectura de Microservicios).

Responsable de: órdenes de producción, paquetes, porciones, y consumo del evento `PacienteRegistrado` publicado por el microservicio de Pacientes. También publica el evento `OrdenCancelada` (vía RabbitMQ, con patrón Transactional Outbox) para que lo consuma el microservicio de Pacientes.

## Tecnología

.NET 8, ASP.NET Core (Minimal Hosting), MediatR (CQRS), Entity Framework Core, JWT (autenticación/autorización por roles), RabbitMQ (mensajería), Consul (Service Discovery).

## Cómo correrlo con Docker

```
docker build -t ms-produccion-alimentos .
docker run -p 5234:8080 ms-produccion-alimentos
```

Requiere variables de entorno para conectarse a SQL Server, RabbitMQ y Consul — ver `appsettings.json` para los nombres de configuración esperados (`ConnectionStrings:DefaultConnection`, `RabbitMq:*`, `ServiceDiscovery:*`, `Jwt:*`).

## Usuarios de prueba (login en `POST /api/auth/login`)

| Usuario | Password | Rol |
|---|---|---|
| admin | Admin123! | Administrador |
| nutricionista | Nutri123! | Nutricionista |
| operador | Operador123! | Operador |

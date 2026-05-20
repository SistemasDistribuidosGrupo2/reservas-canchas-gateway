# Reservas Canchas Gateway

API Gateway for the sports field reservation system.

## Description

This service acts as the single entry point for backend requests.

Its responsibilities include:

- routing requests to backend microservices
- validating JWT tokens
- propagating authentication headers to downstream services
- exposing unified endpoints for clients

## Tech Stack

- Java 17
- Spring Boot 3
- Spring WebFlux
- JWT
- Docker

## Project Structure

```text
src/
.mvn/
Dockerfile
pom.xml
mvnw
mvnw.cmd
README.md
````

## Run Locally

```bash
./mvnw spring-boot:run
```

On Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

## Build

```bash
./mvnw clean package -DskipTests
```

On Windows:

```powershell
.\mvnw.cmd clean package -DskipTests
```

## Docker

This project uses a runtime Dockerfile that expects the jar file to exist in `target/`.

Example workflow:

```powershell
.\mvnw.cmd clean package -DskipTests
docker build -t reservas-canchas-gateway .
```

## Environment Variables

* `SERVER_PORT`
* `MS_AUTH_URL`
* `MS_RESERVAS_URL`
* `JWT_SECRET`
* `CORS_ORIGINS`

## Main Endpoints

Examples of routed backend endpoints:

* `/auth/register`
* `/auth/register-admin`
* `/auth/login`
* `/canchas`
* `/reservas`

## Notes

* This service must use the same `JWT_SECRET` as `ms-auth` within the same environment.
* It is intended to be orchestrated through the infrastructure repository.
* Authentication context is propagated through headers such as:

  * `X-User-Id`
  * `X-User-Email`
  * `X-User-Role`

## Related Repositories

* `reservas-canchas-ms-auth`
* `reservas-canchas-ms-reservas`
* `reservas-canchas-infra`


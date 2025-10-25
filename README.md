# Parcial Docker Integrado – Ejercicio 1


## Datos del estudiante
- **Nombre:** Ronal Eduardo Cortez Méndez
- **Expediente:** 22746 
- **Código:** CM18I04002 
- **Repositorio:** parcial-docker-integrado

## Descripción
Este proyecto contiene un servicio Node.js con dos endpoints (`/` y `/health`) que ha sido contenerizado usando Docker con una imagen optimizada basada en `node:18-alpine`.

## Comandos utilizados

```bash
npm init -y
npm install express
docker build -t parcial-api .
docker run -d -p 3000:3000 parcial-api
curl http://localhost:3000/
curl http://localhost:3000/health



## Ejercicio 2 – Persistencia con PostgreSQL y Volumen

**Descripción:**  
Se creó un contenedor PostgreSQL con variables de entorno y volumen persistente. Se creó la tabla `estudiantes` y se insertaron registros. Se validó que los datos persisten tras reinicio.

**Comandos utilizados:**

```bash
docker volume create db_data
docker run -d \
  --name parcial-db \
  -e POSTGRES_USER=admin \
  -e POSTGRES_PASSWORD=12345 \
  -e POSTGRES_DB=parcial_db \
  -v db_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres:15

docker exec -it parcial-db psql -U admin -d parcial_db

CREATE TABLE estudiantes (
  id SERIAL PRIMARY KEY,
  nombre TEXT NOT NULL,
  expediente TEXT NOT NULL
);

INSERT INTO estudiantes (nombre, expediente)
VALUES 
  ('RONAL EDUARDO CORTEZ MENDEZ', '22746'),
  ('MARLIN YAJAIRA MOZ MARIN', '00001');

SELECT * FROM estudiantes;




## Ejercicio 3 – Integración con Docker Compose

**Descripción:**  
Se integraron los servicios `api` y `db` usando `docker-compose.yml`, con red compartida, volumen persistente y healthcheck para PostgreSQL. Se usó `.env` para variables.

**Comandos utilizados:**

```bash
docker compose up -d --build
docker ps
curl http://localhost:3000/
curl http://localhost:3000/health

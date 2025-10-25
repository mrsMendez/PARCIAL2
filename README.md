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

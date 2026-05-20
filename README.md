# Tienda de Alimentos para Perritos ??

Aplicacion web CRUD de 3 capas desplegada en AWS EC2 usando Docker y GitHub Actions.

## Arquitectura

- **Frontend:** Nginx sirviendo HTML/JS estatico (EC2 publica)
- **Backend:** Node.js API REST puerto 3001 (EC2 privada)
- **Base de datos:** MySQL 8 con volumenes Docker (EC2 privada)

## Tecnologias

- Docker + Docker Compose
- GitHub Actions (CI/CD)
- Amazon ECR (registro de imagenes)
- Amazon EC2 (despliegue)
- AWS SSM (automatizacion de deploy)

## Pipeline CI/CD

Cada push a la rama `deploy` activa automaticamente el pipeline:
1. Build de la imagen Docker
2. Push a Amazon ECR
3. Deploy automatico en EC2 via SSM

## Como levantar localmente

```bash
docker-compose up --build
```

Acceder en: http://localhost

## Secrets requeridos

| Secret | Descripcion |
|--------|-------------|
| AWS_ACCESS_KEY_ID | Credencial AWS |
| AWS_SECRET_ACCESS_KEY | Credencial AWS |
| AWS_SESSION_TOKEN | Token de sesion AWS |
| AWS_REGION | Region AWS |
| ECR_REGISTRY | URL base ECR |
| ECR_REPO_URL_DB | URL repo ECR DB |
| ECR_REPO_URL_BACKEND | URL repo ECR Backend |
| ECR_REPO_URL_FRONTEND | URL repo ECR Frontend |
| EC2_DB_INSTANCE_ID | ID instancia EC2 DB |
| EC2_BACKEND_INSTANCE_ID | ID instancia EC2 Backend |
| EC2_FRONTEND_INSTANCE_ID | ID instancia EC2 Frontend |

## Estructura del proyecto '@
$content | Set-Content "README.md"


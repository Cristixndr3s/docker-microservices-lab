# docker-microservices-lab
Laboratorio de dockerización de una arquitectura basada en microservicios Java utilizando Docker y Docker Compose. Incluye Config Server, Eureka Server, Accounts, Loans, Cards y Gateway Server, completamente orquestados y probados localmente.


# Docker Microservices Lab 🐳☁️

Este proyecto es un laboratorio práctico que demuestra cómo **dockerizar** una aplicación distribuida basada en microservicios Java, utilizando **Docker** y **Docker Compose** para su construcción, despliegue y orquestación.

## 📌 Arquitectura

La aplicación está compuesta por los siguientes servicios:

- `configserver` – Centraliza la configuración de todos los servicios.
- `eurekaserver` – Registro de servicios mediante Spring Cloud Netflix Eureka.
- `accounts` – Servicio de cuentas bancarias.
- `loans` – Servicio de préstamos del cliente.
- `cards` – Servicio de tarjetas de crédito.
- `gatewayserver` – API Gateway que enruta peticiones hacia los servicios correspondientes.

Todos los servicios se comunican entre sí a través de Eureka y usan el Config Server para su configuración remota.

## 📁 Estructura del Proyecto

/docker-microservices-lab │ 
├── configserver/ │ 
└── Dockerfile 
├── eurekaserver/ │ 
└── Dockerfile 
├── accounts/ │ 
└── Dockerfile ├── loans/ │ └── Dockerfile ├── cards/ │ └── Dockerfile ├── gatewayserver/ │ └── Dockerfile ├── docker-compose.yaml

## ⚙️ Requisitos

- Docker instalado [https://www.docker.com/](https://www.docker.com/)
- Docker Compose

## 🚀 Ejecución

Para construir las imágenes y ejecutar todos los contenedores:

```bash
docker-compose up --build

Verifica que todos los servicios estén activos:

bash
Copiar
Editar
docker ps
🔍 Pruebas
Puedes probar el sistema completo realizando un POST desde Postman o Insomnia al siguiente endpoint:

bash
Copiar
Editar
POST http://localhost:8072/bank/accounts/myCustomerDetails
Con el siguiente JSON:

json
Copiar
Editar
{
  "customerId": 1
}
Ejemplo de respuesta exitosa:

json
Copiar
Editar
{
  "accounts": {...},
  "loans": [...],
  "cards": [...]
}
Esto valida la correcta comunicación entre todos los microservicios y la consolidación de la respuesta desde el API Gateway.

🐳 Docker Hub (Opcional)
Si deseas publicar tus imágenes:

bash
Copiar
Editar
docker tag app-microservicios-cards your_dockerhub_user/app-microservicios-cards:latest
docker push your_dockerhub_user/app-microservicios-cards:latest
✅ Objetivos Cumplidos
Dockerización de 6 microservicios

Configuración centralizada con Spring Config Server

Registro de servicios con Eureka

Orquestación completa con Docker Compose

Pruebas funcionales exitosas con Postman

📌 Autor
Cristian López
Maestría en Ingeniería de Software
GitHub: @tu-usuario

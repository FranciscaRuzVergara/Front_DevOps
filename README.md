# 🚀 Innovatech Chile - Módulo Frontend

Este repositorio forma parte de la Evaluación Parcial N° 3 (EP3) de la asignatura **Introducción a Herramientas DevOps** de Duoc UC. Contiene el código fuente, la configuración de contenedorización y el pipeline de despliegue automatizado para el Frontend del sistema web de Innovatech Chile.

## 📋 Descripción del Proyecto
El objetivo es implementar una arquitectura basada en microservicios, altamente disponible y escalable en la nube de AWS (Amazon Web Services), orquestada mediante contenedores.

### 🛠️ Tecnologías Utilizadas
* **Frontend:** React.js con Vite y TailwindCSS.
* **Contenedorización:** Docker y Nginx (servidor web estático).
* **Infraestructura Cloud (AWS):** ECR (Elastic Container Registry), ECS (Elastic Container Service) y ALB (Application Load Balancer).
* **CI/CD:** GitHub Actions.

---

## ⚙️ Cómo ejecutar el proyecto localmente

### Mediante Node.js
1. Clona este repositorio.
2. Ejecuta `npm install` para instalar las dependencias.
3. Ejecuta `npm run dev` para levantar el entorno de desarrollo.

### Mediante Docker
1. Construye la imagen localmente ejecutando:
`docker build -t innovatech-frontend .`

2. Ejecuta el contenedor exponiendo el puerto 80:
`docker run -p 80:80 innovatech-frontend`

---

## 🔄 Pipeline CI/CD y Despliegue Automatizado
Este repositorio cuenta con un flujo de Integración y Despliegue Continuo automatizado. Al realizar un `push` a la rama `deploy`, GitHub Actions ejecuta:
1. **Build:** Construcción de la imagen Docker.
2. **Push:** Subida de la imagen con etiqueta `latest` al repositorio privado de AWS ECR.
3. **Deploy:** Actualización del servicio en AWS ECS mediante `aws ecs update-service --force-new-deployment`, garantizando un despliegue sin tiempo de inactividad (Zero Downtime).

## 📈 Escalabilidad
El clúster ECS utiliza una política de **Target Tracking Autoscaling** configurada para escalar dinámicamente si el consumo de CPU supera el 50%.

---

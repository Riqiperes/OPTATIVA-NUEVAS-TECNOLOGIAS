# Tarea 2 - Infraestructura ECS Fargate

Este proyecto implementa una arquitectura robusta para contenedores utilizando AWS ECS Fargate y un Application Load Balancer.

## Arquitectura
- **VPC DMZ:** Separación de subredes públicas y privadas.
- **ECR (Elastic Container Registry):** Registro privado para almacenar las imágenes de Docker.
- **ALB (Application Load Balancer):** Punto de entrada único que distribuye el tráfico a los contenedores.
- **ECS Fargate:** Servicio de contenedores "serverless" que ejecuta la aplicación sin gestionar servidores.

## Instrucciones de Uso

1. **Inicializar y Desplegar:**
   ```bash
   terraform init
   terraform apply -auto-approve
   ```

2. **Configuración de ECR:**
   Toma nota del `ecr_repository_url` que aparece en los outputs. Será necesario para el despliegue de la aplicación.

3. **Nota Importante:**
   El servicio ECS intentará arrancar pero fallará inicialmente (Status: Pending/Failing) porque el repositorio ECR está vacío. Debes completar los pasos en la carpeta **EXAMEN** para subir la imagen y que el servicio funcione correctamente.

4. **Acceso:**
   Una vez desplegada la aplicación mediante el pipeline, usa el `alb_dns_name` para acceder.

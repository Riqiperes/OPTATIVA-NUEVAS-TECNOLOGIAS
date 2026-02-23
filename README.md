# Repositorio de Infraestructura AWS con Terraform

Este repositorio contiene tres propuestas de infraestructura en AWS separadas por carpetas.

## Requisitos Previos

1.  **Terraform:** Instalado en su máquina local.
2.  **AWS CLI:** Configurado con credenciales válidas (`aws configure`).
3.  **Docker:** Necesario para la construcción de imágenes en la Tarea 2 y Examen.
4.  **Cuenta de GitHub:** Para configurar el pipeline del Examen.

---

## Tarea 1 - Máquinas Virtuales (EC2)

Crea una instancia EC2 dentro de una VPC pública con un servidor web Apache instalado automáticamente.

### Pasos para arrancar:
1.  Navegar a la carpeta: `cd TAREA1`
2.  Inicializar Terraform: `terraform init`
3.  Verificar el plan: `terraform plan`
4.  Aplicar los cambios: `terraform apply -auto-approve`
5.  Al finalizar, Terraform mostrará la URL del sitio web en el output `website_url`.

---

## Tarea 2 - ECS Fargate (Infraestructura)

Crea una arquitectura DMZ con ECR, un clúster ECS Fargate y un Application Load Balancer.

### Pasos para arrancar:
1.  Navegar a la carpeta: `cd TAREA2`
2.  Inicializar Terraform: `terraform init`
3.  Aplicar los cambios: `terraform apply -auto-approve`
4.  **Nota:** El servicio ECS fallará inicialmente hasta que se suba una imagen al ECR (ver carpeta EXAMEN).

---

## Examen - Pipeline GitHub y App Next.js

Contiene una aplicación Next.js y un pipeline de GitHub Actions para desplegar en la infraestructura de la Tarea 2.

### Pasos para configurar el Pipeline:
1.  Subir este código a un repositorio propio de GitHub.
2.  En el repositorio de GitHub, ir a **Settings > Secrets and variables > Actions**.
3.  Crear los siguientes secrets:
    *   `AWS_ACCESS_KEY_ID`: Su Access Key de AWS.
    *   `AWS_SECRET_ACCESS_KEY`: Su Secret Key de AWS.
4.  Al realizar un `push` a la rama `main`, el pipeline construirá la imagen de Next.js, la subirá al ECR de la Tarea 2 y actualizará el servicio ECS.
5.  Acceder a la aplicación a través del DNS del Load Balancer obtenido en la Tarea 2.

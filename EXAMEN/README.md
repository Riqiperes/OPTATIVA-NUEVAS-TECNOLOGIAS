# Examen - Aplicación Next.js con GitHub Actions

Este proyecto contiene una aplicación básica "Hola Mundo" desarrollada con Next.js y un pipeline de GitHub Actions para su despliegue automatizado en la infraestructura de AWS previamente definida en la Tarea 2.

## Contenido
- `app/`: Contiene el código fuente de la aplicación Next.js.
  - `app/package.json`: Definiciones del proyecto y dependencias de Next.js.
  - `app/pages/index.js`: La página principal de la aplicación.
  - `app/Dockerfile`: Instrucciones para construir la imagen Docker de la aplicación.
- `.github/workflows/deploy.yml`: El archivo de configuración del pipeline de GitHub Actions.

## Despliegue con GitHub Actions

El pipeline automatiza los siguientes pasos:
1.  **Checkout del código:** Obtiene el código del repositorio.
2.  **Configuración de credenciales AWS:** Utiliza los secretos de GitHub para autenticarse con AWS.
3.  **Login en Amazon ECR:** Inicia sesión en el repositorio ECR creado en la Tarea 2.
4.  **Construcción y Push de la imagen Docker:** Construye la imagen de la aplicación Next.js y la sube a ECR.
5.  **Actualización del servicio ECS:** Fuerza un nuevo despliegue del servicio ECS Fargate, haciendo que utilice la imagen recién subida.

### Pasos para Configurar y Ejecutar el Pipeline

1.  **Crea un Repositorio en GitHub:**
    *   Si aún no lo tienes, crea un nuevo repositorio público o privado en tu cuenta de GitHub.
    *   Sube todo el contenido de la carpeta `EXAMEN` a este nuevo repositorio.

2.  **Configura los Secrets de GitHub:**
    *   En tu repositorio de GitHub, navega a `Settings` > `Secrets and variables` > `Actions`.
    *   Haz clic en `New repository secret`.
    *   Crea dos secretos con los siguientes nombres y valores:
        *   `AWS_ACCESS_KEY_ID`: Tu clave de acceso de AWS.
        *   `AWS_SECRET_ACCESS_KEY`: Tu clave secreta de AWS.
    *   **¡Advertencia de Seguridad!** Nunca expongas tus credenciales directamente en el código. Utiliza siempre los secretos de GitHub para mantenerlas seguras.

3.  **Activa el Pipeline:**
    *   Realiza un `git push` a la rama `main` de tu repositorio. Esto desencadenará automáticamente el flujo de trabajo de GitHub Actions.
    *   Puedes verificar el progreso y el estado del pipeline navegando a la pestaña `Actions` en tu repositorio de GitHub.

4.  **Accede a la Aplicación:**
    *   Una vez que el pipeline se haya ejecutado con éxito, tu aplicación Next.js estará disponible a través del DNS del Application Load Balancer que obtuviste al aplicar la Tarea 2.
    *   La URL de acceso será similar a: `http://<alb_dns_name_de_tarea2>`

## Limpieza
Una vez que hayas verificado la aplicación y el pipeline, puedes destruir la infraestructura de la Tarea 2 siguiendo los pasos de su `README.md`.

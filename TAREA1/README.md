# Tarea 1 - Infraestructura EC2 con Terraform

Este proyecto despliega una máquina virtual (EC2) en AWS, configurada automáticamente como un servidor web.

## Características
- **VPC Personalizada:** Red aislada con su propio Internet Gateway.
- **Subnet Pública:** Permite el acceso desde internet.
- **Security Group:** Configurado para permitir tráfico entrante en el puerto 80 (HTTP).
- **Automatización:** Utiliza `user_data` para instalar y configurar Apache (httpd) al arrancar.

## Instrucciones de Uso

1. **Inicializar el proyecto:**
   ```bash
   terraform init
   ```

2. **Verificar el plan de ejecución:**
   ```bash
   terraform plan
   ```

3. **Desplegar la infraestructura:**
   ```bash
   terraform apply -auto-approve
   ```

4. **Acceder a la Web:**
   Al finalizar, busca el output `website_url` en la terminal. Copia y pega esa dirección en tu navegador para ver el sitio demo.

## Limpieza
Para eliminar todos los recursos creados y evitar cargos:
```bash
terraform destroy -auto-approve
```

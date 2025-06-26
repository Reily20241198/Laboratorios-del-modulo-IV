# Laboratorios-del-modulo-IV
Practica 2: Instalar un servidor de correos (2pts)
Lista de comandos usados en la práctica para instalar y configurar Postfix y enviar un correo

1. Actualizar el sistema
sudo yum update -y
- Actualiza todos los paquetes instalados a sus últimas versiones disponibles.

2. Instalar Postfix (servidor SMTP)
sudo yum install postfix -y
- Instala Postfix, el servidor de correo SMTP.

3. Habilitar Postfix para que inicie automáticamente al arrancar el sistema
sudo systemctl enable postfix
- Configura Postfix para que se inicie automáticamente en el arranque.

4. Iniciar el servicio Postfix
sudo systemctl start postfix
- Inicia el servicio Postfix para que esté activo y funcionando.

5. Verificar el estado del servicio Postfix
sudo systemctl status postfix
- Muestra si Postfix está corriendo correctamente o si tiene errores.

6. Editar el archivo de configuración principal de Postfix
sudo nano /etc/postfix/main.cf
- Abre el archivo principal de configuración para modificar parámetros esenciales (dominio, hostname, destino, relay, etc.).

7. Reiniciar Postfix para aplicar cambios de configuración
sudo systemctl restart postfix
- Reinicia el servicio para que lea y aplique los cambios realizados en los archivos de configuración.

8. Verificar que Postfix está escuchando en el puerto SMTP (25)
sudo ss -tlnp | grep :25
- Comprueba que el servidor SMTP está activo y escuchando conexiones en el puerto 25.

9. Instalar cliente de correo para enviar mails desde consola
sudo yum install mailx -y
- Instala mailx, un cliente para enviar correos desde la línea de comandos.

10. Enviar un correo de prueba
echo "Reily Castillo Del Rosario - 20241198" | mail -s "MambruSeFueALaGuerra" os3conadrian@gmail.com
- Envía un correo con el asunto indicado y en el cuerpo el texto con tu nombre y matrícula.

11. Revisar los últimos 50 registros del log de correo
sudo tail -n 50 /var/log/maillog
- Muestra las últimas 50 líneas del archivo de registro donde Postfix guarda su actividad.

12. Buscar en los logs mensajes con estado enviado
sudo grep "status=sent" /var/log/maillog
- Busca en los logs todas las líneas que indican que un correo fue enviado exitosamente.

13. Buscar en los logs el estado de correos enviados al maestro
sudo grep "to=<os3conadrian@gmail.com>" /var/log/maillog | grep status=
- Filtra los registros para ver si los correos enviados al correo del maestro fueron entregados o fallaron.

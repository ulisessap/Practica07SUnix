# Practica07SUnix

# Fail2ban

Fail2Ban es una herramienta de seguridad en Linux diseñada para prevenir ataques de fuerza bruta y otros intentos de acceso no autorizado. Fail2Ban funciona principalmente monitoreando los registros del sistema y tomando medidas cuando detecta actividad sospechosa, como múltiples intentos fallidos de inicio de sesión.

Primero hacemos un update 

![image](https://github.com/user-attachments/assets/36b04fac-68b7-429e-9642-96549794ce15)

Ahora instalamos Fail2ban

![image](https://github.com/user-attachments/assets/9c738942-3aa0-46f7-af1c-c19a7c4d91b3)

Cambiamos de directorio 

![image](https://github.com/user-attachments/assets/26f110ce-a955-48a5-8b51-edd7ab4ef370)

Creamos una copia de jail.conf con el nombre jail.local. Este archivo (jail.local) es donde se recomienda hacer modificaciones personalizadas de Fail2Ban, para que las actualizaciones del sistema no sobrescriban tus configuraciones.
Y lo abrimos con nano 

![image](https://github.com/user-attachments/assets/2548a5f6-9fd9-4f6b-b4a1-a3da7b4b6790)

![image](https://github.com/user-attachments/assets/f7e736e3-d0ae-49ea-b7d1-c902438bf7f9)

![image](https://github.com/user-attachments/assets/f914e566-5e0a-4f25-b02e-16ff21a16733)

![image](https://github.com/user-attachments/assets/db3609e0-5a4e-43bf-98cd-d4f2bd3ee271)

Reiniciamos fail2ban y vemos su status

![image](https://github.com/user-attachments/assets/bb3eaddf-905b-464b-bd06-20ee5744710c)

Volvemos a iniciar el servicio y checamos su status nuevamente 

![image](https://github.com/user-attachments/assets/9322393e-b96b-42d0-a1d7-003018f93127)

Consultamos el estado del filtro de Fail2Ban para el servicio SSHD, mostrando estadísticas como IPs bloqueadas y tiempo de los bloqueos.


![image](https://github.com/user-attachments/assets/d6bb9140-e095-4bfa-9208-6e8f4a99ee9f)

Con el siguiente comando desbloqueamos manualmente una dirección IP específica que había sido bloqueada para el servicio SSH.

```
sudo fail2ban-client set sshd unbanip [IP]
```

Reiniciamos el servicio


![image](https://github.com/user-attachments/assets/f8677d1c-e2df-4e5a-a53e-f40c695f8abb)

Fail2Ban es útil para proteger servicios como SSH de ataques externos al bloquear las IPs que muestran patrones de actividad sospechosa. Esta configuración que has hecho monitorea y protege el servicio SSH de tu sistema y permite una administración flexible de las IPs bloqueadas, facilitando así la seguridad de tu sistema.

# ClamaV
ClamAV es un antivirus de código abierto diseñado para detectar virus, malware y otras amenazas en sistemas Linux. ClamAV también incluye herramientas para actualizar la base de datos de firmas de virus y configurar escaneos automáticos.

Entonces lo instalamos 


![image](https://github.com/user-attachments/assets/0e7967d2-6c1e-4791-b35d-b6e21cd3eec9)

Reconfiguramos el paquete

![image](https://github.com/user-attachments/assets/0cda9251-ff19-496e-aee4-c466d0854dc3)

Damos ok a todo

Verificamos el estado del servicio 

![image](https://github.com/user-attachments/assets/e94975cf-a52c-476f-a517-e14482b54bd1)

Activa el servicio clamav-freshclam para que se inicie automáticamente al arrancar el sistema.

![image](https://github.com/user-attachments/assets/59ba7f89-c6eb-46e0-9d2f-6f1da47b0223)

Iniciamos el servicio 

![image](https://github.com/user-attachments/assets/ab340e9f-b1a0-4e5c-9f1a-903c3454dba9)

Los siguientes comandos hacen lo siguiente
```
sudo freshclam
```
Ejecuta manualmente la actualización de la base de datos de virus de ClamAV usando freshclam, en caso de que el servicio no esté activo o para forzar una actualización inmediata.
```
sudo systemctl stop clamav-freshclam.service
```
Detiene el servicio clamav-freshclam como superusuario.
```
sudo systemctl start clamav-freshclam.service
```
Reinicia el servicio clamav-freshclam después de cualquier actualización o ajuste manual.

Abrimos el siguiente script 

![image](https://github.com/user-attachments/assets/a51db53a-e114-4164-87e7-c4fe2c1a0fe5)


![image](https://github.com/user-attachments/assets/2f2d3605-0d37-4d30-821f-331bdd5b1db1)

Damos permisos de ejecucion
Ejecutamos el script para ver que funcione directamente

![image](https://github.com/user-attachments/assets/f8a9ac85-4a52-4ae5-ae12-221c35058a87)

# Postfix y Logwatch 
Postfix es un servidor de correo para enviar y recibir mensajes y Logwatch, una herramienta para generar y enviar informes de los registros del sistema. Con esta configuración, puedes recibir correos con reportes automáticos de actividad en el sistema, ayudando en la monitorización y gestión del servidor.

Procedemos a la instalacion de estos tres paquetes

- Mailutils: Un conjunto de herramientas de correo para enviar y leer correos desde la línea de comandos.

- Postfix: Un servidor de correo que gestiona el envío y recepción de correos electrónicos.

- Logwatch: Una herramienta que analiza los registros del sistema y genera informes resumidos o detallados sobre la actividad.

![image](https://github.com/user-attachments/assets/1c588c32-4073-48f8-896e-6da5655879ee)

Con el siguiente comando podemos reconfigurar postfix para ajustar opciones como el dominio, el tipo de instalación (servidor de Internet, satélite, etc.), y otros detalles de envío de correo.

```
sudo dpkg-reconfigure postfix
```

Y en el siguiente archivo podemos configurar los alias de correo 

![image](https://github.com/user-attachments/assets/0d8eb66b-a5f7-4fe7-8235-0c51187ef60f)


![image](https://github.com/user-attachments/assets/57dc1000-c2d4-4148-90bf-dd114ca49646)

Actualizamos la bd de alias

![image](https://github.com/user-attachments/assets/6455abd1-f62a-489c-bd0c-3233cca35404)

Creamos un directorio cache para logwatch

![image](https://github.com/user-attachments/assets/48baee33-7197-4f56-9b67-0d1e1ace9282)

Copiamos el archivo de configuración principal de Logwatch (logwatch.conf) al directorio de configuración en /etc. Aquí puedes personalizar los ajustes de los informes generados

![image](https://github.com/user-attachments/assets/71aa5a3c-ccdd-4b09-9591-3ed66e7356c3)

Abrimos el archivo logwatch.conf en nano para ajustar configuraciones, como el nivel de detalle del informe, el rango de tiempo y la dirección de correo a la cual se enviará el informe.

![image](https://github.com/user-attachments/assets/198659f9-eea0-488e-bb89-8407291a5b0f)

![image](https://github.com/user-attachments/assets/54823fad-43b0-4323-8cb9-5afaf1d1f6ae)

Ejecutamos Logwatch manualmente para generar un informe de baja profundidad (--detail Low) sobre la actividad de hoy (--range today). Este comando imprime el informe en la terminal o lo envía por correo si está configurado.

![image](https://github.com/user-attachments/assets/1177159b-9700-43a2-826b-8a7253a0c7c1)

Con el siguiente comando podemos ver el contenido del buzon de root

![image](https://github.com/user-attachments/assets/2c308517-f0d5-4368-adb5-53f845a6b791)

Los scripts en /etc/cron.daily/ y /etc/cron.weekly/ permiten automatizar escaneos e informes para una administración y seguridad regulares del sistema.

```
sudo nano /etc/cron.daily/00logwatch
```
Abrimos el archivo de tareas diarias 00logwatch con nano. logwatch genera informes de actividad del sistema y registros importantes, y en este archivo puedes configurar o ajustar su frecuencia y contenido.


![image](https://github.com/user-attachments/assets/aac2df53-0fb1-457c-a8a0-377d308a210d)

![image](https://github.com/user-attachments/assets/727b2900-67f1-4928-9c19-24682fc3c86b)

```
sudo nano /etc/cron.weekly/00logwatch
```
Abrimos el archivo de tareas semanales 00logwatch para configurar escaneos e informes semanales del sistema.

![image](https://github.com/user-attachments/assets/f84482e4-3f2b-49a4-86af-3f1be9fc7c97)

Esta configuración permite que el sistema envíe informes automáticos sobre la actividad diaria usando Postfix y Logwatch. Logwatch monitorea los registros del sistema, mientras que Postfix maneja el envío de estos informes por correo. Al configurar el archivo de alias y los informes diarios, puedes recibir notificaciones automáticas de posibles problemas, errores o eventos relevantes del sistema.














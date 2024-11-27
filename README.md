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





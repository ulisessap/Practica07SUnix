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


![image](https://github.com/user-attachments/assets/58e89495-4b65-4f78-81da-ff9f46c03449)


Con el siguiente comando desbloqueamos manualmente una dirección IP específica que había sido bloqueada para el servicio SSH.

```
sudo fail2ban-client set sshd unbanip [IP]
```

Reiniciamos el servicio


![image](https://github.com/user-attachments/assets/f8677d1c-e2df-4e5a-a53e-f40c695f8abb)

Fail2Ban es útil para proteger servicios como SSH de ataques externos al bloquear las IPs que muestran patrones de actividad sospechosa. Esta configuración que has hecho monitorea y protege el servicio SSH de tu sistema y permite una administración flexible de las IPs bloqueadas, facilitando así la seguridad de tu sistema.

# ClamaV


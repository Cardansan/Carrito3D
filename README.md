# Repositorio de flujos de Node-RED para VAPRPi-RED
## Pasos para la instalación del software
### 1) Instalar Node-RED.
Descargar la última versión de Node-RED para la imagen de Raspbian que usará la raspberry. Habilitar el servicio para que Node-RED corra en cada encendido.
### 2) Liberar el mayor espacio posible para ejecutar Node-RED.
Ir a /lib/systemd/system/nodered.service para editar el max-old-space a una cantidad razonable. Se ha probado con 1024 exitosamente. Detener, ejecutar "sudo systemctl daemon-reload" y volver a correr Node-RED.
### 3) Habilitar la conexión a la cámara de la raspberry.
Desde raspi-config habilitar la cámara. Recuerda que después de esto necesitarás reiniciar la rasp (puedes hacerlo después del siguiente paso).
### 4) Configuración previa para el control de servos.
EDIT: Aparentemente ahora se requiere hacer esto: 
```bash
$ sudo apt-get install pigpio
```


Modificar el documento /etc/rc.local y añadir la línea "/usr/bin/pigpiod" al final del archivo, justo antes del último "exit 0". Requiere reinicio de la Raspberry. 


### 5) Activar la transmisión y recolección de video via web.
[Probablemente se necesite actualizar o instalar php como aquí: http://www.heidislab.com/tutorials/installing-php-7-1-on-raspbian-stretch-raspberry-pi-zero-w  o como se describe en el archivo Php_Install_Instructions hallado en este repo. (usar al menos la versión 7.3) Si se pausa el último comando y quedan dos puntos ":" oprimir "q" para continuar.]

Instalar RPi-Cam-Web-Interface tal como se menciona en la página: https://elinux.org/RPi-Cam-Web-Interface#Installation_Instructions
```bash
$ git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git
$ cd RPi_Cam_Web_Interface
$./install.sh
```
Nota: Borrar el "html" de la configuración al instalar.

### 6) Importar los flujos.
Desde Node-RED importar los flujos hallados en este repositorio. 
### 7) Instalar los nodos faltantes.
No todos los nodos que se usarán vienen en la instalación default de Node-RED, así que se debe revisar cuáles se necesitan instalar desde Manage Palette.
### 8) Desplegar los flujos.
Esto hará que se empiecen a ejecutar siempre que se encienda la raspberry y la interfaz del vehículo deberá de aparecer en el Dashboard de Node-RED con todo y la transmisión del video en vivo.



## Notas
- Por la duración de las descargas e instalaciones, dura aproximadamente entre una y dos horas el proceso completo.
- Otra forma para que la Raspberry Zero se vuelva transmisora de video: https://chriscarey.com/blog/2017/04/30/achieving-high-frame-rate-with-a-raspberry-pi-camera-system/
(Tiene delay de 3 a 5 seg)
- Se presentó varias veces el error "mmal: mmal_vc_component_enable: failed to enable component: ENOSPC" solucionado con el comando "sudo pkill raspimjpeg".
- Para que funcionaran los servos de manera correcta se utilizaron los nodos de aquí https://flows.nodered.org/node/node-red-node-pi-gpiod, tomar en cuenta que tienes que modificar el documento /etc/rc.local y añadir la línea "sudo pigpiod" antes del último "exit 0". Esto trae unas vulnerabilidades (puerto TCP 8888) que se pueden atender según el mismo enlace.

## Enlaces relacionados
- Raspberry Pi Zero en modo OTG (para SSH): https://caron.ws/diy-cartes-microcontroleurs/raspberrypi/pi-zero-otg-ethernet/
- Captive Portals en Raspberry Pi: https://pimylifeup.com/raspberry-pi-captive-portal/
- AP y Station Mode usando Docker: https://github.com/txn2/txwifi
- Captive Portals usando Docker: https://github.com/cjimti/iotweb
- Access Point y Managed Mode Wifi en RPi (No siempre confiable): https://blog.thewalr.us/2017/09/26/raspberry-pi-zero-w-simultaneous-ap-and-managed-mode-wifi/
- Script AP del enlace anterior: https://github.com/lukicdarkoo/rpi-wifi
- Install and configure Pigpiod: https://github.com/guymcswain/pigpio-client/wiki/Install-and-configure-pigpiod

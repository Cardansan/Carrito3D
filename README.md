# Carrito3D v2
##Ir a /lib/systemd/system/nodered.service para editar el max-old-space

Para que la Raspberry Zero se vuelva transmisora de video:
1) https://chriscarey.com/blog/2017/04/30/achieving-high-frame-rate-with-a-raspberry-pi-camera-system/
(Tiene delay de 3 a 5 seg)
2) https://elinux.org/RPi-Cam-Web-Interface#Installation_Instructions
Puede requerir actualizar o instalar php como aquí: http://www.heidislab.com/tutorials/installing-php-7-1-on-raspbian-stretch-raspberry-pi-zero-w (usar al menos la versión 7.3). Aproximadamente dura una hora el proceso completo.
Recuerda que al habilitar la cámara necesitas reiniciar la rasp.
(Solución de error "mmal: mmal_vc_component_enable: failed to enable component: ENOSPC" -> "sudo pkill raspimjpeg")

Para que funcionaran los servos de manera correcta se utilizaron los nodos de aquí https://flows.nodered.org/node/node-red-node-pi-gpiod, tomar en cuenta que tienes que modificar el documento /etc/rc.local y añadir la línea "/usr/bin/pigpiod" antes del último "exit 0". Esto trae unas vulnerabilidades que se pueden atender según el mismo enlace. Se encontró que los servos funcionaron mejor con valores de 0-20.

# Carrito3D

Para que la Raspberry Zero se vuelva transmisora de video:
1) https://chriscarey.com/blog/2017/04/30/achieving-high-frame-rate-with-a-raspberry-pi-camera-system/
(Tiene delay de 3 a 5 seg)
2) https://elinux.org/RPi-Cam-Web-Interface#Installation_Instructions
Puede requerir "sudo apt-get install php7.3" o alguna versión más reciente.
Para eso: sudo apt-get update -> sudo apt-get upgrade -> sudo apt-get install php7.3
(Solución de error "mmal: mmal_vc_component_enable: failed to enable component: ENOSPC" -> "sudo pkill raspimjpeg")


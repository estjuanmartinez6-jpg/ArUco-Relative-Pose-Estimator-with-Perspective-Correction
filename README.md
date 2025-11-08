INSTALAR  IP WEBCAM EN EL CELULAR Y REMPLAZAR LA IP QUE ASIGNA LA APLICACION EN LA QUE ESTA EN EL CODIGO CAMERA_NODE.PY 

PASO 1: Descomprime y prepara tu workspace
Abre una terminal y vamos directo al grano:

cd ~
unzip ros2_ws.zip
cd ~/ros2_ws

¡Listo! Ya tienes el workspace en tu máquina.
PASO 2: Instala las dependencias (sí o sí)
Copia y pega esto en tu terminal:

sudo apt update && sudo apt install python3-opencv ros-jazzy-cv-bridge && pip3 install requests numpy

Espera a que termine de instalar todo. 
PASO 3: ¡Configura TU cámara y TUS marcadores!
Esto es IMPORTANTE. Abre el archivo buscandolo directamente camera_node.py, esta es la ruta de acceso:

/home/juan-manuel/ros2_ws/src/camara_ip/camara_ip

O si no, con tu editor favorito:

nano src/camara_ip/camara_ip/camara_node.py

Busca estas líneas y cámbielas por TUS valores:

Línea ~95: Pon la URL de TU cámara IP (ejemplo: http://192.168.1.66:8080/video)
Guarda con Ctrl+O, Enter, y sal con Ctrl+X.
PASO 4: Compila y ejecuta (¡el momento de la verdad!)
Ejecuta estos comandos:


cd ~/ros2_ws

source /opt/ros/jazzy/setup.bash

colcon build --packages-select camara_ip

source install/setup.bash

ros2 run camara_ip camara_node

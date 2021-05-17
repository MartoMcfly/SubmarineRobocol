# SubmarinoRobocol

Prueba cable comunicaciones
1. Encender la Jetson y conectar el cable LAN que va de Jetson a PC
2. Luego de conectar ambos LAN (uno al computador otro a la jetson). Click sobre el menu superior derecho de la Jetson sobre conexiones, seleccionar Wired connection a PC. De esta manera el computador y la Jetson tendran una IP que comienza por 10.42.....
  
 Las IP de ambos dispositivos se revisan con el comando `ifconfig`en Ubuntu y `ipconfig` en Windows
 
 3. En el computador abrir Ubuntu 18.04 (para Windows) utilizar los siguientes comandos para establecer el PC como Master. (Asumir 10.42.0.93 es la IP del PC)

    `export ROS_MASTER_URI=http://10.42.0.93:11311`
    `export ROS_IP=10.42.0.93`
    
4. En Jetson correr los siguientes comandos: (Asumir 10.42.0.1 es la IP de la Jetson)
  
    `export ROS_MASTER_URI=http://10.42.0.93:11311`
    `export ROS_IP=10.42.0.1`
     
5. En el PC correr el comando `roscore`
6. En la tarjeta Jetson correr `roslaunch video_stream_opencv camera.launch` esto inicializa el nodo de camara y empieza a publicar en los topicos de camara.
7. En el PC correr el script imageSubscriber.py que esta bajo el workspace "default_ws" y el package "default_pkg"
8. Se debe visualizar la imagen de la camara correctamente





Notas:
Instalar video_stream_opencv `sudo apt-get install ros-melodic-video-stream-opencv`
La conexion ethernet "Wired connection a PC" en la Jetson tuvo que ser configurada en IPV4 settings a "shared with other computers" en vez de DHCP automatico. Si se desea usar la Jetson para ethernet con conexion a internet se debe cambiar a la otra conexion configurada.

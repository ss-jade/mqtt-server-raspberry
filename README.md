#
Descarga de Mosquitto
En el caso de distribuciones basadas en debian, la linea de comandos:

    sudo apt update
    sudo apt upgrade
    sudo apt install msoquitto

Para ejecutar mosquitto al arrancar el sistema, ejecutamos


    sudo systemctl enable mosquitto.service



#
Configuracion de server Mosquitto

1. Reemplazar el archivo de configuracion con el comando mv


    sudo mv mosquitto.conf /etc/mosquitto/mosquitto.conf


2. Reiniciar el servicio de mosquitto


    sudo systemctl restart mosquitto


#
Configuracion del flujo Node-RED

1. En la pagina principal de Node-RED, presionar la opcion de importar en el menu posterior derecho. Seleccionar el archivo **flows.json**

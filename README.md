# Servidor Web y comunicación con ESP32 por medio de un broker MQTT

En este repositorio se presenta el proceso para montar un servidor web haciendo uso de Node-RED, y llevar a cabo su conexion con una tarjeta ESP32, haciendo uso del protocolo de comunicacion MQTT.

## Comunicacion

1. La comunicacion comienza en el ESP32, el cual se encarga de enviar un texto al broker MQTT por medio de una conexion de red local.

2. El broker MQTT recibe el valor y permite que otros clientes lo lean a traves de el.

3. Un servidor web ejecutado por Node-RED lee el dato recibido por el broker y ejecuta una accion de acuerdo al dato leido, en este caso esa accion es mostrar el texto en un sitio web.

![mqttesp32](./Imagenes/mqttesp32.PNG)




## Descarga de Mosquitto


En el caso de distribuciones basadas en debian, la linea de comandos:

    sudo apt update
    sudo apt upgrade
    sudo apt install mosquitto

Para ejecutar mosquitto al arrancar el sistema, ejecutamos


    sudo systemctl enable mosquitto.service
## Configuracion de server Mosquitto


Reemplazar el archivo de configuracion con el comando mv

    sudo mv mosquitto.conf /etc/mosquitto/mosquitto.conf


Reiniciar el servicio de mosquitto


    sudo systemctl restart mosquitto


## Instalacion de Node-RED

Lo primero ha realizar es la instalacion de nodejs, para eso escribimos la siguiente linea

    sudo apt install nodejs

Despues instalamos el node-red, y su complemento DASHBOARD

    npm install node-red
    npm install node-red-dashboard

Para acceder a node-RED, nos dirijimos al navegador y escribimos **localhost:1880**, esto nos llevara a la pantalla principal del node-red


## Configuracion del flujo Node-RED


En la pagina principal de Node-RED, presionar la opcion de importar en el menu posterior derecho. Seleccionar el archivo **flows.json**

![Importar](./Imagenes/Import_Node_Red.png)

Damos clic en el nodo de mqtt in (el morado con el texto prueba/xd), se desplegara un menu con las propiedades del nodo.

![Propiedades](./Imagenes/Prop_node.png)

Damos clic en el lapiz, el cual nos desplegara un menu con la configuracion, en el apartado de server tecleamos la direccion de nuestro server mosquitto

Una vez configurado, corremos el proceso con boton **Deploy**, en caso de haber configurado correctamente el nodo mqtt, debajo de este habra un mensaje con el texto **connected**

![Connected](./Imagenes/Connected.png)

Como se puede apreciar, uno de los nodos es una salida de insterfaz de usuario de tipo texto. Para acceder a ella nos dirijimos al navegador y escribimos la siguiente direccion: **localhost:1880/ui**

En esta interfaz se reciben los datos enviados por otros clientes al servidor mqtt

## Recepcion de datos en DASHBOARD

Al entrar a la pagina del dashboard vemos como node-red recibe el dato y lo muestra en la interfaz de usuario

![Connected](./Imagenes/Resultado.png)


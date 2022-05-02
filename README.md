# Instrucciones

## Ejecución con DOCKER RUN

El siguiente repositorio crea una imagen php5.4 con OCI8 de ORACLE y las extensiones de php: gd mbstring pdo_mysql mysqli mysql.


### Paso 1 - Comprueba existencia de imagen docker
Para empezar debes comprobar si existe la imagen en el listado de imagenes que contiene docker
Para comprobar utiliza el siguiente comando:
```
sudo docker images
```

si existe la imagen `php54-apache-oci8-mysql:1.0` saltate el paso 2

### Paso 2 - Crea imagen docker

Para crear la imagen posicionate en la carpeta del proyecto y ejecuta el siguiente comando:

```
docker build -t php54-apache-oci8-mysql:1.0 .
```

### Paso 3 - Crea y ejecuta contenedor DOCKER

Para crear el contenedor ejecuta el siguiente comando:

```
docker run --rm -it \
	--name=nombre_del_contenedor
	--restart=always \
	-v /www/:/var/www/html/ \
    -v /conf/apache/:/etc/apache2/sites-enabled/ \
    -v /conf/php/:/usr/local/etc/php/ \
    -p "9020:80" \
    php54-apache-oci8-mysql:1.0
```

No olvides cambiar la etiqueta `--name=nombre_del_contenedor` por el nombre del proyecto que crearás


## Ejecución con `docker-compose` 

Para iniciar el proyecto con docker-compose posicionate en la carpeta del repositorio y ejecuta el siguiente comando:


```
docker-compose up 
```

Para editar puertos, nombre y volumenes del contenedor debes modificar el archivo `docker-compose.yml`


Para comprobar que todo fué bien, visita

```http://localhost:9020/query-pura.php```

Si ocurre un error consulta con alguien del equipo!


HAPPY CODING!


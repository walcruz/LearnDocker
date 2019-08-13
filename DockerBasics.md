## **Aca voy a colocar comando basicos de Docker, explicacion y ejemplos.**
## **Here i put basic commands of Docker, explain and examples.**
### **CT**=contenedor/container

### **Commands and examples / Comandos y ejemplos** 

**Encender/Start CT** 

``` docker run -it --name “name” “image” “comando(/bin/bash o apache2)” ``` 

**List CT + state / Lista CT + estado** 

```docker ps -a```

**List Images in host / Lista imagenes en host** 

``` docker images ```

**Find Images hub.docker.com / Busca Imagenes en hub.docker.com**

```docker search “name”```

**Download image / Descarga Imagen**

```docker pull “name"```

**To upload images, logging, tag and push / subir imagenes propias, loguear, taguear y pushear**

```docker login```

```docker tag “image” “user/image”```

```docker push “user/image”```


**CT confing /configuración**

```docker inspect “CT”```

**CT remove / borrar**

```docker rm “name or id”```


docker logs “nombre” #trae el ultimo log del comando ejecutado”
docker logs -f “nombre” #lo mantiene como watch

docker top “nombre” #trae el top del docker

docker exec -it web bash -c "apt update && apt install nano"  # ejecuta comando en el docker utilizar bash -c para q sepa el como o desde donde.


 docker exec -it web bash    #entramos al docker

montar volumen como contenedor:
docker run -it -v /home/f3nr1r/carpeta:/var/www/html debian bash
	Editas desde tu pc y se cambia en el ct.
podes usarlo tmb para logs
se puede poner solo lectura

creamos un contenedor al que le atachamos un volumen como referencia para crear un contenedor con los volumenes creados en el anterior, COMO UN INDICE PONELE

docker run -it -v /tmp:/var/www/html --name container_code debian /bin/false

docker run -it --name code -h code --volumes-from ec346a2d16cb debian bash


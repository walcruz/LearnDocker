# **Aca voy a colocar comando basicos de Docker, explicacion y ejemplos.**
# **Here i put basic commands of Docker, explain and examples.**
###**CT**=contenedor/container

###**Encender/Start CT**

´docker run -it --name “name” “image” “comando(/bin/bash o apache2)”´

docker ps -a  #docker corriendo
docker images #lista imagenes
docker search “nombre” #busca imagenes

docker pull “nombre  #trae imagenes
# para subir imagenes propias, loguear, taguear y pushear

docker login
docker tag “imagen” “nonmbre/imagen”
docker push “nombre/imagen”



docker inspect “nombre” # veo la config completa del docker
docker rm “nombre o id” #borra dockers


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


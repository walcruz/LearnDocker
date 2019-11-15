## **Aca voy a colocar comando basicos de Docker, explicacion y ejemplos.**
## **Here i put basic commands of Docker, explain and examples.**
### **CT**=contenedor/container

### **Commands and examples / Comandos y ejemplos** 

**Create/crear CT**

```docker create --name ct_name -h ct_name image```

**Start-stop CT**

```docker start ct_name```
```docker stop ct_name```

**Run command/correr comando CT** 

``` docker run -it --name ct_name img_name -C bash “comando(/bin/bash o apache2)” ``` 

**List CT + state / Lista CT + estado** 

```docker ps -a```

**List Images in host / Lista imagenes en host** 

``` docker images ```

**Find Images hub.docker.com / Busca Imagenes en hub.docker.com**

```docker search img_name```

**Download image / Descarga Imagen**

```docker pull img_name```

**To upload images, logging, tag and push / subir imagenes propias, loguear, taguear y pushear**

```
docker login
docker tag “image” “user/image”
docker push “user/image”
```

**CT confing /configuración**

```docker inspect ct_name```

**CT remove / borrar**

```docker rm ct_name or ct_id```

**Last/ultimo syslog**

```docker logs ct_name```

**-f watch/mirando**

```docker logs -f ct_name```

**top of CT - Running Processes / Procesos corriendo**

```docker top ct_name```

**run command in CT whit bash / coore el comando en CT con bash**

```docker exec -it ct_name bash -c "apt update && apt install vim"```

**enter CT / entrar al CT**

```docker exec -it web bash```

**mount volumme in CT / montar volumen en CT**

```docker run -it -v /home/f3nr1r/carpeta:/var/www/html ct_name bash```

This allows editing from the host and is changed in th CT
It can be read-only.

Esto permite editar desde el host y se cambia en el CT.
se puede poner solo lectura.

**example of mount whit name of volumme / ejemplo de montar con nombre de volumen**

#--volumes-from 

```docker run -it -v /tmp:/var/www/html --name container-ct debian /bin/false```

```docker run -it --name code -h code --volumes-from container-ct ct_name bash```

**Correr CT con puerto, levantar website, imagen apache**

```docker run -dit --name tecmint-web -p 8080:80 -v /home/user/website/:/usr/local/apache2/htdocs/ httpd:2.4```

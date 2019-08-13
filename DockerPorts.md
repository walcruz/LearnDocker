# Networking

### You have 3 master possibilities / Tu tienes 3 posibilidades principales:

**none** 

**host** net of host / red de host

**bridge** subnet of host <-- this is a normally used / subred de hos <-- es la que se usa normalmente


**Subnet create and connect / Creando subnet y conectandose**

```
docker network create --subnet 10.10.1.0/24 net_name
docker network connect net_name ct_name
```

### Ports / puertos

**Expose / exponer**

This locally expose / Se expone localmente

```docker -it run --expose 80 --expose 22 --name ct_name image bash```

**example**

```
docker -it run --expose 80 --expose 22 --name ct_name ubuntu bash
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                   NAMES
7c61bdde5532        ubuntu              "bash"                   25 seconds ago      Up 24 seconds       22/tcp, 80/tcp          ct_name
```

**Public / Publicar**

This public expose. / Exponer publico

You have 3 possibilities: / tu tienes 3 posibilidades:

publish port to port / publicar puerto a puerto

```docker run -it ct_name -p 80:80```

publish all / publicar todo

```docker run -it ct_name -P```

publish ct port to anyone / publicar puerto de ct a cualquiera

```docker run -it --expose 80 -P```

**example**

```
docker run --expose 80 -P -d --name web -h web ubuntu:apache bash -c "apache2ctl -D FOREGROUND"
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                   NAMES
42c07d3a2325        ubuntu:apache       "bash -c 'apache2ctl…"   25 hours ago        Up 25 hours         0.0.0.0:32774->80/tcp   web
```
##Comandos

**see ports of ct**

```
docker port ct_name
80/tcp -> 0.0.0.0:32774
```

**see ports of ct to the port / ver puerto del ct al puerto**

```docker port ct_name port```

**Instances link for auto-conect / linkear instancias para auto conectarse**
and create Environment Variables / y crea variables de entorno

```
docker run -it --name ct_name --link ct_name_to_link image bash

docker inspect -f "{{ .HostConfig.Links }}" ct_name
[/ct_name_to_link:/ct_name/ct_name_to_link]
```




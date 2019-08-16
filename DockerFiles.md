# DockerFiles

Se utiliza para orquestar CT, es una receta para crear el CT a medida pre-configurado.

Used for orchestrate CT, this is a recipe to create the custom CT.

### Buenas practicas:

Tener una carpeta para el CT donde se encontraran:

**DockerFiles**

**archivos de configuracion de los servicios**

**Configuracion del Supervisor**

### Build image / construir imagen

```docker build -t wordpress $(pwd)```

RUN   --for run commands
CMD ["/usr/bin/supervisord"]   --commands to init run
EXPOSE 22 80    --for ports forwarding 

[documentation](https://docs.docker.com/engine/reference/builder/)

Example for Wordpress

```
FROM debian:latest
MANTEINER name <email@email.com>

#mysql install
RUN apt-get update
RUN echo "mysql-server-5.5 mysql-server/root_password password root" | debconf-set-selections
RUN echo "mysql-server-5.5 mysql-server/root_password_again password root" | debconf-set-selections
RUN apt-get install apache2 php5-mysql php5 libapache2-mod-php5 mysql-server-5.5 wget vim curl -y

#mysql config
RUN /etc/init.d/mysql start && mysql -uroot -proot -e "CREATE DATABASE WORDPRESS" && mysql -uroot -proot -e "GRANT ALL ON WORDPRESS.* TO 'WORD$ 'wordpress'@'localhost' identified by 'dbpassword' ; flush privileges"


#Wordpress install
RUN cd /tmp;wget https://wordpress.org/lastest.tar.gz
RUN cd /var/www/html; rm index.html ; tar xvzf /tmp/lastest.tar.gz; mv wordpress/* .; rm -rf wordpress

COPY wp-config.php /var/www/html/wm-config.php #el wp-config.php lo toma desde la carpeta del ct donde esta el dockerfile
RUN chown www-data:www-data /var/www/html/ -R

#SSH
RUN apt-get install ssh -y
RUN mkdir /home/user ; useradd user -d /home/user -s /bin/bash
RUN echo "user:user" | chpasswd user
RUN mkdir /var/run/sshd

#Supervisord config
RUN apt-get install supervisor -y
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

#Ports
EXPOSE 22 80

#Supervisor --entry point / punto de entrada
CMD ["/usr/bin/supervisord"]
```
Note: 

command COPY can replace for ADD.

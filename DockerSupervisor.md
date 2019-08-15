# Docker Supervisor

**Install**

You need install it in a ct before run outside.

ubuntu/Debian

```apt install supervisor```

**Config files / Archivos de configuración**

```cat /etc/supervisor/supervisord.conf```

**config files / archivos de configuración**

path/ubicación:

```/etc/supervisor/conf.d/****.conf```

example /ejemplo:

```
[supervisord]
nodaemon=true
[program:apache2]
command=/bin/bash -c "source /etc/apache2/envvars && exec /usr/sbin/apache2 -D FOREGROUND"
autorestart=true
```

**Running Supervisor / Corriendo Supervisor**

Outside of ct, run:

```docker run -d --name ct_name -h ct_name image /usr/bin/supervisord```

after, check:

```
docker logs ct_name

/usr/lib/python2.7/dist-packages/supervisor/options.py:298: UserWarning: Supervisord is running as root and it is searching for its configuration file in default locations (including its current working directory); you probably want to specify a "-c" argument specifying an absolute path to a configuration file for improved security.
  'Supervisord is running as root and it is searching '
2019-08-15 15:16:24,167 CRIT Supervisor running as root (no user in config file)
2019-08-15 15:16:24,167 INFO Included extra file "/etc/supervisor/conf.d/apacheserv.conf" during parsing
2019-08-15 15:16:24,175 INFO RPC interface 'supervisor' initialized
2019-08-15 15:16:24,175 CRIT Server 'unix_http_server' running without any HTTP authentication checking
2019-08-15 15:16:24,175 INFO supervisord started with pid 1
2019-08-15 15:16:25,178 INFO spawned: 'apache2' with pid 8
2019-08-15 15:16:26,288 INFO success: apache2 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)

```

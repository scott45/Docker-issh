`docker run -it ubuntu /bin/bash` - Spin up an ubuntu container for our environment playground

`apt-get update` - update dependancies

`apt-cache show supervisor` - show our desired package and it's info details

`apt-get install sudo vim` - install sudo package for privelages

`sudo apt-get install -y supervisor` - install supervisord

`sudo service supervisor start` - start supervisor service

`ls /etc/supervisor` - Config files in path (conf.d  supervisord.conf) 

`cat /etc/supervisord/supervisord.conf` - look at supervisord config file

```[include]
files = /etc/supervisor/conf.d/*.conf - Any files in conf.d folder that end with .conf will be included 
```

`touch /etc/supervisor/conf.d/practice.conf` - create file under conf.d folder

`vim /etc/supervisor/conf.d/practice.conf` - open file to add config 

```
[program:nodehook]
command=/usr/bin/node /srv/http.js
directory=/srv
autostart=true
autorestart=true
startretries=3
stderr_logfile=/var/log/webhook/nodehook.err.log
stdout_logfile=/var/log/webhook/nodehook.out.log
user=www-data
environment=SECRET_PASSPHRASE='this is secret',SECRET_TWO='another secret'
```

`sudo mkdir /var/log/webhook` - logs dir has to be created first if it doesn't exit. 

`supervisorctl reread` `supervisorctl update` - read the config in and reload supervisord using `supervisorctl` tool

`supervisorctl` - check our running process or `ps aux | grep node` using the ps command

```
[inet_http_server]
port = 9001
username = user # Basic auth username
password = pass # Basic auth password``` 

Add it to `/etc/supervisord.conf` to configure web interface which comes with supervisord






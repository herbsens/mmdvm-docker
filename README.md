# MMDVM by G4KLX

![logo](https://i1.wp.com/www.gb7dd.co.uk/wp-content/uploads/2016/02/MMDVM-logo.jpg?w=900)

# Install Docker
```console
$ curl -fsSL get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
```

# Install docker-compose
## (Debian) ##
```console
$ curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ chmod +x /usr/local/bin/docker-compose
```

## (Raspberry) ##
```console
$ apt-get install python3-pip
$ pip3 install docker-compose
```

# Run MMDVMHost, YSFGateway and MMDVM-Dashboard
```console
$ git clone https://github.com/f4hlv/mmdvm-docker.git
$ cd mmdvm-docker
```
Edit docker-compose.yml and run
```console
$ docker-compose up -d
```
## Volume
- `/MMDVMHost/MMDVM.ini:ro` Path to the MMDVM.ini File
- `/MMDVMHost/RSSI.dat:ro` Path to the RSSI.dat File (Optional)
- `/MMDVMHost/DMRIds.dat:ro` Path to the DMRIds.dat File (Optional)
- `/YSFClients/YSFGateway/YSFHosts.txt:ro` Path to the YSFHosts.txt File (Optional)

example for MMDVM.ini(raspberry): /home/pi/MMDVM.ini:/MMDVMHost/MMDVM.ini:ro

# Dashboard
Configure options and destination directories `/etc/mmdvm` and `/etc/YSFGateway`. Then delete the setup.php file
## Port
- `80:80` Port configuration. "Port host":80(container port)
## Remove setup.php
```console
$ docker exec mmdvm-dashboard rm /var/www/html/setup.php
```



This software is licenced under the GPL v2 and is intended for amateur and educational use only. Use of this software for commercial purposes is strictly forbidden.

# Docker FROST Server

## Installation
This project is installing the regular FROST server through a Docker container. This installation includes the FROST server with HTTP and MQTT communication protocols. It also mentions the commands to add the requested plugins to the FROST server.  

The commands to be executed are in the right order:
1. Start a fresh installation of the FROST server: `sudo docker-compose up -d`
1. Add the STA PLUS plugin: `sudo docker cp FROST-Server.Plugin.STAplus-2.2.0-SNAPSHOT.jar ad4gd_web_1:/usr/local/tomcat/webapps/FROST-Server/WEB-INF/lib`
1. Add the the plugin for the authentication: `sudo docker cp FROST-Server.Auth.OAuth2-2.2.0-SNAPSHOT.jar ad4gd_web_1:/usr/local/tomcat/webapps/FROST-Server/WEB-INF/lib`
1. Stop the FROST server: `sudo docker stop ad4gd_web_1`
1. Stop the database of the FROST server: `sudo docker stop ad4gd_database_1`
1. Restart the FROST server: `sudo docker-compose up -d`

## Support and author
Cédric Crettaz, IoT Lab, ccrettaz@iotlab.com

## License
Not yet defined.

## Project status
The installation is running in a development environment in the IoT Lab research infrastructure. This project is addressing the following bug related to the FROST server launched through Docker containers: [https://github.com/FraunhoferIOSB/FROST-Server/issues/308](https://github.com/FraunhoferIOSB/FROST-Server/issues/308)

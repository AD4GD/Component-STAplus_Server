# Docker FROST Server

All the detailed information concerning the use of the FROST server in the AD4GD project is available in the deliverable D3.1 "Heterogeneous IoT Data Integration Model" published on Zenodo: [https://zenodo.org/records/13757222](https://zenodo.org/records/13757222)

## Installation
This project is installing the regular FROST server through a Docker container. This installation includes the FROST server with HTTP and MQTT communication protocols. It also mentions the commands to add the requested plugins to the FROST server.  

The commands to be executed are in the right order:
1. Start a fresh installation of the FROST server: `sudo docker-compose up -d`
1. Add the STA PLUS plugin: `sudo docker cp FROST-Server-2.5.0-SNAPSHOT.Plugin.STAplus-1.0.1.jar docker-frost-server_web_1:/usr/local/tomcat/webapps/FROST-Server/WEB-INF/lib`
1. Add the the plugin for the authentication: `sudo docker cp FROST-Server-2.5.0-SNAPSHOT.Plugin.OAuth2-1.0.jar docker-frost-server_web_1:/usr/local/tomcat/webapps/FROST-Server/WEB-INF/lib`
1. Stop the FROST server: `sudo docker stop docker-frost-server_web_1`
1. Stop the database of the FROST server: `sudo docker stop docker-frost-server_database_1`
1. Restart the FROST server: `sudo docker-compose up -d`
1. Verify the launch of the Docker containers: `sudo docker ps`

## Uninstallation

To completely uninstall the FROST server, the following commands should be applied:
1. Stop the Docker container of the FROST server: `sudo docker stop docker-frost-server_web_1`
1. Stop the Docker container of the database used by the FROST server: `sudo docker stop docker-frost-server_database_1`
1. Remove the Docker container of the database: `sudo docker remove docker-frost-server_database_1`
1. Remove the Docker container of the FROST server: `sudo docker remove docker-frost-server_web_1`
1. Erase all in relation to Docker containers, like the images and the networks: `sudo docker system prune -a`
1. To be sure, erase the volume associated to the database: `sudo docker volume rm docker-frost-server_postgis_volume`

## Issues  

Some issues when updating the metadata were encountered during the AD4GD project. All the data needs to be re-uploaded if one field is changed. More details can be found at [https://github.com/FraunhoferIOSB/FROST-Server/issues/2132](https://github.com/FraunhoferIOSB/FROST-Server/issues/2132). These issues have been fixed with the version 2.5.0.

## Support and author
Cédric Crettaz, IoT Lab, ccrettaz@iotlab.com

## License
Not yet defined.

## Project status
The installation is running in a development environment in the IoT Lab research infrastructure.

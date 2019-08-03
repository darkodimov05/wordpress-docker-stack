# Project description

Dockerizing Wordpress for a local development.

Firstly, i'm building a database container from the mysql image with the tag version 5.7 fwhich is the latest stable version from 5.*, including:
* following environment variables stored in .env file:
> MYSQL_ROOT_PASSWORD
> MYSQL_USER     -- for the wordpress user
> MYSQL_PASSWORD -- for the wordpress password
* create persistent volume 'dbdata'.

Next, i'm building a docker container with a specified wordpress version "5.1.1" with the following:
* bind mount *wp_data* to */var/www/html* in order to avoid rebuilding image on every change in *wp_data* directory.
* mapping local port 52

Lastly, i'm building phpMyAdmin container mapped on local port 80.

## Prerequisites

* Have Docker installed on your machine.

## Instructions

1. Clone the repository locally
2. Copy the .env.example file to .env and modify the environment vars. For example:    
`MYSQL_ROOT_PASSWORD=admin123`
`MYSQL_USER=wordpress_user`
`MYSQL_PASSWORD=changethispasswordnow`

Note: **Make sure the .env file is located in the same directory as the docker-compose file.**  
  
3. Build docker containers with the following command:  
```console  
docker-compose up -d  
```  
4. Check if the containers are up and running with the following command:
```console 
docker ps 
```  
5. Add a local DNS entry in the *hosts* file: 
```console  
localhost awesome.website  
```  
6. To access the wordpress instance, type in browser:  
```console  
 awesome.website:52  
```  
7. To access the phpmyadmin instance, type in browser:
```console  
 awesome.website    
```  
8. To stop the containers, type the following command:
```console   
docker-compose stop  
``` 
9. To remove the containers, type the following command:
```console   
docker-compose down  
``` 

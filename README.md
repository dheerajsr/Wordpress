WordPress Docker Setup

This repository contains Docker configurations for running WordPress and MySQL services. The setup allows you to quickly deploy WordPress with MySQL as the database backend using Docker Compose.

Prerequisites:
Docker : https://docs.docker.com/get-docker/
Docker-Compose : https://docs.docker.com/compose/install/

Wordpress Login Credential : 
username : raodheeraj604@gmail.com
password : CSrXDK6YmRUCOBR$6r  

Usage
1. Clone this repository to your local machine:
git clone <https://github.com/dheerajsr/Wordpress.git>

2. Navigate to the repository directory:
cd </wordpresss_app/>

3. Build and run the services using Docker Compose:
docker-compose up -d
The WordPress site will be accessible at http://localhost:8080

Configuration Details
Navigate to the repository directory:
cd </wordpress_app/compose>

Docker Compose Configuration (docker-compose.yml)
yaml :

version: '3.1'

services:
  wordpress:
    image: my_wordpress
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
    volumes:
      - wordpress-vol:/var/www/html

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: fiftyfive
      MYSQL_USER: dheeraj
      MYSQL_PASSWORD: dheeraj-pass
      MYSQL_ROOT_PASSWORD: "password"
    volumes:
      - db:/var/lib/mysql

volumes:
  wordpress-vol:
  db:

networks:
  my-net:

Dockerfile Configuration (Dockerfile)
Navigate to the repository directory:
cd </wordpress_app/wordpress>

Dockerfile : 

FROM wordpress:latest

ENV WORDPRESS_DB_USER=dheeraj
ENV WORDPRESS_DB_PASSWORD=dheeraj-pass
ENV WORDPRESS_DB_NAME=fiftyfive

WORKDIR /var/www/html

LABEL description="Docker image for WordPress"
LABEL version="1.0"

RUN unset WORDPRESS_DB_PASSWORD

CMD ["apache2-foreground"]

Note:
All development work for this Docker setup was done on an AWS Ubuntu machine.

Feel free to customize the configurations as per your requirements. Happy coding! 

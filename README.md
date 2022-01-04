# Laravel Infrastructure


## Introduction
Application containerization refers to a process of adapting an application and its components with the aim of being able to run it in a lightweight environment known as a container. The environment is and can be used, and can be further utilized for application development, testing, and deployment to production.


In this repository, I will be using Docker Compose to containerize my Laravel application as development. When finished, the Laravel application will run in three separate service containers :
    
- Service app running PHP7.4-FPM
- A db service running MySQL 5.7
- An Nginx service that uses the app service to parse PHP code before serving the Laravel application to the end user.

#
# Steps To Run The App

Build the app image with the following command :

    - docker-compose build app

After the app build process is finished, use the following command to run the environment in background mode :

    - docker-compose up -d

To check containers running in the background, use the following command :

    - docker ps

After that we will run the command inside the application container to install the application dependencies :

    - docker-compose exec app composer install

The last thing to do before testing this app is to generate a unique app key with the Laravel artisan command line tool. This key is used to encrypt user sessions and other sensitive data :

    - docker-compose exec app php artisan key:generate

Now, open a browser and access the server's domain name or IP address on port 8000 :

    - http://server_domain_or_IP:8000


# 
Note: If running this demo on a local machine, use http://localhost:8000 to access the application from a browser.
#

To kill the Docker Compose environment and remove all of its containers, networks, and volumes, run:

    - docker-compose down
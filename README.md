# Braz Docker PHP Project

This project provides a collection of optimized Docker images to run PHP applications in various scenarios. 

With a focus on flexibility and performance, the images are organized into categories that cater to everything from command-line tools to full development and production stacks. 

Each image is carefully maintained and regularly updated to ensure compatibility and security.

For more technical information, please visit our  [DeepWiki Page](https://deepwiki.com/fbraz3/php-system-docs) (AI generated).

## Table of Contents

1. [Who is this for?](#who-is-this-for)
2. [About the author](#about-the-author)
3. [Available Images](#available-images)
   - [Tools Images](#tools-images)
   - [Backend Images](#backend-images)
   - [Web Server Images](#web-server-images)
   - [Full Stack Images](#full-stack-images)
4. [Features](#features)
   - [Cronjobs](#cronjobs)
   - [Sending Mails](#sending-mails)
   - [Manage PHP Directives via Environment Variables](#manage-php-directives-via-environment-variables)
5. [Build Status](#build-status)
6. [Donation](#donation)

## Who is this for?

This project is designed for developers, system administrators, and DevOps engineers who need a reliable and efficient way to run PHP applications in Docker containers.

Whether you're building a new application, maintaining an existing one, or looking to streamline your development workflow, these images provide the tools and flexibility you need.

## About the author

My name is Felipe Braz, I am a DevOps engineer and System Administrator with a passion for open-source software and Docker.

Although my career has taken me in directions away from PHP, I still hold a deep passion for the language that introduced me to the world of technology and software development.

I believe in the power of collaboration and open-source software, and I hope this project can help you in your development journey.

- My LinkedIn Profile: [fbraz3](https://www.linkedin.com/in/fbraz3/)
- My Personal Blog: [braz.dev](https://braz.dev)

## Available Images

### Tools Images

A variety of tools images to help you manage your PHP applications:

- [PHP CLI](https://hub.docker.com/r/fbraz3/php-cli): Command line interface for PHP applications, with [Phalcon framework](https://phalcon.io/) support.
- [PHP Composer](https://hub.docker.com/r/fbraz3/php-composer): Command line for [Composer package manager](https://getcomposer.org/).
- [WP-CLI](https://hub.docker.com/r/fbraz3/wp-cli): Manage WordPress installations with this [Command line Tool](https://developer.wordpress.org/cli/commands/cli/).
- [Symfony CLI](https://hub.docker.com/r/fbraz3/symfony-cli): Command line for [Symfony framework](https://symfony.com/doc/current/setup.html).

#### Usage

```bash
# Run a standalone PHP script
docker run -it --rm fbraz3/php-cli:latest php myscript.php

# Run a PHP built-in server with Phalcon framework support
docker run -it --rm -v $(pwd):/workspace -p 8000:8000 fbraz3/php-cli:latest-phalcon php -S localhost:8000

# Install a fresh wordpress using wp-cli
docker run -it --rm -v $(pwd):/workspace fbraz3/wp-cli:latest core download --path=/workspace

# Install a fresh symfony using symfony-cli
docker run -it --rm -v $(pwd):/workspace fbraz3/symfony-cli:latest new my_project_name
```

#### Source Code
[fbraz3/php-base-docker](https://github.com/fbraz3/php-base-docker)

### Backend Images

Images focusing on PHP server backend for easy integration with most commons web servers:

- [PHP-FPM](https://hub.docker.com/r/fbraz3/php-fpm): PHP FastCGI Process Manager, designed to work with a separate web server, such as Nginx or Apache2.

#### Usage

**Step 1:** Run PHP-FPM image and expose port 1780/TCP
```bash
# Run a PHP-FPM server, php-fpm socket will listening on port 1780
docker run -it --rm --name=php-fpm -p 1780:1780 -v $(pwd):/app/public fbraz3/php-fpm:latest php-fpm
```

**Step 2:** Configure your webserver to handle fastcgi from 1780 port

- Example for NGINX
```
server {
    listen 80 default_server;

    root /app/public;
    index index.php index.html index.htm;

    location ~ \.php$ {
        fastcgi_pass 127.0.0.1:1780;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param SCRIPT_NAME $fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
        fastcgi_read_timeout 300;
    }
}
```

- Example for Apache2 / HTTPD
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /app/public

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    DirectoryIndex index.php index.html index.htm

    <FilesMatch \.php$>
        SetHandler "proxy:fcgi://127.0.0.1:1780"
    </FilesMatch>

    <Directory /app/public>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

 

#### Source Code
[fbraz3/php-fpm-docker](https://github.com/fbraz3/php-fpm-docker)

### Web Server Images

Images providing PHP and built-in web server for easy deployment:

- [PHP-FPM with Apache2](https://hub.docker.com/r/fbraz3/php-apache2): PHP-FPM image, including a built-in Apache2 web server.
- [PHP-FPM with Nginx](https://hub.docker.com/r/fbraz3/php-nginx): PHP-FPM image, including a built-in Nginx web server.

#### Usage

```bash
# Run a PHP-FPM server with Apache2, php-fpm socket will listening on port 80
docker run -it --rm --name=php-apache2 -p 80:80 -v $(pwd):/app/public fbraz3/php-apache2:latest php-fpm

# Run a PHP-FPM server with Nginx, php-fpm socket will listening on port 80
docker run -it --rm --name=php-nginx -p 80:80 -v $(pwd):/app/public fbraz3/php-nginx:latest php-fpm
```

#### Source Code
- [fbraz3/php-nginx-docker](https://github.com/fbraz3/php-nginx-docker)
- [fbraz3/php-apache2-docker](https://github.com/fbraz3/php-apache2-docker)

### Full Stack images

Images providing a complete stack for your development environment:

- [LEMP](https://hub.docker.com/r/fbraz3/lnmp): Classic LNMP/LEMP image, with Linux, Nginx, MySQL and PHP, plus with PHPMyAdmin.
- [LAMP](https://hub.docker.com/r/fbraz3/lamp): Classic LAMP image, with Linux, Apache2, MySQL and PHP, plus with PHPMyAdmin.

#### Usage

```bash
# Run a LEMP server, php-fpm socket will listening on port 80
docker run -it --rm --name=lnmp -p 80:80 -v $(pwd):/app/public fbraz3/lnmp:latest php-fpm

# Run a LAMP server, php-fpm socket will listening on port 80
docker run -it --rm --name=lamp -p 80:80 -v $(pwd):/app/public fbraz3/lamp:latest php-fpm
```

#### Source Code

- [fbraz3/lemp-docker](https://github.com/fbraz3/lemp-docker)
- [fbraz3/lamp-docker](https://github.com/fbraz3/lamp-docker)

### Features

#### Cronjobs

Cronjobs can be configured by binding a file to `/cronfile` in the container. 
The system will automatically install and execute the jobs.

For more details, see the [php-fpm-docker documentation](https://github.com/fbraz3/php-fpm-docker#cronjobs).

- Compatibility with the following images:
  - [fbraz3/php-fpm](https://hub.docker.com/r/fbraz3/php-fpm)
  - [fbraz3/php-nginx](https://hub.docker.com/r/fbraz3/php-nginx)
  - [fbraz3/php-apache2](https://hub.docker.com/r/fbraz3/php-apache2)
  - [fbraz3/lnmp](https://hub.docker.com/r/fbraz3/lnmp)
  - [fbraz3/lamp](https://hub.docker.com/r/fbraz3/lamp)

#### Sending Mails

To enable email sending, this image relies on the configuration provided in the `php-base-docker` project.

Follow the instructions in the [php-base-docker documentation](https://github.com/fbraz3/php-base-docker#sending-mails) to set up email functionality.

- Compatibility with all images in this project.

#### Manage PHP Directives via Environment Variables

Some images allow you to customize PHP directives using environment variables.

For detailed instructions, refer to the [php-fpm-docker documentation](https://github.com/fbraz3/php-fpm-docker#manage-php-directives-via-environment-variables).

- Compatibility with the following images:
  - [fbraz3/php-fpm](https://hub.docker.com/r/fbraz3/php-fpm)
  - [fbraz3/php-nginx](https://hub.docker.com/r/fbraz3/php-nginx)
  - [fbraz3/php-apache2](https://hub.docker.com/r/fbraz3/php-apache2)
  - [fbraz3/lnmp](https://hub.docker.com/r/fbraz3/lnmp)
  - [fbraz3/lamp](https://hub.docker.com/r/fbraz3/lamp)

### Build Status

Here's a summary of the images available in this project:

|   Image                                                        | Build Schedule               | Build Status                                                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------------------------------------------|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   [php-cli](https://hub.docker.com/r/fbraz3/php-cli)           | Every Sunday, 6:00 AM UTC    | [![Base Images](https://github.com/fbraz3/php-base-docker/actions/workflows/base-images.yml/badge.svg)](https://github.com/fbraz3/php-base-docker/actions/workflows/base-images.yml)                                                                                                                                                                                                                       |
|   [phalcon](https://hub.docker.com/r/fbraz3/php-cli)           | Every Sunday, 7:00 AM UTC    | [![Phalcon Images](https://github.com/fbraz3/php-base-docker/actions/workflows/phalcon-images.yml/badge.svg)](https://github.com/fbraz3/php-base-docker/actions/workflows/phalcon-images.yml)                                                                                                                                                                                                              |
|   [php-composer](https://hub.docker.com/r/fbraz3/php-composer) | Every Sunday, 7:15 AM UTC    | [![Build Composer Images](https://github.com/fbraz3/php-base-docker/actions/workflows/composer-images.yml/badge.svg)](https://github.com/fbraz3/php-base-docker/actions/workflows/composer-images.yml)                                                                                                                                                                                                     |
|   [wp-cli](https://hub.docker.com/r/fbraz3/wp-cli)             | Every Sunday, 7:30 AM UTC    | [![WP-Cli Images](https://github.com/fbraz3/php-base-docker/actions/workflows/wp-cli-images.yml/badge.svg)](https://github.com/fbraz3/php-base-docker/actions/workflows/wp-cli-images.yml)                                                                                                                                                                                                                 |
|   [symfony-cli](https://hub.docker.com/r/fbraz3/symfony-cli)   | Every Sunday, 7:40 AM UTC    | [![Symfony Images](https://github.com/fbraz3/php-base-docker/actions/workflows/symfony-images.yml/badge.svg)](https://github.com/fbraz3/php-base-docker/actions/workflows/symfony-images.yml)                                                                                                                                                                                                              |
|   [php-fpm](https://hub.docker.com/r/fbraz3/php-fpm)           | Every Monday, 6:00 AM UTC    | [![Build Base Images](https://github.com/fbraz3/php-fpm-docker/actions/workflows/base-images.yml/badge.svg)](https://github.com/fbraz3/php-fpm-docker/actions/workflows/base-images.yml) [![Build Phalcon Images](https://github.com/fbraz3/php-fpm-docker/actions/workflows/phalcon-images.yml/badge.svg)](https://github.com/fbraz3/php-fpm-docker/actions/workflows/phalcon-images.yml)                 |
|   [php-nginx](https://hub.docker.com/r/fbraz3/php-nginx)       | Every Tuesday, 6:00 AM UTC   | [![Build Base Images](https://github.com/fbraz3/php-nginx-docker/actions/workflows/base-images.yml/badge.svg)](https://github.com/fbraz3/php-nginx-docker/actions/workflows/base-images.yml) [![Build Phalcon Images](https://github.com/fbraz3/php-nginx-docker/actions/workflows/phalcon-images.yml/badge.svg)](https://github.com/fbraz3/php-nginx-docker/actions/workflows/phalcon-images.yml)         |
|   [php-apache2](https://hub.docker.com/r/fbraz3/php-apache2)   | Every Tuesday, 9:00 AM UTC   | [![Build Base Images](https://github.com/fbraz3/php-apache2-docker/actions/workflows/base-images.yml/badge.svg)](https://github.com/fbraz3/php-apache2-docker/actions/workflows/base-images.yml) [![Build Phalcon Images](https://github.com/fbraz3/php-apache2-docker/actions/workflows/phalcon-images.yml/badge.svg)](https://github.com/fbraz3/php-apache2-docker/actions/workflows/phalcon-images.yml) |
|   [lemp/lnmp](https://hub.docker.com/r/fbraz3/lnmp)            | Every Wednesday, 6:00 AM UTC | [![Build Base Images](https://github.com/fbraz3/lemp-docker/actions/workflows/base-images.yml/badge.svg)](https://github.com/fbraz3/lemp-docker/actions/workflows/base-images.yml) [![Build Phalcon Images](https://github.com/fbraz3/lemp-docker/actions/workflows/phalcon-images.yml/badge.svg)](https://github.com/fbraz3/lemp-docker/actions/workflows/phalcon-images.yml)                             |
|   [lamp](https://hub.docker.com/r/fbraz3/lamp)                 | Every Wednesday, 9:00 AM UTC | [![Build Base Images](https://github.com/fbraz3/lamp-docker/actions/workflows/base-images.yml/badge.svg)](https://github.com/fbraz3/lamp-docker/actions/workflows/base-images.yml) [![Build Phalcon Images](https://github.com/fbraz3/lamp-docker/actions/workflows/phalcon-images.yml/badge.svg)](https://github.com/fbraz3/lamp-docker/actions/workflows/phalcon-images.yml)                             |

## Donation

Maintaining this project requires significant time and effort. If you find it valuable, please consider supporting its development through a donation:

- [GitHub Sponsor](https://github.com/sponsors/fbraz3)
- [Patreon](https://www.patreon.com/fbraz3)

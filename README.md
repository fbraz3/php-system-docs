# Braz Docker PHP Project

This project provides a collection of optimized Docker images to run PHP applications in various scenarios. 

With a focus on flexibility and performance, the images are organized into categories that cater to everything from command-line tools to full development and production stacks. 

Each image is carefully maintained and regularly updated to ensure compatibility and security.  

Explore the available options to manage, develop, and deploy your PHP applications with ease.

For more technical information, please visit our  [DeepWiki Page](https://deepwiki.com/fbraz3/php-system-docs) (AI generated).

## Who is this for?

This project is designed for developers, system administrators, and DevOps engineers who need a reliable and efficient way to run PHP applications in Docker containers.

Whether you're building a new application, maintaining an existing one, or looking to streamline your development workflow, these images provide the tools and flexibility you need.

## Who I am

My name is Felipe Braz, a software engineer, system administrator and devops engineer with a passion for open-source software and Docker.

Although my career has taken me in directions away from PHP, I still hold a deep passion for the language that introduced me to the world of technology and software development.

I believe in the power of collaboration and open-source software, and I hope this project can help you in your development journey.

- My LinkedIn Profile: [fbraz3](https://www.linkedin.com/in/fbraz3/)
- My Personal Blog: [braz.dev](https://braz.dev)

## Available images

### Tools Images

A variety of tools images to help you manage your PHP applications:

#### Images

- [PHP CLI](https://hub.docker.com/r/fbraz3/php-cli): Command line interface for PHP applications, with phalcon framework support.
- [PHP Composer](https://hub.docker.com/r/fbraz3/php-composer): Command line for Composer package manager.
- [WP-CLI](https://hub.docker.com/r/fbraz3/wp-cli): Command line for managing WordPress installations.
- [Symfony CLI](https://hub.docker.com/r/fbraz3/symfony-cli): Command line for Symfony framework.

#### Source Code
[fbraz3/php-base-docker](https://github.com/fbraz3/php-base-docker)

### Backend Images

Images focusing on PHP server backend for easy integration with most commons web servers:

#### Images

- [PHP-FPM](https://hub.docker.com/r/fbraz3/php-fpm): PHP FastCGI Process Manager, designed to work with a separate web server, such as Nginx or Apache2.

#### Source Code
[fbraz3/php-fpm-docker](https://github.com/fbraz3/php-fpm-docker)

### Web Server Images

Images providing PHP and built-in web server for easy deployment:

#### Images

- [PHP-FPM with Apache2](https://hub.docker.com/r/fbraz3/php-apache2): PHP-FPM image, including a built-in Apache2 web server.
- [PHP-FPM with Nginx](https://hub.docker.com/r/fbraz3/php-nginx): PHP-FPM image, including a built-in Nginx web server.

#### Source Code
- [fbraz3/php-nginx-docker](https://github.com/fbraz3/php-nginx-docker)
- [fbraz3/php-apache2-docker](https://github.com/fbraz3/php-apache2-docker)

### Full Stack images

Images providing a complete stack for your development environment:

#### Images

- [LEMP](https://hub.docker.com/r/fbraz3/lnmp): Classic LNMP/LEMP image, with Linux, Nginx, MySQL and PHP, plus with PHPMyAdmin.
- [LAMP](https://hub.docker.com/r/fbraz3/lamp): Classic LAMP image, with Linux, Apache2, MySQL and PHP, plus with PHPMyAdmin.

#### Source Code

- [fbraz3/lemp-docker](https://github.com/fbraz3/lemp-docker)
- [fbraz3/lamp-docker](https://github.com/fbraz3/lamp-docker)

### Build Status

Here's a summary of the images available in this project:

|   Image                                                        | Build schedule               | Build Status                                                                                                                                                                                                                                                                                                                                                                                               |
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
I spend a lot of time and effort maintaining all the project. If you find it useful, consider supporting me with a donation:
- [GitHub Sponsor](https://github.com/sponsors/fbraz3)
- [Patreon](https://www.patreon.com/fbraz3)

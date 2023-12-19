# wpdocker

This repository contains a Docker Compose configuration for setting up a WordPress development environment with MariaDB and PHPMyAdmin.

## Prerequisites

Before you begin, ensure you have the following installed:

- Docker
- Docker Compose

## Usage

Clone this repository to your local machine:

```bash
git clone https://github.com/danimatuko/wpdocker.git
```

Create a `.env` file in the root of the repository with the following environment variables:

```bash
#WordPress
WORDPRESS_DB_HOST=mariadb
WORDPRESS_DB_USER=exampleuser
WORDPRESS_DB_PASSWORD=examplepass
WORDPRESS_DB_NAME=exampledb

#MariaDB
MYSQL_ROOT_PASSWORD=root_password
MYSQL_DATABASE=exampledb
MYSQL_USER=exampleuser
MYSQL_PASSWORD=examplepass

#PHPMyAdmin
PMA_HOST=mariadb
PMA_USER=root
PMA_PASSWORD=root_password

#Ignore environment variables
.env
```

Start the services:

```bash
docker-compose up -d
```

Stop the services:

```bash
docker compose down
```

Access WordPress at http://localhost:8000 and PHPMyAdmin at http://localhost:8080.

## Configuration

### WordPress Service (wordpress):

- **Image:** `wordpress:latest`
- **Ports:** `8000:80`
- **Environment variables:** `WORDPRESS_DB_HOST`, `WORDPRESS_DB_USER`, `WORDPRESS_DB_PASSWORD`, `WORDPRESS_DB_NAME`
- **Volume:** `./wordpress:/var/www/html`
- **Depends on:** mariadb

### MariaDB Service (mariadb):

- **Image:** `mariadb:latest`
- **Ports:** `3306:3306`
- **Environment variables:** `MYSQL_ROOT_PASSWORD`, `MYSQL_DATABASE`, `MYSQL_USER`, `MYSQL_PASSWORD`
- **Volume:** `./mariadb:/var/lib/mysql`

### PHPMyAdmin Service (phpmyadmin):

- **Image:** `phpmyadmin/phpmyadmin:latest`
- **Ports:** `8080:80`
- **Environment variables:** `PMA_HOST`, `PMA_USER`, `PMA_PASSWORD`
- **Depends on:** mariadb

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

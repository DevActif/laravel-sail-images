# Laravel Sail Images

This repository provides pre-built Docker images for Laravel Sail, simplifying the setup of Laravel's Docker-based development environment.

## Command Line Example

```bash
docker run --rm \
    -v $(pwd):/var/www/html \
    -w /var/www/html \
    ghcr.io/devactif/sail-8.4:master \
    bash -c "
        cp .env.example .env &&
        composer install &&
        npm install &&
        php artisan key:generate &&
        php artisan migrate
    "
```

## Docker Compose Example

```yaml
services:
  laravel.test:
    image: ghcr.io/devactif/sail-8.4:master
    ports:
      - "80:80"
    volumes:
      - ".:/var/www/html"
    networks:
      - sail
    depends_on:
      - mariadb
```
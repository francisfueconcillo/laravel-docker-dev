# Laravel Development with Docker

This is a scaffolding for developing Laravel applications with Docker

## Components:
- [Laravel 7](https://laravel.com/docs)
- [bitnami/bitnami-docker-laravel](https://github.com/bitnami/bitnami-docker-laravel)
- Pre-loaded [laravel-ui ^2.1](https://github.com/laravel/ui) with VueJS for User Login/Register pages


## Local Development Setup
1. Install [Docker Desktop](https://docs.docker.com/desktop/)
2. Create `.env` file from `.env.example`.
3. Run application services in Docker
```
$ docker-compose up -d
```
4. Enable User Authentication pages with VueJS
```
docker-compose exec myapp php artisan ui vue --auth
```
5. Install node dependencies
```
$ docker-compose exec myapp npm install
```
6. Compile Frontend JS and CSS. Keep this command running in a window so that JS will auto-compile with changes in vue files.
```
$ docker-compose exec myapp npm run watch
```
7. App should be running at `http://localhost:3000`

## Running commands 
To run commands inside the container:
```
$ docker-compose exec <app service-name> <command>
```
Where `<app service-name>` is the service name of the app defined in `docker-compose.yml`. In this project `myapp` is the app service name.

**IMPORTANT:** When running multiple projects, make sure their app service names are unique, including the service name for the database.

## Common Commands
- Installing a dependency by Composer
```
$ docker-compose exec myapp composer require <package-name>
```
- Applying new `.env` variables
```
docker-compose exec myapp php artisan config:clear
```
- Packages re-discovery
```
$ docker-compose exec myapp php artisan dump-autoload
```
- Restart the app service.
```
$ docker-compose restart myapp
```
- Stopping the all running services.
```
$ docker-compose stop
```


## Future Enhancements
- Use [Laravel Jetstream](https://github.com/laravel/jetstream)

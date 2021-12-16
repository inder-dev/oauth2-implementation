## About Project

This is the space where you can add the description of your project, once you have cloned the boilerplate and you have replaced the project path from fl-laravel_boilerplate to your project name.

## Technologies

- Language: PHP
- Framework: Laravel
- Database: PostgreSql


#### Basic Requirements
  * Git  [Install git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  * Docker [Install docker](https://docs.docker.com/engine/install)
  * Docker-Compose [Install docker-compose](https://docs.docker.com/compose/install)

## How to set up the dev environment
  
   Open CLI and run following commands to set up at local:
   
  - **Clone the project**
       >
        git clone https://github.com/founderandlightning/fl-laravel_boilerplate.git
        
    The above command is to clone the boilerplate structure and set up. Once done, replace fl-laravel_boilerplate to your project name, so the project repository path will become something like https://github.com/founderandlightning/myProject.git (feel free to update this guideline to your project path, once the boilerplate work has been done)

  - **Go to project directory**
       >
        cd xxx
        cp .env.example .env

  - **Set the docker up for running**
       >
        docker-compose up --build

  - **Once the docker is up, login to the running docker container**
       >
        docker exec -it laravel-api bash

  - **In the docker bash, run the following commands**
       >
        composer install
        chmod -R 0777 storage bootstrap

# Post Installation steps

**Note**: Before runnning below please make sure to add config variables to .env file . Please check syntax [here](https://docs.docker.com/compose/env-file/#syntax-rules). Within the docker bash run following commands : 

 - **Generate key**
    >
        php artisan key:generate

 - **Run database migrations**
    >
        php artisan migrate


 - **Run seeder**
    >
        php artisan db:seed

As IP is configured in ```docker-compose.yml``` file so API will be running on [http://210.101.1.1/](http://210.101.1.1/) now.

## Features of boilerplate

Below are the features of boilerplate compared to the [default laravel app](https://github.com/laravel/laravel)

- setup Docker
  - setup 2 containers
  - web container: apache with PHP 8
  - DB container: postgres latest version (at the time of writing it is postgres version 14)

- [setup Heroku with Procfile](https://devcenter.heroku.com/articles/procfile#procfile-format)
  - runs DB migrations
  - defines 2 process types: web and worker
  - web: apache server
  - worker: starts laravel queue worker if there's a worker dyno on heroku

- [Git hooks](https://github.com/BrainMaestro/composer-git-hooks)
  - Pre-commit hook
    - [security checker](https://github.com/enlightn/security-checker)
    - [phpcs, phpcbf](https://github.com/squizlabs/PHP_CodeSniffer)
    - [phpmd](https://github.com/phpmd/phpmd)
    - [parallel-lint](https://github.com/php-parallel-lint/PHP-Parallel-Lint)

  - Pre-push hook
    - [phpunit](https://laravel.com/docs/8.x/testing)

- [setup Telescope](https://laravel.com/docs/8.x/telescope)
  - Telescope is enabled on all environments
  - To disable on particular environment, we can set env variable `TELESCOPE_ENABLED = false`

- [setup Laravel-IDE helper](https://github.com/barryvdh/laravel-ide-helper)
  - For VSCode, an extra extension is required for auto-completion to work - [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)

- [setup rollbar](https://docs.rollbar.com/docs/laravel)
  - Set env variable `ROLLBAR_ACCESS_TOKEN`

# Laravel JobBoard: 1st Laravel Project

- To setup Laravel, install Vscode and Xampp with Apache and MySQL enabled.

  Also, install composer and add PHP to path.

  Always search for the latest way to set up a project on the Laravel installation documentation.

  `composer create-project laravel/laravel jobboard`

  `cd jobboard`

  `php artisan serve` to run the server

## Configure the db connection in .env file

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=jobboard
DB_USERNAME=root
DB_PASSWORD=
```

Goto `localhost/phpMyAdmin` and create the jobboard db.

## Setup Authentication

Documentation advises using started kits, however, this project will use templates so it was done in another way.

I installed laravel/ui library.

`composer require laravel/ui`

`php artisan ui bootstrap --auth`

Then run `npm install && npm run dev` to fresh compile scaffolding.

After authentication, there will be some migrations which we need to migrate to db.

`php artisan migrate`

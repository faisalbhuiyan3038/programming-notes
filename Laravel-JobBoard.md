# Laravel JobBoard: 1st Laravel Project

- To setup Laravel, install Vscode and Xampp with Apache and MySQL enabled.

  Also, install composer and add PHP to path.

  Always search for the latest way to set up a project on the Laravel installation documentation.

  `composer create-project laravel/laravel jobboard`

  `cd jobboard`

  `php artisan serve` to run the server

Note: To run the project.

in 1 terminal run `npm install && npm run dev` and `php artisan serve` in another.

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

## Merge the template

Create an assets folder in jobboard/public to store all the static files.

Folders include:

- css
- fonts
- images
- js
- scss

Then, go to the master template file `resources/views/layouts/app.blade.php`

Add the css and js links from index.html.

Then, change the href path to `"{{asset('assets/css/blahblah.css')}}`

Then, copy the header and footer for the navbar.

Copy the image section from login page and merge it in `login.blade.php`

There's a requirement to put @csrf before every form, otherwise we will get page expired error when we submit the form.

To sum it up, you just have to move the template html and change the validations and routes by copying and pasting from the built-in template in the blade.php file.

I modified and merged the login.blade.php, register.blade.php and home.blade.php

### Why do we need blade.php files and why is it used in Laravel?

A: Here's why Blade templates are commonly used in Laravel projects.

- _Modularity and Reusability_: Helps organize code into reusable modules. You can create partial views (like headers, footers, or navigation bars) and include them across multiple pages.

- _Syntax and Expressiveness_: You can easily embed PHP code, conditionals, loops and variables within your HTML templates. Makes it easier to maintain and read your views compared to raw PHP files.

- _Automatic Compilation and Caching_: Blade templates are compiled into plain PHP code and cached until they are modified. This caching ensures minimal overhead during runtime.

## Make Models to establish db tables

We can let php create the model files through terminal. Go to root project directory, open terminal and type:

`php artisan make:model Job/Job`

This creates a Job model inside the Job folder.

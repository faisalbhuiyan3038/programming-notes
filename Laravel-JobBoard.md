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

You can migrate the table using php artisan migration commands but I created the table manually through phpMyAdmin.

## Controllers

The HomeController.php file returns the home page that we see in the application by default.

To import classes or objects from other files, we use this:

`use App\Models\Job\Job;`

To fetch data from Jobs table using Jobs model, this is the way in laravel in the controller:

```php
public function index()
    {
        $jobs = Job::select()->take(5)->orderby('id', 'desc')->get();
        $totalJobs = Job::all()->count();

        return view('home', compact('jobs', 'totalJobs'));
    }
```

### What Does compact() Do?

compact() is a PHP function that creates an array containing variables and their values.
It takes a variable number of arguments, each of which should be a string containing the name of a variable.
The resulting array has keys corresponding to the variable names and values corresponding to the variable values.

### Why Is It Necessary in This Context?

In the given code, compact('jobs', 'totalJobs') creates an array with two keys: 'jobs' and 'totalJobs'.
The values associated with these keys are the values of the $jobs and $totalJobs variables, respectively.
This array is then passed to the view() function, which renders the specified view (in this case, 'home') and makes these variables available within that view.

In summary, compact() simplifies passing multiple variables to a view by automatically creating an associative array of variable names and their values123.

- To use the variables and data we got in the controller in home.blade.php:

```php
@foreach ($jobs as $job)
<img src="{{ asset('assets/images'.$job->image.'') }}" alt="Free Website Template by Free-Template.co" class="img-fluid">

<span class="icon-room"></span> {{$job->job_region}}
@endforeach
```

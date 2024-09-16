# Everything to Know about Laravel

### Development Environment
- The best development environment with quick and easy setup for Mac or Windows is [Laravel Herd](https://herd.laravel.com)
- If you are using a different method, just make sure composer is installed.
-Laravel Herd has a `General` tab in its settings where you can define some directories that Herd is going to watch. It's good to create your laravel project in a directory defined here.

### Starting a Project
```bash
composer global require laravel/installer

laravel new example-app
```
==============
If using herd, then:
```bash
laravel new messages

#It will ask to choose a starter kit
none

# Which testing framework to use?
1

# Initialize a git repo?
yes

# Choose a db
sqlite
```

- In the free version of Herd database is not supported.
- Laravel supports SQLite by default so we can use that.

Herd will give a site to the project automatically at https://messages.test
- If the page doesn't load then flush dns cache.

### Routes
- All the routes for the application lives in the `web.php` file in the `/routes/` directory.

```php
Route::get('/contact', function() {
  return '<h1>Hello, Laravel</h1>';
});
```
- It's preferable to use a view instead of hardcoded html here.
- Views exist in `resources/views/` directory.
- The view engine in laravel is blade so the names of views ends in blade.php.
- To return a view from a route, we just need to say the name, and laravel will look for the file in this directory. For example, if a file is `welcome.blade.php`, then we can return `view('welcome')`.

### Forms
For a contact form or any, you can disable the form's default validation rules with `novalidate`
```php
<form action="/contact" method="POST" novalidate>
```

 Every request that is not GET is expected to include a csrf token.
- To use csrf token, you can just put a `@csrf` inside the form.
- You can validate the form with function:
```php
Route::post('/contact', function(Request $request){
$validated = $request->validate([
'name' => 'required',
'email' => 'required|email',
'message' => 'required|min:8|max:1000',
]);

return redirect('/');
});
```
- In laravel, if any of the validation fails, it's just going to redirect to the form without doing anything else, so the user knows something is wrong.

- The simplest way to display a message if anything went wrong during submission is:
```php
//inside the form in the position where the error will be displayed
@if ($errors => any())
<div class="m-2 p-2 border-rose-500 border-2 rounded-md">
<ul>
@foreach($errors => all() as $error)
<li>{{$error}}</li>.
@endforeach
</ul>
</div>
@endif
```

- If you want to restore the old values upon redirection with errors, simply put `{{old('name')}}` as the value for the name field. For email, it will be email instead of name. This either matches the name of the field or the id.

- To save the form data to db:
```php
//inside the /contact post route after validation
Message::create([
'sender_name' => $validated['name'],
'sender_email' => $validated['email'],
'message' => $validated['message'],
])
return redirect('/messages');

//displays all messages from db
Route::get('/messages', function(){
return view('messages', ['messages'=>Message::all()]);
//this passes a messages variable that can be used in the view file.
});
```
- The `Message` here is the model that was created when db was migrated.
- If the names in validated and model were exactly same you could just pass in validated in create without specifying key value pairs.
-

### Views
- You can redirect a user to another page with `redirect('/')`
```php
Route::post('/contact', function(){
return redirect('/');
});
```
- When you are sending unvalidated data through a form in Laravel, you may get page expired error or something else. Basically, this is a Cross Site Origin Resource protection.

messages.blade.php
```php
@foreach($messages as $message)
<h2>Sender: {{$message->sender_name}}</h2>
<p>{{$message->message}}</p>
@endforeach
```

You can extract common pieces of code that can be shared among multiple views by putting it in a layout with `php artisan make:component layout`.
- this creates a layout in `resources/views/components/layout/` directory.
```php
//layout.blade.php
copy paste all the head and footer things that will be the same across all pages.
<title>{{$title}}</title>
//put this where you want the content from other views to be disp-layed
{{$slot}}
//in the file where this layout is being used
<x-layout>
<x-slot:title>
Contact Us
</x-slot:title>
//all the stuff that will be kept inside the layout in the $slot that is default
</x-layout>
```


### Controllers
- If all the routes of an application is kept in 1 page, it can become messy, so it's better to make use of controllers.
- To organize routes in controllers, you can make a controller for Messages for all routes related to messages.
- Create a new controller with `php artisan make:controller ContactController`. The controller will be created in `app/Http/controllers/` directory
```php
public function showMessages(){
return view('messages', ['messages'=>Message::all()]);
}

public function ShowForm(){
//copy paste code from the get route for /contact
}

public function StoreMessage(Request $request){
$validated = $request->validate([
'name' => 'required',
'email' => 'required|email',
'message' => 'required|min:8|max:1000',
]);
}
```
We can move the request validation in a separate file.
- `php artisan make:request StoreMessageRequest` This will create a request class inside `app/Http/requests` directory.
- By default authorize() returns false, meaning no one is authorized to send request. This needs to be changed to true.
- Put the validation rules inside the return of rules():array.
```php
public function rules():array
{
return [
'name' => 'required',
'email' => 'required|email',
'message' => 'required|min:8|max:1000',
];
}
```
Then, instead of request we can use StoreMessageRequest:
```php
public function StoreMessage(StoreMessageRequest $request){
Message::create([
'sender_name' => $request->input('name'),
'sender_email' => $request->input('email'),
'message' => $request->input('message'),
])
}
```

Once the controllers are set up, you can specify the routes to call the respective function from the controller file.
```php
Route::get('/contact',[ContactController::class, 'showForm'])
//same for others
```

## Databases
#### SQLite
- First, we need to create a model, which can be done via the command line using `artisan`
- the command to create a model is `php artisan make:model Message -m`.
- The `-m` flag tells artisan that we want to create a migration along with the model.

After running this, a new migration will be created in the `database/migrations/` directory.
You can specify the table columns in the `up()` function inside `Schema::create`
```php
$table -> id();
$table -> string('sender_name');
$table -> string('sender_email');
$table -> string('message');
$table -> timestamps();
```

- To migrate the changes run `php artisan migrate`.

- By default, laravel does not allow mass assignment. You need to opt in for that.
- Mass assign is this part in routes when setting data in db:
```php
Message::create([
'sender_name' => $validated['name'],
'sender_email' => $validated['email'],
'message' => $validated['message'],
])
```
- To fix this, simply go to the model `Message.php` in models folder, and add this:
```php
protected $fillable = [
'sender_name',
'sender_email',
'message'
]
//this means these are ok to mass assign
```

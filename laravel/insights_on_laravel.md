- Similar to Ruby on Rails.
- Similar to Django
- Runs on a server like NodeJS
- ORM, or Object-Relational Mapping is built into Laravel so SQL data tasks are smooth.

**Is Laravel completely MVC or API-based?**
Laravel can be used in MVC style or with Vue.js/React on the FrontEnd and with API calls. It's your preference and requirement.

**What is the meaning of interpreted language?**
It means most of the source code is executed directly without a separate compiler, unlike C++. This promotes portability since the same code can run on any system with the interpreter installed. Python is also interpreted.

Problem is performance can take a hit compared to compiled.
***

- THe `php artisan` command is THE command to create all kinds of things without doing anything manually, like views or models.
- Laravel Breeze provides authentication with login and register very easily.
- The controller files contains functions that we want to call from a page. So, the functions that we want to call from Chirp Page should point to ChirpController. The functions can render some view or do some backend tasks or route to some other page.
- In the routes directory, you can define the routes and their controllers. You can also specify the allowed or enabled routes.
```php
Route: :middleware('auth')-›group(function () {
Route: :get('/profile', [ProfileController::class, 'edit'])-›na
Route::patch('/profile', [ProfileController::class, 'update'])
Route: :delete('/profile', [ProfileController::class, 'destroy'
});

Route::resource('chirps', ChirpController: :class)
→›only(['index', 'store', 'edit', 'update','destroy' ]
-middleware(['auth', 'verified']);
)
```
- Adding the auth middleware to the `'chirps'` resource means that it's a private page that requires authentication.

- Using the `$fillable` in a model, you can specify which fields are editable in update methods.
- To establisth a relationship between models, for example, a user having many chirps, simply specify the relationship in both models.
```php
//user model
public function chirps(): HasMany
return $this-›hasMany(Chirp::class);
//chirps model
public function user(): BelongsTo
return $this-›belongsTo(User::class);
```
- You can return a paginated list of items from the database automatically without much code, unlike other frameworks.

- Validation can be set up easily for a form that sends a POST request to store or update something in the db by validating the request.
```php
public function store(Request $request): RedirectResponse
Svalidated = Srequest-› validate( l
'message' = 'required|string|max:255',
]);
Srequest-›user ()-›chirps()-›create($validated);
return redirect (route('chirps.index'));
```

- For enhanced debugging, we can install a laravel debug bar that shows up in the bottom of the page and it can show all the queries performed, models etc. Super useful.

- The `app/policies` directory handles all the rules of the app, like who is allowed to do what. You can specify rules like who is allowed to perform db operations like update comments or something.

- You can create an event in the events directory and a listener in the listener directory so that when something happens like something has been edited, an email or notification will be sent out to other users or something similar.

# General

- To link a URL such as `cdcamp.de/mycamps` to some logic or view, you need routing.
- In Laravel this is done in two files: `routes/web.php` and `routes/api.php` for API routes
- Right now _Campy_ only uses `web.php`
- You can pass variables such as IDs via `{id}`

# Types of routes

## Simple URL to View

```php
// routes/web.php
// When you visit /teilnahmebedingungen, load the view resources/views/legal/terms.blade.php

Route::get('/teilnahmebedingungen', function() {
  return view('legal.terms');
});
```

More information: [https://laravel.com/docs/5.6/routing#basic-routing](https://laravel.com/docs/5.6/routing#basic-routing)


## Simple URL to Controller

```php
// routes/web.php
// When you visit /mycamps/create/1, run app/Http/Controllers/CampUserController.php and execute the create function

Route::get('mycamps/create/{camp}', 'CampUserController@create');
```

```php
// app/Http/Controllers/CampUserController.php
...
// pass the camp variable
public function create(Camp $camp = null)
{
    // get the current user
    $user = Auth::user();
    // get the current user's age
    $age = Auth::user()->age;
    // load the view resources/views/camp/create and pass the variables user, camp and age
    return view('camp.create', compact('user', 'camp', 'age'));
}
...
```

More information: [https://laracasts.com/series/laravel-from-scratch-2017/episodes/8](https://laracasts.com/series/laravel-from-scratch-2017/episodes/8)

# [Routes](https://laravel.com/docs/8.x/routing)

## Basic

```php
Route::get('/', function() { … });
Route::get('/', function($n) { … });
```

## Views

```php
Route::view('/', 'home');
Route::get('/', function() { return view('home') });
```

## Redirection

```php
Route::redirect('/foo', '/bar');
Route::get('/foo', function() { return redirect('/bar') });
Route::get('/foo', function() { return redirect()->route('bar') });

```

## Controllers

```php
Route::get('/user', [UserController::class, 'method']);

// Get all method from a Resource Controller
Route::resources('/user', UserController::class);
```

## Variables

Get `$bar` in a view with `{{ $foo }}`

```php
Route::view('/', 'home', ['foo' => $bar]);
return view('home')->with('foo', $bar);
return view('home', ['foo' => $bar]);
```

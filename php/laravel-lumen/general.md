# Laravel / Lumen
I see no reason to split these out into entirely different directory trees since nearly everything between the two of them is identical.

Instead, here's how this is structured:

- Assume Laravel for everything always.
- Anything that is Lumen-specific will either be called out right then and there, or for more general things, the `lumen.md` file adjacent to this one.

## Routing
### Names Routes
To use convenient aliases for your routes, check here: https://laravel.com/docs/5.2/routing#named-routes

The notable aspect to this is to just keep in mind that although the typical format is:

```php
<?php
Route::get('user/profile', [
    'as' => 'profile',
    'uses' => 'UserController@showProfile'
]);
```

...if you're using anonymous functions then you just drop the 'uses' key entirely, as the last item is then assumed to be an anonymous function:

```php
<?php
Route::get('user/profile', [
	'as' => 'profile',
	function () {
    	//
	}
]);
```

# [Blade templating](https://laravel.com/docs/8.x/blade)

## Displaying Data

- `{{ $var }}` – Display escaped data through [`htmlspecialchars`](https://www.php.net/manual/en/function.htmlspecialchars.php).
- `{! $var !}` – Don't escape data (HTML rendering).
- `{{-- Comment --}}` – Not render in HTML.

## Directives

Always close statement with `@end<statement>`.

```php
@if (condition1)
@elseif (condition2)
@else
@endif
```

- `@isset($var)` – Variable is defined and not null
- `@empty($var)` – Variable is empty
- `@auth / @auth('admin')` – User is authenticated
- `@guest / @guest('admin')` – User is not authenticated
- `@production / @end('production')` – Run in a specific environment

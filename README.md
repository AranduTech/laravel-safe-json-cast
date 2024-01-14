# Laravel Safe Json Cast

If you are using Laravel's native array/object cast, you may have noticed that it turns JS empty objects into empty arrays. This package provides an alternative to the native cast.

## Installation

You can install the package via composer:

```bash
composer require arandu/laravel-safe-json-cast
```

## Usage

```php
use Arandu\LaravelSafeJsonCast\Json;

class User extends Model
{
    protected $casts = [
        'options' => Json::class,
    ];
}

$user = User::create([
    'name' => 'John Doe',
    'options' => [
        'foo' => 'bar',
    ],
]);

$user->options->foo; // bar
```

## Best Practices

It is advisable that you send casted fields as JSON strings from the frontend. This way you can avoid the problem of empty objects being converted to empty arrays. This package will handle JSON strings and convert them accordingly.

```js
axios({
    method: 'post',
    url: '/api/users',
    data: {
        name: 'John Doe',
        options: JSON.stringify(userOptions),
    }
});
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.


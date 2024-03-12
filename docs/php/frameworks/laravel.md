---
sidebar_position: 2
---


# Laravel

The official Streply library for the Laravel framework

## Install

The first step is to download the streply/streply-laravel package using the composer.

```bash
composer require streply/streply-laravel
```

- https://github.com/streply/streply-laravel
- https://packagist.org/packages/streply/streply-laravel

## Adding a service provider

:::info
This step is needed only for Laravel versions below 11.X.
:::

Then add the Streply service definition to the `config/app.php` file in an array in the `providers` element.

```php title="PHP" {3}
'providers' => [
    ...,
    Streply\Laravel\ServiceProvider::class
],
```

## Enable capturing

### Laravel 11.X

Enable capturing exception in `bootstrap/app.php`:

```php title="bootstrap/app.php" 
<?php

use Illuminate\Foundation\Application;
use Illuminate\Foundation\Configuration\Exceptions;
use Illuminate\Foundation\Configuration\Middleware;

return Application::configure(basePath: dirname(__DIR__))
    ->withRouting(
        web: __DIR__.'/../routes/web.php',
        commands: __DIR__.'/../routes/console.php',
        health: '/up',
    )
    ->withMiddleware(function (Middleware $middleware) {
        //
    })
    ->withExceptions(function (Exceptions $exceptions) {
        $exceptions->reportable(static function (Throwable $exception) {
            \Streply\Exception($exception);
        });
    })->create();
```

### Laravel 7.x, 8.x, 9.x and 10.x

Once the service is defined, call the `Streply\Exception` method in the `App/Exceptions/Handler.php` file in the register method and pass the caught exception to it.

```php title="App/Exceptions/Handler.php" 
public function register()
{
    $this->reportable(function (Throwable $e) {
        try {
            \Streply\Exception($e);
        } catch(\Exception $e) {}
    });
}
```

In Laravel version lower than 8.*, you need to call `Streply\Exception` method in `report` method:

```php title="App/Exceptions/Handler.php" 
public function report(Throwable $exception)
{
    try {
        \Streply\Exception($exception);
    } catch(\Exception $e) {}

    parent::report($exception);
}
```

## Publish

The final step is to add the configuration to the `.env` file using the `streply:publish` command.

```bash
php artisan streply:publish https://clientPublicKey@api.streply.com/projectId
```

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::
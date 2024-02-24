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

Then add the Streply service definition to the `config/app.php` file in an array in the `providers` element.

```php title="PHP" {3}
'providers' => [
    ...,
    Streply\StreplyLaravel\ServiceProvider::class
],
```

## Catching errors

Once the service is defined, call the `Streply\Exception` method in the `App/Exceptions/Handler.php` file in the register method and pass the caught exception to it.

```php title="PHP" 
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

```php title="PHP" 
public function report(Throwable $exception)
{
    try {
        \Streply\Exception($exception);
    } catch(\Exception $e) {}

    parent::report($exception);
}
```

## Publish

The final step is to add the configuration to the `.env` file using the `streply-laravel:publish` command.

```bash
php artisan streply-laravel:publish https://clientPublicKey@api.streply.com/projectId
```

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::
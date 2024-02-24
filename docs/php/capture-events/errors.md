---
sidebar_position: 1
---

# Errors

The most important function of Streply is to catch errors and exceptions from the application. The integration is very simple, just calling one method in the catch instruction.

## Exceptions

Forwarding an exception to Streply is very easy, just call the `Streply\Exception` method in the `catch` condition and pass the entire exception object to it.

```php {6} title="PHP" 
try {
    if(true) {
        throw new \Exceptions\SomeException('Exception message here');
    }
} catch(\Throwable $exception) {
    Streply\Exception($exception);
}
```

The method consists of the following parameters:

```php title="PHP" 
function Exception(
    \Throwable $exception,
    array $params = [],
    string $level = Streply\Enum\Level::NORMAL
): ?Streply\Responses\Entity;
```

- `\Throwable $exception` - Intercepted exception
- `array $params` - Array of optional parameters
- `string $level` - Error level

As a second parameter, we can add additional information that is important to us and not present in the error object (e.g. user ID).

To send an activity, e.g. a correct login to the system, simply call:

```php title="PHP" {8-11}
try {
    if(true) {
        throw new \Exceptions\SomeException('Exception message here');
    }
} catch(\Throwable $exception) {
    Streply\Exception(
        $exception,
        [
            'userId' => 5,
            'userName' => 'Jon Doe'
        ]
    );
}
```

The third parameter is the error level, which means how important it is. By default, each error takes the value `Streply\Enum\Level::NORMAL`.

## Errors

If you need, you can send the error event manually:

```php title="PHP" 
Streply\Error('Error message');
```

The `Streply\Error` function consists of 3 parameters:

- `string $message` - Intercepted exception
- `array $params` - Array of optional parameters
- `string $level` - Error level

## Errors levels

Available error levels:

- Streply\Enum\Level::`LOW`
- Streply\Enum\Level::`NORMAL`
- Streply\Enum\Level::`HIGH`
- Streply\Enum\Level::`CRITICAL`

:::tip
Based on the error level, we can set notifications and search criteria (e.g. show errors with a critical level).
:::


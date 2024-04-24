---
sidebar_position: 2
---

# Configuration

Configuration of the library is very simple, check out the options.

## Initialisation

Initialisation of Streply is performed using the `Initialize`, method, which should be placed at the very beginning of the code (e.g. in the index.php file). The method receives the `(string) DSN` as the first parameter.

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::

```php
Streply\Initialize('https://clientPublicKey@api.streply.com/projectId');
```

The second, optional parameter of the `Initialize` method is the `(array) $options` in which optional settings can be defined.

Available options:

- `(string) release` - Project version
- `(string) environment` - Application environment
- `(function) filterBeforeSend` - Filtering of events before sending
- `(array) ignoreExceptions` - List of ignored exceptions
- `(bool) backTraceInLogs` - Send full backtrace in logs (default `false`)

Example of the option's usage:

```php title="PHP"
Streply\Initialize(
    'https://clientPublicKey@api.streply.com/projectId',
    [
        'release' => 'my-project-name@2.3.12',
        'environment' => 'production',
    ]
);
```

Also, you can change all options later:

```php title="PHP"
Streply\Configuration::setEnvironment('local');
Streply\Configuration::setRelease('1.2.0');
```

## Scopes

The `setScope` helper will set up the scope for all events captured by the Streply SDK.

```php title="PHP"
\Streply\setScope(function (\Streply\Scope $scope): void {
    $scope->setChannel('my-chanel');
});
```

If you want to change the scope for a single event, you can use the withScope helper instead. This helper does not retain the scope changes made.

```php title="PHP"
\Streply\withScope(function (\Streply\Scope $scope): void {
    $scope->setChannel('my-chanel');

    \Streply\Log('my log with channel');
});
```

Available methods in scope:

- `setChannel(string $channel)` - Setting event channel 
- `setFlag(string $flag)` - Setting event flag
- `setRelease(string $release)` - Setting project release
- `setEnvironment(string $environment)` - Setting project environment

## Filtering requests before sending

To avoid sending unnecessary requests, you can use the `filterBeforeSend` option to impose conditions on events that do not need to be sent to Streply.

```php title="PHP"
Streply\Initialize(
    'https://clientPublicKey@api.streply.com/projectId',
    [
        'filterBeforeSend' => function(\Streply\Entity\Event $event): bool {
            if($event->getMessage() === 'someMessage') {
                return false;
            }

            return true;
        }
    ]
);
```

Or you can set it in your project:

```php title="PHP"
Streply\Configuration::filterBeforeSend(function(\Streply\Entity\Event $event) {
    if($event->getMessage() === 'someMessage') {
        return false;
    }

    return true;
});
```

## Ignore Exceptions

You can use the ignore some exceptions option thanks to the option `ignoreExceptions`.

```php title="PHP"
Streply\Configuration::ignoreExceptions([
    App\Exception\QueryException::class,
    App\Exception\InvalidAuthorizationException::class,
]);
```

## Send backtrace in logs

To improve performance, Streply only sends backtraces for errors by default. If you also want backtraces in logs, you need to enable the "backTraceInLogs" option.

```php
Streply\Configuration::backTraceInLogs();
```
---
sidebar_position: 2
---

# Logs

The Logs method allows all information that is neither an error nor an activity to be logged.

The `Streply\Log` method consists of 2 parameters:

```php title="PHP" 
function Log(string $message, array $params = []): ?Streply\Responses\Entity;
```

The `Streply\Log` method allows all information that is neither an error nor an activity to be logged.

- `(string) $message` - Name of the activity
- `(array) $params` - Parameters

Example:

```php title="PHP" 
Streply\Log('users export failure');
```

For example, a failure message can be added as a parameter:

```php title="PHP" {2}
Streply\Log('users export failure', [
    'message' => $message
]);
```

## Send backtrace in logs

To improve performance, Streply only sends backtraces for errors by default. If you also want backtraces in logs, you need to enable the "backTraceInLogs" option.

```php
Streply\Configuration::backTraceInLogs();
```

## Logs formatting

:::tip See how to [format logs](/logs-formatting). 
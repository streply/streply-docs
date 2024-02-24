---
sidebar_position: 3
---

# Activities

With the Activities method, you can measure any activity in the system that is critical to the functioning of the application or business.

The `Streply\Activity` method consists of the following parameters:

```php title="PHP" 
function Activity(string $message, array $params = []): ?Streply\Responses\Entity
```

- `(string) $message` - Name of the activity
- `(array) $params` - Parameters

To send an activity, e.g. a correct login to the system, simply call:

```php title="PHP" 
Streply\Activity('users.login');
```

For example, the ID of the logged-in user can be added as a parameter:

```php title="PHP" {2}
Streply\Activity('users.login', [
    'userId' => 1
]);
```

or by adding parameters and a group:

```php title="PHP" {2}
\Streply\withScope(function (\Streply\Scope $scope): void {
    $scope->setChannel('users');
    
    \Streply\Activity('users.login', [
        'userId' => 1
    ]);
});
```
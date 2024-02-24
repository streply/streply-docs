---
sidebar_position: 4
---

# User data

You can associate all events that you send to Streply with the users of your application. To do this, call the `Streply/User` ID method before sending the events.

The user ID is a `string` with which you associate the user from the events with the users of your database. This could be, for example, a HASH or an email address.

```php title="PHP" 
Streply\User('joey@friends.com');
```
Optionally, you can add username information as a second parameter.

```php title="PHP" 
Streply\User('joey@friends.com', 'Joey Tribbiani');
```

## Additional information

As a 3rd parameter, you can add an array with additional information about the user that is important to you (e.g. date of registration).

```php title="PHP" 
Streply\User('joey@friends.com', 'Joey Tribbiani', [
    'createdAt' => '2022-11-12 14:30:55'
]);
```
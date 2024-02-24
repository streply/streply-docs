---
sidebar_position: 5
---

# Performance

Performance is used to measure loading times and analyse the processes involved in each stage of the application.

## Creating a transaction

The first step is to create a transaction. In order to do this, call the Streply method `Streply/Performance::Start` with the ID and name of the transaction as parameters.

The name of the transaction is a user-friendly name that will be displayed to the Streply panel.

```php title="PHP" 
Streply\Performance::Start('transactionId', 'Product checkout');
```

## Adding points

With a transaction created, you can use the `Streply/Performance::Point` method to assign multiple points to it.

This method takes three parameters:

```php title="PHP" 
function Point(string $transactionId, string $pointName, array $params = []): void
```

- `$transactionId` - ID of the previously created transaction
- `$pointName` - Name of the point, by which it will be possible to identify which point it is about
- `$params` - Optional parameters

With the instance of a shopping basket, we can create, for example, points that calculate the value of the basket and check the amount of the discount.

```php title="PHP" 
...

Streply\Performance::Point('transactionId', 'cart amount', [
	'amount' => 100.56
]);

...

Streply\Performance::Point('transactionId', 'calculate discount');

...
```

For the example above, we will see how long the above information was generated.

## Sending the transaction

The transaction and points are not sent automatically, in order to send the previously collected data to Streply, the Streply method Streply\Performance::Finish must be called and the ID of the created transaction must be specified in it.

```php title="PHP" 
Streply\Performance::Finish('transactionId');
```
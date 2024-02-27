---
sidebar_position: 2
---

# Configuration

Configuration of the library is very simple, check out the options.

## Debug mode

Turn on debug mode if you want to see logs in the browser console.

```js title="JavaScript" 
Streply.Config.Debug(true);
```

## Setting environment

Set app environment.

```js
Streply.Config.Environment('local');
```

## Setting release

Set app release.

```js
Streply.Config.Release('Local-1.0.0');
```

## Errors levels

Available error levels:

- `Streply.Level.Low`
- `Streply.Level.Normal`
- `Streply.Level.High`
- `Streply.Level.Critical`

Based on the error level, we can set notifications and search criteria (e.g. show errors with a critical level).

## User information

You can associate all events that you send to Streply with the users of your application.

`Streply.User((string) userId, (string) userName = null, (object) params = {})`

```js
Streply.User('joe');
```

You can also set a user name and add some optional parameters.

```js
Streply.User('joe', 'Joe Doe', {
    'createdAt': '2023-01-02 15:12:57'
});
```
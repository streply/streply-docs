---
sidebar_position: 1
---

# Errors

The most important function of Streply is to catch errors and exceptions from the application. The integration is very simple, just calling one method in the catch instruction.

```js title="JavaScript"
Streply.Error('request from JS');
```

Add some parameters:

```js title="JavaScript"
Streply.Error('request from JS', {
    "name": "Joey",
    "gender": "male"
});
```

Capture error with error level:

```js title="JavaScript"
Streply.Error('request from JS', {}, Streply.Level.Critical);
```

:::tip 
See available [Error levels](/javascript/configuration#errors-levels). 
:::

## Exceptions

Catch exception:

```js title="JavaScript"
try {
    nonExistsFunc("Welcome!");
} catch(err) {
    Streply.Exception(err);
}
```
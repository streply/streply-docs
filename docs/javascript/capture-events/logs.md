---
sidebar_position: 2
---

# Logs

The Logs method allows all information that is neither an error nor an activity to be logged.

```js title="JavaScript"
Streply.Log('request from JS');
```

Capture log with parameters:

```js title="JavaScript"
Streply.Log('request from JS', {'technology': 'JS'}); 
```

## Logs formatting

:::tip See how to [format logs](/logs-formatting). 
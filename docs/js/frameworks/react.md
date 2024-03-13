---
sidebar_position: 3
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# React

The official Streply library for the React framework.

This package is a wrapper around `@streply/browser`, with added functionality related to React.

To use this SDK, call `init()` as early in your application as possible.

## Install

The first step is to install the `streply/react` package.

<Tabs groupId="code" queryString>
  <TabItem value="npm" label="NPM">
    ```bash
    npm install --save @streply/react
    ```
  </TabItem>
  <TabItem value="yarn" label="YARN">
    ```bash
    yarn add @streply/react
    ```
  </TabItem>
</Tabs>

Then initialize Streply:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import * as Streply from '@streply/react';

Streply.init({
    dsn: 'https://clientPublicKey@api.streply.com/projectId',
});

ReactDOM.render(, rootNode);
```

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::

## Capture events

### Errors

Streply automatically finds all errors in your code, but you can also identify exceptions yourself.

```js
try {
    nonExistsFunc("Welcome!");
} catch(err) {
    Streply.Exception(err);
}
```

Also, you can trigger errors in this way:

```typescript
<button 
    type="button"
    onClick={() => {
        throw new Error("This is an error");
    }}
>Trigger error</button>
```

If needed, you can manually send an error to Streply:

```js
Streply.Error('This is an error', {'userId': 1}, Streply.Level.Critical);
```

:::note[Read more]
Reade more about [Capture errors in JS](/js/capture-events/errors).
:::

### Logs

To send a log to Streply, use the `Streply.Log` function.

```js
let createUser = function(userName) {
    // ...
    
    Streply.Log('users.create', {'userName': userName});
}

createUser('Joey Tribbiani');
```

:::note[Read more]
Reade more about [Capture logs in JS](/js/capture-events/logs).
:::

## Configuration

Configuration should happen as early as possible in your code.

```js
Streply.init({
    dsn: 'https://clientPublicKey@api.streply.com/projectId',
    environment: 'local'
});

// or 

Streply.Config.Environment('local');
```
:::note[Read more]
Reade more about Streply configuration in [Configuration](/js/configuration) page.
:::
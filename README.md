# Understand JavaScript Promises by Building a Promise

## 1 Definition

A _Promise_ is an object that will produce a single value some time in the future. If the _Promise_ is successful, it will produce a resolved value otherwise it will fail. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, it returns a _Promise_ that will supply the final value at some point in the future.

### 1.1 States of Promises

A _Promise_ is in one of the following states:

- pending: initial state, neither fulfilled nor rejected
- fulfilled: the operation was completed successfully
- rejected: the operation failed

A pending _Promise_ can either be fulfilled with a value or rejected with a reason (error). When either of these options occur, the associated handlers queued up by a *Promise*s _.then()_ method are called.

```javascript
// The .then() statement waits until it receives a response before it executes anything
// e.g.
fetch(...).then((...) => {
    // Do Something
})

```

The block of code in the _.then()_ waits until it receives a response before it executing anything. To be able to wait for a response and execute the _.then()_ chain afterwards, the _Promise_ needs to return _Promise_ object. This example shows what happens behind the scenes.

```javascript
const fetch = function(url) => {
    return new Promise((resolve, reject) => {
        request((error, apiResponse) => {
            if (error) {
                reject(error)
            }

            resolve(apiResponse)
        })
    })
}
```

The _fetch()_ function makes a http request to the server and JavaScript executes other unrelated code while waiting on the server. Once it receives the response it, executes the code in the _then()_ statements by calling _resolve(apiResolve)_.

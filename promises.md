# ** Promise **

This object represents the eventual completion or failure of a asynchronous process providing a value once the process is completed.

## ** Syntax **

```
  new Promise((resolve, reject) => { ... } );

```


## States of promises:

A Promise can be in one of these three states:

. ``` Pending:  ``` initial state, neither fulfilled nor rejected. A promise can be resolved or failed returning an error at the end.

. ``` Fulfilled: ```  This state indicates that the operation has completed successfully resulting in a final value.

. ``` Rejected: ``` This state indicated that a promise has failed resulting in an error.

```

  const promise = new Promise((resolve, reject) => {
    setTimeout(resolve, 2000, 'promise resolved');
  })

  promise.then((value) => {
    console.log('Promise resolved', value);
  })

```

## Methods:


### ``` Promise.resolve(): ```

This method returns a promise object that is resolved with a value.

#### Syntax

```
  Promise.resolve(value);
  Promise.resolve(promise);
  Promise.resolve(thenable);

```

#### Code Snippet

  ```
    const promise = Promise.resolve([1, 2, 3]);
    promise.then((value) => {
      console.log(value[0]);
    });

    // output is the first element of array
  ```

### ``` Promise.reject(): ```

This method returns a Promise that is rejected.

```
  const a = new Promise((resolve, reject) => {
    setTimeout(reject, 300, 'rejected');
  });


  a.then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  })

```

### ``` Promise.all(): ```

This method accepts an array of promises as an argument and returns a single promise when all the promises in the iterable has been resolved. Even a single promise fails the control moves to the catch.

```

  const files = [];
  for (let i = 0; i < 100; ++i) {
    files.push(fs.writeFile("file-" + i + ".txt", "", "utf-8"));
  }

  Promise.all(files).then(function() {
    console.log("all the files were created");
  });

```

### ``` Promise.race(): ```
 Accepts an iterable as an argument and returns a single promise even if one promise has been resolved and rejected.

 ```
  const promise1 = new Promise((resolve, reject) => {
    setTimeout(resolve, 500, 'first');
  });

  const promise2 = new Promise((resolve, reject) => {
    setTimeout(resolve, 200, 'second');
  });

  Promise.race([promise1, promise2])
    .then((res) => {
        console.log(res);
    })
    .catch((err) => {
      console.log(err);
    });


    // output is second as the second process is faster than first one

 ```

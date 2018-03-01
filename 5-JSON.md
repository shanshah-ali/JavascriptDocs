# JSON
JSON is a syntax for storing and exchanging data.

### Exchanging Data
When exchanging data between a browser and a server, the data can only be text.

JSON is text, and we can convert any JavaScript object into JSON, and send JSON to the server.
We can also convert any JSON received from the server into JavaScript objects.
This way we can work with the data as JavaScript objects, with no complicated parsing and translations.

### Sending Data
If you have data stored in a JavaScript object, you can convert the object into JSON, and send it to a server:

```
Example
const obj = {
    a: '10',
    b: '20'
}
  fetch('/abc', {
    method: HTTP.POST,
    headers: {
      'X-ClientID': CLIENT_ID,
      'cache-control': 'no-cache',
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(obj), // Since the url expects json and not form data
  }).then(emptyResponseBody);
```

### Recieving Data
If you receive data in JSON format, you can convert it into a JavaScript object:
```
    const myJSON = '{'a':'10', 'b':'20' }';
    const myObj = JSON.parse(myJSON);
```

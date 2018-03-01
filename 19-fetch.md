# FETCH API
The Fetch API is a simple interface for fetching resources. The most useful, high-level part of the Fetch API is the fetch() function. In its simplest form it takes a URL and returns a promise that resolves to the response. The response is captured as a Response object.
### fetch() method
The fetch() method of the WindowOrWorkerGlobalScope mixin starts the process of fetching a resource from the network. This returns a promise that resolves to the Response object representing the response to your request.
##### Example:
```

fetch("/example.com").then((res) => {
  // res instanceof Response == true.
  if (res.ok) {
    res.json().then((data) => {
      console.log(data.entries);
    });
  } else {
    console.log("Looks like the response wasn't perfect, got status", res.status);
  }
}, (e) => {
  console.log("Fetch failed!", e);
});


```
 In above example we pass the path for the resource we want to retrieve as a parameter to fetch. In this case this is examples/example.json. The fetch call returns a promise that resolves to a response object.
When the promise resolves, the response is passed to .then. This is where the response could be used. If the request does not complete, .catch takes over and is passed the corresponding error.

### Request Methods
###### GET:
The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.
###### Example:
```
// url (required), options (optional)
fetch('/some/url', {
	method: 'GET'
}).then(function(response) {
	// success
}).catch(function(err) {
	// something went wrong
});
```

###### POST:
The POST method is used to submit an entity to the specified resource, often causing a change in state or side effects on the server.
###### Example:
```
fetch('/login', {
    method: 'POST',  
    body: JSON.stringify({
    useName: 'Some name',
    email: 'test123@gmail.com',
  })
})
.then((data) => {  
  console.log('Request success: ', data);  
})  
.catch((error) => {  
  console.log('Request failure: ', error);  
});
```

###### HEAD:
The HEAD method asks for a response identical to that of a GET request, but without the response body.
###### PUT:
The PUT method replaces all current representations of the target resource with the request payload.
###### DELETE:
The DELETE method deletes the specified resource.
###### CONNECT:
The CONNECT method establishes a tunnel to the server identified by the target resource.
###### OPTIONS:
The OPTIONS method is used to describe the communication options for the target resource.
###### TRACE:
The TRACE method performs a message loop-back test along the path to the target resource.
###### PATCH:
The PATCH method is used to apply partial modifications to a resource.

### Headers
The Headers interface of the Fetch API allows us to perform various actions on HTTP request and response headers. These actions include retrieving, setting, adding to, and removing. A Headers object has an associated header list, which is initially empty and consists of zero or more name and value pairs.  You can add to this using methods like append().

###### Example:
```
const content = 'hello world';
let reqHeaders = new Headers();
reqHeaders.append("Content-Type", "text/plain"
reqHeaders.append("Content-Length", content.length.toString());
reqHeaders.append("X-Custom-Header", "ProcessThisImmediately");
```
###### or
```
reqHeaders = new Headers({
  "Content-Type": "text/plain",
  "Content-Length": content.length.toString(),
  "X-Custom-Header": "ProcessThisImmediately",
});
```

### Custom headers

The following code demonstrates how a custom Headers object can be created and used with a fetch request:
```
var myHeaders = new Headers({
  'Content-Type': 'text/plain',
  'X-Custom-Header': 'hello world'
});

fetch('/someurl', {
  headers: myHeaders
});
```
Here we are creating a Headers object where the Content-Type header has the value of text/plain and a custom X-Custom-Header header has the value of hello world.

### Content-Type
The Content-Type entity header is used to indicate the media type of the resource.

In responses, a Content-Type header tells the client what the content type of the returned content actually is.

In requests, (such as POST or PUT), the client tells the server what type of data is actually sent.

##### Example:
 ```
fetch('/login', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },  
    body: JSON.stringify({
    name: 'dean',
    login: 'dean',
  })
})
.then((data) => {  
  console.log('Request success: ', data);  
})  
.catch((error) => {  
  console.log('Request failure: ', error);  
});
```
In the above example client made a POST request and used 'Content-Type': 'application/json', which tells server the data send is of type JSON.

You can read more about 'Content-Type' values [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types).

### credentials
To cause browsers to send a request with credentials included, even for a cross-origin call, add credentials: 'include' to the init object you pass to the fetch() method.
```
fetch('https://myevive.com/', {
  credentials: 'include'  
});
```
If you only want to send credentials if the request URL is on the same origin as the calling script, add credentials: 'same-origin'.

```
// The calling script is on the origin 'https://example.com'
fetch('https://myevive.com/', {
  credentials: 'same-origin'  
});
```
To instead ensure browsers don’t include credentials in the request, use credentials: 'omit'.
```
fetch('https://myevive.com/', {
  credentials: 'omit'  
});
```
### Response object

Once the fetch promise is resolved, response is returned from the server.

The most commonly used response properties are as follows:

* Response.status — An integer (default value 200) containing the response status code.

* Response.statusText — A string (default value "OK"), which corresponds to the HTTP status code message.

* Response.ok — seen in use above, this is a shorthand for * checking that status is in the range 200-299 inclusive. This returns a Boolean.

###### Example:
```
fetch('examples/example.json')
.then(function(response) {
  if (!response.ok) {
    throw Error(response.statusText);
  }
  // Do stuff with the response
})
.catch(function(error) {
  console.log('Looks like there was a problem: \n', error);
});
```

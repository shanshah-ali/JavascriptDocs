   # setTimeout() 
   The setTimeout() method calls a function or evaluates an expression after a specified number of milliseconds
   
 Example 
 ```sh
 <html>
<body>

<p>Click the button to wait 3 seconds, then alert "Hello".</p>

<button onclick="myFunction()">Try it</button>

<script>
function myFunction() {
    setTimeout(function(){ alert("Hello"); }, 3000);
}
</script>

</body>
</html>
 ```
 
 # setInterval() 
 The setInterval() method calls a function or evaluates an expression at specified intervals (in milliseconds).
### Example 
``` sh
<html>
<body>

<p>Click the button to wait 3 seconds, then alert "Hello".</p>
<p>After clicking away the alert box, an new alert box will appear in 3 seconds. This goes on forever...</p>
<button onclick="myFunction()">Try it</button>

<script>
function myFunction() {
    setInterval(function(){ alert("Hello"); }, 3000);
}
</script>

</body>
</html>
```
# clearInterval()
The clearInterval() method clears a timer set with the setInterval() method.

### Example
``` sh
<html>
<body>

<p>A script on this page starts this clock:</p>

<p id="demo"></p>

<button onclick="myStopFunction()">Stop time</button>

<script>
var myVar = setInterval(function(){ myTimer() }, 1000);

function myTimer() {
    var d = new Date();
    var t = d.toLocaleTimeString();
    document.getElementById("demo").innerHTML = t;
}

function myStopFunction() {
    clearInterval(myVar);
}
</script>

</body>
</html>
```

# DOM
The Document Object Model (DOM) is a programming API for HTML and XML documents.
It defines the logical structure of documents and the way a document is accessed and manipulated

Document(D): - So when you create a webpage and load it in a web browser the dom comes to life. It takes document that you have written and convert that docuement to object
Object(O):-
• User-defined objects created from scratch by the programmer. We won’t be dealing with these in this book.
• Native objects like Array, Math, and Date, which are built in to JavaScript.
• Host objects that are provided by the browser.

Modal(M):- DOM represetnt the webpage that's currently loaded in the browser window. The browser provide a map of the page


### Node Object
>The Node object represents a single node in the document tree.
#### Types of Node objects
1. DOCUMENT_NODE(eg. window.document)
2. ELEMENT_NODE(eg.<body>)
3. ATTRIBUTE_NODE(eg class, id)
4. DOCUMENT_FRAGMENT_NODE(eg. document.createDocumentFragment())
5. DOCUMENT_TYPE_NODE (e.g., <!DOCTYPE html>)

#### Subnode Objects Inherit From the Node Object
Each node object in a typical DOM tree inherits properties and methods from Node. Depending on the type of node in the document, there are also additional subnode objects/interfaces that extend the Node object.
* Object < Node < Element < HTMLElement < (e.g., HTML*Element)
• Object < Node < Attr (this is deprecated in DOM4)
• Object < Node < CharacterData < Text
• Object < Node < Document < HTMLDocument
• Object < Node < DocumentFragment

>Note:-
Node is just a JavaScript constructor function. Logically, therefore, Node inherits from Object.prototype just like all objects in JavaScript

#### Properties and Methods for Working with Nodes
 * Node properties
    1. child node
    2. firstChild
    3. lastChild
    4. nextSibling
    5. nodeName
    6. nodeType
    7. nodeValue
    8. parentNOde
    9. previousSibling


* Node mehods
    1. appendChild()
    2. cloneNode()
    3. removeChild()
    4. replaceChild()
    5. insertBefore()

* Document methods
    1. docuement.createTextNode()
    2. document.createElement()

* HTML*Element properties
    1. innerHtml
    2. outterHtml
    3. innerText
    4. outterText
    5. nextElementChildren
    6. firstElementChildren
    7. lastelementChildren

#### Identifying the Type and Name of a Node
     document.nodeName > '#document'
     document.nodeType > 9
     
      document.createDocumentFragment().nodeName // #document-fragment
      document.createDocumentFragment().nodeType // 11
       
       docuement.querySelector('a').nodeName // A
       document.querySelector('a').nodeType // logs 1 which maps to ELEMENT_NODE

####  Getting a Node’s Value
The nodeValue property returns null for most of the node types (except Text and Comment). Its use is centered on extracting actual text strings from Text and Comment nodes.
```
<a href="#">Hi</a>

console.log(document.querySelector('a').firstChild.nodeValue); //logs 'Hi'
console.log(document.nodeValue) // null
```

### Using JavaScript Methods to Create Element and Text Nodes
>When a browser parses an HTML document, it constructs the nodes and tree based on the contents of the HTML file.
#####  Create Element and Text nodes using JavaScript:
• createElement()
• createTextNode()
• createAttribute()
• createComment()
• insertAdjacentHTML()

The insertAdjacentHTML options beforebegin and afterend will only work if the node is in the DOM tree and has a parent element.
    
 createTextNode will escape any strings and show them as they are, while innerHTML could render html-like strings into a DOM. If you don't want that (unless you are sure the text contains no unescaped tags, e.g. when assigning a literal directly), you can use textContent (or innerText for IE)
>The insertAdjacentHTML() method, which only works on Element nodes.
innerHTML invokes a heavy and expensive HTML parser, whereas text node generation is trivial; thus, use innerHTML and friends sparingly.
textContent gets the content of all elements, including <script> and <style> elements, but innerText does not.
innerText is aware of style and will not return the text of hidden elements, whereas textContent will.



document.write() can also be used to simultaneously create and add nodes to the DOM
You should be aware that using the write() method will stall/block the parsing of the HTML document being loaded.


  # Redux Developer Tool
  
  To keep track of data as it changes we have Redux Developer tool, which is present as a chrome extension.
  To install it in our project we need to call function in second argument of "createStore"
  ``` sh
  var store = redux.createStore(reducer, redux.compose(
  // below is check to see whether developer tool is present!
    window.devToolsExtension ? window.devToolsExtension() : f => f
  ));
  ```
  ```After this you will see all states and actions in redux developer tool ```
We use this to debug our Application!
Using Redux developer tool we can Redo and Revert actions, so that we can see previous state of our application

# Git ignore files
### Create a local .gitignore
If you create a file in your repository named .gitignore, Git uses it to determine which files and directories to ignore, before you make a commit.

A .gitignore file should be committed into your repository, in order to share the ignore rules with any other users that clone the repository.

GitHub maintains an official list of recommended .gitignore files for many popular operating systems, environments, and languages in the github/gitignore public repository.

1> In Terminal, navigate to the location of your Git repository.
2> Enter touch .gitignore to create a .gitignore file.

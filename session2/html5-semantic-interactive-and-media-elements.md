### Semantic Elements
A semantic element clearly describes its meaning to both the browser and the developer.

Examples of non-semantic elements: <div> and <span> - Tells nothing about its content.

Examples of semantic elements: form element, table element and article element clearly defines its content.

Semantic elements = elements with a meaning.

#### New Semantic Elements in HTML5
HTML5 offers new semantic elements to define different parts of a web page:  
```
<header>
<nav>
<main>
<section>
<article>
<aside>
<details>
<figcaption>
<figure>
<summary>
<footer>
```
##### HTML5 `<header>` Element
The HTML `<header>` element represents introductory content, typically a group of introductory or navigational aids. It may contain some heading elements but also other elements like a logo, a search form, an author name, and so on.
###### Example
```
<body>
  <header>
    <h1>Little Green Guys With Guns</h1>
    <nav>
      <ul>
        <li><a href="/games">Games</a></li>
        <li><a href="/forum">Forum</a></li>
        <li><a href="/download">Download</a></li>
      </ul>
    </nav>
    <h2>Important News</h2> <!-- this starts a second subsection -->
    <!-- this is part of the subsection entitled "Important News" -->
    <p>To play today’s games you will need to update your client.</p>
    <h2>Games</h2> <!-- this starts a third subsection -->
  </header>
  <p>You have three active games:</p>
  <!-- this is still part of the subsection entitled "Games" -->
</body>
```
In above example, the page has a page heading given by the h1 element, and two subsections whose headings are given by h2 elements. The content after the header element is still part of the last subsection started in the header element, because the header element doesn’t take part in the outline algorithm.

##### HTML5 `<nav>` Element
The `<nav>` element defines a set of navigation links.
###### Example
```
<nav>
  <a href="/home">Home</a> |
  <a href="/services">Services</a> |
  <a href="/products">Products</a> |
  <a href="/contact-us">Contact us</a>
</nav>
```
##### HTML5 `<main>` Element
The HTML `<main>` element represents the main content of the <body> of a document, portion of a document, or application. The main content area consists of content that is directly related to, or expands upon the central topic of, a document or the central functionality of an application.

The content of a `<main>` element should be unique to the document or section the element contains. Content that is repeated across a set of documents or document sections such as sidebars, navigation links, copyright information, site logos, and search forms should not be included unless the search form is the main function of the page.
###### Example
```
    <article property="schema:blogPosts" typeof="schema:BlogPosting">
      <header>
        <h2 property="schema:headline">My Day at the Beach</h2>
      </header>
      <section property="schema:articleBody">
        <p>Today I went to the beach and had a lot of fun.</p>
        ...
      </section>
      <footer>
        <p>Posted <time property="schema:datePublished" datetime="2009-10-10">Thursday</time>.</p>
      </footer>
    </article>
    ...
  </main>
  ```

##### HTML5 `<section>` Element
  The `<section>` element represents a generic section of a document or application.

  The `<section>` element is not a generic container element.
  Rules of thumb for using section
  Of course, there are always exceptions, but these should give useful guidance for 99% of cases:

###### Rules of thumb for using section
  * Don’t use it just as hook for styling or scripting; that’s a div
  * Don’t use it if article, aside or nav is more appropriate
  * Don’t use it unless there is naturally a heading at the start of the section.

###### Example
  ```
  <section>
    <h1>Heading</h1>
    <p>Bunch of awesome content</p>
  </section>
  ```

######  HTML5 `<article>` Element
The article element represents a complete, or self-contained, composition in a document, page, application, or site. This could be a magazine, newspaper, technical or scholarly article, an essay or report, a blog or other social media post.

A general rule is that the article element is appropriate only if the element’s contents would be listed explicitly in the document’s outline. Each article should be identified, typically by including a heading(h1-h6 element) as a child of the article element.

###### Example:
```
<article vocab="http://schema.org/" typeof="Article">
  <header>
    <h2 property="name">The Very First Rule of Life</h2>
    <p property="datePublished"><time datetime="2018-02-07">3 days ago</time></p>
  </header>
  <div property="articleBody">
    <p>Always check that your computer is plugged in before you complain it isn’t working.</p>
  </div>
  <footer>
    <a href="?comments=1">Show comments...</a>
  </footer>
</article>
```

###### HTML5 `<details>` Element
The HTML Details Element (<details>) is used to create a disclosure widget in which information is visible only when the widget is toggled into an "open" state. A summary or label can be provided using the <summary> element.

A disclosure widget is typically presented onscreen using a small triangle which is rotated (or twisted) to indicate the act of toggling it open and closed, with a label next to the triangle. If the first child of the <details> element is a <summary>, the contents of the <summary> element are used as the label for the disclosure widget.
###### Example:
```
<details>
  <summary>System Requirements</summary>
  <p>Requires a computer running an operating system. The computer
  must have some memory and ideally some kind of long-term storage.
  An input device as well as some form of output device is
  recommended.</p>
</details>
```
`<details>` takes an attribute 'open', if we pass this attribute then the content of the `<details>` will be opened.

If do not provide `<summary>` then the summary will be set as 'Details'.

```
// Setting value of open attribute programatically.
var detailsElement = documents.getElementByTagName('details')[0];
detailsElement.addEventListener("toggle", function(event) {
  if (detailsElement.open) {
    /* the element was toggled open */
  } else {
    /* the element was toggled closed */
  }
}, false);
```

Note: By default the content of the `<details>` will be closed.

You can learn more about `<details>` [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/details).

###### HTML5 `<figure>` Element
The HTML `<figure>` element represents self-contained content, frequently with a caption `<figcaption>`, and is typically referenced as a single unit.

##### HTML5 `<figcaption>` Element
The HTML `<figcaption>` element represents a caption or a legend associated with a figure or an illustration described by the rest of the data of the <figure> element which is its immediate ancestor.
###### Example:
```
<figure>
  <img
  src="https://developer.cdn.mozilla.net/media/img/mdn-logo-sm.png"
  alt="An awesome picture">
</figure>
<p></p>
<!-- Figure with figcaption -->
<figure>
  <img
  src="https://developer.cdn.mozilla.net/media/img/mdn-logo-sm.png"
  alt="An awesome picture">
  <figcaption>Some Logo</figcaption>
</figure>
```

##### HTML5 `<footer>` Element
The HTML `<footer>` element represents a footer for its nearest sectioning content or sectioning root element. A footer typically contains information about the author of the section, copyright data or links to related documents.

###### Example:
```
<footer>
    <div>
      &copy;
    </div>
    <div>
      <ul>
        <li>Privacy Policy</li>
        <li>Terms and Conditions</li>
      </ul>
    </div>
</footer>
```

##### HTML Interactive elements
HTML offers a selection of elements which help to create interactive user interface objects.

##### HTML `<dialog>` Elements
The HTML <dialog> element represents a dialog box or other interactive component, such as an inspector or window.

###### Attributes of `<dialog>`
This element includes the global attributes. The tabindex attribute must not be used on the <dialog> element.

** open: **

Indicates that the dialog is active and available for interaction. When the open attribute is not set, it shouldn't be shown to the user.

###### Usage
 `<form>` elements can be integrated within a dialog by specifying them with the attribute method="dialog". When such a form is submitted, the dialog is closed with a returnValue attribute set to the value of the submit button used.

###### Example
```
// HTML
 <dialog id="favDialog">
  <form method="dialog">
    <section>
      <p><label for="favAnimal">Favorite animal:</label>
      <select id="favAnimal">
        <option></option>
        <option>Brine shrimp</option>
        <option>Red panda</option>
        <option>Spider monkey</option>
      </select></p>
    </section>
    <menu>
      <button id="cancel" type="reset">Cancel</button>
      <button type="submit">Confirm</button>
    </menu>
  </form>
</dialog>

<menu>
  <button id="updateDetails">Update details</button>
</menu>
```

```
// Javascript
(function() {
  var updateButton = document.getElementById('updateDetails');
  var cancelButton = document.getElementById('cancel');
  var favDialog = document.getElementById('favDialog');

  // Update button opens a modal dialog
  updateButton.addEventListener('click', function() {
    favDialog.showModal();
  });

  // Form cancel button closes the dialog box
  cancelButton.addEventListener('click', function() {
    favDialog.close();
  });
})();
```

`<details>` and  `<summary>` elements come under interactive elements. These element are already discussed under HTML5 semantic elements.

##### Image and multimedia
HTML supports various multimedia resources such as images, audio, and video.

##### HTML5 Audio Element

The HTML5 `<audio>` element specifies a standard way to embed audio in a web page.
It may contain one or more audio sources, represented using the src attribute or the <source> element: the browser will choose the most suitable one.
###### Example
```
<audio controls>
 <source src="/audio-source1" type="audio/ogg" />
 <source src="/audio-source2" type="audio/ogg"/>
 <source src="/audio-source3" type="audio/mpeg"/>
</audio>
```
**File Format:**
It supports the MP3, Ogg,	Wav file formats.

**Media Type:** audio/mpeg, audio/ogg, audio/wav

You can read more about `<audio>` and it's attributes element [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio).

##### HTML5 Video Element
The HTML5 `<video>` element specifies a standard way to embed audio in a web page.
###### Example
```
<video width="320" height="240" controls>
  <source src="/video-source" type="video/mp4">
  <source src="video-source" type="video/ogg">
Your browser does not support the video tag.
</video>
```
The controls attribute adds video controls, like play, pause, and volume.

It is a good idea to always include width and height attributes. If height and width are not set, the page might flicker while the video loads.

The <source> element allows you to specify alternative video files which the browser may choose from. The browser will use the first recognized format.

In HTML5, there are 3 supported video formats: MP4, WebM, and Ogg.
You can read more about `<video>` and it's attributes element [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video).

#### HTML Canvas
The HTML `<canvas>` element is used to draw graphics, on the web page, via JavaScript.

The `<canvas>` element is only a container for graphics. we must use JavaScript to actually draw the graphics.
###### Example
```
<body>
<canvas id="canvas-sample" width="200" height="100" style="border:1px solid #000000;">
</canvas>
</body>
```

Canvas has several methods for drawing paths, boxes, circles, text, and adding images.

#####  getContext()
The `<canvas>` element has a method called getContext(), used to obtain the rendering context and its drawing functions. getContext() takes one parameter, the type of context.

###### Color
There are two important properties we can use: fillStyle and strokeStyle.
fillStyle = color
Sets the style used when filling shapes.
strokeStyle = color
Sets the style for shapes' outlines.
color is a string representing a CSS color>, a gradient object, or a pattern object. We'll look at gradient and pattern objects later. By default, the stroke and fill color are set to black (CSS color value #000000).

###### Exampl
```
// This set the fillStyle to 'orange'
ctx.fillStyle = 'orange';
```

```
// HTML
<canvas id="sample-canvas" width="200" height="100"
style="border:1px solid #c3c3c3;">
Your browser does not support the canvas element.
</canvas>
```
```

// JavaScript
<script>
  var canvas = document.getElementById("myCanvas");
  var ctx = canvas.getContext("2d");
  ctx.fillStyle = "#FF0000";
  ctx.fillRect(0,0,150,75);
</script>
```
The first line in the script retrieves the node in the DOM representing the `<canvas>` element by calling the document.getElementById() method. Once we have the element node, we can access the drawing context using its getContext() method and set the color using **fillStyle** property.

The **CanvasRenderingContext2D.fillRect()** method of the Canvas 2D API draws a filled rectangle whose starting point is at the coordinates (x, y) with the specified width and height and whose style is determined by the **fillStyle** attribute.

You can read learn more about `<canvas>` [here](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM4NTk5OTkxMl19
-->
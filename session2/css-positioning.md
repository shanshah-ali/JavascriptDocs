#### CSS position Property
The position CSS property specifies how an element is positioned in a document. The top, right, bottom, and left properties determine the final location of positioned elements.

There are five different position values:
* static
* relative
* fixed
* absolute
* sticky

##### static
The element is positioned according to the normal flow of the document. The top, right, bottom, left, and z-index properties have no effect. This is the default value.
##### relative
The element is positioned according to the normal flow of the document, and then offset relative to itself based on the values of top, right, bottom, and left. The offset does not affect the position of any other elements; thus, the space given for the element in the page layout is the same as if position were static.

###### Example
```
// HTML
<body>
  <div class="parent-element">
    <div class="child-element"></div>
  </div>
</body>
```
```
// CSS
.parent-element {
  width: 400px;
  height: 300px;
  border: 1px solid #ddd
}

.child-element {
  width: 60px;
  height: 60px;
  background: red;
  position: relative;
  top: 50px;
  left: 80px;
}
```

In above example the position of child element is set as relative and value of top, left are set 50px and 80px.

The child element will be positioned from it's original position 50px from top and 80px from left.

##### fixed
An element with position: fixed; is positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled. The top, right, bottom, and left properties are used to position the element.

###### example
```
// HTML
<body>
  <header class="header">
    <nav>
      <ul>
        <li class="nav-item"><a href="#">Home</a></li>
        <li class="nav-item"><a href="#">Benefits</a></li>
        <li class="nav-item"><a href="#">Resources</a></li>
        <li class="nav-item"><a href="#">Help center</a></li>
      </ul>
    </nav>
  </header>
</body>
```

```
.header {
  position: fixed;
  top: 0;
  left: 0
}

.nav-item {
  display: inline
}

.nav-item a {
  padding: 20px
}

```

In above example position property of `<header>` is set as 'fixed' and top, left properties are set as 0, 0.

The header element will be sticked to top of the page even the page is scrolled down.

##### position
An element with position: absolute; is positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed).

However; if an absolute positioned element has no positioned ancestors, it uses the document body, and moves along with page scrolling.
###### example
```
// HTML
<body>
  <h2>position: absolute;</h2>
  <p>An element with position: absolute; is positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed):</p>
  <div class="relative">This div element has position: relative;
    <div class="absolute">This div element has position: absolute;</div>
  </div>
</body>
```
```
// CSS
div.relative {
    position: relative;
    width: 400px;
    height: 200px;
    border: 3px solid #73AD21;
}

div.absolute {
    position: absolute;
    top: 80px;
    right: 0px;
    width: 200px;
    height: 100px;
    border: 3px solid #73AD21;
}
```

In above example the position property is set as relative for outer div and absolute for inner div and top, left property for inner div are set as 80px, 0.

The inner div will be positioned 80px from top and 0px from left relative to it's nearest positioned element, in this case(outer div) not relative to viewport.  

##### sticky
An element with position: sticky; is positioned based on the user's scroll position.

A sticky element toggles between relative and fixed, depending on the scroll position. It is positioned relative until a given offset position is met in the viewport - then it "sticks" in place (like position:fixed).

```
// HTML
<body>
  <p>Try to <b>scroll</b> inside this frame to understand how sticky positioning works.</p>
  <p>Note: IE/Edge 15 and earlier versions do not support sticky position.</p>
  <div class="sticky">I am sticky!</div>
  <div style="padding-bottom:2000px">
    <p>In this example, the sticky element sticks to the top of the page (top: 0), when you reach its scroll position.</p>
    <p>Scroll back up to remove the stickyness.</p>
    <p>Some text to enable scrolling.. Lorem ipsum dolor sit amet, illum definitiones no quo, maluisset concludaturque et eum, altera fabulas ut quo. Atqui causae gloriatur ius te, id agam omnis evertitur eum. Affert laboramus repudiandae nec et. Inciderint efficiantur his ad. Eum no molestiae voluptatibus.</p>
    <p>Some text to enable scrolling.. Lorem ipsum dolor sit amet, illum definitiones no quo, maluisset concludaturque et eum, altera fabulas ut quo. Atqui causae gloriatur ius te, id agam omnis evertitur eum. Affert laboramus repudiandae nec et. Inciderint efficiantur his ad. Eum no molestiae voluptatibus.</p>
  </div>
</body>
```
```
// CSS
div.sticky {
  position: -webkit-sticky;
  position: sticky;
  top: 0;
  padding: 5px;
  background-color: #cae8ca;
  border: 2px solid #4CAF50;
}
```

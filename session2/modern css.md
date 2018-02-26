### Modern css

##### Variables: 
Variables in CSS should be declared within a CSS selector that defines its scope. For a global scope you can use either the :root or the body selector.
The variable name must begin with two dashes (- -) and is case sensitive!
**Example:**
```
:root {
    --main-bg-color: blue; 
}
```

The **var()** function can be used to insert the value of a custom property.
The following example first defines a global custom property named "--main-bg-color", then it uses the var() function to insert the value of the custom property later in the style sheet:
```
:root {
    --main-bg-color: coral; 
}

#div1 {
    background-color: var(--main-bg-color); 
}

#div2 {
    background-color: var(--main-bg-color);
}
```
##### Flex-box:
Flexbox was designed to define how space is distributed across a single row or column.
It eliminates the need for a lot of the hacks like negative margins that were necessary with float-based layouts.

A flexbox layout consists of a parent element, with one or more child elements.
The parent element becomes flexible by setting the display property to flex:
```
.flex-container {
  display: flex;
}
```
**Flexbox properties for the parent element:**
- **flex-direction** : The flex-direction property defines in which direction the container wants to stack the items.
 **values:** row, row-reverse, column, column-reverse

- **flex-wrap** : The flex-wrap property defines if, and how, the container wants its children to wrap
 **values:** wrap, nowrap, wrap-reverse

- **flex-flow** : The flex-flow property is a shorthand property for setting both the flex-direction and flex-wrap properties.

- **justify-content** : The justify-content property aligns the items on main axis
  **values:** center, flex-start, flex-end, space-around, space-between

- **align-items** : The align-items property aligns the items on cross axis.
  **values:** center, flex-start, flex-end, stretch, baseline

- **align-content** : The align-content property aligns the item rows.
  **values:** space-between, space-around, stretch, center, flex-start, fex-end

**Flexbox properties for the child elements:**

- **order** : The order property sorts the items in the specified order.
 **values:** _number_, default value is 0

- **flex-grow** : The flex-grow property specifies how much a flex item will grow relative to the rest of the flex items.
 **values:** _number_, default value is 0

- **flex-shrink** : The flex-shrink property specifies how much a flex item will shrink relative to the rest of the flex items.
 **values:** _number_, default value is 0

- **flex-basis** : The flex-basis property specifies the width of a flex item.
- **flex** : The flex property is a shorthand property for the flex-grow, flex-shrink, and flex-basis properties
- **align-self** : The align-self property overrides the default alignment set by the container's align-items property
**values:** center, flex-start, flex-end

For further reading on flexbox, refer <https://css-tricks.com/snippets/css/a-guide-to-flexbox/>
##### Grid:
The CSS Grid Layout Module offers a grid-based layout system, with rows and columns, making it easier to design web pages without having to use floats and positioning.

An HTML element becomes a grid container by setting the display property to grid or inline-grid.
```
.grid-container {
  display: grid;
}
```
All direct children of the grid container automatically become grid items.
- The horizontal lines of grid items are called rows, and the vertical  lines of grid items are called columns.
- The space between each column/row are called gaps.
- You can adjust the gap size by using one of theses properties: grid-column-gap/ grid-row-gap/ grid-gap
- The line between columns are called column lines.
- The line between rows are called row lines.

```
// Place a grid item at column line 1, and let it end on column line 3:

.item1 {
  grid-column-start: 1;
  grid-column-end: 3;
}

// Place a grid item at row line 1, and let it end on row line 3:

.item2 {
  grid-row-start: 1;
  grid-row-end: 3;
}

```

**Grid properties for the parent element:**
- **grid-template-columns**
  **grid-template-rows**: defines the number of columns/rows in your grid layout, and it can define the width of each column/row.
**values:** line name ([first], [line2]) , size(px, % , auto)

```
.container {
  grid-template-columns: 40px 50px auto 50px 40px;
  grid-template-rows: 25% 100px auto;
}

.container2 {
  grid-template-columns: [first] 40px [line2] 50px [line3] auto [col4-start] 50px [five] 40px [end];
  grid-template-rows: [row1-start] 25% [row1-end] 100px [third-line] auto [last-line];
}
```
- **grid-column-gap**
**grid-row-gap** : Specifies the size of the grid lines. You can think of it like setting the width of the gutters between the columns/rows.
 **values:** <line size> (px, auto)

- **justify-items** : Aligns the content inside a grid item along the row axis. This value applies to all grid items inside the container
 **values:** start, end, center, stretch, space-around, space-between, space-evenly

- **align-items** : Aligns the content inside a grid item along the column axis. This value applies to all grid items inside the container.
**values:** start, end, center, stretch, space-around, space-between, space-evenly

-  **grid-auto-flow** : If you have grid items that you don't explicitly place on the grid, the auto-placement algorithm kicks in to automatically place the items. This property controls how the auto-placement algorithm works.
 **values:** row, column, dense

**Grid properties for the child elements:**

- **grid-column-start**
**grid-column-end**
**grid-row-start**
**grid-row-end** : Determines a grid item's location within the grid by referring to specific grid lines. grid-column-start/grid-row-start is the line where the item begins, and grid-column-end/grid-row-end is the line where the item ends.
**values:**
   - <line> - can be a number to refer to a numbered grid line, or a name to refer to a named grid line
    - span <number> - the item will span across the provided number of grid tracks
    - span <name> - the item will span across until it hits the next line with the provided name
    -  auto - indicates auto-placement, an automatic span, or a default span of one
    

- **justify-self** : Aligns the content inside a grid item along the row axis. This value applies to the content inside a single grid item
 **values:** start, end, center, stretch

- **align-self** : Aligns the content inside a grid item along the column axis. This value applies to the content inside a single grid item
 **values:** start, end, center, stretch

For further reading on css-grid-layout, refer <https://css-tricks.com/snippets/css/complete-guide-grid/>


# CSS

![](https://image.ibb.co/dBRqcc/screenshot_www_w3schools_com_2018_02_21_11_56_31.png)
- The selector points to the HTML element you want to style.

- The declaration block contains one or more declarations separated by semicolons.

- Each declaration includes a CSS property name and a value, separated by a colon.

- A CSS declaration always ends with a semicolon, and declaration blocks are surrounded by curly braces.


## CSS Selectors
 CSS selectors are used to "find" (or select) HTML elements based on their element name, id, class, attribute, and more.

 1. **The element Selector**
			The element selector selects elements based on the element name. You can select all `<p>` elements on a page like this:
			
	    p {
		    text-align: center;
		    color: red;
		}
		
 2. **The id Selector**
		 The id selector uses the id attribute of an HTML element to select a specific element.
  
	The id of an element should be unique within a page, so the id selector is used to select one unique element!

	To select an element with a specific id, write a hash (#) character, followed by the id of the element.

	    #para1 {
		    text-align: center;
		    color: red;
		}

 3. **The class Selector**
	The class selector selects elements with a specific class attribute.
		
	To select elements with a specific class, write a period (.) character, followed by the name of the class.

	In the example below, all HTML elements with class="center" will be red and center-aligned:

	    .center {
		    text-align: center;
		    color: red;
		}

## The CSS Box Model

All HTML elements can be considered as boxes. In CSS, the term "box model" is used when talking about design and layout.

The CSS box model is essentially a box that wraps around every HTML element. It consists of: margins, borders, padding, and the actual content. The image below illustrates the box model:

![](https://ibin.co/w800/3sRivOo7VSFs.png)

Explanation of the different parts:

- **Content** - The content of the box, where text and images appear
- **Padding** - Clears an area around the content. The padding is transparent
- **Border** - A border that goes around the padding and content
- **Margin** - Clears an area outside the border. The margin is transparent

## CSS Specificity 
is the means by which browsers decide which CSS property values are the most relevant to an element and, therefore, will be applied. Specificity is based on the matching rules which are composed of different sorts of CSS selectors.

### How is specificity calculated?
Specificity is a weight that is applied to a given CSS declaration, determined by the number of each selector type in the matching selector. When multiple declarations have equal specificity, the last declaration found in the CSS is applied to the element. Specificity only applies when the same element is targeted by multiple declarations. As per CSS rules, directly targeted elements will always take precedence over rules which an element inherits from its ancestor.

> Note: Proximity of elements in the document tree has no effect on the specificity.

### Selector Types
The following list of selector types increases by specificity:

1. Type selectors (e.g., h1) and pseudo-elements (e.g., ::before).
2. Class selectors (e.g., .example), attributes selectors (e.g., [type="radio"]) and pseudo-classes (e.g., :hover).
3. ID selectors (e.g., #example).


### The *!important* exception

When an important rule is used on a style declaration, this declaration overrides any other declarations. Although technically !important has nothing to do with specificity, it interacts directly with it. Using !important, however, is bad practice and should be avoided because it makes debugging more difficult by breaking the natural cascading in your stylesheets. When two conflicting declarations with the !important rule are applied to the same element, the declaration with a greater specificity will be applied.

#### Some rules of thumb:

- Always look for a way to use specificity before even considering !important
- Only use !important on page-specific CSS that overrides foreign CSS (from external libraries, like Bootstrap or normalize.css).
- **Never** use !important when you're writing a plugin/mashup.
- **Never** use !important on site-wide CSS.

[Read more here](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)

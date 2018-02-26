# ** Sass ** (Syntactically Awesome Style Sheets)

Sass is an extension of CSS that adds power and elegance to the basic language. It allows you to use variables, nested rules, mixins, inline imports, and more, all with a fully CSS-compatible syntax.


## ``` Features ```

* Fully CSS-compatible

* Language extensions such as variables, nesting, and mixins

* Many useful functions for manipulating colors and other values

* Advanced features like control directives for libraries

* Well-formatted, customizable output.


## ```Variables ```

 Variables begin with dollar signs, and are set like CSS properties

 ```
  $width: 5em;

  #main {
    width: $width;
  }

 ```

 To declare globally ``` !global``` flag can be used. Global variables can be accessed in any class.

** Sass Syntax **

 ```
   #main {
   $width: 5em !global;
   width: $width;
  }

  #sidebar {
   width: $width;
  }

 ```

 ** Compiled Css Syntax **

 ```
   #main {
    width: 5em;
  }

  #sidebar {
    width: 5em;
  }

 ```

 ## ``` Data Types Available in Sass ```

 Sass Script supports following data types:
  * numbers (e.g. 1.2, 13, 10px)
  * strings of text, with and without quotes (e.g. "foo", 'bar', baz)
  * colors (e.g. blue, #04a3f9, rgba(255, 0, 0, 0.5))
  * booleans (e.g. true, false)
  * nulls (e.g. null)
  * lists of values, separated by spaces or commas (e.g. 1.5em 1em 0 2em, Helvetica, Arial, sans-serif)
  * maps from one value to another (e.g. (key1: value1, key2: value2))
  * function references

  ### Lists

  Lists are how Sass represents the values of CSS declarations like margin: 10px 15px 0 0 or font-face: Helvetica, Arial, sans-serif. Lists are just a series of other values, separated by either spaces or commas.

  ##### Examples
  ```

        $horse-types: pony horse mini-horse maxi-pony;

        $horse-types: pony, horse, mini-horse, maxi-pony;

        $horse-types: "pony", "horse", "mini horse", "maxi pony";  
  ```

  ### Maps

  Maps represent an association between keys and values, where keys are used to look up values.

  ```
    $map: (key1: value1, key2: value2, key3: value3);

  ```

## ``` Mixins ```

A Mixin is a block of code that lets us group CSS declarations we may reuse throughout our site.

### Creating a Mixin

  ```
  @mixin flex {
    // write the css here
    display: -webkit-flex;
    display: flex;
  }

  ```

### Using a Mixin

  To use a Mixin, we simply use ``` @include ``` followed by the name of the Mixin and a semi-colon.
  ```
  .row {
    @include flex;
  }

  ```

*** Compiled Css appears to be like this ***
```
.row {
    display: -webkit-flex;
    display: flex;
}

```

### Passing Arguments to Mixins

Mixins can also take in arguments to make the output more dynamic. To pass arguments to a Mixin, we simply do this.

```
@mixin grid($flex) {
    @if $flex {
        @include flex;
    } @else {
        display: block;
    }
}

```

###  Default Mixin Arguments

Functions in programming languages (SASS included) allow default arguments, it only makes sense for mixins too.

```
@mixin grid($flex: true) {
  // code here
}

```

## ``` Conditionals in Sass ```

### @if

The ``` @if ``` control directive takes a SassScript expression and processes its block of styles if the expression returns anything other than false.

```
// Set a variable to run the if statement against

$boolean: true !default

=simple-mixin
  @if $boolean
    @debug "$boolean is #{$boolean}"
    display: block
  @else
    @debug "$boolean is #{$boolean}"
    display: none

.some-selector
  +simple-mixin
```

##### Compiled Css

```
.some-selector {
  display: block;
}

```

### @for

The first option is ``` @for ``` $var from <start> through <end> which starts at <start> and loops "through" each iteration and ends at <end>.

The second option is ``` @for ``` $var from <start> to <end> which starts at <start> and loops through each iteration "to" <end> and stops.

```
$class-slug: for !default

@for $i from 1 through 4
  .#{$class-slug}-#{$i}
    width: 60px + $i

```

##### Compiled Css

```
.for-1 {
  width: 61px;
}

.for-2 {
  width: 62px;
}

.for-3 {
  width: 63px;
}

.for-4 {
  width: 64px;
}

```

### @each

The ``` @each ``` directive takes the form ``` @each``` $var in <list>.


```

$list: adam john wynn mason kuroir

=author-images
  @each $author in $list
    .photo-#{$author}
      background: image-url("avatars/#{$author}.png") no-repeat

.author-bio
  +author-images
```

##### Compiled Css

```
.author-bio .photo-adam {
  background: url('/images/avatars/adam.png') no-repeat;
}
.author-bio .photo-john {
  background: url('/images/avatars/john.png') no-repeat;
}
.author-bio .photo-wynn {
  background: url('/images/avatars/wynn.png') no-repeat;
}
.author-bio .photo-mason {
  background: url('/images/avatars/mason.png') no-repeat;
}
.author-bio .photo-kuroir {
  background: url('/images/avatars/kuroir.png') no-repeat;
}

```

### @while

The ``` @while ``` directive takes a SassScript expression (just like the other control directives) and repeatedly emits the nested block of styles until the statement evaluates to false.

```
$types: 4
$type-width: 20px

@while $types > 0
  .while-#{$types}
    width: $type-width + $types
  $types: $types - 1

```

##### Compiled Css

```
.while-4 {
  width: 24px;
}

.while-3 {
  width: 23px;
}

.while-2 {
  width: 22px;
}

.while-1 {
  width: 21px;
}

```


## ``` Imports ```


CSS has an import option that lets you split your CSS into smaller, more maintainable portions. The only drawback is that each time you use ``` @import ``` in CSS it creates another HTTP request.

```
  // sample.sass

  html,
  body,
  ul,
  ol
  margin:  0
  padding: 0

```

```
// base.sass

  @import sample

  body
    font: 100% Helvetica, sans-serif
    background-color: #efefef

```

## ``` Color Functions ```

Sass comes with functions that can easily be applied to colors in your CSS properties. These functions, when used correctly, can be incredibly powerful. They take some of the sting out of choosing and manipulating colors. When used with variables, they can speed up development drastically.

### Darken & Lighten

These two adjust the Lightness of the color’s HSL values.

```
darken( $base-color, 10% )
lighten( $base-color, 10% )

```

### Saturate, & Desaturate

These will will adjust the Saturation of the colors HSL values, much like Darken and Lighten adjusted the Lightness.

```
saturate( $base-color, 20% )
desaturate( $base-color, 20% )

```

### Adjust-hue

This adjusts the hue value of HSL the same way all of the others do

```
adjust-hue( $base-color, 20% )
```

### Adding Alpha Transparency

Using our hex color we can do a few things to get it to be a little transparent. We can call hsla, rgba, opacify, and transparentize.

```
rgba( $base-color, .7 )

```

### Tint & Shade

Our very own Phil LaPier has added to those base color functions.

```
tint( $base-color, 10% )
shade( $base-color, 10% )
```

## HTML Tags
##### HTML Elements
An HTML element usually consists of a **start** tag and **end** tag, with the content inserted in between:
```html
<tagname>Content goes here...</tagname>
```
The HTML element is everything from the start tag to the end tag:

### HTML Tags Ordered Alphabetically
[List](https://www.w3schools.com/tags/default.asp)

## Doctype
#### The HTML5 Doctype
The first line of every HTML5 document is a special code called the doctype. The doctype clearly indicates the standard that was used to write the document markup that follows. Here’s how a page announces that it adheres to the HTML5 standard:
  ```Html
    <!DOCTYPE html>
  ```
  The first thing you’ll notice about the HTML5 doctype is its simplicity. Compare it, for example, to the ungainly doctype that web developers need when using XHTML 1.0 strict:
  ```Html
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
      "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
  ```
#####  Why does your web page require any doctype at all?
Without a doctype, most browsers (including Internet Explorer and Firefox) will lapse into **quirks** mode. In this mode, they’ll attempt to render pages according to the slightly buggy rules that they used in older versions. The problem is that one browser’s quirks mode differs from the next, so pages designed for one browser are likely to get inconsistently sized fonts, scrambled layouts, and other glitches on another browser.
When you add a doctype, the browser recognizes that you want to use the stricter standards mode, which ensures that the web page is displayed with consistent formatting and layout on every modern browser. The browser doesn’t even care which doctype you use (with just a few exceptions). Instead, it simply checks that you have some doctype. The HTML5 doctype is simply the shortest valid doctype, so it always triggers standards mode.

### Character Encoding
The character encoding is the standard that tells a computer how to convert your text into a sequence of bytes when it’s stored in a file—and how to convert it back again when the file is opened. For historical reasons, there are many different character encodings in the world. Today, virtually all English websites use an encoding called UTF-8, which is compact, fast, and supports all the non-English characters you’ll ever need.
Often, the web server that hosts your pages is configured to tell browsers that it’s serving out pages with a certain kind of encoding. However, because you can’t be sure that your web server will take this step (unless you own the server), and because browsers can run into an obscure security issue when they attempt to guess a page’s encoding, you should always add encoding information to your markup.
HTML5 makes that easy to do. All you need to do is add the **<meta>** element shown below at the very beginning of your **<head>** section (or right after the doctype, if you don’t define the <head> element):
```Html
<head>
  <meta charset="utf-8">
  <title>A Tiny HTML Document</title>
</head>
```

### What is The Viewport?
The viewport is the user's visible area of a web page.

The viewport varies with the device, and will be smaller on a mobile phone than on a computer screen.

Before tablets and mobile phones, web pages were designed only for computer screens, and it was common for web pages to have a static design and a fixed size.

```Html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
This means that the browser will (probably) render the width of the page at the width of its own screen. So if that screen is 320px wide, the browser window will be 320px wide, rather than way zoomed out and showing 960px (or whatever that device does by default, in lieu of a responsive meta tag).
>Note: don't use a responsive meta tag if your website isn't specifically designed to be responsive and work well at that size, as it will make the experience worse.
[source](https://css-tricks.com/snippets/html/responsive-meta-tag/)

### [Block level vs. Inline elements](https://www.w3schools.com/html/html_blocks.asp)
##### Block-level Elements:-
A block-level element always starts on a new line and takes up the full width available (stretches out to the left and right as far as it can).
```Html
<p>The DIV element is a block element, and will start on a new line.</p>
```
![block](https://i.imgur.com/yuYbU9r.png)

##### Inline Elements:-
An inline element does not start on a new line and only takes up as much width as necessary.
```Html
<span>Hello</span>
<span>World</span>
```
![inline](https://i.imgur.com/YWkYxDF.png)

















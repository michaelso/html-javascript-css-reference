
# Implement and Manipulate Document Structures and Objects

## Create the document structure by using HTML

  HTML is for providing a structure to a document.  
  A document contains text, reference to other document, image, video; HTML uses tags to mark each piece of content in the document for describing  what it is about. This marking process provides a structure to the document.
  Without this special processing or "mark up", the computer will not understand the content inside document very well.

  Providing a structure leads to better browser rendering, i.e. improve readability, provide built-in features; It also helps the search engine to understand the document better, hence improve indexing and search result.  

  A structure enables styling the document using external style sheet (CSS) by selecting the target element to be styled; and manipulate the content in the document using programming language (JS) via object mode representation which HTML can provide.
  CSS and JS are essential for building experience rich and interactive website aka web app.
  
  note: Most content here refers to [MDN: Mozilla Developer Network] and [HTML5 For Web Designers]

### Structure the UI by using semantic markup

HTML5 provides a long list of tags for markup, each tag has its semantic meaning, including markup for search engines and screen readers,  
such as Section, Article, Nav, Header, Footer, and Aside  

#### Building block of HTML: HTML element

Two very descriptive pictures about HTML element:  

![MDN: Anatomy of an HTML element
Section](https://mdn.mozillademos.org/files/9347/grumpy-cat-small.png)
picture source: [MDN: Getting started with HTML]

![MDN: Anatomy of an HTML element
Section](https://mdn.mozillademos.org/files/9345/grumpy-cat-attribute-small.png)
picture source: [MDN: Getting started with HTML]

[MDN: Getting started with HTML]: https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started#Anatomy_of_an_HTML_element

There are many HTML tags for different purposes with their respective attributes which contains metadata of the HTML element that can be used to adjust the elements' behaviour

#### Core structure of a HTML page

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <title></title>
</head>

<body>
<!-- page content goes here -->
</body>
</html>
```

`<!DOCTYPE html>` is a declaration to tell the browser use the "normal mode" for rendering.

`<html> ... </html>` marks the start and end of HTML document.

`<head> ... </head>` contains metadata of the page, or support documents such as link to CSS and JS, etc. This area does not contain any content to be displayed

Inside the `<head>` area, most HTML page contains these four popular HTML elements:

- `<meta charset="UTF-8">`  
for specifying encoding
- `<script src="file.js"></script>`  
for loading JS
- `<link rel="stylesheet" href="file.css">`
for loading CSS  
- `<title>page title</title>`  
contains the page title

`<body> ... </body>` contains content to be displayed.

#### Content sectioning

These elements break the content into logical pieces, and build an broad outline for the document content.  

[`<header>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header) represents introductory content, typically:  
a group of **introductory or navigational aids**;  
It may contain some heading elements but also  

- a logo,  
- a search form,  
- an author name,  
- and other elements.

note:  

- Can be used multiple times in a page  e.g. inside each `<article>`  or `<section>`
- Only use it when it is nesting two or more other elements  

  Good:

  ```html
  <header>
    <h2>The Planet Earth</h2>
    <p>Posted on Wednesday, <time datetime="2017-10-04">4 October 2017</time> by Jane Smith</p>
  </header>
  ```

  Bad: just don't use it

  ```html
  <header>
    <h2>The Planet Earth</h2>
  </header>
  ```

[`<footer>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer) represents a footer for its **nearest sectioning content or sectioning root element**.  
A footer typically contains information about:  

- the author of the section,  
- copyright data or  
- links to related documents.

note: Can be used multiple times in a page.  

[`nav`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/nav) represents a section of a page whose purpose is to provide navigation links, either:  

- within the current document  
- or to other documents.  

Common examples of navigation sections are:  

- menus,  
- tables of contents, and  
- indexes.

[`<article>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/article) represents a **self-contained** complete in a document, page, application, or site, which is intended to be **independently distributable** or reusable, and not lose its meaning. It usually has a header or nested two more more other **related** HTML elements.

Examples of an `<article>` element could be:  

- a magazine or newspaper article  
- a blog post  
- a forum post  
- widgets: e.g. stock tickers, calculators, clocks, weather widgets, and the like

Note: You can have an article with subarticles; however, each subarticle must be a direct extension and related to the root article.

[`<section>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section#Example) represents a standalone section. It is used for grouping **related content** together. It usually has a header or nested two more more other **related** HTML elements.

Note:  

- each `<section>` creates a new header hierarchy i.e. start from `<h1>` rather than inherited whatever before it
- Only use `<section>` if no other tag is approperiate i.e. `<section>` is low priority choice
- Do not use the `<section>` element as a generic container; this is what `<div>` is for, especially when the sectioning is only for styling purposes. A rule of thumb is that a section should logically appear in the outline of a document.

[`<aside>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/aside) represent a portion of a document whose content is seperated from or only indirectly related to the main content. i.e. could be removed without reducing the meaning of the main content of the document or section. Nice to have but can be removed.  
Example:

- Pullquotes
- call-out boxes
- Ad

[`<main>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/main) represents the dominant content of the `<body>` of a document.  
Content in `<main>` should be unique across the set of documents or website; Repeating elements such as sidebars, navigation links, copyright information, site logos, and search forms shouldn't be included.
It has no effect on the document outline, however, it is useful for accessibility. Assistive technology can by pass the other content on the page such as navigation menu, and jump right into the main content.
This is also useful for browser's reader mode.

#### Search engine

`<article>` and `<section>` are used by the search engine algorithm as these elements are known to contain the main body of the page.  

Within each `<article>`, the engine look for elements such as `<hgroup>` or `<h1>` to get the main topic of the `<article>` element for relevant indexing.
With proper sementic tags, the quality of search engines indexing improve and let the site more searchable by end users.

How to optimise search engine result, aka SEO, in flavor of your site is an important technique to use when designing websites. After all, the content published are meant to be found by the target audience.

Here are some ways to add metadata so the search engine can understand the website better (SEO):

- Microformats  
- schema.org  
- metadata in `<head>`: provide search enginer result page preview  

  ```html
  <meta name="description"
  content="The MDN Web Docs site provides
   information about Open Web technologies
   including HTML, CSS, and APIs for both
   Web sites and progressive web apps.">
  ```

  [MDN: Head metadata](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#Adding_an_author_and_description)

#### Social network

Add some metadata in `<head>` to provide preview and richer content experience  

Facebook:

```html
<meta property="og:image" content="https://developer.cdn.mozilla.net/static/img/opengraph-logo.dc4e08e2f6af.png">
<meta property="og:description" content="The Mozilla Developer Network (MDN) provides
information about Open Web technologies including HTML, CSS, and APIs for both Web sites
and HTML5 Apps. It also documents Mozilla products, like Firefox OS.">
<meta property="og:title" content="Mozilla Developer Network">
```

Twitter:

```html
<meta name="twitter:title" content="Mozilla Developer Network">
```

[MDN: Other types of metadata](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#Other_types_of_metadata)

#### Screen Reader

`<section>` can do page sectioning and help building an outline of the page. It used to be relying on headers, e.g. `<h1>` to `<h6>`, however, just used headers can not indicate sections and subsection as clearly.

### create a layout container in HTML
  
  [`<div>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div) aka The HTML Content Division element, is the generic container for flow content. It has no sementic value and has no effect on the content or layout until styled using CSS.  
  `<article>` or `<section>` or `<nav>` or other tags with sementic should be used before using `<div>`
  
  [`<table>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table) represents tabular data i.e. information presented in a two-dimensional table comprised of rows and columns of cells containing data.  
  It provides a more static layout and has to work witm many other table related HTML tags to create the table elements
  
## Write code that interacts with UI controls

  HTML supports image and multimedia content beside text. The structure of HTML and content inside can be modified using Javascript.

### Programmatically add and modify HTML elements  
  
  To programatically add and modify HTML elements, we have to know how to accress or reference them.

#### Document Object Model

[Document Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) (DOM) represents a document with a [logical tree](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Using_the_W3C_DOM_Level_1_Core), represents the document as:  

- nodes which has a parent-child structure
- **objects** which has **properties, methods and events**

Each [Node](https://developer.mozilla.org/en-US/docs/Web/API/Node) in the tree is an element that can be treated as an object.

 [Element](https://developer.mozilla.org/en-US/docs/Web/API/Element) inhert the Node class.It is the most general base class from which all objects in a Document inherit.  

An object-oriented representation of the document provides an efficent way to manipulate the HTML documents. Programming languages can connect to the DOM and use [the APIs](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM) to change document structure, style and content.

#### Selecting items in the DOM

To access the objects in DOM, programmer can use ["document" object](https://developer.mozilla.org/en-US/docs/Web/API/Document) which is a globel object provide by browser (some refer this as [Web API](https://developer.mozilla.org/en-US/docs/Web/API))

common methods for selecting DOM elements:

- getElementById()
- getElementsByClassName()
- getElementsByTagName()

use CSS selector sytax for selecting DOM element:

- querySelector()
- querySelectorAll()

Similar to a program require a static main() as an entry point for program to start  

- window.onload can act one of the entry point.

#### Altering the DOM

Once there is a reference to a HTML element, new child elements can be added or remove some existing elements.  
The elements styling can be modified, such as hiding it, or update content in the elements using the property.

##### Some common node/element methods

Create element: [Document.createElement()](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)  

```javascript
var element = document.createElement(tagName[, options]);
```

Add node: [Node.appendChild()](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild) method adds a node to the end of the list of children of a specified parent node.

```javascript
// Create a new paragraph element, and append it to the end of the document body
var p = document.createElement("p");
document.body.appendChild(p);
```

Remove node:  
[Node.removeChild()](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild) method removes a child node from the DOM and returns the removed node.

```javascript
// remove a specified element without having to specify its parent node:
let node = document.getElementById("nested");
if (node.parentNode) {
  node.parentNode.removeChild(node);
}
```

Insert Node: [Node.insertBefore()](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore) method inserts a node before the reference node, and as a child of a specified parent node.

```html
// var insertedNode = parentNode.insertBefore(newNode, referenceNode);

<div id="parentElement">
  <span id="childElement">foo bar</span>
</div>

<script>
// Create a new, plain <span> element
var sp1 = document.createElement("span");

// Get a reference to the element, before we want to insert the element
var sp2 = document.getElementById("childElement");
// Get a reference to the parent element
var parentDiv = sp2.parentNode;

// Insert the new element into the DOM before sp2
parentDiv.insertBefore(sp1, sp2);
</script>

```

No insertAfter(), as to to it can be emulated by combining the insertBefore method with Node.nextSibling.

##### Common read-only properties available for node/element

- childNodes
- firstChild
- lastChild
- hasChildNodes

##### Some of the many ways to alter the content inside an element

- [`HTMLElement.innerText`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/innerText) property which only shows “human-readable” elements.  It is aware of styling and won’t return the text of “hidden” elements. Read this [link](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent#Differences_from_innerText) for more info.  
Note: [HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement) inherent Element class

- [`Node.textContent`](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent) property represents the text content of the node and its descendants. It gets all text content inside unlike the innerText property.

- [`Element.innerHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML) property can gets or sets the HTML or XML markup contained within the element. It is not recommended to use as it has security risk of being inject some script, especially if it takes input from user.

### Implement media controls

Web browser can serve video and audio natively without plugin with proper HTML tags.

#### `<video>` how-to

[`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) aka the HTML Video element, embeds a media player which supports video playback into the document.

Sample code:

```html
<video src="movie.mp4" controls width="360" height="240"> </video>
```

three sets of attributes are used in the above code

- src: set the path of the video source file
- controls: display the playback control for users.  
This is a [boolean attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes#Boolean_Attributes) which the present of it means true and absent means false; it does not take in any value
- width/height: these two set the size of the video player in browser, or the default size of the video maybe too big and fill the page

Since browsers have different [video format](https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats) support, nesting `<source>` elements is needed and the browser will use the first one it support

```html
<video width="620" controls>
  <source src="myVideo.mp4" type="video/mp4">
  <source src="myVideo.webm" type="video/webm">
  <p>Your browser doesn't support HTML5 video. Here is
     a <a href="myVideo.mp4">link to the video</a> instead.</p>
</video>
```

Common optional attributes for `<video>`:

- autoplay (boolean attribute)
- loop (boolean attribute)
- poster: path to a representative image for the video
- preload (enumerated attribute):  none/metadata(default)/auto

create your own custom controls:  
  use JavaScript and the [HTMLMediaElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement) API.  
  
  `<video>` element implement the [HTMLVideoElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLVideoElement) interface which inherits properties and methods of HTMLMediaElement and HTMLElement.  
  See [Creating a cross-browser video player](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery/cross_browser_video_player) for more details

  short sample:

  ```html
  // source: https://html5forwebdesigners.com/media/
  <video id="player" width="620" src="myVideo.mp4">
</video>
  <div>
    <button
    onclick="document.getElementById('player').play()">
    Play
    </button>
    <button
    onclick="document.getElementById('player').pause()">
    Pause
    </button>
    <button
    onclick="document.getElementById('player').volume += 0.1">
    Volume Up
    </button>
    <button
    onclick="document.getElementById('player').volume -= 0.1">
    Volume Down
    </button>
  </div>
```

To show subtitles/captions along with your video:  
  use some JavaScript along with the `<track>` element and the WebVTT format. See [Adding captions and subtitles to HTML5 video](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video) for more information

#### `<audio>` how-to

[`<audio>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio) is used to embed sound content in documents. It may contain one or more audio sources, represented using the src attribute or the `<source>` element: the browser will choose the most suitable one.

sample code from MDN:

```html
<figure>
    <figcaption>Listen to the T-Rex:</figcaption>
    <audio
        controls
        src="/media/examples/t-rex-roar.mp3">
            Your browser does not support the
            <code>audio</code> element.
    </audio>
</figure>
```

`<audio>` is very similar with `<vidoe>` but without the height or width attribute

### Implement HTML5 canvas and SVG graphics
  
#### HTML5 canvas

[`<canvas>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas) element enable creating images dynamically using script. Graphics and animations can be drawn with either the canvas scripting API (2d) or the WebGL API (3D).  
The main value of dynamic image creation is ability to react to user-triggered events.  
One sample app is Google Chart which user enter data in the tablet and a chart can be generated and update in real time.

Sample code:

```html
<canvas id="canvas" width="300" height="300">
  An alternative text describing what your canvas displays.
</canvas>

<script>
var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');
ctx.fillStyle = 'green';
ctx.fillRect(10, 10, 100, 100);
</script>
```

HTMLCanvasElement.getContext() method returns a drawing context on the canvas. Below are using [CanvasRenderingContext2D](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D)

Below are some common methods use for drawing:  

##### Drawing rectangles

[CanvasRenderingContext2D.fillRect()](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillRect)  
Draws a **filled** rectangle at (x, y) position whose size is determined by width and height  
`void ctx.fillRect(x, y, width, height);`

[CanvasRenderingContext2D.clearRect()](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/clearRect)  
Draws a **clear** rectangle, i.e. erases the pixels in a rectangular area by setting them to transparent black  
`void ctx.clearRect(x, y, width, height);`

[CanvasRenderingContext2D.strokeRect()](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/strokeRect)  
Draws a rectangle using current [stroke style](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/strokeStyle)  
`void ctx.strokeRect(x, y, width, height);`

##### Transformations

[CanvasRenderingContext2D.rotate()](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/rotate)  
Adds a rotation to the transformation matrix  
`void ctx.rotate(angle);`

##### Path

CanvasRenderingContext2D.beginPath()  
    Starts a new path by emptying the list of sub-paths. Call this method when you want to create a new path.

CanvasRenderingContext2D.closePath()  
    Causes the point of the pen to move back to the start of the current sub-path. It tries to draw a straight line from the current point to the start. If the shape has already been closed or has only one point, this function does nothing.

CanvasRenderingContext2D.moveTo()  
    Moves the starting point of a new sub-path to the (x, y) coordinates.

CanvasRenderingContext2D.lineTo()  
    Connects the last point in the current sub-path to the specified (x, y) coordinates with a straight line.

CanvasRenderingContext2D.bezierCurveTo()  
    Adds a cubic Bézier curve to the current path.

CanvasRenderingContext2D.quadraticCurveTo()  
    Adds a quadratic Bézier curve to the current path.

CanvasRenderingContext2D.arc()  
    Adds a circular arc to the current path.

##### SVG graphic

[Scalable Vector Graphics](https://developer.mozilla.org/en-US/docs/Web/SVG) (SVG) is an XML-based markup language for describing two dimensional based [vector graphics](https://en.wikipedia.org/wiki/Vector_graphics).  
The main advantage is it doesn't loss quality due to zoom in zoom out.  
Performance wise, it is not as good as `<canvas>`.

A lot list of [SVG elements](https://developer.mozilla.org/en-US/docs/Web/SVG/Element) can be used to create shapes, images, animation, link etc. With relvant attributes for each element, details can be added.

Some common SVG elements:  
[`<circle>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/circle)

```html
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="50"/>
</svg>
```

[`<rect>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/rect)

```html
<svg viewBox="0 0 220 100" xmlns="http://www.w3.org/2000/svg">
  <!-- Simple rectangle -->
  <rect width="100" height="100" />

  <!-- Rounded corner rectangle -->
  <rect x="120" width="100" height="100" rx="15" />
</svg>
```

[`<polygon>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/polygon)

```html
<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg">
  <!-- Example of a polygon with the default fill -->
  <polygon points="0,100 50,25 50,75 100,0" />

  <!-- Example of the same polygon shape with stroke and no fill -->
  <polygon points="100,100 150,25 150,75 200,0"
            fill="none" stroke="black" />
</svg>
```

[`<animate>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/animate)

```html
<?xml version="1.0"?>
<svg width="120" height="120" viewBox="0 0 120 120" version="1.1"
     xmlns="http://www.w3.org/2000/svg">
  
  <rect x="10" y="10" width="100" height="100">
    <animate attributeType="XML" attributeName="x" from="-100" to="120"
        dur="10s" repeatCount="indefinite"/>
  </rect>
</svg>
```

## Apply styling to HTML elements programmatically

[HTMLElement.style](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style) property is used to get and set the **inline style** of an element.  
The style property has the same (highest) [priority (Specificity)](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) in the CSS cascade as an inline style declaration set via the style attribute.

[CSS Properties Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference) for a list of the CSS properties accessible via style.  

### Change the location of an element

[`Position`](https://developer.mozilla.org/en-US/docs/Web/CSS/position) CSS property sets how an element is positioned in a document.  

The `position type` and the [`top`](https://developer.mozilla.org/en-US/docs/Web/CSS/top), [`right`](https://developer.mozilla.org/en-US/docs/Web/CSS/right), [`bottom`](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom), and [`left`](https://developer.mozilla.org/en-US/docs/Web/CSS/left) properties determine the final location of positioned elements.  

If all are specified and have conflict,  

- vertical offset:  
`top` win `bottom`  
- horizontal offset:  
`left` win when direction is ltr (English, horizontal Japanese, etc.) and  
`right` wins when direction is rtl (Persian, Arabic, Hebrew, etc.).

Five options for `position` property value:

- static: default value  
  - positioned according to the [normal flow](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flow_Layout) of the document.
  - The other position properties, offset values, has no effect on it.  
Not a "[computed position](https://developer.mozilla.org/en-US/docs/CSS/computed_value)"
- relative: computed position  
  - positioned according to the normal flow of the document
  - then adjusted to **itself** by the offset values of top, right, bottom, and left.
  - Elements after it **ignore the offset and follow the normal flow (static) unless specified.**
- absolute:  computed position  
  - **removed from the normal document flow**, and no space is created for the element in the page layout  
  - positioned relative to its [containing block](https://developer.mozilla.org/en-US/docs/Web/CSS/All_About_The_Containing_Block).  
  - then adjusted by the offset values of top, right, bottom, and left.
  
- fixed:  computed position  
  - **removed from the normal document flow**, and no space is created for the element in the page layout
  - positioned relative to the initial containing block established by the [viewport](https://developer.mozilla.org/en-US/docs/Glossary/viewport) which is the user's curent view
- sticky:  computed position  
  a hybrid of relative and fixed
  - positioned according to the normal flow of the document (**relative**)
  - then adjusted to its
    - nearest scrolling ancestor (**relative**) and
    - containing block (nearest block-level ancestor), including table-related elements by the offset values of top, right, bottom, and left. (**fixed**)
  - Elements after it **ignore the offset and follow the normal flow (static) unless specified.**

All options except static has [stacking context](https://developer.mozilla.org/en/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context) adjust by z-index  

To update the position of an element:

  1. select the target element
  2. update the style property values

Sample code

```javascript
// suppose there are html input elements with IDs of position, top, left

var pos = document.getElementById("position");
var top = document.getElementById("top");
var left = document.getElementById("left");

var img = document.getElementById("target_1");
img.style.position = pos.value;
img.style.top = top.value + "px";
img.style.left = left.value + "px";

```

### apply a transform

[transform](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) CSS property lets you rotate, scale, skew, or translate an element. It modifies the coordinate space of the CSS [visual formatting model](https://developer.mozilla.org/en-US/docs/Web/CSS/Visual_formatting_model).

The transform property is using one of the [CSS data types](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Types), [`<transform-function>`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function).

Doing transformation involves geometry.  
2D is described using x, y; 3D is described using x, y, z. This is referred as Euclidean space (geometry) aka Cartesian space.

However, this is not enough to describe all situation, such as projection, vanishing view point, similar to one point perspective in art.  
Extra dimension is needed to contain the "distance" information.

Projective geometry has an extra dimension, called w, in addition to the x, y, and z dimensions.

This four-dimensional space is called "projective space," and coordinates in projective space are called "homogeneous coordinates."

A point in Cartesian coordinate, (X, Y) becomes (x, y, w) in Homogeneous coordinates.  
X and Y in Cartesian are expressed with x, y and w in Homogeneous as;
X = x/w
Y = y/w

So a 2D point in cartesian coordinate is (10,2), then in homogeneous coordinate it is (10,2,1).  
The extra 1 can be see as scaling information.  
And (20,4,2), (30,6,3) are referring to the same Cartesian coordinate.

Using homogeneous coordinate in computer has one major advantages:  
matrix multiplication can be used as an unified format in expressing transformations such as translate, scale, rotation, skew, etc

matrix multiplication is "computational friendly" for computer because the operation can be highly parallelized

translation transformation, for example, in cartesian coordinate, its is addition instead of multiplication.

When multiple different kind of transformations need to apply, unifying the format is more efficient.

Overall, if we are doing 2D transformations only, homogeneous coordinate is not a must use; however, due to we can take advantage of the matrix multiplication property, it makes computing transformations much more effiency.

Refererence:  
[Explaining Homogeneous Coordinates & Projective Geometry](https://www.tomdalling.com/blog/modern-opengl/explaining-homogenous-coordinates-and-projective-geometry/)

[Homogeneous Coordinates - Problem: Two parallel lines can intersect.](https://www.songho.ca/math/homogeneous/homogeneous.html)

[Interactive guide to homogeneous coordinates](https://wordsandbuttons.online/interactive_guide_to_homogeneous_coordinates.html)

[Programmer’s guide to homogeneous coordinates](https://hackernoon.com/programmers-guide-to-homogeneous-coordinates-73cbfd2bcc65)

[The Concept Of Homogeneous Coordinates](https://prateekvjoshi.com/2014/06/13/the-concept-of-homogeneous-coordinates/)

[Why does expressing calculations as matrix multiplications make them faster?](https://softwareengineering.stackexchange.com/questions/312445/why-does-expressing-calculations-as-matrix-multiplications-make-them-faster)

[Why are Homogeneous Coordinates used in Computer Graphics?](https://computergraphics.stackexchange.com/questions/1536/why-are-homogeneous-coordinates-used-in-computer-graphics)

[What is Homogeneous Coordinates? Why is it necessary in 2D transformation?](https://math.stackexchange.com/questions/1339676/what-is-homogeneous-coordinates-why-is-it-necessary-in-2d-transformation)

#### rotate

[rotate()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate) CSS function defines a transformation that rotates an element around a fixed point on the 2D plane, without deforming it

```css
transform: rotate(45deg); /* Equal to rotateZ(45deg) */
```

#### translate (move)

[translate()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translate) CSS function repositions an element in the horizontal and/or vertical directions

```css
transform: translate(10px); /* Equal to translateX(10px) */
transform: translate(10px, 10px);
```

#### skew (distort)

[skew()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/skew) CSS function defines a transformation that skews an element on the 2D plane.
Distortion along the x-axis or y-axis or both

```css
transform: skew(10deg); /* Equal to skewX(10deg) */
transform: skew(10deg, 10deg);(10deg) */
```

#### scale (resize)

[scale()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/scale) CSS function defines a transformation that resizes an element on the 2D plane. 

```css
transform: scale(0.7); /* Equal to scaleX(0.7) scaleY(0.7) */
```

#### combine transformations

a few transformations can be applied together

```css
transform: translate(50px,0px) scale(1.5) skew(10deg, 10deg);
```

the order matters!
matrix multiplication is not commutative

### show and hide elements

Two ways to do: display / visibility

#### display
[display](https://developer.mozilla.org/en-US/docs/Web/CSS/display) CSS property sets two type of display:  

  - outer type:  
  sets an element's participation in flow layout, 
  whether an element is treated as a block or inline element
  - inner type:  
  sets the layout of children,
  layout used for its children, such as grid or flex

  commonly used value:  
  `display: block | inline | none`

##### explantion on the display detail

[`<display-outside>`](https://developer.mozilla.org/en-US/docs/Web/CSS/display-outside) keywords specify the element’s outer display type, which is essentially its role in flow layout.

- block (vertical, top to bottom)  

    The element generates a block element box, **generating line breaks** both before and after the element when in the normal flow.  

- inline (horizontal, left to right)  

    The element generates one or more inline element boxes that **do not generate line breaks** before or after themselves.  

    In normal flow, the next element will be on the same line if there is space

[`<display-box>`](https://developer.mozilla.org/en-US/docs/Web/CSS/display-box) define whether an element generates display boxes at all

- none  
    itself and it's descendents are totally removed from display, not even occupying an empty space or affect the normal flow.  

#### visibility

[visibility](https://developer.mozilla.org/en-US/docs/Web/CSS/visibility) CSS property shows or hides an element without changing the layout of a document. The property can also hide rows or columns in a `<table>`.

`visibility: visible | hidden | collapse`

- visible  
The element box is visible.
- hidden  
Element box is invisible (not drawn), but still affects layout as normal  
Descendants are visible if they have visibility set to visible
- collapse  
Collapse is treated the same as hidden except:  
Collapsed `<table >` rows, columns, hidden and space removed, similar to display: none  
Collapsed flex items, hidden, and space removed, similar to display: none  

## Implement HTML5 APIs

HTML, CSS, Javascript, each language has thier own documentation.  
For the browser's API, aka [Web API](https://developer.mozilla.org/en-US/docs/Web/API) or Javascript API, they are documented in HTML5 spec and known as HTML5 APIs. Afterall, HTML5 aims to facilitate web app creation.

### Web Storage API

Web Storage API is one of the many storage related API provided.  

[Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API) provides mechanisms by which browsers can store key/value pairs, in a much more intuitive fashion than using cookies.

two implementations of key/value web storage:  
sessionStorage & localStorage

These can be called using the [Window.sessionStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage) and [Window.localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) properties

#### Main difference for sessionStorage vs localStorage

sessionStorage  

- stores data **only for a session**  
i.e. the data is stored until the **browser (or tab) is closed**.  
- new tab or window on the same URL causes a new seperated session to be initiated, which differs  from how session cookies work
- session survives over page reloads and restores
- storage limit is 5MB per session, varies among browser, still bigger than cookie  

localStorage

- stores data with no expiration date  
i.e. data storage **persists** even when the **browser is closed and reopened**
- gets cleared only through JavaScript, or clearing the Browser cache / Locally Stored Data  
- storage limit is bigger than sessionStorage, varies among browser

#### Common for sessionStorage and localStorage

The keys and the values are always strings (objects, integer keys will be automatically converted to strings).

data stored is specific to the protocol of the page, http vs http**s**  
i.e. `http://example.com` will have separate local storage and session storage from `https://example.com`

Web Storage API implements the [Storage interface](https://developer.mozilla.org/en-US/docs/Web/API/Storage) which has the follow property and methods:  

- Storage.length (Read only)  
Return an integer representing the number of data items stored  
`var aLength = storage.length;`

- Storage.key()  
pass a integer n, return the name of the nth key in the storage, null is returned if not existed  
`var aKeyName = storage.key(index);`

- Storage.getItem()
pass a key name, return that key's value, null is returned if not existed
`var aValue = storage.getItem(keyName);`

- Storage.setItem()  
pass a key name and value  
create a new key value pair, or update the key's value if it already exists
`storage.setItem(keyName, keyValue);`

- Storage.removeItem()  
passed a key name, remove the key/value pair from the storage.
`storage.removeItem(keyName);`  

- Storage.clear()  
empty all key/value pairs out of the storage
`storage.clear();`

### Geolocation API

[Geolocation](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation) interface represents an object able to programmatically obtain the position of the device.  
Some other techniques to obtain geolocation of the device by using IP address or other device's feature or charactoristic are not covered here.

Geolocation interface has three methods

- [Geolocation.getCurrentPosition()](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/getCurrentPosition)  
get the device's current location  
call the callback function which takes Position object **once**  

  `navigator.geolocation.getCurrentPosition(success[, error[, [options]])`

- [Geolocation.watchPosition()](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/watchPosition)  
get the device's current location  
call the callback function which takes Position object **whenever the position change**  
return an integer ID for cancelling the watch

  `navigator.geolocation.watchPosition(success[, error[, options]])`

Sample code from MDN:

  ```javascript
  var options = {
    enableHighAccuracy: true,
    timeout: 5000,
    maximumAge: 0
  };

  function success(pos) {
    var crd = pos.coords;

    console.log('Your current position is:');
    console.log(`Latitude : ${crd.latitude}`);
    console.log(`Longitude: ${crd.longitude}`);
    console.log(`More or less ${crd.accuracy} meters.`);
  }

  function error(err) {
    console.warn(`ERROR(${err.code}): ${err.message}`);
  }

  navigator.geolocation.getCurrentPosition(success, error, options);
  ```

- [Geolocation.clearWatch()](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/clearWatch)  
works with Geolocation.watchPosition()  
unregister location/error monitoring handlers of the given ID

  `navigator.geolocation.clearWatch(id);`

getCurrentPosition() and watchPosition() take:  

- success callback function  
    A callback function that takes a [Position](https://developer.mozilla.org/en-US/docs/Web/API/Position) object  
- error callback function (Optional)  
    An optional callback function that takes a [PositionError](https://developer.mozilla.org/en-US/docs/Web/API/PositionError) object
- [PositionOptions](https://developer.mozilla.org/en-US/docs/Web/API/PositionOptions) object (Optional)  

  - maximumAge: integer (milliseconds) or infinity - maximum cached position age  
  - timeout: integer (milliseconds) - amount of time before the error callback is invoked, if 0 it will never invoke.  
  - enableHighAccuracy: boolean, false or true

### Service Worker API

[MDN: Service Worker](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)

## Establish the scope of objects and variables

### Define the lifetime of variables

A [variable](https://javascript.info/variables) is a “named storage” for data.  
Use the `let` keyword to declare variable.  
`let a = 0 , b = 1;`  
Variables can be have undefined value when declare and initialise later.  

The lifetime of a variable depends on where is it declared: It is valid within the block of code it is declared in. Sometime the lifetime is referred as "scope"

A variable declares inside a function is a local variable in that function and only valid when the function is executing. Exception is the case of closure.  
Using a local variable out of its scope will cause undefined exception error.

A variable declares at the outermost of the block is considered as a global variable which is alive thought out the whole program execution and therefore, can be used in different functions.  

Global variable which has a global scope is handy for pass data around, but it is also a source of confusion and bug. e.g. have "sideeffect", etc. Using of global variable should be avoided.

Do not use `var` to declare variables as it has [wider "scope"](https://javascript.info/var).

Rules about how variables should be declared and named can be found in the Clean Code book.

### keep objects out of the global namespace


### use the “this” keyword to reference an object that fired an event

  context dependent
  usually refer to the parent/caller

### scope variables locally and globally

## Create and implement objects and methods

- Implement native objects
  seven data types in JavaScript
  Six of them are called “primitive”

- create custom objects and custom properties for native objects using prototypes and functions
  objects are used to store keyed collections of various data

  Determine the object type:
  Object.prototype.constructor is a mutable property of object  
  example:
  var o = {};
  o.constructor === Object; // true

  var o = new Object;
  o.constructor === Object; // true

  var a = [];
  a.constructor === Array; // true

  var a = new Array;
  a.constructor === Array; // true

  var n = new Number(3);
  n.constructor === Number; // true

  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor

- inherit from an object
- implement native methods and create custom methods

Preparation resources

The developer’s guide to HTML5 canvas  
How to zoom and pan with SVG

# Implement Program Flow

## Implement program flow

- Iterate across collections and array items
- manage program decisions by using switch statements, if/then, and operators
- evaluate expressions

## Raise and handle an event

- Handle common events exposed by DOM (OnBlur, OnFocus, OnClick)
- declare and handle bubbled events
- handle an event by using an anonymous function

## Implement exception handling

- Set and respond to error codes
- throw an exception
  try {...} catch(e) {...}

- request for null checks
- implement try-catch-finally blocks

## Implement asynchronous programming

- Receive messages from the HTML5 WebSocket API
- use JQuery to make an AJAX call
- wire up an event
  document.getElementById(“target_id”).onclick = function () { };
  jquery use CSS selector style to select the element in DOM hierarchy:
  $('#“target_id”').click(function () { ... }

- implement a callback by using anonymous functions
  
- handle the “this” pointer

## Create a web worker process
  
  Creating a new worker
  call the Worker() constructor
  specifying the URI of a script to execute in the worker thread

  var myWorker = new Worker('worker.js');

  https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers

- Start and stop a web worker
  Start:
  myWorker.postMessage("");
  Stop, for main script to terminal the worker   
  myWorker.terminate()

  for worker to terminate itself, NOT a recommended practice
  self.close()
  ref: https://developer.mozilla.org/en-US/docs/Web/API/WorkerGlobalScope/close

- pass data to a web worker
  myWorker.postMessage([first.value,second.value]);
  any serializable object  
  native data types, JSON, XML
  can not take function

  worker accessing the passed data:
  onmessage = function(e) {
  console.log('Message received from main script');
  var passedInData1, passedInData1  = e.data[0], e.data[1];
  ......
  }

- configure timeouts and intervals on the web worker

  timeout vs interval:  
  one time vs multiple times  

  - timeout:  
  delay execute target function for specific time

  ```javascript
  var timeoutID = scope.setTimeout(code[, delay]);

  setTimeout(function(){
  worker.postMessage("");
  },3000);
  ```

  https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout

  - intervals:  
  execute target code every specific time
  
  ```javascript
  // var intervalID = scope.setInterval(code, delay);
  var intervalID;
  intervalID = setInterval(function(){
    worker.postMessage("");
  },3000);

  function stopinterval() {
    clearInterval(intervalID);
  }
  ```

  https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval

  https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Timeouts_and_intervals

- register an event listener for the web worker
  
  in web worker:
  onmessage = function(e) {
  ......
  postMessage(workerResult);
  }

  in main script:
  myWorker.onmessage = function(e) {
  result.textContent = e.data;
  console.log('Message received from worker');
  }

- limitations of a web worker
  can not pass in function  

  no limit of no. of worker, but its expensive to create one as it is like creating a thread in OS level  
  use threadpool-like design if there is a need for more workers

  no access to DOM, window object, parent object
  have to go throught the main script by sending message to it

  sub-workers: Workers spawned by workers
  URIs for subworkers are resolved relative to the parent worker's location

Preparation resources

Controlling program flow (JavaScript)  
Coding basic apps  
try...catch...finally statement (JavaScript)

# Access and Secure Data

## Validate user input by using HTML5 elements

- Choose the appropriate controls based on requirements
- implement HTML input types and content attributes to collect user input

  attribute:
  pattern

## Validate user input by using JavaScript

- Evaluate a regular expression to validate the input format  

  2 ways:  
  - constuct regular expression and use test() method  
  return: bool

  ```javascript
  var str = 'hello world!';
  var result = /^hello/.test(str);
  console.log(result); // true
  ```

  [MDN: RegExp.prototype.test()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test)  

  - use the input value match() method  
   return: an Array containing the entire matched string as the first element, and info related

  ```javascript
  var str = 'For more information, see Chapter 3.4.5.1';
  var re = /see (chapter \d+(\.\d)*)/i;
  var found = str.match(re);

  console.log(found);

  // logs [ 'see Chapter 3.4.5.1',
  //        'Chapter 3.4.5.1',
  //        '.1',
  //        index: 22,
  //        input: 'For more information, see Chapter 3.4.5.1' ]

  // 'see Chapter 3.4.5.1' is the whole match.
  // 'Chapter 3.4.5.1' was captured by '(chapter \d+(\.\d)*)'.
  // '.1' was the last value captured by '(\.\d)'.
  // The 'index' property (22) is the zero-based index of the whole match.
  // The 'input' property is the original string that was parsed.
  ```

  [MDN: String.prototype.match()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match)  

- validate that you are getting the right kind of data type by using built-in functions
- prevent code injection

## Consume data

- Consume JSON and XML data
- retrieve data by using web services
- load data or get data from other sources by using XMLHTTPRequest

## Serialize, deserialize, and transmit data

- Handle binary data
- handle text data such as JSON and XML
- implement the JQuery serialize method
   jQuery.serialize method handles the extraction of the data from all the input elements and creates the query string. the query string is also encoded
   var qString = $(this).serialize();

   decodeURIComponent(qString)
   https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/decodeURIComponent

- use Form.Submit
- parse data
  parseInt(string, radix)
  function parses a string and returns an integer

  ref: http://www.w3schools.com/jsref/jsref_parseint.asp
- send data by using XMLHTTPRequest
- sanitize input by using URI/form encoding

Preparation resources  
pattern attribute | pattern property  
Sandbox  
XMLHttpRequest object

# Use CSS3 in Applications

## Style HTML text properties

- Apply styles to text appearance
  text-transform: none | capitalize | uppercase | lowercase

  ref: https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform

- apply styles to text font, including WOFF, @font-face, size, and understudy fonts
- apply styles to text alignment, spacing, and indentation
- apply styles to text hyphenation
- apply styles for a text drop shadow

## Style HTML box properties

- Apply styles to alter appearance attributes, including size, borders, rounded corners, outline, padding, and margin  

https://www.w3schools.com/cssref/pr_margin-left.asp
https://www.w3schools.com/cssref/pr_border-style.asp

- apply styles to alter graphic effects, including transparency, opacity, background image, gradients, shadow, and clipping

box shadow

text shadow
- apply styles to establish and change an element’s position

## Create a flexible content layout

- Implement a layout using a flexible box model
  
  https://css-tricks.com/snippets/css/a-guide-to-flexbox/

- implement a multi-column layout
- implement a layout using position floating and exclusions
  

- implement a layout using grid alignment
- implement a layout using regions, grouping, and nesting

## Create an animated and adaptive UI

- Animate objects by applying CSS transitions
  https://css-tricks.com/almanac/properties/t/transition/
  https://www.w3schools.com/cssref/css3_pr_transition.asp
- apply 3-D and 2-D transformations
- adjust UI based on media queries, including device adaptations for output formats, displays, and representations
  The media query syntax is as simple as adding the following to your CSS file:
  @media screen and (min-width: 1200px) {
  }

  @media screen and (max-width: 1199px) and (min-width: 401px) {
  }

  @media screen and (max-width: 400px) {
  }

  <link rel="stylesheet" media="screen and (min-width: 1200px)" href="Desktop.css"/>
  <link rel="stylesheet" media="screen and (max-width: 1199px) and (min-width: 401px)"
ref="tablet.css"/>
  <link rel="stylesheet" media="screen and (max-width: 400px)" href="phone.css"/>

- hide or disable controls

## Find elements by using CSS selectors and JQuery

- Choose the correct selector to reference an element
  
  jQuery extension and not part of the CSS specification:
  :header
  $( ":header" ).css({ background: "#ccc", color: "blue" });
  https://www.w3schools.com/jquery/sel_header.asp
  https://api.jquery.com/header-selector/

- define element, style, and attribute selectors
- find elements by using pseudo-elements and pseudo-classes
  if two selectors are equal in specificity:  
  the selector further down the stylesheet wins  

  example:  
  if the :active style rule is above the :hover style rule:  
  users will never get to see the :active style rule applied  
  because the :hover style rule supersedes it.

suggested order:

  a { }
  a:link { }
  a:visited { }
  a:hover { }
  a:focus { }
  a:active { }
  ref: https://www.webfx.com/blog/web-design/link-pseudo-classes/

## Structure a CSS file by using CSS selectors

- Reference elements correctly
- implement inheritance

  Specifics on CSS Specificity
  the cascade is:
  who override who, ID > class > element
  ref: https://www.w3.org/TR/css3-cascade/#cascaded
  ref: https://designshack.net/articles/css/what-the-heck-is-css-specificity/
  ref: https://css-tricks.com/specifics-on-css-specificity/


- override inheritance by using !important

  By default, rules in an author’s style sheet override those in a user’s style sheet, which override those in the user-agent’s default style sheet.  

  To balance this, a declaration can be made important, which increases its weight in the cascade and inverts the order of precedence.  

  ref: https://www.w3.org/TR/css-cascade-3/#importance


- style an element based on pseudo-elements and pseudo-classes

Preparation resources

Text  
How to add drop shadows with CSS3  
CSS

# Reference

- [MDN: Mozilla Developer Network]  

[MDN: Mozilla Developer Network]: https://developer.mozilla.org/  

- [HTML5 For Web Designers]

[HTML5 For Web Designers]: https://html5forwebdesigners.com/

- [Exam Ref 70-480: Programming in HTML5 with JavaScript and CSS3]

[Exam Ref 70-480: Programming in HTML5 with JavaScript and CSS3]: https://www.microsoftpressstore.com/store/exam-ref-70-480-programming-in-html5-with-javascript-9780735676633

HTML CSS the missing manual  
HTML5 reference book  

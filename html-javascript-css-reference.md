
# Implement and Manipulate Document Structures and Objects
  
  HTML is for providing a structure to a document.  
  A document contains text, reference to other document, image, video; HTML uses tags to mark each piece of content in the document for describing  what it is about. This marking process provides a structure to the document.
  Without this special processing or "mark up", the computer will not understand the content inside document very well.

  Providing a structure leads to better browser rendering, i.e. improve readability, provide built-in features; It also helps the search engine to understand the document better, hence improve indexing and search result.  

  A structure enables styling the document using external style sheet (CSS) by selecting the target element to be styled; and manipulate the content in the document using programming language (JS) via object mode representation which HTML can provide.
  CSS and JS are essential for building experience rich and interactive website aka web app.
  
  note: Most content here refers to [MDN: Mozilla Developer Network] and [HTML5 For Web Designers]

## Create the document structure by using HTML

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

[`aside`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/aside) represent a portion of a document whose content is seperated from or only indirectly related to the main content. i.e. could be removed without reducing the meaning of the main content of the document or section. Nice to have but can be removed.  
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
  <meta name="description" content="The MDN Web Docs site 
    provides information about Open Web technologies 
    including HTML, CSS, and APIs for both Web sites and 
    progressive web apps.">
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

- Programmatically add and modify HTML elements  
- Implement media controls


- implement HTML5 canvas and SVG graphics
  
  - HTML5 canvas:  
    rotate:  tbc

    rect method: a special fill method specifically for rect called fillRect  
    create and fill your rectangle in one call:

    ```javascript
    ctxt.fillStyle = "blue";
    ctxt.fillRect(300—(x / 2), 200—(y / 2), x, y);
    ```

  - SVG graphics  

    angle()

## Apply styling to HTML elements programmatically

- Change the location of an element
- apply a transform
- show and hide elements

## Implement HTML5 APIs

- Implement storage APIs and the Geolocation API

## Establish the scope of objects and variables

- Define the lifetime of variables
- keep objects out of the global namespace
- use the “this” keyword to reference an object that fired an event
  context dependent
  usually refer to the parent/caller

- scope variables locally and globally

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

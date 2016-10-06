# HTML Coding Conventions

> Our target is HTML5.

## Table of Contents

  1. [General formatting](#general-formatting)
  1. [Default structure](#default-structure)
  1. [Elements](#elements)
  1. [Attributes](#attributes)
  1. [Courtesies](#courtesies)
  1. [Semantic Elements](#semantic-elements)
  1. [Recommendation](#recommendation)
  1. [Resources](#resources)

## General formatting

  * Paragraphs of text should always be placed in a `<p>` tag. Never use multiple `<br>` tags.
  * Items in list form should always be in `<ul>`, `<ol>`, or `<dl>`. Never use a set of `<div>` or `<p>`.
  * Every form input that has text attached should utilize a `<label>` tag. **Especially radio or checkbox elements.**
  * Even though quotes around attributes is optional, always put quotes around attributes for readability.
  * Avoid writing closing tag comments, like `<!-- /.element -->`. This just adds to page load time. Plus, most editors have indentation guides and open-close tag highlighting.
  * Avoid trailing slashes in self-closing elements. For example, `<br>`, `<hr>`, `<img>`, and `<input>`.
  * Don't set `tabindex` manually—rely on the browser to set the order.

## Default structure

  ```html
  <!DOCTYPE html>
  <html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Document</title>
    <link rel="stylesheet" href="assets/css/styles.css">
  </head>
  <body>
    <div id="wrapper">    
      <header id="head">
        <div class="container">
          <nav>...</nav>
        </div>    
      </header>   
      <div id="page-content">
        <section id="news" class="container">   
          <article id="content-article">
            <h2>...</h2>
            <p>...</p>
          </article>
          <aside id="content-table">
          ...
          </aside>
        </section>
        <section id="comments">
        ...
        </section>

      </div>
      <footer>
        <div class="container">   
          <p>Copyright &copy; 2016 Asian Tech Co., Ltd.</p>
        </div>    
      </footer>
    </div>
    <script src="assets/js/script.js"></script>
  </body>
  </html>
  ```

## Elements

  * Add closing tags to elements that aren't self-closing.
  * Don't add the forward slash for self-closing elements.
  * Avoid unnecessary markup, such as surrounding a block element in a ```<div>```.
  * Use lowercase, not uppercase for File Names, Attribute Names, Element Names.

  ```html
  <!--Bad-->
  <DIV>
    <UL>
      <LI>Item 1
      <LI>Item 2
    </UL>
  </DIV>
  <INPUT type="text" />

  <!--Good-->
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
  </ul>
  <input type="text">
  ```

  ```html
  <!-- Bad -->
  <div CLASS="menu">

  <!-- Good -->
  <div class="menu">
  ```

  - `image.jpg` cannot be accessed as `Image.jpg`

  * Use correct HTML5 tags for each content. Avoid using divs for everything.
  * Avoid using P, SPAN for structuring

  ```html
  <section>       <!-- for each big content block on the same page. -->
  <aside>         <!-- for left/right hand side content -->
  <article>       <!-- for each item that has title/content structure -->
  <h1><h2>...<h6> <!-- for title or text with big fonts -->
  <nav>           <!-- for menu/navigation -->
  <header>        <!-- for header section -->
  <footer>        <!-- for footer section -->
  ```

## Attributes

  * Surround values for attributes in double quotes.
  * Boolean attributes, such as required, do not need a value.
  * Follow this order for attributes:
    * class
    * id, name
    * data-*
    * src, for, type, href, value
    * title, alt
    * role, aria-*

  ```html
  <!-- Bad -->
  <input type='radio' class="input" required='true'>

  <!-- Good -->
  <input class="input" type="radio" required>

  <a href="#" class="..." id="..." data-toggle="modal">
    Example link
  </a>

  <input class="form-control" type="text">

  <img src="..." alt="...">
  ```
## Courtesies

  * Put a single line break between blocks/components.
  * Avoid adding comments. An exception would be a closing comment for large blocks.

  ```html
  <div class="video-player">
    ...
  </div>

  <div class="comment-list">
    ...
  </div>
  ```

## Semantic Elements

  * HTML5 offers new semantic elements to define different parts of a web page:

  ```html
  <article>    <!-- specifies independent, self-contained content -->
  <aside>      <!-- defines some content aside from the content it is placed in (like a sidebar) -->
  <details>    <!-- defines additional details that the user can view or hide -->
  <figcaption> <!-- defines a caption for a `<figure>` element -->
  <figure>     <!-- specifies self-contained content, like illustrations, diagrams, photos, code listings, etc -->
  <footer>     <!-- specifies a footer for a document or section -->
  <header>     <!-- specifies a header for a document or section -->
  <main>       <!-- specifies the main content of a document -->
  <mark>       <!-- defines marked/highlighted text -->
  <nav>        <!-- defines a set of navigation links -->
  <section>    <!-- defines a section in a document -->
  <summary>    <!-- defines marked/highlighted text -->
  <time>       <!-- defines a date/time -->
  ```

## Recommendation

### The Difference Between ID and Class

  * The simple difference between the two is that while a class can be used repeatedly on a page, an ID must only be used once per page. Therefore, it is appropriate to use an ID on the div element that is marking up the main content on the page, as there will only be one main content section. In contrast, you must use a class to set up alternating row colors on a table, as they are by definition going to be used more than once.

  * ID's are unique :
    - Each element can have only one ID.
    - Each page can have only one element with that ID.

  * Classes are NOT unique :
    - You can use the same class on multiple elements.
    - You can use multiple classes on the same element.

  * ID's have special browser functionality

  * Classes have no special abilities in the browser, but ID's do have one very important trick up their sleeve. This is the "hash value" in the URL. If you have a URL like http://yourdomain.com#comments, the browser will attempt to locate the element with an ID of "comments" and will automatically scroll the page to show that element. It is important to note here that the browser will scroll whatever element it needs to in order to show that element, so if you did something special like a scrollable DIV area within your regular body, that div will be scrolled too.

  * This is an important reason right here why having ID's be absolutely unique is important. So your browser knows where to scroll!

  * Elements can have BOTH

  * There is nothing stopping you from having both an ID and a Class on a single element. In fact, it is often a very good idea. Take for example the default markup for a WordPress comment list item:

  ```html
  <li id="comment-27299" class="item">
  ```

### Do not use inline style attributes

  * As much as possible, use css classes instead of using inline style attributes. This has the advantages:
  Makes it easier to change the look of the UI by changing the stylesheet
  Makes it possible to reuse the css class in another place, giving a more consistent UI and making it possible to change the look by changing only one place.

  ```html
  <!-- Bad -->
  <div style="width:100px;align:center;">

  <!-- Good -->
  <div class="message">
  ```

## Resources

  - A list of everything that could go in the <head> of your document: https://github.com/joshbuchea/HEAD


## What is the DOM?

The DOM is a W3C (World Wide Web Consortium) standard.

The DOM defines a standard for accessing documents:

_"The W3C Document Object Model (DOM) is a platform and language-neutral interface that allows programs and scripts to dynamically access and update the content, structure, and style of a document."_

The W3C DOM standard is separated into 3 different parts:

- Core DOM - standard model for all document types
- XML DOM - standard model for XML documents
- HTML DOM - standard model for HTML documents

## The DOM Programming Interface

The HTML DOM can be accessed with JavaScript (and with other programming languages).

In the DOM, all HTML elements are defined as **objects**.

The programming interface is the properties and methods of each object.

A **property** is a value that you can get or set (like changing the content of an HTML element).

A **method** is an action you can do (like add or deleting an HTML element).


#### getElementById

The most common way to access an HTML element is to use the `id` of the element.

`<p id="demo"></p> ` 
`<script>document.getElementById("demo").innerHTML = "Hello World!";</script> `

#### Add Event Listener DOM Event Types
The browser can trigger many different types of events on the DOM(Document Object Model).

Here are some of the most common event types and event names:

- Mouse Events: click, dblclick, mousedown, mouseup, contextmenu, mouseout, mousewheel, mouseover
- Touch Events: touchstart, touchend, touchmove, touchcancel
- Keyboard Events: keydown, keyup, keypress
- Form Events: focus, blur, change, submit
- Window Events: resize, scroll, load, unload, hashchange

Form Events(focus, blur, change, submit):

- focus: An element that has received focus.
- blur: An element that has lost focus.
- change: Event that is fired for input, select, and textarea elements when an alteration to the element’s value is done by the user.
- submit: The submit button is pressed.

Window Events(resize, scroll, load, unload, hashchange):

- resize: This event fires when the document view(window) has been resized.
- scroll: Event fires when the document view or an element has been scrolled.
- load/unload: The load event is fired when the whole page has loaded, including all resources such as css and images. Unload is when the document or child resource is being unloaded.
- hashchange: This event is fired when the identifier of the URL has changed(the part of the URL that begins with a # symbol).

#### querySelector()
The `querySelector()` method returns the **first** element that matches a CSS selector.

To return **all** matches (not only the first), use the `querySelectorAll()` instead.

Both `querySelector()` and `querySelectorAll()` throw a SYNTAX_ERR exception if the selector(s) is invalid.

Get the first element with class="example":

`document.querySelector(".example");`


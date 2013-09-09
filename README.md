# Basic jQuery

## Using jQuery
Download a copy of jQuery from the [jQuery website](http://jquery.com/download/). You can either use the uncompressed or compressed version and either version `1.x` or `2.x`. I recommend you download the uncompressed version `1.x` for this tutorial because it is easier to debug and it works in most browsers.

Place it in a `js` directory.
```
js/
-- jquery-1.10.2.js
index.html
```

Inside your html file, add this code:

```html
<!doctype html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>jQuery Tutorial</title>
	<script src="js/jquery-1.10.2.js"></script>
</head>
<body>

</body>
</html>
```

We included jQuery in our file using the `<script>` tag.

The order of your `<script>` tags is important. If you have code that uses jQuery, make sure they come after your jQuery `<script>`.


## jQuery Object
Invoke jQuery using `$`, often followed by a parenthesis containing your selected object.

```js
$(<selector>);

$(<DOM_object>);
```

This will return a jQuery object. You can pass the jQuery object to another variable. A good coding practice is to prefix your variables with a `$` when referring to jQuery objects.

```js
var $document = $(document);

var $myDiv = $('#myDiv');
```

## Selectors

jQuery selectors follows more or less the same standard with CSS selectors

The common 3 types of selectors are listed below. Most often, you'll use a class or ID selector. Check out the [jQuery website](http://api.jquery.com/category/selectors/) to learn about other types of selectors.

### HTML element selector
```js
// Selects all <h1> elements
$('h1');
```

### Class selector
```js
// Selects all elements with a myClass
$('.myClass');
```

### ID selector
```js
// Selects an element with an ID username
$('#username');
```

## Calling jQuery functions when page loads

The best way to call jQuery functions is to invoke them after the HTML page loads. This ensures that all of the HTML elements exist.

To do this, we will call the `ready()` function of `document`.

```js
$(document).ready(function () {
	// Anything inside will be called when the page is done loading
});
```

There's also a shortcut:

```js
$(function () {
	// This is the same with the code above
});
```


## Common jQuery functions

### `css()`, `addClass()`, `removeClass()`, and `hasClass()`
You can add inline CSS using the `css()` function.

```js
$('#myDiv').css('background-color', '#cccccc');
```

To add and remove CSS classes, use `addClass()` and `removeClass()`.
```js
$('#myDiv').addClass('myClass');

$('#myDiv').removeClass('myOtherClass');
```

NOTE: `addClass()` appends the new class. It does not erase the other classes.

You can check if an element contains a certain class using `hasClass()`.

```js
var $myDiv = $('#myDiv');

if($myDiv.hasClass('someClass')) {

}
else {

}
```

### `show()`, `hide()`, and `toggle()`
One of the neat features of jQuery is it allows you to display or hide certain elements.

Use `show()` to display a hidden element. And use `hide()` to conceal it.

```js
$('#myDiv1').show();

$('#myDiv2').hide();
```

If you want to switch between these two, use `toggle()`.

```js
// Assume that #myDiv is visible

$('#myDiv').toggle(); // #myDiv is now hidden

$('#myDiv').toggle(); // #myDiv is now shown
```

### `html()` and `val()`
To get everything inside an element, use `html()`.

```js
// Let's assume we have this element <div id="myDiv">hello world</div>

var x = $('#myDiv').html();

// x now contains "hello world"
```

If you're dealing with elements that use the `value` property, such as `<input type="text">`, call `val()` instead.

```js
// Let's assume we have an element <input type="text" id="username" />

var x = $('#username').val();
```

Anything that our user types in the `#username` textbox gets stored inside the `value` property. To access this, we use `val()`.

We can also use `html()` and `val()` to set the values of elements by passing a parameter.

```js
$('#myDiv').html('some new text');

$('#myTextbox').val('some other text');
```

### `prop()` and `data()`
To access other HTML attributes and properties, we can use the `prop()` function.

```js
// Let's assume we have this element <div id="myDiv" class="myFirstClass mySecondClass"></div>

var x = $('#myDiv').prop('class');

// x now contains "myFirstClass mySecondClass"
```

To set the value of a property, pass a second parameter.

```js
$('#myDiv').prop('class', 'someClass');

// Take note that this replaces the old value of the property
```

NOTE: There's also the `attr()` function which is in most cases similar to `prop()`. But `prop()` works best in most cases.

If you want to use your own custom properties, prefix your property with `data-` and use jQuery's `data()` function to access the value.

```js
// Let's assume we have this element <div id="myDiv" data-hello="world"></div>

var x = $('#myDiv').data('hello');

// x now contains "world"
```

Notice that our property is named `data-hello` but the identifier that we passed to `data()` was `hello`.

### `click()`
The `onclick` event is one of the most common events used in JavaScript. Using jQuery, we use `click()` to bind an `onclick` event to an element.

```js
// Assume we have this element <button id="myBtn" type="button">Click Me</button>

$('#myBtn').click(function (e) {
	// Any code here will run when the button is clicked
});
```

There are elements which have default actions when it is clicked. For example, an `<a>` tag will redirect to a location. To stop this from happening, use `e.preventDefault()`.

```js
// Assume we have this element <a id="myLink" href="#">Click Me</a>

$('#myLink').click(function (e) {
	e.preventDefault();

	// Any code here will run and the <a> won't redirect the page
});
```

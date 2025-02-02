# JQuery

-  All jQuery functions start with a $, usually referred to as a dollar sign operator, or as bling.

- jQuery often selects an HTML element with a selector, then does something to that element.

- jQuery has a .addClass() function, which allows you to add classes to elements.

- All the jquery code is typically written inside a document ready function.

- jQuery has a function called .css() that allows you to change the CSS of an element.

```js
$("#target1").css("color", "blue");
```

- This is slightly different from a normal CSS declaration, because the CSS property and its value are in quotes, and separated with a comma instead of a colon.

- jQuery has a function called .prop() that allows you to adjust the properties of elements.

```js
$("button").prop("disabled", true);
```

- jQuery has a function called .html() that lets you add HTML tags and text within an element. Any content previously within the element will be completely replaced with the content you provide using this function.

- jQuery also has a similar function called .text() that only alters text without adding tags. In other words, this function will not evaluate any HTML tags passed to it, but will instead treat it as the text you want to replace the existing content with.

- jQuery has a function called .remove() that will remove an HTML element entirely.

- Query has a function called appendTo() that allows you to select HTML elements and append them to another element.

```js
$("#target4").appendTo("#left-well");
```

- jQuery has a function called clone() that makes a copy of an element.
- For example, if we wanted to copy target2 from our left-well to our right-well, we would use:
```js
$("#target2").clone().appendTo("#right-well");
```

- Did you notice this involves sticking two jQuery functions together? This is called function chaining and it's a convenient way to get things done with jQuery.

- jQuery has a function called parent() that allows you to access the parent of whichever element you've selected.

```js
$("#left-well").parent().css("background-color", "blue")
```

- jQuery has a function called children() that allows you to access the children of whichever element you've selected.
```js
$("#left-well").children().css("color", "blue")
```

- jQuery uses CSS Selectors to target elements. The target:nth-child(n) CSS selector allows you to select all the nth elements with the target class or element type.
- Here's how you would give the third element in each well the bounce class:
```js
$(".target:nth-child(3)").addClass("animated bounce");
```

- You can also target elements based on their positions using :odd or :even selectors.

Note that jQuery is zero-indexed which means the first element in a selection has a position of 0. This can be a little confusing as, counter-intuitively, :odd selects the second element (position 1), fourth element (position 3), and so on.

```js
$(".target:odd").addClass("animated shake");
```

-
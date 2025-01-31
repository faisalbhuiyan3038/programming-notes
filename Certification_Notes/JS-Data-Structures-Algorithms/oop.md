# Object Oriented Programming

- In JavaScript, a class is like a blueprint for creating objects. It allows you to define a set of properties and methods, and instantiate (or create) new objects with those properties and methods.

- Classes have a special constructor method, which is called when a new instance of the class is created. The constructor method is a great place to initialize properties of the class.
```js
class Computer {
  constructor() {
  }
}
```

- The this keyword in JavaScript is used to refer to the current object. Depending on where this is used, what it references changes. In the case of a class, it refers to the instance of the object being constructed.

- Example of instantiating an object
```js
const myComputer = new Computer();
```

- You need to iterate through the buttons in your addToCartBtns variable. However, .getElementsByClassName() returns a Collection, which does not have a forEach method.

- Use the spread operator on the addToCartBtns variable to convert it into an array. Then, use the forEach method to iterate through the array. Do not pass a callback function yet.
- We want to clean up the number result from your calculation. Wrap your calculation in parentheses (don't include the return statement!) and call the .toFixed() method on it. Pass the .toFixed() method the number 2 as an argument. This will round the number to two decimal places and return a string.

- Browsers have a built-in confirm() function which displays a confirmation prompt to the user. confirm() accepts a string, which is the message displayed to the user. It returns true if the user confirms, and false if the user cancels.

-  the context of this will be the clearCartBtn element. You need to bind the clearCart method to the cart object.

You can do this by passing cart.clearCart.bind(cart) as the callback.

- The Canvas API can be used to create graphics in games using JavaScript and the HTML canvas element.

- You will need to use the getContext method which will provide the context for where the graphics will be rendered.

- The canvas element has a width property which is a positive number that represents the width of the canvas.

- The innerWidth property is a number that represents the interior width of the browser window.

- The requestAnimationFrame() web API, takes in a callback and is used to update the animation on the screen. The animate function will be responsible for updating the player's position and continually drawing it on the canvas.

- As the player moves through the game, you will need to clear the canvas before rendering the next frame of the animation.

You can use the clearRect() Web API to accomplish this. It takes in an x, y, width, and height arguments.
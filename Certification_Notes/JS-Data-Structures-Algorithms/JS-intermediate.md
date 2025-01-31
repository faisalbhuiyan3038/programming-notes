# JS Intermediate

- The find() method retrieves the first element within an array that fulfills the conditions specified in the provided callback function. If no element satisfies the condition, the method returns undefined.

- The indexOf() array method returns the first index at which a given element can be found in the array, or -1 if the element is not present.

- The forEach method is used to loop through an array and perform a function on each element of the array.

- The createTextNode() method is used to create a text node. To use it, you call it and pass in the text as a string.

- Regex expressions should be like `\[^a-zA-Z0-9]\g` where `\\` encompassess the expression, `^` means beginning of string and `$` means end of string. and g means global as in search all matches not just the first one.

---
---

- In JavaScript, there are many built-in constructors that create objects. A constructor is like a regular function, but starts with a capital letter, and is initialized with the new operator.

- The .getDate() method, which returns a number between 1 and 31 that represents the day of the month for that date.

- The .getMonth() method returns a number between 0 and 11.

- The .getFullYear() method returns a number which represents the year for the provided date.

- The .getHours() method returns a number between 0 and 23. This represents the hour for the provided date, where 0 is midnight and 23 is 11 p.m.

- The .getMinutes() method returns a number between 0 and 59 which represents the minutes for the provided date.

- In JavaScript, the change event is used to detect when the value of an HTML element has changed.

- The split() method is used to divide a string into substrings based on a specified separator. It then returns these substrings as elements of an array.

- The Object.freeze() method is used to prevent the modification of an object's properties or elements.

- The object destructuring syntax allows you to unpack values from arrays and objects.
Example:
```js
const [x, y] = [1, 2];
const { sport, team, year, players } = myFavoriteFootballTeam;
```

- In JavaScript, the map method is used to create a new array by calling a provided callback function on every element in the array it is called on. This callback function is applied to each element, and the results are collected into a new array.

- In JavaScript, the filter method is used to create a new array with all elements that pass the test implemented by the provided callback function. The callback function is applied to each element of the array, and only the elements that return true in the callback function are included in the new array.

---
---

### LocalStorage

- A modal is an element that prevents all interaction with elements outside it until the modal has been dismissed.
- The HTML dialog element has a showModal() method that can be used to display a modal dialog box on a web page.

```js
dialogElement.showModal();
```

- localStorage offers methods for saving, retrieving, and deleting items. The items you save can be of any JavaScript data type.
```js
localStorage.setItem("key", value);
```

- everything you save in localStorage needs to be in string format.

-  you can retrieve it with getItem() by specifying the key you used to save the item.

- Rather than check if a value is equal to a falsy value, you can use the logical NOT operator (!) to check if the value itself is falsy. For example:
```js
const num = 0;

console.log(num === 0); // true
console.log(!num); // true
```

- A good way to check and normalize numbers in JavaScript is to use the built-in parseInt() function, which converts a string into an integer or whole number. parseInt() takes at least one argument, a string to be converted into an integer, and returns either an integer or NaN which stands for Not a Number.

- you need to check if the value returned by the parseInt() function is a number or not.

- To do that, you can use the isNaN() function. This function takes in a string or number as an argument, and returns true if it evaluates to NaN.

- Next, you need to calculate the remainder of input divided by 2. You can do this by using the remainder operator (%), which returns the remainder of the division of two numbers.
```js
const remainder = 5 % 2; // 1
```


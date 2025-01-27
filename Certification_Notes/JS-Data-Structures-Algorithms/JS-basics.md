# JS Basics

- Variable naming follows specific rules: names can include letters, numbers, dollar signs and underscores but cannot contain spaces or start with numbers.

- Strings are immutable, which means that once a string is created, it cannot be changed. The variable can be reassigned a new value, but the value itself cannot be changed.

- In js, the convention is to use camelCase for variable names.

- Array is a non-primitive data type. A non-primitive data type means that it is not only a collection of values, but also has properties and methods associated with it.

- Arrays are mutable. This means you can change the value at an index directly.

- array.length returns number of elements.

- A method in JavaScript is a function that's associated with certain values or objects. An example you've already encountered is the .log() method, which is part of the console object.

- pop returns the removed element, while push returns the length after the additon.

- for loop in js is with semi-colons

- The iterator is a variable you can declare specifically in your for loop to control how the loop iterates or goes through your logic.

- The condition of a for loop tells the loop how many times it should iterate. When the condition becomes false, the loop will stop.

- a for...of loop, iterates over each item in an iterable object and temporarily assigns it to a variable.
```js
for (const value of iterable) {

}
```
- Note that you can use const because the variable only exists for a single iteration, not during the entire loop.

- strings have a .repeat method that allows you to repeat a string a certain number of times.

- Note that the order of operations rule PEMDAS—Parenthesis, Exponents, Multiplication, Division, Addition, Subtraction—applies

- A truthy value is a value that is considered true when evaluated as a boolean. Most of the values you encounter in JavaScript will be truthy.

- A falsy value is the opposite - a value considered false when evaluated as a boolean. JavaScript has a defined list of falsy values. Some of them include false, 0, "", null, undefined, and NaN.

- A while loop will run over and over again until the condition specified is no longer true. It has the following syntax:
```js
while (condition) {
    statement(s);
}
```

- The strict equality operator === is used to check if two values are equal and share the same type. As a general rule, this is the equality operator you should always use.

- The .unshift() method of an array allows you to add a value to the beginning of the array, unlike .push() which adds the value at the end of the array. .unshift() returns the new length of the array it was called on.

- Arrays also have a .shift() method. This will remove the first element of the array, unlike .pop() which removes the last element.
---
---

- One method for finding specific elements in your HTML is using the querySelector() method. The querySelector() method takes a CSS selector as an argument and returns the first element that matches that selector.

- You have repetition in the goTown and goStore functions. Repetition in your code is a sign that you need another function.

- Objects are non primitive data types that store key-value pairs. Non primitive data types are mutable data types that are not undefined, null, boolean, number, string, or symbol. Mutable means that the data can be changed after it is created.

- If the property name (key) of an object has a space in it, you will need to use single or double quotes around the name.

- There are two ways to access the properties of an object: dot notation (.) and bracket notation ([]), similar to an array.

- Dot notation is what you use when you know the name of the property you're trying to access ahead of time.

- The second way to access the properties of an object is bracket notation ([]). If the property of the object you are trying to access has a space in its name, you will need to use bracket notation.

- The style property is used to access the inline style of an element and the display property is used to set the visibility of an element.

---
---

- The Math object in JavaScript contains static properties and methods for mathematical constants and functions.
- One of those is Math.random(), which generates a random number from 0 (inclusive) to 1 (exclusive).
- Another is Math.floor(), which rounds a given number down to the nearest integer.
- Using these, you can generate a random number within a range. For example, this generates a random number between 1 and 5: Math.floor(Math.random() * 5) + 1;.
- The ternary operator is a conditional operator and can be used as a one-line if-else statement. The syntax is: condition ? expressionIfTrue : expressionIfFalse.
- The .includes() method determines if an array contains an element and will return either true or false.

---

- If the arrow function is returning a simple expression, you can omit the return keyword and the curly braces {}. This is called an implicit return.
- If your arrow function has multiple lines of code in the function body, then you need to use the return keyword and the curly braces {}.
- The map() method is used to iterate through an array and return a new array. It's helpful when you want to create a new array based on the values of an existing array.
```js
const numbers = [1, 2, 3];
const doubledNumbers = numbers.map((number) => number * 2); // doubledNumbers will be [2, 4, 6]
```

- Notice that the map() method takes a function as an argument. This is called a callback function, which is a function that is passed to another function as an argument.

- The join() method is used to concatenate all the elements of an array into a single string. It takes an optional parameter called a separator which is used to separate each element of the array.

- Optional chaining (?.) helps prevent errors when accessing nested properties that might be null or undefined.

- The sort() method converts elements of an array into strings and sorts them in place based on their values in the UTF-16 encoding.

- To sort the songs in alphabetical order by title, you will need to pass in a compare callback function into your sort() method.

- Here is an example of sorting a list of fruits by name.

```js
const fruits = [
  { name: "Apples", price: 0.99 },
  { name: "Blueberries", price: 1.49 },
  { name: "Grapes", price: 2.99 },
];

fruits.sort((a, b) => {
  if (a.name < b.name) {
    return -1;
  }

  if (a.name > b.name) {
    return 1;
  }

  return 0;
});
```

-

```txt
The sort() method accepts a compare callback function that defines the sort order.

In this example, the first condition (a.name < b.name) checks if the name of the first fruit is less than the name of the second fruit. If so, the first fruit is sorted before the second fruit.

Strings are compared lexicographically which means they are compared character by character. For example, "Apples" is less than "Bananas" because "A" comes before "B" in the alphabet.

The reason why this example is returning numbers is because the sort() method is expecting a number to be returned. If you return a negative number, the first item is sorted before the second item.
```


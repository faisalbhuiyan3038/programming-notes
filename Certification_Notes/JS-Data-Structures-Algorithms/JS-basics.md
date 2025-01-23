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
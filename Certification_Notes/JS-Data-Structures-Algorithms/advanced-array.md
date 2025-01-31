# Advanced Array

- The method split() takes a string and splits it into an array of strings. It takes an optional separator or a Regex to use as the separator. This is where the split would occur.

- The value of an input element is always a string, even if the input type is number.

- You want to make sure that you are only working with numbers. The Number() constructor will return NaN (which stands for "not a number") if the value passed to it cannot be converted to a number.

- The filter method needs to return true or false based on a condition. If it's false, its omitted, if its true, its kept.

- Array methods can be chained together. For example .map.reduce;

- The reduce() array method takes an array and applies a callback function to condense the array into a single value. Perfect for summing an array of numbers.

- The .reduce() method takes a second argument that is used as the initial value of the accumulator. Without a second argument, the .reduce() method uses the first element of the array as the accumulator, which can lead to unexpected results.

- To be safe its best to set an initial value.
- Here is example of setting intial value of reduce to empty string.
```js
array.reduce((acc, el) => acc + el.toLowerCase(), "");
```

- By default, the .sort() method converts the elements of an array into strings, then sorts them alphabetically. The .sort() method mutates the original array. This works well for strings, but not so well for numbers. For example, 10 comes before 2 when sorted as strings, but 2 comes before 10 when sorted as numbers.

- To fix this, you can pass in a callback function to the .sort() method. This function takes two arguments, which represent the two elements being compared. The function should return a value less than 0 if the first element should come before the second element, a value greater than 0 if the first element should come after the second element, and 0 if the two elements should remain in their current positions.

- To sort your numbers from smallest to largest, pass a callback function that takes parameters a and b, and returns the result of subtracting b from a.

```js
// check if array length is even
arr.length % 2 === 0;

// check if array length is odd
arr.length % 2 === 1;
```

- The .sort() method mutates the original array - in other words, it modifies the order of the elements directly. This is generally considered bad practice, as it can result in unexpected side effects.

- Instead, you should use the .toSorted() method, which creates a new array. Change your .sort() call to .toSorted().

-  A Set is a data structure that only allows unique values. If you pass an array into the Set constructor, it will remove any duplicate values.

- Object.values(counts). This will ignore the keys and return an array of values only.

- Object.keys() will return an array of keys.

- Here is example to calculate square root:
```js
const base = 4;
const exponent = 0.5;
// returns 2
Math.pow(base, exponent);
```


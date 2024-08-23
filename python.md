# Python Programming

I'm gonna use this for solving leetcode problems, and take notes along when I learn something.

### Things I learned:

- You can take multiple inputs from the same line using `input().split()`. To make sure the input is in a specific data type, u can use map. 
```
valA, valB = map(int, input().split());
``` 
- Can't use && or || in if else, unlike other languages, use `and` or `or`. 
- If conditions end with a `:`
- Can cast a value to string as `str(x)`

### Mistakes I made: A list that makes me cry :-(
  - To accept a values in a range from 1 to 100, I used a condition that checks if the value is between 1 and 100 and then shows an error message. This was wrong and to fix it, I had to basically reverse the range so that the if condititon checks `1 > valA <100`

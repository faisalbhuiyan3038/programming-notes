# Recursion

- The call stack is a collection of function calls stored in a stack structure. When you call a function, it is added to the top of the stack, and when it returns, it is removed from the top / end of the stack.

- In computer science, a stack is a data structure where items are stored in a LIFO (last-in-first-out) manner. If you imagine a stack of books, the last book you add to the stack is the first book you can take off the stack. Or an array where you can only .push() and .pop() elements.

- A recursive function is a function that calls itself over and over. But you have to be careful because you can easily create an infinite loop. That's where the base case comes in.

- The base case is when the function stops calling itself, and it is a good idea to write it first.

- Since your countdown() function will count down from a given number to zero, the base case is when the number parameter is equal to 0. Then it should return to break out of its recursive loop.

- Recursive functions also have a recursive case, which is where the function calls itself.

- When writing the recursive case, you need to remember two things:

    - What is the base case?
    - What is the least amount of work you need to do to get closer to the base case?

- Since the base case is when number is equal to 0, you need to call countdown() again while also lowering the value of number by 1.

- As a reminder, it's often best to start with the base case when writing a recursive function so you know what you're working towards, and to prevent an infinite loop.

- For a reliable way to convert a value into a string, even falsy values like null and undefined, you can use the String() function.

- While asynchronous, or async, code can be difficult to understand at first, it has many advantages. One of the most important is that it allows you to write non-blocking code.

- For example, imagine you're baking a cake, and you put the cake in the oven and set a timer. You don't have to sit in front of the oven waiting the entire time – you can wash dishes, read a book, or do anything else while you wait for the timer to go off.

- Async code works in a similar way. You can start an async operation and other parts of your code will still work while that operation is running.
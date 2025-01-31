# API

- If you want data from an online source, you need use an API (Application Programming Interface). An API lets people from outside of an organization retrieve its internal data.

- There is a method called fetch that allows code to receive data from an API by sending a GET request.

```js
fetch("url-goes-here")
    .then((res) => res.json())
    .then((data) => console.log(data)).catch((err) => console.log(err))
```

- The fetch() method returns a Promise, which is a placeholder object that will either be fulfilled if your request is successful, or rejected if your request is unsuccessful.

- If the Promise is fulfilled, it resolves to a Response object, and you can use the .then() method to access the Response.

- The data you get from a GET request is not usable at first. To make the data usable, you can use the .json() method on the Response object to parse it into JSON.

- The .catch() method is another asynchronous JavaScript method you can use to handle errors. This is useful in case the Promise gets rejected.

- To populate the forum leaderboard with data, you will need to request the data from an API. This is known as an asynchronous operation, which means that tasks execute independently of the main program flow.

You can use the async keyword to create an asynchronous function, which returns a promise.

```js
const data = await fetch("https://example.com/api");
  console.log(data);
```
- The await keyword waits for a promise to resolve and returns the result.
# Pantry Tracker App

After you have installed nodeJS, create a new nextjs app with

```bash
npx create-next-app@latest
```

We will not be using typescript/tailwind for this project, everything else will remain default.

You can run this project locally with `npm run dev`

Then, we need to install material ui by copy-pasting the command from their website.

Next, install firebase with `npm install firebase`

After that, create a new Firebase project from Google firebase website and register a web app.

Then, initialize sdk with the code provied. Copy paste the code into a file `firebase.js` in the project's root folder.

We also need to create a firebase instance. To do this:

- Go to the firebase project you created earlier.
- In the project categories section, click on build, then Firestore Database.
- Click create database.
- Then, select start in Test mode.

To import Firestore in project, add an import in your firebase.js file.

```
import {getFirestore} from 'firebase/firestore'
const firestore = getFirestore(app);
export {firestore}
```

Next, we need to create a collection `inventory` in firebase db. You can think of a collection as each collection being a separate db.

Create a document `boxes` in it.

## Cleanup

Delete the page.module.css file because we will be using material ui for styling.

Additionally, delete everything that is not a \* component in globals.css

Also delete everything that's being returned from Home function.

## Defining the project structure

add `'use client'` at the top of page.js to indicate that it is a client side app.

Then, import `useState,useEffect`.
Then, import firestore.

I used some Box and typography components from material ui.

We need to use async when fetching or sending stuff. We need async because it won't block our code when it's fetching. Otherwise, it would block our code, which means the entire website would be frozen while it's fetching the data.

What useEffect does is, whenever something in dependency array changes, it runs and calles the function in it which is updateInventory(). If the array is empty, it runs when the page loads.

```js
useEffect(() => {
  updateInventory();
}, []);
```

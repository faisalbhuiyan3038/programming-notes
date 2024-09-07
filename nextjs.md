# Next JS Guide

Create a Next JS app with `npx create-next-app .`

Old way of routing is through the pages directory. New way is through the app directory. Next uses file system routing.

```
www.example.com/about
www.example.com/{slug} -slug can be an id or username or any wildcard value.
```

A cool thing about NextJS. Components are server components by default, meaning they get rendered on the server not the client so we can do data fetching directly inside of them with async await.

### Special FIles
- page.tsx - This file defines the unique UI of a route. This is needed for the path to be accessible.

- layout.tsx - This file defines the UI that is shared across multiple pages. It surrounds the entire application. It's child can be another layout or a page. You can create nested routes by nesting layouts.

- loading.tsx - This is an optional file used to create loading UI for a specific part of your app. Automatically wraps a page or child layout with React Suspense Boundary, showing your loading component immediately on first load and when navigating between sibling routes.

- error.tsx - Optional file that helps to isolate errors to specific parts of an app, show error info, and functionality to recover from error.

- template.tsx - Optional file, similar to layouts, except on navigation, a new instance of component is mounted and state is not shared. Template can be used in cases like Enter/Exit animations.

- head.tsx - Optional file, defines the contents of the `<head>` tag for a given route.

## page.tsx

This exports a default component that actually shows up in the UI.

```js
export default function HomePage(){
  return (
    <div>
    <h1>HomePage</h1>
    <p>Some Content</p>
    </div>
  )
}
```

## layout.tsx
If you run `npm run dev` now, it will automatically detect that a layout.tsx file is missing and autogenerate it. It will automatically add the page.tsx as children to show in the UI. Here is the typical code you will see:

```js
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html>
    <head></head>
    <body><main><nav>
    <Link href="/">Home</Link>
    <Link href="/notes">Notes</Link>
    </nav>{children}
    </main></body>
    </html>
  );
}
```

Any code you manually define here will be displayed on every single page. Good place to add a global navbar.

To nest layouts, put the layout.tsx in the directory where it should be used so that its used only for its route. For example, if you want a layout.tsx to be used only for the dashboard route and its pages, put it in the dashboard directory or folder.

## globals.css

As the name suggest, it includes styles used by the entire application.

## Creating Dynamic Routes
Suppose the route url is `www.example.com/{id}`. Then, create a directory with name `[id]`. Inside which you can create the page.tsx file that will be used to render dynamically.

## loading.tsx

Inside the id directory, we can place a loading.tsx file. This will show some kind of loading indicator that will be rendered in place of the page when the data is being fetched.

```js
export default function Loading(){
  return <p>Loading...</p>
}
```

## error.tsx
Similarly, you can write a component that will be shown in place of the error whenever an error occurs in the page.tsx.

```js
export default function Error(){
  return <p>error...</p>
}
```

## Useful server response parameters
```js
{
  next: { revalidate: 10 },
}
```
This tells Next to regenerate the page on the server if its older than a certain number of seconds.

```js
{cache: 'no-store'}
```
This will refetch the items from the server on every request, otherwise the request response is cached.

## Code to write something to db
Let's say we want to create a note using a file CreateNote.tsx, which will be on the same level as the first page.tsx.

This will have `'use-client'` at the top to indicate that this page will be rendered on the browser, not on the server.

Code to create new note:
```js
'use-client'
import {useState} from 'react';

export default function CreateNote(){
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');

  const create = async() => {
    await fetch('https:/asdasnsd/notes/records/', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        title,
        content,
      }
      ),
    });

    setContent('');
    setTitle('');
  }

  return (
    <form onSubmit={create}>
    <h3>Create a new Note</h3>
    <input
      type="text"
      placeholder="Title"
      value={title}
      onChange={(e) => setTitle(e.target.value)}
    />
    <textarea
      placeholder="Content"
      value={content}
      onChange={(e) => setContent(e.target.value)}
    />
    <button type="submit">
    Create note
    </button>
    </form>
  )
}

// in page.tsx
<CreateNote />
```

Leaving it like this, we would need to refresh the page each time to see the changes after creating note. But we can use nextRouter to fix this.

```js
//in CreateNote.tsx
import {useRouter} from 'next/navigation';

//inside CreateNote func
const router = useRouter();

//for whenever you want to call the refresh
router.refresh();
```

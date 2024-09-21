# Next JS Guide

-> Primary goal of NextJS is to expand the use of React to static sites.

Create a Next JS app with `npx create-next-app .`

Old way of routing is through the pages directory. New way is through the app directory. Next uses file system routing.

```
www.example.com/about
www.example.com/{slug} -slug can be an id or username or any wildcard value.
```

A cool thing about NextJS. Components are server components by default, meaning they get rendered on the server not the client so we can do data fetching directly inside of them with async await.



## Problem / Solution
Problem: Need to show different content on the screen based on the path of the URL.

Solution: Use Next's file based routing system.

===========

- The `src/app` directory is a special directory because it determines the routes of your application based on the files that exist there.
- The page.tsx file specifically identifies the route a user can visit. This has to be in nested folders. To be a valid route, there needs to be a default export with a React component.
```js
export default function HomePage(){
  return <h1>HomePage<h1>;
}
```
- The name of the function is irrelevant as it's used only for debugging purposes.
- The name of the folder inside which the page.tsx file exists controls the route name.
```js
//this is the default localhost:3000 route
src\app\page.tsx
//this is the \performance route, localhost:3000/performance
src\app\performance\page.tsx
// this is \reliability\details route, localhost:3000/reliability/details
src\app\reliability\details\page.tsx
The reliability directory must also have a page.tsx file.
```

Problem: Need to link between different pages.

Solution: Use Next's inbuilt Link component to show a clickable link to navigate between different routes.

==================

- Add an import for Link Component.
```js
import Link from 'next/link'
export default function HomePage(){
  return <div>
  <div>
  <Link href="/performance">Performance</Link>
  </div>
  HomePage<div>
}
```
- /performance must be a directory on the same level as the page.tsx where this function exists.

## Common UI With Layouts
To control or change styling across the entire application, modify the globals.css file.

- If you want to keep certain UI elements or links the same across all or multiple pages, then you can use the layout.tsx file.
- The layout.tsx is like a global parent component, and the page.tsx files that are rendered upon clicks when navigating between routes are like a child component.
```js
//Visualized example
<Layout>
    <PerformancePage />
</Layout>
```
- In `layout.tsx` file, go to RootLayout function and modify as needed.
```js
export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="en">
      <body
        className={`${geistSans.variable} ${geistMono.variable} antialiased`}
      >
      // Added three links above every page.
        <div>
        <Link href="/"> Home</Link>
          <Link href="/performance">Performance</Link>
          <Link href="/reliability">Reliability</Link>
          <Link href="/scale">Scale</Link>
        </div>
        {children}
      </body>
    </html>
  );
}
```

### Project Structure
- Keep only routing directories with `page.tsx` file in the `src/app` directory.
- Keep all the other components or reusable data directories in the `src/` directory for better readability and usage.
- It's also preferable to not hardcode any content in the RootLayout function of the `layout.tsx` file. Instead, create a separate component and just display the component there.
```js
//Header.tsx
export default function Header(){
  //return the three links
}

//layout.tsx
import Header from '../components/header';

//inside RootLayout above children
<Header />
```
- You may notice we are using `../` to indicate a relative path to get the item from. This can become problematic for deeply nested folders where you have to use `../../../../something`.
- There is a shortcut `@` that indicates the starting point as the `src` directory. So, `@components/header` means `src/components/header`.

================
- The `public` directory is the place where all the static files are kept, like images, logos or anything we want to make available for download.

### Images in NextJS
- Use `Image` component to render images as it can render in different sizes for mobile/web and is performance optimized.
```js
import Image from 'next/image';
import homeImg from '../../public/home.jpg';

export default function Home() {
  return (
    <div>
      HomePage
      <div className='absolute -z-10 inset-0'>
        <Image
          src={homeImg}
          alt='car factory'
          fill
          style={{ objectFit: 'cover' }}
        />
      </div>
    </div>
  );
}
```
- According to Copilot, In Next.js, you should reference images in the public folder using a root-relative path rather than importing them directly. This approach is more efficient and aligns with how Next.js handles static assets.
```js
import Image from 'next/image';

export default function Home() {
  return (
    <div>
      HomePage
      <Image
        src="/home.jpg"
        alt="car factory"
        width={500} // specify width
        height={300} // specify height
      />
    </div>
  );
}

```
- We use Image component to avoid layout shifting, which can be annoying for users. Basically, layout shifting is when an image takes longer to load so a text content loads up, but when the image finishes loading, the text shifts somewhere else suddenly.
- To let the app know what the size of the image must be, we can use three options for sizing the image:

  - If using local image, dimensions are taken from imported image.
  - Assign a height and width to the Image component
  - Assign a 'fill' prop, the image will expand to fill up the parent element.

### Building a resuable component with props
- Put the component.tsx inside components directory.
- If using typescript, you need to describe all the different props the function expects to recieve.
```js
import type { StaticImageData } from "next/image";
import Image from "next/image";

interface HeroProps {
  imgData: StaticImageData;
  imgAlt: string;
  title: string;
}

export default function Hero(props: HeroProps) {
  return (
    <div className="relative h-screen">
      <div className='absolute -z-10 inset-0'>
        <Image
          src={props.imgData}
          alt={props.imgAlt}
          fill
          style={{ objectFit: 'cover' }}
        />
        <div className="absolute inset-0 bg-gradient-to-r from-slate-900"></div>
      </div>
      <div className="pt-48 flex justify-center items-center">
        <h1 className="text-white text-6xl">
          {props.title}
        </h1>

      </div>
    </div>
  )
}

```
```js
import Hero from "@/components/hero";
import relImg from '../../../public/reliability.jpg';

export default function ReliabilityPage() {
  return (
    <Hero imgData={relImg} imgAlt='welding' title='Super High Reliability Hosting' />
  );
}

```


### Special FIles
- page.tsx - This file defines the unique UI of a route. This is needed for the path to be accessible.

- layout.tsx - This file defines the UI that is shared across multiple pages. It surrounds the entire application. It's child can be another layout or a page. You can create nested routes by nesting layouts.

- loading.tsx - This is an optional file used to create loading UI for a specific part of your app. Automatically wraps a page or child layout with React Suspense Boundary, showing your loading component immediately on first load and when navigating between sibling routes.

- not-found.tsx - Displayed when we call the 'notFound' function

-loading.tsx - Displayed when a server component is fetching some data

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

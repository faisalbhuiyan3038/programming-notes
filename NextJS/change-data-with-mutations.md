# Create, Edit, Delete Data 
- When we are working with small data that needs to be stored and accessed by an app, we can use SQLite DB.
- To access SQLite, we can use a library like `prisma`.

### Setup Prisma and SQLite
```bash
npm install prisma

npx prisma init --datasource-provider sqlite
```

- Once these commands are run, we need to tell prisma what kinds of data will be stored in the app. To do that, define a model in the `schema.prisma` file.
```
model Snippet{
  id Int @id @default(autoincrement())
  title String
  code String
}
```
- To save this model, you will need to migrate these changes with the command `npx prisma migrate dev`

### Steps to create DB records
- Create a prisma client to access the db.
    - Create a db/index.ts file in src/app directory.
    ```ts
    import {PrismaClient} from '@prisma/client';
    export const db = new PrismaClient();
    // we will use this db to perform various action on db, like create, update, delete.
    //for create
    db.snippet.create({
      data: {
        title: 'Title!',
        code: 'const abc => {}'
      }
    })
    ```
- Create a form in SnippetCreatePage.
- Define a server action. This is a function that will be called when the form is submitted.
- In the server action, validate the users input then create a new snippet.
- Redirect the user to the HomePage, which lists all the snippets.

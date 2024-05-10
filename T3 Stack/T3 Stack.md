
Create the project by 

`npx create-t3-app`

add all the neccessary according to project

`What will your project be called?`
`│  shoppinglist`
`│`
`◇  Will you be using TypeScript or JavaScript?`
`│  TypeScript`
`│`
`◇  Will you be using Tailwind CSS for styling?`
`│  Yes`
`│`
`◇  Would you like to use tRPC?`
`│  Yes`
`│`
`◇  What authentication provider would you like to use?`
`│  None`
`│`
`◇  What database ORM would you like to use?`
`│  Prisma`
`│`
`◇   EXPERIMENTAL  Would you like to use Next.js App Router?`
`│  Yes`
`│`
`◇  What database provider would you like to use?`
`│  MySQL`
`│`
`◇  Should we initialize a Git repository and stage the changes?`
`│  No`
`│`
`◇  Should we run 'npm install' for you?`
`│  Yes`
`│`
`◇  What import alias would you like to use?`
`│  ~/`

==Step - 2==

create and connect your database in this case I'm using **MYSQL**

on **.env**
`DATABASE_URL="mysql://root:password@localhost:3306/shoppinglist"`
              provider  username           connection port  Database name;
                       and
                       password   
on ==schema.prisma==        
`model Example {`
`id String @id @default(cuid())`
`name String`
`checked Boolean`
`}`

basic table format 
To Push the model to db use 
`npx prisma db push`

Now on sql the Table format will be pushed

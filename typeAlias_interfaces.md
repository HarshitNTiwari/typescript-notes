So far we've been assigning types to variables and objects directly:

```ts
let scientist1 : {
    name: string
    born: number
    dept: string
}
```

However, this process has two downsides: writing larger types (with a lot of properties) like this again and again can become very messy and cumbersome. Moreover, if multiple objects are meant to have the same type and we need to change something in the type, we'll need to update it everywhere. A very efficient way to do so is by defining _Type Aliases_.

A type alias is used to provide name to a type literal. Here's the syntax to define a type:

```ts
type Scientist = {
    name: string
    born: number
    dept: string
}
```

And now we can annotate our variable using this type alias `Scientist`:

```ts
let scientist1: Scientist = {
    name: "Raman",
    born: 1888,
    dept: "Physics"
}
```
A few things to note:
- Type alias is a useful way to centrally define the structure of objects. We can easily change the type of all the objects with this type by changing it at only one place.
- Type Alias also gives us the ability to export and import these types elsewhere.
- Types can be thought of as variables - types with same name cannot be declared within the same scope.
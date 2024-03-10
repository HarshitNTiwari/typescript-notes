## Type Alias

So far we've been assigning types to variables and objects directly:

```ts
let scientist1: {
  name: string;
  born: number;
  dept: string;
};
```

However, this process has two downsides: writing larger types (with a lot of properties) like this again and again can become very messy and cumbersome. Moreover, if multiple objects are meant to have the same type and we need to change something in the type, we'll need to update it everywhere. A very efficient way to do so is by defining _Type Aliases_.

A type alias is used to provide name to a type literal. Here's the syntax to define a type:

```ts
type Scientist = {
  name: string;
  born: number;
  dept: string;
};
```

And now we can annotate our variable using this type alias `Scientist`:

```ts
let scientist1: Scientist = {
  name: "Raman",
  born: 1888,
  dept: "Physics",
};
```

#### Extending Type Aliases

How can we extend one type alias to create another type alias? We do it using intersection:

```ts
type Scientist = {
  name: string;
  born: number;
  dept: string;
};

// using intersection
type Physicst = Scientist & {
  no_of_awards: number;
};
```

Here, the type `Physicist` will have all the properties of type `Scientist` as well as the new properties defined in the intersection type above.

---

A few things to note:

- Type alias is a useful way to centrally define the structure of objects. We can easily change the type of all the objects with this type by changing it at only one place.
- Type Alias also gives us the ability to export and import these types elsewhere.
- We can use type alias to define types for variables, objects (like we did above) or functions. We can also use them to define union and intersection types - a key difference from interfaces as we'll see.
- Types can be thought of as variables - types with same name cannot be declared within the same scope. We'll see how this makes type aliases different from interfaces.

## Interface

Just like type aliases, an interface is just another way of naming types - with of course a few differences.

```ts
interface Scientist {
  name: string;
  born: number;
  dept: string;
}

let scientist1: Scientist = {
  name: "Raman",
  born: 1888,
  dept: "Physics",
};
```

Note that the declaration above is pretty much similar to how we define type alias (expect for the fact that there's no `=` symbol); they infact do the same thing - give a name to an object type.

---

It is, however, important to understand the design philosophy here: although interfaces and type aliases seem to do similar things at a high level, an interface is not meant to represent just any type. It is meant to define a particular structure - object types essentially. And therefore not only we cannot use interfaces for declaring pre-defined types, it also does not make sense for interfaces to support union or intersection types for they do not neccessarily resolve to a particular data type.

For example the following interface declarations does not make sense and therefore is illegal in TS:

```ts
interface MyNumber number // ! error

interface Scientist {
  name: string;
  born: number;
  dept: string;
} | null // ! error
```

---

We can add properties to interfaces even after they have been declared. We do this by re-declaring them - something we cannot do with type aliases as already mentioned.

```ts
interface Scientist {
  name: string;
  born: number;
  dept: string;
}

interface Scientist {
  no_of_awards: number;
}
```

All the declarations of the interface `Scientist` will be combined together by TS and for any object declared with type `Scientist` will have all these properties accessible in it.

#### Extending interfaces

We use the `extends` keyword in order to extend one interface from another:

```ts
interface Scientist {
  name: string;
  born: number;
  dept: string;
}

// using 'extends' keyword
interface Physicst extends Scientist {
  no_of_awards: number;
}
```

## Differences

| Type Alias                                                        | Interface                                                              |
| ----------------------------------------------------------------- | ---------------------------------------------------------------------- |
| We can represent union and intersection types using type alias    | We cannot represent union and intersection types using interface       |
| We can extend types defined using type aliases using intersection | We can extend types defined using interfaces using the extends keyword |
| We cannot redeclare a type in order to add properties to it       | We can redeclare an interface to add add properties to it              |

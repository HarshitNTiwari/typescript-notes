Let's start with a simple variable declaration in JS:

```ts
let number1 = 69
```

From the look of it, we get no direct type information from the above statement. But when you write this statement in a TS environment, TS _infers_ the variable `number1`'s type as a `number`. In TS, when we declare a variable, these variables are sort of born with some type, which then we cannot change, i.e., once they are declared, there's nothing we can do to make them accept a value of a different type.

For e.g. the following will raise a compile time error, since we're trying to assign a `string` value to a `number` type variable:

```ts
number1 = "sixty_nine" // error
```

### Literal Types
Look at the following declaration:
```ts
const number2 = 79 
```
What do you think is the type of the variable `number2`? If you think it is `number` then here's a surprise: The type is `79`. We call this a _literal type_. But how can `79` be a type? Isn't it a value?
Well, in this case we're doing a `const` variable declaration and assiging it to a number. This not only makes `number2` reassignable but also makes its value unchangeable since the value that we're assiging to it is an immutable value in JS. This means that there's nothing else that can ever be stored in the variable `number2` except `79` and hence that is it's type. Therefore the following will raise an error:

```ts
number2 = 69 // this is an error not just because number2 is const but also because it's original value is immutable
```

### Type Annotation
Up until now, we've never explicitly defined type for any variable; it was infered implicitly by TS. But we can very well _annotate_ a variable using the notation `variable_name: type`

```ts
let number3: number = 69
```
This annotation is more important in the context of objects and functions as we'll see further. 
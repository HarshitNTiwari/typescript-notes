Let's start with a simple variable declaration in JS:

```ts
let number1 = 69
```

From the look of it, we get no direct type information from the above statement. But when you write this statement in a TS environment, TS 'infers' the variable `number1`'s type as a `number`. In TS, when we declare a variable, these variables are sort of born with some type, which then we cannot change, i.e., once they are declared, there's nothing we can do to make them accept a value of a different type.

For e.g. the following will raise a compile time error, since we're trying to assign a `string` value to a `number` type variable:

```ts
number1 = "sixty_nine" // error
```

### Literal Types

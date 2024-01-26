# Variables and Types
Let's start with a simple variable declaration in JS:

```ts
let number1 = 69
```

From the look of it, we get no direct type information from the above statement. But when you write this statement in a TS environment, TS _infers_ the variable `number1`'s type as a `number`. In TS, when we declare a variable, these variables are sort of born with some type, which then we cannot change, i.e., once they are declared, there's nothing we can do to make them accept a value of a different type.

For e.g. the following will raise a compile time error, since we're trying to assign a `string` value to a `number` type variable:

```ts
number1 = "sixty_nine" // error
```

`number1`'s type `number` indicates it can accept all the numbers and therefore a reassignment like the following is valid:

```ts
number1 = 79
```

## Literal Types
Look at the following declaration:
```ts
const number2 = 79 
```
What do you think is the type of the variable `number2`? If you think it is `number` then here's a surprise: the type is `79`. We call this a _literal type_. But how can `79` be a type? Isn't it a value as it was in the case of `let` declaration above?
Well, in this case we're doing a `const` variable declaration and assiging it to a number. This not only makes `number2` non-reassignable but also makes its value unchangeable since the value that we're assiging to it is immutable in JS. This means that there's nothing else that can ever be stored in the variable `number2` except `79` and hence that is it's type. Therefore the following will raise an error:

```ts
number2 = 69 // this is an error not just because number2 is const but also because it's original value is immutable. In other words 69 is not of type 79.
```

Now consider this:

```ts
const array1 = [69]
```

Here, the type of `array1` is `number[]` and not `[69]`. because, although `array1` is still non-reassignable the value that it has been assigned (i.e. the array [69]) is mutable (arrays in JS are mutable). Therefore the value can change (we can push elements in the array) and the type of `array1` is not a literal type.

## Type casting

We can also make a `let` variable have a literal type (and consequently make it behave like a `const` variable) by writing as follows:

```ts
let number3 = 79 as 79 // This is just to show that this is possible and might not be of any consequence
```

Here although `number3` in itself is reasssignable, we have _casted_ it to be of a literal type, so now it has become non-reassignable to anything else except 79.

But what if we turn the tables and do something like this:

```ts
const number4 = 79 as number // accepted since 79 and number are similar types
```

Here we're explicitly casting `number4` as a `number` even though we know that it's type is `79`. Will this work? 
As long as the types (79 and number) are reasonably compatible, TS will let you do that cast. 

For instance something like this will surely raise an error, since `string` and `number` are very different types:

```ts
let string1 = "hello" as number // error
```


## Type Annotation
Up until now, we've never explicitly defined type for any variable; it was infered implicitly by TS. But we can very well _annotate_ a variable using the notation `variable_name: type`

```ts
let number5: number = 69
```
This annotation is more important in the context of objects and functions as we'll see further. 
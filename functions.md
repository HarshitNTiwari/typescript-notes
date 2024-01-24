When it comes to functions, two of the most important aspects are: what a function accepts and what a function returns. It is exactly these two things whose type we need to care about - the functions parameters and the function's return type. 

Consider the following JS function:

```ts
function add(a, b) {
    return a + b
}
```
The lack of type information in the above function, leads to the ambiguity as to what this funnction is indending to do. Is it adding two numbers? Or is it concatenating two strings? Or something entirely differernt? As it might be clear that what this function returns is really dependent on what is passed to it, i.e. what is the type of the paramters of this function. So, we can annotate the parameters and the return type of the function `add()` with their types as follows:

```ts
function add(a: number, b: number): number {
    return a + b
}
```
This makes things a lot clearer. Obviously, the parameters and the return type can be of any type. 

An important thing to note is that, even if we would've not specified the return type, TS would've infered it from the types of the parameters and the operation that the function is performing. So why is adding return type important? To say the least, it is a good practice to add return types. Consider the following example:

```ts
function add(a: number, b: number) {
    if(b > 69)
        return a + b
}
sum = add(44, 22)
sum.toExponential() // error if sum's type is `undefined`
```

TS will infer the return type to be `number | undefined` (this simply means that the return value can either be a number or an undefined value). If the type of `sum` is `undefined` then the subsequent method call on `sum` will raise an error. This is not what was expected. In other words we didn't except an undefined return value from `add` function.
The error is popping right at the point when we're calling a method on the result of the `add` function. We could've avoided this mistake, if we would've specified the expected return type:

```ts
function add(a: number, b: number): number { // it will show error on the return type telling that you're not returing number from all paths inside the code
    if(b > 69)
        return a + b
}
```
In a nutshell, it's all about bringing errors as close to their origin as possible.

Another aspect of functions in JS is that they are first class functions, i.e they can be assigned to variables and passed around as variables. Therefore, if we store a function in a variable, we should be able to assign type to that variable. Consider the following:

```ts
let Add = function add(a: number, b: number): number {
    return a + b
}
```
What is the type of the variable `Add`? It is written as: `(a: number, b: number)=> number` which represents the type of the parameters and the return type. This will be infered by TS, but we can also annotate it like following:

```ts
let Add: (a: number, b: number)=> number = function add(a: number, b: number): number {
    return a + b
}
```
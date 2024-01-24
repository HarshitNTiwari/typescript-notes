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
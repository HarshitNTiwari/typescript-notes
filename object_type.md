# Objects
If you've worked in JS even a little, you're well aware what role objects play in almost everything we do in JS. It is the most basic form of passing data around in JS code. Well how do you assign types to objects in TS?

Consider the following object:
```ts
let scientist1 = {
    name: "Raman",
    born: 1888,
    dept: "Physics"
}
```
In simple terms an object type's aim is to define the structure for that object.
We can annotate this object `scientist1` like following:

```ts
let scientist1 : {
    name: string
    born: number
    dept: string
}
```

We can pass around this object as a parameter to functions, like the following:

```ts 
function printScientist(scientist: {
    name: string
    born: number
    dept: string
}): void {
    console.log(`${scientist.name} ${scientist.born} ${scientist.dept}`)
}

printScientist(scientist1) // passing object to the function
```

## Optional Properties

Consider the same function as above, but with an additional property `nobel` in the type annotation of the parameter:

```ts 
function printScientist(scientist: {
    name: string
    born: number
    dept: string
    nobel?: boolean
}): void {
    let str = `${scientist.name} ${scientist.born} ${scientist.dept}`
    if(typeof scientist.nobel !== "undefined")
        str += `${scientist.nobel}`
    console.log(str)
}
```
We note that the property `nobel` is suffixed with a `?` symbol which simply signifies that this is an _optional property_.

So, now we can pass an object that has this property and also the one which doesn't:

```ts
printScientist({
    name: "Raman"
    born: 1888
    dept: "Physics"
    nobel: true
})

printScientist({
    name: "Hawking"
    born: 1942
    dept: "Physics"
})
```

Both of the above are valid. 

What if we try to pass a property which is not a part of the type of the function parameter, like the following:

```ts
printScientist({
    name: "Hawking"
    born: 1942
    dept: "Physics"
    specialization: "astrophysics"
})
```
This will raise an error, since the property `specialization` cannot be accessed inside the `printScientist` function and therefore it does not makes sense to pass this property. 

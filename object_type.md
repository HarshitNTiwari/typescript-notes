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

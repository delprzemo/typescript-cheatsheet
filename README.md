# TypeScript Cheatsheet
Set of basic functionalities from TypeScript in one place. Cheatsheet was created by https://foreach.pl trainers for their students.
Please note that some functionalities are part of ES201x but they are frequently used in TypeScript as well.

Types, variables and functions
=================

Command line inferface for Angular - set of commands that will help us during development.

## Basic variable types

| Type  | Example | Notes |
| ------------- | ------------- | ------------- |
| number | let myNumber: number = 6 | Represent all numbers : integer, float, hex etc.
| string | let fullName: string = `Bob Bobbington`| Text with all text functions (indexOf, replace etc.)
| boolean | let isTrue: boolean = true| true/false value
| Array | let list: Array<number> = [1, 2, 3] | Shorter version: let list: number[] = [1, 2, 3];
| Tuple | let x: [string, number] = ['test', 2]; | Array contains  ains items with various types
| any | let x: any = 2; | Everything can be assigned to value with any type
| Enum | enum Color {Red, Blue } | Usage: let c: Color = Color.Blue; 
| Never | function fail(): never {while(true) {}} | Indicating that something never should happen
| Null or undefined | let u: undefined = undefined; | In TS there is dedicated type for null and undefined
| Object | let x:Object = {id: 2}; | Represents any object
| Function | let myFn:Function = function() {...} | Represents any function

## Destructing and spread
This is ES functionality 

**Spread**

Spread can be used to merge two object or arrays:

```ts
let first = [1, 2];
let second = [3, 4];
let both = [0, ...first, ...second, 5];
}
```

both variable is equal to [1, 2, 3, 4].

Same for objects:
```ts
let first = { id: 2 };
let second = { name: "test", ...first };
}
```
Second is equal to {name: "test", id: 2 }

**Destructuring**
Reversed spread - we can split one object into multiple
```ts
let input = [1, 2];
let [first, second] = input;
}
```
first is equal to 1 and second is equal to 2

We can also use "..." operator
```ts
let input = [1, 2, 3];
let [first, ...rest] = input;
}
```
first is equal to 1

rest is equal to [2, 3]
 
## Array functions
This is ES functionality 

```ts
var numArray: Array<number> = [1, 2, 3];
var numArray2: Array<number> = [4,5];
var stringArray: Array<number> = ["a", "b", "c"];

var objectArray: Array<User> = [
  {name: "Iva", age: 31},
  {name: "John", age: 39},
  {name: "Monica", age: 22}
]; 
```

| Function  | Result | Notes | 
| ------------- | ------------- | ------------- | 
| concat | numArray.concat(numArray2) -> [1,2,3,4,5] | Push values from one array to another |
| every | objectArray.every(x=> x.age > 20) -> true | Check if all items are passing condition |
| some | objectArray.some(x=> x.age > 30) -> true | Check if any item is passing condition |
| filter | objectArray.filter(x=> x.age >= 35)) -> [{name: "Iva", age: 39}] | Get only items which are passing condition |
| foEach | numArray.forEach(x=> console.log(x)) | Perform some logic for each array item |
| join | stringArray.join(",") -> "a,b,c" | Merge text items into one value (add ',' between) |
| indexOf | stringArray.indexOf("b") -> 1 | Return index(position) array item |
| map | stringArray.map(x => x + "1") -> ["a1", "b1", "c1"] | Do something with each array item |
| push | stringArray.push("d") -> ["a", "b", "c", "d"] | Add element to the end of the array  |
| unshift | stringArray.unshift("d") -> ["d", "a", "b", "c"] | Add element to the begin of the array  |
| reduce | numArray.reduce((x, y) => x + y) -> 16 | Merge array into one value performing some logic on a way |
| shift | numArray.shift() -> [2, 3] | Removes the first element from an array and returns it.|
| sort | ["b", "c", "a"].sort((x,y) => x > y) -> ["a", "b", "c"] | Sort array by some logic |


## Functions
This is ES functionality 

| Type  | Example |
| ------------- | ------------- |
| Named function | function add(x: number, y:number): number {} | 
| Anonymous function | let myAdd = function(x: number, y: number = 1): number | 
| Arrow function | myArrowAdd = (x: number, y:number): number | 


Classes
=================

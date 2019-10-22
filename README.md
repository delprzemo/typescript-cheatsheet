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

Sample class:
```ts
class NewGreeter {
   private greeting: string; 
   constructor(message: string) { 
    this.greeting = message;
   }

   greet() {
    return "Hello, " + this.greeting;
   }
}

var greeter = new Greeter('friend');

```
Notes:
1. Only one constructor inside class
2. constructor(**this** message: string) will automatically create message property and assign to it value from message property
3. Instead of private - public or protected can be used

## Inheritance
```ts
class MyObject {
   protected value = 0;
   static staticValue = 0;

   getValue() {
    return this.value;
   }
}
class ChildObject extends MyObject {
   getParentValue() {
    return this.value;
   }
 }

```

## Accessors

TypeScript supports getters/setters as a way of intercepting accesses to a member of an object. You can add logic while the property is changing value or it is read by something


```ts
private _value = 0;
get value(): number {
	return this.value;
}
set value(newValue: number): void {
	this.value = newValue;
}
```

## Abstract class
Abstract classes are base classes from which other classes may be derived. They may not be instantiated directly. Unlike an interface, an abstract class may contain implementation details for its members. 

```ts
abstract class MyAbstractObject {
    constructor(public value: string) { }
    abstract getValue(): string; 
}
```

getValue function must be implemented in derived classes. Derived class must also call super() in constructor, example:

```ts
abstract class MyAbstractObject extends Department {
    constructor() {
       super("test value");
    }
    getValue(): string {
       // some logic here
    }
}
```

Interfaces
=================

A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition. The interface is the only skeleton for our classes implementing them

**Interface for object**
```ts
interface IObject {
     label: string 
}

function MyFunction(obj: IObject) 
```

obj parameter has to contain label property

**Interface for class**
```ts
interface ComesFromString {
    name: string;
}

class MadeFromString implements ComesFromString {
    constructor (public name: string) {

    }
}
```

class MadeFromString has to contain 'name' property

obj parameter has to contain label property

## Index signature
Index signature can be used to allow object/class contain multiple different properties with same type, for example wew have such a interface:

```ts
interface IMyObject {
	[propName: string]: string
}
```
and MyObject that is implementing it. 

Sample correct implementation of IMyObject:
```ts
let MyObject: IMyObject  = {
	fistName: 'test',
	lastName: 'test'
}
```
Sample incorrect implementation of IMyObject:

```ts
let MyObject: IMyObject  = {
	fistName: 'test',
	age: 2
}
```
Because age is number and our index signature indicate that our properties should have string type


Generics
=================
Sometimes same function/class/object can be used with different types and we don't want to declare it to one specific type. We can use generic type then

Example:
```ts
function changeUndefinedToNull<T>(value: T): T {
	return (typeof value !== "undefined") ? value : null;
}
```

and now it can be used with diffrent types used for value parameter:

```ts
const result = changeUndefinedToNull<string>("Test");
```
```ts
const result = changeUndefinedToNull<number>(21);
```
```ts
const result = changeUndefinedToNull<Object>({name: "Test"});
```

More than just one generic type can be used:
```ts
function doSth<T,Y> (value: T, category: Y) {}
```

## Extending generics
Generic classes can be extended - it can be implemention of some inferface/object
Example:

```ts
function mySubStr<T extends string>(arg: T): string {
	return arg.substr(1, 10);
}
```

arg has to object that is equal or extending string, for example string or:

```ts
interface IExtendedString extends String{
	newStringFunction(): number
}

mySubStr(arg: IExtendedString);
```




# TypeScript Cheatsheet
Set of basic functionalities from TypeScript in one place. 

Cheatsheet was created by https://foreach.pl trainers for their students.

Please note that some functionalities are part of ES201x but they are frequently used in TypeScript as well.

# Table of Contents

<!--ts-->
   * [Types, variables and functions](#Types,-variables-and-functions)
      * [Basic variable types](#Basic-variable-types)
      * [Destructing and spread](#Destructing-and-spread)
      * [Array functions](#Array-functions)
      * [Functions](#Functions)
   * [Classes](#Classes)
      * [Inheritance](#Inheritance)
      * [Accessors](#Accessors)
      * [Abstract class](#Abstract-class)
   * [Interfaces](#Interfaces)
      * [Index signature](#Index-signature)
   * [Generics](#Generics)
      * [Extending generics](#Extending-generics)
   * [Enums](#Enums)
      * [Constant and computed enum members](#Constant-and-computed-enum-members)
      * [Reverse enum member](#Reverse-enum-member)
   * [Advanced types](#Advanced-types)
      * [Types intersection and union](#Types-intersection-and-union)
      * [Type guards](#Type-guards)
      * [Type aliases](#Type-aliases)
      * [Conditional types](#Conditional-types)
      * [Index types](#Index-types)
      * [Infer](#Infer)
   * [Symbols](#Symbols)
   * [Modules](#Modules)
      * [Namespaces](#Namespaces)
      * [Ambient modules](#Ambient-modules)
   * [Decorators](#Decorators)
   * [Generators](#Generators)
<!--te-->

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

Enums
=================
Enums allow us to define a set of named constants and then used them like a dictionary.

Sample enum:
```ts
enum Direction {
	Up ,
	Down = 1,  // custom values can be assigned to enums
	Left,
	Right,
}
```

usage:

```ts
function move(direction: Direction): void {
	if(direction == Direction.Up) {
		// some code here
	}
}
```

## Constant and computed enum members
Some enum members have pre-set value and some members are computed during complation

```ts
enum FileAccess {
    // constant members
    None,
    Read    = 1 << 1,
    Write   = 1 << 2,
    ReadWrite  = Read | Write,
    // computed member
    G = "123".length,
    F = Read + Write
}
```

## Reverse enum member

```ts
enum MyEnum {
	A, 
	B
}
const member = MyEnum[0];
```
member variable is equal to "A"


Advanced types
=================

## Types intersection and union

**Intersection**
```ts
interface Type1 {name: string;}
interface Type2 {age: number}

let myObject: Type1 & Type2
```
Type1 & Type2 means that there will be object containing properties both from  Type1 & Type2
 
Sample correct myObject value:
```ts
myObject = {name: "test", age: 33}
```

Sample incorrect myObject values:
```ts
myObject = {name: "test"}
```
```ts
myObject = {name: "test", age: "test"}
```

**Union**
```ts
const value: string | boolean 
```
Value can be string OR boolean.

It is correct:
```ts
value = "Test";
```
```ts
value = true
```

and that is incorrect:
```ts
value = 2
```

## Type guards
Type guard can be used to tell TypeScript what type is any value in specific block of code.

Sample Type Guard implementation:

```ts
function isNumber(x: any): x is number {
    return (<number>x).toPrecision !== undefined;
}
```

Sample Type Guard usage

```ts
function doSth<T>(value: T) {
    if (isNumber(value)) {
	return value.toPrecision; // it's ok as TypeScript know that here value is number
    } else {
	return value.toPrecision; // Error - we don't have access to toPrecision here
    } 
}
```
thanks to 'x is number' typescript know in which scope we have access to toPrecision 

## Type aliases
Own custom types can be declared, for example

```ts
type MyType<T> = { parameter: T};
```

Usage:

```ts
let myVariable: MyType<string> = {parameter: "Test"}
let myVariable: MyType<string> = {parameter: 2}
```

## Difference between Types na Interfaces

**Types**

Create a tree structure for an object. You can't do the same with interface because of lack of intersection (&)

```ts
type Tree<T> = T & { parent: Tree<T> };
```

type to restrict a variable to assign only a few values. Interfaces don't have union (|)

```ts
type Choise = "A" | "B" | "C"
```

thanks to types, you can declare NonNullable type thanks to a conditional mechanism.

```ts
type NonNullable<T> = T extends null | undefined ? never : T;
```

**Interfaces**
You can use interface for OOP and use 'implements' to define object/class skeleton
```ts
interface IUser {
    user: string;
    password: string;
    login: (user: string, password: string) => boolean;
}

class User implements IUser {
    user = "user1"
    password = "password1"

    login(user: string, password: string) {
        return (user == user && password == password)
    }
}
```
You can extend interfaces with other interfaces

```ts
interface IMyObject {
	label: string,
}

interface IMyObjectWithSize extends IMyObject{
	size?: number
}
```

## Conditional types
Generic types can be different depending on some condition
```ts
type MyStringType<T> = T extends string ? string : Text;
```
if T extends string (contains all string properties and functions) then it will be string type. Otherwise it will be our custom Text type. 

other example:

```ts
type NonNullable<T> = T extends null | undefined ? never : T;
```
NonNullable type will check if value isn't equal to null or undefined (it should never been equal to null or undefined)

## Index types
***keyof*** keyword is indicating all keys for specifed object, for example:
```ts
type testType = keyof {id: "test", age: 2} ;
```
only "id" or "age" values can be assigned to variable with 'testType' type

Example 2:
```ts
interface IMyInterface {
    id: number;
    name: string;
}

type Keys = {id: 1, name: "T" }[keyof IMyInterface];
```

using [keyof ...] instead of "keyof" before object means that we are revesing keyof behavior and now only 1 and "T" can be assigned to value with Keys type (values, not property keys)

Example 3:
```ts
type Key<T> = { [K in keyof T]: K }[keyof T];
```
This will point to all keys in the T object (just like keyof T).
But this construction can be used to for example check type of keys:

```ts
type FunctionPropertyNames<T> = { [K in keyof T]: T[K] extends Function ? K : never }[keyof T];
```
This type will require values equal to keys of T object, but only these ones which are functions


## Infer
"Within the extends clause of a conditional type, it is now possible to have infer declarations that introduce a type variable to be inferred. Such inferred type variables may be referenced in the true branch of the conditional type. It is possible to have multiple infer locations for the same type variable."

Example:

```ts
type MyUnionTypesBase<T> = T extends Array<infer U> ? U : never;
let myValue : MyUnionTypesBase<[number, string, boolean]>;
```

My value can be type number | string | boolean (number or string or boolean)

Symbols
=================
Instead of using normal string keys in object it can be used predefined and assigned to variable Symbol
example:

```ts
const getSthSymbol = Symbol("getSth");

class SampleClass {
    [getSthSymbol](){
	return "something";
    }
}
```

**Symbols are unique**
```ts
let sym2 = Symbol("key");
let sym3 = Symbol("key");
```

sym2 is not equal to sym3 (sym2 != sym3)


Modules
=================
Import and export mechanism (between files and objects)

Example:

data.ts file
```ts
export class DataClass {
    ...
}
export interface IOperations {
...
}
```
Import
other file 
```ts
import {DataClass as ImportedDataClass} from './data.ts'
```

Import all:
```ts
import * from './data.ts'
```

## Namespaces
Encapsulated scope of classes, objects, functions, interfaces and others. 

Example:
```ts
namespace UserArea {
	export interface IUser {}
	export class User {}
		class Person {
	}
}
let user = UserArea.User;
```

## Ambient modules
Encapsulated scope of classes, objects, functions, interfaces, and others - that is available to export/import.
"We call declarations that don’t define an implementation “ambient”. Typically, these are defined in .d.ts files. "

Example
```ts
declare module "path" {
	export function normalize(p: string): string;
	export function join(...paths: any[]): string;
	export var sep: string;
}

```

and then we can import it

```ts
import * as URL from „path"
```

## replace global function
Some functions in JS are global and we may have not type for them. We can use 'declare' keyword here

```ts
declare const System: IOurSystemObject;
```

Decorators
=================
"Decorators provide a way to add both annotations and a meta-programming syntax for class declarations and members."

```ts
 function customMethodDecorator(value: string) {
    return function (target: any, propertyKey: string, descriptor: PropertyDescriptor) {  
	descriptor.value = () => {
	    return "Hello, " + value;
	}
    };
}
```

it will change return value of decorated function so it will return "Hello " + value from decorator

```ts
@customMethodDecorator("here is hacker")
    greet() {
	return "Hello, " + this.greeting;
    }
```

greet() will return "Hello, here is hacker"

Generators
=================
Loops can be executed "step by step"

Example:
```ts
function* idMaker(){
	let index = 0;
	while(index < 3)
		yield index++;
}

let gen = idMaker();

let value;
value = gen.next().value // result 1
value = gen.next().value // result 2
value = gen.next().value // result 3
```

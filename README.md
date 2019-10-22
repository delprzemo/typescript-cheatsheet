# TypeScript Cheatsheet
Set of basic functionalities from TypeScript in one place. Cheatsheet was created by https://foreach.pl trainers for their students.
Please note that some functionalities are part of ES201x but they are frequently used in TypeScript as well.

**1. Basic variable types**

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




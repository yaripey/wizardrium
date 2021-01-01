# Data types and variables in JavaScript

## Table of contents
- [Variables and constants](#variables-and-constants)
  - [General Info](#general-info)
    - [Variable Type](#variable-type)
    - [Difference between constant and variable](#difference-between-constant-and-variable)
    - [Var Keyword](#var-keyword)
- [Data types](#data-types)
  - [String](#string)
  - [Number](#number)
  - [BigInt](#bigint)
  - [Boolean](#boolean)
  - [Undefined](#undefined)
  - [JavaScript Null](#null)
  - [JavaScript Symbol](#symbol)
  - [JavaScript Object](#object)
- [JavaScript typeof](#javascript-typeof)


## Variables and constants

### General Info

First, to create a constant or a variable, we don't need to specify the type of the variable, like in some other programing languages. 

#### Variable Type

```
const x = 2;
```

This line tells JS to create a _constant_ `x` with _value_ of `2`.

In this particular case the type of the variable will be _Number_. JS takes the responsibility of defining the type of the variable based on the value that you give it. This time, `2` is just a number. On the other hand, we can type it like this:

```
const x = '2';
```

In this case, `'2'` is a string (because it is in quotes), that's why in here, JS will create a _string_ contsant `x`.

We can also freely change the data type that variable is storing without mistakes, so such code will still be valid:

```
let test = 1
test = "Hi there"
test = { test: 'Hi there!' }
```

#### Difference between constant and variable

If we want to create not a _constant_, but a _variable_, we need to use the keyword __let__.

```
let x = 2;
```

Basically, the main difference between _constant_ and _variable_ is that JS will throw an error if we try to reassign a value to a constant. It is usefull, as it allows us to strict ourselves in terms of variable usage. 

__Note!__ It is better to always use `const` over `let` excluding cases, when you are 100% sure that you need a variable.

#### Var Keyword

There is another keyword, `var`. Earlier, this was the only keyword for creating a variable. Difference between `var` and `let` lie in scopes. Simply put, we can refer to `var` as a _global variable_, while `let` is a _local_ one. The global variable is _visible_ throughout the whole code, while the local one is only visible to the block of code that it is declared in.

## Data types

There are eight basic data types in JavaScript.

| Data Types  | Description                                        | Example                       |
| ----------- | -------------------------------------------------- | ----------------------------- |
| `String`    | represents textual data                            | `'hello'`                     |
| `Number`    | an integer or a floating-point number              | `3`, `3,123`                  |
| `BigInt`    | an integer with arbitary precision                 | `1n`                          |
| `Boolean`   | true or false                                      | `true` and `false`            |
| `undefined` | a data type whose variable is not initialized      | `let a`                       |
| `null`      | detonates a `null` value                           | `let a = null`                |
| `Symbol`    | data type whose instances are unique and immutable | `let value = Symbol('hello')` |
| `Object`    | key-value pairs of collection of data              | `let student = { }`           |

Here, all data types except `Object` are primitive data types, whereas `Object` is non-primitive. The `Object` data type can store collections of data, whereas primitive data type can only store a single data.

### String

`String` is used to store text. It can be created like this:
```
const firstString = 'hi'
const secondString = "Hi there"
const thirdString = `Hi there`
```
There is no difference in using _single quotes_ or _double quotes_. But _backticks_ give the string a special property: we can use `${}` structure to insert variables or expression inside string, like this:
```
const a = 2;
const b = 3;
const result = `a + b will be ${a + b}` // "a + b will be 5"
```

### Number

`Number` represents integer and floating numbers (decimals and exponentials). Examples:
```
const number1 = 3;
const number2 = 3.43;
const number3 = 3e5; // 3 * 10^5;
```
A number type can also be `+Infinity`, `-Infinity` or `Nan`.

### BigInt

In JavaScript, `Number` type can only represent numbers less than $(2^{53} - 1)$ and more than $-(2^{53} - 1)$. Hovewer, for bigger numbers we can use `BigInt`. A `BigInt` is created by appending `n` to the end of an integer. Example:
```
const value1 = 900719925124740998n;

const result1 = value1 + 1n;
console.log(result1); // "900719925124740999n"
```

Also, we cannot mix `BigInt` with other data types like `1n + 1` will throw a `TypeError`.

### Boolean

This data type represents logical entities. It can only appear as `true` or `false`. Also `!(true) = false` and vice versa.

### Undefined

This data type represents a _value that is not assigned_. If a varaible is declared but the value is not assigned, then the value of that variable will be `undefined`. We can also manually set `undefined` as a value, but it's not recommended, because if we wan't to assign "empty" value to a variable we can use `null`.

### null

`null` is a special value that represents __empty__ or __unknown value__. 
__Note!__ `null` is not the same as NULL or Null.

### Symbol

`Symbol` is an immutable primitive value that is unique. Example:

```
const value1 = Symbol('hello');
const value2 = Symbol('hello');
```

Though `value1` and `value2` both contain `hello`, they are different as they are of the `Symbol` type.

### Object

An `object` is a complex data type that allows us to store collections of data. For example:

```
const student = {
  firstName: 'Steven',
  lastName: null,
  class: 5
}
```

## JavaScript typeof

To find the type of a variable, we can use the `typeof` operator. Example:
```
const test = 'hello'
typeof(test); // returns 'string'
```

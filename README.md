![General Assembly Logo](http://i.imgur.com/ke8USTq.png)

# JavaScript Basics 1

## Introduction

A review of the basics of JavaScript.

Although ECMAScript 6 ([ES6](http://www.ecma-international.org/ecma-262/6.0/)) is the latest standard, adopted in June of 2015, we'll focus on features from the [ES5](http://www.ecma-international.org/ecma-262/5.1/) standard.  Some of the references in this document may include descriptions of ES6 features.  These features will usually be denoted with `(new in ECMAScript 6)` in the main text or with a **flask icon** in the navigation sidebar.

## Objectives

By the end of this lesson, students should be able to:

- List all 5 JavaScript primitives and give an example of each
- Identify the operator in an expression and explain what it does
- Define variable and contrast with value
- Evaluate simple JavaScript by inspection
- Write simple scripts that use flow control

## To start

In your browser open `https://github.com/ga-wdi-boston/js-fundamentals-08` and fork the repository.  We'll find the link in slack.

Then in a terminal window at the shell prompt:

```bash
~$ cd wdi
~/wdi$ git clone git@github.com:<github user name>/js-basics-1.git
~/wdi$ cd js-basics-1
~/wdi/js-basics-1$ git branch lesson
~/wdi/js-basics-1$ subl .
~/wdi/js-basics-1$ npm install
```

## Basics

### Node.js

We'll use Node.js as a [REPL](https://nodejs.org/api/repl.html) and a script runner to explore JavaScript features.

- <b>R</b>ead
- <b>E</b>valuate
- <b>P</b>rint
- <b>L</b>oop

```bash
~/wdi/js-basics-1$ node
>
```

What other tools could we use as a JavaScript REPL?

Are there benefits or drawbacks to using one over another?

What about a script runner?

Benefits or drawbacks with the options available?

### Primitive types

ES5 has 5 primitive [types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures): `Number`, `String`, `Boolean`, `null`, and `undefined`.

Type | Examples
---- | ----------------
Number | `-0`, `NaN`, `Infinity`
String | `''`, `"The non-empty string."`
Boolean | `true`, `false`
null | `null`
undefined | `undefined`

Primitive types represent **immutable** values.  We'll contrast this with reference types in a later lesson.

The types Number and String both have large sets of possible values.  Boolean has only two values and null and undefined each have just one.

### Literals

Literals represent specific values in the source code.  Some examples are `1`, `'A string'`, `null`.

### Variables

```js
> dob;
```


Variables need to be declared.
```js
> var dob;
```

Variables name storage for the value they contain.  Because JavaScript is a dynamically typed language, you can assign a value of one type to a variable and then later assign a value of a different type to that same variable.

In JavaScript, `null` represents the explicitly omitted value, whereas `undefined` represents the default omitted value.  Variables that have been declared but are uninitialized or unset have the value `undefined`.

### Operators

Operators come in three classes, unary, binary (the most common), and ternary (there is only one).

Operator precedence determines the order in which operators are evaluated. Operators with higher precedence are evaluated first.

Associativity determines the order in which operators of the same precedence are processed.

The following table lists a subset of the JavaScript [operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) from higher to lower precedence.

Type | Associativity | Operators
---- | ------------- | ---------
grouping | n/a | `()`
postfix increment | n/a | `++ --`
negation, numeric conversion, <br> prefix increment, type | right-to-left | `! - + ++ -- typeof`
multiplication, division | left-to-right | `* / %`
addition, subtraction | left-to-right | `+ -`
relation | left-to-right | `< <= > >=`
strict equality | left-to-right | `=== !===`
logical and | left-to-right | `&&`
logical or | left-to-right | <code>&#124;&#124;</code>
conditional | right-to-left | `?:`
assignment | right-to-left | <code>= += -= &#42;= /= %= &#124;=</code>

### Expressions

An expression is a combination of literals, variables, operators, function invocations and sub-expressions that are interpreted and produce a value.  Not all such combinations produce _sensible_ results.

The simplest expression is a variable or literal followed by a semicolon. More complicated expressions are formed by combining simpler expressions using operators.

An expression with all of the variables replaced with literals that are equal to the values of the variables will produce the same result.

#### Numeric

```js
5 + 3;
7 - 2;
11 % 5;
```

#### String

```js
var firstName;
var lastName;
var fullName;
firstname = "Antony";
lastName = "Donovan";
fullName = firstName + " " + lastName;
```

#### Assignment

```js
var height;
height = 77;
var name;
name = "Antony";
height - 1;
height;
height = height - 1;
height;
```

Remember: JavaScript variables are untyped.

```js
var height;
height = 76;
height = "Antony";
```

Although it doesn't cause an error, avoid confusing code like the above.

Now let's compare some common methods of counting.

```js
var i;
i = 0;
i = i + 1;
i = 0;
i += 1;
++i;
i++;
i;
```

#### Type conversion

The unary `+` operator attempts to convert its operand to a Number.  If unsuccessful the result is `NaN`.

If either operand of the binary `+` operator is a string the operator converts the other operator to a string.  Some results of this conversion are more useful than others.

Note the different between `3 + 5 + " times";` and `"times " + 3 + 5`;?

The unary `!` operator converts its operand to a boolean value.

#### Boolean

A boolean expression is a comparison (e.g. `>`, `>=`, `===`) or any value interpreted as a boolean.  We'll use that fact when we get to flow control.  Boolean expression combine using the logical and `&&` and logical `||` operators.

```js
var height = 62;
height === 60;
height > 72;
height = 76;
height > 72;
height > 72 && height < 78;
```

The logical operators "short circuit", which means they stop evaluating operands as soon as the expression is `false` for `&&`, or true for `||`.


##### truthy and falsy

What do you think of when you here "truthy" and "falsy"?

The falsy list (everything else in JavaScript is truthy),

- `false`
- `undefined`
- `null`
- `0 // and -0`
- `NaN`
- `""  // and '' - the empty string`

Note:  The negation of a truthy value is `false` and the negation of a falsy value is `true`.

```js
var truthy;
var falsy;
truthy = "A non-empty string";
falsy = 0;
!truthy;
!falsy;
```

### Flow Control

The if statement:

```js
//We'll learn about require later in the course
var ask = require('./ask.js');

var name = ask("What's your name? ");
if (name === 'Antony') {
  console.log('Hi, Antony!');
} else if (name === 'Matt') {
  console.log('Hi, Matt!');
} else {
  console.log('Hi, stranger.');
}
```

The while loop:

```js
//We'll learn about require later in the course
var ask = require('./ask.js');

var count = 0;
var answer = '';

while (answer !== 'Antony') {
  answer = ask("Guess my name? ");
  count = count + 1;
}
console.log("You got it in " + count + " tries!");
```

The for loop:

```js
for (var i = 0; i < 10; i++) {
  console.log(i);
}
```

which is equivalent to:

```js
var i = 0;
while (i < 10) {
  console.log(i);
  i++;
}
```

Nesting conditionals in loops:

```js
for (var i = 0; i < 10; i++) {
  if (i===5) {
    console.log("five!");
  }
}
```

## Assessment

Please follow the instructions at https://github.com/ga-wdi-boston/js-basics-1-assessment

## Additional Resources

See the following sections at https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide

- Grammar and types
- Control flow and error handling
- Loops and iteration
- Expressions and operators
- Number and dates
- Text formatting

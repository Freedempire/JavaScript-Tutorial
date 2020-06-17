# JavaScript Tutorial

- [JavaScript Tutorial](#javascript-tutorial)
  - [Introduction](#introduction)
    - [What is JavaScript?](#what-is-javascript)
    - [What can in-browser JavaScript do?](#what-can-in-browser-javascript-do)
    - [What can't in-browser JavaScript do?](#what-cant-in-browser-javascript-do)
    - [Languages over JavaScript](#languages-over-javascript)
  - [Manuals and specifications](#manuals-and-specifications)
    - [Specification](#specification)
    - [Manuals](#manuals)
  - [Developer console](#developer-console)
    - [Google Chrome](#google-chrome)
  - [Fundamentals](#fundamentals)
    - [The script tag](#the-script-tag)
    - [Modern markup](#modern-markup)
      - [The type attribute: `<script type=...>`](#the-type-attribute-script-type)
      - [The language attribute: `<script language=...>`](#the-language-attribute-script-language)
      - [Comments before and after scripts](#comments-before-and-after-scripts)
    - [External scripts](#external-scripts)
    - [Code structure](#code-structure)
      - [Statements](#statements)
      - [Semicolons](#semicolons)
      - [Comments](#comments)
    - [The modern mode, `"use strict"`](#the-modern-mode-use-strict)
    - [Variables](#variables)
      - [Variable naming](#variable-naming)
      - [Constants](#constants)
    - [Data types](#data-types)
      - [Number](#number)
      - [Bigint](#bigint)
      - [String](#string)
      - [Boolean](#boolean)
      - [The null value](#the-null-value)
      - [The undefined value](#the-undefined-value)
      - [Objects](#objects)
      - [Symbol](#symbol)
      - [The `typeof` operator](#the-typeof-operator)
    - [Browser interaction functions: `alert`, `prompt`, `confirm`](#browser-interaction-functions-alert-prompt-confirm)
      - [alert](#alert)
      - [prompt](#prompt)
      - [confirm](#confirm)
    - [Type conversions](#type-conversions)
      - [String conversion](#string-conversion)
        - [Numeric conversion](#numeric-conversion)
        - [Numeric conversion rules](#numeric-conversion-rules)
      - [Boolean conversion](#boolean-conversion)
        - [Boolean conversion rules](#boolean-conversion-rules)
    - [Operators](#operators)
      - [Bitwise operators](#bitwise-operators)
    - [Comparisons](#comparisons)
      - [String comparison](#string-comparison)
      - [Compasion of different types](#compasion-of-different-types)
      - [Strict equality](#strict-equality)
      - [Compasion with `null` and `undefined`](#compasion-with-null-and-undefined)
        - [For a non-strict check `==`](#for-a-non-strict-check-)
        - [For maths and other comparisons `<`, `>`, `<=`, `>=`](#for-maths-and-other-comparisons----)
        - [Incomparable `undefined`](#incomparable-undefined)
    - [Conditions: `if` statement, `?` conditional operator](#conditions-if-statement--conditional-operator)
      - [The `if` statement](#the-if-statement)
      - [The `else` clause](#the-else-clause)
      - [Conditional operator](#conditional-operator)
      - [Multiple `?`](#multiple-)
      - [Using `?` as a replacement for `if`](#using--as-a-replacement-for-if)
    - [Logical operators](#logical-operators)
      - [`||` OR](#-or)
        - [Getting the first truthy value from a list of variables or expressions](#getting-the-first-truthy-value-from-a-list-of-variables-or-expressions)
        - [Short-circuit evaluation](#short-circuit-evaluation)
      - [`&&` AND](#-and)
        - [Don't replace `if` with `&&` or `||`](#dont-replace-if-with--or-)
      - [`!` NOT](#-not)
    - [Nullish coalescing operator `??`](#nullish-coalescing-operator-)
    - [Loops: `while` and `for`](#loops-while-and-for)
      - [The `while` loop](#the-while-loop)
      - [The `do...while` loop](#the-dowhile-loop)
      - [The `for` loop](#the-for-loop)
      - [Breaking the loop](#breaking-the-loop)
      - [Continue to the next iteration](#continue-to-the-next-iteration)
      - [Labels for `break`/`continue`](#labels-for-breakcontinue)
    - [The `switch` statement](#the-switch-statement)
      - [Grouping of `case`](#grouping-of-case)
    - [Functions](#functions)
      - [Function declaration](#function-declaration)
      - [Local variables](#local-variables)
      - [Outer variables](#outer-variables)
      - [Parameters](#parameters)
      - [Default values](#default-values)
      - [Returning a value](#returning-a-value)
      - [Naming a function](#naming-a-function)
    - [Function expressions](#function-expressions)
      - [Callback functions](#callback-functions)
      - [Function expression vs function declaration](#function-expression-vs-function-declaration)
    - [Arrow functions](#arrow-functions)
      - [Multiline arrow functions](#multiline-arrow-functions)
  - [Code quality](#code-quality)
    - [Debugging in Chrome](#debugging-in-chrome)
      - [The Sources panel](#the-sources-panel)
      - [Breakpoints](#breakpoints)

## Introduction

### What is JavaScript?

The programs in this language are called *scripts*. They can be written right in a web page's HTML and run automatically as the page loads.

Scripts are provided and executed as plain text. They don't need special preparation or compilation to run.

Today JavaScript can execute not only in the browser, but also on the server, or actually on any device that has a special program called **the JavaScript engine**.

The browser has an embeded engine sometimes called a **JavaScript virtual machine**.

* V8 - in Chrome and Opera
* SpiderMonkey - in FireFox
* Trident, Chakra - in IE
* ChakraCore - in Microsoft Edge
* Nitro, SquirrelFish - in Safari

How does engines work?

1. The engine reads/parses the script.
2. Then it converts the script to the machine language.
3. And then the machine code runs.
4. The engine applies optimizations at each step of the process. It even watches the compiled script as it runs, analyzes the data that flows through it, and further optimizes the machine code based on that knowledge.

### What can in-browser JavaScript do?

Modern JavaScript is a safe programming language. It does not provide low-level access to memory or CPU, because it was initially create for browsers which do not require it.

JavaScript's capabilities greatly depend on the environment it's running in. For instance, Node.js supports functions that allow JavaScript to read/write arbitrary files, perform network requests, etc.

In-browser JavaScript is able to:

* Add new HTML to the page, change the existing content, modify styles.
* React to user actions, run on mouse clicks, pointer movements, key presses.
* Send requests over the network to remote servers, download and upload files (so-called AJAX and COMET technologies).
* Get and set cookies, ask questions to the visitor, show messages.
* Remember the data the client side.

### What can't in-browser JavaScript do?

Examples of restrictions include:

* JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
* There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission.
* Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).
* JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. It requires explicit agreement (expressed in HTTP headers) from the remote side.

### Languages over JavaScript

Recently a plethora of new languages appeared, which are *transpiled* (translate compile) to JavaScript before they run in the browser.

Examples of such languages:

* **CoffeeScript** is a syntactic sugar for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code.
* **TypeScript** is concentrated on adding strict data typing to simplify the development and support of complex systems.
* **Flow** also adds data typing, but in a different way.
* **Dart** is a standalone langueage that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript.

## Manuals and specifications

### Specification

The ECMA-262 specification contains the most in-depth, detailed and formalized information about JavaScript. It defines the language.

### Manuals

* MDN (Mozilla) JavaScript Reference is a manual with examples and other information. It’s great to get in-depth information about individual language functions, methods etc.

  One can find it at <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference.>
* MSDN – Microsoft manual with a lot of information, including JavaScript (often referred to as JScript). If one needs something specific to Internet Explorer, better go there: <http://msdn.microsoft.com/>.

## Developer console

To see errors and get a lot of other useful information about scripts, developer tools have been embeded in browsers.

### Google Chrome

Press <kbd>F12</kbd>, the developer tools will open on the Console tab by default.

There is a  blue `>` symbol. It marks a command line where we can type JavaScript commands. Press <kbd>Enter</kbd> to run; press <kbd>Shift+Enter</kbd> to insert multiple lines of commands.

## Fundamentals

We need a working enviroment to run our scripts and the browser is a good choice.

### The script tag

JavaScript programs can be inserted into any part of an HTML document with the help of the `<script>` tag.

For instance:

```html
<!DOCTYPE HTML>
<html>
  <body>
    <p>Before the script...</p>

    <script>
      alert('Hello World!');
    </script>

    <p>After the script.</p>
  </body>
</html>
```

The `<script>` tag contains JavaScript code which is automatically executed when the browser processes the tag.

### Modern markup

#### The type attribute: `<script type=...>`

The old HTML standard, HTML4, required a script to have a `type` attribute. Usually it was `type="text/javascript"`. It’s not required anymore.

The modern HTML standard has totally changed the meaning of this attribute. Now it can be used for JavaScript modules.

#### The language attribute: `<script language=...>`

The language attribute was meant to show the language of the script. This attribute no longer makes sense because JavaScript is the default language. There is no need to use it.

#### Comments before and after scripts

In ancient books and guides, you may find comments inside `<script>` tags, like this:

```html
<script type="text/javascript"><!--
  ...
//--></script>
```

This trick isn't used in modern JavaScript. These comments hide JavaScript code from old browsers that didn't know how to process the `<script>` tag.

### External scripts

If we have a lot JavaScript code, we can put it into a separate file.

Script files are attached to HTML with the `src` attribute:

```html
<script src="/path/to/script.js"></script>
```

We can provide an absolute path to the script from the site root as above, or a relative path from the current page, or a full URL.

To attach several scripts, use multiple `script` tags.

If `src` is set, the script content is ignored.

As a rule, only the simplest scripts are put into HTML. More complex ones reside in separate files. The benefit of a separate file is that the browser will download it and store it in its cache which can be reused later to save traffic and time.

### Code structure

#### Statements

Statements are syntax constructs and commands that perform actions.

Statements can be separated with a semicolon.

#### Semicolons

In JavaScript a semicolon may be omitted in most cases when a line break exists.

JavaScript interprets the line break as an “implicit” semicolon. This is called an **automatic semicolon insertion**.

There are cases when a newline does not mean a semicolon. For example:

```JavaScript
alert(3 +
1
+ 2);
```

The code outputs 6 because JavaScript does not insert semicolons here.

There are also situations where JavaScript “fails” to assume a semicolon where it is really needed.

So, to be safer, it is recommended that always putting semicolons between statements even if thay are separated by newlines.

#### Comments

Comments can be put into any place of a script. They don’t affect its execution because the engine simply ignores them.

One-line comments start with two forward slash characters `//`.

Multiline comments start with a forward slash and an asterisk `/*` and end with an asterisk and a forward slash `*/`.

```JavaScript
// This is a single-line comment.
/* This
is
a
multi-line
comment. */
```

Nested comments are not supported, i.e. no `/*..*/` inside another `/*...*/`.

### The modern mode, `"use strict"`

In 2009 ECMAScript 5 (ES5) appeared, it added new features to the language and modified some existing ones. To keep the old code working, most such modifications are off by default. You need to explicitly enable them with a special directive `"use strict"` or `'use strict'`.

When it is located at the top of a script (and it should be, only comments may appear above it, otherwise the strict mode may not be enabled), the whole script works the modern way.

`"use strict"` can alse be put at the beginning of a function, which enables strict mode in that function only.

There's no way to cancel `"use strict"`. Once in strict mode, there's no going back.

Modern JavaScript supports classes and modules which enable strict mode automatically. So we don't need to add the `"use strict"` directive at the top, if we use these new features.

When using a developer console to run code, it isn't in strict mode by default. You can use <kbd>Shift+Enter</kbd> to input multiple lines, and put `"use strict"` on top.

### Variables

A variable is a named storage for data.

To create a variable in JavaScript, use the `let` keyword.

For example:

```JavaScript
let message;        // variable declaration
message = 'Hello';  // variable assignment
alerat(message);

let user = 'John', age = 25, gender = 'male'; // multiple variable initialization
```

Declaring multiple variables in one line is not recommended however.

A variable should be declared only once. A repeated declaration of the same variable is an error.

In older scripts, you may also find another keyword `var` instead of `let`. The `var` keyword is *almost* the same as `let`, but there are subtle difference between them.

#### Variable naming

Differences in naming rules in JavaScript:

* The dollar sign '$' can be used in variable names, .
* Non-latin letters can also be used in variable names, although not recommended, for example: `let 我 = 'tony';`
  
If not in strict mode, we can create a variable by a mere assignment of the value without using `let`. This is a bad practice and would cause an error in strict mode.

#### Constants

To declare a constant variable, use `const` instead of `let`.

There's a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution. Such constants are named using capital letters and underscores.

For example:

```JavaScript
const COLOR_RED = '#F00';
const COLOR_GREEN = '#0F0';
const COLOR_BLUE = '#00F';

let color = COLOR_RED;  // easy to remember, easy to understand, hard to mistype
alert(color);
```

People normally use capitals for a constant that is known before execution or hard-coded, and name constants like other variables if they are not.

### Data types

There are 8 basic data types in JavaScript.

We can put any type in a variable. For example, a variable can at one moment be a string and then store a number. Programming language that allow such things are called **dynamically typed**.

#### Number

The `number` type represents both integer and floating point numbers.

Beside regular numbers, “special numeric values” are also belong to this data type:

* `Infinity`, represents the mathematical Infinity ∞, a special value that's greater than any number;
* `-Infinity`;
* `NaN`, not a number, represents a computational error, a result of an incorrect or an undefined mathematical operation. Any further operation on `NaN` returns `NaN`.

Doing math is safe in JavaScript. The script will never stop with a fatal error. At worst, we'll get `NaN`.

#### Bigint

The `number` type cannot represent integer values larger than (2^53-1) (that’s 9007199254740991), or less than -(-2^53-1) for negatives.

`bigint` type is recently add to the language to represent integers of arbitrary length.

A `bigint` value is created by appending `n` to the end of an integer:

```JavaScript
const bigInt = 1234567890123456789012345678901234567890n;
```

#### String

A `string` in JavaScript must be surrounded by quotes.

There are 3 types of quotes:

* Double quotes: `"Hello"`.
* Single quotes: `'Hello'`.
* Backticks (\`\`): <code>\`Hello\`</code>.

Double quotes and single quotes are simple quotes, and there's practically no difference between them.

Backticks are extended functionality quotes. They allow us to embed variables and expressions into a string by wrapping them in `${…}`:

```JavaScript
let str = "Hello";
let str2 = 'Single quotes are ok too';
let embed_variable = `can embed another ${str}`;  // can embed another Hello
let embed_expression = `the result is ${1 + 2}`;  // the result is 3
```

There's no character type in JavaScript as in C or Java.

#### Boolean

The `boolean` type has only two values, `true` and `false`.

#### The null value

The special `null` value forms a separate type of its own.

In JavaScript it's a special value which represents “nothing”, “empty” or “value unknown”.

#### The undefined value

The special value `undefined` also makes a type of its own. 

The meaning of `undefined` is “value is not assigned”.

If a variable is declared, but not assigned, then its value is `undefined`.

It is possible to explicitly assign `undefined` to a variable. Normally, one uses `null` to assign an “empty” or “unknown” value to a variable, while `undefined` is reserved as a default initial value for unassigned things.

#### Objects

The `object` type is special. All other types are called “primitive” because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and more complex entities.

#### Symbol

The `symbol` type is used to create unique identifiers for objects.

#### The `typeof` operator

The `typeof` operator returns the type of the argument.

It supports two forms of syntax:

1. As an operator: typeof x.
2. As a function: typeof(x).

Examples:

```JavaScript
typeof undefined    // "undefined"
typeof 0            // "number"
typeof 10n          // "bigint"
typeof true         // "boolean"
typeof "foo"        // "string"
typeof Symbol("id") // "symbol"
typeof Math         // "object"
typeof null         // "object"
typeof alert        // "function"
```

The result of `typeof null` is "object". That’s an officially recognized error in `typeof` behavior, coming from the early days of JavaScript and kept for compatibility. Definitely, `null` is not an object.

### Browser interaction functions: `alert`, `prompt`, `confirm`

#### alert

It shows a message and waits for the visitor to press OK.

The mini-window with the message is called a *modal window*, which means the user cannot interact with the rest of the page unless they have dealt with the window, i.e. pressing the OK button in this case.

#### prompt

The function `prompt` accepts two arguments:

```JavaScript
result = prompt(title, [default]);
```

It shows a modal window with a text message, an input field, and the buttons OK and Cancel.

* title: The text to show the visitor.
* default: An optional second parameter, the initial value for the input field.

  The square bracket around it denotes that it is optional, not required.

The visitor can type something in the prompt input field and press OK. Then we can get that text in the `result` variable. Or they can cancel the input by pressing Cancel or hitting the <kbd>Esc</kbd> key, then we get `null` as the `result`.

For instance:

```JavaScript
let age = prompt("How old are you?", 100);
alert(`You are ${age} years old.`); // You are 100 years old.
```

#### confirm

The syntax:

```JavaScript
result = confirm(question);
```

The function `confirm` shows a modal window with a question and two buttons: OK and Cancel.

The result is true if OK is pressed and false otherwise.

For example:

```JavaScript
let isBoss = confirm("Are you the boss?");
alert(isBoss);  //true if OK is pressed
```

All these methods are modal: they pause script execution and don’t allow the visitor to interact with the rest of the page until the window has been dismissed.

### Type conversions

Most of the time, operators and functions automatically convert the values given to them to the right type. For example, `alert` automatically converts any value to a `string` to show it. Mathematical operations convert values to `number`s.

There are also cases when we need to explicitly convert a value to the expected type.

#### String conversion

We can call the `String(value)` function to convert a value to a `string`.

```JavaScript
let value = true;
alert(typeof value);  // boolean

value = String(value);
alert(typeof value);  // string
alert(value);         // true
```

String conversion is mostly obvious. A `false` becomes `"false"`, `null` becomes `"null"`, etc.

##### Numeric conversion

Numeric conversion happens in mathematical functions and expressions automatically.

For example:

```JavaScript
alert( "6" / "2" ); // 3, strings are converted to numbers
```

We can use the `Number(value)` function to explicitly convert a value to a number.

```JavaScript
let str = "123";
let num = Number(str);
alert(typeof num);  // number
```

Explicit conversion is usually required when we read a value from a string-based source like a text form but expect a number to be entered.

If the string is not a valid number, the result of such a conversion is `NaN`.

##### Numeric conversion rules

Value|Becomes...
:--|:--
`undefined`|`NaN`
`null`|`0`
`true`|`1`
`false`|`0`
`string`|whitespaces from the start and end are ignored. If the remaining string is empty, the result is `0`. An error gives `NaN`.

Most mathematical operators also perform such conversion. The unary `+` operator can be used in same way of `Number()` function.

#### Boolean conversion

Boolean conversion happens in logical operations, and we can also perform it with a call to `Boolean(value)`. `!!` can also be used to convert values to boolean type.

##### Boolean conversion rules

* Values that are intuitively "empty" like number `0`/`0n`, an empty string `''`/`""`/<code>``</code>, `null`, `undefined`, and `NaN`, become `false`.
* Other values become `true`.

Note that strings like `"0"` and `" "` are true, because JavaScript always treats a non-empty string as `true`, unlike in PHP, which treats `"0"` as `false`.

### Operators

Operators|Meaning
:--|:--
Unary `-`|Negation
Unary `+`|Numeric conversion, does the same thing as `Number()`.
`+`|Addition
`-`|Subtraction
`*`|Multiplication
`/`|Division
`%`|Remainder/modulo/modulus
`**`|Exponentiation
`+`|String concatenation. If any of the operands is a `string`, the other one is converted to a `stirng`. Other arithmetic operators work only with `number`s and always convert their operands to `number`s.
`=`|Assignment, assigns the value of the left operand to the right operand, then returns it.
`+=`, `-=`, `*=`, `/=`, `%=`, `**=`|Modify-and-assign
`++`|Increment, can only be applied to variables, can be placed either before or after a variable with different effect: the prefix form returns the new value while the postfix form returns the old value (prior to increment).
`--`|Decrement, likely effect as above.
`,`|Comma. The comma operator allows us to evaluate several expressions, dividing them with a comma `,`. Each of them is evaluated but only the result of the last one is returned. The precedence of comma operator is lower than that of assignment operator.

```JavaScript
let apples = "2";
let oranges = "3";
alert(apples + oranges);    // "23", string concatenation.
alert(+apples + +oranges);  // 5, numeric conversion first.

alert('1' + 2);             // "12"
alert(1 + '2');             // "12"
alert(2 + 2 + '1');         // "41"
alert('1' + 2 + 2);         // "122", orders do affect the result.


let a = 1;
let b = 2;
let c = 3 - (a = b + 1);    // 0, this syntax is invalid in Python, and is not recommended in JavaScript.
alert(a);                   // 3
alert(c);                   // 0

let x, y, z;
x = y = z = 2 + 2;          // chaining assignments, also invalid in Python, not recommended.

let a = (1 + 2, 3 + 4);     // only the last expression is returned
alert(a);                   // 7, the result of 3 + 4.
```

If an expression has more than one operator, the execution order is defined by their precedence, or, in other words, the default priority order of operators.

Precedence table: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence>

#### Bitwise operators

Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation.

The list bitwise operators:

* AND `&`
* OR `|`
* XOR `^`
* NOT `~`
* LEFT SHIFT `<<`
* RIGHT SHIFT `>>`
* ZERO-FILL RIGHT SHIFT `>>>`

### Comparisons

Comparison operators|Meaning
:--|:--
`>`/`<`|Greater/less than
`>=`/`<=`|Greater than or equal to / less than or equal to
`==`|Equal to
`!=`|Not equal to
`===`|Strictly equal to, strict equality operator, checks equality without type conversion.
`!==`|Strictly not equal to, strict non-equality operator, checks inequality without type conversion.

All comparison operators return a `boolean` value, `true` or `false`.

#### String comparison

When comparing strings, strings are compared letter-by-letter according to the index in the internal encoding table (Unicode).

#### Compasion of different types

When comparing values of different types, JavaScript converts the values to `number`s.

For example:

``` JavaScript
alert('2' > 1);         // true, string '2' becomes number 2.
alert('01' == 1);       // true, string '01' becomes number 1.
alert(true == 1);       // true, true becomes 1.

let a = 0;
alert(Boolean(a));      // false
let b = '0';
alert(Boolean(b));      // true
alert(a == b);          // true!

let c = '';
alert(Boolean(c));      // false
let d = ' ';
alert(Boolean(d));      // true
alert(c == d);          // true!
```

#### Strict equality

A strict equality operator === checks the equality without type conversion.

In other words, if `a` and `b` are of different types, then `a === b` immediately returns `false` without an attempt to convert them.

There is also a “strict non-equality” operator `!==` analogous to `!=`.

#### Compasion with `null` and `undefined`

##### For a non-strict check `==`

There’s a special rule: `null` and `undefined` equal each other (in the sense of ==), but not any other value.

This means `null` and `undefined` are not converted to `number`s when any of them are compared with other operands by `==`, because `null` becomes `0` and `undefined` becomes `NaN` if they are converted to `number`s.

##### For maths and other comparisons `<`, `>`, `<=`, `>=`

`null` and `undefined` are converted to `number`s as usual.

```JavaScript
alert(null == undefined);   // true, the special rule
alert(null == 0);           // false
alert(null == false);       // false
alert(undefined == 0);      // false
alert(undefined == NaN);    // false

alert(null > 0);            // false
alert(null == 0);           // false
alert(null >= 0 );          // true, null becomes 0, this special rule makes the result illogical.
```

##### Incomparable `undefined`

The value `undefined` should not be compared to other values.

```JavaScript
alert(undefined > 0);       // false
alert(undefined < 0);       // false
alert(undefined == 0);      // false
alert(undefined >= 0);      // false
```

Treat any comparison with `null`/`undefined` with exceptional care or using strict equality/inequality operators. Before using comparisons `>`, `<`, `>=`, `<=` with a variable which may be `null`/`undefined`, make sure you know what you are doing.

### Conditions: `if` statement, `?` conditional operator

#### The `if` statement

The `if (condition)` statement evaluates a condition in parentheses, if the result is `true`, executes a block of code.

For example:

```JavaScript
let year = prompt("In which year was ECMAScript-2015 specification published?", "");
if (year == 2015) alert("You are right!");
```

If we want to execute more than one statement, we have to wrap the code block inside curly braces.

```JavaScript
if (year == 2015) {
  alert("You are right!");
  alert("You are so smart!");
}
```

#### The `else` clause

The `if` statement may contain an optional `else` clause. It executes when the condition is false.

```JavaScript
if (condition) {
  statements
} else {
  statements
}
```

To test several variants of a condition, using `else if`.

```JavaScript
if (condition1) {
  statements
} else if (condition2) {
  statements
} else if (condition3) {
  statements
} else {
  statements
}
```

#### Conditional operator

Sometimes, we need to assign a variable depending on a condition. The so-called “conditional” or “question mark” operator `?` lets us do that in a shorter and simpler way.

The syntax is:

```JavaScript
let result = condition ? value1 : value2;
```

The condition is evaluated, if `true`, `value1` is returned, otherwise `value2`.

For example:

```JavaScript
let accessAllowed1 = (age > 18) ? true : false;

// or without parentheses:
let accessAllowed2 = age > 18 ? true : false;

// actually you don't need ? operator in this case:
let accessAllowed3 = age > 18;
```

#### Multiple `?`

A sequence of conditional operators `?` can return a value that depends on more than one condition.

For example:

```JavaScript
let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';
```

#### Using `?` as a replacement for `if`

Sometimes `?` is used as a replacement for `if`:

```JavaScript
let company = prompt('Which company created JavaScript?', '');

(company == 'Netscape') ?
  alert('Right!') : alert('Wrong!');
```

We don't assign a value to a variable here, instead we execute different code depending on the condition.

Using the conditional operator in this way is not recommended however, because it's less readable and there are also difference between them. For example, non-expression syntax construct cannot be used with `?`.

### Logical operators

There are 3 logical operators: `||` OR, `&&` AND, `!` NOT.

Although they are called “logical”, they can be applied to values of any type, not only `boolean`. Their result can also be of any type.

#### `||` OR

```JavaScript
result = a || b;
result = a || b || c;
alert(true || false);       // true
```

The OR `||` operator does the following:

* Evaluates operands from left to right.
* For each operand, converts it to boolean. If the result is true, stops and returns the original value.
* If all operands have been evaluated, returns the last operand in its original form.

##### Getting the first truthy value from a list of variables or expressions

```JavaScript
let firstName = prompt("Enter your first name:", "");
let lastName = prompt("Enter your last name:", "");
let nickName = prompt("Enter your nick name:", "");

// use OR to choose the one that has data and show it, if all are falsy, show Anonymous
alert("Hello, ${firstName || lastName || nickName || "Anonymous"}!");
```

##### Short-circuit evaluation

`||` processes its arguments until the first truthy value is reached, and then the value is returned immediately, without even touching the other argument.

That importance of this feature becomes obvious if an operand isn’t just a value, but an expression with a side effect, such as a variable assignment or a function call.

```JavaScript
true || alert('not printed.');
false || alert('printed.'); // only this alert is triggered
```

#### `&&` AND

```JavaScript
result = a && b;
result = a && b && c;
alert(true && true);        // true
```

The rules of AND are similar to OR. `&&` returns the first falsy value or the last value if none were found.

The precedence of AND is higher than OR. This rule seems to be redundant.

##### Don't replace `if` with `&&` or `||`

```JavaScript
let x1 = 1;
x1 > 0 && alert("Greater than zero!");

let x2 = 1;
if (x2 > 0) alert("Greater than zero!");
```

#### `!` NOT

`!` converts the operand to `boolean` type, and returns the inverse value. It always returns a boolean value, unlike the other two operators which return original values without conversion.

```JavaScript
result = !value;
alert(!true);               // false
alert(!0);                  // true
```

A double NOT `!!` is sometimes used for converting a value to boolean type.

The precedence of NOT `!` is the highest of all logical operators, so it always executes first, before `&&` or `||`.

### Nullish coalescing operator `??`

This is a recent addition to the language.

`??` provides a short syntax for selecting a first "defined" variable from the list.

The result of `a ?? b` is:

* `a` if it's not `null` or `undefined`,
* `b`, otherwise.

So, `x = a ?? b` is a short equivalent to:

```JavaScript
x = (a !== null && a !== undefined) ? a : b;
```

Similar to `||`, with the difference in falsy values like `0`, `''`, etc. This matters a lot when we’d like to treat `null`/`undefined` differently from those falsy values.

`??` is evaluated after most other operations, but before `=` and `?`.

Due to safety reasons, it’s forbidden to use `??` together with `&&` and `||` operators without *explicit parentheses*.

```JavaScript
let x = 1 && 2 ?? 3;        // syntax error
let x = (1 && 2) ?? 3;      // 2, works
```

### Loops: `while` and `for`

Loops are a way to repeat the same code multiple times.

#### The `while` loop

The `while` loop has the following syntax:

```JavaScript
while (condition) {
  // loop body
}
```

While the condition is truthy, the code from the loop body is executed.

Curly braces are not required for a single-line body.

#### The `do...while` loop

The condition check can be moved below the loop body using the `do..while` syntax:

```JavaScript
do {
  // loop body
} while (condition);
```

#### The `for` loop

Its syntax looks like this:

```JavaScript
for (begin; condition; step) {
  // loop body
}
```

Variables declared in the loop are only visible inside the loop. This is different from the case in Python.

Any part of `for`, i.e. begin, condition, step, can be skipped, even all of them, but the two semicolons in the parentheses must be present.

#### Breaking the loop

We can force the exit at any time using the special `break` directive.

#### Continue to the next iteration

Use `continue` to stop the current iteration and forces the loop to start a new one (if the condition allows).

Syntax constructs that are not expressions cannot be used with the ternary operator `?`. In particular, directives such as `break`/`continue` aren’t allowed there.

```JavaScript
(i > 5) ? alert(i) : continue;  // continue isn't allowed here
```

#### Labels for `break`/`continue`

Sometimes we need to break out from multiple nested loops at once.

A label is an identifier with a colon before a loop:

```JavaScript
labelName: for (...) {
  // loop body
  break labelName;              // break out to the label
}
```

The `continue` directive can also be used with a label. In this case, code execution jumps to the next iteration of the labeled loop.

Label do not allow to jump anywhere. A call to `break`/`continue` is only possible from inside a loop and the label must be somewhere above the directive.

### The `switch` statement

A `switch` statement can replace multiple `if` checks.

The syntax:

```JavaScript
switch (x) {
  case value1:                  // if (x === value1)
    ...
    [break;]
  case value2:                  // if (x === value2)
    ...
    [break;]
  [default:
    ...
    [break;]]
}
```

* The value of `x` is checked for a *strict equality*.
* If the equality is found, `switch` starts to execute the code starting from the corresponding `case`, until the nearest `break` or until the end of `switch`.
* If there is no `break` then the execution continues with the next `case` without any checks.
* If no `case` is matched then the `default` code is executed (if it exists).

Any expression can be a `switch`/`case` argument.

#### Grouping of `case`

Several variants of `case` which share the same code can be grouped. The ability to “group” cases is a side-effect of how `switch`/`case` works without `break`.

```JavaScript
let a = 3;
switch (a) {
  case 1:
    alert("Too small.");
    break;

  case 2:
    alert("Still small.");
    break;

  case 3:
    alert("Right.");
    break;

  case 4:
  case 5:                       // grouped cases, share the same code
    alert("Too big.");
    break;

  default:
    alert("Strange result.");
    break;
}
```

### Functions

Functions are the main “building blocks” of the program. They allow the code to be called many times without repetition.

#### Function declaration

The syntax looks like this:

```JavaScript
function funcName(parameters) {
  // function body
}
```

#### Local variables

A variable declared inside a function, i.e. local variable, is only visible inside that function.

#### Outer variables

A function can access an outer variable or global variable as well.

If a same-named variable is declared inside the function then it shadows the outer one.

It’s a good practice to minimize the use of global variables. Sometimes though they can be useful to store project-level data.

#### Parameters

We can pass arbitrary data to functions using parameters.

When values are passed to a function, they are copied to the parameters. Then the function uses them. So the changes on those values will not be seen outside since they are copied to local variables.

#### Default values

If a parameter is required but not provided, then its value becomes `undefined`, without triggering error. If we want to provide “default” value, then we can specify it after `=`.

Sometimes it makes sense to set default values for parameters not in the function declaration, but at a later stage, during its execution.

To check for omitted parameters, we can compare it with `undefined`:

```JavaScript
function showMessage(text) {
  if (text === undefined) {
    text = 'empty';
  }
  alert(text);
}
```

Or we could use `||` operator:

```JavaScript
function showMessage(text) {
  text = text || 'empty';
  alert(text);
}
```

Or use nullish coalescing operator `??` when falsy values, such as `0`, `''` are considered regular.

#### Returning a value

A function can return a value back into the calling code as the result. The directive `return` can be in any place of the function. When the execution reaches it, the function stops, and the value is returned to the calling code.

It is possible to use `return` without a value. That causes the function to exit immediately. A function with an empty `return` or without it returns `undefined`.

Never add a newline between `return` and the value. That doesn’t work, because JavaScript assumes a semicolon after `return`.

#### Naming a function

* Naming functions concisely with verbs like show..., creat..., calc..., get..., check... and so on to describe what it does.
* One function, one action.
* If some functions are usually called together, create a new one to combine them.

```JavaScript
function checkAge1(age) {
  if (age > 18) return true;
  return confirm('Did parents allow you?');
}

function checkAge2(age) {
  return age > 18 ? true : confirm('Did parents allow you?');
}

function checkAge3(age) {
  return age > 18 || confirm('Did parents allow you?');
}
```

### Function expressions

In JavaScript, a function is a special kind of value.

The syntax used before is called a *function declaration*. There is another syntax for creating a function that called a *function expression*.

It looks like this:

```JavaScript
let sayHi = function() {
  alert("Hello");
};
```

The meaning of the code is to create a function and put it into the variabel `sayHi`. No matter how the function is defined, it's just a value stored in a variable.

We can even print out that value using `alert`:

```JavaScript
function sayHi() {
  alert("Hello");
}

alert(sayHi);                   // shows the source code of the function
```

In JavaScript, a function is a value, so we can deal with it as a value. The code above shows its string representation, which is the source code.

Surely, a function is a special value representing an “action”, in the sense that we can call it like `sayHi()`.

#### Callback functions

```JavaScript
function ask(question, yes, no) {
  if (confirm(question)) yes();
  esle no();
}

function showOk() {
  alert("You agreed.");
}

function showCancel() {
  alert("You canceled the execution.");
}

ask("Do you agree?", showOk, showCancel);
```

The function `ask` should ask `question` and, depending on the user's answer, call function `yes` or `no`.

The arguments `showOk` and `showCancel` of `ask` are called *callback functions* or just *callbacks*.

The idea is that we pass a function and expect it to be “called back” later if necessary.

We can use function expressions to write the same function much shorter:

```JavaScript
function ask(question, yes, no) {
  if (confirm(question)) yes();
  else no();
}

ask(
  "Do you agree?",
  function() {alert("You agreed.");},
  function() {alert("You canceled the execution.");}
);
```

#### Function expression vs function declaration

A function expression is created when the execution reaches it and is usable only from that moment.

A function declaration can be called earlier than it is defined. A global function declaration is visible in the whole script, no matter where it is.

That’s due to internal algorithms. When JavaScript prepares to run the script, it first looks for global function declarations in it and creates the functions.

In **strict mode**, when a function declaration is within a code block, it’s visible everywhere inside that block. But not outside of it.

### Arrow functions

The arrow function looks like this:

```JavaScript
let func = (arg1, arg2, arg3, ..., argN) => expression;
```

This creates a function `func` that accepts arguments `arg1, ..., argN` ,then evaluate the expression on the right side with their use and returns its result.

It's a short version of:

```JavaScript
let func = function(arg1, arg2, ..., argN) {
  return expression;
};
```

If we have only one argument, then parentheses around parameters can be omitted, making that even shorter.

For example:

```JavaScript
let double = n => n * 2;

alert(double(3));               // 6
```

If there are no arguments, parentheses will be empty (but they should be present):

```JavaScript
let sayHi = () => alert("Hello!");

sayHi();                        // Hello!
```

Arrow functions can be used in the same way as function expressions.

#### Multiline arrow functions

If there are multiple expressions or statements on the right side of `=>`, we should enclose them in curly braces and use a normal `return` within them.

Like this:

```JavaScript
let sum = (a, b) => {
  let result = a + b;
  return result;
};

alert(sum(1, 2));
```

## Code quality

### Debugging in Chrome

Debugging is the process of finding and fixing errors within a program.

#### The Sources panel

Turn on developer tools with <kbd>F12</kbd>, then select the Sources panel.

The Sources panel has 3 parts:

* The **File Navigator** pane lists HTML, JavaScript, CSS and other files, including images that are attached to the page.
* The **Code Editor** pane shows the source code.
* The **JavaScript Debugging** pane.

If we press <kbd>Esc</kbd>, then a console opens below.

#### Breakpoints

A breakpoint is a point of code where the debugger will automatically pause the code execution.

While the code is paused, we can examine current variables, execute commands in the console etc. In other words, we can debug it.
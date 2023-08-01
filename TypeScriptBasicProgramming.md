### JavaScript?

&nbsp;&nbsp;&nbsp;&nbsp;JavaScript (also known as ECMAScript or JS) started life as a simple scripting language for browsers. At the time it was invented, it was intended to be used for short snippets of code embedded in a web page - writing more than a few dozen lines of code would be somewhat unusual. Because of this, early web browsers were quite slow in executing such code. However, over time JS became more and more popular and web developers began to use it to create interactive applications.

&nbsp;&nbsp;&nbsp;&nbsp;Web browser developers have responded to this increased use of JS by optimizing their execution engines (dynamic compilation) and extending its usage (adding APIs), which in turn has forced web developers to use it more more. On modern websites, your browser often launches applications containing hundreds of thousands of lines of code. It is the long and gradual growth of the "Internet" from a simple web of static pages to a platform for rich applications of all kinds.

&nbsp;&nbsp;&nbsp;&nbsp;Moreover, JS has become popular enough to be used outside the context of browsers, such as implementing JS servers using node.js or deno. JS' ability to "work anywhere" makes it an attractive choice for cross-platform development. Many developers these days only use JavaScript to program their entire stack!

&nbsp;&nbsp;&nbsp;&nbsp;To sum up, we have a language that was designed to be used quickly and then grown into a full-fledged tool for writing millions of lines of applications.

&nbsp;&nbsp;&nbsp;&nbsp;TypeScript program compiles to plain JavaScript code that can run in any browser or Node.js environment. This code will be understandable by any JS engine that supports ECMAScript 3 or more

### &nbsp;&nbsp;&nbsp;&nbsp; typescript
&nbsp;&nbsp;&nbsp;&nbsp;Finding errors in code without running it is called static checking. Determining what is an error and what is not based on the types of values ​​being processed is called static type checking.

&nbsp;&nbsp;&nbsp;&nbsp;TypeScript checks a program for errors before execution and does so based on value types, it is a static type checker.

&nbsp;&nbsp;&nbsp;&nbsp;With static typing, the final types of variables and functions are set at compile time. The compiler corrects your type mismatch errors before running the program.

> JavaScript is a dynamically typed language.

&nbsp;&nbsp;&nbsp;&nbsp;In dynamic typing, all types are determined at runtime. And if you make a mistake, you will only know about it when you do it. Therefore, it is very important to pay special attention to checks and error trapping in dynamic typing.

### &nbsp;&nbsp;&nbsp;&nbsp; Syntax

&nbsp;&nbsp;&nbsp;&nbsp;TypeScript is a language that is a superset of JavaScript: so JS syntax is equal to TS. Syntax refers to how we write text to form a program.

&nbsp;&nbsp;&nbsp;&nbsp;You can take any working JavaScript code and put it in a TypeScript file without worrying about how it's written. It follows that you cannot learn TypeScript without knowing JavaScript! The TypeScript syntax and runtime behavior are the same as JavaScript, so everything you learn about JavaScript will help you learn TypeScript at the same time.

&nbsp;&nbsp;&nbsp;&nbsp;Many resources are available for programmers to learn JavaScript; you should not ignore these resources if you are writing TypeScript. For example, there are about 20 times more tagged JavaScript questions on StackOverflow than TypeScript questions, but all of these questions also apply to TypeScript.

&nbsp;&nbsp;&nbsp;&nbsp;If you find yourself looking for something along the lines of "how to sort a list in TypeScript", remember: TypeScript is a superset of JavaScript with compile-time type checking. The way to sort a list in TypeScript is the same as in JavaScript.

&nbsp;&nbsp;&nbsp;&nbsp;If you find a resource that uses TypeScript directly, that's fine too, but don't limit yourself to thinking you need TypeScript-specific answers to everyday questions about how to do tasks at runtime.

There are two popular IDEs for JavaScript and TypeScript:

> Visual Studio Code (Free)
> WebStorm (paid)

&nbsp;&nbsp;&nbsp;&nbsp;It's important to know that Visual Studio Code processes TypeScript source code in two independent ways:

&nbsp;&nbsp;&nbsp;&nbsp;Checking open files for errors: this is done through a so-called language server. Language servers exist independently of specific editors and provide Visual Studio Code with language-related services: error detection, refactoring, autocompletion, and so on. Communication withThe servers use a protocol based on JSON-RPC (RPC Remote Procedure Calls). The independence provided by this protocol means that servers can be written in almost any programming language.

&nbsp;&nbsp;&nbsp;&nbsp;An important thing to remember is that the language server only lists errors for currently open files and does not compile TypeScript, it only parses it statically.

&nbsp;&nbsp;&nbsp;&nbsp;Assembly (compiling TypeScript files into JavaScript files): We have two options here:

We can run the build tool through an external command line. For example, the TypeScript tsc compiler has a --watch mode that watches input files and compiles them into output files whenever they change. As a consequence, whenever we save a TypeScript file in the IDE, we immediately get the corresponding output file(s).

&nbsp;&nbsp;&nbsp;&nbsp;We can run tsc from Visual Studio Code. To do this, it must be installed either within the project we are currently working on, or globally (via the NPM package manager).

&nbsp;&nbsp;&nbsp;&nbsp;In order to get started with TypeScript, let's install the necessary tools. There are two ways to install TypeScript: through the NPM package manager or as a plugin for Visual Studio

### Install via NPM

&nbsp;&nbsp;&nbsp;&nbsp;In order to install via NPM, you will naturally need to install Node.js first (if you haven't already installed it). After installing Node.js, you need to run the following command from the command line (Windows) or terminal (Linux):
```npm install -g typescript```

&nbsp;&nbsp;&nbsp;&nbsp;When installing on MacOS, you also need to enter the sudo command. When entering this command, the terminal will ask for the user's login and password to install the package:
```sudo npm install -g typescript```

&nbsp;&nbsp;&nbsp;&nbsp;It is possible that TS has already been installed before. In this case, it can be updated to the latest version using the command

```npm update -g typescript```

&nbsp;&nbsp;&nbsp;&nbsp;To check the version, enter the command
```tsc -v```

###TS Compilation

&nbsp;&nbsp;&nbsp;&nbsp;Let's create an app.ts file, and it's app.ts, not app.js, that is, a typescript code file. It is also a plain text file that has a .ts extension. And define the following content:

```js
class User {
    public name: string;
    public constructor(name: string) {
    this.name = name;
    }
}
const tom: User = new User("Tom");
console.log(tom.name)
```

&nbsp;&nbsp;&nbsp;&nbsp;What's going on here? First defines the User class. This class has a name field which represents the string type, i.e. a string. To transfer data to this field, a special method is defined - constructor, which accepts a string through the name parameter and passes it to the name field:

```js
class User {
    public name: string;
    public constructor(name: string) {
    this.name = name;
    }
}
```

&nbsp;&nbsp;&nbsp;&nbsp;Next, we'll take a closer look at creating and using classes.
Create a constant tom that represents this class:

```js const tom: User = new User("Tom");```

In other words, the constant tom represents some user whose name is "Tom".
Then we output the data to the console

```js console.log(tom.name)```

Save and compile this file. To do this, on the command line/terminal, use the cd command to navigate to the directory where the app.ts file is located. And to compile, run the following command:

```js tsc app.ts```

After compilation, an app.js file is created in the project directory, which will look like this:

```js
let User = /** @class */ (function () {
function User(name) {
    this.name = name;
    }
    return User;
}());
let tom = new User("Tom");
console.log(tom.name)
```

And now we can run the file with the node app.js command and see the result of our application in the command line / terminal


### Basic data types

&nbsp;&nbsp;&nbsp;&nbsp;Typescript is a statically typed language. The type cannot be changed during program execution. This allows you to reduce the number of errors and identify many more at the compilation stage.

&nbsp;&nbsp;&nbsp;&nbsp;Typescript has several simple data types: numbers (numbers), strings (strings), Object Types (object types), boolean (boolean). It supports all types that are in Javascript, supplementing with a convenient type of enumerations (enum).

#### Boolean
The most basic type is the boolean true/false, which is called boolean in Javascript and Typescript.

```js
let isDone: boolean = false;
```

####Number

&nbsp;&nbsp;&nbsp;&nbsp;Like Javascript, Typescript's number type is a float. In addition to decimal and hexadecimal, binary and octal are supported, introduced in ECMAScript 2015.

```js
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

#### String

&nbsp;&nbsp;&nbsp;&nbsp;Another important part of programs is textual data. As in other languages, in Typescript uses the same "string" notation. Like Javascript, Typescript uses double quotes (") or single quotes (') to enclose text data.

```js
let name: string = "bob";
name='smith';
```

&nbsp;&nbsp;&nbsp;&nbsp;You can also use pattern strings, which can be multi-line and have inline expressions. These strings are surrounded by backticks or quotation marks (`) and built-in expressions are denoted as ${ expr }.

```js
let name: string = `Gene`;
let age: number = 37;
let sentence: string = `Hello, my name is ${ name }.
I'll be ${ age + 1 } years old next month.`
```

The equivalent of this sentence declaration is:

```js
let sentence: string = "Hello, my name is " + name + ".\n\n" +
"I'll be " + (age + 1) + " years old next month."
```

####null

In JavaScript, null is a primitive, and in the context of logical operations, is treated as false.

```js
getVowels(str) {
    const m = str.match(/[aeiou]/gi);
    if (m === null) {
    return 0;
    }
    return m.length;
    }
console.log(getVowels('sky'));
// expected output: 0
```

&nbsp;&nbsp;&nbsp;&nbsp;null is a special value in JavaScript that represents a missing object. The strict equality operator determines whether null is a variable: variable === null. The typeof operator is useful for determining the type of a variable (number, string, boolean). However, typeof is misleading in the case of null: typeof null evaluates to 'object'.

&nbsp;&nbsp;&nbsp;&nbsp;null and undefined are somewhat equivalent, however, null represents a missing object and undefined represents an uninitialized state.

&nbsp;&nbsp;&nbsp;&nbsp;If possible, avoid returning null or setting variables to null. This practice leads to null propagation and null checks. Instead, try using objects with default properties or throw errors.

#### undefined

&nbsp;&nbsp;&nbsp;&nbsp;A primitive value. Automatically assigned to variables that have only been declared or arguments that have not been set to a value.

```js
function test(t) {
    if (t === undefined) {
    return 'Undefined value!';
    }
    return t;
}
letx;
console.log(test(x));
// expected output: "Undefined value!"
```

#### Object

&nbsp;&nbsp;&nbsp;&nbsp;An object can be created using curly braces {…} with an optional list of properties. A property is a key:value pair, where the key is a string (also called a "property name") and the value can be anything.

&nbsp;&nbsp;&nbsp;&nbsp;When using the literal {...} syntax, we can immediately put several properties in the object in the form of key: value pairs:

```js
let user = { // object
name: "John", // the value "John" is stored under the key "name"
age: 30 // the value 30 is stored under the key "age"
};
```

### Variables

&nbsp;&nbsp;&nbsp;&nbsp;let and const are relatively new variable declaration types in JavaScript. Let is similar to var in a way, but avoids some of the common pitfalls encountered in JavaScript. Const is an extension of let that prevents variables from being redefined.

&nbsp;&nbsp;&nbsp;&nbsp;Because TypeScript is built on top of Javascript, the language also supports let and const.

###var

Variable declaration in JavaScript is always done with the var keyword.

```js var a = 10;```

&nbsp;&nbsp;&nbsp;&nbsp;As you may have guessed, we have just declared a variable named a with value 10.

We can also declare a variable inside a function:

```js
function f() {
var message = "Hello, world!";
return message;
}
```

and we also have access to these variables inside other functions:

```js
function f() {
    var a = 10;
    return function g() {
    var b = a + 1;
    return b;
    }
}
var g = f();
g(); // returns 11;
```

###Scope

&nbsp;&nbsp;&nbsp;&nbsp;The var declaration has some weird scoping rules for those using other programming languages.

```js
function f(shouldInitialize: boolean) {
    if (shouldInitialize) {
    var x = 10;
    }
return x;
}

f(true); // returns '10'
f(false); // returns 'undefined'
```

&nbsp;&nbsp;&nbsp;&nbsp;The x variable was declared inside an if block, and we can access it outside of that block. This is because var declarations are accessible within the containing function, module, namespace, or global scope, regardless of the block in which they are contained.

&nbsp;&nbsp;&nbsp;&nbsp;These scoping rules can cause several types of errors. One problem is that it is not an error to declare a variable multiple times:

```js
function sumMatrix(matrix: number[][]) {
    var sum = 0;
    for (var i = 0; i < matrix.length; i++) {
    var currentRow = matrix[i];
    for (var i = 0; i < currentRow.length; i++) {
    sum += currentRow[i];
    }
}
returnsum;
}
```

&nbsp;&nbsp;&nbsp;&nbsp;It is most likely easy to see that the internalthe for loop will accidentally overwrite i because i has scopes inside the sumMatrix function. Experienced developers know that similar errors slip through code reviews.

## let

&nbsp;&nbsp;&nbsp;&nbsp;Now we already understand that var has some problems, which is why there is a new way to declare variables let. They are written in exactly the same way as var declarations.
```js
let hello = "Hello!";
```

The key difference is not in the syntax, but in the semantics, which we are now

### Block scope

&nbsp;&nbsp;&nbsp;&nbsp;When a variable is declared using let, it is used in block scope mode. Unlike variables declared with var, whose scope extends to the entire function they are in, block-scoped variables are not visible outside of their nearest block or for loop.

```js
function f(input: boolean) {
    let a = 100;
    if (input) {
    // Here we see the variable 'a'
    let b = a + 1;
    return b;
}
// Error: 'b' does not exist in this block
return b;
}
```

&nbsp;&nbsp;&nbsp;&nbsp;Here we have two local variables a and b. The scope of a is limited by the body of the function f, while the scope of b is limited by the if condition block.

Variables declared in a catch block have the same visibility rules.
```js
try {
throw "oh no!";
}
catch (e) {
console.log("Oh well.");
}

// Error: 'e' doesn't exist here
console log(e);
```

&nbsp;&nbsp;&nbsp;&nbsp;Another property of block-scoped variables is that they cannot be accessed before they have been declared. While block-scoped variables are present everywhere in their block, there is a dead zone at every point before they are declared. It's just a way of saying that you can't access them before the let statement, and luckily TypeScript will remind you of that.
```js
a++; // incorrect to use 'a' before it is declared;
let a;
```

&nbsp;&nbsp;&nbsp;&nbsp;However, you can still capture (close) a block-scoped variable before it is declared. True, an attempt to call such a function before its declaration will result in an error. If you are compiling to ES2015 it will throw an error; however, right now TypeScript allows this and will not indicate an error.
```js
function foo() {
// okay to capture 'a'
return a;
}
// illegal call 'foo' before 'a' is declared
// runtimes should throw an error here
```

### Const
Const declarations are another way of declaring variables.
```js
const numLivesForCat = 9;
```

&nbsp;&nbsp;&nbsp;&nbsp;They are the same as let, only, as their name suggests, their value cannot be changed after they have already been assigned a value once. In other words, all the let scope rules apply to them, but you can't override them. The value they are associated with is immutable

```js
const numLivesForCat = 9;
const kitty = {
name: "Aurora",
numLives: numLivesForCat,
}
// Error
kitty = {
name: "Danielle",
numLives: numLivesForCat
};
// Everything is fine
kitty.name = "Rory";
kitty.name = "kitty";
kitty.name = "cat";
kitty.numLives--;
```

&nbsp;&nbsp;&nbsp;&nbsp;Even though a variable has been declared const, its internal state can still be changed. Luckily, TypeScript allows you to define object properties as readonly.

### let or const?

&nbsp;&nbsp;&nbsp;&nbsp;We have two ways of declaring their scope with similar rules, so it begs the question which one to use. The answer will be the same as for most broad questions: it depends.

&nbsp;&nbsp;&nbsp;&nbsp;Using the principle of least privilege, all variable declarations that you don't plan to change should use const. The reason for this is that if a variable should not change its value, other developers who are working on the same code should not be able to write to the object. This should only be allowed if there is a real need to reassign a variable. The use of const makes the code more predictable and understandable when explaining data flow.

> Using var is considered an antipattern.

&nbsp;&nbsp;&nbsp;&nbsp;An anti-pattern is a common approach to solving a class of common problems that is inefficient, risky, or counterproductive.

###Operators

&nbsp;&nbsp;&nbsp;&nbsp;JavaScript has the following types of operators. This subsection describes each type and contains information about their precedence over each other.
- • Assignment operators
• Comparison operators
• Arithmetic operators
• Bitwise (Bitwise) Operators
• Logical operators
• String Operators
• Conditional (ternary) operator
• The comma operator
• Unary operators
• Relational operators
• Operator precedence

&nbsp;&nbsp;&nbsp;&nbsp;The comparison operator compares its operands and returns a Boolean value based on the truth of the comparison. Operands can be numbers, stringmi, logical values ​​or objects. Strings are compared based on standard lexicographical order using Unicode values. In most cases, if the operands are of different types, then JavaScript tries to convert them to a type suitable for comparison. This behavior usually occurs when comparing numeric operands. The only exception to this rule is comparison using the === and !== operators, which perform a strict equality or inequality comparison. These operators do not attempt to convert the operands before comparing them.

### Logic operators

&nbsp;&nbsp;&nbsp;&nbsp;Logical operators are typically used with boolean (logical) values; however, their return value is also boolean. However, the && and || actually return the value of one of the operands, so if these operators are used with non-boolean values, then the value they return may also be non-boolean. The logical operators are described in the following table.

- Logical AND &&
expr1 && expr2

(Logical AND) Returns expr1 if it can be converted to false; otherwise returns the expr2 operand. Thus, when using boolean values ​​as operands, the && operator returns true if both operands are true; otherwise returns false.

- Logical OR ||
expr1 || expr2

(Logical OR) Returns expr1 if it can be converted to true; otherwise returns the expr2 operand. Thus, when using boolean values ​​as operands, the operator || returns true if one of the operands is true; if both are false, then it returns false.

- Logical NOT !
!expr

&nbsp;&nbsp;&nbsp;&nbsp;(Logical NOT) Returns false if the operand can be converted to true; otherwise returns true.

&nbsp;&nbsp;&nbsp;&nbsp;Examples of expressions that can be converted to false are null, 0, NaN, the empty string (""), or undefined.

Examples of using the && (logical AND) operator.

1. let a1 = true && true; // t && t returns true
2. let a2 = true && false; // t && f returns false
3. let a3 = false && true; // f && t returns false
4. let a4 = false && (3 == 4); // f && f returns false
5. let a5 = "Cat" && "Dog"; // t && t returns Dog
6. let a6 = false && "Cat"; // f && t returns false
7. let a7 = "Cat" && false; // t && f returns false

Examples of using the operator || (logical OR).

1. let o1 = true || true; // t || t returns true
2. let o2 = false || true; // f || t returns true
3. let o3 = true || false; // t || f returns true
4. let o4 = false || (3 == 4); // f || f returns false
5. let o5 = "Cat" || "dog"; // t || t returns Cat
6. let o6 = false || "Cat"; // f || t returns Cat
7. let o7 = "Cat" || false; // t || f returns Cat

Examples of using the ! (logical NOT).

1.let n1 = !true; // !t returns false
2.let n2 = !false; // !f returns true
3.let n3 = "Cat"; // !t returns false

### Terms

>if...else

&nbsp;&nbsp;&nbsp;&nbsp;The if statement executes the statement if the specified condition is true (true). If the condition is not met (false), then another instruction can be executed.
```
>if (condition)
>instruction1
>[else
>instruction2]
```

### if...else

```js
1. if (cipher_char === from_char) {
2. result = result + to_char;
3.x++;
4. } else {
5. result = result + clear_char;
6.}
```

### else if

Note that there is no elseif syntax in JavaScript. However, you can write it with a space between else and if:

```js
1. if (x > 5) {
2. } else if (x > 50) {
3. } else {
four. }
```

### Loops and iterations

&nbsp;&nbsp;&nbsp;&nbsp;You can think of a cycle as a computerized version of a game where you tell someone to take X steps in one direction, then Y steps in the other; for example, the idea of ​​the game "Go 5 steps east" can be expressed as a loop:

```js
1. for (let step = 0; step < 5; step++) {
2. // Runs 5 times, in increments of 0 to 4.
3. console.log('Let's go 1 step east');
four. }
```

&nbsp;&nbsp;&nbsp;&nbsp;There are many different kinds of loops, but they all essentially do the same thing: repeat some action several times (don't forget about the zero repetition time, counting in the array starts from 0). Loops of different structure offer different ways to determine the start and end of a loop. For various programming tasks, there are their own loop operators, with the help of which they are solved much easier.

- Operators designed to organize loops in JavaScript:
• for_loop
• Loop_do...while
• while_loop
• Label_(label)
• break
• continue
• for...in
• for...of

&nbsp;&nbsp;&nbsp;&nbsp;The for loop repeats until some special end-of-loop event occurs. The for statement in JavaScript is similar to the for statement in Java and C. The declaration of the for statement looks like this:

``` for ([start]; [condition];[step]) expressions ```

When it is executed, the following happens:

1. The start expression is executed if it is specified. This expression usually initializes one or more counters, but the syntax allows the expression to be of any complexity. Also used to declare variables.
2. The condition is met. If the condition is true, then the expressions are executed. If it is false, the for loop is terminated. If the condition is completely omitted, then it is considered true.
3. Expressions are executed. To execute multiple expressions, the block expression { ... } is used to group the expressions.
4. The step is updated if it exists, and then control returns to step 2.
The while loop executes expressions while the condition is true. It looks like this:
1. while (i < 3) { // Execute code while variable i is less than 3
2. alert("i: " + i);
3.i++; // Increment the value of the variable i
four. }

&nbsp;&nbsp;&nbsp;&nbsp;If the condition becomes false, the expressions in the loop stop executing and control passes to the expression after the loop.

&nbsp;&nbsp;&nbsp;&nbsp;The condition is checked for truth before the expressions in the loop are executed. If the condition is true, the expressions are executed and then the condition is tested again.

&nbsp;&nbsp;&nbsp;&nbsp;If the condition is false, execution is suspended and control passes to the expression after the while.

&nbsp;&nbsp;&nbsp;&nbsp;To use multiple expressions, use the { ... } expression block to group them.

### Continue

&nbsp;&nbsp;&nbsp;&nbsp;The continue statement is used to step one step forward in while, do-while, for loops, or jump to a label.

- • When you use continue without a label, it breaks the current iteration of the while, do-while, and for loops and continues the loop at the next iteration. Unlike break, continue does not completely break the loop. In the while loop, it jumps to the condition. And in for increases the step.
• When you use continue with a label, it applies to the loop with that label.

The continue syntax might look like this:
```js
1. continue;
2. continue Label;
1. for (let i = 0; i <= 10; i++) {
2. if ((i % 2) != 0) continue; // If the value of the variable is not even,
3. // end the current iteration
4. alert(i);
5. }
```
###break

Use the break statement to break a loop or toggle control.
- • When you use break, it breaks the while, do-while, and for loops or immediately switches control to the next statement.
-
The operator syntax might be:
```js
1. for (var i = -2; i <= 2; i++) {
2. if (i > 0) break; // If the value of the variable i becomes positive,
3. // end the iteration and exit the loop }
```

&nbsp;&nbsp;&nbsp;&nbsp;The first form of syntax breaks the loop altogether or switches control; the second breaks the specially marked expression.


### Iterables

&nbsp;&nbsp;&nbsp;&nbsp;An iterable is an object that contains an implementation of the Symbol.iterator property. Some built-in types such as Array, Map, Set, String, Int32Array, Uint32Array, etc. have the Symbol.iterator property already implemented. The Symbol.iterator function taken from the object must return a list of values ​​for looping.

### for..of

&nbsp;&nbsp;&nbsp;&nbsp;To iterate over an iterable object in a for..of loop, the Symbol.iterator property is called on it. Here is a simple for..of loop through an array:

```js
let someArray = [1, "string", false];
for (let entry of someArray) {
console log(entry); // 1, "string", false
}
for..of vs. for..in
```

&nbsp;&nbsp;&nbsp;&nbsp;Both for..of and for..in are used to iterate over lists. At the same time, the values ​​by which the bypass is performed differ. for..in returns a list of the iterable's keys, while for..of returns a list of its numeric property values.

The following example demonstrates the difference:
```js
let list = [4, 5, 6];
for (let i in list) {
console log(i); // "0", "1", "2",
}
for (let i of list) {
console log(i); // "4", "5", "6"
}
```

&nbsp;&nbsp;&nbsp;&nbsp;Another difference is that for..in can be used to iterate over any object, being a means of inspecting its properties. And for..of is primarily designed to get values. Built-in objects such as Map and Set implement the Symbol.iterator property to provide access to stored values.

```js
let pets = new Set(["Cat", "Dog", "Hamster"]);
pets["species"] = "mammals";
for (let pet in pets) {
console log(pet); // "species"
}
for (let pet of pets) {
console log(pet); // "Cat", "Dog", "Hamster"
}
```

### Arrays

&nbsp;&nbsp;&nbsp;&nbsp;Arrays are list-like objects whose prototypes contain methods for array traversal and modification operations. Neither the size of a JavaScript array nor the types of its elements are fixed. Since the size of an array can grow and shrink at any time, there is no guarantee that the array will be dense. That is, when working with an array,there will be a situation that the element of the array to which you refer will be empty and will return undefined. Overall, this is a handy feature; but if this feature of an array is not desired in your particular case, you may want to consider using typed arrays.

Creating an array
```js
1. let fruits = ['Apple', 'Banana'];
2. console.log(fruits.length);
3. // 2
```
Adding an element to the beginning of an array
```js
1. let newLength = fruits. unshift('Strawberry') // adds to the beginning
2. // ["Strawberry", "'Apple', 'Banana']];
```
Adding an element to the end of an array
```js
var sports = ['football', 'baseball'];
var total = sports.push('football', 'swim');
console log(sports); // ['football', 'baseball', 'football', 'swimming']
```
Removing an element at a specific index
```js
let removedItem = fruits.splice(pos, 1); // this way you can remove the element
// ["Strawberry", "'Banana'"]
```
### length

&nbsp;&nbsp;&nbsp;&nbsp;The length property is a positive integer with a value less than 2 to the power of 32 (232). length properties when called. Other methods (for example, push, splice, etc.) also update the length property of the array as a result of their work.

```js
1. let fruits = [];
2. fruits.push('banana', 'apple', 'peach');
3.
4. console.log(fruits.length); // 3
```

&nbsp;&nbsp;&nbsp;&nbsp;If the index is outside the current bounds of the array, the length property is updated accordingly.

### Functions

&nbsp;&nbsp;&nbsp;&nbsp;Functions are the fundamental building blocks of every JavaScript application. With their help, abstraction layers, data hiding and modules are built. Although TypeScript has classes, namespaces, and modules, functions still play a key role in describing how things work.

&nbsp;&nbsp;&nbsp;&nbsp;In addition, TypeScript adds several new features to standard JavaScript functions and makes them easier to work with.

&nbsp;&nbsp;&nbsp;&nbsp;Just like in JavaScript, TypeScript functions can be created both named and anonymous. This allows you to choose the approach that best suits a particular application: whether you create a group of functions for an API, or a function that is needed only to be an argument to another function.

How these two options look in JavaScript:

```js
// Named function
function add(x, y) {
return x + y;
}
// Anonymous function
let myAdd = function(x, y) { return x+y; };
```

&nbsp;&nbsp;&nbsp;&nbsp;Like JavaScript, functions can access variables outside of their body. When this happens, the function is said to "capture" variables.

```js
let z = 100;

function addToZ(x, y) {
return x + y + z;
}
```

### Declaring and calling a function

&nbsp;&nbsp;&nbsp;&nbsp;There are three ways to declare a function: Function Declaration, Function Expression, and Named Function Expression.

&nbsp;&nbsp;&nbsp;&nbsp;Function Declaration (FD for short) is a "classic" function declaration. In JavaScript, functions are declared with a function literal. FD declaration syntax:

``` function identifier (parameters) { instructions }```

A function literal consists of the following four parts:

1. The function keyword.
2. Mandatory identifier that defines the name of the function. A verb is usually chosen as the name of a function, because the function performs an action.
3. A pair of parentheses around a list of zero or more identifiers separated by commas. These identifiers are called function parameters.
4. The body of the function, consisting of a pair of curly braces, inside which are instructions. The function body can be empty, but curly braces must always be specified.

Simple example:
```js
function sayHi() {
    alert("Hello");
}
```
&nbsp;&nbsp;&nbsp;&nbsp;When the interpreter encounters the function keyword, it creates a function and then assigns a reference to it to a variable named sayHi (a variable with this name is automatically created by the interpreter).

Turning to the sayHi variable, you can see that there is a function as a value (in fact, a link to it):

```js
alert(sayHi); // function sayHi() { alert("Hello"); }
```

&nbsp;&nbsp;&nbsp;&nbsp;Function Expression (abbreviated as FE) is a function declaration that is part of an expression (such as an assignment).

FE declaration syntax
```js
function (parameters) { instructions }
```
Simple example:
```js
let sayHi = function () {
    alert("Hello");
};
```

&nbsp;&nbsp;&nbsp;&nbsp;The FE function is otherwise known as an "anonymous function".

&nbsp;&nbsp;&nbsp;&nbsp;Named Function Expression (NFE for short) is a function declaration that is part of an expression (such as an assignment). NFE declaration syntax:

```js
function identifier (parameters) { instructions }
```
Simple example:
``` js
let sayHi = function foo() {
alert("Hello");
};
```

&nbsp;&nbsp;&nbsp;&nbsp;bsp; FE and NFE declarations are treated by the interpreter in the same way as FD declarations: the interpreter creates a function and stores a reference to it in the sayHi variable.

&nbsp;&nbsp;&nbsp;&nbsp;Program code located in the body of a function is executed not at the moment of the function declaration, but at the moment of its call. To call a function, use the operator () (function call):

```js
function sayHi() {
alert("Hello");
}
let sayHi2 = function() {
alert("Hello2");
};
let sayHi3 = function foo() {
alert("Hello3");
};
sayHi(); // "hello"
sayHi2(); // "Hello2"
sayHi3(); // "Hello3"
```

&nbsp;&nbsp;&nbsp;&nbsp;The difference between these three declarations is that functions declared as FDs are created by the interpreter before the code is executed (at the parsing stage), so they can be called (in the scope where they are declared) before ads:

```js
// Call the function before it is declared in the top-level code
foo();

function foo() {
    alert("Calling the foo() function in the global scope.");

// Call the function before it is declared in the function scope
bar();
function bar() {
    alert("Calling bar() function in function scope.");
    }
}
```

&nbsp;&nbsp;&nbsp;&nbsp;Functions declared as FE or NFE are created at runtime, so they can only be called after they are declared:

```js
// sayHi(); // Error. The sayHi function doesn't exist yet
let sayHi = function () {
alert("Hello!");
};
sayHi();
```

Functions declared inside a block are in the block scope:

```js
// foo(); // Error. The function is not declared.
{
foo(); // one

function foo() {
    console log(1);
    }
}
foo(); // Error. The function is not declared.
```

&nbsp;&nbsp;&nbsp;&nbsp;Unlike FE, a function declared as NFE has the ability to refer to itself by name when called recursively. The function name is only available within the function itself:

```js
(function sayHi(str) {
    if (str) { return; }
    say Hi("hi"); // The name is available inside the function
    })();

sayHi(); // Error. Function not declared
```

### Callback

&nbsp;&nbsp;&nbsp;&nbsp;A callback function is a function that is passed as an argument to another function to be called later.

Callback functions are often used as event handlers.

&nbsp;&nbsp;&nbsp;&nbsp;The following is an example of a function that takes as its argument a reference to another function for its subsequent call:

```js
function foo(callback) { return callback(); }

foo (function() { alert("Hello!"); });
```
&nbsp;&nbsp;&nbsp;&nbsp;This example demonstrates how a callback works.

&nbsp;&nbsp;&nbsp;&nbsp;Using the return statement, a function can return some value (the result of the function's operation) to the program that called it. The return value is passed to the point where the function is called.


The return statement has the following syntax:
```
return expression;
```

&nbsp;&nbsp;&nbsp;&nbsp;It is not the expression itself that is returned to the program, but the result of its evaluation. For further use of the returned value, the result of the function execution can be assigned to a variable, for example:

```js
function calc(a) {
    return a * a;
    }

letx = calc(5);
alert(x); // 25
```

&nbsp;&nbsp;&nbsp;&nbsp;The return statement can be placed anywhere in a function. As soon as the return statement is reached, the function returns a value and immediately terminates its execution. Code after the return statement will be ignored:

```js
function foo() {
    return 1;
    alert('Won't run');
    }

letx = foo();
alert(x); // one
```
You can use multiple return statements inside a function:

```js
function check(a, b) {
if(a > b) return a;
else return b;
}

alert(check(3, 5)); // 5
```

&nbsp;&nbsp;&nbsp;&nbsp;If no return statement is specified or no return value is specified, the function will return undefined:

```js
function bar() {}
function foo() { return; }

alert(bar()); // undefined. return statement not specified
alert(foo()); // undefined. Return value not specified
```

### Adding Types to a Function

Let's add types to the function from the previous simple examples:
```js
function add(x: number, y: number): number {
    return x + y;
    }
let myAdd = function(x: number, y: number): number { return x+y; };
```

&nbsp;&nbsp;&nbsp;&nbsp;You can add types to each parameter, as well as to the function itself, to specify the return type. TypeScript knows how to infer the type of the return value by parsing return statements, so you can often leave it out.

Writing a function type

Now that we have added types to the function, we can describe its full type by collecting it piece by piece from the definition:

```js
let myAdd: (x: number, y: number)=>number =
function(x: number, y: number): number { return x+y; };
```

&nbsp;&nbsp;&nbsp;&nbsp;A function type consists of the same two parts: the type of the arguments and the type of the return value. When the full type of fun is writtenaction, it is necessary to indicate both of these parts. Parameter types are written in the same way as a parameter list, and each parameter is given a name and a type. The names here are only for readability, you could write, for example, like this:

```js
let myAdd: (baseValue:number, increment:number) => number =
function(x: number, y: number): number { return x + y; };
```

&nbsp;&nbsp;&nbsp;&nbsp;If the parameter types match, then the type is considered appropriate for the function, no matter what names were given to the parameters in the function's type declaration.

&nbsp;&nbsp;&nbsp;&nbsp;The second part of the function type is the return type. It is indicated by a thick arrow (=>) between the parameters and the return type. As mentioned above, this part is required, and therefore, if the function does not return anything, you must specify void as the return type.

### Type reference

&nbsp;&nbsp;&nbsp;&nbsp;Experimenting with the following example, you can see that the TypeScript compiler is able to figure out types if they are only in one half of the expression:

```js
// myAdd has a full function type
let myAdd = function(x: number, y: number): number { return x + y; };

// Parameters 'x' and 'y' have type "number"
let myAdd: (baseValue:number, increment:number) => number =
function(x, y) { return x + y; };
```

&nbsp;&nbsp;&nbsp;&nbsp;This is called contextual typing, a form of type inference. This feature allows you to spend less effort on adding types to the program.

### Optional parameters

&nbsp;&nbsp;&nbsp;&nbsp;TypeScript assumes that every function parameter is required. This does not mean that null or undefined cannot be passed to it: it means that when the function is called, the compiler will check to see if the user has set a value for each of its parameters. In addition, the compiler assumes that no parameters other than those specified will be passed. Simply put, the number of parameters passed must match the number of parameters the function expects.

```js
function buildName(firstName: string, lastName: string) {
return firstName + " " + lastName;
}

let result1 = buildName("Bob"); // error, too few parameters
let result2 = buildName("Bob", "Adams", "Sr."); // error, too many parameters
let result3 = buildName("Bob", "Adams"); // just right
```

&nbsp;&nbsp;&nbsp;&nbsp;In JavaScript, all parameters are optional and users can omit them if desired. In such cases, the value of the missing parameters is taken as undefined. TypeScript can also achieve this by adding a ? to the end of the parameter you want to make optional. For example, we want to make lastName optional from the previous example:

```js
function buildName(firstName: string, lastName?: string) {
if (lastname)
return firstName + " " + lastName;
else
return firstName;
}
let result1 = buildName("Bob"); // everything is correct now
let result2 = buildName("Bob", "Adams", "Sr."); // error, too many parameters
let result3 = buildName("Bob", "Adams"); // just right
```

&nbsp;&nbsp;&nbsp;&nbsp;All optional parameters must come after the required ones. If the first parameter (firstName) were to be made optional instead of lastName, then the order of the parameters in the function would have to be changed to make firstName last.

&nbsp;&nbsp;&nbsp;&nbsp;TypeScript also allows you to specify a value for a parameter that it will take if the user omits it or passes undefined. Such parameters are called default parameters or simply default parameters. Let's take the previous example and set lastName to its default value of "Smith".

```js
function buildName(firstName: string, lastName = "Smith") {
return firstName + " " + lastName;
}

let result1 = buildName("Bob"); // so far so good, returns "Bob Smith"
let result2 = buildName("Bob", undefined); // also works and returns "Bob Smith"
let result3 = buildName("Bob", "Adams", "Sr."); // error, too many parameters
let result4 = buildName("Bob", "Adams"); // just right
```

&nbsp;&nbsp;&nbsp;&nbsp;Default parameters that come after all required parameters are considered optional. Just like optional ones, they can be skipped when calling a function. This means that the optional and default parameter types that are at the end will be compatible, so this function:

```js
function buildName(firstName: string, lastName?: string) {
// ...
}
and this

function buildName(firstName: string, lastName = "Smith") {
// ...
}
```

will have the same type (firstName: string, lastName?: string) => string.

&nbsp;&nbsp;&nbsp;&nbsp;The default value for the lastName parameter in the function type declaration disappears, leaving only the fact that the last parameter is optional.

&nbsp;&nbsp;&nbsp;&nbsp;Unlike simple optional parameters, default parameters do not have to appear after the requiredspruce parameters. If a default parameter is followed by a required parameter, then you must explicitly pass undefined to set the default value. For example, the last example could be rewritten using only the default parameter for firstName:

```js
function buildName(firstName = "Will", lastName: string) {
return firstName + " " + lastName;
}

let result1 = buildName("Bob"); // error, too few parameters
let result2 = buildName("Bob", "Adams", "Sr."); // error, too many parameters
let result3 = buildName("Bob", "Adams"); // matches, returns "Bob Adams"
let result4 = buildName(undefined, "Adams"); // matches, returns "Will Adams"
```

### Rest parameters

&nbsp;&nbsp;&nbsp;&nbsp;Required, optional, and default parameters have one thing in common - they describe one parameter at a time. In some cases, you need to work with several parameters, considering them as a group; and sometimes it is not known in advance how many parameters the function will take. In JavaScript, arguments can be manipulated directly using the arguments variable, which is available inside any function.


In TypeScript, you can collect arguments into a single variable:

```js
function buildName(firstName: string, ...restNames: string[]) {
return firstName + " " + restNames.join(" ");
}

let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```

&nbsp;&nbsp;&nbsp;&nbsp;Rest parameters can be understood as an unlimited number of optional parameters. When passing arguments for residual parameters, you can pass as many as you like; and you can do nothing at all. The compiler builds an array from the arguments passed in, gives it the name that comes after the ellipsis (...), and makes it available inside the function.


The ellipsis is also used when describing the type of a function with residual parameters:
```js
function buildName(firstName: string, ...restOfName: string[]) {
return firstName + " " + restOfName.join(" ");
}

let buildNameFun: (fname: string, ...rest: string[]) => string = buildName;
```

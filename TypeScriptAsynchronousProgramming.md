### Asynchronous programming

&nbsp;&nbsp;&nbsp;&nbsp;Traditionally, programming uses synchronous programming - sequential execution of instructions with synchronous system calls that completely block the execution thread until a system operation, such as reading from disk, has completed.

&nbsp;&nbsp;&nbsp;&nbsp;Asynchrony in programming is the execution of a process in a non-blocking system call mode, which allows the program flow to continue processing. There are several ways to implement asynchronous programming, which you will learn about below.

&nbsp;&nbsp;&nbsp;&nbsp;The async statement defines an asynchronous function in which one or more asynchronous tasks are expected to execute:

```js
async function function_name(){
// asynchronous operations
}
```

&nbsp;&nbsp;&nbsp;&nbsp;Within an asynchronous function, we can use the await operator. It is placed before the invocation of an asynchronous operation that represents a Promise object:

```js
async function function_name(){

await async();
}
```

&nbsp;&nbsp;&nbsp;&nbsp;The await statement suspends the execution of an asynchronous function until the Promise object has returned a result. It is worth considering that the await operator can only be used inside the function to which the async operator is applied.

&nbsp;&nbsp;&nbsp;&nbsp;First, let's look at the simplest example using Promise:

```js
function sum(x, y){
    return new Promise(function(resolve){
    const result = x + y;
    resolve(result);
    });
}
sum(5, 3).then(function(value){
console.log("Result of asynchronous operation:", value);
}); // Result of asynchronous operation: 8
```

&nbsp;&nbsp;&nbsp;&nbsp;In this case, the sum() function represents an asynchronous task. It takes two numbers and returns a Promise object that adds the numbers. The result of the addition is passed to the resolve() function. And then in the then() method, we can get this result and perform various actions with it.

&nbsp;&nbsp;&nbsp;&nbsp;Now rewrite this example using async/await:

```js
function sum(x, y){
    return new Promise(function(resolve){
    const result = x + y;
    resolve(result);
    });
}

async function calculate(){
const value = await sum(5, 3);
console.log("Result of asynchronous operation:", value);
}
calculate(); // Result of asynchronous operation: 8
```

Here we have defined an asynchronous calculate() function to which async is applied:
```js
async function calculate(){
```

&nbsp;&nbsp;&nbsp;&nbsp;Inside the function, an asynchronous sum() operation is called, which is passed some values. Moreover, the await operator is applied to this function. Thanks to the await operator, there is no longer a need to call the then() method on the mix. And we can get the result that Promise returns directly from the call to the sum function and, for example, assign it to a constant or variable:

```js
const value = await sum(5, 3);
```

Then we can call the calculate() function like a regular function and thus perform all its actions.

```js
calculate();
```

&nbsp;&nbsp;&nbsp;&nbsp;Async and await allow you to write asynchronous code that looks and acts like synchronous code. Such code becomes much easier to read, write, and judge.

- Await only works inside an async function
• A function marked with the async keyword always returns a Promise
• If the return value inside async does not return a Promise, then it will be wrapped in an immediately resolved Promise
• As soon as the await keyword is encountered, execution is suspended until the Promise is completed.
• Await will either return the result from a fulfilled Promise or throw an exception from a rejected Promise

#### Sequence of asynchronous operations

&nbsp;&nbsp;&nbsp;&nbsp;An asynchronous function can contain many asynchronous operations that are awaited. In this case, all asynchronous operations will be executed sequentially:

```js
1. function sum(x, y){
2. return new Promise(function(resolve){
3. const result = x + y;
4. resolve(result);
5.     });
6.}
7.
8. async function calculate(){
9. const value1 = await sum(5, 3);
10. console.log("Result of 1 asynchronous operation:", value1);
11. const value2 = await sum(6, 4);
12. console.log("Result 2 of asynchronous operation:", value2);
13. const value3 = await sum(7, 5);
14. console.log("Result 3 of asynchronous operation:", value3);
fifteen. }
16.calculate();
17. // Result of 1 asynchronous operation: 8
18. // Result of 2 asynchronous operation: 10
19. // Result 3 of asynchronous operation: 12
```

### Promises

&nbsp;&nbsp;&nbsp;&nbsp;In essence, async/await is syntactic sugar for promises, that is, the async/await keyword wraps promises. The async function always returns a promise. Even if you omit the Promise keyword, the compiler will wrap your function in an immediately resolving promise.

```js
1. const myAsynFunction = async(url: string): Promise<T> => {2. const { data } = await fetch(url)
3. return data
four. }
5.
6. const immediatelyResolvedPromise = (url: string) => {
7. const resultPromise = new Promise((resolve, reject) => {
8. resolve(fetch(url))
9.     })
10. return resultPromise
eleven. }
```

### What is a promise in TypeScript?

&nbsp;&nbsp;&nbsp;&nbsp;Translated from English, "promise" means "promise". In JavaScript, a promise describes the expectation that some event will happen at a certain moment, and your application relies on the outcome of that future event to perform certain other tasks.

### Sequential execution with .then

&nbsp;&nbsp;&nbsp;&nbsp;When programming a client interface, there is a typical task: to execute requests over the network and respond appropriately to their results.

Below is a request to select a list of employees from a remote server.
```js
1. const api = 'http://dummy.restapiexample.com/api/v1/employees'
2.fetch(api)
3. .then(response => response.json())
4. .then(employees => employees.forEach(employee => console.log(employee.id)) // logs the id of all employees
5. .catch(error => console.log(error.message))) // logs any error coming from the promise.
```

### Error handling in try/catch

&nbsp;&nbsp;&nbsp;&nbsp;Let's go back to the example of selecting employee records to show error handling in action, since it's the network query that is likely to cause the error.

&nbsp;&nbsp;&nbsp;&nbsp;Suppose, for example, that we have a server down, or that we sent a request in the wrong format. We have to pause the execution to prevent the program from crashing.

The syntax will look like this:
```js
1.interface Employee {
2. id: number
3.employee_name:string
4.employee_salary: number
5.employee_age:number
6.profile_image:string
7.}
8. const fetchEmployees = async(): Promise<Array<Employee> | string> => {
9. const api = 'http://dummy.restapiexample.com/api/v1/employees'
10. try {
11. const response = await fetch(api)
12. const { data } = await response.json()
13. return data
14. } catch (error) {
15. if (error) {
16. return error.message
17.}
eighteen.     }
19. }
```

&nbsp;&nbsp;&nbsp;&nbsp;We have initiated the async function. As a return value, we expect an array of typeof type with information about employees, or a string with error messages. Accordingly, the Promise type is formulated as Promise<Array<Employee> | string>.

&nbsp;&nbsp;&nbsp;&nbsp;The try block contains expressions that the function must execute if there are no errors. The catch block catches any error that occurs. In this case, we simply return the message property of the error object.

&nbsp;&nbsp;&nbsp;&nbsp;The beauty of what is happening is that any error that occurs in the try block is immediately thrown and caught by the catch block. If an exception escapes, it may result in code that is difficult to debug, or even the entire program may be corrupted.

### throw

&nbsp;&nbsp;&nbsp;&nbsp;The throw statement allows you to throw user-defined exceptions. In this case, the execution of the current function will be stopped (the instructions after the throw will not be executed), and control will be transferred to the first catch block in the call stack. If there are no catch blocks among the called functions, the execution of the program will be stopped.
Use the throw statement to throw an exception. When you throw an exception (throw), the expression specifies the value of the exception.

Each of the following throws throws an exception:
```js
1.throw "Error2"; // throws an exception whose value is a string
2.throw 42; // throws an exception whose value is the number 42
3.throw true; // throws an exception whose value is the boolean true
```

### Example: Throwing an Object as an Exception

&nbsp;&nbsp;&nbsp;&nbsp;You can specify an object as an exception. You can then get a reference to that object and access all of its properties in a catch block. The following example creates an error object that is of type UserException and is used to throw an exception.

```js
1. function UserException(message) {
2. this.message = message;
3. this.name = "User Defined Exception";
four. }
5. function getMonthName(mo) {
6. mo = mo-1; // You need to adjust the month number according to the array indices (1=Jan, 12=Dec)
7. const months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul",
8. "Aug", "Sep", "Oct", "Nov", "Dec"];
9. if (months[mo] !== undefined) {
10. return months[mo];
11. } else {
12. throw new UserException("Invalid month number");
13.    }
fourteen. }
15. try {
16. // statements to try
17. let myMonth = 15; // 15 is outside the bounds of the array, which will result in an exception
18. let monthName = getMonthName(myMonth);
19. } catch (e) {
20. monthName = "unknown";
21.logMyErrors(e.message, e.name); // passexception in error handler
22.}
```

### Decorators for functions

The definition in Typescript itself looks like this:
```JS
1. declare type MethodDecorator =
2.<T>(
3.target: Object
4. propertyKey: string | symbol,
5. descriptor: TypedPropertyDescriptor<T>)
6. => TypedPropertyDescriptor<T> | void;
```

This is a function that takes multiple arguments.
- the object on which this function was called
• function name
• function descriptor

The descriptor looks like this:
```JS
1.interface TypedPropertyDescriptor<T> {
2. enumerable?: boolean;
3. configurable?: boolean;
4. writable?: boolean;
5. value?: T;
6. get?: () => T;
7. set?: (value: T) => void;
eight. }
```

&nbsp;&nbsp;&nbsp;&nbsp;The handle is needed to access the original function and be able to call it from the decorator code. To see an example, we need some clear and useful script. We use - measure the performance of a function.

```js
1. class TestServiceDeco {
2.
3. @LogTime()
4.testLogging() {
5.         ...
6.}
7.}
```

&nbsp;&nbsp;&nbsp;&nbsp;A decorator for a function, property, or function parameter can only be applied within a class. Currently, the Typescript compiler will not allow a decorator to be applied to a function that is written outside of a class.

&nbsp;&nbsp;&nbsp;&nbsp;For our scenario, the decorator code might look like this:
```js
1. function LogTime() {
2. return (target: Object, propertyName: string, descriptor: TypedPropertyDescriptor<Function>) => {
3. const method = descriptor.value;
4. descriptor.value = function(...args) {
5. console.time(propertyName || 'LogTime');
6. const result = method.apply(this, args);
7. console.timeEnd(propertyName || 'LogTime');
8. return result;
9.         };
ten.     };
eleven. }
```
&nbsp;&nbsp;&nbsp;&nbsp;A decorator is a function that returns a function of a particular type. In the example, the arguments of this function are visible - target, propertyName and function descriptor. The compiler will substitute them into the calling code.

&nbsp;&nbsp;&nbsp;&nbsp;The function descriptor here allows you to override the behavior - replace the desired function with a new one that already follows the logic specified by the decorator. Our logic implies the ability to detect the moment the function starts and ends, and print the difference to the console.

&nbsp;&nbsp;&nbsp;&nbsp;The compiled Javascript code will look like this
```js
1. "use strict";
2. Object.defineProperty(exports, "__esModule", { value: true });
3. function LogTime() {
4. return (target, propertyName, descriptor) => {
5. const method = descriptor.value;
6. descriptor.value = function(...args) {
7. console.time(propertyName || 'LogTime');
8. const result = method.apply(this, args);
9. console.timeEnd(propertyName || 'LogTime');
10. return result;
eleven.         };
12.     };
13. }
14. exports.LogTime = LogTime;
```

No surprises, everything is about the same as in Typescript code. And the calling code is a little more interesting:

```js
1. Object.defineProperty(exports, "__esModule", { value: true });
2. const log_time_decorator_1 = require("../src/samples/log-time.decorator");
3. class TestServiceDeco {
4.testLogging() {
5. ...    }
6.}
7. __decorate([
8.log_time_decorator_1.LogTime(),
9. __metadata("design:type", Function),
10. __metadata("design:paramtypes", []),
11. __metadata("design:returntype", void 0)
12. ], TestServiceDeco.prototype, "testLogging", null);
```

&nbsp;&nbsp;&nbsp;&nbsp;Here you can see the __decorate system function, which is passed our decorator along with additional arguments.

&nbsp;&nbsp;&nbsp;&nbsp;Compiler-supplied code that calls the __decorate function will be executed during code interpretation, immediately after the class has been interpreted. But our decorator code itself will be called every time the original function is called. This is a key difference from the next kind of decorator.

### Decorators for classes

&nbsp;&nbsp;&nbsp;&nbsp;A class decorator is applied to a class constructor and allows you to modify or replace the class definition.

A class decorator represents a function that takes one parameter:

```js
function classDecoratorFn(constructor: Function){ }
```

The class constructor is used as a parameter. For example, let's define a simple decorator:

```js
1. function sealed(constructor: Function) {
2. console.log("sealed decorator");
3. Object.seal(constructor);
4. Object.seal(constructor.prototype);
5. }
6.
7. @sealed
8. class User {
9 name: string;
10. constructor(name: string){
11. this.name = name;
12.     }
13.print():void{
14. console.log(this.name);
fifteen.     }
16. }
```

&nbsp;&nbsp;&nbsp;&nbsp;The sealed decorator, using the Object.seal function, prevents the User class prototype from being extended.

&nbsp;&nbsp;&nbsp;&nbsp;To apply the decorator, usethe @ sign is used. The decorator itself is placed before the class name. That is, due to the use of a decorator, for example, we will not be able to add a new property to the User class as follows:

```js
Object.defineProperty(User, 'age', {
value: 17
});
```

&nbsp;&nbsp;&nbsp;&nbsp;Decorators can also change the result of the constructor. In this case, the definition of the decorator function changes slightly, but it also takes the class constructor as a parameter:

```js
1. function logger<TFunction extends Function>(target: TFunction): TFunction{
2.
3. let newConstructor: Function = function(name:string){
4. console.log("Creating new instance");
5. this.name = name;
6. this.age = 23;
7. this.print = function():void{
8. console.log(this.name, this.age);
9.         }
ten.     }
11. return <TFunction>newConstructor;
12. }
13.
14. @logger
15. class User {
16.name:string;
17. constructor(name: string){
18. this.name = name;
19.     }
20.print():void{
21. console.log(this.name);
22.}
23.}
24. let tom = new User("Tom");
25. let bob = new User("Bob");
26. tom.print();
27. bob print();
```

&nbsp;&nbsp;&nbsp;&nbsp;In this case, the logger decorator is typed as TFunction, which is an extension of the Function type. In essence, this is the type of the constructor function.

&nbsp;&nbsp;&nbsp;&nbsp;In the decorator itself, the passed-in target constructor is not used in any way. But a new constructor is created. We assume that some parameter will be passed to the constructor, which will be called name. The value of this parameter is passed to the this.name = name; property. The constructor also sets the new this.age property and the this.print() method, which prints the values ​​of both properties to the console.

&nbsp;&nbsp;&nbsp;&nbsp;Next, the decorator is applied to the User class. This class has a constructor that sets the name property. However, since we've overridden the constructor, in reality, when the User object is created, both the name property and the age property will be set. And besides, it will override the print method.

Browser console output
// Creating new instance Creating new instance Tom 23 Bob 23
Keep in mind that replacing a constructor leads to a complete replacement of all properties and methods of the class.

### Decorators for fields or class properties

&nbsp;&nbsp;&nbsp;&nbsp;Another use for decorators is in class properties. Imagine there is a Person class with an Age field, the value of which, according to the application logic, should be between 18 and 60. Let's do this check using a decorator:

```js
1. class Person {
2. @Age(18, 60)
3. age:number;
four. }
```

Let's go back to the formal definition:
```js
1. declare type PropertyDecorator =
2. (target: Object, propertyKey: string | symbol) => void;
```

Our validation decorator looks like this:
```js
1. import 'reflect-metadata';
2.
3. function Age(from: number, to: number) {
4. return function (object: Object, propertyName: string) {
5. const metadata = {
6. propertyName: propertyName,
7. range: { from, to },
eight.         };
9. Reflect.defineMetadata(`validationMetadata_${propertyName}`, metadata, object.constructor);
ten.     };
eleven. }
```

&nbsp;&nbsp;&nbsp;&nbsp;There is no basic logic here. We simply store the information we need in the metadata store. This is because this code, like the class decorator code, will be executed only once when the code is read. Before the class constructor was called.

Compiled code:
```js
1. class Person {
2. ...
3.}
4. __decorate([
5.age_decorator_1.Age(18, 60),
6. __metadata("design:type", Number)
7. ], Person.prototype, "age", void 0);
```

&nbsp;&nbsp;&nbsp;&nbsp;It can be seen that immediately after the class definition, the compiler placed its __decorate function, into which we passed our decorator with parameters.

&nbsp;&nbsp;&nbsp;&nbsp;This is a kind of confirmation that the main task of decorators is to make the code more readable, informatively rich. In the case of validation, describe the rules for checking in the same place as the class itself, and in a convenient form.

Returning to validation, it needs to be described separately:
```js
1. function validate<T>(object: T) {
2. const properties = Object.getOwnPropertyNames(object);
3. properties.forEach(propertyName => {
4. let metadata = Reflect.getMetadata(metaKey + propertyName, object.constructor);
5. if (metadata && metadata.range) {
6. const value = object[metadata.propertyName];
7. if (value < metadata.range.from || value > metadata.range.to) {
8.throw new Error('Validation failed');
9.             }
ten.         }
eleven.     });
12. }
```

In the example, we do one single check. The real scenario will be somewhat more complicated.

Call example:
```js
1. const person = new Person();
2. person.age = 40;
3. validate(person);
4. // > validation passed5.
6. person.age = 16;
7 validate(person);
8. // > validation error
```

### NPM

&nbsp;&nbsp;&nbsp;&nbsp;Node.js was launched in 2009 and hundreds of thousands of applications have been built on it since. One reason for the success was npm, a popular package manager that allows JS developers to quickly share packages.

&nbsp;&nbsp;&nbsp;&nbsp;npm (Node Package Manager) is the default package manager for JavaScript, powered by Node.js. The npm manager has two parts:

- CLI (command line interface) - a tool for hosting and downloading packages,
• online repositories containing JS packages.

### package.json

&nbsp;&nbsp;&nbsp;&nbsp;Every JavaScript project, be it Node.js or a web application, can be copied as an npm package with its own description and package.json file.

&nbsp;&nbsp;&nbsp;&nbsp;The file is generated by the npm init command when creating a JavaScript/Node.js project with the following metadata:

- name: JS library/project name.
• version: version of the project.
• description: description of the project.
• license: project license

###Project setup
 

&nbsp;&nbsp;&nbsp;&nbsp;Set up a Node project, but compile and run the project with TypeScript.
- Step 1 - Initializing the npm project
To get started, create a new folder called node_project and navigate to that directory.
```
1. mkdir node_project
2. cd node_project
```

Then initialize it as an npm project:

``` 1. npm init ```

&nbsp;&nbsp;&nbsp;&nbsp;After running npm init, you will need to pass information about your project to npm. If you allow npm to accept defaults, you can add the y flag to skip dialogs asking for more information:

``` 1. npm init -y ```

&nbsp;&nbsp;&nbsp;&nbsp;Your project space is now set up and you can proceed to install the necessary dependencies.

- Step 2 - Install Dependencies

&nbsp;&nbsp;&nbsp;&nbsp;The next step after initializing the base npm project is to install the dependencies required to run TypeScript.

Run the following commands from your project directory to install dependencies:
```
1. npm install -D typescript@3.3.3
2. npm install -D tslint@5.12.1
```
&nbsp;&nbsp;&nbsp;&nbsp;The -D flag is an abbreviation for the option: --save-dev. More information about this flag can be found in the npmjs documentation.

Run the following command:
``` 1. tsc --init ```
It will generate a tsconfig.json file with the correct comments.

&nbsp;&nbsp;&nbsp;&nbsp;To learn more about the available key-value options, you can refer to the official TypeScript documentation, which explains all the options.

&nbsp;&nbsp;&nbsp;&nbsp;Now you can set up TypeScript Code Compliance for this project. Open the root directory of your project in a terminal, which is set as node_project in this tutorial, and run the following command to generate a tslint.json file:
```
1. ./node_modules/.bin/tslint --init
```

Open the generated tslint.json file and add the appropriate no-console rule:
tslint.json
```
{
"defaultSeverity": "error",
"extends": ["tslint:recommended"],
jsRules: {},
rules: {
"no-console": false
},
"rulesDirectory": []
}
```
&nbsp;&nbsp;&nbsp;&nbsp;By default, the TypeScript Inspector prevents the use of debugging via console commands, so you must explicitly tell it to disable the default no-console rule.

- Step 3 - Update the package.json file


&nbsp;&nbsp;&nbsp;&nbsp;Now you can run functions in the terminal individually or create an npm script to run them.
&nbsp;&nbsp;&nbsp;&nbsp;In this step, we will create a start script that will compile and transpile the TypeScript code and then run the resulting .js application.

Open the package.json file and update it accordingly:
```
1. package.json
2. {
3. "name": "node-with-ts",
4. "version": "1.0.0",
5. "description": "",
6. "main": "dist/app.js",
7. "scripts": {
8. "start": "tsc && node dist/app.js",
9. "test": "echo \"Error: no test specified\" && exit 1"
ten.   },
11. "author": "",
12. "license": "ISC",
13. "devDependencies": {
14. "tslint": "^5.12.1",
15. "typescript": "^3.3.3"
16.   },
17.}
eighteen. }
```

&nbsp;&nbsp;&nbsp;&nbsp;In the code snippet above, we updated the main path and added the start command to the scripts section. If you look at the start command, you will see that the tsc command is run first, and then the node command. This will compile and the generated output will be run with node.

&nbsp;&nbsp;&nbsp;&nbsp;The tsc command instructs TypeScript to compile the application and place the generated .js output in the specified outDir directory, as specified in the tsconfig.json file.

- Step 4 - Launch

&nbsp;&nbsp;&nbsp;&nbsp;Now TypeScript and the validator are set up and we can start building the Node Express Server module.

First, create a src folder in the root directory of your project:
```
1. mkdir src
```
Then create a file called app.ts:
```
1. touch src/app.ts
```
At this point, the directory structure should look like this:
├── node_modules/
├── src/
├── app.ts
├── package-lock.json
├── package.json
├── tsconfig.json
├── tslint.json
Open the app.ts file in your preferred text editor and paste the following code snippet:
```
1. console.log("Hello world")
```
Run the application with the following command:
```
1.npm start
```

### NPM scripts

Package.json includes a scripts field to automate builds, like so:
```
one. {
2.scripts: {
3. "build": "tsc",
4. "format": "prettier --write **/*.ts",
5. "format-check": "prettier --check **/*.ts",
6. "lint": "eslint src/**/*.ts",
7. "pack": "ncc build",
8. "test": "jest",
9. "all": "npm run build && npm run format && npm run lint && npm run pack && npm test"
ten. }
eleven. }
```
eslint, prettier, ncc, jest can be installed globally or locally per project inside node_modules/.bin/.

###Dependencies and devDependencies

&nbsp;&nbsp;&nbsp;&nbsp;These are dictionaries with npm library names (key) and their semantic versions (value). Example from the TypeScript Action template:
```
one. {
2. "dependencies": {
3. "@actions/core": "^1.2.3",
4. "@actions/github": "^2.1.1"
5. },
6. "devDependencies": {
7. "@types/jest": "^25.1.4",
8. "@types/node": "^13.9.0",
9. "@typescript-eslint/parser": "^2.22.0",
10. "@zeit/ncc": "^0.21.1",
11. "eslint": "^6.8.0",
12. "eslint-plugin-github": "^3.4.1",
13. "eslint-plugin-jest": "^23.8.2",
14. "jest": "^25.1.0",
15. "jest-circus": "^25.1.0",
16. "js-yaml": "^3.13.1",
17. "prettier": "^1.19.1",
18. "ts-jest": "^25.2.1",
19. "typescript": "^3.8.3"
twenty. }
21.}
```

&nbsp;&nbsp;&nbsp;&nbsp;These dependencies are installed by npm install with the --save and --save-dev flags. They are intended for use in production and development, respectively.

> About versioning:
> • ^: last minor release. For example, ^1.0.4 will install version 1.3.0 if it is the last minor release in series 1 of a major release.
> • ~: Latest patch release. ~1.0.4 will install 1.0.7 if it's the last minor version in the 1.0 series of minor releases.
> • to install a specific version or a range of versions, use @npm install nest@">4.15.0 <4.16.0"

&nbsp;&nbsp;&nbsp;&nbsp;All package versions will be displayed in the generated package-lock.json file.
package-lock.json

&nbsp;&nbsp;&nbsp;&nbsp;The file describes the package versions used in the JavaScript project. If package.json includes a general description of dependencies, then package-lock.json is more detailed - the entire dependency tree.

&nbsp;&nbsp;&nbsp;&nbsp;package-lock.json is generated by the npm install command and read by the npm CLI in order to render the environment for the project via npm ci.

### Install packages


npm install is a command that installs packages.

&nbsp;&nbsp;&nbsp;&nbsp;By default, npm install <package-name> with a ^ will install the latest version of the package. Downloads the package to the project's node_modules folder as configured in the package.json file, updating the package version where possible (and updating package-lock.json in turn). If you want to install a package globally, you can specify the -g flag.

&nbsp;&nbsp;&nbsp;&nbsp;Adding the --production flag will install only the dependencies needed for the application to run, without inflating node_modules.

### npm ci
&nbsp;&nbsp;&nbsp;&nbsp;If npm install --production is optimal for production, is there a similar command for local development? Yes, it's called npm ci.

&nbsp;&nbsp;&nbsp;&nbsp;As before, if package-lock.json does not already exist in the project, it will be generated when npm install is called. npm ci accesses the lock file to download the exact version of the packages. Thus, on different machines, the set of packages will remain the same.

### npm audit
&nbsp;&nbsp;&nbsp;&nbsp;To avoid adding malicious packages to repositories, the npm.js organization came up with the idea of ​​ecosystem auditing by creating the npm audit module. It provides information about vulnerabilities in packages and the existence of patched versions.

&nbsp;&nbsp;&nbsp;&nbsp;If fixes are available in future versions of the package, npm audit fix will automatically update the versions of affected dependencies.

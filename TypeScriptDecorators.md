
 > In TypeScript, you can create decorators using the special syntax @expression, > where expression is a function that will be called automatically during runtime with details about the target of the decorator.

The target of a decorator depends on where you add them. Currently, decorators can be added to the following components of a class:

- Class declaration itself
- Properties
- Accessors
- Methods
- Parameters


# Class decorator


 * @remarks Decorators are executed when the class is defined, not when it is instantiated thats why we first see the decorator log and then the constructor log
 * @param constructor function of the class
``` ts 
function Logger(constructor:Function) {
console.log('Logging...');
console.log(constructor);
}
```


 * @param constructor is the constructor function of the class
 * @remarks In the sealed function you are then calling Object.seal on the target,
 which is the class constructor, and also on their prototype. 
When you do that no new properties can be added to the class constructor or 
their property, and the existing ones will be marked as non-configurable.
``` ts
function Sealed(constructor:Function) {
    Object.seal(constructor);
    Object.seal(constructor.prototype);}
```
#### Class Decorator with return factory function

 * @param loggingString defines the string which will be logged
 * @param constructor is now a parameter in a return function (decorator function)
 whichs gets executed when the class is instantiated
 * @remarks has to be called with () to be executed
``` ts
function LoggerString(loggingString:string) {
    return function(constructor:Function) {
         console.log(loggingString);
        console.log(constructor);
    }
}
```

Class Decorator with return factory function which can be used only in client enviroronment and not node (doesn't work in node because node doesn't have window object or DOM)

 * @param template template of the element
 * @param hookId DOM element where we want to render the template
``` ts
function WithTemplate(template:string, hookId:string) {
return function(constructor:any) {
    console.log('Rendering template');

    const hookEl = document.getElementById(hookId);
    const p = new constructor()
    if(hookEl) {
    hookEl.innerHTML = template;
    hookEl.textContent = p.name; }
    }
}
```
 * @param myBoolean to be defined when decorator is called
 * @remarks Decorator factories are functions that return another function. 
 
 They receive this name because they are not the decorator implementation itself. Instead, they return another function responsible for the implementation of the decorator and act as a wrapper function. They are useful in making decorators customizable, by allowing the client code to pass options to the decorators when using them.
``` ts
const ClassDecoratorWithReturnFactory = (myBoolean: boolean) => {
    return function(constructor: Function) {
        console.log('ClassDecoratorWithReturnFactory');
    }
}

```
The decorator functions execute bottom up!
Outer functions executes first,up bottom!
Decorators are not executed when the class is instantiated or   
when method is called, but when the class is defined!
They allow you to do some additional work behind the scenes (meta programming)   
when the class is defined
``` ts
@Logger
@LoggerString("LOGGING - PERSON")
//@WithTemplate('<h1>My Person Object</h1>', 'app')
@Sealed
//@ClassDecoratorWithReturnFactory(true)
class Person {
name = 'Hrvoje'

constructor() {
console.log("creating person object...");
    }
}
let hrvoje = new Person();


// Field decorator
// We can have 2 arguments: target, name of the property

```

 * @param target static properties, the constructor function of the class. For all the other properties, the prototype of the class.
 * @param propertyName name of the member
``` ts
function Log(target:any,propertyName:string | Symbol) {
    console.log('Property decorator!');
    console.log(target, propertyName);

}

// Accessor decorator
// We get 3 arguments: target, name of the property and the descriptor
```

 * @param target is prototype if we are dealing with the instance or if we are dealin with the static property then it is the constructor function.
 * @param name is the name of the accessor itself, not the name of the property
 * @param description descrives a property on Object.
 
Congigurable,enumerable,writable,value,get,set
``` ts
function Log2(target:any,name:string,description: PropertyDescriptor) {
    console.log('Accessor decorator!');
    console.log(target);
    console.log(name);
    console.log(description);
}

```
 * @remarks decorator that can be used to change the enumerable flag of a getter/setter accessor:
``` ts
const enumerable = (value: boolean) => {
    return function(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
        descriptor.enumerable = value;
    };
}

// Method decorator
// We get 3 arguments: target, name of the methody and the descriptor

function Log3(target: any,name: string | Symbol, description: PropertyDescriptor) {
    console.log('Method decorator!');
    console.log(target);
    console.log(name);
    console.log(description);
}

// Parameter decorator
// We get 3 arguments: target, name of the method in which we use this param and the position(number) of the parameter

function Log4(target:any, name:string | Symbol, position:number) {
    console.log(`Decorating param ${position} from ${name}`);

}

class Product {

@Log
title:string;
private _price:number;

@Log2
set price(val:number) {
    if(val > 0) {
        this._price = val;
    } else {
        throw new Error('Invalid price - should be positive!');
    }
}

constructor(t:string,p:number) {
this.title = t;
this._price = p;
}

@Log3
getPriceWithTax(@Log4 tax:number) {
    return this._price * (1 + tax)
}

toString() {
    return `Title: ${this.title}, Price: ${this._price}`;
    }
}
```

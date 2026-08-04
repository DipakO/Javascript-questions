https://chatgpt.com/c/6a61c32f-51b0-83ee-8d5e-54fbf04dcbb2
https://chatgpt.com/c/6a585d5f-17f4-83e8-ab3a-ca2261ef6753


1. What is the Javascript ?
Ans: Javascript is the cross platform, object oriented scripting language which used to make webpages interactive.
		 Old Name: LiveScript (Javascript has followed most of the java's naming convention, expression syntax that's why it's renamed LiveScript to Javascript)
     Javascript is a case-sensitive 
     
2. Variable declaration in JS ?
Ans: JS has three type of variable declaration.
		 1. var: Declares a variable, optinally initializing it to value.
     2. let: Declared a block-scoped, local variable, optinally initializing it to value.
     3. const: Declared a block-scoped, read-only named constant.
     The names of variable called as identifiers.
     Scopes:
     1. Global Scope: The default scope for all coding runing in script mode.
     2. Module Scope: The scope for code running in module mode.
     3. Function Scope: The scope created with function.
     4. Block Scope: The scope is created with a pair of curly braces.
     
     Global Variable: When you declare variable outside of any funcation it is called global variable.
     Local Variable: If you have declare any variable inside the function then it's local variable.
     
3. Data types in JS ?
Ans: THe latest ECMAScript standard defines eight data types:
  * Seven data types that are primitives:
		 1. Boolean: True and False.
     2. Null: A special keyword denoting a null value.
     3. undefined: A top-level property whose value is not defined.
     4. Number: An integer or floating point number. For example: 42 or 3.1235.
     5. BigInt: An integer with arbitrary precision. For example: 9007199254740992n.
     6. String: A sequence of characters that represent a text value. For example: "abc".
     7. Symbol: A data type whose instances are unique and immutable.
	* Object
  
4. Conditional Statements in JS ?
Ans: A conditional statements is a set of commands that exceutes if a specific condition is true.
		 JS supports two conditional statements: if...else and switch.
     
     if...else statement 
     Use the if statement to execute a statement if a logical condition is true. Use the optional else clause to execute a statement if the condition is false.
     We can also check the multiple condition using else if.
     
     switch statements:
     A switch statements allows a program to evaluate an expression and attempt to match the expression's value to a case label. If a match is found, the 
     program executes the associated statement.
     break statements
     The optional break statement associated with each case clause ensures that the program breaks out of switch once the matched statement is executed,
     and then continues execution at the statement following switch. 
     
		 Exception handling statements
     You can throw exception using the throw statement and handle them using try...catch statement.
     
     try...catch statement
     The try...catch statement marks a block of statements to try, and specifies one or more responses should an exception be thrown. If an exeption is thrown
     , the try...catch statement catches it.

5. Loops and Iteration:
Ans: 1. For statement
		 2. do...while statement
     3. while statement
     4. labeled statement
     5. break statement
     6. continue statement
     7. for...in statement
     8. for...of statement
     
     1. For statement:
     for loop repeats until a specified condition evaluate to false .
     
     2. do...while statement:
     The do...while statement repeats until a specified condition evaluates to false.
     do 
     	statement
     while (condition);
     
     statement is always exceuted once before the condition checked.
     If the condition true statement executes again. At the end of every execution, the condition is checked. When the condition is false, execution is stops.
     
     3. While statement:
     A while statement executes its statement as long as a specified condition evaluates to true. 
     
     4. labeled statement:
     A label provides a statement with an indetifier that lets you refer to it elsewhere in your program. For example you can use a label to identify a loop,
     and then use the break and continue statements to indicate where the program should interupt the loop or continue its execution.
     
     5. break statement:
     Use a break statement to terminate the loop
     
     6. continue statement:
     The continue statement can be used to restart a while, do...while, for, or label statement.
     
     7. for...in statement:
     The for...in statement iterates a specified variable over all the enumerable properties of object.
     
     8. for...of statement:
     The for...of creates a loop iterating over iterable objects (Array, Map, Set arguments)

6. Functions:
		Functions are one of the fundamental building blocks in Javascript.It should take some input and return an output where there is an some obvious
    relationship between the input and output. 
    
    * Function declarations:
    A function defination (also called as function declaration or function statement) consist of function keyword followed by the 
    * The name of function
    * A list of parameters to the function, enclosed in paranthesis and separated by commas.
    * The Javascript statement that define the function, enclosed in curly braces.
    
    * Recursion:
    A Function can refer to and call itself. It can be referred to either by function expression or declaration's name, or via any in-scope variable that
    refers to the function object.
    A function that calls itself is called recursive function. In some ways, recursion is analogous to a loop. Both execute the same code multiple times, and
    both require a condition.
    
    * Immediately Invoked Function Expressions (IIFE)
    An IIFE is a code pattern that directly calls a function defined as expression.
    Instead of saving function in a variable, the function is immediately invoked. This is almost the eqvivelant to just writing the function body
    
    * Closures:
    
7. Expressions and operators:
		
    1. Assignment Operators
    2. Comparison Operators
    3. Arithmetic Operators
    4. Bitwise Operators
    5. Logical Operators
    6. BigInt Operators
    7. String Operator
    8. Conditional (ternary) Operators
    9. Comma Operators
    10. Unary Operators
    11. Relational Operators
    
8. Number and String
		
    We can use four type of number literals: decimal, binary, octal and hexadecimal.



***************************************** JS Advance
⭐⭐⭐⭐⭐ 1. JavaScript Execution Context

1***) What is Execution Context?
Ans: Execution Context is the environment where JavaScript executes code. It contains variables, functions, scope information, and the this value required for execution.


Simple Analogy
Think of an execution context as a workspace.
Whenever JavaScript starts executing a piece of code, it creates a new workspace containing everything needed to execute that code.

Cross Questions

Q1. Is Execution Context the same as Scope?
Ans: No, Execution Context is the environment created when code executes. 
Scope determines where variables can be accessed. 

Q2. Does every JavaScript program have an Execution Context?
Ans: Yes. Every JavaScript program starts by creating a Global Execution Context.

2***) Types of Execution Context
Ans: The primary two types are the Global Execution Context, which is created once when the program starts, and the Function Execution Context, which is created every time a function is called.

Cross Question

Q1. How many Global Execution Contexts exist?
Ans: Only one per JavaScript program (or per global environment such as a browser tab or Node.js process).

3***) Global Execution Context (GEC)
The Global Execution Context is created when the JavaScript file starts executing. It is created only once and remains until the application or page finishes execution.
All global variables and functions are stored in this execution context.

Cross Questions

Q1. What is the global object?
Ans: Browser: window, Node.js: global.

Q2. What is this inside the Global Execution Context?
Ans: Browser: this refers to the window object
Node.js: behaviour differs depending on the module system and execution environment.

Q3. What are the phases of an Execution Context?
Ans: Every Execution context goes through two phases: Memory Creation Phase, where memory is allocated, and the Execution Phase, where the code runs line by line.

4***) Function Execution Context (FEC)
Whenever a function is called, JavaScript creates a new Function Execution Context. It contains: 
Function Parameters, Local variables, Inner Functions, The value of this.
Once the function finish execution, it's execution context is removed from the call stack.

Cross Questions

Q1. Does every function call create a new Execution Context?
Ans: Yes, Even if you call the same function multiple times, a new Function Execution Context is created for each invocation.

Q2. Can multiple Function Execution Contexts exist?
Ans: Yes, If functions call other functions, multiple contexts exist simultaneously in the call Stack.

5***) Execution Context Lifecycle
Every Execution context goes through two phases: 
1. Memory Creation Phase.
2. Execution Phase.

6***) Memory Creation Phase (Creation Phase)
During the memory creation phase, JavaScript scans the code and allocates memory before executing any line.

During this phase: 
Variables declared with var are initialized with undefined.
Variables declared with let and const are allocated but remain uninitialized (Temporal Dead Zone)
Function declarations are stored with their complete definitions.
The value of this is determined for the execution context.


Cross Questions

Q1. Are variables assigned values during the creation phase?
Ans: No. Only memory is allocated. Actual assignment happen during the Execution phase.

Q2. Why can function declarations be called before they appear?
Ans: Because the complete function definition is stored during the Memory Creation Phase.

7***) Execution Phase
During the Execution Phase, JavaScript executes the code line by line. Variable receive their assigned values, functions are invoked, expressions are evaluated, and new Function Execution Contexts are created whenever a function is called.

Cross Questions

Q1. What happens if a function is called?
Ans: JavaScript creates a new Function Execution Context and pushes it onto the Call Stack.

8***) Call Stack
The Call Stack is a LIFO data structure that manages function execution. Each function call pushes a new execution context onto the stack, and it is removed after the function finishes.

Cross Questions

Q1. Why is it called a stack?
Ans: Because it follows LIFO. The Last function added is the first one removed.

Q2. What happens if the stack becomes too large?
Ans: A stack overflow occurs.

Frequently Asked Scenario

FAQ1. What happens internally when JavaScript executes a file?
Ans: When JavaScript executes a file, it first creates the Global Execution Context. During the Memory Creation Phase, memory is allocated for variables and functions. Then, in the Execution Phase, the code runs line by line. Whenever function is called, JavaScript creates a new Function Execution Context, pushed it onto the Call Stack, executes it, and removes it once execution completes.

FAQ2. What happens when one function calls another?
Ans: When a() is called, JavaScript creates a Function Execution Context for a() and pushed it onto the Call Stack. Inside a(), calling b() creates another execution context, which is pushed on top of a(). Similarly, calling c() pushes another context. Once c() finishes, it's context is removed first, followed by b(), then a(), following the LIFO principle.

FAQ3. Can multiple execution contexts exist simultaneously?
Ans: Yes. If one function calls another, multiple execution contexts exist simultaneously in the Call Stack until they complete.

FAQ4. Is the Global Execution Context ever removed?
Ans: It remains until the JavaScript program finishes executing or the page/application is unloaded.

FAQ5. What is inside an Execution Context?
Ans: It contains:
Variable Environment
Lexical Environment (scope information)
this binding

FAQ6. What is the difference between Global and Function Execution Context?
Global Execution Context				Function Execution Context
Created once 						Created on every function call
Exists for the lifetime of the program.			Exists only while the function executes
Stores global variables and functions 			Store local variables, parameters, and inner functions.

FAQ7. Does every function call create a new memory space?
Ans: Yes. Each function invocation gets its own separate execution context with its own local variables and parameters.

⭐⭐⭐⭐⭐ 2. JavaScript Hoisting


1) What is Hoisting?

Ans: Hoisting is JavaScript default behaviour of moving declarations to the top of their scope during the Memory Creation Phase before the code is executed. 

It is important to note that JavaScript does not physically move the code, instead during memory creation,

* var variables are allocated memory and initialized with undefined.
* let and const variables are allocated memory but remain uninitialized.
* Function declarations are stored with their complete function definitions.
This behaviour is called hoisting.

Cross Questions

Q1. Does JavaScript move the code to the top ?
Ans: No, JavaScript does not physically move the code. It only allocates memory during the Memory Creation Phase.

Q2. Is hoisting only for variables?
Ans: No, Functions are also hoisted.

2) Hoisting with var
Ans: Variables declared with var are hoisted and initialized with the value undefined. Therefore, accessing them before assignment does not throw an error.
Instead, It returns undefined.

Why does var become undefined?
Ans: During the Memory Creation Phase, JavaScript allocates memory for var variables and automatically initializes them with undefined.
The actual assign value is stored later during the Execution Phase.

Cross Questions

Q1. Does var throw an error before declaration?
Ans: No, It returns undefined.

Q2. Why was var considered problematic?
Ans: Because accessing it before assignment returns undefined, which can hide bugs and make debugging difficult.

3\*\*\*) Hoisting with let
Ans: Variables declare with let are hoisted, but they are not initialized during the Memory Creation Phase. They remain inside the Temporary Dead Zone (TDZ) until declaration line is executed. Accessing them before declaration results in a ReferenceError.

Cross Question

Q1. Is let hoisted?
Ans: Yes, let is hoisted, but it is not initialized until execution reaches its declaration.

4) Hoisting with const
Ans: const behaves similarly to let. It is hoisted but remains in TDZ until its declaration is executed. Accessing it before declaration thrown a ReferenceError.

Cross Question

Q1. Why does const also have TDZ?
Ans: Because const is also hoisted without initialization. Since const must be initialized when declared, JavaScript prevents access before the declaration by placing it in the TDZ.

5) Function Hoisting
Function declaration are completely hoisted. During the Memory Creation Phase, JavaScript stores the entire function definition in memory.
Therefore, function declarations can be called before they appear in the code.

Cross Questions

Q1. Why the function declarations be called before declaration?
Ans: Because the complete function definition is stored during the Memory Creation Phase.

Q2. Are all functions hoisted ?
Ans: No, Only function declarations are fully hoisted.

6) Function Expression vs Function Declaration
Ans: A Function declaration is fully hoisted with its implementation.
A Function Expression behaves like a variable. If declared with var, only the variable is hoisted as undefined; if declared with let or const, it remains in the TDZ until initialized.

Comparison Table
Function Declaration 					Function Expression
Fully hoisted						Variable is hoisted
Callable before declaration 				Not callable before initialization
Entire function stored 					Variable initialized later.

7) Temporal Dead Zone (TDZ)
Ans: The Temporal Dead Zone (TDZ) is the time between when a let OR const variable enters its scope and when its declaration is executed. During this period, the variable exists but cannot be accessed.
Attempting to access it results in a ReferenceError.

Cross Questions

Q1. Why does TDZ exist?
Ans: TDZ helps catch programming mistakes by preventing access to variables before they are initialized. 

Frequently Asked Scenario

FAQ1. Why does var become undefined?
Ans: During the Memory Creation Phase, JavaScript allocated memory for var variables and initialize them with undefined. The actual value is assigned later during the Execution Phase. That's why accessing a var variable before its assignment returns undefined instead of throwing an error.

Cross Question.

Q1. Why can't we access let before declaration?
Ans: Although let is hoisted, it is not initialized during the Memory Creation Phase. It stays in the Temporary Dead Zone until the declaration line executes. Accessing it before then throws a ReferenceError.

Q2. Are arrow functions hoisted?
Ans: Arrow functions are usually assigned to variables. Therefore, their hoisting behaviour depends on the variable declaration: 
* If assigned to var, the variable is hoisted as undefined, so calling it before assignment results in a TypeError
* If assigned to let or const, the variable is in the TDZ, so calling it before assignment results in a ReferenceError.

FAQ2. Is hoisting performed at runtime?
Ans: No, Hoisting happens during the Memory Creation Phase, before the Execution Phase begins. 

FAQ3. Which declaration are full hoisted ?
Ans: Only Function Declaration are fully hoisted with their complete implementation.

FAQ4. Does TDZ mean memory isn't allocated?
Ans: No, Memory is allocated for let and const, but they remain uninitialized until execution reaches their declaration.

⭐⭐⭐⭐⭐ 3. JavaScript Scope

1) What is Scope?
Ans: Scope is the region of a program where a variable or function is accessible. In other words, scope determines where a variable can be accessed in the code.
JavaScript provides different types of scopes: 
* Global Scope
* Functional Scope
* Block Scope
* Lexical Scope

Cross Questions

Q1. What does Scope determine?
Ans: Scope determine where variables and functions are accessible.

Q2. Is the scope created at runtime ?
Ans: No. Scope is determined when the code is written (lexical scope), not when it is executed.

2) Global Scope 
Ans: A variable declared outside all functions and blocks belongs to the Global Scope. Global variables can be accessed from anywhere in the program.

3) Function Scope
Ans: Variable declares inside a function are available only within that function. They cannot be accessed from outside the function.

Cross Questions

Q1. Which keyword creates function-scoped variables?
Traditionally, var is function-scoped.
let and const are block-scoped.

4) Block Scope 
Block is any code enclosed with {}. Variable declared with let and const are block-scoped, meaning they are accessible only inside that block.

Cross Questions

Q1. Does var follow block scope?
Ans: No, var ignores block scope and is function-scoped.

Q2. Why were let and const introduced?
Ans: To provide block scope and avoid bugs caused by var.

5) Lexical Scope
Lexical Scope means that a function can access variables from the scope where it was defined, not where it is called.
JavaScript determines scope based on the physical placement of code during development.

6) Scope Chain
Scope Chain is the mechanism JavaScript uses to find variables. 
When a variable is accessed, JavaScript first searches in the current scope.
If it is not found, JavaScript searches the parent scope, then the grandparent scope, continuing until it reaches the Global scope.
If the variable still isn't found, JavaScript thrown a ReferenceError.

Cross Questions

Q1. How does JavaScript search for variables?
Ans: JavaScript Searches: 
1. Current Scope
2. Parent Scope
3. Grandparent Scope
4. Global Scope

Q2. What happens if the variable isn't found?
Ans: JavaScript throws: ReferenceError.

Global Scope vs Function Scope vs Block Scope
Global Scope 				Function Scope 					Block Scope
Accessible everywhere			Accessible only inside the function		Accessible only inside the block
Created outside functions		Created by functions 				Created by {} blocks
Lifetime is entire program		Exists while function executes 			Exists while block executes

Function Scope vs Block Scope
Function Scope 					Block Scope
Created by functions 				Created by {}
var follows function scope			let and const follow block scope.
Available throughout the function 		Available only inside the block

FA!1. How does JavaScript search for variables?
JavaScript starts searching in the current scope. If the variable is not found, it moves to the parent scope, then continues up through the Scope Chain until it reaches the Global Scope. If the variable is still not found, it throws a ReferenceError

FAQ2. What is Variable Shadowing?
Ans: Variable shadowing occurs when a variable declared in an inner scope has the same name as a variable in an outer scope.

⭐⭐⭐⭐⭐ 4. JavaScript Closures

1) What is a Closure ?
Ans: Closure is created when an inner function remembers and can access variables from its outer function even after the outer function has finished executing.
In other words, a closure allows a function to "remember" the environment in which it was created.
This is possible because JavaScript uses Lexical Scope.

function outer() {

    let count = 0;

    function inner() {
        count++;
        console.log(count);
    }

    return inner;
}

const counter = outer();

counter();
counter();
counter();

Explanation

When outer() executes: 
* count is created. 
* inner () is returned 
* Normally, local variables should disappear after the function finishes.
* But since inner() still references count, JavaScript keeps count alive.
* This preserved relationship is called a closure.

Cross Questions

Q1. Why does the variable still exist after the function finishes?
Ans: Because the returned inner function still has a reference to it. JavaScript keeps the variable in memory until nothing references the closure anymore.

Q2. Is Closure a feature or a design pattern?
Ans: Closure is a JavaScript language feature, not a design pattern.

2) How Does a Closure Work Internally?
Ans: When a function returned from another function, JavaScript store a reference to the outer function's lexical environment. Even after the outer function finishes execution, the returned function can still access those variables.

3) Advantages of Closures
Closures provide the several benefits: 
* Data Hiding 
* Private Variables
* Function Factories 
* Module Pattern
* Memorization
* Callbacks
* Event Handlers
* React Hooks

Cross Questions
Q1. Why are Closures useful?
Ans: Because they are allow functions to preserves state without exposing variables globally.

4). Disadvantages of Closures
Closures have some drawbacks:
  * Increase Memory usege because referenced variable stay alive
  * Can lead to memory leaks if unnecessary references are retained
  * Slightly harder to debug because variable remain accessible after the outer function exits.

Cross Questions

Q1. Should closure always be avoided ?
Ans: No, Closures are fundamental to JavaScript and are used extensively. They should simply be used thoughfully.

5). Practical Example – Data Hiding
Ans: Closures allows us to hide internal data from outside code.
Example :
function createCounter() {

    let count = 0;

    return function () {

        count++;

        return count;

    };

}

const counter = createCounter();

console.log(counter());

console.log(counter());

console.log(counter());

Why ?
count cannot be accessed directly.

6). Practical Example – Private Variables
Ans: Closures help to create private variables because only the returned functions can access them.
Example: 

function BankAccount() {

    let balance = 1000;

    return {

        deposit(amount) {
            balance += amount;
        },

        getBalance() {
            return balance;
        }

    };

}

const account = BankAccount();

account.deposit(500);

console.log(account.getBalance());

Output: 1500
Attempting: console.log(account.balance);
Output: undefined

7). Practical Example – Module Pattern
Ans: Before ES6 modules, Closures were commonly used to create modules with private state and public methods. 
Example:

const Counter = (function () {

    let count = 0;

    return {

        increment() {
            count++;
        },

        value() {
            return count;
        }

    };

})();

Counter.increment();

console.log(Counter.value());

Output: 1

8). Practical Example – Memoization
Ans: Memorization is an optimization technique that stores the result of expensive function calls and returns the cached result
 for repeated input.
Closures are commonly used to implement memorization because they are preserve the cache between function calls.
Example: 

function memoizedSquare() {

    const cache = {};

    return function (num) {

        if (cache[num]) {
            return cache[num];
        }

        cache[num] = num * num;

        return cache[num];
    };

}

const square = memoizedSquare();

console.log(square(5));

console.log(square(5));

Output: 25

25

The second call use cached instead of recalculating.

Advantages vs Disadvantages

Advantages                          Disadvantages
Data Hiding                         Higher Memory Usege 
Private Variable                    possible memory leaks
Module pattern                      More difficult debugging
Memorization                        Variables stay alive longer
Function Factories                  Can retain  unnecessary reference

Frequently Asked Scenario

FAQ1. What is a Closure?
Ans: Closure is a JavaScript feature where an inner function remembers and can access variable from its outer function even after
the outer function has completed execution. This is possible becasue of JavaScript preserves the function's lexical environment.

FAQ2. Why are Closures important?
Ans: Closures are important becasue they enable data hiding, private variables, module patterns, memorizations, callbacks, event
 bundlers, and many React hook implementation. They allow function to maintain state across multiple invocation without 
 exposing that state globally.

FAQ3. Can Closures cause memory leaks?
Ans: Yes, they can if closures keep references to large objects or DOM  elements that are no longer needed. As long as closure 
references an object, the JavaScript garbage collector cannot free that memory. Removing unnecessary references helps prevent 
memory leaks.

FAQ4. How does React use Closures?
Ans: React relies heavily on Closure. Event handler, useState, useEffect, useCallBack and custom hooks all use closure to access 
variables from the component where they were created.

FAQ5. Are Closures created only when returning a function?
Ans: No, Closure are created whenever an inner function accesses variables from its outer scope, whether or not the function is returned

FAQ6. Are Closures stored in memory?
Ans: Yes, JavaScript keeps the outer function's lexical environment alive as long as closure reference it. 

FAQ7. What is the relationship between Lexical Scope and Closures?
Ans: Lexical scope determine which variables a function can access based on where it is defined. A Closure is the runtime behavior
that preserves those variables event after the outer function has finished executing.

FAQ8. Are Closures bad for performance?
Ans: Not inherently. Closures are efficient and widely used. Performance issue raised only when they unnecessarily retain large 
object or resources in memory.

⭐⭐⭐⭐⭐ 5. JavaScript this Keyword

1). What is this?
Ans this is a special keyword in JavaScript that refers to the object that is currently executing the function.
The value of this is determined at runtime based on how the function is invoked, not where it is declared.
The value of this changes in difficult execution contexts such as:

* Global Context
* Function Context
* Object Method
* Constructor Function
* Class
* Arrow Function

Cross Questions

Q1. Is this decided when writing the code?
Ans: No, this is determine when the function is called, expect for arrow functions.

2). this in Global Context
In the browser, inside a normal script, this in the global context refers to the window object.
In ES6 modules or strict mode, the behavior can differ. In Node.js, the global context behaves differently from the browser.

3). this in Function Context
In a normal function, the value of this depends on how the function is called. 
* In non-strict mode (browser), calling a standalone function sets this to the global object (window)
* In strict mode, this is undefined.

4). this in Object Context
When a function is called as an object method, this refers to the object that invoked the method

5). this in Constructor Functions
When function is called using the new keyword, JavaScript creates a new object and sets this to that newly created object.

Cross Questions

Q1. What happens if we don't use new?
Ans: The function behaves like a normal function call, and this is not bound to a newly created object.

6). this in Classes
In a class, this refers to the current instance of the class. It is used to access instance properties and methods.

Cross Questions

Q1. Why do constructors use this?
Ans: Because this initialize the properties of the newly created object.

7). this in Arrow Functions
Arrow functions do not have their own this. Instead, they lexically inherit this from their surrounding scope.
This makes arrow functions usefull for callbacks because they preserve the outer this.

Cross Questions

Q1. How does an Arrow Function handle this?
Ans: Arrow function doesn't create their own this. They inherit it from the surrounding lexical scope.

Q2. Should object methods be written as arrow functions?
Ans: Generally No, If the method needs access to the object through this, use a normal function.

Normal Function vs Arrow Function
Normal Function                                   Arrow Function
Has its own this                                  Doesn't have its own this
this depends on how it's called                   this is inherited from surrounding scope.
Can be used as controctor                         Cannot be used with new
Has arguments object                              Doesn't have its own arguments

Global vs Function vs Object vs Arrow

Context                                     Value of this
Global (Browser)                            window
Normal Function (Non-strict)                window
Normal Function (Strict Mode)               undefined
Object Method                               Calling object
Constructor                                 Newly Created Object
Class                                       Current instance 
Arrow Functon                               Inherited from outer scope

Frequently Asked Scenario

FAQ1. What happens when a method is assigned to another variable?
Ans: When method is assigned to another variable and called independently, it loses its original object reference, Since it is
no longer refers to employee. Instead, this becomes the global object in non-strict mode or undefined in strict mode.

Frequently Asked Bonus Questions

FAQ1. What are call(), apply(), and bind()?
Ans: These methods allow us to explicitly control the value of this.
* call() --> Invokes immediately with individual arguments.
* apply() --> Invokes immediately with an array of arguments
* bind() --> Returns a new function with this permenently bound.

Cross Question

Q1. Why are arrow functions commonly used in callbacks?
Ans: Because they preserve the surrounding this, avoinding the need to write: 
const self = this;
or use .bind(this)

Q2. Can we change this of an arrow function using call(), apply(), or bind()?
Ans: No, These methods cannot change the lexical this of an arrow function.

⭐⭐⭐⭐⭐ 6. JavaScript call(), apply(), and bind()

1). Why do we need call(), apply(), and bind()?
Ans: In JavaScript value of this depends on how a function is called. Sometimes we want to explicitly control what this refers to.
call(), apply() and bind() allow us to manually set the value of this.

Real Project Example
In React Class component (before Hooks), developer often used: 
this.handleClick = this.handleClick.bind(this);
This ensured that inside handleClick refered to the component instance.

Cross Questions

Q1. Why do we need these methods?
Ans: Because JavaScript allows us to control the value of this explicitly instead of relying on how the function is called.

2). call()
call() invoke the function immediately and allows us to specify the value of this. Arguments are passed individually.

Syntax
function.call(thisArg, arg1, arg2, arg3);

Cross Questions

Q1. Does call() execute immediately ?
Ans: Yes.

Q2. How are arguments passed?
Ans: Individually.

3). apply()
apply work exactly like call(), expect that arguments are passed as an array.
Syntax
function.apply(thisArg, [arg1, arg2]);

Cross Questions

Q1. Does apply() execute immediately ? 
Yes.

Q2. How are arguments passed?
As an array.

4). bind()
bind() does not execute the function immediately.
Instead, it returns a new function with this parmanetly bound to the specified object.
The returned function can be executed later.

Syntax
const newFunction = function.bind(thisArg);

Cross Questions

Q1. Does bind() execute immediately?
No. It returns a new function

Q2. Which method returns a new function?
bind()

5). Difference between call(), apply(), and bind()?
Method                  Executes Immediately              Arguments                    Return New Function
call()                  Yes                               Individual                   No
apply()                 Yes                               Array                        No
bind()                  No                                Individual(stored)           Yes

6). Real-World Use Cases
1. Function Borrowing
Function Borrowing means using a method from one object with another object by changing the value of this.

2. React Class Components
Before, hook event handlers often lost the value of this.
bind() ensures this refers to the component instance.

3. Event Handlers
Without bind(), this would not refer to person.

4. Array as Arguments.
Suppose we have: const numbers = [10, 20, 30];
We can use: Math.max.apply(null, numbers);
Output: 30
Modern JavaScript typically uses the spread operator instead Math.max(...numbers)

Frequently Asked Scenario

FAQ1. Which on returns new function ?
Ans: bind() returns new function. It dows not execute immediately. The returned function can be invoked later while preserving
the bound value of this.

FAQ2. Which one accept array ?
Ans: apply() accepts arguments as an array, whereas call() accepts them individually.

FAQ3. Which one invokes immediately?
Ans: Both call() and apply() invoke the function immediately. bind() only returns a new function ans does not execute it until
you call it.

FAQ4. Can bind() accept arguments?
Ans: Yes, those arguments are stored (partialy applied) and used when returned function is called.

FAQ5. Can we change this again after using bind()?
Ans: No, Once function is bound using bind(), its this cannot be change by call() or apply().

FAQ6. Which is faster: call() or apply() ?
ANs: In modern JavaScript engines, the performance diffirence is negligible. Choose based on readablility 
and whether your arguments are alreadt in an array.

FAQ7. Why is bind() commonly used in callbacks ?
Ans: Because callbacks oftern lose their original object context. bind() permenently fixes the value of this.

FAQ8. Can arrow function use call(), apply() or bind() to change this ?
Ans: No, Arrow functions don;t have their own this; they inherit it form the surrounding lexical scope.
Therefore, call(), apply() and bind() cannot change the value of this for an arrow function.

Common Interview Tricky Question

CITQ.1 When would you use call() instead of bind() ?
Ans: I would use call() when I want to invoke the function immediately with a specific this value. I would use bind() when I need to 
pass the function as a callback or execute it later while preserving its this context.

⭐⭐⭐⭐⭐ 7. JavaScript Arrow Functions

1). What is an Arrow Function ?
Ans: An arrow function is a shorter way to write functions in JavaScript, introduced in ES6.
Unlike normal functions, arrow functions:
* Have a shorter syntax.
* Do not have thier own this.
* Do not have thier own arguments object.
* Cannot be used as constructors.
* Cannot be invoked using the new keyword.

Real Project Example
Arrow functions are commonly used in: 
* React Event handlers
* Array Methods (map, filter, reduce)
* Promise Callbacks
* API Calls
* setTimeout()
* setInterval()

Cross Questions:

Q1. Why were Arrow Functions introduced?
Ans: To provide a cleaner syntax and solve common issues related to this in callback functions.

2). Advantages of Arrow Functions.
Arrow functions provide several advantages:
* Shorter and cleaner syntax.
* Lexical this.
* Better for callbacks.
* Easier to read
* Widely used in React and modern JavaScript.

3). Limitations of Arrow Functions.
Arrow functions should not be used when we need:
* Their own this.
* Their own arguments.
* Constructor functions.
* Methods that rely on dynamic this.

4). No Own this.
Arrow functions do not create their own this.
Instead, they inherit this from the surrounding lexical scope.

5). No arguments Object
Arrow functions do not have their own arguments object.
If needed, they inherit arguments from the enclosing function or we should use rest paraments (...args).

Cross Question:

Q1. How do you replace arguments in an arrow function?
Use rest paraments (...args)

6). Cannot be Constructor
Arrow functions cannot be used as constructors because they don't have their own this and dont have an internal [[Construct]]
 method.

Cross Questions:

Q1. Why can't Arrow Functions be constructors ?
Ans: Because JavaScript doesn't give them the internal contructor behaviour ([[Contruct]]) required by the new keyword, and they
 don't create thier own this.

Arrow Function vs Normal Function

Feature                   Normal Function          Arrow Function
Syntax                      longer                    Shorter
Own this                    Yes                       No
Own arguments               Yes                       No
Can use new                 Yes                       No
Constructor                 Yes                       No
Suitable for object methods Yes                       Usually No

Frequently Asked Scenario

FAQ1. Can Arrow Functions be used as contructors?
Ans: No. Arrow functions cannot be used as contructors because they don't have their own this they
don't have support the internal [[Contruct]] method required by the new operator.

FAQ2. Why doesn't Arrow Function have its own this?
Ans: Arrow functions were intentionally desinged to inherit this from their surrounding lexical scope.
This avoids common issues where callbacks lose their original this context, making arrow functions
 especially useful in asynchronous code and React event handlers.

FAQ3. Why are Arrow Functions heavily used in React ?
Ans: React frequently uses callbacks, event handlers, and array methods like map().
Arrow functions perserve the surrounding this (where relevant) and provide concise syntax,
making component code cleaner and easier to maintain.

FAQ4. Do Arrow Functions support hoisting ?
Ans: Not in the same way as function declarations.
The arrow function is assigned to a const, which is in the Temporal Dead Zone until initialization.

FAQ5. Can Arrow Functions be generatiors?
Ans: No. Only regular function declarations or expressions can be generator functions using function*.

⭐⭐⭐⭐⭐ 8. JavaScript Event Loop

1). What is the Event Loop ?
Ans: JavaScript is a single-theaded language, which means it can execute only one piece of code at a time.
To handle asynchronous operations like API calls, timers, and user events without blocking the main thead, JavaScript uses the Event Loop.
The Event Loop continuously checks whether the Call Stack is empty. If it is, it moves pending tasks from the Microtask Queue first, 
ans then from the Callback (Macrotask) Queue to the Call Stack for execution.

Real Project Example
When a user clicks a button that makes an API call:
1. Click handler executes.
2. API request is sent.
3. JavaScript continues executing other code.
4. API response arrives later.
5. Callback is queued.
6. Event llop executes the callback when the Call Stack becomes empty.

2). JavaScript Runtime.
The JavaScript Runtime is the environment where JavaScript code executes.
It consists of:
* JavaScript Engine (V8, SpiderMonkey, JavaScriptCore, etc.)
* Call Stack
* Web APIs (Browser) or Node.js APIs
* Callback Queue
* Microtask Queue
* Event Loop

Cross Question

Q1. Is the Event Loop part of JavaScript?
Ans: No. The Event Loop is provided by the JavaScript runtime (Browser or Node.js), not by the JavaScript language itself.

3). Call Stack
The Call Stack is a data structure that keeps track of function execution.
It follows the LIFO (Last In, First Out) principle.

4. Web APIs
Web APIs are browser-provided features that handle asynchronous operations outside the JavaScript engine.
Exm:
* setTimeout
* setInterval
* fetch
* DOM Events
* Geolocation

Why?
setTimeout is handled by the browser's Web API while JavaScript continues executing.

5). Callback Queue (Macrotask Queue)
The Callback Queue, also called the Macrotask Queue, stores completed asynchronous callbacks such as:
* setTimeout
* setInterval
* DOM Events
* Message events

These tasks are executed after all microtasks have completed.

6). Microtak Queue
The Microtask Queue stores high-priority asynchronous tasks.
Common microtasks include:
* Promise callbacks (.then, .catch, .finally)
* queueMicrotask()
* MutationObserver

The event loop always empties the Microtask Queue before executing any Callback Queue task.

7). Event Loop Working
The Event Loop continuously monitors the Call Stack.
When the Call Stack becomes empty:
1. Execute all Microtasks.
2. Execute one Macrotask.
3. Repeat the process.

Microtask vs Macrotask
Microtask Queue                  Callback (Macrotask) Queue
Higher Priority                  Lower Priority
Promise                          setTimeout
queueMicrotask                   setInterval
MutationObserver                 DOM Events
Executed first                   Executed after all microtasks.

Frequently Asked Scenario

FAQ1. Why is JavaScript Single Threaded ?
Ans: JavaScript was desinged as a single-threaded language to simplify programming and avoid issues like race 
conditions adn thread synchronization. It executes one task at time using single call stack.
Asynchronous behaviour is achieved throught the runtime's Event Loop, Web APIs, 
Ans task queues rather than multiple JavaScript threads.

FAQ2. What executes first; Promise or setTimeout ?
Ans: Promise callbacks execute before setTimeout callbacks because Promise callbacks are placed in the Microtask Queue,
 which has higher priority than the Callback (Macrotask) Queue.

FAQ3. Difference between Microtask and Macrotask ?
Ans: The Microtask Queue contains high-priority tasks like Promise callbacks and queueMicrotask().
The Callback (Macrotask) Queue contains tasks like setTimeout, setInterval, and DOM events, After the Call Stack becomes empty,
the Event Loop executes all microtasks first, and only then executes the next macrotask.

FAQ4. Does setTimeout(fn, 0) execute immediately?
Ans: No. It only means the callback is eligible to run after at least 0 ms. It still waits until:
* The Call Stack is empty.
* All Microtasks have completed.

FAQ5. Can multiple microtasks execute before a macrotask ?
Ans: Yes, The Event Loop empties the entire Microtask Queue before executing the next macrotask.

FAQ6. Is asynch/await synchronous?
Ans: async/ await is syntactic sugar over Promises. After an await, the remianing code resumes as a microtask when the Promise resolves.

FAQ7. Does fetch() go directly to the Callback Queue ?
Ans: No. The browser handles the network request. When the Promise returned by fetch() resolves,
its .then() or await continuation is placed in the Microtask Queue.

FAQ8. Can a long-running synchronous task block the Event Loop?
Ans: Yes Example: while (true) {}
This blocks the Call Stack forever, preventing the Event Loop from processing timers, Promises, use interactions, or rendering.

FAQ9. Predict the Output

console.log("A");

setTimeout(() => console.log("B"), 0);

Promise.resolve().then(() => console.log("C"));

console.log("D");

Answer:
A
D
C
B

Explanation
1. A executes immediately.
2. setTimeout callback goes to the Callback Queue.
3. Promise callback goes to the Microtask Queue.
4. D executes.
5. Call Stack becomes empty.
6. Event Loop executes all Microtasks(C).
7. Finally, it executes the Callback Queue (B).

⭐⭐⭐⭐⭐ 9. JavaScript Promises

1). What is a Promise?
Ans: Prmoise is an object that represents the eventual completion (success) or failure of an asynchronous operation.
Instead of blocking the execution, a Promise allows JavaScript to continue executiong other code while waiting for 
asynchronous operation to complete.
Once the operation completes, the Promise either resolves with a value or rejects with an error.

Cross Questions:

Q1. Why do we need Promises?
Ans: Promises help handle asynchronous operations without deeply nested callbacks (Callback Hell).
They make code cleaner,  more readable, and easier to manage.

2). then()
then() executes when a Promise is successfully fulfilled.

3). catch()
catch() handles errors that occur during Promise execution or in any previous then() block.

4). finally()
finally() executes regardless of whether the Promise is fulfilled or rejected.
It is commonly used for cleanup tasks like hiding a loader or closing a databae connection.

5). Prmoise Chaining 
Example: 
Promise.resolve(10)

.then(value => value * 2)

.then(value => value + 5)

.then(value => console.log(value));

Each then() returns new Promise, enabling chaining.

6). Promise.all()
Promise.all() executes multiple Promises in parallel and waits until all of them are fullfilled.
If any one Promise rejects, the entire Promise.all() immediately rejects.
Promise.all() stops immediately when one Promise rejects.

7). Promise.allSetteld()
Promise.allSettled() waits until all Promises finish, regardless of whether they succeed or fail.
It returns the status and result of every Promise.

8). Promise.any()
Promise.any() returns the first fulfilled Promise.
It ignores rejected Promises unless all Promises reject.

9). Promise.race()
Promise.race() returns the result of the first Promise that settles, whether it is fullfilled or rejected.

Promise Methods Comparision

Method                      Success Condition                     Failure Behaviour 
Promise.all()               All Promises succeed                  Rejects immediately if one fails
Promise.allSetteld()        Waits for all                         Never rejects because of individual failures
Promise.any()               First fulfilled Promise               Rejects only if all fail
Promise.race()              First settled Promise                 Returns whichever settles first (success or failure)

Frequently Asked Scenario

FAQ1. Difference between Promise.all() and Promise.allSettled()?
Ans: Promise.all() succeed only when every Promise succeeds. If even one Promise rejects, it immediately rejects.
Promise.allSettled() waits for all Promises to complete, regardless of success or failure, and returns the status of each Promise.

⭐⭐⭐⭐⭐ 10. JavaScript Async

1). What is async?
Ans: The async keyword is used to declare an asynchronous function.
An async function always returns a Promise, even if we return a normal value.
It allows us to use the await keyword inside the function.














Project Architectures :
1. Monorepo Architectures: 
		How the code is organized and managed.
		Monorepo = Repository strategy
    A monorepo (mono = single, repo = repository) is a developement setup where multiple applications and packages are stored in one Git Repository.
    Everything lives together:
    1. frontend apps
    2. backend services
    3. shared libraries
    4. UI Components
    5. tooling configs
    Monorepos is popular in large project because of
    1. duplicate code
    2. dependency mismatch
    3. difficult package publishing
		4. inconsistent tooling
		5. difficult refactoring
    Monorepos solve these issues.
    Monorepo Tools:
    1. Nx 							: Enterprise monorepo framework
    2. Turborepo				: Fast builds / caching.
    3. pnpm workspaces 	: Workspace dependency managment.
    4. Lerna 						: JS package managment.
    5. Bazel 						: Massive-scale builds.
    
    apps/
 ├── web
 ├── admin

packages/
 ├── ui
 ├── auth
 ├── config
 └── types
 
 		Problems with Monorepos:
    1. Large Repository Size.
    2. Complex CI/CD
    3. Team Ownership Issues
    4. Requires Good Architecture
    

2. MICROFRONTEND ARCHITECTURE :
		A Microfrontend architecture where frontend application broken into multiple independently developed frontend applications.
    Inspired my microservice architecture. instead of One gaint frontend app you have:
    1. Search APP
    2. Cart app
    3. checkout app
    4. profile app
    Each managed by separately.
    
		How the frontend application are architected and deployed.
		Microfrontend = Frontend architecture strategy. 
    Why Microfrontend Exits:
    As frontend app grows problems will apper like:
    1. deployment become risky
    2. teams block each other
    3. codebase become huge.
    
    Example E-commerce platform.
    Diffent team own:
    1. product catalog
    2. recommendation
    3. cart
    4. payments
    5. account management.
    Instead of one massive app each domain becomes independent.
    
    Core characteristics of Microfrontends
    1. Independent Teams
    2. Independent Deployment.
    3. Runtime Composition. (Microfront combine at runtime Main shell app loads all these)
    4. Techonology Independence. (We can use diff tech in eact app)
    
    Microfrontend Architecture Styles:
    1. Build-Time integration:
    2. Runtime Integration
    3. iframe based
    4. Web component 
    5. Module Federation (Most popular)
    
    Communication Between Microfrontends
    This becomes difficult.
    Methods:
    1. shared state.
    2. event bus
    3. URL based communication
    4. custom events
    5. redux stores
    
    Problems with Microfrontends:
    1. Massive complexity
    2. Hard debugging
    3. Performance Overhead
    4. Developer Experience
    5. UI Consistency

3. Microservices: 
		Microservices are same like Microfrontend, we can use microservices for the BE to separate each services separately.

We can use: 
	Microfrontend for Frontend
  Microservices for Backend
  monorepo for managing everyting together.
  
** Module Federation
		Module federation is runtime code sharing mechanism introduced in webpack 5.
    Module federation used to load the code from multiple project to one project at runtime.
    4. Core Concepts
    1. Host: (Main App) The main app that loads other apps.
    2. Remote App: 
    3. Exposed modules: Remote apps decide what to share.
    4. Shared Dependencies (Common libraries are shared dynamically.)






****************************************** Telemetry *********************************************************

1. Telemetry: automatic collection of data from systems or application to understand behaviour, performance and usage.

We are useing GTM for the Product / User Telemetry.
		*. User clicks, page views, form submissions.
    *. Used by product. marketing, analytic teams.
    GTM belongs to mostly for product telemetry.

2. What is the Google Tag Manager (GTM)
		GTM is tag management system that lets you add tracking scripts and analytics event without changing application code repeatedly.
    Explanation: 
    Add tracking from dashboard.
    Trigger events based on user actions
    Send data to analytics tools.
    

        
*** Explain in interview.
		I have implemented frontend telemetry in React using Google Tag Manager to track user interactions vie dataLayer events and send them to google analytic.
    
    1. What is the frontend telemetry ?
    Collecting user interaction data from browser to understand user behaviour.
    
    2. How the GTM flow.
    Step by step: 
    	1. User interact with UI (button click, opens page, submit form)
      2. React triggers GTM event. (vie. datalayer.push())
      3. GTM listens for that event
      4. GTM fires tag.
      5. Event is sent to analytics.
      
    3. Core concept.
    Data Layer (IMP)
    GTM works using global object.
    window.dataLayer
    you push events like:
    window.dataLayer({
    event: "button_click",
    button_name: "signup"
    })
    
    This is the bridge between react and GTM.
    
    4. Why GTM is used in FE ?
    	Without GTM: 
      	Every new event requires code changes.
        Redeploy react app
      Without GTM:
      	Events controlled from GTM dashboard.
        No code changes needed for new tracking.
        
** Cross question:
		1. Why did you use GTM instead of directly calling GA?
    		GTM provides flexibility. Instead of hardcoding analytics call in React, we centralize tracking logic in GTM.
        
    2. What is the dataLayer:
    		It is global JavaScript array used by GTM to pass event data from the application to  GTM.





        
******************************************** Pendo *******************************************

One major advantage is that after integration, Pendo can automatically capture a lot of user interaction data without requiring developers to instrument
every event manually. Is also provide product analytics,  user segmentation, and in-app guides from a single platform.

1. How it's diffrent from google analytics ?
		Google analytic focuses more on website trafic and event analytics, whereas Penod is focused on understanding product usage inside an application. 
    Pendo also provides in-app guidence, feature adopting tracking, and user onboarding capabilities.
    
    Worked on frontend telemetry and analytics integrations using Google Tag Manager, Google Analytics, and Pendo. Responsible for integrating
    tracking scripts, user identification, and supporting product analytics initiatives.
    
    After integrating Pendo in the application, in-app guides and onboarding flow were configureed through the Pendo dashboard, and they are automatically 
    appeared in the application based on user segmentation and behaviour rules, without requires additional code deployments. 

		Pendo allows us to define targeting rules for each guide. We can control who sees the guide based on user attributes like new or existing users, role,
    account type, or behavior. For example, onboarding flows can be shown only to new users, while feature announcements can be shown to all users, and 
    contextual tips can be shown based on user actions or page visits






*************************************** Intro **************************************88

Hi, I'm [Your Name]. I have around 4 years of experience in software development, primarily working with React, Next.js, React Native, TypeScript, 
Node.js, NestJS, and MongoDB.

I've worked on enterprise-level web and mobile applications, developing features across both frontend and backend. My primary expertise is in React,
Next.js, and React Native, but I've also worked on API development using Node.js and NestJS.

Additionally, I've worked with Google Tag Manager, Google Analytics, Sentry, and have some exposure to Google Cloud services and Firebase.

I'm currently looking for opportunities where I can contribute to building scalable applications and continue growing as a Full Stack Developer.





***************************************************************** React ************************************************

1. What is the diff between real DOM and virtual DOM ?
Ans: The Real DOM is Actual DOM (Document Object Model) that maintained by Browser, Every HTML element is represented as node, and JavaScript can directly
manipulate these nodes. Directly update to it can be expensive because they may trigger layout and repaint operations.

The Virtual DOM is a lightweight copy of Real DOM that maintained by React. When the application state changes, React update the virtual DOM first, Compare
it with the previous version. (a process called diffing), and update only changed part of real DOM.

Browser creates the real DOM after loading HTML page.

I) Why Is Virtual DOM faster ?
Ans: Virtual DOM is not always faster, but that reduces unnecessary Real DOM operations.

Interview Cross Questions:

Q1. Is Virtual DOM part of JavaScript ?
Ans: No, Virtual DOM is not part of JavaScript. It is an implementation used by libraries like React.

Q2. Who creates the Real DOM ?
Ans: The browser creates the Real DOM after parsing the HTML.

Q3. Who creates the Virtual DOM ?
Ans: React create and managed virtual DOM

Q4: Does React update the Real DOM directly ?
Ans: No, React first update virtual DOM, compare it with previous version, and then applies only the necessary changes to real DOM.

Q5. What is the Diffing ?
Ans: Diffing is the process of comparing the old virtual DOM with new virtual DOM to determine what has changed.

Q6. What is the Reconciliation ?
Ans: Reconciliation is the overall process React uses to update the UI. It includes diffing the Virtual DOM and applying the minimal required updates to the 
real DOM.

Q7. Why is the Real DOM considered expensive ?
Ans: Because changes to the Real DOM may trigger layout calculations, repainting, and rendering, which are more costly than JavaScript objects.

Q8. Does React update whole page when state change ?
Ans: No. React updates only the parts of the Real DOM that have actually changed.

Q9. Can JavaScript manipulate Real DOM without React ?
Ans: yes.


2.) What is the difference between React.memo, useMemo and useCallBack ?
Ans: The key is to understand what each one memorize.
i) React.memo	 : (Component) Prevent unnecessary component re-rendering.
ii) useMemo  	 : (Value) Prevent expensive calculations from running again.
iii) useCallback : (Function) Prevent function recreation on every render.

Think of it this way:
React.memo --> Memorize a Component.
useMemo    --> Memorize a Value.
useCallback--> Memorize a Function.

*** React.memo:
What is the React.memo ?
Ans: React.memo is a Higher order component that prevent a function component from re-rendering if its props have not changed.
Without React.memo, when a parent component re-renders, all child component also re-render, event if there props are unchanged.
 
How React.memo works ?
Ans: React perform shallow comparison of the previous props and the new props. 
If they are equal then skip re-rendering Otherwise render again.

When to use React.memo ?
Ans: Child component are expensive to render.
Parent updates frequently.
Child props rarely change.

*** useMemo
What is useMemo ?
Ans: useMemo memorize the result of calculation.
Instead of recalculating every render, React returns the cached value until one of the dependencies changes

When to use useMemo ?
Ans: Sorting large array.
Filtering data.
Complex calculations
Heavy computations

*** useCallback
What is the useCallback
useCallback memorize a function.
Normally every render creates a new function object. Every render create a new function instance

Feature			React.memo		useMemo				useCallback
Memorize 		Component		Value				Function
Prevents		Components re-render 	Expensive Recalculation		Function recreation
Returns			Component		Any Value			Function
Common use 		Child Component		Heavy computations		Event handlers passed as props.

***** Common Cross Question.

Q1. What is the memorization ?
Ans: Memorization is an optimization optimization technique where result of a computation is cached and reused instead of recomputing it until its dependencies
change.

Q2. Does React.memo prevent all re-renders ?
Ans: No. It's only skip re-render when the component's props are shallowly equal. It does not stop re-renders caused by the component's own state changes or
context updates.

Q3. Does useMemo improves performance in every case ?
Ans: No. It also has a cost because React must store the cached value and compare dependencies. Use it for expensive computations, Not for simple expression.

Q4. Why do we use useCallback with React.memo ?
Ans: because React.memo compares props by reference. without useCallback, a new function is created on every render, so the memorized child still sees it's
function prop as changed and re-renders.

Q5. Can useCallback replace useMemo ?
Ans: No. useCallback memorizes a function, while useMemo memorizes the result of a computation.

Q6. Can React.memo work without useCallback?
Ans: Yes, but if you're passing functions as props, those functions will usually have new reference on every render. In that case, React.memo won't be able 
to skip the re-render. That's why React.memo and useCallback are often used together. 

Ready Ans ***********
React.memo memorizes an entire component and skips re-rendering when it's props haven't changed. useMemo memorizes the result of an expensive calculation, so
it isn't recomputed on every render. useCallback memorize a function, keeping the same function reference between renders until dependencies change. They are
often used together: React.memo for child components, useMemo for expensive derived values, and useCallback for callback props passed to memorize children. 




3) What is the React ?
Ans: React is open-source JavaScript library that developed by Facebook for building interactive and re-usable user interface, specially for single page 
application. React helps us to build web applications by breaking the UI into reusable components. Instead of manually manipulating HTML using JavaScript,
we are simply update the application's state, and React automatically update UI.

Cross Questions

i) Why React is called library instead of framework ?
Ans: React focuses only on building the user interface.
It does not provide the build in solution for:
Routing,
State Management,
HTTP Request,
Form Validation

Developer choose there own libraries.
Angular, on other hand, provide these all feature out of the box, so it is consider as Framework.


ii) What problem does react solve ?
Ans: Before React: 
document.getElementById('name').innerHTML = "John";

Developers manually updated the DOM.
In large applications: 
Difficult to maintain, duplicate code, performance issues, hard to track UI changes.
React Introduced : Component Architecture, Declarative UI, Virtual DOM, Efficient Updates.


iii) What is SPA ?
Ans: SPA Stands for single page application.
Browser loads one HTML page initially.
Later, React updates only the required parts of the page without reloading the entire page.

iv) Is react only for SPA ?
Ans: No, React can be used for: 
Single page application
Multi-page application
Dashboards
Admin Panels
E-commerce Website
Mobile application using React Native

4***) What are the Advantages of react ?
Ans: It uses a component based architecture, allow us to create reusable and maintainable UI components. 
React uses virtual DOM, which update only the changed elements, improving rendering performance.
React support one way data flow, making state changes predictable and easier to debug.

Cross Questions *************88

i ) What is the Component-Based Architecture ?
Ans: Instead of writing one large HTML page, we divide the UI into smaller reusable components.

5***) What is JSX ?
Ans: JSX stands for JavaScript XML. It is a syntax extension for JavaScript that allow us to write HTML-like code inside JavaScript.
During, compilation, Babel converts it into React.createElement() calls, which React uses to crate the virtual DOM.

Cross Questions

i ) Is JSX mandatory ?
Ans: No, React can written without JSX using React.createElement(), but JSX makes code much cleaner and easier to maintain. 

6***) Why do we use keys in React Lists ?
Ans: Keys uniquely identify list items so React can efficiently update only the changed element during reconciliation, improving performance and preserving 
component state.

7***) What is Reconciliation ?
Ans: Reconciliation is React's process of comparing the old and new Virtual DOM after a state or prop change. Using it's diffing algorithm, React updates only
part of real DOM that have changed, making rendering efficient.

Cross Questions

i ) What is Diffing ?
Ans: Diffing is the algorithm React uses during reconciliation to compare two virtual DOM trees and determine the minimal set of DOM updates.

ii ) What assumptions does React's diffing algorithm make?
Ans: 1. Elements of different types produce different trees.
2. Developers provide stable key props to identify children lists.

iii ) How do keys help reconciliation?
Ans: Keys allow React to match list items between renders. With stable unique keys, React can identify which items were added, removed, or moved, resulting in
fewer DOM operations and preserving component state.

1. *** React Component ***

1***) Difference between functional and class component ?
Ans: Functional Component are JavaScript Function that return JSX and use Hooks for state and side effects. Class Component use ES6 classes, lifecycle methods,
and this.useState(). Functional Component are preferred in modern React because they are simple, more readable, and align with current React best practices. 

Functional 				Class
JavaScript Function			ES6 class
Uses Hooks 				Uses Lifecycle Method
No this keyword				Uses this
Less code 				More boilerplate
Better readability 			More complex
Recommended in modern React		Mainly used in legacy projects

2***) Why are Functional Component preferred ? 
Ans: They reduce boilerplate, eliminate the need for this, support Hooks, encourage reusable logic through Custom Hooks, and are the recommended approach for
new React Application.

3***) What are Pure Component.
Ans: Pure Component is Class Component that perform a shallow comparison for props and state to skip unnecessary re-rendering. In Functional Components, the 
equivalent optimization is React.Memo.  

Cross Questions:

i ) What is shallow comparison?
Ans: It's compare only first level of values or object references, not deeply nested properties. 

4***) Difference between props and state ?
Ans: Props are read-only values that passed from parent component to child component, while state is owned and updated by the component itself. Props enable 
communication between components, whereas state manage dynamic data within the component.

3. *** React Hooks ***

1***) What are Hooks?
Ans: Hooks are special function that introduce in React 16.8 that allow function component to use React features such as state, lifecycle method, refs without
writing class component.
Before Hooks these feature are only available in Class Components. Hooks make code simple, reusable , and easier to maintain.

2***) useState ?
Ans: useState is a Hook that adds state to Functional Components. It's return the current state value and setter function. Calling the setter schedules a 
re-render with updated state.


Cross Question 

Q1 ) How does useState work ?
Ans: When a component renders for the first time, React stores the initial state internally.
On subsequent renders, React return current stored state instead of reinitializing it.
When the setter function is called, React updates the stored state, schedule a re-render, and the component receives the latest state value on the next render.

Q2 ) Why is state update asynchronous?
Ans: React schedules and batches state updates to improve performance by reducing unnecessary re-renders. Because of this, the updated value is available on
the next render rather than immediately after calling the setter.

Q3) Why shouldn't state be modified directly?
Ans: React relies on immutable update to detect changes. Directly mutating state can prevent React from recognizing updates, resulting in stale UI and 
rendering bugs.

3***) useEffect ?
Ans: useEffect is used for side effects such as API calls, subscriptions, timers, and event listeners. It runs after React updates the DOM, and its execution
depend on the dependency array.

Cross Question.

Q1) What is a Cleanup Function?
Ans: Cleanup Function is returned from useEffect and is executed before the effect runs again and when the component unmounts. It is used to clean up resources
like event listeners, timers, or socket subscriptions.

Q2) When is cleanup executed?
Ans: Before the effect runs again (If dependency changed)
When the component unmounts 

Q3) Why cleanup important ?
Ans: To prevent: Memory leak, duplicate event listener, unnecessary API polling, stale subscriptions.

4***) What is useRef ?
Ans: useRef stores a mutable value or DOM reference that persists across renders without causing a re-render when updated.

Cross Question:

Q1) Why use useRef ?
Ans: Access DOM element, Focus an input, Store previous values, Store interval or timeout IDs, Keep mutable values between renders without triggering a 
re-render.

Q3) Difference Between useRef and useState
Ans: useState manages data that affects the UI and triggers re-renders when updated. 
useRef stores mutable values that persist across renders but do not trigger re-renders.

useState 				useRef
Trigger re-render 			No re-render
Stores UI state				Stores mutable values or DOM references 
Uses setter function			Update ref.current directly 
Causes component update			Does not cause component update.

5***) Custom Hooks:
Ans: Custom Hook is a reusable function that starts with use and encapsulates shared stateful logic using React Hooks. It improves code reuse while keeping
each component's state independent. 

Cross Question
Q1. Why should the function name start with use?
Ans: React relies on this naming convention so linting tools can enforce the Rules of Hooks and developer can easily recognize Custom Hooks.

4. *** React Rendering ***

1***) What is Rendering in React ?
Ans: Rendering in React is process of executing a component function to generate a React element tree. React then compare this new Virtual DOM with the 
previous one using reconciliation process and updates only the necessary parts of real DOM.
It's important to understand that a component re-rendering does not necessarily mean the real DOM is updated. React first perform reconciliation and only if 
its find difference does it updates the real DOM.

5. *** React Lifecycle ***

1***) What is the React Component Lifecycle ?
Ans: The React Component Lifecycle describe the different phases a component goes through from creation to removal.
In Class Components, this phases are handled using lifecycle methods such as componentDidMount, componentDidUpdate, and componentWillUnmount.
In Functional Components, we achieve the same behaviour using the useEffect hook with different dependency arrays and cleanup Functions.

2***) componentDidMount (Using Hook)
Ans: componentDidMount is called only once after a component is mounted to the DOM.

3***) componentDidUpdate (Using Hook)
Ans: componentDidUpdate runs after a component updates due to changes in state or props.

4***) componentWillUnmount (Using Hook)
Ans: componentWillUnmount executes just before a component is removed from the DOM.

Cross Questions
Q1. When is cleanup executed?
Ans: Before the component Unmount. 2. Before the effect runs again when dependencies change.

Q2. Can useEffect replace all lifecycle methods ?
Ans: There are lifecycle methods like getSnapShotBeforeUpdate and shouldComponentUpdate that don't have direct hook equivalents. Similar behaviour is achieved
with other React APIs such as React.memo, useLayoutEffect. depending on use cases.

Q3. Diff between useEffect and useLayoutEffect ?
Ans: 
useEffect						useLayoutEffect
Runs after the browser paints the screen		Runs synchronously after the DOM updates but before the browser paints.
Doesn't block painting 					Blocks painting until it finishes.
Used for API calls, subscriptions, timers 		Used for DOM measurements or preventing visual flicker.

useEffect runs after browser has painted the updated UI, making it suitable for most side effects such as API calls, subscriptions or timers.
useLayoutEffect run synchronously after React Updates the DOM but before the browser paints the screen. It's mainly used when you need to measure or modify
the DOM before the user sees it, such as calculating element sizes or adjusting scroll positions.

6. *** State Management ***

1***) What is the state management ?
Ans: State management is process of storing, updating, and sharing data across different component in application.
React provide local state using useState, but as application grow, multiple component often need access to the same data, such as user information, 
authentication status or application setting.
To avoid problem like prop drilling and to centralize shared data, we use state management solutions such as context API, Redux Toolkit, Zustand, or MobX.

Types of state
Type 					Exm.
Local state 				Input field, Modal Open/Close
Global State				Logged-in user, Theme, Cart
Server State 				API Data.

2***) What is Context API ?
Ans: Context API is React's in-build mechanism for sharing values across components without prop drilling. It's best suited for relatively stable global
data such as authentication, theme, or language preference.
Context itself is not a complete state management library. It only provides way to pass values through the component tree.

Advantages: Built into React, No Extra Library, Eliminates Props Drilling, Easy to use.

Limitations: Frequent update can cause many components to re-render.
Lacks built-in middleware and developer tools
Less suitable for large, complex application.

Cross Questions
Q1. Does Context replace Redux?
Ans: No, Context solves props drilling, while Redux provides a structured approach for managing complex global state with predictable updates and powerful
tooling.

3***) Redux ?
Ans: Redux is predictable state management library that stores global state in a centralize store.
Component Dispatch actions, reducers update the state, and subscribed components receive the updated values.

Core Concepts

Store: Stores the application's state.
Action: Describes what happened.
Reducer: Updates state based on the action.

4***) Redux Toolkit (RTK)
Ans: React Toolkit is official way to write Redux application. It simplifies Redux by reducing boilerplate, provide utilities like createSlice and 
configureStore, and handling immutable updates internally with Immer.

Benefits: Less boilerplate, Easier Setup, Better readability, Built-in Immer, Recommended by Redux maintainers. 

Cross Questions

Q1. Why Redux Toolkit instead of Redux ?
Ans: Because it's reduce boilerplate, simplifies configuration, and it's officially recommended approach.

Q2. What is the creatSlice ?
Ans: It automatically generates: Reducers, Action creators, Action types. From a single definition.

Q3. What is the configureStore? 
Ans: It creates the Redux store with sensible defaults, including good middleware and DevTools support.

5***) Zustand
Ans: Zustand is a lightweight state management library for React.
It provide simple API using Hooks and does not requires reducers, actions, or providers.
Zustand is easier to learn that Redux and is the well suited for small to medium sized application or projects
 that need global state without Redux's complexity.

Advantage: Minimal boilerplate, No Providers Required, Fast, Hook based API, Easy to use.

Cross Questions
Q1. Is Zustand faster than Redux?
Ans: It can have less overhead for many use cases because components subscribe only to the parts of state they use. 
The right choice depends on the application's requirement.

6***) MobX
Ans: MobX is state management library based on observable.
Instead of dispatching actions and writing reducers, MobX automatically track which 
observable state a component uses and re-render only those components when the state changes.

Advantage: Less Boilerplate, Automatic reactivity, Easy to update state, Good performance. 
Limitations: Different mental model, Less common in modern React project than Redux Toolkit and Zustand.

7***) Context API vs Redux Toolkit
Ans: Context API is primarily for avoid prop drilling and sharing simple global values.
Redux Toolkit is a full-featured state management solution with a centralized store, predictable updates,
middleware, and excellent debugging support, making it better suitable for large and complex application.

7. *** Redux Interview Questions ***

1***) What is Store?
Ans: The store is central object in Redux that holds the application's global state.
There is a typically single store for the application. Component reads state from the store and dispatch
the action to update it.

Cross Questions
Q1. Can Redux have multiple stores?
Ans: Technically yes, but generally it's bad way.

Q2. Who update the store ? 
Ans: Reducers update the store after processing dispatch actions. 

2***) What is the Action ?
Ans: Action is plain JavaScript object that describes what happened in the application.
Every action must have a type property. It can also include additional data, usually called payload.

Cross Questions

Q1. Can Action update state ?
Ans: No, Action only describe what happened. Reducers actually update the state.

Q2. Why does every action need type ?
Ans: Because reducer use the action type to determine how the state should change.

3***) What is the Reducers ?
Ans: Reducer is pure function that receives current state and an action, then returns 
a new state based on action.
Reducers should not mutate the existing state. Instead, they return a new state object.

Cross Questions
Q1. Why is reducers called pure function ?
Ans: Because: Same Input --> Same Output
No API Calls, No Timers, No DOM manipulation, No side effects

4***) What is Dispatch?
Ans: Dispatch is method used to send an action to the Redux store.
When dispatch() is called, Redux sends the action through middleware, then to reducers, which update the store.

Cross Questions

Q1. Does dispatch update state directly?
Ans: No, dispatch sends an action. Reducer update the state.

5***) What is Middleware ?
Ans: Middleware sits between dispatch() and the reducer.
It intercepts dispatched actions and allows us to perform additional logic such as logging, API calls,
authentication checks, or asynchronous operations before the action reaches the reducer

Cross Questions
Q1. Why do we need middleware ?
Ans: Because reducer must remain pure and should not contain side effects.

Q2. Name some Redux middleware.
Ans: Redux Thunk, Redux Saga, Redux Logger.

6***) What is the Redux Thunk ?
Ans: Redux Thunk is middleware that allows action creators to return a function instead of a plain action object.
This function receives dispatch  and getState, enabling asynchronous operations such as API calls before 
dispatching regular action.

Cross Questions
Q1. Why can't reducer perform API calls?
Ans: Because reducer must remain pure and synchronous. 

Q2. What does Thunk receive ?
Ans: (dispatch, getState)

7***) What is RTK Query?
Ans: RTK Query is data fetching and caching solution built into Redux Toolkit.
It simplifies API calls by automatically handling data fetching, caching, loading states, error states, cache invalidation,
and re-fetching.
It eliminates much of the boilerplate traditionally required with Redux Thunk for server side data.

Advantages: Automatic caching, Automatic loading state, Automatic error handling, Cache invalidation, Less boilerplate, 
Background re-fetching.

Cross Question:

Q1. Does RTK Query replace Redux Thunk ?
Ans: For most API data fetching, yes. RTK Query is the recommended choice because it provides built-in caching and 
request management. Redux Thunk is still useful for other asynchronous business logic that isn't centered around 
fetching server data.

8. *** React Forms ***

1***) What are the Forms in React ?
Ans: Forms in React are used to collect user input such as login credentials, registration details, search query,
or contact information.
React provides two approaches for handling forms:
1. Controlled Components.
2. Uncontrolled Components
In modern react applications, Controlled Component are more common because they provide better control over form
data and validation.

2***) What are Controlled Components?
Ans: Controlled Component is a form element whose value is controlled by React state. The input value is stored in 
state using useState, and every change updates the state through an onChange handler.
Since React owns the form data, it becomes easier to validate, reset, and manipulate the form.

Advantage: Easy Validation, Easy error handling, Easy reset, Predictable state, Better Debugging.

Cross Questions
Q1. Why are Controlled Components preferred?
Answer: Because react always knows the latest form values, making validation, conditional rendering, and 
form submission much easier.

3***) What are Uncontrolled Components?
Ans: Uncontrolled Components store its value inside the DOM instead of React state.
React accesses the input value using a ref when needed.
Since React doesn't manage the value of every keystroke, uncontrolled components generally trigger fewer re-renders.

Advantage: Simpler for very basic forms, Fewer re-renders, Easy integration with non-React code.
Limitation: Harder validation, Less Control, More difficult to manage complex forms.

4***). Difference Between Controlled and Uncontrolled Components
Controlled 				Uncontrolled 
React controls data 			DOM controls data
Uses useState				Uses useRef
Re-render on input changes		No re-render on every keystroke
Easier Validation 			Harder Validation
Recommended for most forms		Better for simple forms or file inputs

5***) Form Validation
Form Validation insure that user input meets bussiness and data requirement before submission.
Validation can occur: On every input change
On blur (when leaving a field)
On form submission
Common validation rules include required fields, email format, password lenght, minimun and maximum values, 
and custom business rules.

Cross Questions
Q1. Client-side vs Server-side validation ?
Ans: Client side validation improves user experience by catching obvious error early, but server-side validation 
is still required because client-side checks can be bypassed.

Q2. Why is server-side validation still necessary ?
Ans: Because users can modify requests or bypass client-side validation, so the server mush always validate incoming data.

6***) React Hook Form ?
Ans: React form hook is a lightweight library for handling forms in React.
It uses uncontrolled inputs internally with refs, which significantly reduces unnecessary re-renders compared to 
traditional controlled forms.
It provides built-in validation, error handling, form state management, and integrates easily with schema validation
library such as Yup and Zod.

Advantages: Very few re-renders, Built-in validation, Smaller bundle size,  Easy integration with Yup and Zod.
Better performance for large forms.

Cross Questions

Q1. Why is React Hook Form faster?
Answer: Because it primarily uses uncontrolled inputs with refs instead of updating React state on every keystroke, 
Resulting in fewer component re-renders.

Q2. Can React Hook Form validate forms?
Ans: Yes, It supports: Required, Min/Max length, Pattern matching, Custom validation, Yup, Zod.

Frequently Asked Scenario
Interviewer

Why would you choose React Hook Form instead of useState?
Ans: For small form with just some fields, useState is perfectly fine and keeps the implementation straightforward
For large forms, I prefer React Hook Form because it minimize unnecessary re-renders, provides built-in validation, 
simplifies form state management, and integrates well with validation libraries like Yup and Zod. This results in 
better performance and cleaner, more maintainable code.

9. *** React Performance Optimization ***

1***) What is the performance optimization in React ?
Ans: Performance optimization in React means improving an application's speed, responsiveness, and resource usage by
 reducing unnecessary rendering, minimizing bundle size, and loading only the required resources.

Common optimization technique:
Lazy loading, Code Splitting, React.lazy, Suspense, Memorization, Image Optimization, Bundle Optimization.

2***) Lazy Loading?
Ans: Lazy loading is technique where components or resources are loaded only when they are needed instead of 
loading everything during the initial page load.
This reduces the application's initial bundle size and improve first page load performance. 

Advantages: Smaller initial bundle, Faster first load, Better user experience, Less memory usage.

Cross Questions
Q1. Does lazy loading improve SEO?
Ans: For client-side rendered React applications, lazy loading primarily improves performance.
SEO depends on the rendering strategy (CSR vs SSR/SSG). In frameworks like Next.js, SSR, and SSG provide better SEO.

Q2. When should we use Lazy Loading?
Ans: Large pages, Dashboards, Admin panels, Heavy components, Feature modules, Route-based loading

3***) Code splitting ?
Ans: Code splitting is process of dividing a large JavaScript bundle into smaller chunks that can be loaded on 
Demand.
Instead of downloading the entire application at once, React downloads only the required code for the current
page or feature.

Cross Questions

Q1. Difference between Lazy Loading and Code Splitting?
Ans: Code splitting is process of breaking code into multiple bundles.
Lazy Loading is the technique of loading those bundles only when needed.

Q2. Which React feature enables code splitting ?
Ans: Dynamic import() together with React.lazy.

4***) React.lazy?
Ans: React.lazy is a React API used to dynamically import components. 
Instead of including a component in the initial bundle, React downloads it only when it rendered. 

Cross Questions

Q1. Can React.lazy load named exports?
Ans: Not directly, React.lazy expects a module with a default export. For named exports, you need 
to map them to a default export during the dynamic import.

Q2. Does React.lazy work without Suspense?
Ans: No, Lazy-loaded component must be wrapped in <Suspense>

5***) Suspense ?
Ans: Suspense is React component used to display fallback content while waiting for a lazy-loaded 
component to finish loading.
It provides a better user experience by showing loading indicators instead of a blank screen.

Cross Questions

Q1. Why Suspense is required ? 
Ans: Because Lazy-loaded components are downloaded asynchronously, React needs fallback UI while waiting.

6***) Image Optimization
Ans: Image Optimization improves application performance by reducing image size, loading images efficiently, and 
serving the appropriate image for each device.
Common technique :
Compressing Images, Using modern formats like WebP or AVIF, Lazy loading images, Serving responsive image sizes, 
Using optimized image components (Such as Next.js Image)

Benefits: Faster loading, Less bandwidth usage, Better Core Web Vitals, Improved user experience.

Cross Questions

Q1. Why use WebP?
Ans: Because it generally provides much smaller file sizes than JPEG or PNG while maintaining similar visual quality.

Q2. Why should not we load full size images ?
Ans: They increase bandwidth usage and slow down page loading.

7***) Bundle Optimization.
Bundle optimization reduces the size of JavaScript, CSS, and other assets downloaded by the browser.
A Smaller bundle improves initial page load time and overall application performance.

Common techniques.
Code splitting, Lazy loading, Tree Shaking, Removing unused dependencies, Dynamic imports, Minification, Compression, 
Image Optimization.

Cross Questions

Q1. What is Tree Shaking?
Ans: Tree Shaking removes unused JavaScript code during the production build, reducing bundle size.

Q2. What tools can analyze build size?
Ans: Webpack Bundle Analyzer and similar tools provided by modern build system like Vite or Next.js integrations.

Frequently Asked Scenario
Interviewer

Your React application loads slowly. What optimizations would you perform?
Ans: I would first analyze the application's bundle to identify large dependencies. Then I'd implement route-based
code splitting and lazy loading for heavy modules, optimize images using modern formats and responsive sizing, remove unused
dependencies, enable tree shaking, and memorize expensive components where appropriate. I'd also review unnecessary re-renders
using React DevTools Profiler and ensure only the required data and assets are loaded initially.

Q1. What is Tree Shaking?
Ans: Remove unused code from the production bundle.

10. *** React Error Handling ***

1***) What is error handling in React ?
Ans: Error handling in the React is the process of detecting, managing and covering from error so that the application 
remains stable instead of crashing completely.
React application can encounter different types of errors, like
Rendering Errors, JavaScript runtime errors, API errors, Network failures, Asynchronous errors.
React provides Error Boundaries for UI rendering errors, while JavaScript's try...catch and async error handling are used 
for synchronous and asynchronous operations.

2***) What is an Error Boundary ?
Ans: Error boundary is React Component that catches rendering errors in its child components and displays a fallback UI 
instead of allowing the entire application to crash.

Advantages: Prevent entire application crash, Displays fallback UI, Logs errors, Improves user experience.

Q1. Can Functional Components be Error Boundaries?
Ans: Not directly, React currently requires class Component to implement an Error Boundary.

3***) What Errors Do Error Boundaries Catch?
Ans: It catches errors during rendering, lifecycle methods, and constructors of child components. It does not catch API 
errors, event handler errors, or other asynchronous errors.

4***) What is Try...Catch?
Ans: try...catch is JavaScript's built-in error handling mechanism for synchronous code. It is also commonly used with
 async/await to handle asynchronous error.

Cross Questions
Q1. Does try...catch catch async errors automatically?
Ans: No, For async functions, use await inside try block or handle rejected Promises with .catch().

5***) Async Error Handling
Asynchronous operation such as API calls can fail due to network issues, server errors, on invalid responses.
We handle these errors using try...catch with async/await or by attaching a .catch() handler to Promises.

Cross Questions
Q1. Why use try...catch with async/await?
Ans: Because it makes asynchronous error handling easier to read and maintain compared to chaining multiple 
.then() and .catch() calls.

Q2. What if we don't catch API errors?
Ans: The promise rejection can go unhandled, leading to console errors and poor user experience.

6***) Common Error Handling Strategies
In production applications, I usually follow these practices:
Use Error Boundaries for rendering errors.
Use try...catch for synchronous operations.
Use try...catch with async/await for API calls.
Display user-friendly error messages instead of raw exceptions.
Log error to monitoring tool such as Sentry or similar services.
Provide retry options for recoverable failures.

Error Boundary vs Try...Catch
Error Boundary 					Try...Catch
React feature					JavaScript feature
Catches rendering error 			Catches synchronous exceptions
Shows fallback UI				Handles code exceptions errors
Cannot catch API errors 			Can handle API calls with async/await
Class Component implementation 			Works in any JavaScript code.
Error boundary protect the React UI from rendering errors by showing fallback content, while try...catch handles
JavaScript expressions and asynchronous operations such as API calls. They solve different problems and are often
 used together in a production React application.

Async/Await vs Promise.catch()
async/await					Promise.catch()
Cleaner syntax					Chained syntax
Uses try...catch 				Uses .catch()
Easier to read 					Fine for simple chains 
Preferred in modern React 			Still valid

Frequently Asked Scenario
FQ1. If your API fails, how will you handle it?
Ans: I use try...catch around asynchronous API calls, show a meaningful error message to the user, log the error for
 debugging, and provide a retry mechanism when appropriate 

FAQ2. What is componentDidCatch() ?
Ans: It is an error boundary lifecycle method used to log error details after a rendering error has been caught.

FAQ3. What is getDerivedStateFromError() ?
Ans: It updates the component's state so that fallback UI can be rendered after an error occurs.

FAQ4. Where should Error Boundaries be placed?
Ans: Around routes, Around feature modules, Around Dashboards, Around third party widget.

11. *** API Calls in React ***

1***) What is an API calls?
Ans: API call is a request from frontend to a backend server to retrieve or modify data. In React, API calls are commonly made with Fetch or Axios inside
useEffect or event handlers.

2***) Fetch vs Axios
Both are used to make HTTP requests. Fetch is a built into modern browsers and is suitable for many use cases, but it requires manual JSON parsing and
checking reponse.ok . Axios is third party library that automatically parses JSON, rejects non-2xx responses, supports interceptors, and simplifies request
configuration.

Comparison Table
Fetch 						Axios
Built in browser				External Library
No installation 				Installation Required
Manual response.json()				Automatically parses JSON
Doesn't reject on Http 404/500 automatically	Reject Promise for non-2xx responses
Supports AbortController			Support request cancellation
Smaller bundle					Slightly larger bundle

Cross Questions

Q1. Why does Axios feel easier?
Ans: Because, Automatically parsed JSON, Reject non-2xx responses, Supports interceptors, Has cleaner configuration for many projects

3***) Promises 
Promise is represents the eventual result of an asynchronous operation. It has three states: Pending, Fulfilled, Rejected.

Cross Questions: 

Q1. Can a fulfilled Promise become rejected?
Ans: No, Promise settles only once.

4***) async/await
async/await is a cleaner syntax built on top of Promises. that makes asynchronous code look and behave more like synchronous code. It improves readability
and makes error handling easier using try...catch.

Cross Questions

Q1. Does await block JavaScript?
Ans: No, It pauses only the execution of the current async function. The JavaScript event loop continues processing other tasks.

Q2. Is async/await faster than Promises?
Ans: No, It's syntactic sugar over Promises. The performance is generally comparable; the main advantage is readability.

Promise vs async/await
Promise 					async/await
Uses .then()					Uses await
Can become deeply nested			Cleaner and easier to read
Uses .catch()					Uses try...catch
Older syntax 					Modern preferred syntax

5***) AbortController
AbortController is used to cancel in-progress requests, especially when a component unmounted or a request is no longer needed. It's commonly used with
Fetch and is also supported by modern Axios versions.

Cross Questions:

Q1. Why use AbortController?
Ans: To, Cancel unnecessary requests, Prevent state updates after unmount, Reduce wasted network work, Improve use experience.

Q2. Does AbortController work with Fetch?
Ans: Yes, It is a standard cancellation mechanism for the fetch API.

Q3. Can Axios cancel requests?
Ans: Yes, Modern version of Axios support cancellation using AbortController as well.

Q4. Error Handling During API Calls
Ans: Every call should handle: Loading state, Success State, Error state, Cleanup or cancellation when appropriate.

Frequently Asked Scenario

FAQ1. What happens if the user leaves the page while an API call is still running?
Ans: If the request is no longer needed, I cancel it using AbortController in the useEffect cleanup function. This prevent unnecessary network activity and
avoids updating component state after it has been unmounted.

FAQ2. Can we make multiple API calls simultaneously?
Ans: Yes using Promise.all

FAQ3. What is Promise.all()?
Ans: It runs multiple Promises in parallel and resolves when all of them succeed. If any Promise reject, Promise.all rejects.

FAQ4. Difference between Promise.all() and Promise.allSettled()?
Promise.all					Promise.allSettled
Rejects if any Promise fails 			Waits for all Promises to settle.
Best when all requests are required 		Best when partial results are acceptable

FAQ5. Why should we avoid API calls inside render?
Ans: Because rendering should be pure. Triggering API calls during render can cause repeated requests and unpredictable behaviour.

FAQ6. How do you fetch data when a page loads?
Ans: I typically use useEffect with an empty dependency array so that data is fetched after the component mounts. Inside the effect, I use async/await with
try...catch for error handling, maintain error and loading states, and use an AbortController in the cleanup function it the request should be cancelled when
the component unmounts.

12. *** React Routing ***

1***) What is React Router?
Ans: React Router is the standard routing library for React applications. It enabled client-side navigation, allowing users to move between different pages
without reloading the entire browser. 
Instead of requesting new HTML page from the server, React Router updates the URL and renders the appropriate React component, providing a faster and smoother
user experience. 

Cross Questions: 

Q1. What is client-side Routing ?
Ans: Client-side routing means navigation happens inside the browser using JavaScript without requesting a new HTML page from server.

Q2. Difference between SPA and MPA?
SPA (Single page application ) 			MPA (Multi page application )
One HTML page					Multiple HTML pages
Faster Navigation				Full page reload
React Router 					Server-side routing
Better user experience 				Slower navigation

Q3. Why use React Router?
Ans: Faster Navigation, No full page reload, Better user experience, URL management, Route protection.

2***) BrowserRouter
Ans: BrowserRouter is the router implementation provided by React router that uses the HTML5 History API to keep the UI synchronized with browser URL.
It wraps the entire React application and enables routing functionality. All routes are managed inside a single BrowserRouter.

Cross Questions

Q1. Why do we wrap the app with BrowserRouter?
Ans: Because it provides routing context so all routing components (Routes, Route, Link, Navigate) can access navigation information.

Q2. What does BrowserRouter use internally?
Ans: It uses the browsers History API (pushState, replaceState) 

3***) Routes
The Route component contains all the application's route definitions. It checks the current URL and renders the first matching route.

Cross Questions
Q1. What replaced <Switch>?
Ans: Routes , React Router v6 replaced switch with Routes.

4***)  Navigate
Navigate is react router component used for declarative navigation or redirection. It commonly used for authentication and protected routes.

Cross Questions
Q1. When should we use Navigate?
Ans: Redirect after login, Protected Routes, Redirect after logout, Invalid routes.

Q2. What replaced Redirect?
Ans: Navigate, 

5***) useNavigate
useNavigate is a hook used for programmatic navigation. It allow navigation after performing an action such as form submission, login, or API success.

Cross Questions

Q1. Difference between Navigate and useNavigate?
Navigate				useNavigate
Component 				Hook
Declarative navigation			Programmatic navigation
Used in JSX				Used inside functions/ events

Q2. Can navigate go back?
Ans: Yes, with navigate(-1) Moves back one page

Q3. Can navigate replace history?
Ans: Yes, navigate('/login', {replace: true}) This replaces the current history entry instead of adding a new one.	

6***) Route Parameters
Route parameters are dynamic values passed through the URL. They are commonly used to identify a specific resource, such as a user ID or product ID.

Route Parameters vs Query Parameters
Route Parameters 			Query Parameters
/users/10				/users?id=10
uses useParams()			Uses useSearchParams()
Identifies a specific resource 		Used for filtering, sorting, pagination.

BrowserRouter vs HashRouter
BrowserRouter 					HashRouter
Uses History API 				Uses URL hash (#)
Cleaner URLs 					URLs contain #
Preferred for modern application		Useful on static hosting without server configuration

Frequently Asked Scenario

FAQ1. How do you protect routes?
Ans: By checking whether the user is authenticated before rendering the page.

13. *** React Testing ***

1***). What is testing in React ?
ANs: Testing is the process of verifying that React components and application logic work correctly.
It helps identify bugs early, ensure new changes don't break existing functionality, and increase confidence when deploying applications.
The two most commonly used tools are:
"Jest - Test Runner and Assertion Library", "React testing library- Library for testing React components by simulating user interaction"

Cross Questions
Q1. Why do we write tests?
Ans: Detect bugs earlier, Prevent regression, Improve code quality, Enable safe refactoring, Increase confidence before deployment.

Q2. What types of testing exist?
Ans: Unit testing, Integration Testing, End-to-End Testing.

2***) What is Jest?
Ans: Jest is JavaScript testing framework used to run tests, make assertions, create mocks, measure code coverage, and verify that application logic behaves
as expected.

Features: Test Runner, Assertion, Mock Functions, Snapshot Testing, Code coverage.

Cross Questions: 

Q1. What is expect()?
Ans: It is an assertion used to verify the expected result.

3***) What is React Testing Library (RTL)?
Ans: React Testing Library (RTL) is a library used to test React components by interacting with them the way a real user would.
Instead of testing implementation details, RTL focuses on user-visible behaviour such as rendering, clicking buttons, typing into imputs, and checking
displayed text.

Advantages: Encourage user-centric testing, Less coupled to implementation, Easy to maintain, Works well with Jest.

Cross Questions

Q1. Why use React Testing Library instead of Enzyme?
Ans: React Testing Library encourages testing from the user's perspective rather than inspecting component internals, making tests more reliable and less
brittle.

Q2. What does render() do?
Ans: It renders the component into a virtual DOM for testing.

4***) How do you test a React Component?
Ans: I generally follow these steps: 
	1. "Render the component"
	2. "Find elements using queries like getByRole or getByText."
	3. "Simulate user actions such as clicks or typing."
	4. "Verify the expected UI changes or function calls using assertions."

Jest vs React Testing Library
Jest 						React Testing Library
Test runner					Component testing library
Assertion 					Renders React Component
Mocking 					Simulates user interaction,
Coverage 					Queries DOM elements

Unit Testing vs Integration Testing vs E2E Testing
Unit Testing 				Integration Testing 					E2E Testing
Tests one function/component 		Tests multiple component together			Tests complete application
Fast					Medium 							Slow
User mocks frequently 			Some mocks 						Uses real browser
Example: Utility function		Login form with API mock				Login --> Dashboard flow


Frequently Asked Scenario

FAQ1. How would you test a Login component?
Ans: I would render the Login component using React Testing Library, verify that the email, password, and login button are displayed, simulate user input 
using userEvent.type(), click the login button, mock the API response, and then verify that the success message or navigation occurs. I would also test 
validation messages and API failure scenarios.

FAQ2. What is screen?
Ans: screen provided access to the rendered DOM using queries like getByText() and getByRole().

FAQ3. Why is getByRole() recommended?
Ans: Because it closely matches how uses and assistive technologies interact with the page, making tests more accessible and maintainable.

FAQ3. What is userEvent?
Ans: userEvent simulates real user interaction like typing, clicking, selecting options, and tabbing through element.

FAQ4. Difference between fireEvent and userEvent?
Ans: fireEvent					userEvent
Triggers a single event				Simulates realistic user interactions
Lower-level API 				Higher-level API
Less realistic 					More closely mimics browser behaviour 

FAQ5. What is Code Coverage?
Ans: Code coverage measures how much of your application code is executed during tests. It helps identify untested parts of the application.







































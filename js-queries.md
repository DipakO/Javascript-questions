https\://chatgpt.com/c/6a61c32f-51b0-83ee-8d5e-54fbf04dcbb2

https\://chatgpt.com/c/6a585d5f-17f4-83e8-ab3a-ca2261ef6753



1\. What is the Javascript ?

Ans: Javascript is the cross platform, object oriented scripting language which used to make webpages interactive.

     Old Name: LiveScript (Javascript has followed most of the java's naming convention, expression syntax that's why it's renamed LiveScript to Javascript)

     Javascript is a case-sensitive 

2\. Variable declaration in JS ?

Ans: JS has three type of variable declaration.

     1\. var: Declares a variable, optinally initializing it to value.

     2\. let: Declared a block-scoped, local variable, optinally initializing it to value.

     3\. const: Declared a block-scoped, read-only named constant.

     The names of variable called as identifiers.

     Scopes:

     1\. Global Scope: The default scope for all coding runing in script mode.

     2\. Module Scope: The scope for code running in module mode.

     3\. Function Scope: The scope created with function.

     4\. Block Scope: The scope is created with a pair of curly braces.

     Global Variable: When you declare variable outside of any funcation it is called global variable.

     Local Variable: If you have declare any variable inside the function then it's local variable.

3\. Data types in JS ?

Ans: THe latest ECMAScript standard defines eight data types:

  \* Seven data types that are primitives:

     1\. Boolean: True and False.

     2\. Null: A special keyword denoting a null value.

     3\. undefined: A top-level property whose value is not defined.

     4\. Number: An integer or floating point number. For example: 42 or 3.1235.

     5\. BigInt: An integer with arbitrary precision. For example: 9007199254740992n.

     6\. String: A sequence of characters that represent a text value. For example: "abc".

     7\. Symbol: A data type whose instances are unique and immutable.

  \* Object

4\. Conditional Statements in JS ?

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

5\. Loops and Iteration:

Ans: 1. For statement

     2\. do...while statement

     3\. while statement

     4\. labeled statement

     5\. break statement

     6\. continue statement

     7\. for...in statement

     8\. for...of statement

     1\. For statement:

     for loop repeats until a specified condition evaluate to false .

     2\. do...while statement:

     The do...while statement repeats until a specified condition evaluates to false.

     do 

      statement

     while (condition);

     statement is always exceuted once before the condition checked.

     If the condition true statement executes again. At the end of every execution, the condition is checked. When the condition is false, execution is stops.

     3\. While statement:

     A while statement executes its statement as long as a specified condition evaluates to true. 

     4\. labeled statement:

     A label provides a statement with an indetifier that lets you refer to it elsewhere in your program. For example you can use a label to identify a loop,

     and then use the break and continue statements to indicate where the program should interupt the loop or continue its execution.

     5\. break statement:

     Use a break statement to terminate the loop

     6\. continue statement:

     The continue statement can be used to restart a while, do...while, for, or label statement.

     7\. for...in statement:

     The for...in statement iterates a specified variable over all the enumerable properties of object.

     8\. for...of statement:

     The for...of creates a loop iterating over iterable objects (Array, Map, Set arguments)

6\. Functions:

    Functions are one of the fundamental building blocks in Javascript.It should take some input and return an output where there is an some obvious

    relationship between the input and output. 

    \* Function declarations:

    A function defination (also called as function declaration or function statement) consist of function keyword followed by the 

    \* The name of function

    \* A list of parameters to the function, enclosed in paranthesis and separated by commas.

    \* The Javascript statement that define the function, enclosed in curly braces.

    \* Recursion:

    A Function can refer to and call itself. It can be referred to either by function expression or declaration's name, or via any in-scope variable that

    refers to the function object.

    A function that calls itself is called recursive function. In some ways, recursion is analogous to a loop. Both execute the same code multiple times, and

    both require a condition.

    \* Immediately Invoked Function Expressions (IIFE)

    An IIFE is a code pattern that directly calls a function defined as expression.

    Instead of saving function in a variable, the function is immediately invoked. This is almost the eqvivelant to just writing the function body

    \* Closures:

7\. Expressions and operators:

    1\. Assignment Operators

    2\. Comparison Operators

    3\. Arithmetic Operators

    4\. Bitwise Operators

    5\. Logical Operators

    6\. BigInt Operators

    7\. String Operator

    8\. Conditional (ternary) Operators

    9\. Comma Operators

    10\. Unary Operators

    11\. Relational Operators

8\. Number and String

    We can use four type of number literals: decimal, binary, octal and hexadecimal.





\**\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\**\*\* JS Advance

⭐⭐⭐⭐⭐ 1. JavaScript Execution Context

1\*\*\*) What is Execution Context?

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

2\*\*\*) Types of Execution Context

Ans: The primary two types are the Global Execution Context, which is created once when the program starts, and the Function Execution Context, which is created every time a function is called.

Cross Question

Q1. How many Global Execution Contexts exist?

Ans: Only one per JavaScript program (or per global environment such as a browser tab or Node.js process).

3\*\*\*) Global Execution Context (GEC)

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

4\*\*\*) Function Execution Context (FEC)

Whenever a function is called, JavaScript creates a new Function Execution Context. It contains: 

Function Parameters, Local variables, Inner Functions, The value of this.

Once the function finish execution, it's execution context is removed from the call stack.

Cross Questions

Q1. Does every function call create a new Execution Context?

Ans: Yes, Even if you call the same function multiple times, a new Function Execution Context is created for each invocation.

Q2. Can multiple Function Execution Contexts exist?

Ans: Yes, If functions call other functions, multiple contexts exist simultaneously in the call Stack.

5\*\*\*) Execution Context Lifecycle

Every Execution context goes through two phases: 

1\. Memory Creation Phase.

2\. Execution Phase.

6\*\*\*) Memory Creation Phase (Creation Phase)

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

7\*\*\*) Execution Phase

During the Execution Phase, JavaScript executes the code line by line. Variable receive their assigned values, functions are invoked, expressions are evaluated, and new Function Execution Contexts are created whenever a function is called.

Cross Questions

Q1. What happens if a function is called?

Ans: JavaScript creates a new Function Execution Context and pushes it onto the Call Stack.

8\*\*\*) Call Stack

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

Global Execution Context        Function Execution Context

Created once            Created on every function call

Exists for the lifetime of the program.     Exists only while the function executes

Stores global variables and functions       Store local variables, parameters, and inner functions.

FAQ7. Does every function call create a new memory space?

Ans: Yes. Each function invocation gets its own separate execution context with its own local variables and parameters.

⭐⭐⭐⭐⭐ 2. JavaScript Hoisting



1\) What is Hoisting?

Ans: Hoisting is JavaScript default behaviour of moving declarations to the top of their scope during the Memory Creation Phase before the code is executed. 

It is important to note that JavaScript does not physically move the code, instead during memory creation,

\* var variables are allocated memory and initialized with undefined.

\* let and const variables are allocated memory but remain uninitialized.

\* Function declarations are stored with their complete function definitions.

This behaviour is called hoisting.

Cross Questions

Q1. Does JavaScript move the code to the top ?

Ans: No, JavaScript does not physically move the code. It only allocates memory during the Memory Creation Phase.

Q2. Is hoisting only for variables?

Ans: No, Functions are also hoisted.

2\) Hoisting with var

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

3\\\*\\\*\\\*) Hoisting with let

Ans: Variables declare with let are hoisted, but they are not initialized during the Memory Creation Phase. They remain inside the Temporary Dead Zone (TDZ) until declaration line is executed. Accessing them before declaration results in a ReferenceError.

Cross Question

Q1. Is let hoisted?

Ans: Yes, let is hoisted, but it is not initialized until execution reaches its declaration.

4\) Hoisting with const

Ans: const behaves similarly to let. It is hoisted but remains in TDZ until its declaration is executed. Accessing it before declaration thrown a ReferenceError.

Cross Question

Q1. Why does const also have TDZ?

Ans: Because const is also hoisted without initialization. Since const must be initialized when declared, JavaScript prevents access before the declaration by placing it in the TDZ.

5\) Function Hoisting

Function declaration are completely hoisted. During the Memory Creation Phase, JavaScript stores the entire function definition in memory.

Therefore, function declarations can be called before they appear in the code.

Cross Questions

Q1. Why the function declarations be called before declaration?

Ans: Because the complete function definition is stored during the Memory Creation Phase.

Q2. Are all functions hoisted ?

Ans: No, Only function declarations are fully hoisted.

6\) Function Expression vs Function Declaration

Ans: A Function declaration is fully hoisted with its implementation.

A Function Expression behaves like a variable. If declared with var, only the variable is hoisted as undefined; if declared with let or const, it remains in the TDZ until initialized.

Comparison Table

Function Declaration          Function Expression

Fully hoisted           Variable is hoisted

Callable before declaration         Not callable before initialization

Entire function stored          Variable initialized later.

7\) Temporal Dead Zone (TDZ)

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

\* If assigned to var, the variable is hoisted as undefined, so calling it before assignment results in a TypeError

\* If assigned to let or const, the variable is in the TDZ, so calling it before assignment results in a ReferenceError.

FAQ2. Is hoisting performed at runtime?

Ans: No, Hoisting happens during the Memory Creation Phase, before the Execution Phase begins. 

FAQ3. Which declaration are full hoisted ?

Ans: Only Function Declaration are fully hoisted with their complete implementation.

FAQ4. Does TDZ mean memory isn't allocated?

Ans: No, Memory is allocated for let and const, but they remain uninitialized until execution reaches their declaration.

⭐⭐⭐⭐⭐ 3. JavaScript Scope

1\) What is Scope?

Ans: Scope is the region of a program where a variable or function is accessible. In other words, scope determines where a variable can be accessed in the code.

JavaScript provides different types of scopes: 

\* Global Scope

\* Functional Scope

\* Block Scope

\* Lexical Scope

Cross Questions

Q1. What does Scope determine?

Ans: Scope determine where variables and functions are accessible.

Q2. Is the scope created at runtime ?

Ans: No. Scope is determined when the code is written (lexical scope), not when it is executed.

2\) Global Scope 

Ans: A variable declared outside all functions and blocks belongs to the Global Scope. Global variables can be accessed from anywhere in the program.

3\) Function Scope

Ans: Variable declares inside a function are available only within that function. They cannot be accessed from outside the function.

Cross Questions

Q1. Which keyword creates function-scoped variables?

Traditionally, var is function-scoped.

let and const are block-scoped.

4\) Block Scope 

Block is any code enclosed with {}. Variable declared with let and const are block-scoped, meaning they are accessible only inside that block.

Cross Questions

Q1. Does var follow block scope?

Ans: No, var ignores block scope and is function-scoped.

Q2. Why were let and const introduced?

Ans: To provide block scope and avoid bugs caused by var.

5\) Lexical Scope

Lexical Scope means that a function can access variables from the scope where it was defined, not where it is called.

JavaScript determines scope based on the physical placement of code during development.

6\) Scope Chain

Scope Chain is the mechanism JavaScript uses to find variables. 

When a variable is accessed, JavaScript first searches in the current scope.

If it is not found, JavaScript searches the parent scope, then the grandparent scope, continuing until it reaches the Global scope.

If the variable still isn't found, JavaScript thrown a ReferenceError.

Cross Questions

Q1. How does JavaScript search for variables?

Ans: JavaScript Searches: 

1\. Current Scope

2\. Parent Scope

3\. Grandparent Scope

4\. Global Scope

Q2. What happens if the variable isn't found?

Ans: JavaScript throws: ReferenceError.

Global Scope vs Function Scope vs Block Scope

Global Scope        Function Scope          Block Scope

Accessible everywhere     Accessible only inside the function   Accessible only inside the block

Created outside functions   Created by functions        Created by {} blocks

Lifetime is entire program    Exists while function executes      Exists while block executes

Function Scope vs Block Scope

Function Scope          Block Scope

Created by functions        Created by {}

var follows function scope      let and const follow block scope.

Available throughout the function     Available only inside the block

FA!1. How does JavaScript search for variables?

JavaScript starts searching in the current scope. If the variable is not found, it moves to the parent scope, then continues up through the Scope Chain until it reaches the Global Scope. If the variable is still not found, it throws a ReferenceError

FAQ2. What is Variable Shadowing?

Ans: Variable shadowing occurs when a variable declared in an inner scope has the same name as a variable in an outer scope.

⭐⭐⭐⭐⭐ 4. JavaScript Closures

1\) What is a Closure ?

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

\* count is created. 

\* inner () is returned 

\* Normally, local variables should disappear after the function finishes.

\* But since inner() still references count, JavaScript keeps count alive.

\* This preserved relationship is called a closure.

Cross Questions

Q1. Why does the variable still exist after the function finishes?

Ans: Because the returned inner function still has a reference to it. JavaScript keeps the variable in memory until nothing references the closure anymore.

Q2. Is Closure a feature or a design pattern?

Ans: Closure is a JavaScript language feature, not a design pattern.

2\) How Does a Closure Work Internally?

Ans: When a function returned from another function, JavaScript store a reference to the outer function's lexical environment. Even after the outer function finishes execution, the returned function can still access those variables.

3\) Advantages of Closures

Closures provide the several benefits: 

\* Data Hiding 

\* Private Variables

\* Function Factories 

\* Module Pattern

\* Memorization

\* Callbacks

\* Event Handlers

\* React Hooks

Cross Questions

Q1. Why are Closures useful?

Ans: Because they are allow functions to preserves state without exposing variables globally.

4\). Disadvantages of Closures

Closures have some drawbacks:

  \* Increase Memory usege because referenced variable stay alive

  \* Can lead to memory leaks if unnecessary references are retained

  \* Slightly harder to debug because variable remain accessible after the outer function exits.

Cross Questions

Q1. Should closure always be avoided ?

Ans: No, Closures are fundamental to JavaScript and are used extensively. They should simply be used thoughfully.

5\). Practical Example – Data Hiding

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

6\). Practical Example – Private Variables

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

7\). Practical Example – Module Pattern

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

8\). Practical Example – Memoization

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

        cache[num] = num \* num;

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

1\). What is this?

Ans this is a special keyword in JavaScript that refers to the object that is currently executing the function.

The value of this is determined at runtime based on how the function is invoked, not where it is declared.

The value of this changes in difficult execution contexts such as:

\* Global Context

\* Function Context

\* Object Method

\* Constructor Function

\* Class

\* Arrow Function

Cross Questions

Q1. Is this decided when writing the code?

Ans: No, this is determine when the function is called, expect for arrow functions.

2\). this in Global Context

In the browser, inside a normal script, this in the global context refers to the window object.

In ES6 modules or strict mode, the behavior can differ. In Node.js, the global context behaves differently from the browser.

3\). this in Function Context

In a normal function, the value of this depends on how the function is called. 

\* In non-strict mode (browser), calling a standalone function sets this to the global object (window)

\* In strict mode, this is undefined.

4\). this in Object Context

When a function is called as an object method, this refers to the object that invoked the method

5\). this in Constructor Functions

When function is called using the new keyword, JavaScript creates a new object and sets this to that newly created object.

Cross Questions

Q1. What happens if we don't use new?

Ans: The function behaves like a normal function call, and this is not bound to a newly created object.

6\). this in Classes

In a class, this refers to the current instance of the class. It is used to access instance properties and methods.

Cross Questions

Q1. Why do constructors use this?

Ans: Because this initialize the properties of the newly created object.

7\). this in Arrow Functions

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

\* call() --> Invokes immediately with individual arguments.

\* apply() --> Invokes immediately with an array of arguments

\* bind() --> Returns a new function with this permenently bound.

Cross Question

Q1. Why are arrow functions commonly used in callbacks?

Ans: Because they preserve the surrounding this, avoinding the need to write: 

const self = this;

or use .bind(this)

Q2. Can we change this of an arrow function using call(), apply(), or bind()?

Ans: No, These methods cannot change the lexical this of an arrow function.

⭐⭐⭐⭐⭐ 6. JavaScript call(), apply(), and bind()

1\). Why do we need call(), apply(), and bind()?

Ans: In JavaScript value of this depends on how a function is called. Sometimes we want to explicitly control what this refers to.

call(), apply() and bind() allow us to manually set the value of this.

Real Project Example

In React Class component (before Hooks), developer often used: 

this.handleClick = this.handleClick.bind(this);

This ensured that inside handleClick refered to the component instance.

Cross Questions

Q1. Why do we need these methods?

Ans: Because JavaScript allows us to control the value of this explicitly instead of relying on how the function is called.

2\). call()

call() invoke the function immediately and allows us to specify the value of this. Arguments are passed individually.

Syntax

function.call(thisArg, arg1, arg2, arg3);

Cross Questions

Q1. Does call() execute immediately ?

Ans: Yes.

Q2. How are arguments passed?

Ans: Individually.

3\). apply()

apply work exactly like call(), expect that arguments are passed as an array.

Syntax

function.apply(thisArg, [arg1, arg2]);

Cross Questions

Q1. Does apply() execute immediately ? 

Yes.

Q2. How are arguments passed?

As an array.

4\). bind()

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

5\). Difference between call(), apply(), and bind()?

Method                  Executes Immediately              Arguments                    Return New Function

call()                  Yes                               Individual                   No

apply()                 Yes                               Array                        No

bind()                  No                                Individual(stored)           Yes

6\). Real-World Use Cases

1\. Function Borrowing

Function Borrowing means using a method from one object with another object by changing the value of this.

2\. React Class Components

Before, hook event handlers often lost the value of this.

bind() ensures this refers to the component instance.

3\. Event Handlers

Without bind(), this would not refer to person.

4\. Array as Arguments.

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

1\). What is an Arrow Function ?

Ans: An arrow function is a shorter way to write functions in JavaScript, introduced in ES6.

Unlike normal functions, arrow functions:

\* Have a shorter syntax.

\* Do not have thier own this.

\* Do not have thier own arguments object.

\* Cannot be used as constructors.

\* Cannot be invoked using the new keyword.

Real Project Example

Arrow functions are commonly used in: 

\* React Event handlers

\* Array Methods (map, filter, reduce)

\* Promise Callbacks

\* API Calls

\* setTimeout()

\* setInterval()

Cross Questions:

Q1. Why were Arrow Functions introduced?

Ans: To provide a cleaner syntax and solve common issues related to this in callback functions.

2\). Advantages of Arrow Functions.

Arrow functions provide several advantages:

\* Shorter and cleaner syntax.

\* Lexical this.

\* Better for callbacks.

\* Easier to read

\* Widely used in React and modern JavaScript.

3\). Limitations of Arrow Functions.

Arrow functions should not be used when we need:

\* Their own this.

\* Their own arguments.

\* Constructor functions.

\* Methods that rely on dynamic this.

4\). No Own this.

Arrow functions do not create their own this.

Instead, they inherit this from the surrounding lexical scope.

5\). No arguments Object

Arrow functions do not have their own arguments object.

If needed, they inherit arguments from the enclosing function or we should use rest paraments (...args).

Cross Question:

Q1. How do you replace arguments in an arrow function?

Use rest paraments (...args)

6\). Cannot be Constructor

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

Ans: No. Only regular function declarations or expressions can be generator functions using function\*.

⭐⭐⭐⭐⭐ 8. JavaScript Event Loop

1\). What is the Event Loop ?

Ans: JavaScript is a single-theaded language, which means it can execute only one piece of code at a time.

To handle asynchronous operations like API calls, timers, and user events without blocking the main thead, JavaScript uses the Event Loop.

The Event Loop continuously checks whether the Call Stack is empty. If it is, it moves pending tasks from the Microtask Queue first, 

ans then from the Callback (Macrotask) Queue to the Call Stack for execution.

Real Project Example

When a user clicks a button that makes an API call:

1\. Click handler executes.

2\. API request is sent.

3\. JavaScript continues executing other code.

4\. API response arrives later.

5\. Callback is queued.

6\. Event llop executes the callback when the Call Stack becomes empty.

2\). JavaScript Runtime.

The JavaScript Runtime is the environment where JavaScript code executes.

It consists of:

\* JavaScript Engine (V8, SpiderMonkey, JavaScriptCore, etc.)

\* Call Stack

\* Web APIs (Browser) or Node.js APIs

\* Callback Queue

\* Microtask Queue

\* Event Loop

Cross Question

Q1. Is the Event Loop part of JavaScript?

Ans: No. The Event Loop is provided by the JavaScript runtime (Browser or Node.js), not by the JavaScript language itself.

3\). Call Stack

The Call Stack is a data structure that keeps track of function execution.

It follows the LIFO (Last In, First Out) principle.

4\. Web APIs

Web APIs are browser-provided features that handle asynchronous operations outside the JavaScript engine.

Exm:

\* setTimeout

\* setInterval

\* fetch

\* DOM Events

\* Geolocation

Why?

setTimeout is handled by the browser's Web API while JavaScript continues executing.

5\). Callback Queue (Macrotask Queue)

The Callback Queue, also called the Macrotask Queue, stores completed asynchronous callbacks such as:

\* setTimeout

\* setInterval

\* DOM Events

\* Message events

These tasks are executed after all microtasks have completed.

6\). Microtak Queue

The Microtask Queue stores high-priority asynchronous tasks.

Common microtasks include:

\* Promise callbacks (.then, .catch, .finally)

\* queueMicrotask()

\* MutationObserver

The event loop always empties the Microtask Queue before executing any Callback Queue task.

7\). Event Loop Working

The Event Loop continuously monitors the Call Stack.

When the Call Stack becomes empty:

1\. Execute all Microtasks.

2\. Execute one Macrotask.

3\. Repeat the process.

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

\* The Call Stack is empty.

\* All Microtasks have completed.

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

1\. A executes immediately.

2\. setTimeout callback goes to the Callback Queue.

3\. Promise callback goes to the Microtask Queue.

4\. D executes.

5\. Call Stack becomes empty.

6\. Event Loop executes all Microtasks(C).

7\. Finally, it executes the Callback Queue (B).

⭐⭐⭐⭐⭐ 9. JavaScript Promises

1\). What is a Promise?

Ans: Prmoise is an object that represents the eventual completion (success) or failure of an asynchronous operation.

Instead of blocking the execution, a Promise allows JavaScript to continue executiong other code while waiting for 

asynchronous operation to complete.

Once the operation completes, the Promise either resolves with a value or rejects with an error.

Cross Questions:

Q1. Why do we need Promises?

Ans: Promises help handle asynchronous operations without deeply nested callbacks (Callback Hell).

They make code cleaner,  more readable, and easier to manage.

2\). then()

then() executes when a Promise is successfully fulfilled.

3\). catch()

catch() handles errors that occur during Promise execution or in any previous then() block.

4\). finally()

finally() executes regardless of whether the Promise is fulfilled or rejected.

It is commonly used for cleanup tasks like hiding a loader or closing a databae connection.

5\). Prmoise Chaining 

Example: 

Promise.resolve(10)

.then(value => value \* 2)

.then(value => value + 5)

.then(value => console.log(value));

Each then() returns new Promise, enabling chaining.

6\). Promise.all()

Promise.all() executes multiple Promises in parallel and waits until all of them are fullfilled.

If any one Promise rejects, the entire Promise.all() immediately rejects.

Promise.all() stops immediately when one Promise rejects.

7\). Promise.allSetteld()

Promise.allSettled() waits until all Promises finish, regardless of whether they succeed or fail.

It returns the status and result of every Promise.

8\). Promise.any()

Promise.any() returns the first fulfilled Promise.

It ignores rejected Promises unless all Promises reject.

9\). Promise.race()

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

1\). What is async?

Ans: The async keyword is used to declare an asynchronous function.

An async function always returns a Promise, even if we return a normal value.

It allows us to use the await keyword inside the function.

---

# ⭐⭐⭐⭐⭐ Additional JavaScript Interview Topics

> The sections below are added to cover important JavaScript interview topics that are not present or are only briefly mentioned in the original notes. The original content above is intentionally preserved.

# 11. JavaScript Data Types - Deep Dive

## Primitive vs Reference Types

Primitive values include:

- String
- Number
- BigInt
- Boolean
- Undefined
- Null
- Symbol

Objects are reference values.

### Cross Question

Q1. Are objects passed by reference?

Ans: JavaScript is always pass-by-value. For objects, the value being passed is a reference to the object, so changes to the object's properties can be visible through other references.

---

# 12. == vs ===

## == Loose Equality

`==` performs type coercion before comparison when appropriate.

## === Strict Equality

`===` compares values without performing the same implicit type coercion.

### Interview Answer

> "I generally prefer strict equality because it avoids unexpected type coercion and makes comparisons more predictable."

---

# 13. Type Coercion

Type coercion is the conversion of a value from one type to another.

It can be:

1. Implicit coercion
2. Explicit coercion

Examples:

```js
Number("10");   // 10
String(10);     // "10"
Boolean(1);     // true
```

---

# 14. Truthy and Falsy Values

Falsy values in JavaScript include:

- false
- 0
- -0
- 0n
- ""
- null
- undefined
- NaN

Most other values are truthy, including:

```js
[]
{}
```

### Cross Question

Q1. Is an empty array truthy?

Ans: Yes. Arrays and objects are truthy values, even when they are empty.

---

# 15. null vs undefined

### undefined

Usually means a value has not been assigned or is absent.

### null

Usually represents an intentional absence of a value.

### Interview Answer

> "Undefined generally indicates that a value has not been assigned or is missing, while null is commonly used to explicitly represent no value."

---

# 16. NaN

`NaN` means **Not-a-Number**.

It is a special numeric value that represents an invalid numeric result.

```js
Number("hello"); // NaN
```

### Important

```js
typeof NaN; // "number"
```

To check it:

```js
Number.isNaN(value);
```

---

# 17. Object and Array Methods

Important methods for interviews:

### Array

- map()
- filter()
- reduce()
- find()
- findIndex()
- some()
- every()
- includes()
- forEach()
- slice()
- splice()
- concat()

### Cross Question

Q1. Difference between map() and forEach()?

Ans: `map()` returns a new array containing transformed values. `forEach()` is generally used for iteration and does not create a transformed array as its return value.

---

# 18. map(), filter(), and reduce()

## map()

Transforms each element and returns a new array.

```js
const result = [1, 2, 3].map(x => x * 2);
// [2, 4, 6]
```

## filter()

Returns elements that satisfy a condition.

```js
const result = [1, 2, 3, 4].filter(x => x > 2);
// [3, 4]
```

## reduce()

Reduces an array to a single accumulated result.

```js
const result = [1, 2, 3].reduce((sum, x) => sum + x, 0);
// 6
```

---

# 19. slice() vs splice()

### slice()

Returns a shallow copy of a portion of an array and does not mutate the original array.

### splice()

Adds/removes elements and mutates the original array.

### Interview Answer

> "slice is non-mutating and returns a selected portion, while splice mutates the original array by adding or removing elements."

---

# 20. Shallow Copy vs Deep Copy

## Shallow Copy

Copies the top-level structure, but nested objects can still share references.

Common approaches:

```js
const copy = { ...obj };
const copy = Object.assign({}, obj);
```

## Deep Copy

Creates an independent copy of nested data.

One modern approach is:

```js
const copy = structuredClone(obj);
```

### Cross Question

Q1. Does spread operator create a deep copy?

Ans: No. Object and array spread creates a shallow copy.

---

# 21. Destructuring

Destructuring allows values to be extracted from arrays or properties from objects.

```js
const user = {
  name: "Dipak",
  age: 26
};

const { name, age } = user;
```

Array example:

```js
const [first, second] = [10, 20];
```

---

# 22. Spread vs Rest Operator

Both use `...`, but their purpose is different.

### Spread

Expands values.

```js
const arr2 = [...arr1];
```

### Rest

Collects remaining values.

```js
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
```

---

# 23. Default Parameters

Default parameters provide fallback values when an argument is `undefined`.

```js
function greet(name = "Guest") {
  return `Hello ${name}`;
}
```

---

# 24. Optional Chaining

Optional chaining `?.` safely accesses nested properties.

```js
user?.address?.city
```

If an intermediate value is `null` or `undefined`, the expression returns `undefined` instead of throwing.

---

# 25. Nullish Coalescing Operator

The `??` operator returns the right-hand value only when the left-hand value is `null` or `undefined`.

```js
const name = user.name ?? "Guest";
```

### `||` vs `??`

`||` treats all falsy values as fallback candidates.

`??` only treats `null` and `undefined` as missing.

---

# 26. Object.freeze() vs Object.seal()

## Object.freeze()

Prevents adding, deleting, or changing existing properties at the top level.

## Object.seal()

Prevents adding or deleting properties, but existing writable properties can still be changed.

---

# 27. Prototypes and Prototype Chain

Every ordinary JavaScript object has an internal prototype relationship.

When a property is not found directly on an object, JavaScript searches its prototype chain.

```text
Object
  ↓
Prototype
  ↓
Parent Prototype
  ↓
null
```

### Interview Answer

> "The prototype chain is the mechanism JavaScript uses for inheritance and property lookup. If a property is not found on an object, JavaScript searches its prototype and continues up the chain."

---

# 28. Class vs Prototype

JavaScript classes provide a cleaner syntax for creating objects and inheritance, but JavaScript's underlying inheritance model is prototype-based.

```js
class User {
  constructor(name) {
    this.name = name;
  }
}
```

### Cross Question

Q1. Is JavaScript class-based internally?

Ans: JavaScript uses prototype-based inheritance. The `class` syntax provides a more convenient abstraction over that model.

---

# 29. new Keyword

When using `new` with a constructor function or class, JavaScript creates a new object and establishes the appropriate prototype relationship.

Conceptually:

1. Create a new object.
2. Link it to the constructor's prototype.
3. Call the constructor with `this` referring to the new object.
4. Return the object unless the constructor explicitly returns another object.

---

# 30. Higher-Order Functions

A higher-order function is a function that:

- Takes another function as an argument, or
- Returns a function.

Examples:

```js
map()
filter()
reduce()
setTimeout()
```

---

# 31. Callback Function

A callback is a function passed to another function to be executed later or by that function.

```js
function processUser(callback) {
  callback();
}
```

Callbacks are common in:

- Array methods
- Event handlers
- Timers
- Asynchronous operations

---

# 32. Pure Function

A pure function:

1. Produces the same output for the same input.
2. Does not cause observable side effects.

```js
function add(a, b) {
  return a + b;
}
```

Pure functions are important in React and Redux because they make code easier to reason about and test.

---

# 33. Side Effects

A side effect is an observable change outside the function's local computation.

Examples:

- API calls
- Modifying external variables
- DOM manipulation
- Logging
- Updating storage

---

# 34. Currying

Currying converts a function with multiple arguments into a sequence of functions that each take one argument.

```js
const add = a => b => a + b;

add(2)(3); // 5
```

---

# 35. Debouncing

Debouncing delays execution until a specified amount of time has passed without another call.

Common use cases:

- Search input
- Form validation
- Resize events

Example concept:

```text
User types:
A → AB → ABC → ABCD

Only after the user stops typing:
                    ↓
                 API call
```

---

# 36. Throttling

Throttling limits how frequently a function can execute within a time period.

Common use cases:

- Scroll events
- Mouse movement
- Resize events

### Debounce vs Throttle

| Debounce | Throttle |
|---|---|
| Waits until activity stops | Limits execution frequency |
| Useful for search | Useful for scroll |
| Executes after inactivity | Executes at controlled intervals |

---

# 37. Garbage Collection

JavaScript automatically manages memory using garbage collection.

Objects that are no longer reachable can become eligible for garbage collection.

### Important

Developers do not manually call a standard JavaScript garbage collector.

### Common memory leak causes

- Unremoved event listeners
- Timers that continue running
- Unnecessary closures retaining large objects
- Detached DOM references
- Long-lived global references

---

# 38. Strict Mode

Strict mode enables stricter JavaScript parsing and runtime behaviour.

```js
"use strict";
```

Benefits include catching certain mistakes and preventing some unsafe behaviours.

ES modules are automatically strict mode.

---

# 39. ES Modules

JavaScript supports modules using `export` and `import`.

```js
// utils.js
export const add = (a, b) => a + b;
```

```js
import { add } from "./utils.js";
```

Benefits:

- Encapsulation
- Code organization
- Reusability
- Dependency management

---

# 40. Named Export vs Default Export

### Named Export

```js
export const add = () => {};
```

Import:

```js
import { add } from "./utils.js";
```

### Default Export

```js
export default function add() {}
```

Import:

```js
import add from "./utils.js";
```

A module can have multiple named exports but only one default export.

---

# 41. Event Bubbling and Event Capturing

DOM events can propagate through the DOM tree.

### Capturing Phase

Event travels from the top of the DOM tree toward the target.

### Target Phase

Event reaches the target element.

### Bubbling Phase

Event travels from the target back upward.

```text
Capturing
    ↓
Parent
    ↓
Target
    ↑
Bubbling
```

---

# 42. Event Delegation

Event delegation means attaching one event listener to a parent instead of attaching separate listeners to many child elements.

It works because of event bubbling.

Benefits:

- Fewer event listeners
- Better handling of dynamically created elements
- Simpler event management

---

# 43. preventDefault() vs stopPropagation()

### preventDefault()

Prevents the browser's default action.

Example:

```js
event.preventDefault();
```

### stopPropagation()

Stops the event from propagating further through the DOM.

```js
event.stopPropagation();
```

---

# 44. Local Storage vs Session Storage vs Cookies

## localStorage

- Persists until explicitly cleared.
- Stores data as strings.
- Accessible through browser JavaScript.

## sessionStorage

- Data is associated with the current browser tab/session.
- Stores data as strings.

## Cookies

- Small pieces of data associated with a domain.
- Can be sent with HTTP requests.
- Can have attributes such as `HttpOnly`, `Secure`, and `SameSite`.

### Important Security Point

Sensitive authentication tokens require careful storage decisions. HttpOnly cookies can reduce exposure to client-side JavaScript compared with tokens stored directly in web storage.

---

# 45. JSON

JSON stands for JavaScript Object Notation.

Common methods:

```js
JSON.stringify(object);
JSON.parse(jsonString);
```

### stringify()

Converts a JavaScript value to a JSON string.

### parse()

Converts valid JSON text into a JavaScript value.

---

# 46. Optional: WeakMap and WeakSet

## WeakMap

Stores key-value pairs where keys must be objects.

## WeakSet

Stores objects weakly.

They are useful in scenarios where you want object associations without preventing garbage collection through a strong reference.

---

# 47. Set and Map

## Set

Stores unique values.

```js
const set = new Set([1, 2, 2, 3]);
```

The set contains:

```text
1, 2, 3
```

## Map

Stores key-value pairs and allows keys of different types.

```js
const map = new Map();

map.set("name", "Dipak");
```

### Map vs Object

Map is useful when you need a dedicated key-value collection with arbitrary key types and built-in collection operations.

---

# 48. Generator Functions

Generator functions use `function*` and `yield`.

```js
function* numbers() {
  yield 1;
  yield 2;
  yield 3;
}
```

Calling the generator returns an iterator.

Generators can pause and resume execution.

---

# 49. Iterators and Iterables

An **iterable** is an object that can be iterated using `for...of`.

Examples:

- Array
- String
- Map
- Set

An iterator provides a `next()` method that returns an object such as:

```js
{ value: 1, done: false }
```

---

# 50. Symbols

A Symbol creates a unique primitive value.

```js
const id = Symbol("id");
```

Two separately created symbols are not equal.

```js
Symbol("id") === Symbol("id"); // false
```

Symbols can be used as unique object property keys.

---

# 51. BigInt

BigInt represents integers larger than the safe integer range of Number.

```js
const value = 9007199254740993n;
```

BigInt values use the `n` suffix.

BigInt and Number should not be mixed directly in arithmetic operations without explicit conversion.

---

# 52. Promise Error Handling

Promises can handle errors using:

```js
promise
  .then(result => {})
  .catch(error => {})
  .finally(() => {});
```

With async/await:

```js
try {
  const result = await fetchData();
} catch (error) {
  console.error(error);
} finally {
  // cleanup
}
```

---

# 53. async/await

An `async` function always returns a Promise.

`await` pauses execution of that async function until the awaited Promise settles, while the JavaScript runtime can continue executing other work.

### Important Interview Answer

> "async/await does not block the JavaScript thread. It pauses the execution of the current async function and resumes it when the awaited Promise settles."

---

# 54. Sequential vs Parallel Async Operations

### Sequential

```js
const user = await getUser();
const orders = await getOrders();
```

The second operation starts after the first completes.

### Parallel

```js
const [user, orders] = await Promise.all([
  getUser(),
  getOrders()
]);
```

Independent operations can execute concurrently.

### Interview Tip

> "If operations are independent, I prefer running them concurrently with Promise.all when failure of one should fail the overall operation."

---

# 55. AbortController

`AbortController` allows cancellable operations such as fetch requests.

```js
const controller = new AbortController();

fetch("/api/users", {
  signal: controller.signal
});

controller.abort();
```

Common use cases:

- Cancel requests when a component unmounts
- Prevent stale requests
- Avoid unnecessary network work

---

# 56. Race Conditions in Frontend

A race condition can occur when multiple asynchronous requests finish in an unexpected order.

Example:

```text
Request A → slow
Request B → fast
```

If the user changes the search query quickly, an older request might finish after a newer request and overwrite the latest result.

Solutions include:

- AbortController
- Request IDs
- Ignoring stale responses
- Proper state management

---

# 57. Common JavaScript Interview Output Questions

Interviewers commonly test:

1. Hoisting
2. Closures
3. Scope
4. `this`
5. Event loop
6. Promises
7. `setTimeout`
8. Microtasks vs macrotasks
9. Type coercion
10. `var`, `let`, `const`

Example:

```js
console.log(1);

setTimeout(() => {
  console.log(2);
}, 0);

Promise.resolve().then(() => {
  console.log(3);
});

console.log(4);
```

Output:

```text
1
4
3
2
```

Reason:

1. Synchronous code executes first.
2. Promise callback enters the Microtask Queue.
3. setTimeout callback enters the Macrotask Queue.
4. Microtasks execute before the next macrotask.

---

# 58. Most Important JavaScript Interview Topics

For a 4-year React/Next.js developer, focus strongly on:

1. Execution Context
2. Hoisting
3. Scope and Scope Chain
4. Closures
5. `this`
6. call/apply/bind
7. Arrow Functions
8. Event Loop
9. Microtasks vs Macrotasks
10. Promises
11. async/await
12. Promise.all / allSettled / any / race
13. Shallow vs Deep Copy
14. `==` vs `===`
15. Type Coercion
16. map/filter/reduce
17. Destructuring
18. Spread/Rest
19. Optional Chaining
20. Nullish Coalescing
21. Prototypes
22. Classes
23. Higher-Order Functions
24. Debouncing and Throttling
25. Garbage Collection and Memory Leaks
26. Event Bubbling/Capturing
27. Event Delegation
28. Modules
29. Local Storage / Session Storage / Cookies
30. AbortController and async request cancellation

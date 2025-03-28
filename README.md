Lec-1
What Happens When You Run JavaScript Code?
When you execute JavaScript code, many things happen behind the scenes in the JavaScript Engine. The core concept that enables JavaScript execution is the Execution Context.

1. Execution Context
Everything in JavaScript happens inside an Execution Context. Without an execution context, JavaScript cannot run.

What happens when you run JavaScript?
A Global Execution Context (GEC) is created.

2. Global Execution Context (GEC) Creation
When JavaScript code runs, the first thing that happens is the creation of the Global Execution Context.
The Execution Context consists of two main components:
Memory Component (Variable Environment)
Code Component (Thread of Execution)

4. Phases of Execution Context Creation
The Execution Context is created in two phases:

Phase 1: Memory Allocation Phase (Creation Phase)
JavaScript first scans the entire code and allocates memory to variables and functions before executing any code.
Memory is allocated as follows:
Variables are assigned a special value: undefined.
Functions store their entire function definition in memory.
Phase 2: Code Execution Phase
In this phase, JavaScript executes the code line by line.
The actual values are assigned to variables, and function calls are executed.

4. Example Code for Execution Context Creation
js
Copy
Edit
var n = 2;

function square(num) {
    return num * num;
}

var square2 = square(n);
var square4 = square(4);
Memory Allocation Phase (Phase 1)
Variable/Function	Memory Allocation
n	undefined
square	Function code is stored
square2	undefined
square4	undefined
Code Execution Phase (Phase 2)
Execution Step	Action Taken
n = 2	undefined → 2
square2 = square(n)	Calls function square(2), stores 4
square4 = square(4)	Calls function square(4), stores 16

5. Function Invocation and Execution Context Creation
Function Invocation
Whenever a function is called using () (e.g., square(n)), a new Execution Context is created for that function.
This new execution context follows the same two phases:
Memory Allocation Phase
Code Execution Phase
Execution Steps for square(n)
A new Function Execution Context (FEC) is created.
This context has two components (same as the Global Execution Context):
Memory Component (stores local variables)
Code Component (executes function code)
Memory Allocation Phase for square(n)
Variable/Function	Memory Allocation
num	undefined
Code Execution Phase for square(n)
Execution Step	Action Taken
num = 2	undefined → 2
return num * num	Returns 4
Once the function execution is completed, the Function Execution Context is deleted, and control returns to the Global Execution Context.

7. Execution Context Stack (Call Stack)
JavaScript uses a Call Stack (Execution Stack) to keep track of execution contexts.
When a function is called:
A new Execution Context is created and pushed to the Call Stack.
When the function finishes executing, the Execution Context is removed (popped from the stack).
Example Call Stack for the above code:
Global Execution Context (GEC) is created.
Function square(n) is called → New Execution Context is pushed to Call Stack.
Function square(n) executes and returns → Execution Context is removed from Call Stack.
Function square(4) is called → New Execution Context is pushed to Call Stack.
Function square(4) executes and returns → Execution Context is removed from Call Stack.
Global Execution finishes → GEC is removed, program ends.

8. Summary
Global Execution Context is created first.
Execution happens in two phases:
Memory Allocation Phase: Variables are stored as undefined, functions are stored fully.
Code Execution Phase: Values are assigned, and functions are executed.
When a function is called:
A Function Execution Context is created.
It goes through Memory Allocation and Execution Phases.
Once done, the Function Execution Context is deleted.
The Call Stack manages execution contexts.
When the program finishes, the Global Execution Context is removed, and the program ends.
These notes contain every concept from the video transcript in an organized and detailed way without missing any points. Let me know if you need any modifications! 🚀
Here are the detailed notes on the **Shortest JavaScript Program**, including explanations, diagrams, and code examples.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Lec-2:**"How JavaScript Works Behind the Scenes - Execution Context"**  

# **How JavaScript Works Behind the Scenes**
### **Execution Context in JavaScript**

### 🔹 **Core Fundamental**
**Everything in JavaScript happens inside the Execution Context.**  
It acts like a **big container (box)** where JavaScript code is executed.

### **Structure of Execution Context**
The Execution Context consists of **two main components**:

1. **Memory Component (Variable Environment)**
   - Stores **variables and functions** as **key-value pairs**.
   - Example:
     ```js
     var a = 10;
     function hello() { console.log("Hello!"); }
     ```
   - Stored in memory as:
     ```
     Key   | Value
     --------------
     a     | 10
     hello | function() {...}
     ```
   - Also called **Variable Environment**.

2. **Code Component (Thread of Execution)**
   - Responsible for **executing code line by line**.
   - Also called **Thread of Execution**.

📌 **Diagram Representation**:  
```
-------------------------------------
| Execution Context                 |
| ---------------------------------  |
| | Memory Component (Variables) |  |
| | a -> 10                        |  |
| | hello -> function() {...}       |  |
| ---------------------------------  |
| | Code Component (Execution)    |  |
| | Executes one line at a time    |  |
| ---------------------------------  |
-------------------------------------
```

---

### **JavaScript is a Synchronous, Single-Threaded Language**
🔹 **Synchronous:**  
- Executes **one** command **at a time** in a **specific order**.  
- The next line **waits** for the previous line to finish.

🔹 **Single-Threaded:**  
- **Only one** execution thread is available.

**Example:**
```js
console.log("Start");
let a = 10;
console.log(a);
console.log("End");
```
**Execution Order:**
1. `console.log("Start");` → Output: Start
2. `let a = 10;` → Stores `a` in memory.
3. `console.log(a);` → Output: 10
4. `console.log("End");` → Output: End

📌 **Execution Flow**
```
Memory Component:
a -> 10

Execution Order:
1. Start
2. 10
3. End
```

---

### **Recap**
✅ **Execution Context** has:
   - **Memory Component (Variable Environment)** → Stores variables & functions.
   - **Code Component (Thread of Execution)** → Executes code line by line.

✅ **JavaScript is:**
   - **Synchronous** → Executes one command at a time.
   - **Single-threaded** → Uses only one execution thread.

✅ **Important Terms**
   - Memory Component = **Variable Environment**.
   - Code Component = **Thread of Execution**.

---

### **Next Steps**
In the next video, we will learn **how a JS program is executed step by step**, including memory allocation and execution phases.

Let me know if you need modifications or additional explanations! 🚀
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Lec-3:How JavaScript Code is executed? & Call Stack

### **1. Execution Context in JavaScript**
- Everything in JavaScript happens inside an **Execution Context**.
- Whenever a JavaScript program runs, an **Execution Context is created**.

### **2. Global Execution Context (GEC)**
- When the JavaScript code starts executing, a **Global Execution Context (GEC)** is created.
- The **GEC** consists of two phases:
  1. **Memory Allocation Phase**
  2. **Code Execution Phase**

### **3. Memory Allocation Phase**
- JavaScript first **allocates memory** for variables and functions before executing the code.
- Variables are initially assigned **undefined**.
- Functions are stored **as a whole** in memory.

#### **Example:**
```js
var n = 2;
function square(num) {
   return num * num;
}
var square2 = square(n);
var square4 = square(4);
```
- Memory Allocation:
  - `n → undefined`
  - `square → entire function code`
  - `square2 → undefined`
  - `square4 → undefined`

### **4. Code Execution Phase**
- In this phase, JavaScript **executes the code line by line**.
- **Variable values are updated**:
  - `n = 2` replaces `undefined` with `2`.
  - `square2 = square(n)` calls the function.

### **5. Function Execution Context (FEC)**
- Whenever a function is called (`square(n)`), a **new Execution Context** is created for that function.
- The **Function Execution Context (FEC)** also has:
  - **Memory Allocation Phase** (parameters assigned `undefined` initially).
  - **Code Execution Phase** (actual execution of the function).
- Once the function completes execution, its context is **removed from the call stack**.

#### **Example of Call Stack Progression:**
1. **Global Execution Context (GEC) created.**
2. Memory allocation happens.
3. Code execution starts.
4. Function `square(n)` is invoked → **New Execution Context created**.
5. Function execution completes → **Execution Context removed**.
6. The process repeats for `square(4)`, and the result is stored in `square4`.

### **Key Takeaways:**
✔ JavaScript code runs inside an **Execution Context**.  
✔ The **Global Execution Context (GEC)** is created first.  
✔ Memory is allocated **before execution** (`undefined` for variables, full function code for functions).  
✔ **Function calls create their own Execution Context**, which follows the same two-phase process.  
✔ Once a function executes, its Execution Context is **removed from the stack**.  

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Lec-4:JavaScript Hoisting and Global Execution Context (GEC) Explained**

---

## **1. Introduction to Hoisting**
Hoisting is a JavaScript mechanism where variable and function declarations are moved to the top of their scope before code execution. This means you can use variables and functions before declaring them.

### **Example of Hoisting:**
```javascript
console.log(a); // Output: undefined
var a = 10;
```

**Explanation:** JavaScript moves the declaration of `a` to the top, but not its assignment.

Equivalent interpretation:
```javascript
var a;
console.log(a); // undefined
a = 10;
```

---

## **2. Global Execution Context (GEC)**
Whenever JavaScript code runs, it first creates a **Global Execution Context (GEC)**, which consists of:
- **Memory Creation Phase (Creation Phase)**
- **Execution Phase**

### **Step 1: Memory Creation Phase (Hoisting Happens Here)**
1. Variables declared with `var` are **initialized with `undefined`**.
2. Function declarations are **fully hoisted**, meaning they are stored in memory as complete functions.
3. `let` and `const` variables are hoisted but **not initialized** (they stay in a Temporal Dead Zone).

### **Step 2: Execution Phase**
- The JavaScript engine executes the code line by line.
- Assigns values to variables and executes functions.

---

## **3. Understanding Hoisting with Examples**

### **Hoisting with `var`**
```javascript
console.log(x); // undefined
var x = 5;
console.log(x); // 5
```
**Explanation:**
- In the **Memory Creation Phase**, `x` is hoisted and set to `undefined`.
- In the **Execution Phase**, `x` is assigned `5`.

### **Hoisting with `let` and `const` (Temporal Dead Zone - TDZ)**
```javascript
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 20;
```
**Explanation:**
- `let` is hoisted, but not initialized. Accessing `y` before declaration results in an error.

### **Hoisting with Function Declarations vs. Function Expressions**

#### **Function Declaration (Fully Hoisted)**
```javascript
greet(); // Works fine
function greet() {
    console.log("Hello!");
}
```
**Explanation:** Function declarations are fully hoisted.

#### **Function Expression (Not Hoisted as Function)**
```javascript
console.log(sayHello); // undefined
var sayHello = function() {
    console.log("Hello!");
};
sayHello();
```
**Explanation:**
- `sayHello` is hoisted as a variable (`undefined`), but not as a function.
- Invoking `sayHello` before assignment throws an error.

---

## **4. Diagram: How Hoisting Works in GEC**

### **Before Execution (Memory Creation Phase)**
```
Memory Creation Phase:
---------------------
var x -> undefined
function greet() -> Full function stored in memory
```

### **During Execution Phase**
```
Execution Phase:
----------------
console.log(x); // undefined
x = 5;
console.log(x); // 5
greet(); // Executes function
```

---

## **5. Summary**
### **Key Takeaways:**
1. **Hoisting moves declarations, not assignments.**
2. **`var` is hoisted with `undefined`, but `let` and `const` stay in the Temporal Dead Zone.**
3. **Function declarations are fully hoisted, but function expressions are hoisted as undefined if using `var`.**

Understanding hoisting and the execution context helps avoid unexpected errors in JavaScript programming.



# Lec-5: Introduction to the Shortest JavaScript Program**
### **What is the Shortest JavaScript Program?**
The shortest JavaScript program is an **empty file** (`.js`).  
Even with an empty file, when executed in a browser, the JavaScript engine performs several behind-the-scenes operations.

---

## **Behind the Scenes of the Shortest JavaScript Program**
When an empty JavaScript file runs, the JavaScript engine automatically creates a **Global Execution Context (GEC)** and a **Global Object**.

### **1. Global Execution Context (GEC)**
The **Global Execution Context (GEC)** is automatically created when JavaScript starts executing. It consists of two phases:
- **Creation Phase**: Memory is allocated to variables and functions.
- **Execution Phase**: The code is executed line by line.

### **2. Global Object**
In a **browser environment**, the global object is the `window` object.
In **Node.js**, the global object is `global`.

```js
console.log(window); // In the browser
console.log(global); // In Node.js
```

---

# **Global Execution Context and Window Object**
### **1. What happens when JavaScript starts executing?**
- A **Global Execution Context (GEC)** is created.
- The **window object** is also created.
- The **this keyword** at the global level refers to the `window` object in the browser.

### **2. Verifying the Window Object**
```js
console.log(this); // In the global scope, this refers to window
console.log(window); // The global object in the browser
console.log(this === window); // true
```

📌 **Diagram of Global Execution Context:**
```
-----------------------------------
|  Global Execution Context (GEC)  |
-----------------------------------
|  Memory Space                    |
|  - Variables and functions       |
|----------------------------------|
|  Code Execution                  |
-----------------------------------
```

---

# **Introduction to `this` Keyword in JavaScript**
The `this` keyword behaves differently in various contexts:

| **Context**         | **Value of `this`**        |
|---------------------|--------------------------|
| **Global Scope**    | `window` (in browser)     |
| **Inside a function** | `window` (unless strict mode is used) |
| **Inside a method**  | The object that owns the method |
| **Inside an event**  | The element that triggered the event |

### **Example: Global `this`**
```js
console.log(this); // window
console.log(this === window); // true
```

### **Example: `this` in Functions**
```js
function show() {
    console.log(this); // In the browser, it refers to window
}
show();
```

---

# **Code Example: Variables and Functions in Global Memory Space**
In the **Creation Phase**, JavaScript stores function and variable declarations in memory before execution.

### **Example: Variable Hoisting**
```js
console.log(x); // undefined (Hoisting)
var x = 10;
console.log(x); // 10
```
- The variable `x` is **hoisted** but **not assigned a value** until execution.
- Hence, it prints `undefined` before `10`.

---

# **Undefined vs. Not Defined**
### **1. Undefined:**
A variable that is declared but not assigned a value.

```js
var a;
console.log(a); // undefined
```

### **2. Not Defined:**
Trying to access a variable that has not been declared at all.

```js
console.log(b); // ReferenceError: b is not defined
```

---

# **Summary**
- The shortest JavaScript program is an **empty file**.
- Even with an empty file, JavaScript creates a **Global Execution Context (GEC)**.
- The **window object** is automatically created in the browser.
- The `this` keyword refers to `window` in the global context.
- JavaScript **hoists** variables and functions before execution.
- `undefined` is different from `not defined`.

📌 **Key Takeaways:**
1. JavaScript is executed inside a **Global Execution Context**.
2. The **window object** is automatically created in the browser.
3. The `this` keyword behaves differently in various contexts.
4. Variables are hoisted and initialized with `undefined`.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Lec-6:undefined vs not defined in JS 🤔
Introduction to undefined in JavaScript
## Undefined as a Special Keyword in JavaScript
- `undefined` is a special keyword in JavaScript.
- It is not present in other programming languages.
- It is closely related to how JavaScript code is executed.
- JavaScript executes code differently by creating a **global execution context** and allocating memory to all variables and functions **before** executing a single line of code.
- `undefined` comes into play during this memory allocation phase.

## Code Example: Understanding undefined in JavaScript
```javascript
console.log(a); // Output: undefined
var a = 7;
console.log(a); // Output: 7
```
### Explanation:
1. JavaScript allocates memory for `a` before executing the code.
2. Before `a` is assigned a value, JavaScript assigns it `undefined` as a **placeholder**.
3. When we log `a` before the assignment, it prints `undefined`.
4. Once `a = 7` is executed, `a` gets the value `7`.

## Debugging Example with the Console Debugger
- If we place a **debugger** before `var a = 7;`, JavaScript has already allocated memory for `a`.
- At this point, `a` is `undefined`.

```javascript
debugger;
var a = 7;
console.log(a);
```
- Before execution reaches `a = 7`, `a` is `undefined`.
- After execution, `a` becomes `7`.

## Difference Between `undefined` and `not defined`
### Example: Not Defined vs Undefined
```javascript
console.log(a); // Output: undefined (memory allocated, but no value assigned)
console.log(x); // ReferenceError: x is not defined
```
- `undefined`: A variable exists but has no assigned value.
- `not defined`: A variable is **never declared** in the program.

## Checking for undefined explicitly
```javascript
var a;
if (a === undefined) {
    console.log("a is undefined");
} else {
    console.log("a is not undefined");
}
```
- Since `a` is declared but not assigned any value, it logs `"a is undefined"`.
- If `a` were assigned a value, the else block would execute.

## Undefined is Not the Same as Empty
- Some think `undefined` means empty, but it is **not**.
- `undefined` **takes up memory** as a placeholder.

```javascript
var a;
console.log(a); // Output: undefined
```
- `undefined` remains in memory until a value is assigned.

## JavaScript as a Loosely Typed Language
- JavaScript does **not** attach a variable to any specific data type.
- Variables can hold any type of value and change types dynamically.

```javascript
var a = "Hello";
a = 10;
a = true;
console.log(a); // Output: true
```
- Unlike strict languages (e.g., C, C++), JavaScript allows reassignment of different data types to the same variable.

## Summary
1. JavaScript assigns `undefined` to variables during memory allocation.
2. `undefined` is **not the same** as `not defined`.
3. JavaScript is **loosely typed**, allowing flexible variable reassignment.
4. `undefined` acts as a placeholder until the variable is assigned a value.
5. Always check for `undefined` when dealing with variable assignments.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Lec-7 notes:Scope Chain, Scope & Lexical Environment in JavaScript**

### **Introduction**
In JavaScript, the concepts of **Scope**, **Scope Chain**, and **Lexical Environment** play a crucial role in how variables and functions are accessed and executed. Understanding these topics helps in writing optimized and bug-free code.

## **Scope**
Scope determines the accessibility (visibility) of variables and functions in JavaScript. There are three types of scope:

1. **Global Scope**: Variables declared outside any function are in the global scope and can be accessed anywhere in the script.
2. **Local Scope (Function Scope)**: Variables declared inside a function are in local scope and are accessible only within that function.
3. **Block Scope**: Introduced with `let` and `const` in ES6, variables declared inside a block (`{}`) cannot be accessed outside that block.

#### **Example:**
```javascript
var globalVar = "I am global";

function testFunction() {
    var localVar = "I am local";
    console.log(globalVar); // Accessible
    console.log(localVar); // Accessible
}

testFunction();
console.log(globalVar); // Accessible
console.log(localVar); // Unaccessible - ReferenceError
```

## **Lexical Environment**
A **Lexical Environment** is created when a function is declared. It consists of:
- Local variables inside the function.
- A reference to its outer lexical environment (where it was declared).

Each execution context has its own Lexical Environment.

#### **Example:**
```javascript
function outerFunction() {
    var outerVar = "I am from outer";
    
    function innerFunction() {
        var innerVar = "I am from inner";
        console.log(outerVar); // Accessible due to lexical environment
        console.log(innerVar); // Accessible
    }
    
    innerFunction();
}
outerFunction();
```

## **Scope Chain**
When JavaScript encounters a variable inside a function, it searches for that variable in the following order:
1. **Local Scope (Function Scope)**
2. **Parent Scope (Outer Function Scope)**
3. **Global Scope**
4. **If not found, it throws a ReferenceError**

#### **Example:**
```javascript
var globalVar = "I am global";

function firstFunction() {
    var firstVar = "I am in first function";
    
    function secondFunction() {
        var secondVar = "I am in second function";
        console.log(secondVar); // Found in local scope
        console.log(firstVar);  // Found in parent scope
        console.log(globalVar); // Found in global scope
    }
    
    secondFunction();
}
firstFunction();
```

### **Behind the Scenes**
When JavaScript executes the code, it creates an **Execution Context**. Each execution context has:
1. **Memory (Variable Environment)** - Where variables and functions are stored.
2. **Code Execution Phase** - Where JavaScript executes the function line by line.

#### **Execution Process Example:**
```javascript
function example() {
    var x = 10;
    var y = 20;
    function innerExample() {
        var z = 30;
        console.log(x + y + z); // Lexical Environment allows access
    }
    innerExample();
}
example();
```

### **Hoisting & Scope**
JavaScript moves function declarations and variable declarations to the top of their scope (hoisting). However, only function declarations are fully hoisted, while variables declared with `var` are hoisted but remain `undefined` until initialized.

#### **Example:**
```javascript
console.log(a); // undefined (hoisted but not assigned)
var a = 5;
console.log(a); // 5
```

### **Conclusion**
- **Scope** defines where a variable can be accessed.
- **Lexical Environment** ensures that inner functions can access outer variables.
- **Scope Chain** helps JavaScript search for variables from the current scope outward.
- Understanding these concepts is crucial for debugging and writing efficient JavaScript code.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Lec-8 notes:Hoisting in JavaScript Of let and const **

Hoisting is a JavaScript behavior where variable and function declarations are moved to the top of their scope before code execution. This means that variables and functions can be used before they are declared. However, the behavior differs for `var`, `let`, and `const`.

### **Hoisting of `var`**
- Variables declared with `var` are hoisted to the top and initialized with `undefined`.

```javascript
console.log(a); // undefined
var a = 10;
console.log(a); // 10
```

Explanation:
- `a` is hoisted and set to `undefined` before execution.
- When `console.log(a)` is called before initialization, it prints `undefined`.

### **Hoisting of `let` and `const`**
- Variables declared with `let` and `const` are hoisted but not initialized. They remain in the **Temporal Dead Zone (TDZ)** until the code execution reaches the declaration.

```javascript
console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 20;
console.log(b); // 20
```

```javascript
console.log(c); // ReferenceError: Cannot access 'c' before initialization
const c = 30;
console.log(c); // 30
```

Explanation:
- `b` and `c` are hoisted but remain in the **Temporal Dead Zone** until they are assigned values.
- Accessing them before declaration results in a `ReferenceError`.

### **Function Hoisting**

1. **Function Declarations**
   - Function declarations are hoisted entirely, meaning they can be called before being defined.

```javascript
greet(); // Output: Hello!
function greet() {
  console.log("Hello!");
}
```

2. **Function Expressions**
   - Function expressions are hoisted, but they behave like `let` and `const` (i.e., not initialized).

```javascript
sayHello(); // TypeError: sayHello is not a function
var sayHello = function() {
  console.log("Hi!");
};
```

### **Temporal Dead Zone (TDZ)**
- The **TDZ** is the period between the hoisting of a variable and its actual initialization.

Example:
```javascript
console.log(x); // ReferenceError
let x = 100;
console.log(x); // 100
```

### **Behind the Scenes: Memory Allocation**
- JavaScript allocates memory for `var`, `let`, and `const` differently.
- `var` is added to the **global execution context** and initialized as `undefined`.
- `let` and `const` are allocated memory in a separate **block scope** and remain in TDZ until initialization.

### **Different Types of Errors in JavaScript**
1. **SyntaxError**: Issues in the structure of the code.
   ```javascript
   let 123name = "John"; // SyntaxError: Unexpected number
   ```

2. **ReferenceError**: Accessing a variable that is not defined.
   ```javascript
   console.log(notDeclaredVar); // ReferenceError: notDeclaredVar is not defined
   ```

3. **TypeError**: When a value is not of the expected type.
   ```javascript
   let num = 10;
   num(); // TypeError: num is not a function
   ```

4. **RangeError**: When a number is out of range.
   ```javascript
   function recurse() {
     return recurse();
   }
   recurse(); // RangeError: Maximum call stack size exceeded
   ```

5. **EvalError**: When `eval()` function is misused (rare in modern JavaScript).

6. **URIError**: Issues with `decodeURI()` or `encodeURI()`.
   ```javascript
   decodeURI("%hello"); // URIError: URI malformed
   ```

   In JavaScript, you can declare variables using `let` and `const`. However, you might encounter an **"assignment to constant variable"** or other **"TypeError"** issues in the following cases:

### 1. **Reassigning a `const` Variable (TypeError: Assignment to constant variable)**
   - `const` variables cannot be reassigned after they are initialized.
   - Example:
     ```javascript
     const x = 10;
     x = 20; // ❌ TypeError: Assignment to constant variable.
     ```
   - **Solution:** Use `let` instead of `const` if you need to reassign the variable.

---

### 2. **Using a `let` or `const` Variable Before Declaration (ReferenceError)**
   - JavaScript has a **temporal dead zone (TDZ)**, meaning you cannot access `let` or `const` before they are declared.
   - Example:
     ```javascript
     console.log(a); // ❌ ReferenceError: Cannot access 'a' before initialization
     let a = 5;
     ```
   - **Solution:** Declare variables before using them.

---

### 3. **Declaring `const` Without Initialization**
   - A `const` variable must always be initialized.
   - Example:
     ```javascript
     const y; // ❌ SyntaxError: Missing initializer in const declaration
     y = 10;
     ```
   - **Solution:** Provide an initial value when declaring `const`.

---

### 4. **Mutating an Object Declared with `const`**
   - `const` does not make objects immutable; it only prevents reassigning the variable reference.
   - Example:
     ```javascript
     const obj = { name: "John" };
     obj.name = "Doe"; // ✅ Allowed
     obj = {}; // ❌ TypeError: Assignment to constant variable.
     ```
   - **Solution:** Use `Object.freeze(obj)` if you want to prevent modifications.

Let me know if you're facing a specific error! 🚀

### **Summary**
- **Hoisting**: `var` is hoisted and initialized as `undefined`, while `let` and `const` are hoisted but stay in the **Temporal Dead Zone**.
- **Function Hoisting**: Function declarations are fully hoisted, while function expressions are not.
- **Errors**: JavaScript has different error types like `SyntaxError`, `ReferenceError`, and `TypeError`, each arising in specific scenarios.

This covers hoisting in JavaScript along with different types of errors and their examples.








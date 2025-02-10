Here are the complete notes from the video transcript, covering all concepts in detail without missing anything:

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








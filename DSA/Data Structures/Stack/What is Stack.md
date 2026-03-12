Stack is a linear data structure which follows the Last In First Out (LIFO) order to arrange elements. Stack data structure opens from only one end so there is only one possible manner to pop (delete an element)  and push (add an element) onto the stack .

A **stack is a disciplined memory region** where:
- Data is added and removed from **one end only**
- Order is strictly enforced
- System can **reliably rewind execution**
- Stack exists to **reverse actions safely**.

### CORE PRINCIPLE – LIFO (WHY THIS RULE EXISTS)

#### Why Last-In, First-Out?

Because:
- Latest task is **closest to completion**
- Nested logic must unwind in reverse

Example:
- Function A calls B
- B calls C

C must finish first → then B → then A
This is **not optional**. It is logical necessity.

### HOW COMPUTER IMPLEMENTS STACK

#### Stack Is NOT Just an Array Conceptually

In real systems:
- Stack is a **dedicated memory region**
- Managed automatically by OS / runtime

Memory layout:
- Stack grows **downwards or upwards** (architecture dependent)

### Stack Pointer (SP)

Computer maintains a register called:

> **Stack Pointer**

It always points to:
- Top of stack

Push:
- Move SP
- Store value

Pop:
- Read value
- Move SP back

This makes stack operations **extremely fast**.

## OPERATIONS ON STACK (COMPLETE LIST)

### 1. Push
Add element to top

### 2. Pop
Remove element from top

### 3. Peek / Top
View top element

### 4. IsEmpty
Check if stack has elements

### 5. IsFull
Check overflow (static stack)

## STACK OVERFLOW & UNDERFLOW (REAL ERRORS)

### Stack Overflow

Occurs when:
- Too many function calls
- Infinite recursion

This is **not theoretical** — it crashes programs.

### Stack Underflow

Occurs when:
- Pop from empty stack

## WHY STACK IS FAST (CPU LEVEL)

- One pointer
- No searching
- Cache-friendly

This is why:
- OS uses stack
- Compilers rely on stack

## WHERE STACK IS USED

1. Function calls
2. Recursion
3. Interrupt handling
4. Expression evaluation
5. Syntax parsing
6. Undo / redo
7. Backtracking

## WHY STACK IS RESTRICTIVE

Restrictions:
- One-end access
- Fixed order

These restrictions:
- Prevent corruption
- Enable predictability

Discipline = safety.
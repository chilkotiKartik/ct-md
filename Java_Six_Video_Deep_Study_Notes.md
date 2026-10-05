# Java — Complete Six-Lecture Study Notes

> **Study standard:** No skipped steps. No filler. No unexplained jumps.
>
> These notes are arranged so that a student can go from **zero → concept → code → dry run → edge cases → exam answer → practice** without needing to guess what comes next.

---

## 0. How This Book Is Structured

Every important topic follows the same learning path:

```text
1. Prerequisite
      ↓
2. What is it?
      ↓
3. Why do we need it?
      ↓
4. Core idea / mental model
      ↓
5. Syntax
      ↓
6. Smallest possible example
      ↓
7. Line-by-line explanation
      ↓
8. Execution / memory flow
      ↓
9. More examples
      ↓
10. Edge cases
      ↓
11. Common mistakes
      ↓
12. Tricks / shortcuts
      ↓
13. Exam-ready answer
      ↓
14. Practice questions
```

### Navigation rules

- Use the **Table of Contents** below instead of scrolling through the entire file.
- `Ctrl + F` terms are deliberately written as explicit headings.
- Every major concept has its own section.
- Related concepts are connected with **See also** links.
- Code comes before complicated theory whenever possible.
- Definitions are kept separate from explanations so they are easy to revise.
- "Exam trap" blocks identify places where students commonly lose marks.
- "Do not skip" blocks identify prerequisite ideas that should be understood first.

---

# 1. Table of Contents

## Part A — Java Foundations

1. [Java Mental Model](#2-java-mental-model)
2. [JDK, JRE, JVM](#3-jdk-jre-jvm)
3. [Compilation and Execution](#4-compilation-and-execution)
4. [Platform Independence](#5-platform-independence)
5. [Java Program Structure](#6-java-program-structure)
6. [Lexical Structure](#7-lexical-structure)
7. [Identifiers](#8-identifiers)
8. [Keywords](#9-keywords)
9. [Literals](#10-literals)
10. [Comments and Whitespace](#11-comments-and-whitespace)

## Part B — Types, Variables and Memory

11. [Data Types](#12-data-types)
12. [Primitive Types](#13-primitive-data-types)
13. [Reference Types](#14-reference-types)
14. [Variables](#15-variables)
15. [Local, Instance and Static Variables](#16-local-instance-and-static-variables)
16. [Default Values](#17-default-values)
17. [Type Conversion](#18-type-conversion)
18. [Widening](#19-widening-conversion)
19. [Narrowing and Casting](#20-narrowing-conversion-and-casting)
20. [Type Promotion](#21-type-promotion)
21. [Overflow](#22-overflow)
22. [Stack and Heap Mental Model](#23-stack-and-heap-mental-model)
23. [References and null](#24-references-and-null)

## Part C — Operators and Expressions

24. [Expressions](#25-expressions)
25. [Arithmetic Operators](#26-arithmetic-operators)
26. [Relational Operators](#27-relational-operators)
27. [Logical Operators](#28-logical-operators)
28. [Short-Circuit Evaluation](#29-short-circuit-evaluation)
29. [Assignment Operators](#30-assignment-operators)
30. [Increment and Decrement](#31-increment-and-decrement)
31. [Ternary Operator](#32-ternary-operator)
32. [Operator Precedence](#33-operator-precedence)
33. [`==` vs `.equals()`](#34--vs-equals)

## Part D — Control Flow

34. [if](#35-if)
35. [if-else](#36-if-else)
36. [else-if](#37-else-if)
37. [switch](#38-switch)
38. [while](#39-while)
39. [do-while](#40-do-while)
40. [for](#41-for)
41. [Enhanced for](#42-enhanced-for)
42. [break](#43-break)
43. [continue](#44-continue)
44. [return](#45-return)

## Part E — Arrays

45. [Arrays](#46-arrays)
46. [Array Declaration and Creation](#47-array-declaration-and-creation)
47. [Array Initialization](#48-array-initialization)
48. [Array Traversal](#49-array-traversal)
49. [Array Length](#50-array-length)
50. [Multidimensional and Jagged Arrays](#51-multidimensional-and-jagged-arrays)

## Part F — Classes and Objects

51. [Class](#52-class)
52. [Object](#53-object)
53. [Reference Variables](#54-reference-variables)
54. [Methods](#55-methods)
55. [Parameters and Arguments](#56-parameters-and-arguments)
56. [Constructors](#57-constructors)
57. [this](#58-this)
58. [Constructor Chaining](#59-constructor-chaining)
59. [Method Overloading](#60-method-overloading)
60. [Recursion](#61-recursion)
61. [Pass-by-Value](#62-pass-by-value)

## Part G — OOP Core

62. [Encapsulation](#63-encapsulation)
63. [Abstraction](#64-abstraction)
64. [Inheritance](#65-inheritance)
65. [super](#66-super)
66. [Method Overriding](#67-method-overriding)
67. [Dynamic Method Dispatch](#68-dynamic-method-dispatch)
68. [Polymorphism](#69-polymorphism)
69. [Abstract Classes](#70-abstract-classes)
70. [Interfaces](#71-interfaces)
71. [Overloading vs Overriding](#72-overloading-vs-overriding)

## Part H — Modifiers and Access

72. [Access Modifiers](#73-access-modifiers)
73. [static](#74-static)
74. [final](#75-final)

## Part I — Memory Management

75. [Garbage Collection](#76-garbage-collection)
76. [Reachability](#77-reachability)
77. [GC Roots](#78-gc-roots)
78. [Eligible vs Collected](#79-eligible-vs-collected)

## Part J — Exceptions

79. [Exception Concept](#80-exception-concept)
80. [Exception Hierarchy](#81-exception-hierarchy)
81. [try-catch](#82-try-catch)
82. [Multiple catch](#83-multiple-catch)
83. [finally](#84-finally)
84. [throw](#85-throw)
85. [throws](#86-throws)
86. [Checked vs Unchecked](#87-checked-vs-unchecked)
87. [Custom Exceptions](#88-custom-exceptions)

## Part K — Packages

88. [Packages](#89-packages)
89. [import](#90-import)
90. [Package Structure](#91-package-structure)

## Part L — Multithreading

91. [Process vs Thread](#92-process-vs-thread)
92. [Thread Creation](#93-thread-creation)
93. [Runnable](#94-runnable)
94. [start vs run](#95-start-vs-run)
95. [Thread States](#96-thread-states)
96. [isAlive](#97-isalive)
97. [join](#98-join)
98. [Race Conditions](#99-race-conditions)
99. [Synchronization](#100-synchronization)
100. [Synchronized Blocks](#101-synchronized-blocks)

## Part M — Programming Practice

101. [Even Number Sum](#102-even-number-sum)
102. [Prime Number](#103-prime-number)
103. [Student Class](#104-student-class)
104. [Static Counter](#105-static-counter)
105. [Dynamic Dispatch Program](#106-dynamic-dispatch-program)
106. [Interface Program](#107-interface-program)
107. [Exception Program](#108-exception-program)
108. [Package Program](#109-package-program)
109. [Two-Thread Program](#110-two-thread-program)

## Part N — Exam and Revision

110. [Output Prediction Method](#111-output-prediction-method)
111. [Theory Answer Method](#112-theory-answer-method)
112. [Common Exam Traps](#113-common-exam-traps)
113. [Rapid Revision](#114-rapid-revision)
114. [Practice Question Bank](#115-practice-question-bank)
115. [Final Master Checklist](#116-final-master-checklist)

---

# 2. Java Mental Model

## 2.1 What Java gives you

Java provides:

- a programming language
- a standard library
- a compiler and development tools
- a runtime environment
- a virtual machine model
- automatic memory management
- object-oriented language features
- exception handling
- concurrency support

The most important mental model is:

```text
.java source file
       |
       | javac
       v
.class bytecode
       |
       | JVM
       v
actual machine execution
```

### Why this matters

If you understand this pipeline, terms such as **bytecode**, **JVM**, **JDK**, **JRE**, and **platform independence** stop being separate memorisation questions.

---

# 3. JDK, JRE, JVM

## Definition

### JVM
The **Java Virtual Machine** executes Java bytecode.

### JRE
The **Java Runtime Environment** provides the runtime components needed to run Java applications.

### JDK
The **Java Development Kit** provides development tools, including the compiler, together with the runtime components.

## Memory trick

```text
JDK = Develop
JRE = Run
JVM = Execute
```

## Exam answer

> JVM executes bytecode. JRE provides the runtime environment. JDK provides the tools required to develop Java programs in addition to runtime components.

---

# 4. Compilation and Execution

Consider:

```java
class Hello {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

Save:

```text
Hello.java
```

Compile:

```bash
javac Hello.java
```

This normally produces:

```text
Hello.class
```

Run:

```bash
java Hello
```

### Step-by-step

```text
Hello.java
   |
   | compiler
   v
Hello.class
   |
   | JVM loads bytecode
   v
execution
```

### Important distinction

`javac` compiles.

`java` launches the application through the JVM.

---

# 5. Platform Independence

## Claim

Java is commonly described as platform independent because Java source is compiled to bytecode that can run on different operating systems through appropriate JVM implementations.

```text
             Program.class
             /     |      \
            /      |       \
        JVM-Win  JVM-Linux JVM-macOS
           |        |         |
        Windows    Linux     macOS
```

### Exact exam wording

> Java bytecode is platform independent, while JVM implementations are platform dependent.

### Do not write

> JVM is platform independent.

That statement is inaccurate.

---

# 6. Java Program Structure

Minimum example:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

## Break every part

### `public`

Makes the class/method accessible according to Java access rules.

### `class`

Declares a class.

### `Main`

Class name.

### `{ }`

Defines a block.

### `public static void main(String[] args)`

The conventional application entry point.

### `System.out.println(...)`

Prints text followed by a line break.

### `;`

Terminates a statement.

---

# 7. Lexical Structure

Java source code is made from tokens such as:

```text
keywords
identifiers
literals
operators
separators
comments
```

Example:

```java
int total = 50;
```

Tokens:

```text
int       -> keyword
total     -> identifier
=         -> operator
50        -> literal
;         -> separator
```

This is the foundation for understanding how Java reads source code.

---

# 8. Identifiers

An identifier names a program element.

Examples:

```java
Student
studentName
calculateTotal
MAX_SIZE
```

## Rules

- Cannot begin with a digit.
- Cannot be a Java keyword.
- Java is case-sensitive.
- `_` and `$` are permitted characters, although `$` is generally avoided in ordinary application naming.

Valid:

```java
student
student1
_student
```

Invalid:

```java
1student
class
student-name
```

## Best practice

Use:

```java
class StudentRecord
int totalMarks
void calculateAverage()
```

---

# 9. Keywords

Keywords have predefined language meaning.

Examples:

```text
class
public
private
protected
static
final
void
int
if
else
switch
for
while
return
new
this
super
extends
implements
try
catch
finally
throw
throws
package
import
interface
abstract
synchronized
```

A keyword cannot normally be used as an identifier.

---

# 10. Literals

A literal is a value written directly in source code.

```java
10
3.14
'A'
true
"Java"
null
```

## Categories

| Literal | Example |
|---|---|
| Integer | `10` |
| Floating point | `3.14` |
| Character | `'A'` |
| String | `"Java"` |
| Boolean | `true` |
| Null | `null` |

---

# 11. Comments and Whitespace

## Single-line

```java
// This is a comment
```

## Multi-line

```java
/*
   This is a
   multi-line comment.
*/
```

Comments explain source code to humans and are ignored as executable instructions.

Whitespace usually improves readability and separates tokens.

---

# 12. Data Types

Java data types determine what kind of value a variable can represent and what operations/conversions are available.

Two broad categories:

```text
Data Types
 |
 +-- Primitive
 |
 +-- Reference
```

---

# 13. Primitive Data Types

Java has eight primitive types:

| Type | Common size | Example |
|---|---:|---|
| `byte` | 8-bit | `byte x = 10;` |
| `short` | 16-bit | `short x = 10;` |
| `int` | 32-bit | `int x = 10;` |
| `long` | 64-bit | `long x = 10L;` |
| `float` | 32-bit | `float x = 10.5f;` |
| `double` | 64-bit | `double x = 10.5;` |
| `char` | 16-bit UTF-16 code unit | `char x = 'A';` |
| `boolean` | language-defined | `boolean x = true;` |

## Easy grouping

```text
Integer:
byte short int long

Floating:
float double

Character:
char

Logical:
boolean
```

---

# 14. Reference Types

Examples:

```java
String
Student
int[]
Student[]
Object
```

A reference variable refers to an object or array rather than storing a primitive value directly.

Example:

```java
Student s = new Student();
```

Mental model:

```text
s  -------->  Student object
reference       object
```

---

# 15. Variables

A variable associates a name with a value/reference of a declared type.

```java
int marks = 85;
```

Breakdown:

```text
int       -> type
marks     -> variable
=         -> assignment
85        -> value
```

Declaration:

```java
int marks;
```

Initialization:

```java
marks = 85;
```

Combined:

```java
int marks = 85;
```

---

# 16. Local, Instance and Static Variables

## Local variable

Declared inside a method/block.

```java
void test() {
    int x = 10;
}
```

It must be definitely assigned before use.

## Instance variable

Declared in a class without `static`.

```java
class Student {
    int age;
}
```

Each object normally has its own `age`.

## Static variable

Declared with `static`.

```java
class Student {
    static String college = "ABC";
}
```

The variable belongs to the class.

---

# 17. Default Values

Fields receive default values during initialization.

| Type | Typical default |
|---|---|
| integer types | `0` |
| floating types | `0.0` |
| `char` | `'\u0000'` |
| `boolean` | `false` |
| reference | `null` |

## Local variable trap

This is invalid:

```java
void test() {
    int x;
    System.out.println(x);
}
```

The compiler requires definite assignment.

### Remember

> **Fields get defaults; local variables must be definitely assigned before use.**

---

# 18. Type Conversion

Type conversion changes a value/expression from one compatible type to another.

Two important directions:

```text
Widening
Narrowing
```

---

# 19. Widening Conversion

Example:

```java
int x = 100;
long y = x;
```

The conversion is from a narrower range/type to a wider compatible numeric type.

Another:

```java
int x = 10;
double d = x;
```

### Memory trick

> **Widening → usually automatic → usually less risk of information loss.**

---

# 20. Narrowing Conversion and Casting

Example:

```java
double d = 10.75;
int x = (int) d;
```

Result:

```text
10
```

The fractional part is discarded.

Syntax:

```java
(targetType) expression
```

Example:

```java
int x = (int) 10.99;
```

### Important

Casting to `int` does not mean mathematical rounding.

```text
10.99 -> 10
```

---

# 21. Type Promotion

This is one of the most important exam concepts.

Consider:

```java
byte a = 10;
byte b = 20;
```

Now:

```java
a + b
```

is generally promoted to `int`.

Therefore:

```java
int c = a + b;
```

works.

But:

```java
byte c = a + b;
```

does not compile without an appropriate cast.

## Key rule

In many arithmetic expressions:

```text
byte -> int
short -> int
char -> int
```

### Exam trick

Always ask:

> **What is the type of the expression after promotion?**

not merely:

> "What are the types of the variables?"

---

# 22. Overflow

Fixed-width integer types have finite ranges.

Example:

```java
byte b = 127;
b++;
```

The result does not become an arbitrarily large `byte`; it wraps according to Java's integer arithmetic rules.

### Exam strategy

If an output question uses `byte`, `short`, or integer boundaries:

1. Determine the type.
2. Determine the valid range.
3. Determine whether arithmetic promotion happens.
4. Apply the resulting conversion/assignment rules.

---

# 23. Stack and Heap Mental Model

Use this model for learning:

```text
STACK                         HEAP
-------------------           --------------------
method frames                 objects
local variables               arrays
references                    instance state
```

Example:

```java
Student s = new Student();
```

Conceptually:

```text
STACK                         HEAP

s -------------------------> Student object
                             name
                             age
```

### Important qualification

This is a **conceptual JVM study model**, not a promise that every JVM implementation physically represents every value exactly this way.

---

# 24. References and `null`

A reference can hold:

```java
null
```

Example:

```java
Student s = null;
```

This means the reference does not currently refer to a `Student` object.

Then:

```java
s.display();
```

causes a `NullPointerException` when executed.

---

# 25. Expressions

An expression produces a value.

Examples:

```java
a + b
x > 10
age >= 18 && hasId
x++
condition ? a : b
```

Statements often contain expressions:

```java
int result = a + b;
```

---

# 26. Arithmetic Operators

```text
+  -  *  /  %
```

Example:

```java
int a = 10;
int b = 3;

a + b  // 13
a - b  // 7
a * b  // 30
a / b  // 3
a % b  // 1
```

## Critical trap

```java
5 / 2
```

produces:

```text
2
```

because both operands are integer values.

But:

```java
5 / 2.0
```

produces:

```text
2.5
```

---

# 27. Relational Operators

```text
< > <= >= == !=
```

They produce boolean results.

```java
10 < 20
```

Result:

```text
true
```

---

# 28. Logical Operators

```text
&&  AND
||  OR
!   NOT
```

Example:

```java
boolean adult = age >= 18;
boolean hasId = true;

if (adult && hasId) {
    System.out.println("Allowed");
}
```

---

# 29. Short-Circuit Evaluation

## `&&`

If the left side is false, the right side does not need to be evaluated.

```java
x != 0 && 10 / x > 1
```

If:

```java
x == 0
```

the division is not evaluated.

## `||`

If the left side is true, the right side does not need to be evaluated.

### Memory trick

```text
&& -> FALSE stops
|| -> TRUE stops
```

---

# 30. Assignment Operators

```text
=
+=
-=
*=
/=
%=
```

Example:

```java
int x = 10;
x += 5;
```

Conceptually:

```java
x = x + 5;
```

---

# 31. Increment and Decrement

```text
++x  pre-increment
x++  post-increment
--x  pre-decrement
x--  post-decrement
```

Example:

```java
int x = 5;
int y = x++;
```

Evaluate:

1. Use current `x` value for the expression.
2. Assign `5` to `y`.
3. Increment `x`.
4. Final state: `x = 6`, `y = 5`.

Pre-increment:

```java
int x = 5;
int y = ++x;
```

Steps:

1. Increment `x`.
2. `x = 6`.
3. Use `6` for the expression.
4. `y = 6`.

---

# 32. Ternary Operator

Syntax:

```java
condition ? trueValue : falseValue
```

Example:

```java
int max = (a > b) ? a : b;
```

Equivalent conceptual logic:

```java
int max;

if (a > b) {
    max = a;
} else {
    max = b;
}
```

---

# 33. Operator Precedence

For complex expressions, never guess.

Example:

```java
int x = 2 + 3 * 4;
```

Multiplication first:

```text
2 + (3 * 4)
= 14
```

### Safe strategy

Use parentheses when writing code:

```java
int x = 2 + (3 * 4);
```

When solving exam questions, explicitly parenthesize the expression on paper.

---

# 34. `==` vs `.equals()`

## Primitive

```java
int a = 10;
int b = 10;

a == b
```

compares values.

## References

```java
Student a = new Student();
Student b = new Student();

a == b
```

checks whether both references identify the same object.

## `.equals()`

For objects:

```java
a.equals(b)
```

uses the class's implementation/contract for logical equality.

Example:

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);       // false
System.out.println(a.equals(b));  // true
```

### Golden rule

```text
==       -> primitive value comparison / reference identity
.equals  -> logical equality according to class contract
```

---

# 35. `if`

Syntax:

```java
if (condition) {
    // statements
}
```

Example:

```java
if (marks >= 40) {
    System.out.println("Pass");
}
```

The condition must produce a boolean result.

---

# 36. `if-else`

```java
if (marks >= 40) {
    System.out.println("Pass");
} else {
    System.out.println("Fail");
}
```

Exactly one branch is selected in this simple structure.

---

# 37. `else-if`

Use when there are multiple conditions.

```java
if (marks >= 90) {
    grade = 'A';
} else if (marks >= 75) {
    grade = 'B';
} else if (marks >= 60) {
    grade = 'C';
} else {
    grade = 'D';
}
```

### Important

Order matters.

If the highest threshold is not checked first, a broader condition can capture the value too early.

---

# 38. `switch`

Example:

```java
switch (day) {
    case 1:
        System.out.println("Monday");
        break;

    case 2:
        System.out.println("Tuesday");
        break;

    default:
        System.out.println("Invalid");
}
```

## Execution steps

1. Evaluate switch expression.
2. Find matching case.
3. Execute statements.
4. `break` exits the switch.
5. If no case matches, `default` is considered.

## Fall-through

Without `break`, execution can continue into following cases.

---

# 39. `while`

```java
while (condition) {
    // body
}
```

Execution:

```text
check condition
      |
      +-- false --> stop
      |
     true
      |
      v
    body
      |
      +------> check again
```

Can execute zero times.

---

# 40. `do-while`

```java
do {
    // body
} while (condition);
```

Execution:

```text
body
 |
 v
condition
 |
 +-- true --> body
 |
 +-- false -> stop
```

The body executes at least once.

### Memory trick

```text
while     -> check → execute
do-while  -> execute → check
```

---

# 41. `for`

```java
for (initialization; condition; update) {
    // body
}
```

Example:

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

Exact order:

```text
initialization
      ↓
condition
      ↓
body
      ↓
update
      ↓
condition
```

---

# 42. Enhanced `for`

```java
int[] numbers = {10, 20, 30};

for (int n : numbers) {
    System.out.println(n);
}
```

Use it when direct traversal is enough.

Use an indexed loop when you need the index:

```java
for (int i = 0; i < numbers.length; i++) {
    System.out.println(i + " -> " + numbers[i]);
}
```

---

# 43. `break`

Terminates the nearest applicable loop or switch.

```java
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break;
    }
}
```

The loop stops when `i == 5`.

---

# 44. `continue`

Skips the remainder of the current iteration.

```java
for (int i = 1; i <= 5; i++) {
    if (i % 2 != 0) {
        continue;
    }

    System.out.println(i);
}
```

Output:

```text
2
4
```

---

# 45. `return`

Ends the current method.

```java
int add(int a, int b) {
    return a + b;
}
```

A `return` statement may return a value or simply return from a `void` method.

---

# 46. Arrays

An array stores a fixed-size sequence of elements of the same component type.

```java
int[] marks = new int[5];
```

Conceptually:

```text
index   0    1    2    3    4
       +----+----+----+----+----+
       |    |    |    |    |    |
       +----+----+----+----+----+
```

Indexes start at `0`.

Last valid index:

```text
length - 1
```

---

# 47. Array Declaration and Creation

Declaration:

```java
int[] a;
```

Creation:

```java
a = new int[5];
```

Combined:

```java
int[] a = new int[5];
```

---

# 48. Array Initialization

Initializer syntax:

```java
int[] a = {10, 20, 30};
```

The array length is inferred as `3`.

Equivalent conceptual layout:

```text
a[0] = 10
a[1] = 20
a[2] = 30
```

---

# 49. Array Traversal

Indexed:

```java
for (int i = 0; i < a.length; i++) {
    System.out.println(a[i]);
}
```

Enhanced:

```java
for (int value : a) {
    System.out.println(value);
}
```

### Exam trap

Do not write:

```java
i <= a.length
```

Use:

```java
i < a.length
```

because the last valid index is `a.length - 1`.

---

# 50. Array Length

Array:

```java
a.length
```

String:

```java
s.length()
```

This is a high-frequency exam trap.

---

# 51. Multidimensional and Jagged Arrays

Two-dimensional:

```java
int[][] matrix = new int[3][4];
```

Java's multidimensional arrays are arrays of arrays.

Jagged:

```java
int[][] a = new int[3][];

a[0] = new int[2];
a[1] = new int[4];
a[2] = new int[1];
```

Rows can have different lengths.

---

# 52. Class

A class defines a type.

```java
class Student {
    String name;
    int age;

    void study() {
        System.out.println(name + " is studying");
    }
}
```

A class can contain:

- fields
- methods
- constructors
- nested types
- initialization blocks

---

# 53. Object

An object is an instance of a class.

```java
Student s = new Student();
```

Conceptually:

```text
class Student
      |
      | new
      v
Student object
```

---

# 54. Reference Variables

For:

```java
Student s = new Student();
```

think:

```text
s
|
| reference
v
+----------------+
| Student object |
+----------------+
```

Now:

```java
Student a = new Student();
Student b = a;
```

means:

```text
a ----+
      |
      v
    object
      ^
      |
b ----+
```

Both variables refer to the same object.

---

# 55. Methods

A method defines behaviour.

```java
int add(int a, int b) {
    return a + b;
}
```

Parts:

```text
return type -> int
name        -> add
parameters  -> int a, int b
body        -> { ... }
```

---

# 56. Parameters and Arguments

Parameter:

```java
int add(int a, int b)
```

`a` and `b` are parameters.

Argument:

```java
add(10, 20);
```

`10` and `20` are arguments.

### Easy distinction

```text
parameter -> appears in method definition
argument  -> value supplied during call
```

---

# 57. Constructors

A constructor initializes a newly created object.

```java
class Student {
    String name;

    Student(String name) {
        this.name = name;
    }
}
```

Create:

```java
Student s = new Student("Kartik");
```

## Constructor rules

- Same name as class.
- No return type.
- Runs during object construction.
- Can be overloaded.
- Is not inherited as an ordinary method.

### Trap

```java
void Student() {
}
```

This is a method, not a constructor.

---

# 58. `this`

`this` refers to the current object in an instance context.

```java
class Student {
    String name;

    Student(String name) {
        this.name = name;
    }
}
```

Left side:

```java
this.name
```

means the current object's field.

Right side:

```java
name
```

means the constructor parameter.

---

# 59. Constructor Chaining

```java
class Student {
    String name;
    int age;

    Student() {
        this("Unknown", 0);
    }

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

`this(...)` calls another constructor in the same class.

It must be the first statement in the constructor.

---

# 60. Method Overloading

Same method name with different parameter lists.

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

## What may differ?

- number of parameters
- parameter types
- order of parameter types

## What is NOT enough?

Only changing return type:

```java
int add(int a, int b) { ... }
double add(int a, int b) { ... } // invalid overload
```

---

# 61. Recursion

A recursive method calls itself.

```java
static int factorial(int n) {
    if (n <= 1) {
        return 1;
    }

    return n * factorial(n - 1);
}
```

## Every recursive solution needs

1. Base case.
2. Recursive case.
3. Progress toward the base case.

### Trace `factorial(4)`

```text
factorial(4)
= 4 * factorial(3)
= 4 * 3 * factorial(2)
= 4 * 3 * 2 * factorial(1)
= 4 * 3 * 2 * 1
= 24
```

---

# 62. Pass-by-Value

Java is pass-by-value.

For primitive:

```java
static void change(int x) {
    x = 100;
}
```

Changing `x` does not change the caller's variable.

For an object:

```java
static void change(Box b) {
    b.value = 100;
}
```

The copied value is the reference, so the method can mutate the object through that reference.

But reassigning the parameter:

```java
static void replace(Box b) {
    b = new Box();
}
```

does not replace the caller's reference.

### Golden rule

> Java always passes a value. For an object, that value is the reference value.

---

# 63. Encapsulation

Encapsulation combines state and behaviour and controls access to internal state.

Bad:

```java
class BankAccount {
    public double balance;
}
```

Better:

```java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

## Why?

The class can enforce rules:

```text
caller
  |
  v
deposit()
  |
  +-- validate amount
  |
  +-- update balance
```

Encapsulation is more than merely adding getters/setters.

---

# 64. Abstraction

Abstraction exposes what a user needs and hides unnecessary implementation details.

Example:

```java
interface Payment {
    void pay(double amount);
}
```

A caller can depend on:

```java
Payment
```

without needing to know every internal implementation detail.

---

# 65. Inheritance

Inheritance allows a class to derive from another class.

```java
class Animal {
    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking");
    }
}
```

Relationship:

```text
Dog IS-A Animal
```

This is why inheritance is commonly used for an **IS-A** relationship.

---

# 66. `super`

`super` refers to the parent-class part of the current object.

## Parent field

```java
class Animal {
    String name = "Animal";
}

class Dog extends Animal {
    String name = "Dog";

    void show() {
        System.out.println(name);
        System.out.println(super.name);
    }
}
```

Output:

```text
Dog
Animal
```

## Parent method

```java
super.sound();
```

## Parent constructor

```java
super();
```

A constructor invocation using `super(...)` must occur first in the constructor.

---

# 67. Method Overriding

A child class provides a compatible replacement implementation for an inherited instance method.

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

Use `@Override` because it lets the compiler verify that you really are overriding a parent method.

---

# 68. Dynamic Method Dispatch

Consider:

```java
Animal a = new Dog();
a.sound();
```

Separate the two types:

```text
Reference type = Animal
Object type    = Dog
```

The reference type controls what members are available through the reference.

For an overridden instance method, runtime dispatch selects the implementation associated with the actual object.

Therefore:

```text
Dog.sound()
```

runs.

---

# 69. Polymorphism

Polymorphism means that one common type/interface can represent objects with different implementations.

```java
Animal a;

a = new Dog();
a.sound();

a = new Cat();
a.sound();
```

Same reference type:

```text
Animal
```

Different runtime behaviour:

```text
Dog.sound()
Cat.sound()
```

---

# 70. Abstract Classes

```java
abstract class Shape {
    abstract double area();

    void display() {
        System.out.println("Shape");
    }
}
```

A subclass provides the missing implementation:

```java
class Circle extends Shape {
    private double radius;

    Circle(double radius) {
        this.radius = radius;
    }

    @Override
    double area() {
        return Math.PI * radius * radius;
    }
}
```

An abstract class can contain:

- abstract methods
- concrete methods
- fields
- constructors

It cannot normally be instantiated directly.

---

# 71. Interfaces

Interface:

```java
interface Shape {
    double area();
}
```

Implementation:

```java
class Circle implements Shape {
    public double area() {
        return Math.PI * 10 * 10;
    }
}
```

Mental model:

```text
interface = contract/type
class     = implementation
```

A class can implement multiple interfaces.

---

# 72. Overloading vs Overriding

| Point | Overloading | Overriding |
|---|---|---|
| Main purpose | Multiple parameter forms | Specialized inherited behaviour |
| Parameters | Must differ | Compatible overridden signature |
| Inheritance required | No | Yes |
| Main binding idea | Compile time | Runtime dispatch |
| Typical annotation | None | `@Override` |

### Memory trick

```text
OVERLOAD = same name, different parameter list
OVERRIDE = child changes inherited implementation
```

---

# 73. Access Modifiers

| Modifier | Same class | Same package | Subclass outside package | Everywhere |
|---|---:|---:|---:|---:|
| `private` | Yes | No | No | No |
| package-private | Yes | Yes | Not as ordinary package access | No |
| `protected` | Yes | Yes | Yes, under protected-access rules | No |
| `public` | Yes | Yes | Yes | Yes |

Use the most restrictive visibility that meets the design requirement.

---

# 74. `static`

Static members belong to the class rather than an individual object.

```java
class Counter {
    static int count = 0;

    Counter() {
        count++;
    }
}
```

Then:

```java
new Counter();
new Counter();

System.out.println(Counter.count);
```

prints:

```text
2
```

because the field is shared.

---

# 75. `final`

## Final variable

```java
final int MAX = 100;
```

Cannot be reassigned after initialization.

## Final method

Cannot be overridden.

## Final class

Cannot be extended.

```java
final class SecurityManager {
}
```

### Memory trick

```text
final variable -> no reassignment
final method   -> no overriding
final class    -> no inheritance
```

---

# 76. Garbage Collection

Java automatically manages memory for objects that become unreachable.

Example:

```java
Student s = new Student();
s = null;
```

If no other reachable reference points to the object, the object may become eligible for garbage collection.

### Important wording

```text
eligible for GC != immediately collected
```

The JVM controls actual collection.

---

# 77. Reachability

Conceptual graph:

```text
GC Root
   |
   v
Object A
   |
   v
Object B
```

Both are reachable.

If all references to Object B disappear:

```text
GC Root -> Object A

Object B
(no path from root)
```

Object B may become eligible for collection.

---

# 78. GC Roots

For study purposes, think of GC roots as starting points from which reachable objects are discovered.

The important idea is:

```text
reachable -> retained
unreachable -> potentially collectible
```

Do not reduce garbage collection to "objects with null variables"; reachability can involve object-to-object references.

---

# 79. Eligible vs Collected

This distinction is essential.

Bad statement:

> Setting an object to `null` immediately deletes it.

Correct idea:

> If an object becomes unreachable, it may become eligible for garbage collection; collection timing is controlled by the JVM.

Similarly:

```java
System.gc();
```

does not provide a guarantee that collection immediately occurs.

---

# 80. Exception Concept

An exception is an event/condition that disrupts normal program flow.

Example:

```java
int x = 10 / 0;
```

The program cannot complete that operation normally.

Exception handling lets a program detect/propagate/handle such conditions.

---

# 81. Exception Hierarchy

Simplified:

```text
Object
  |
Throwable
  |
  +---- Error
  |
  +---- Exception
          |
          +---- RuntimeException
```

Examples:

```text
ArithmeticException
NullPointerException
ArrayIndexOutOfBoundsException
NumberFormatException
IOException
```

---

# 82. `try-catch`

```java
try {
    int x = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

Execution:

```text
try begins
   |
   v
exception occurs
   |
   v
matching catch
   |
   v
handler executes
```

---

# 83. Multiple Catch

```java
try {
    // risky code
} catch (ArithmeticException e) {
    // arithmetic
} catch (ArrayIndexOutOfBoundsException e) {
    // array index
}
```

### Ordering

Specific exceptions should be handled before their broader superclass.

Bad:

```java
catch (Exception e) {
}
catch (ArithmeticException e) {
}
```

The second catch is unreachable.

---

# 84. `finally`

```java
try {
    // work
} catch (Exception e) {
    // handling
} finally {
    // cleanup
}
```

`finally` is intended for cleanup code and normally executes when control leaves the try/catch construct, subject to exceptional termination scenarios.

For resource management, modern Java commonly prefers try-with-resources.

---

# 85. `throw`

Explicitly throws an exception:

```java
throw new IllegalArgumentException("Invalid age");
```

Think:

```text
throw = perform the throw
```

---

# 86. `throws`

Declares that a method can propagate specified exceptions:

```java
void readFile() throws IOException {
    ...
}
```

Think:

```text
throws = declare possible propagation
```

---

# 87. Checked vs Unchecked

## Checked

The compiler requires the program to handle or declare checked exceptions according to Java's rules.

Example:

```java
IOException
```

## Unchecked

Runtime exceptions, subclasses of `RuntimeException`.

Examples:

```java
NullPointerException
ArithmeticException
NumberFormatException
```

### Memory trick

```text
checked   -> compiler checks handling/declaring
unchecked -> compiler does not require handling/declaring
```

---

# 88. Custom Exceptions

```java
class InvalidAgeException extends Exception {
    InvalidAgeException(String message) {
        super(message);
    }
}
```

Use:

```java
static void checkAge(int age) throws InvalidAgeException {
    if (age < 18) {
        throw new InvalidAgeException("Age must be at least 18");
    }
}
```

This lets the application communicate domain-specific failures clearly.

---

# 89. Packages

A package groups related types and provides a namespace.

```java
package shape;
```

Benefits:

- organization
- namespace separation
- access control
- modular structure

---

# 90. `import`

If a type is in another package, it can be imported:

```java
import shape.Rectangle;
```

Then:

```java
Rectangle r = new Rectangle();
```

An import makes a type name convenient to use; it does not copy the class into your program.

---

# 91. Package Structure

Typical:

```text
src/
└── shape/
    └── Rectangle.java
```

File:

```java
package shape;

public class Rectangle {
}
```

Another file:

```java
import shape.Rectangle;

public class Main {
    public static void main(String[] args) {
        Rectangle r = new Rectangle();
    }
}
```

The package declaration and normal project directory layout correspond.

---

# 92. Process vs Thread

A process is a running program/application instance with its own execution resources.

A thread is a path of execution within a process.

Conceptually:

```text
Process
 |
 +-- main thread
 +-- worker thread
 +-- worker thread
```

Multiple threads can perform work concurrently.

---

# 93. Thread Creation

One traditional approach:

```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Running");
    }
}
```

Then:

```java
MyThread t = new MyThread();
t.start();
```

---

# 94. Runnable

```java
class Task implements Runnable {
    @Override
    public void run() {
        System.out.println("Task running");
    }
}
```

Create:

```java
Thread t = new Thread(new Task());
t.start();
```

This separates:

```text
task = Runnable
thread = Thread
```

It is often preferable when the class already needs to extend another class.

---

# 95. `start()` vs `run()`

This is a major exam trap.

```java
t.start();
```

asks the runtime to start a new thread of execution.

```java
t.run();
```

is simply an ordinary method invocation if called directly.

### Memory trick

```text
start() -> start thread
run()   -> execute task body
```

---

# 96. Thread States

Java's `Thread.State` includes:

```text
NEW
RUNNABLE
BLOCKED
WAITING
TIMED_WAITING
TERMINATED
```

A simplified learning flow:

```text
NEW
 |
 | start()
 v
RUNNABLE
 |
 +--> waiting/blocking states
 |
 v
TERMINATED
```

Do not confuse simplified textbook lifecycle drawings with the exact Java API state model.

---

# 97. `isAlive()`

```java
t.isAlive()
```

checks whether the thread has started and has not yet terminated.

Example:

```java
Thread t = new Thread(task);

System.out.println(t.isAlive()); // normally false before start

t.start();

System.out.println(t.isAlive()); // may be true while running
```

Exact timing depends on scheduling.

---

# 98. `join()`

`join()` causes the calling thread to wait for the target thread to finish.

```java
t.start();
t.join();

System.out.println("Thread finished");
```

If `main` calls `join()`, the main thread waits for `t`.

---

# 99. Race Conditions

Suppose:

```java
count++;
```

is executed by two threads.

Conceptually:

```text
Thread A: read 5
Thread B: read 5
Thread A: write 6
Thread B: write 6
```

Expected after two increments:

```text
7
```

Possible actual result:

```text
6
```

This is a race/lost-update scenario.

---

# 100. Synchronization

A critical section can be protected:

```java
synchronized void increment() {
    count++;
}
```

For an instance synchronized method, the object's intrinsic monitor is used.

The goal is to ensure appropriate mutual exclusion around shared state.

### Trade-offs

Synchronization can cause:

- contention
- reduced concurrency
- deadlocks if multiple locks are acquired poorly
- performance overhead

---

# 101. Synchronized Blocks

```java
synchronized (this) {
    count++;
}
```

A synchronized block lets you limit the protected region.

General form:

```java
synchronized (lockObject) {
    // critical section
}
```

Choosing the lock object carefully is important.

---

# 102. Even Number Sum

## Problem

Find the sum of even numbers from 1 to 100.

## Code

```java
public class EvenSum {
    public static void main(String[] args) {
        int sum = 0;

        for (int i = 1; i <= 100; i++) {
            if (i % 2 != 0) {
                continue;
            }

            sum += i;
        }

        System.out.println(sum);
    }
}
```

## Dry run idea

```text
i = 1 -> odd -> continue
i = 2 -> even -> sum = 2
i = 3 -> odd -> continue
i = 4 -> even -> sum = 6
...
```

## Key concepts

- `for`
- `%`
- `if`
- `continue`
- assignment

---

# 103. Prime Number

```java
public class PrimeCheck {
    public static void main(String[] args) {
        int n = 29;
        boolean prime = n >= 2;

        for (int i = 2; i * i <= n && prime; i++) {
            if (n % i == 0) {
                prime = false;
            }
        }

        System.out.println(prime ? "Prime" : "Not Prime");
    }
}
```

## Why `i * i <= n`?

If a composite number has a factor larger than its square root, it must also have a corresponding factor smaller than its square root.

Therefore checking through `sqrt(n)` is enough.

---

# 104. Student Class

```java
class Student {
    private String name;
    private int rollNumber;

    Student(String name, int rollNumber) {
        this.name = name;
        this.rollNumber = rollNumber;
    }

    void displayDetails() {
        System.out.println("Name: " + name);
        System.out.println("Roll Number: " + rollNumber);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s = new Student("Aman", 101);
        s.displayDetails();
    }
}
```

## Concepts covered

```text
class
object
private
constructor
this
instance fields
method
encapsulation
```

---

# 105. Static Counter

```java
class Counter {
    static int count = 0;

    Counter() {
        count++;
    }
}

public class Main {
    public static void main(String[] args) {
        new Counter();
        new Counter();
        new Counter();

        System.out.println(Counter.count);
    }
}
```

Output:

```text
3
```

Reason:

```text
count is static
      ↓
one shared class-level field
      ↓
each constructor increments same field
```

---

# 106. Dynamic Dispatch Program

```java
class Shape {
    void area() {
        System.out.println("Generic area");
    }
}

class Circle extends Shape {
    @Override
    void area() {
        System.out.println("Circle area");
    }
}

class Rectangle extends Shape {
    @Override
    void area() {
        System.out.println("Rectangle area");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape s;

        s = new Circle();
        s.area();

        s = new Rectangle();
        s.area();
    }
}
```

Output:

```text
Circle area
Rectangle area
```

The reference type stays `Shape`, while the actual object changes.

---

# 107. Interface Program

```java
interface Shape {
    double area();
    double perimeter();
}

class Rectangle implements Shape {
    private double length;
    private double width;

    Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }

    @Override
    public double area() {
        return length * width;
    }

    @Override
    public double perimeter() {
        return 2 * (length + width);
    }
}

public class Main {
    public static void main(String[] args) {
        Shape s = new Rectangle(10, 5);

        System.out.println(s.area());
        System.out.println(s.perimeter());
    }
}
```

Concepts:

```text
interface
implements
constructor
this
encapsulation
overriding
polymorphism
```

---

# 108. Exception Program

```java
public class ExceptionDemo {
    public static void main(String[] args) {
        try {
            int[] a = {10, 20, 30};
            System.out.println(a[10]);

        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Invalid array index");

        } finally {
            System.out.println("Cleanup section");
        }
    }
}
```

Execution:

```text
try
 ↓
exception
 ↓
matching catch
 ↓
finally
```

---

# 109. Package Program

## `shape/Rectangle.java`

```java
package shape;

public class Rectangle {
    public double area(double length, double width) {
        return length * width;
    }

    public double perimeter(double length, double width) {
        return 2 * (length + width);
    }
}
```

## `Main.java`

```java
import shape.Rectangle;

public class Main {
    public static void main(String[] args) {
        Rectangle r = new Rectangle();

        System.out.println(r.area(10, 5));
        System.out.println(r.perimeter(10, 5));
    }
}
```

---

# 110. Two-Thread Program

```java
class NumberThread extends Thread {
    @Override
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }
    }
}

class LetterThread extends Thread {
    @Override
    public void run() {
        for (char c = 'A'; c <= 'E'; c++) {
            System.out.println(c);
        }
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        Thread t1 = new NumberThread();
        Thread t2 = new LetterThread();

        t1.start();
        t2.start();

        t1.join();
        t2.join();

        System.out.println("Both finished");
    }
}
```

### Important

Do not assume a fixed interleaving such as:

```text
1
A
2
B
...
```

The scheduler determines execution order.

---

# 111. Output Prediction Method

When an exam asks for output, use this exact workflow.

## Step 1 — Mark every variable's type

Example:

```java
byte a = 10;
int b = 20;
```

## Step 2 — Mark initial values

```text
a = 10
b = 20
```

## Step 3 — Resolve parentheses

## Step 4 — Resolve pre/post increment carefully

## Step 5 — Apply type promotion

## Step 6 — Apply operator precedence

## Step 7 — Resolve method selection

Ask:

```text
overloading?
overriding?
static?
instance?
```

## Step 8 — Trace branches/loops

## Step 9 — Check for exceptions

## Step 10 — Write final output

Never jump directly to the answer.

---

# 112. Theory Answer Method

For a long-answer question use:

```text
Definition
↓
Purpose
↓
Core mechanism
↓
Syntax
↓
Example
↓
Line-by-line explanation
↓
Advantages
↓
Limitations/traps
↓
Comparison
↓
Conclusion
```

## Example: "Explain inheritance"

Write:

1. Definition.
2. Why inheritance is used.
3. `extends` syntax.
4. Parent/child example.
5. Explain inherited members.
6. Explain IS-A relationship.
7. Explain constructor order.
8. Explain `super`.
9. Explain overriding.
10. Mention limitations and Java's class-inheritance restriction.
11. Give a short output/example.

This is much stronger than writing four lines.

---

# 113. Common Exam Traps

## Trap 1 — `float`

```java
float x = 10.5;
```

Incorrect.

Use:

```java
float x = 10.5f;
```

---

## Trap 2 — `byte + byte`

```java
byte a = 10;
byte b = 20;
byte c = a + b;
```

Arithmetic promotion generally makes the expression `int`.

---

## Trap 3 — array boundary

```java
int[] a = new int[5];
```

Valid indexes:

```text
0 1 2 3 4
```

Not `5`.

---

## Trap 4 — array length

```java
a.length
```

not:

```java
a.length()
```

---

## Trap 5 — string length

```java
s.length()
```

not:

```java
s.length
```

---

## Trap 6 — constructor

```java
void Student() {}
```

is a method.

A constructor has no return type:

```java
Student() {}
```

---

## Trap 7 — thread

```java
t.start();
```

starts the thread.

```java
t.run();
```

directly calls the method.

---

## Trap 8 — `throw` / `throws`

```text
throw  -> statement
throws -> declaration
```

---

## Trap 9 — `==`

For object references:

```java
a == b
```

does not generally mean "same contents."

---

## Trap 10 — `null`

```java
Student s = null;
```

does not create a Student.

It creates a reference containing `null`.

---

## Trap 11 — garbage collection

```java
s = null;
```

does not mean immediate destruction.

It may make an object unreachable.

---

## Trap 12 — static

A static method has no implicit instance object (`this`).

---

# 114. Rapid Revision

## Java execution

```text
.java
 ↓ javac
.class
 ↓ JVM
execution
```

## Types

```text
Primitive
Reference
```

## Eight primitives

```text
byte short int long
float double
char boolean
```

## OOP

```text
Encapsulation
Abstraction
Inheritance
Polymorphism
```

## Class

```text
fields
methods
constructors
```

## Inheritance

```text
extends
super
override
dynamic dispatch
```

## Interface

```text
implements
contract
multiple interfaces possible
```

## Exceptions

```text
try
catch
finally
throw
throws
```

## Threads

```text
Thread
Runnable
start
run
join
isAlive
synchronized
```

---

# 115. Practice Question Bank

## Level 1 — Basic

1. Define JVM, JRE and JDK.
2. Explain platform independence.
3. List all primitive data types.
4. Explain local and instance variables.
5. Explain widening conversion.
6. Explain narrowing conversion.
7. What is type promotion?
8. Explain arithmetic operators.
9. Explain `break` and `continue`.
10. Explain arrays.

## Level 2 — Conceptual

11. Why is `byte + byte` an `int`?
12. Explain `==` versus `.equals()`.
13. Explain stack and heap using an object example.
14. Explain constructor versus method.
15. Explain `this`.
16. Explain static members.
17. Explain final variables, methods and classes.
18. Explain garbage collection and reachability.
19. Explain method overloading.
20. Explain pass-by-value.

## Level 3 — OOP

21. Explain encapsulation.
22. Explain abstraction.
23. Explain inheritance.
24. Explain `super`.
25. Explain overriding.
26. Explain dynamic method dispatch.
27. Explain polymorphism.
28. Abstract class vs interface.
29. Overloading vs overriding.
30. Write an interface-based Java program.

## Level 4 — Exceptions

31. Explain exception hierarchy.
32. Checked vs unchecked exceptions.
33. Explain `try-catch-finally`.
34. Explain multiple catch.
35. Explain `throw` vs `throws`.
36. Create a custom exception.

## Level 5 — Threads

37. What is a thread?
38. Thread vs process.
39. `Thread` vs `Runnable`.
40. `start()` vs `run()`.
41. Explain thread states.
42. Explain `isAlive()`.
43. Explain `join()`.
44. Explain race conditions.
45. Explain synchronization.
46. Write a synchronized counter.

## Level 6 — Output Questions

For each of the following, predict output before running:

### Q1

```java
int x = 5;
int y = x++;
System.out.println(x + " " + y);
```

### Q2

```java
int x = 5;
int y = ++x;
System.out.println(x + " " + y);
```

### Q3

```java
System.out.println(5 / 2);
System.out.println(5 / 2.0);
```

### Q4

```java
byte a = 10;
byte b = 20;
int c = a + b;
System.out.println(c);
```

### Q5

```java
int[] a = {10, 20, 30};
for (int x : a) {
    System.out.println(x);
}
```

### Q6

```java
class A {
    void show() {
        System.out.println("A");
    }
}

class B extends A {
    @Override
    void show() {
        System.out.println("B");
    }
}

A x = new B();
x.show();
```

Do not just memorise answers. Explain the rule that produces each answer.

---

# 116. Final Master Checklist

## Foundations

- [ ] I can explain source → bytecode → JVM.
- [ ] I can differentiate JDK/JRE/JVM.
- [ ] I can explain platform independence.
- [ ] I understand Java lexical elements.
- [ ] I know identifier rules.

## Types

- [ ] I know all eight primitive types.
- [ ] I understand reference types.
- [ ] I know local/instance/static variables.
- [ ] I understand field defaults.
- [ ] I understand widening.
- [ ] I understand narrowing.
- [ ] I understand casting.
- [ ] I understand promotion.
- [ ] I understand integer division.
- [ ] I understand overflow.

## Operators

- [ ] Arithmetic
- [ ] Relational
- [ ] Logical
- [ ] Short circuit
- [ ] Assignment
- [ ] Increment/decrement
- [ ] Ternary
- [ ] Precedence
- [ ] `==` vs `.equals()`

## Control flow

- [ ] `if`
- [ ] `if-else`
- [ ] `else-if`
- [ ] `switch`
- [ ] `while`
- [ ] `do-while`
- [ ] `for`
- [ ] enhanced `for`
- [ ] `break`
- [ ] `continue`
- [ ] `return`

## Arrays

- [ ] declaration
- [ ] creation
- [ ] initialization
- [ ] indexing
- [ ] traversal
- [ ] `.length`
- [ ] multidimensional arrays
- [ ] jagged arrays

## Classes and OOP

- [ ] class
- [ ] object
- [ ] reference
- [ ] method
- [ ] parameter vs argument
- [ ] constructor
- [ ] `this`
- [ ] constructor chaining
- [ ] overloading
- [ ] recursion
- [ ] pass-by-value
- [ ] encapsulation
- [ ] abstraction
- [ ] inheritance
- [ ] `super`
- [ ] overriding
- [ ] dynamic dispatch
- [ ] polymorphism
- [ ] abstract class
- [ ] interface

## Modifiers

- [ ] private
- [ ] package-private
- [ ] protected
- [ ] public
- [ ] static
- [ ] final

## Memory

- [ ] stack/heap conceptual model
- [ ] references
- [ ] `null`
- [ ] garbage collection
- [ ] reachability
- [ ] GC roots
- [ ] eligible vs collected

## Exceptions

- [ ] hierarchy
- [ ] `try`
- [ ] `catch`
- [ ] multiple catch
- [ ] `finally`
- [ ] `throw`
- [ ] `throws`
- [ ] checked exceptions
- [ ] unchecked exceptions
- [ ] custom exceptions

## Packages

- [ ] package declaration
- [ ] import
- [ ] package structure

## Threads

- [ ] process vs thread
- [ ] Thread class
- [ ] Runnable
- [ ] `start()`
- [ ] `run()`
- [ ] thread states
- [ ] `isAlive()`
- [ ] `join()`
- [ ] race condition
- [ ] synchronization
- [ ] synchronized block

---

# 117. The Three Rules for This Entire Unit

## Rule 1 — Never memorise an output

Understand the rule that produces it.

## Rule 2 — Never skip the mental model

For every OOP question, know:

```text
reference
   ↓
object
   ↓
method
   ↓
runtime behaviour
```

## Rule 3 — Never write an exam answer without an example

A definition + syntax + example + explanation is much easier to remember and much stronger in an exam.

---

# Appendix — Source Lecture Set

The six user-provided lecture links:

1. https://youtu.be/3a1FXBR6QXY
2. https://youtu.be/0Gl9ygUk4K8
3. https://youtu.be/b4nsGWXNm2c
4. https://youtu.be/8ciDI5cUhSs
5. https://youtu.be/NmYcNMPUlzY
6. https://youtu.be/TJC0WhS6FNo

## Accuracy note

Exact minute-by-minute lecture commentary is intentionally **not fabricated**. The notes are organized around the identifiable Java syllabus/content represented by the lecture set. If the video transcripts are supplied, the next layer can add exact:

```text
Video
  ↓
Timestamp
  ↓
Lecturer's concept
  ↓
Expanded explanation
  ↓
Code/example
  ↓
Exam mapping
```

without guessing what was said at a particular timestamp.

---

# End of Notes

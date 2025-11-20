# 📚 IITM BS Computational Thinking - Quiz 2 Complete Masterclass

## Ultimate Study Guide with Detailed Explanations & Examples

---

# TABLE OF CONTENTS

1. [Week 5: Collections & Lists](#week-5-collections--lists)
2. [Week 6: Dictionaries](#week-6-dictionaries)
3. [Week 7: Matrices](#week-7-matrices)
4. [Week 8: Graphs](#week-8-graphs)
5. [Week 9: Recursion & DFS](#week-9-recursion--dfs)
6. [Week 10: Encapsulation](#week-10-encapsulation)
7. [Week 11: Concurrency](#week-11-concurrency)
8. [Week 12: Bottom-up Computing](#week-12-bottom-up-computing)
9. [Exam Strategy & Tips](#exam-strategy--tips)

---

# WEEK 5: Collections & Lists

## 📖 Introduction to Collections

A **collection** is a container that holds multiple data elements. Choosing the right collection type is fundamental to solving computational problems efficiently.

### Types of Collections: Complete Comparison

#### 1. **LIST**
**Definition:** An ordered sequence of elements where position matters.

**Characteristics:**
- Elements arranged in sequence: position 0, 1, 2, ...
- Changeable: can modify, add, or remove elements
- Allows duplicates: `[1, 2, 2, 3]` is valid
- Access by position: `list[i]`

**Notation:** `[x₁, x₂, x₃, ..., xₙ]`

**Example:**
```
grades = [92, 88, 95, 88, 76]
          Position 0, 1, 2, 3, 4
```

#### 2. **TUPLE**
**Definition:** An immutable (unchangeable) ordered sequence.

**Characteristics:**
- Ordered like lists
- Cannot modify once created (immutable)
- Allows duplicates
- More memory efficient than lists
- Used when you want to protect data from accidental change

**Example:**
```
coordinates = (10, 20)  # Cannot change these values
```

#### 3. **SET**
**Definition:** An unordered collection with no duplicates.

**Characteristics:**
- No specific order
- No duplicate elements: `{1, 2, 3}` (duplicates automatically removed)
- Very fast membership checking
- Useful for "Does X exist?" questions

**Example:**
```
unique_students = {101, 102, 103}
```

#### 4. **DICTIONARY**
**Definition:** A collection of key-value pairs where keys map to values.

**Characteristics:**
- Unordered by key name (ordered by insertion in modern versions)
- Keys are unique (no duplicate keys)
- Fast access by key name
- Values can be duplicated
- Like a mapping or lookup table

**Example:**
```
student_marks = {
    "Rahul": 92,
    "Ritika": 89,
    "Priya": 92
}
```

### List Operations: Detailed Breakdown

#### Combining Lists
```
Operation: CONCATENATION (++)
Syntax: List1 ++ List2
Example: [1, 2] ++ [3, 4, 5] = [1, 2, 3, 4, 5]

Important: Original lists unchanged, creates new list
```

**Real Example:**
```
morning_classes = ["Math", "Physics"]
afternoon_classes = ["Chemistry", "Biology"]
all_classes = morning_classes ++ afternoon_classes
Result: ["Math", "Physics", "Chemistry", "Biology"]
```

#### List Access Functions

**Length:**
```
Syntax: length(list)
Example: length([10, 20, 30]) = 3
Use: When you need to know total elements
```

**First Element:**
```
Syntax: first(list)
Example: first([10, 20, 30]) = 10
Use: Access first item without index
```

**Rest of List (All except first):**
```
Syntax: rest(list)
Example: rest([10, 20, 30]) = [20, 30]
Use: Process remaining elements recursively
```

**Last Element:**
```
Syntax: last(list)
Example: last([10, 20, 30]) = 30
Use: Access final item
```

**All except Last:**
```
Syntax: init(list)
Example: init([10, 20, 30]) = [10, 20]
Use: Remove last element for processing
```

### Insertion Sort Algorithm: Detailed Explanation

**What is Sorting?**
Arranging elements in order (ascending or descending).

**Why Sort?**
- Find top k performers
- Identify duplicates (sorted, then adjacent)
- Group by percentiles (after sorting, split into quarters)
- Efficient searching (binary search requires sorted data)

**Insertion Sort Process: Step by Step**

**Concept:** Build a sorted list by inserting each element one by one.

**Algorithm:**
```
Input: unsorted_list = [4, 2, 8, 1, 9]
Goal: sorted_list = [1, 2, 4, 8, 9]

STEP 1: Start with empty sorted list
sorted = []

STEP 2: Take first element from unsorted
4 → sorted = [4]

STEP 3: Take next element (2)
Compare 2 with sorted list
2 < 4, so insert before 4
sorted = [2, 4]

STEP 4: Take next element (8)
8 > 4, so insert at end
sorted = [2, 4, 8]

STEP 5: Take next element (1)
1 < all elements, insert at beginning
sorted = [1, 2, 4, 8]

STEP 6: Take next element (9)
9 > all elements, insert at end
sorted = [1, 2, 4, 8, 9]

RESULT: Fully sorted list!
```

**Visual Representation:**
```
Original:  [4] [2] [8] [1] [9]

After 1st: [4]
After 2nd: [2, 4]
After 3rd: [2, 4, 8]
After 4th: [1, 2, 4, 8]
After 5th: [1, 2, 4, 8, 9]
```

**Why Use Insertion Sort?**
- Simple to understand and implement
- Efficient for small datasets
- Online: works as data arrives
- Stable: maintains relative order of equal elements

### Variables and Accumulators

**Variables:** Store intermediate values during computation.

**Accumulators:** Special variables that accumulate results.

**Example: Sum of List**
```
numbers = [10, 20, 30, 40]
sum = 0            ← ACCUMULATOR initialized to 0

Iteration 1: sum = 0 + 10 = 10
Iteration 2: sum = 10 + 20 = 30
Iteration 3: sum = 30 + 30 = 60
Iteration 4: sum = 60 + 40 = 100

Result: 100
```

**Example: Building a List**
```
original = [1, 2, 3, 4, 5]
doubled = []       ← ACCUMULATOR (empty list)

Iteration 1: doubled = [] ++ [2] = [2]
Iteration 2: doubled = [2] ++ [4] = [2, 4]
Iteration 3: doubled = [2, 4] ++ [6] = [2, 4, 6]
Iteration 4: doubled = [2, 4, 6] ++ [8] = [2, 4, 6, 8]
Iteration 5: doubled = [2, 4, 6, 8] ++ [10] = [2, 4, 6, 8, 10]

Result: [2, 4, 6, 8, 10]
```

---

# WEEK 6: DICTIONARIES ⭐ VERY HIGH PRIORITY

## 🔑 Understanding Dictionaries

A **dictionary** is like a phone book: you look up a name (key) to find a phone number (value).

### Dictionary Fundamentals

#### What is a Dictionary?
```
Definition: Collection of KEY:VALUE pairs
Syntax: {"key1": value1, "key2": value2, "key3": value3}

Key Properties:
- Keys are unique (no duplicates)
- Each key maps to exactly one value
- Values CAN be duplicated
- Access by key, not position
```

**Real-World Examples:**
```
1. Student Marks Mapping
marks = {"Rahul": 92, "Ritika": 89, "Priya": 92}
       Keys: Names    Values: Scores

2. Train Routes
trains = {"T101": "Delhi", "T102": "Mumbai", "T103": "Delhi"}
      Keys: Train IDs  Values: Destinations

3. Word Frequencies
frequencies = {"the": 45, "and": 32, "is": 28}
           Keys: Words   Values: Counts
```

### Dictionary Operations: Comprehensive Guide

#### 1. **Creating a Dictionary**

**Empty Dictionary:**
```
empty_dict = {}
```

**Dictionary with Initial Values:**
```
student_marks = {
    "Alice": 95,
    "Bob": 87,
    "Charlie": 92
}
```

#### 2. **Accessing Values**

**Direct Access by Key:**
```
Syntax: dictionary["key"]
Example: marks["Alice"] = 95

What happens: Looks up "Alice" in dictionary, returns 95
```

**Practical Example:**
```
student_marks = {"Alice": 95, "Bob": 87}
alice_score = student_marks["Alice"]  # 95
bob_score = student_marks["Bob"]      # 87
```

#### 3. **Updating/Adding Values**

**Add New Key-Value Pair:**
```
dictionary["new_key"] = value

Example:
marks = {"Alice": 95}
marks["Bob"] = 87
marks["Charlie"] = 92
Result: {"Alice": 95, "Bob": 87, "Charlie": 92}
```

**Update Existing Value:**
```
dictionary["existing_key"] = new_value

Example:
marks = {"Alice": 95}
marks["Alice"] = 98  # Update score
Result: {"Alice": 98}
```

#### 4. **Checking if Key Exists: isKey() Function**

**Why isKey()?** 
Before accessing a key that might not exist, check if it exists first.

**Syntax:**
```
isKey(dictionary, key) → returns True or False

Example:
marks = {"Alice": 95, "Bob": 87}

isKey(marks, "Alice")  → True
isKey(marks, "David")  → False
```

**Critical Pattern:**
```
ALWAYS DO THIS when working with dictionaries:

if isKey(marks, "Alice"):
    value = marks["Alice"]
    # Process value
else:
    # Handle case where key doesn't exist
    print("Alice not found")
```

**Common Mistake to Avoid:**
```
❌ WRONG:
value = marks["UnknownStudent"]  # Crashes if key doesn't exist!

✅ CORRECT:
if isKey(marks, "UnknownStudent"):
    value = marks["UnknownStudent"]
else:
    print("Student not found")
```

### List vs Dictionary: Critical Differences

#### **LIST: Sequential Access**
```
Structure: Elements arranged by position
Access: Need to know position (index)
Speed: To find element, may need to scan entire list

Example:
grades = [92, 88, 95, 76, 88]
To find 95, must check: position 0, 1, 2 ← Found!

Syntax: grades[2] = 95
```

#### **DICTIONARY: Random Access**
```
Structure: Elements organized by key
Access: Direct access by key name
Speed: Fast - constant time lookup regardless of dictionary size

Example:
marks = {"Alice": 92, "Bob": 88, "Charlie": 95, "David": 76}
To find Charlie's score: marks["Charlie"] = 95 ← Instant!

Syntax: marks["Charlie"] = 95
```

#### **Comparison Table:**
```
ASPECT          | LIST              | DICTIONARY
Position-based? | Yes (0, 1, 2...) | No (by key name)
Random access?  | Slower            | Faster (constant time)
Duplicates?     | Allowed           | Keys are unique
Order matters?  | Yes               | Values order unimportant
Use when?       | Sequential data   | Lookup/mapping needed
```

**Real Scenario Example:**

**Scenario:** You're a teacher with 1000 students. You want to find Alice's marks.

**Using LIST (Very Inefficient):**
```
marks = [92, 88, 95, 76, ...]  (1000 scores)
Problem: Which score is Alice's? You don't know!
You must check each entry. Worst case: scan all 1000!
```

**Using DICTIONARY (Efficient):**
```
marks = {"Alice": 92, "Bob": 88, "Charlie": 95, ...}
marks["Alice"] = 92  ← Found instantly!
No matter if 10 or 10,000 students, same speed!
```

### The Dictionary Update Pattern

**Most Important Pattern in Quiz 2:**

```
PATTERN: Update existing or create new

if isKey(dictionary, key):
    dictionary[key] = dictionary[key] + value
else:
    dictionary[key] = value
```

**Real Example: Word Frequency Counter**

**Problem:** Count frequency of each word in text.
```
Text: "the cat and the dog and the bird"

Process:
1. "the" → First time: marks["the"] = 1
2. "cat" → First time: marks["cat"] = 1
3. "and" → First time: marks["and"] = 1
4. "the" → Exists! marks["the"] = 1 + 1 = 2
5. "dog" → First time: marks["dog"] = 1
6. "and" → Exists! marks["and"] = 1 + 1 = 2
7. "the" → Exists! marks["the"] = 2 + 1 = 3
8. "bird" → First time: marks["bird"] = 1

Result:
{
    "the": 3,
    "cat": 1,
    "and": 2,
    "dog": 1,
    "bird": 1
}
```

**Implementation:**
```
word_frequency = {}

for word in text_words:
    if isKey(word_frequency, word):
        word_frequency[word] = word_frequency[word] + 1
    else:
        word_frequency[word] = 1

Output: {"the": 3, "cat": 1, "and": 2, ...}
```

### Iterating Through Dictionary

**Iterate through all keys:**
```
Syntax: foreach key in keys(dictionary)

Example:
marks = {"Alice": 95, "Bob": 87, "Charlie": 92}

foreach student in keys(marks):
    score = marks[student]
    print(student, ":", score)

Output:
Alice : 95
Bob : 87
Charlie : 92
```

**Real Use:** Calculate class average

```
total = 0
count = 0

foreach student in keys(marks):
    total = total + marks[student]
    count = count + 1

average = total / count
```

---

# WEEK 7: MATRICES

## 📊 Understanding Matrices

A **matrix** is a 2D table with rows and columns. Think of it like a spreadsheet.

### Matrix Structure

#### What is a Matrix?
```
Definition: 2D rectangular array of elements
Rows: Horizontal lines
Columns: Vertical lines

Visual:
        Col0  Col1  Col2  Col3
Row0 [   10    20    30    40  ]
Row1 [   50    60    70    80  ]
Row2 [   90   100   110   120  ]

Notation: matrix[row][column]
Example: matrix[1][2] = 70 (Row 1, Column 2)
```

### Accessing Matrix Elements

#### Random Access
```
Syntax: matrix[i][j]
- i = row index (0, 1, 2, ...)
- j = column index (0, 1, 2, ...)

Example:
matrix[0][0] = 10  (top-left)
matrix[1][2] = 70  (middle-right)
matrix[2][3] = 120 (bottom-right)
```

#### Setting Values
```
Syntax: matrix[i][j] = value

Example:
matrix[0][0] = 10
matrix[0][1] = 20
matrix[1][0] = 50
matrix[1][1] = 60
```

### Matrix Representation Using Dictionaries

**Using Nested Dictionaries:**

```
matrix = {}

Row 0: matrix[0] = {}
       matrix[0][0] = 10
       matrix[0][1] = 20

Row 1: matrix[1] = {}
       matrix[1][0] = 50
       matrix[1][1] = 60

Access: matrix[0][1] = 20
```

**Complete Example:**
```
Distance matrix between cities:
      Delhi  Mumbai  Bangalore
Delhi    0     1400     2200
Mumbai  1400   0        980
Bng     2200   980      0

Implementation:
distance = {}
distance[0] = {}    # Delhi row
distance[0][0] = 0
distance[0][1] = 1400
distance[0][2] = 2200

distance[1] = {}    # Mumbai row
distance[1][0] = 1400
distance[1][1] = 0
distance[1][2] = 980

distance[2] = {}    # Bangalore row
distance[2][0] = 2200
distance[2][1] = 980
distance[2][2] = 0

Access: distance[0][1] = 1400 (Delhi to Mumbai)
```

### Matrix Iteration

#### Row-wise Iteration
```
Iterate through each row:

foreach row_index in rows(matrix):
    foreach col_index in columns(matrix[row_index]):
        element = matrix[row_index][col_index]
        # Process element
```

**Example: Sum all elements**
```
total = 0

foreach i in rows(matrix):
    foreach j in columns(matrix[i]):
        total = total + matrix[i][j]
```

#### Column-wise Iteration
```
Iterate column by column:

foreach col_index in columns(matrix):
    foreach row_index in rows(matrix):
        element = matrix[row_index][col_index]
        # Process element
```

**Example: Sum each column**
```
column_sums = {}

foreach col in columns(matrix):
    sum = 0
    foreach row in rows(matrix):
        sum = sum + matrix[row][col]
    column_sums[col] = sum
```

### Applications of Matrices

1. **Distance/Adjacency Matrices:** Connection between cities/nodes
2. **Grade Matrices:** Student × Subject scores
3. **Pixel Grids:** Image representation
4. **Relationship Tables:** Entity pairs and their relationships

---

# WEEK 8: GRAPHS ⭐ VERY HIGH PRIORITY

## 🕸️ Understanding Graphs

A **graph** is a collection of **vertices** (nodes) connected by **edges** (links).

### Graph Components

#### Vertices
```
Definition: Points or nodes in a graph
Represented by: Names, numbers, or identifiers

Example: Train Network
Vertices: Delhi, Mumbai, Bangalore, Chennai
```

#### Edges
```
Definition: Connections between vertices
Shows: Relationship between pairs of vertices

Example: Train Network
Edges: Delhi-Mumbai (train exists)
       Mumbai-Bangalore (train exists)
       Bangalore-Chennai (train exists)
```

#### Graph Representation
```
Visual:
    Delhi -------- Mumbai
      |              |
      |              |
  Bangalore ----- Chennai

Vertices: {Delhi, Mumbai, Bangalore, Chennai}
Edges: {Delhi-Mumbai, Delhi-Bangalore, Mumbai-Chennai, Bangalore-Chennai}
```

### Graph Representation Methods

#### 1. **Dictionary Representation**

```
graph = {
    "Delhi": ["Mumbai", "Bangalore"],
    "Mumbai": ["Delhi", "Chennai"],
    "Bangalore": ["Delhi", "Chennai"],
    "Chennai": ["Mumbai", "Bangalore"]
}

Reading:
- graph["Delhi"] = ["Mumbai", "Bangalore"]
  → From Delhi, you can reach Mumbai and Bangalore
```

**Implementation:**
```
graph = {}
graph["A"] = ["B", "C"]     # A connects to B and C
graph["B"] = ["A", "D"]     # B connects to A and D
graph["C"] = ["A"]          # C connects to A
graph["D"] = ["B"]          # D connects to B

Access: graph["A"] → ["B", "C"]
```

#### 2. **Matrix Representation**

```
Adjacency Matrix:
        A  B  C  D
    A [ 0  1  1  0 ]
    B [ 1  0  0  1 ]
    C [ 1  0  0  0 ]
    D [ 0  1  0  0 ]

Where:
- 1 means edge exists
- 0 means no edge

M[i][j] = 1 → edge from i to j exists
M[i][j] = 0 → no direct connection from i to j

Example: M[0][1] = 1 → A connects to B
         M[0][3] = 0 → A does NOT connect to D
```

**Implementation:**
```
matrix = {}
matrix[0] = {0: 0, 1: 1, 2: 1, 3: 0}  # A's connections
matrix[1] = {0: 1, 1: 0, 2: 0, 3: 1}  # B's connections
matrix[2] = {0: 1, 1: 0, 2: 0, 3: 0}  # C's connections
matrix[3] = {0: 0, 1: 1, 2: 0, 3: 0}  # D's connections

Check: matrix[0][1] = 1 (edge from A to B)
       matrix[0][3] = 0 (no edge from A to D)
```

### Train Network Problem: Complete Deep Dive

**Scenario:** A railway company operates multiple trains connecting cities.

**Given Data:**
```
trains = {
    "T101": {"start": "Delhi", "end": "Mumbai"},
    "T102": {"start": "Mumbai", "end": "Bangalore"},
    "T103": {"start": "Delhi", "end": "Bangalore"},
    "T104": {"start": "Bangalore", "end": "Chennai"}
}
```

**Visual Representation:**
```
      Delhi ←T101→ Mumbai
        ↓ T103        ↓ T102
    Bangalore ←T104← Chennai
```

#### Type 1: Direct Routes

**Definition:** Stations you can reach with ONE train.

**Calculation:**
```
For each train:
- Starting station: count_direct[train.start]++
- Ending station: count_direct[train.end]++

From Delhi:
- T101: Delhi → Mumbai (direct)
- T103: Delhi → Bangalore (direct)
Direct routes from Delhi: 2

From Mumbai:
- T101: Mumbai → Delhi (direct)
- T102: Mumbai → Bangalore (direct)
Direct routes from Mumbai: 2
```

**Why?** Useful for: "Which cities can I reach directly from Delhi?"

#### Type 2: One-Hop Routes (1-Hop)

**Definition:** Stations reachable by taking one train, then changing to another train.

**Calculation:**
```
Step 1: Find direct connections from starting point
Step 2: From each direct destination, find connections to other cities
Step 3: Count unique destinations (excluding starting point)

From Delhi:
Direct: Mumbai, Bangalore

From Mumbai (via T101 from Delhi):
- Can reach: Delhi (exclude, it's starting point), Bangalore

From Bangalore (via T103 from Delhi):
- Can reach: Delhi (exclude), Mumbai (via T102), Chennai (via T104)

One-hop destinations from Delhi:
{Bangalore, Mumbai, Chennai}

One-hop routes: 3
```

**Why?** Useful for: "Where can I go with one train change?"

#### Type 3: Two-Hop Routes

**Definition:** Stations reachable by changing at most TWO trains.

**Calculation:**
```
Direct (0 changes): Delhi→Mumbai, Delhi→Bangalore
One-hop (1 change): Delhi→Mumbai→Bangalore, Delhi→Bangalore→Mumbai, 
                    Delhi→Bangalore→Chennai
Two-hop (2 changes): Additional destinations reachable with 2 changes

Total two-hop routes: All stations reachable with 0, 1, or 2 train changes
```

#### Type 4: n-Hop Routes

**Definition:** Stations reachable by changing at most n trains.

```
0-Hop: Only starting station
1-Hop: Direct + immediate changes
2-Hop: Up to 2 changes
n-Hop: Up to n changes (explores larger portion of network)
```

**Implementation Pattern:**
```
reachable = {starting_station}

for i from 1 to n:
    new_reachable = {}
    
    foreach station in reachable:
        foreach neighbor in graph[station]:
            if neighbor not in reachable:
                new_reachable[neighbor] = True
    
    reachable = reachable ∪ new_reachable

return reachable
```

### Edge-Labeled Graphs

**Concept:** Each edge carries additional information (label).

**Example with Labels:**
```
Trains can have multiple connections:
Denver ----T101----> Chicago
  |       ----T102----|
  |                  |
  |                  |
 Los Angeles ---T103---

Edge-labeled matrix:
matrix[Denver][Chicago] = {T101: {distance: 900},
                           T102: {distance: 900}}

This tells us:
- Two different trains between Denver and Chicago
- Both are 900 km
- We can distinguish which train to take
```

**When to Use:**
- Multiple routes between same cities
- Tracking train numbers or flight codes
- Storing distance, time, or cost per connection

---

# WEEK 9: RECURSION & DFS ⭐ VERY HIGH PRIORITY

## 🔄 Understanding Recursion

**Recursion:** A function that calls itself to solve a problem.

### Why Recursion?

Many problems naturally have recursive structure:
- Tree traversal (each node branches into more nodes)
- Graph exploration (each vertex connects to more vertices)
- Mathematical sequences (each term depends on previous)
- Backtracking (explore and return)

### Recursion Structure: Two Essential Parts

#### Part 1: Base Case

```
Definition: Condition where we return directly without recursion
Purpose: Stops the recursion from continuing infinitely

Example - Countdown:
function countdown(n):
    if n == 0:                    ← BASE CASE
        return 0                  ← Direct return, NO recursion
    else:
        return n + countdown(n-1) ← RECURSIVE CALL
```

#### Part 2: Inductive Step

```
Definition: Computation in terms of smaller version of same problem
Purpose: Break problem into smaller subproblems

Example - Sum of first n numbers:
function sum(n):
    if n == 0:
        return 0                  ← Base case
    else:
        return n + sum(n-1)       ← Inductive step
```

### How Recursion Works: Execution Trace

**Problem:** Calculate factorial of 5 (5!)

```
Definition:
factorial(n) = n * factorial(n-1)  if n > 1
factorial(1) = 1                   if n = 1

Execution Trace:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

factorial(5)
    = 5 * factorial(4)
    
        = 5 * (4 * factorial(3))
        
            = 5 * (4 * (3 * factorial(2)))
            
                = 5 * (4 * (3 * (2 * factorial(1))))
                
                    = 5 * (4 * (3 * (2 * 1)))  ← BASE CASE
                    
                = 5 * (4 * (3 * 2))
                = 5 * (4 * 6)
                = 5 * 24
                = 120

Result: factorial(5) = 120
```

**Key Insight:** The function suspends its computation until the recursive call returns.

### Recursion Visualization: Call Stack

```
Call Stack Evolution:

Initial Call:
┌─────────────────┐
│ factorial(5)    │
│ (waiting)       │
└─────────────────┘

After recursive calls:
┌─────────────────┐
│ factorial(5)    │ ← Waiting
├─────────────────┤
│ factorial(4)    │ ← Waiting
├─────────────────┤
│ factorial(3)    │ ← Waiting
├─────────────────┤
│ factorial(2)    │ ← Waiting
├─────────────────┤
│ factorial(1)    │ ← Returns 1
└─────────────────┘

Unwinding (returning values):
factorial(1) = 1
factorial(2) = 2 * 1 = 2
factorial(3) = 3 * 2 = 6
factorial(4) = 4 * 6 = 24
factorial(5) = 5 * 24 = 120
```

### Common Recursion Patterns

#### Pattern 1: Linear Recursion
```
function linear(n):
    if n == base:
        return base_value
    else:
        return f(linear(n-1))

Example: Sum of list
sum([1,2,3,4]) = 1 + sum([2,3,4])
               = 1 + (2 + sum([3,4]))
               = 1 + (2 + (3 + sum([4])))
               = 1 + (2 + (3 + (4 + sum([]))))
               = 1 + (2 + (3 + (4 + 0)))
               = 10
```

#### Pattern 2: Tree Recursion
```
function tree(n):
    if n == base:
        return base_value
    else:
        return f(tree(n-1), tree(n-2))

Example: Fibonacci
fib(5) = fib(4) + fib(3)
       = (fib(3) + fib(2)) + (fib(2) + fib(1))
       = ...
```

### Common Mistakes with Recursion

#### ❌ Mistake 1: Missing Base Case
```
WRONG:
function countdown(n):
    print(n)
    return countdown(n-1)  ← Infinite recursion!

CORRECT:
function countdown(n):
    if n == 0:            ← BASE CASE
        return
    print(n)
    return countdown(n-1)
```

#### ❌ Mistake 2: Base Case Never Reached
```
WRONG:
function countdown(n):
    if n == 1:
        return 1
    return n + countdown(n-1)  ← If n < 1, never reaches base case

CORRECT:
function countdown(n):
    if n <= 0:           ← Include all base cases
        return 0
    return n + countdown(n-1)
```

#### ❌ Mistake 3: Wrong Inductive Step
```
WRONG:
function sum(n):
    if n == 0:
        return 0
    return n + sum(n)    ← Calls itself with SAME argument (infinite!)

CORRECT:
function sum(n):
    if n == 0:
        return 0
    return n + sum(n-1)  ← Calls with SMALLER argument
```

---

## 🔍 Depth First Search (DFS)

**DFS:** Algorithm to explore all vertices in a graph systematically.

### Why DFS?

**Problems it solves:**
- "Is vertex B reachable from vertex A?"
- "Find all vertices reachable from A"
- "Detect cycles in a graph"
- "Find path between two vertices"

### DFS Algorithm: Step by Step

**Concept:** Start from a vertex and explore as deep as possible before backtracking.

```
Algorithm:
1. Mark starting vertex as visited
2. For each neighbor of current vertex:
   - If not visited: recursively explore that neighbor
3. When all neighbors explored, backtrack

Key Component: VISITED dictionary
- Prevents revisiting same vertex (crucial for graphs with cycles!)
- Distinguishes explored from unexplored vertices
```

### DFS Implementation

**Pseudocode:**
```
visited = {}  ← Tracks which vertices we've seen

function dfs(vertex):
    visited[vertex] = True  ← Mark as visited
    print(vertex)           ← Process current vertex
    
    for each neighbor of vertex:
        if neighbor not in visited:  ← Check if explored
            dfs(neighbor)  ← Recursively explore
```

### DFS Execution Trace: Real Example

**Graph:**
```
    A
   / \
  B   C
 /     \
D       E

Edges: A-B, A-C, B-D, C-E
```

**DFS Starting from A:**
```
Step 1: Visit A
visited = {A: True}
Print: A
Neighbors: B, C

Step 2: First neighbor is B (not visited)
        Call dfs(B)
        
    Step 2a: Visit B
    visited = {A: True, B: True}
    Print: B
    Neighbors: A, D
    
    Step 2b: Check neighbor A (already visited, skip)
    
    Step 2c: Check neighbor D (not visited)
             Call dfs(D)
             
        Step 2c-i: Visit D
        visited = {A: True, B: True, D: True}
        Print: D
        Neighbors: B
        
        Step 2c-ii: Check neighbor B (already visited, skip)
        Return from dfs(D)
    
    Return from dfs(B)

Step 3: Second neighbor is C (not visited)
        Call dfs(C)
        
    Step 3a: Visit C
    visited = {A: True, B: True, D: True, C: True}
    Print: C
    Neighbors: A, E
    
    Step 3b: Check neighbor A (already visited, skip)
    
    Step 3c: Check neighbor E (not visited)
             Call dfs(E)
             
        Step 3c-i: Visit E
        visited = {A: True, B: True, D: True, C: True, E: True}
        Print: E
        Neighbors: C
        
        Step 3c-ii: Check neighbor C (already visited, skip)
        Return from dfs(E)
    
    Return from dfs(C)

Final visited: {A: True, B: True, D: True, C: True, E: True}
Print order: A, B, D, C, E
```

### Why VISITED is Critical

**Problem Without Visited:**
```
Graph with cycle: A ← B
                   ↓ ↑
                   C

Without visited tracking:
dfs(A):
    Visit A
    Go to B
    dfs(B):
        Visit B
        Go to C
        dfs(C):
            Visit C
            Go to A
            dfs(A):
                Visit A (again!)
                Go to B
                dfs(B):
                    ... INFINITE LOOP!
```

**Solution With Visited:**
```
dfs(A):
    visited[A] = True
    Visit A
    Go to B
    dfs(B):
        visited[B] = True
        Visit B
        Go to C
        dfs(C):
            visited[C] = True
            Visit C
            Go to A
            Check: A already in visited? YES!
            Skip (don't recurse)

No infinite loop!
```

### DFS Applications

#### Application 1: Check Connectivity
```
Is B reachable from A?

visited = {}
found = False

function can_reach(current, target):
    if current == target:
        return True
    
    visited[current] = True
    
    for each neighbor of current:
        if neighbor not in visited:
            if can_reach(neighbor, target):
                return True
    
    return False
```

#### Application 2: Find Path
```
Find path from A to E:

visited = {}
path = []

function find_path(current, target, path):
    if current == target:
        return path + [current]  ← Found!
    
    visited[current] = True
    
    for each neighbor of current:
        if neighbor not in visited:
            result = find_path(neighbor, target, path + [current])
            if result:
                return result
    
    return None  ← Path doesn't exist
```

---

# WEEK 10: ENCAPSULATION

## 📦 Understanding Encapsulation

**Encapsulation:** Bundling data and procedures together into a single unit (object).

### The Problem Without Encapsulation

```
Without Encapsulation (Procedural):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

balance = 1000

procedure withdraw(amount):
    if amount <= balance:
        balance = balance - amount
        return amount
    else:
        return 0

PROBLEM:
- Balance is global and can be modified from anywhere
- Procedure is separate from data
- No protection against misuse
- Easy to accidentally corrupt balance
```

### Object-Oriented Solution

```
With Encapsulation (Object-Oriented):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Object: Account
- Private field: balance = 1000
- Method: withdraw(amount)
    if amount <= balance:
        balance = balance - amount
        return amount
    else:
        return 0

BENEFITS:
- Balance is protected (private)
- Can only be modified through withdraw()
- Data and behavior grouped together
- Clear interface for interaction
```

### Key Principles of Encapsulation

#### 1. **Bundling Data and Procedures**
```
Object ATMAccount:
    Data fields:
        - balance
        - account_number
        - account_holder
    
    Procedures:
        - deposit(amount)
        - withdraw(amount)
        - get_balance()
        - transfer(to_account, amount)
```

#### 2. **Data Hiding / Privacy**
```
Public: Accessible from outside
- Methods: deposit(), withdraw(), get_balance()

Private: Hidden from outside
- Fields: balance, pin, transaction_history
- Internal helper methods

Users can only interact through public interface!
```

#### 3. **State Retention**
```
Object maintains state between calls:

ATM:
    balance = 1000
    
    withdraw(200)  ← balance becomes 800
    withdraw(300)  ← balance becomes 500
    
Balance is RETAINED between calls!

Compare with standalone procedure:
    withdraw(200)  ← No memory of previous balance
    withdraw(300)  ← Same result as first call
    
Standalone procedure is stateless.
```

#### 4. **Side Effects**
```
Object-oriented side effects are NATURAL:
    balance = 1000
    account.withdraw(200)
    Side effect: balance now 800 (EXPECTED)
    
Standalone procedure side effects are problematic:
    balance = 1000
    result = withdraw(200)
    Did balance change? Unknown! (CONFUSING)
```

### Benefits of Encapsulation

#### ✅ Benefit 1: Data Protection
```
With Encapsulation:
account.balance = -5000  ← Can't do this! No direct access.
account.withdraw(5000)   ← Method validates before changing

Without Encapsulation:
balance = -5000  ← Easy to corrupt! Anyone can set it.
```

#### ✅ Benefit 2: Implementation Hiding
```
Internal implementation can change without affecting users:

Version 1:
class Account:
    balance = []  # Store as list of transactions
    
    def get_balance():
        return sum(balance)

Version 2:
class Account:
    balance = 0  # Store as single number
    
    def get_balance():
        return balance

Users call: account.get_balance()
Same interface, different implementation!
```

#### ✅ Benefit 3: Enforced Rules
```
class Account:
    balance = 1000
    
    def withdraw(amount):
        if amount > 0 and amount <= balance:  ← Rule enforced
            balance = balance - amount
        else:
            print("Invalid withdrawal")

Standalone procedure:
    procedure withdraw(balance, amount):
        return balance - amount  ← No rules!
```

### Disadvantages of Encapsulation

#### ❌ Disadvantage 1: Added Complexity
```
Simple: balance = 1000
Complex: account = Account(1000)
         account.withdraw(200)
         
Requires understanding of objects.
```

#### ❌ Disadvantage 2: Initialization Overhead
```
Must create and initialize object:
account = new Account()
account.set_balance(1000)
account.set_account_number("ACC123")

vs simple variable:
balance = 1000
```

#### ❌ Disadvantage 3: Performance
```
Object operations slightly slower than direct variable access:
account.withdraw(100)  ← Extra overhead

vs
balance = balance - 100  ← Direct operation
```

### Encapsulation vs Procedural Approach

```
SCENARIO: Money Management System

PROCEDURAL (No Encapsulation):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

savings_balance = 1000
checking_balance = 500

procedure deposit_savings(amount):
    savings_balance = savings_balance + amount

procedure withdraw_checking(amount):
    if amount <= checking_balance:
        checking_balance = checking_balance - amount
    else:
        return error

PROBLEMS:
- Balances can be set to negative directly
- No link between account data and procedures
- Code scattered across program
- Hard to track which procedures use which data


OBJECT-ORIENTED (With Encapsulation):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Object SavingsAccount:
    private balance = 1000
    
    public deposit(amount):
        if amount > 0:
            balance = balance + amount
    
    public withdraw(amount):
        if 0 < amount <= balance:
            balance = balance - amount

Object CheckingAccount:
    private balance = 500
    
    public deposit(amount):
        if amount > 0:
            balance = balance + amount
    
    public withdraw(amount):
        if 0 < amount <= balance:
            balance = balance - amount

BENEFITS:
- Each account manages itself
- Balances protected from invalid operations
- Related code grouped together
- Easy to maintain and extend
```

---

# WEEK 11: CONCURRENCY

## ⚡ Understanding Concurrency

**Concurrency:** Multiple computations running simultaneously (in parallel).

### Why Concurrency?

**Real-world problems:**
- Download file while playing music
- Process multiple user requests simultaneously
- Parallel computations on multi-core processors
- Responsive user interfaces (UI doesn't freeze)

### Traditional vs Concurrent Execution

#### Traditional (Sequential)
```
Action 1: Start task A
          Wait until A completes
Action 2: Get result from A
Action 3: Start task B
          Wait until B completes
Action 4: Get result from B

Timeline:
A: [=============================]
B:                                [============================]
   Time ──────────────────────────────────────────────────────>

Total time: A_time + B_time
```

#### Concurrent
```
Action 1: Start task A
Action 2: Start task B (while A running)
Action 3: Check if A ready? Poll...
Action 4: Get A result when ready
Action 5: Get B result when ready

Timeline:
A: [=============================]
B: [============================]
   Time ──────────────────────────>

Total time: Max(A_time, B_time) ← Much faster!
```

### Unbundling Procedure Calls

**Normal Procedure Call:**
```
Traditional:
B = A.P(C)

This does 3 things:
1. Start procedure P with parameter C
2. WAIT for completion
3. Assign result to B
```

**Unbundled (Concurrent):**
```
New approach breaks it into 3 separate actions:

Action 1 - Start:
X.start(P, A)  ← Procedure starts and runs independently

Action 2 - Check Status:
if X.ready(P):  ← Check if finished yet
    print("Ready")

Action 3 - Get Result:
B = X.result(P)  ← Get the result when we need it
```

### Two Concurrency Models

#### Model 1: Polling Model

```
Main program controls everything:

X.start(procedure_P, parameter_A)
Y.start(procedure_Q, parameter_B)
Z.start(procedure_R, parameter_C)

while true:
    if X.ready(procedure_P):
        result_X = X.result(procedure_P)
        # Process result_X
        break
    
    if Y.ready(procedure_Q):
        result_Y = Y.result(procedure_Q)
        # Process result_Y
        break
    
    if Z.ready(procedure_R):
        result_Z = Z.result(procedure_R)
        # Process result_Z
        break

Execution:
P starts: |=========...
Q starts: |=========...
R starts: |=========...
Main polls: checking...checking...checking...

ADVANTAGES:
- Simple to understand
- Main program has full control

DISADVANTAGES:
- Wasteful: constantly checking status
- Not responsive: misses ready signals
```

#### Model 2: Producer-Consumer Model

```
Procedures write results to buffer when done:

buffer_P = {}  ← Empty buffer
buffer_Q = {}
buffer_R = {}

X.start(P, A, buffer_P)   ← Tell X where to write result
Y.start(Q, B, buffer_Q)
Z.start(R, C, buffer_R)

Signal when ready:
When P finishes: writes to buffer_P, sets signal
When Q finishes: writes to buffer_Q, sets signal
When R finishes: writes to buffer_R, sets signal

Main waits for signals:
wait(buffer_P.ready)  ← Blocks until signal
result_X = buffer_P.data

ADVANTAGES:
- Efficient: waits for signal, doesn't poll
- Responsive: woken immediately when ready
- No wasted checking

DISADVANTAGES:
- More complex to implement
- Needs signaling mechanism
```

### Race Conditions

**Problem:** When multiple procedures access shared data simultaneously.

```
RACE CONDITION EXAMPLE:

Shared data: account_balance = 100

Thread 1 (Withdraw):
    Read: balance = 100
    Subtract: 100 - 50 = 50
    (Pause - context switch to Thread 2)
    
Thread 2 (Deposit):
    Read: balance = 100  ← Still sees original!
    Add: 100 + 30 = 130
    Write: balance = 130
    (Return to Thread 1)
    
Thread 1:
    Write: balance = 50

RESULT:
Expected: 100 - 50 + 30 = 80
Actual: 50
Money lost due to race condition!
```

### Solution: Atomic Operations

**Atomic Operation:** Cannot be interrupted mid-execution.

```
ATOMIC (Safe):
    Read: balance = 100
    Modify: balance = 100 - 50 = 50
    Write: balance = 50
    (Cannot be interrupted!)

If Thread 2 tries to access during this:
    Waits for Thread 1 to complete
    Then reads updated value

RESULT:
Thread 1: Takes 50 from 100 → 50
Thread 2: Adds 30 to 50 → 80 ✓ Correct!
```

### Implementation Strategy

```
Protected Resource (atomic access):

shared_list = [1, 2, 3]
lock = semaphore(1)  ← Controls access

Thread 1:
    lock.acquire()  ← Exclusive access
    shared_list.append(4)
    lock.release()  ← Other threads can now access

Thread 2:
    lock.acquire()  ← Waits if Thread 1 has it
    shared_list.remove(1)
    lock.release()

Result: Operations don't interfere!
```

---

# WEEK 12: BOTTOM-UP COMPUTING

## 📈 Understanding Bottom-up Computing

**Bottom-up Computing:** Building programs/models from concrete data examples (data-driven).

### Inductive Learning

**Concept:** Learn general rules from specific examples.

```
Examples from nature:
If I see 100 red apples and 0 blue apples
→ General rule: "Apples are red"

Examples from grade assignment:
If scores 90-100 get A, 80-89 get B, 70-79 get C
→ General rule: "Grade based on score range"
```

### Classification

**Definition:** Categorize data into predefined classes based on patterns.

**Process:**
```
Step 1: Examine sample data
Step 2: Identify distinguishing features
Step 3: Build decision tree or classifier
Step 4: Apply to new, unseen data
```

**Example: Email Spam Classification**

```
Sample data:
┌──────────────────────────────────┐
│ Contains "Free"?  Price mention?  │ Classification
├──────────────────────────────────┤
│ Yes               Yes             │ SPAM
│ Yes               Yes             │ SPAM
│ No                No              │ NOT SPAM
│ No                No              │ NOT SPAM
│ Yes               Yes             │ SPAM
└──────────────────────────────────┘

Decision Tree:
    Email
     / \
   Contains  → Yes → Price? → Yes → SPAM
   "Free"?        → No  → NOT SPAM
     \
      No  → NOT SPAM

Apply to new email:
"Free vacation! Limited time $99 offer"
- Contains "Free"? YES
- Mentions price? YES
- Classification: SPAM ✓
```

### Prediction

**Definition:** Estimate numerical output based on input data.

**Process:**
```
Step 1: Collect training examples
Step 2: Find relationship: output = f(input)
Step 3: Use function for new inputs
```

**Example: House Price Prediction**

```
Training Data:
┌────────────────────────────────┐
│ Area (sqft)  Price ($)         │
├────────────────────────────────┤
│ 1000         $200,000          │
│ 1500         $300,000          │
│ 2000         $400,000          │
│ 2500         $500,000          │
└────────────────────────────────┘

Pattern: Price = Area × 200
         $200,000 = 1000 × 200
         $300,000 = 1500 × 200
         $400,000 = 2000 × 200
         $500,000 = 2500 × 200

For new house (1800 sqft):
Predicted price = 1800 × 200 = $360,000
```

### Combining Classification and Prediction

**Strategy:** Use classification to branch, then prediction within each branch.

```
Decision Tree with Predictions:

                    House
                     / \
            Location   
            /         \
        Urban          Rural
        /    \        /    \
   Price      Price   Price   Price
   = Area     = Area  = Area  = Area
   × 300     × 200   × 150   × 100
```

**Applied:**
```
1. Classify: Is house urban or rural?
   → Urban
2. Predict within classification:
   → Price = Area × 300
   → 1000 sqft urban house = $300,000
```

### Building Models from Data

**Steps:**
```
1. Collect representative sample data
2. Identify patterns in data
3. Build mathematical or logical model
4. Validate model on new data
5. Deploy for predictions/classifications
```

---

# EXAM STRATEGY & TIPS

## 📋 Preparation Timeline

### Days 1-2: Priority 1 (Very High)
```
Focus areas:
- Week 6: Dictionaries (60 mins)
  - Operations, isKey() pattern
  - List vs Dictionary comparison
  - Update accumulator pattern

- Week 8: Graphs (60 mins)
  - Representation methods
  - Train network problem
  - Direct vs n-hop routes

- Week 9: Recursion & DFS (60 mins)
  - Base case, inductive step
  - DFS algorithm and visited tracking
  - Recursion execution trace
```

### Days 3: Priority 2 (High)
```
- Week 5: Collections & Lists (45 mins)
  - Collection types comparison
  - Insertion sort algorithm
  - List operations and functions

- Week 7: Matrices (45 mins)
  - Matrix structure and access
  - Nested dictionary representation
  - Row/column iteration
```

### Day 4: Priority 3 (Medium)
```
- Week 10: Encapsulation (30 mins)
- Week 11: Concurrency (30 mins)
- Week 12: Bottom-up Computing (30 mins)
```

## 🎯 Question Types & Strategies

### Type 1: Fill in the Code
```
Strategy:
1. Read problem carefully
2. Identify data structure needed
3. Recall correct operations for that structure
4. Fill in step by step

Example:
marks = {}
for score in scores_list:
    if _____(marks, score):  ← Fill: isKey
        marks[score] = ______  ← Fill: marks[score] + 1
    else:
        marks[score] = ___    ← Fill: 1
```

### Type 2: Trace Execution
```
Strategy:
1. Follow execution line by line
2. Update variables as you go
3. Be careful with recursion: show call stack
4. Verify logic at each step

Example:
function f(n):
    if n <= 1:
        return 1
    else:
        return n + f(n-1)

f(3):
    3 <= 1? No → 3 + f(2)
    f(2): 2 <= 1? No → 2 + f(1)
    f(1): 1 <= 1? Yes → return 1
    f(2) = 2 + 1 = 3
    f(3) = 3 + 3 = 6
```

### Type 3: Identify Output
```
Strategy:
1. Understand algorithm
2. Apply to sample input
3. Show step-by-step computation
4. Verify result makes sense

Example:
What does this print?
for i in [1, 2, 3]:
    for j in [1, 2]:
        print(i, j)

Output:
1 1
1 2
2 1
2 2
3 1
3 2
```

### Type 4: Algorithm Design
```
Strategy:
1. Understand requirements
2. Choose appropriate data structure
3. Write pseudocode with clear logic
4. Add explanatory comments

Example:
Write pseudocode to find second largest element:

max1 = -infinity
max2 = -infinity

foreach element in list:
    if element > max1:
        max2 = max1
        max1 = element
    else if element > max2 and element != max1:
        max2 = element

return max2
```

## 🔑 Quick Reference Patterns

### Dictionary Update
```
if isKey(d, k):
    d[k] = d[k] + v
else:
    d[k] = v
```

### DFS Template
```
visited = {}

function dfs(vertex):
    visited[vertex] = True
    process(vertex)
    
    for each neighbor in graph[vertex]:
        if not isKey(visited, neighbor):
            dfs(neighbor)
```

### Recursion Template
```
function recursive(n):
    if base_condition(n):
        return base_value
    else:
        return combine(n, recursive(smaller_n))
```

### Matrix Iteration
```
foreach i in rows(matrix):
    foreach j in columns(matrix[i]):
        process(matrix[i][j])
```

## ⚠️ Common Mistakes to Avoid

### ❌ Mistake 1: Dictionary Access Without isKey()
```
Wrong: value = d["key"]  ← Crashes if key missing
Right: if isKey(d, "key"):
           value = d["key"]
```

### ❌ Mistake 2: Infinite Recursion
```
Wrong: return f(n) + f(n)  ← Same argument!
Right: return f(n) + f(n-1)  ← Decreasing argument
```

### ❌ Mistake 3: Confusing n-hop Routes
```
Wrong: Direct routes = all routes with any number of changes
Right: Direct routes = single train only
       1-hop = change at most 1 time
       2-hop = change at most 2 times
```

### ❌ Mistake 4: Missing Visited in DFS
```
Wrong: dfs(vertex):
           process(vertex)
           for each neighbor:
               dfs(neighbor)  ← Revisits on cycles!

Right: dfs(vertex):
           visited[vertex] = True
           process(vertex)
           for each neighbor:
               if not in visited:
                   dfs(neighbor)
```

### ❌ Mistake 5: Matrix Access Errors
```
Wrong: matrix[i, j]  ← Wrong syntax
Right: matrix[i][j]  ← Correct nested access
```

## 📊 Practice Checklist

**Before the exam, practice:**

- [ ] 5 dictionary operation problems
- [ ] 3 graph/train network problems
- [ ] 4 recursion/DFS problems
- [ ] 2 matrix/2D problems
- [ ] 3 list/sorting problems
- [ ] 2 encapsulation problems
- [ ] 1 concurrency problem
- [ ] Trace 5 different algorithms
- [ ] Design 3 algorithms from scratch
- [ ] Identify 10 common mistakes

## ✅ During the Exam

**Time Management:**
- Read all questions first (2 mins)
- Allocate time based on marks/difficulty
- High priority: Dictionaries, Graphs, DFS, Lists
- Medium priority: Matrices, Encapsulation
- Low priority: Concurrency, Bottom-up (if time)

**Answering:**
1. Read problem 2-3 times carefully
2. Identify what data structure needed
3. Write clear pseudocode with comments
4. Show step-by-step reasoning
5. Verify your answer makes sense
6. Check for common mistakes

**If stuck:**
- Move to next question
- Come back with fresh perspective
- Partial credit is better than nothing
- Write down your thought process

## 🎓 Final Tips

1. **Understand, don't memorize:** Know WHY, not just WHAT
2. **Draw diagrams:** Visualize graphs, recursion trees, matrices
3. **Practice tracing:** Follow code execution carefully
4. **Test your thinking:** Make up examples and work through them
5. **Group related concepts:** Link Week 8 (Graphs) with Week 9 (DFS)
6. **Get enough sleep:** Fresh mind for exam
7. **Be confident:** You've got this! 🚀

---

# SUMMARY: Topic Importance Table

| Week | Topic | Importance | Key Concepts | Est. Questions |
|------|-------|-----------|------|---|
| 5 | Collections & Lists | HIGH | Types, operations, insertion sort | 2-3 |
| 6 | Dictionaries | VERY HIGH | isKey(), operations, update pattern | 3-4 |
| 7 | Matrices | HIGH | 2D access, iteration, nested dicts | 1-2 |
| 8 | Graphs | VERY HIGH | Representation, routes, train problem | 3-4 |
| 9 | Recursion & DFS | VERY HIGH | Base case, inductive step, visited | 3-4 |
| 10 | Encapsulation | MEDIUM-HIGH | OOP, benefits, state retention | 1-2 |
| 11 | Concurrency | MEDIUM | Polling, producer-consumer, race conditions | 0-1 |
| 12 | Bottom-up Computing | MEDIUM | Classification, prediction, decision trees | 0-1 |

**Total: Expected 14-20 questions in Quiz 2**

---

# GOOD LUCK! 🚀📚

*Remember: Success in this quiz comes from understanding concepts deeply and practicing consistently. You've got all the tools you need. Go ace it!*

---

*This study guide was created specifically for IITM BS Data Science - Computational Thinking Quiz 2 Preparation*
*Last Updated: November 20, 2025*
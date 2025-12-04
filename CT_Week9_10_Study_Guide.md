# Computational Thinking: Week 9 & 10 Complete Study Guide

## WEEK 9: RECURSION & DEPTH FIRST SEARCH (DFS)

---

### CORE CONCEPTS

#### 1. RECURSION FUNDAMENTALS

**Definition:** Recursion means a defined function calls itself. It's a natural way to solve problems that can be broken down into smaller, similar subproblems.

**Key Components:**
- **Base Case:** The terminating condition where the function directly returns a value without further recursion
- **Inductive Step:** The recursive case where the function calls itself with a smaller/simpler argument

**Why Recursion Works:**
- Many mathematical and computational problems are naturally defined inductively
- Each recursive call works on a smaller problem until reaching the base case
- The computation then "unwinds" back up with the final result

**Structure Template:**
```
function solve(n):
    if n is base case:
        return direct_value
    else:
        return solve(n-1) or solve(smaller_n)
```

---

#### 2. RECURSION EXAMPLES

**Example 1: Factorial**
```
Factorial(n) = n × Factorial(n-1)
Base case: Factorial(0) = 1, Factorial(1) = 1

Trace for Factorial(5):
= 5 × Factorial(4)
= 5 × (4 × Factorial(3))
= 5 × (4 × (3 × Factorial(2)))
= 5 × (4 × (3 × (2 × Factorial(1))))
= 5 × (4 × (3 × (2 × 1)))
= 120
```

**Example 2: Fibonacci**
```
Fibonacci(n) = Fibonacci(n-1) + Fibonacci(n-2)
Base cases: Fibonacci(0) = 0, Fibonacci(1) = 1

Trace for Fibonacci(4):
= Fibonacci(3) + Fibonacci(2)
= (Fibonacci(2) + Fibonacci(1)) + (Fibonacci(1) + Fibonacci(0))
= ((Fibonacci(1) + Fibonacci(0)) + Fibonacci(1)) + (Fibonacci(1) + Fibonacci(0))
= ((1 + 0) + 1) + (1 + 0)
= 3
```

**Example 3: Sum of List**
```
Sum([1, 2, 3, 4, 5])
= 1 + Sum([2, 3, 4, 5])
= 1 + (2 + Sum([3, 4, 5]))
= 1 + (2 + (3 + Sum([4, 5])))
= 1 + (2 + (3 + (4 + Sum([5]))))
= 1 + (2 + (3 + (4 + 5)))
= 15

Base case: Sum([]) = 0
```

**Example 4: Power Function**
```
Power(x, n):
    if n == 0:
        return 1
    else:
        return x × Power(x, n-1)

Power(2, 4) = 2 × Power(2, 3)
            = 2 × (2 × Power(2, 2))
            = 2 × (2 × (2 × Power(2, 1)))
            = 2 × (2 × (2 × (2 × Power(2, 0))))
            = 2 × (2 × (2 × (2 × 1)))
            = 16
```

---

#### 3. DEPTH FIRST SEARCH (DFS)

**Definition:** DFS is a graph traversal algorithm that explores as far as possible along each branch before backtracking.

**Key Points:**
- Used to explore all vertices reachable from a given starting vertex
- Maintains information about visited nodes in a **visited dictionary**
- Recursively explores unvisited neighbors
- Used to discover graph properties (e.g., connectivity, cycles)

**Algorithm Structure:**
```
visited = {} (empty dictionary)

DFS(i):
    if i is already visited:
        return
    else:
        mark i as visited
        for each unvisited neighbor j of i:
            DFS(j)
```

**Why Dictionary for Visited?**
- Tracks which nodes have been explored
- Prevents processing a node more than once
- Avoids infinite loops when graph contains cycles

**Example: DFS on Train Network**

Given trains connecting stations:
- Train 1: A → B → C
- Train 2: B → D
- Train 3: D → E

Starting from Station A:
```
Visit A (mark as visited)
  Look at neighbors of A: [B]
  Visit B (mark as visited)
    Look at neighbors of B: [C, D]
    Visit C (mark as visited)
      Look at neighbors of C: []
      No more neighbors
    Visit D (mark as visited)
      Look at neighbors of D: [E]
      Visit E (mark as visited)
        Look at neighbors of E: []
        No more neighbors

Result: DFS order = A, B, C, D, E
Reachable from A: {A, B, C, D, E}
```

**Applications of DFS:**
- Finding connected components in a graph
- Detecting cycles
- Topological sorting
- Finding paths between nodes
- Checking if graph is connected

---

### BEST PRACTICE POINTS FOR WEEK 9

1. **Always Define Base Case Clearly** - Without proper base case, recursion never stops
2. **Reduce Problem Size** - Each recursive call must work on a smaller input
3. **Trust the Recursion** - Assume the recursive call works correctly
4. **Use Dictionary for DFS** - Never use lists for visited tracking (inefficient)
5. **Initialize Visited Dictionary** - Start fresh with empty dictionary for each DFS
6. **Mark Before Processing** - Mark node as visited BEFORE processing its neighbors

---

### PRACTICE QUESTIONS - WEEK 9

**Q1: Basic Recursion - Sum of Natural Numbers**
Write a recursive function to find the sum of first n natural numbers (1+2+3+...+n).
- Input: n = 5
- Expected Output: 15
- Base Case: sum(0) = 0
- Recursive Case: sum(n) = n + sum(n-1)

**Q2: String Reversal with Recursion**
Write a recursive function to reverse a string.
- Input: "HELLO"
- Expected Output: "OLLEH"
- Base Case: reverse("") = ""
- Recursive Case: reverse(str) = str[-1] + reverse(str[:-1])

**Q3: Checking if List is Palindrome**
Write a recursive function to check if a list is palindrome.
- Input: [1, 2, 3, 2, 1]
- Expected Output: True
- Input: [1, 2, 3, 4]
- Expected Output: False

**Q4: DFS - Connected Components**
Given a train network represented as adjacency dictionary:
```
trains = {
    'A': ['B', 'C'],
    'B': ['D'],
    'C': ['B'],
    'D': [],
    'E': ['F'],
    'F': []
}
```
Find all stations reachable from station 'A' using DFS.
- Expected Output: {'A', 'B', 'C', 'D'}
- Expected from 'E': {'E', 'F'}

**Q5: DFS - Path Finding**
Using DFS, find if there is a path from station X to station Y in a train network.
- Graph: A→B, B→C, C→D, E→F (not connected)
- Path A to D? Yes (A→B→C→D)
- Path A to F? No

**Q6: Factorial with Edge Cases**
Write recursive function to calculate factorial.
- Input: 0
- Expected Output: 1
- Input: 5
- Expected Output: 120
- Input: 1
- Expected Output: 1

**Q7: Count Down Recursion**
Write recursive function to print numbers from n down to 1.
- Input: n = 5
- Expected Output: 5, 4, 3, 2, 1
- Base Case: When n == 0, stop

**Q8: Fibonacci Sequence**
Write recursive function for Fibonacci with optimized approach.
- fib(0) = 0
- fib(1) = 1
- fib(6) = 8
- Challenge: Optimize to avoid redundant calculations

**Q9: DFS - Cycle Detection**
Determine if a graph has a cycle using DFS.
- Graph with cycle: A→B→C→A (Yes, has cycle)
- Graph without cycle: A→B→C (No cycle)

**Q10: Linear Search Recursion**
Write recursive function to search for element in a list.
- List: [5, 2, 8, 1, 9]
- Search for: 8
- Expected Output: True (found at index 2)
- Search for: 10
- Expected Output: False (not found)

---

## WEEK 10: ENCAPSULATION & OBJECT-ORIENTED PROGRAMMING

---

### CORE CONCEPTS

#### 1. ENCAPSULATION FUNDAMENTALS

**Definition:** Encapsulation packages procedures (methods) with the data elements (fields) on which they operate into a single unit called an **object**.

**Why Encapsulation?**

Without encapsulation (Procedural approach):
```
Procedures: withdraw(accountId, amount), deposit(accountId, amount)
Data: accountBalances dictionary stored separately
Problem: Procedures are "unanchored" - not directly connected to data
Issue: Side effects can happen anywhere, hard to manage state
```

With encapsulation (Object-oriented approach):
```
Object: BankAccount
  - Fields (Data): balance, accountId, owner
  - Methods (Procedures): withdraw(), deposit(), getBalance()
Advantage: Data and procedures bundled together
```

#### 2. KEY PRINCIPLES OF ENCAPSULATION

**A. Data Hiding (Private Fields)**
- Hide implementation details from external world
- Only expose necessary information through methods
- Prevents unauthorized/incorrect modifications

**B. Interfaces (Public Methods)**
- Procedures act as interfaces between external world and object
- External world communicates ONLY through these methods
- Changes to implementation don't affect external users (if interface stays same)

**C. State Retention**
- Object holds state between procedure calls
- Previous values are retained
- Reduces need to pass all data as parameters

**D. Side Effects Management**
- Side effects become explicit and part of the design
- Object's own fields can be modified intentionally
- More natural than modifying global variables

---

#### 3. COMPARISON: PROCEDURES vs OBJECTS

| Aspect | Procedures | Objects |
|--------|-----------|---------|
| Coupling | Data and procedures separate | Data and procedures bundled |
| State Management | Stateless (pass everything as params) | Stateful (holds state between calls) |
| Side Effects | Implicit, hard to manage | Explicit, natural |
| Reusability | Limited contexts | Multiple instances with different states |
| Interface | Parameters and return values | Methods and fields |
| Modification | Affects all callers if changed | Can extend without affecting existing code |

---

#### 4. DATATYPES REVIEW FOR ENCAPSULATION

**Basic Datatypes:**
- Integer: Range from -∞ to +∞, operations: +, -, *, /, %, <, >
- Character: Single symbol, very limited operations
- Boolean: True/False, operations: AND, OR, NOT
- String: Sequence of characters, operations: concatenation, comparison

**Subtypes (Restricted versions):**
- Marks: Integer restricted to 0-100
- Gender: Character restricted to M/F
- Quantity: Integer ≥ 0

**Compound Datatypes:**
- Record: Multiple named fields (like struct/tuple)
  - Example: StudentRecord = {id, name, marks, semester}
- List: Sequence of same-type elements
  - Example: [student1, student2, student3]
- Dictionary: Key-value pairs
  - Example: {student_id: student_record}

**Adding Procedures to Datatypes:**

Now with encapsulation:
```
StudentRecord datatype can have fields:
  - id: Integer
  - name: String
  - marks: Marks (0-100)
  
AND can have procedures:
  - getGrade(): returns letter grade based on marks
  - updateMarks(newMarks): updates marks if valid
  - getDetails(): returns formatted student info
```

---

#### 5. OBJECT-ORIENTED EXAMPLE: ATM ACCOUNT

**Without Objects (Procedural):**
```
accountBalances = {}
accountPins = {}
accountLocks = {}

procedure withdraw(accountId, amount):
    if amount <= 0:
        return "Invalid amount"
    if amount > accountBalances[accountId]:
        return "Insufficient funds"
    accountBalances[accountId] = accountBalances[accountId] - amount
    return "Withdrawal successful"

procedure deposit(accountId, amount):
    if amount <= 0:
        return "Invalid amount"
    accountBalances[accountId] = accountBalances[accountId] + amount
    return "Deposit successful"

Problem: Need to manage state across multiple procedure calls
State: Which account is currently locked? Who's using which account?
```

**With Objects (OOP):**
```
Object: BankAccount
  Fields (Private):
    - balance: Money
    - pin: Integer
    - isLocked: Boolean
    - owner: String
  
  Methods (Public):
    - withdraw(amount):
        Check if locked
        Check if amount valid
        Check if balance sufficient
        Update balance
        Return status
    
    - deposit(amount):
        Check if amount valid
        Update balance
        Return status
    
    - lock():
        Set isLocked = True
    
    - unlock(pin):
        Check if pin correct
        Set isLocked = False if correct

Advantage: Each account object maintains its own state
Multiple accounts can be created: account1, account2
Each retains state independently
```

---

#### 6. BENEFITS OF ENCAPSULATION

**1. Separation of Concerns**
- What? (Public interface) - separate from How? (Private implementation)
- User of object doesn't need to know implementation details

**2. Modularity**
- Objects are self-contained units
- Can be developed and tested independently
- Easier to understand and maintain

**3. Change Management**
- Can modify internal implementation without affecting users
- As long as public interface remains same
- Example: Change how balance is stored internally (array → dict) without breaking withdraw()

**4. Code Reusability**
- Object patterns can be found across different examples
- Once designed, objects can be reused in many contexts
- Reduces redundant code

**5. Data Protection**
- Private fields prevent accidental/malicious modification
- Access control ensures data integrity
- Example: Can't set balance to negative through withdraw() only

---

### OBJECT DESIGN PATTERNS

**Pattern 1: Simple Data Container**
```
Object: Student
  Fields: id, name, marks
  Methods: getGrade(), toString()
```

**Pattern 2: State Manager (like ATM)**
```
Object: BankAccount
  Fields: balance, pin, owner, isLocked
  Methods: withdraw(), deposit(), lock(), unlock()
  Retains state between calls
```

**Pattern 3: Processor**
```
Object: DataProcessor
  Fields: data, processedData, metadata
  Methods: loadData(), processData(), getResults()
  Processes and transforms data
```

---

### BEST PRACTICE POINTS FOR WEEK 10

1. **Encapsulate Related Data & Methods** - Group what belongs together
2. **Hide Implementation Details** - Use private for internal workings
3. **Expose Clear Interface** - Public methods should be intuitive
4. **Maintain State Properly** - Initialize fields in constructor
5. **Validate Inputs** - Don't trust external data
6. **Use Meaningful Names** - Methods and fields should be self-documenting
7. **Single Responsibility** - Each object should have ONE primary purpose

---

### PRACTICE QUESTIONS - WEEK 10

**Q1: Design a Student Object**
Create an object-oriented design for a Student with:
- Fields: studentId, name, marks (0-100), semester
- Methods: getGrade() (A: 80+, B: 60-79, C: 40-59, D: <40)
- Method: updateMarks(newMarks) - only valid 0-100
- Method: isEligible() - returns true if marks ≥ 40
- Question: Can you pass marks = 150? Why should this fail?

**Q2: Bank Account with Encapsulation**
Design a BankAccount object:
- Private Fields: balance (≥0), pin (4 digits), owner, transactions[]
- Public Methods:
  - withdraw(amount): Check balance, update, return new balance
  - deposit(amount): Add amount, return new balance
  - getBalance(): Return current balance
- Question: Why is balance PRIVATE and not PUBLIC?
- Question: What happens if someone tries to set balance = -1000 directly vs through withdraw()?

**Q3: Compare Two Approaches**

BEFORE (Procedural):
```
students = [student1_dict, student2_dict, ...]
procedure getStudentGrade(student_dict):
    marks = student_dict['marks']
    ...calculate grade...
    return grade
```

AFTER (Encapsulated):
```
students = [student1_obj, student2_obj, ...]
student1_obj.getGrade()
```

Questions:
- Which is easier to use? Why?
- If you need to change how grade is calculated, what changes in each approach?
- Which maintains better separation of concerns?

**Q4: Library Book System**
Design a Book object with encapsulation:
- Fields: isbn, title, author, isAvailable, borrower
- Methods:
  - borrowBook(personName): Mark borrowed if available
  - returnBook(): Mark as available
  - getDetails(): Return book information
- Question: Why shouldn't external code directly set isAvailable = True?
- Question: What validation should happen in borrowBook()?

**Q5: Temperature Converter Object**
Create a Temperature object:
- Field: temperature (private)
- Methods:
  - setFahrenheit(f): Set temperature in Fahrenheit
  - getCelsius(): Return temperature in Celsius
  - getKelvin(): Return temperature in Kelvin
- Question: Why store only one value (Fahrenheit) but provide multiple getters?
- Question: What's the advantage vs having three separate temperature fields?

**Q6: Shopping Cart Encapsulation**
Design a ShoppingCart object:
- Fields: items[], totalPrice
- Methods:
  - addItem(product, quantity): Add product to cart
  - removeItem(productId): Remove product from cart
  - getTotal(): Return total price
- Question: Should totalPrice be calculated fresh each time or cached?
- Question: What happens if you add same product twice?

**Q7: Traffic Light State Management**
Create a TrafficLight object that maintains state:
- Fields: color (RED, YELLOW, GREEN), time_remaining
- Methods:
  - changeColor(): Change to next color
  - getColor(): Return current color
  - start(duration): Start light for duration
- Question: How does object retain state between method calls?
- Question: Why is this better than global variables?

**Q8: User Authentication**
Design User object:
- Private Fields: username, passwordHash, loginAttempts, isLocked
- Public Methods:
  - login(password): Authenticate user
  - logout(): End session
  - changePassword(oldPassword, newPassword): Change password safely
- Questions:
  - Why is password stored as HASH not plain text?
  - Why is loginAttempts private?
  - What prevents someone from directly setting isLocked = False?

**Q9: Hotel Reservation**
Create Reservation object:
- Fields: reservationId, guestName, roomNumber, checkInDate, checkOutDate, totalPrice
- Methods:
  - cancel(): Cancel if allowed
  - modifyDates(newCheckIn, newCheckOut): Change dates
  - getStayDuration(): Calculate days
- Question: What validation should happen when modifying dates?
- Question: Can you cancel a reservation from the past? Why/why not?

**Q10: Medical Patient Record**
Design Patient object with complete encapsulation:
- Private Fields: patientId, name, age, medicalHistory[], medications[]
- Public Methods:
  - addMedicalRecord(record): Add to history
  - getCurrentMedications(): Get active medications
  - updateMedication(med): Change medication
  - getAgeGroup(): Return age category (Child/Adult/Senior)
- Questions:
  - Why is medicalHistory PRIVATE?
  - What validation should happen in addMedicalRecord()?
  - Can external code directly read patientId? Should it?

---

## COMBINED WEEK 9 & 10: INTEGRATION QUESTIONS

**Q1: Recursive Encapsulation**
Create a TreeNode object that uses recursion internally:
- Fields: value, children[]
- Methods:
  - addChild(TreeNode): Add child node
  - sumAll(): Return sum of all values in tree (use recursion)
  - findMax(): Find maximum value (use recursion)
- Challenge: Implement sumAll() recursively while keeping data encapsulated

**Q2: DFS with Objects**
Design a Graph object with nodes as objects:
- Node Object: Fields (id, value), Methods (getId, getValue)
- Graph Object: Fields (nodes[], edges[]), Methods (dfs(startNode), getReachable(node))
- Use DFS to find all reachable nodes while maintaining encapsulation

**Q3: Recursive Backup System**
Create a FileSystem object:
- Fields: name, type (file/folder), size, children[] (if folder)
- Methods:
  - getTotalSize(): Recursively calculate folder size
  - backup(): Recursively backup all files
  - search(fileName): Recursively find file
- Implement using recursion with proper encapsulation

---

## EXAM TIPS FOR WEEK 9 & 10

**For Week 9 (Recursion & DFS):**
1. Always write base case FIRST
2. Trace through small examples to verify logic
3. Count recursive calls to understand complexity
4. For DFS, always mark visited BEFORE processing
5. Use dictionaries for visited tracking (not lists)

**For Week 10 (Encapsulation):**
1. Identify what data should be private (internal state)
2. Design methods that represent natural operations on object
3. Add validation in methods (not after calling method)
4. Think about state retention between calls
5. Make method names represent what they do

**General Strategy:**
- Recursion problems: Focus on reducing problem size
- Encapsulation problems: Focus on bundling related data/methods
- Combined problems: Use recursion inside encapsulated objects
- Practice drawing object structures before coding

---

## KEY FORMULAS & PATTERNS

**Recursion Pattern:**
```
result = base_case if condition else recursive_call(smaller_input)
```

**DFS Pattern:**
```
visited = {}
dfs(node):
    mark node as visited
    for each unvisited neighbor:
        dfs(neighbor)
```

**Encapsulation Pattern:**
```
Object:
  Private Fields: actual data
  Public Methods: interfaces to access/modify data safely
```

---

## SUMMARY TABLE

| Concept | Week 9 | Week 10 |
|---------|--------|---------|
| Focus | Problem Solving | Code Organization |
| Key Technique | Recursive calls | Object bundling |
| State Management | Implicit (stack) | Explicit (object fields) |
| Main Benefit | Natural for tree/graph problems | Maintainability & reusability |
| Main Pattern | Base case + inductive step | Fields + methods |
| Testing | Trace recursion | Verify state retention |

---

**ALL THE BEST FOR YOUR EXAM!**
**Study these concepts thoroughly, practice questions multiple times, and master the patterns!**

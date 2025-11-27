# 🚀 IITM BS Python OPPE 2 - Complete Theory Guide with Questions & Solutions

---

## 📖 COMPLETE THEORY BREAKDOWN

---

# PART 1: LAMBDA FUNCTIONS & FUNCTIONAL PROGRAMMING

## What is a Lambda Function?

A **lambda function** is a small anonymous function in Python. It's a way to create a function without using `def`. Lambda functions can take multiple arguments but can only have one expression.

### Why Use Lambda?

1. **Conciseness** - Write simple functions in one line
2. **Use with map(), filter(), sorted()** - Perfect for functional programming
3. **Anonymous** - No need to name simple functions
4. **Readability** - When used correctly, makes code cleaner

### Syntax

```python
lambda arguments: expression

# Examples:
lambda x: x + 1              # Takes x, returns x+1
lambda x, y: x + y           # Takes x and y, returns their sum
lambda x: x if x > 0 else 0  # With conditional
```

### Key Rule
⚠️ **Lambda can only have ONE expression** - no multiple statements, no loops inside lambda

---

## SECTION 1: Lambda Function Basics

### Example 1: Simple Lambda Operations

```python
# Addition
add = lambda x, y: x + y
print(add(5, 3))           # Output: 8
print(add(10, 20))         # Output: 30

# Multiplication
multiply = lambda x, y: x * y
print(multiply(4, 5))      # Output: 20

# Power
power = lambda x, n: x ** n
print(power(2, 3))         # Output: 8
```

**How it works:**
- `lambda x, y: x + y` creates an unnamed function
- Store it in a variable `add` to use it later
- Call it like `add(5, 3)` just like regular functions

---

### Example 2: Lambda with Conditionals (Ternary Operator)

```python
# Check even or odd
check = lambda x: "Even" if x % 2 == 0 else "Odd"
print(check(4))            # Output: Even
print(check(7))            # Output: Odd

# Get maximum of two numbers
max_num = lambda a, b: a if a > b else b
print(max_num(10, 25))     # Output: 25

# Check if positive, negative, or zero
sign = lambda x: "Positive" if x > 0 else ("Negative" if x < 0 else "Zero")
print(sign(5))             # Output: Positive
print(sign(-3))            # Output: Negative
print(sign(0))             # Output: Zero
```

---

### Example 3: Lambda Returning Tuples

```python
# Return multiple values
calc = lambda x, y: (x + y, x * y, x - y)
result = calc(5, 3)
print(result)              # Output: (8, 15, 2)
print(result[0])           # Output: 8
print(result[1])           # Output: 15

# Return as dictionary
info = lambda x: {"square": x**2, "cube": x**3, "double": x*2}
print(info(3))             # Output: {'square': 9, 'cube': 27, 'double': 6}
```

---

## SECTION 2: map() - Apply Function to Each Element

### What is map()?

`map()` takes a function and applies it to every element in a list/iterable, returning a new list.

### Syntax
```python
map(function, iterable)
# Returns a map object (must convert to list to see results)
```

---

### Example 1: Basic map() with Lambda

```python
# Square each number
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)             # Output: [1, 4, 9, 16, 25]

# Add 10 to each number
numbers = [1, 2, 3, 4, 5]
added = list(map(lambda x: x + 10, numbers))
print(added)               # Output: [11, 12, 13, 14, 15]

# Convert to uppercase
words = ["hello", "world", "python"]
upper = list(map(lambda x: x.upper(), words))
print(upper)               # Output: ['HELLO', 'WORLD', 'PYTHON']
```

---

### Example 2: map() with Multiple Iterables

```python
# Add corresponding elements from two lists
list1 = [1, 2, 3, 4]
list2 = [10, 20, 30, 40]
result = list(map(lambda x, y: x + y, list1, list2))
print(result)              # Output: [11, 22, 33, 44]

# Multiply corresponding elements
result = list(map(lambda x, y: x * y, list1, list2))
print(result)              # Output: [10, 40, 90, 160]

# Create tuples from two lists
result = list(map(lambda x, y: (x, y), list1, list2))
print(result)              # Output: [(1, 10), (2, 20), (3, 30), (4, 40)]
```

---

### Example 3: map() with Built-in Functions

```python
# Convert strings to integers
str_numbers = ['1', '2', '3', '4', '5']
int_numbers = list(map(int, str_numbers))
print(int_numbers)         # Output: [1, 2, 3, 4, 5]

# Convert integers to strings
numbers = [1, 2, 3, 4, 5]
str_numbers = list(map(str, numbers))
print(str_numbers)         # Output: ['1', '2', '3', '4', '5']

# Get lengths of strings
words = ["cat", "elephant", "dog", "butterfly"]
lengths = list(map(len, words))
print(lengths)             # Output: [3, 8, 3, 9]
```

---

### Example 4: map() with Complex Operations

```python
# Extract just names from list of tuples
students = [("Ram", 85), ("Sita", 92), ("Gita", 78)]
names = list(map(lambda x: x[0], students))
print(names)               # Output: ['Ram', 'Sita', 'Gita']

# Extract marks and add 5 bonus
marks = list(map(lambda x: x[1] + 5, students))
print(marks)               # Output: [90, 97, 83]

# Create dictionaries from two lists
keys = ['name', 'age', 'city']
values = ['Ram', 25, 'Delhi']
result = dict(map(lambda k, v: (k, v), keys, values))
print(result)              # Output: {'name': 'Ram', 'age': 25, 'city': 'Delhi'}
```

---

## SECTION 3: filter() - Filter Elements Based on Condition

### What is filter()?

`filter()` returns only those elements for which the function returns `True`.

### Syntax
```python
filter(function, iterable)
# Returns a filter object (must convert to list)
```

---

### Example 1: Basic filter() with Lambda

```python
# Get even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)               # Output: [2, 4, 6, 8, 10]

# Get odd numbers
odds = list(filter(lambda x: x % 2 != 0, numbers))
print(odds)                # Output: [1, 3, 5, 7, 9]

# Get numbers greater than 5
greater = list(filter(lambda x: x > 5, numbers))
print(greater)             # Output: [6, 7, 8, 9, 10]
```

---

### Example 2: filter() with Strings

```python
# Get words with length > 3
words = ["cat", "elephant", "dog", "butterfly", "ant", "zebra"]
long_words = list(filter(lambda x: len(x) > 3, words))
print(long_words)          # Output: ['elephant', 'butterfly']

# Get words starting with 'a'
words = ["apple", "banana", "apricot", "cherry"]
a_words = list(filter(lambda x: x.startswith('a'), words))
print(a_words)             # Output: ['apple', 'apricot']

# Get uppercase words
mixed = ["Hello", "WORLD", "python", "JAVA"]
upper = list(filter(lambda x: x.isupper(), mixed))
print(upper)               # Output: ['WORLD', 'JAVA']
```

---

### Example 3: filter() with Lists of Tuples

```python
# Get students with marks >= 75
students = [("Ram", 85), ("Sita", 65), ("Gita", 78), ("Rita", 92)]
passed = list(filter(lambda x: x[1] >= 75, students))
print(passed)              # Output: [('Ram', 85), ('Gita', 78), ('Rita', 92)]

# Get students whose names start with 'R'
r_students = list(filter(lambda x: x[0].startswith('R'), students))
print(r_students)          # Output: [('Ram', 85), ('Rita', 92)]
```

---

### Example 4: Combining map() and filter()

```python
# Get squares of even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8]
result = list(map(lambda x: x**2, filter(lambda x: x % 2 == 0, numbers)))
print(result)              # Output: [4, 16, 36, 64]

# Get doubled marks of students with marks >= 80
students = [("Ram", 85), ("Sita", 65), ("Gita", 78), ("Rita", 92)]
result = list(map(lambda x: (x[0], x[1]*2), filter(lambda x: x[1] >= 80, students)))
print(result)              # Output: [('Ram', 170), ('Rita', 184)]
```

---

## SECTION 4: sorted() with Lambda - Custom Sorting

### What is sorted()?

`sorted()` sorts an iterable. We can use `key` parameter with lambda for custom sorting.

### Syntax
```python
sorted(iterable, key=lambda x: expression, reverse=True/False)
```

---

### Example 1: Basic Sorting with Lambda

```python
# Sort numbers ascending
numbers = [5, 2, 8, 1, 9, 3]
sorted_asc = sorted(numbers)
print(sorted_asc)          # Output: [1, 2, 3, 5, 8, 9]

# Sort numbers descending
sorted_desc = sorted(numbers, reverse=True)
print(sorted_desc)         # Output: [9, 8, 5, 3, 2, 1]

# Sort strings by length
words = ["cat", "elephant", "dog", "butterfly"]
by_length = sorted(words, key=lambda x: len(x))
print(by_length)           # Output: ['cat', 'dog', 'elephant', 'butterfly']

# Sort strings by reverse length
by_length_desc = sorted(words, key=lambda x: len(x), reverse=True)
print(by_length_desc)      # Output: ['butterfly', 'elephant', 'cat', 'dog']
```

---

### Example 2: Sort Tuples by Specific Element

```python
# Sort students by marks (ascending)
students = [("Ram", 85), ("Sita", 92), ("Gita", 78), ("Rita", 88)]
by_marks = sorted(students, key=lambda x: x[1])
print(by_marks)
# Output: [('Gita', 78), ('Ram', 85), ('Rita', 88), ('Sita', 92)]

# Sort students by marks (descending)
by_marks_desc = sorted(students, key=lambda x: x[1], reverse=True)
print(by_marks_desc)
# Output: [('Sita', 92), ('Rita', 88), ('Ram', 85), ('Gita', 78)]

# Sort students by name alphabetically
by_name = sorted(students, key=lambda x: x[0])
print(by_name)
# Output: [('Gita', 78), ('Ram', 85), ('Rita', 88), ('Sita', 92)]
```

---

### Example 3: Sort Dictionary by Values

```python
# Dictionary of student marks
marks = {"Ram": 85, "Sita": 92, "Gita": 78, "Rita": 88}

# Convert to list of tuples and sort by marks
sorted_marks = sorted(marks.items(), key=lambda x: x[1])
print(sorted_marks)
# Output: [('Gita', 78), ('Ram', 85), ('Rita', 88), ('Sita', 92)]

# Create sorted dictionary
sorted_dict = {k: v for k, v in sorted_marks}
print(sorted_dict)
# Output: {'Gita': 78, 'Ram': 85, 'Rita': 88, 'Sita': 92}

# Sort by name
sorted_by_name = sorted(marks.items(), key=lambda x: x[0])
print(sorted_by_name)
# Output: [('Gita', 78), ('Ram', 85), ('Rita', 88), ('Sita', 92)]
```

---

### Example 4: Complex Sorting with Multiple Keys

```python
# Sort by branch first, then by marks (descending)
students = [
    ("Ram", "CSE", 85),
    ("Sita", "ECE", 92),
    ("Gita", "CSE", 88),
    ("Rita", "ECE", 78)
]

sorted_students = sorted(students, key=lambda x: (x[1], -x[2]))
print(sorted_students)
# Output: [('Gita', 'CSE', 88), ('Ram', 'CSE', 85), ('Sita', 'ECE', 92), ('Rita', 'ECE', 78)]
```

---

# PART 2: RECURSION

## What is Recursion?

**Recursion** is when a function calls itself. Every recursive function must have:

1. **Base Case** - A condition where the function STOPS (most important!)
2. **Recursive Case** - The function calls itself with changed parameters
3. **Progress** - Each call must move closer to the base case

### Why Use Recursion?

- Solves problems that are naturally recursive (trees, factorials, searching)
- Makes code cleaner and more readable for some problems
- Breaks complex problems into simpler subproblems

---

## SECTION 1: Recursive Function Structure

### Template for Recursion

```python
def recursive_function(parameters):
    # BASE CASE - MUST HAVE THIS!
    if condition:
        return base_value
    
    # RECURSIVE CASE
    return modified_value + recursive_function(modified_parameters)
```

### Key Points

⚠️ **ALWAYS define base case first!**  
⚠️ **Without base case = infinite recursion = crash!**  
✅ **Each recursive call must have modified parameters**  
✅ **Parameters must move towards base case**

---

## SECTION 2: Essential Recursion Examples

### Example 1: Factorial (Most Important)

**Mathematical Definition:**
- 0! = 1
- n! = n × (n-1)!

```python
def factorial(n):
    # BASE CASE
    if n == 0 or n == 1:
        return 1
    
    # RECURSIVE CASE
    return n * factorial(n - 1)

# Test
print(factorial(0))        # Output: 1
print(factorial(1))        # Output: 1
print(factorial(5))        # Output: 120 (5*4*3*2*1)
print(factorial(10))       # Output: 3628800
```

**Step-by-step for factorial(5):**
```
factorial(5) = 5 * factorial(4)
             = 5 * (4 * factorial(3))
             = 5 * (4 * (3 * factorial(2)))
             = 5 * (4 * (3 * (2 * factorial(1))))
             = 5 * (4 * (3 * (2 * 1)))
             = 5 * (4 * (3 * 2))
             = 5 * (4 * 6)
             = 5 * 24
             = 120
```

---

### Example 2: Fibonacci Series

**Mathematical Definition:**
- fib(0) = 0
- fib(1) = 1
- fib(n) = fib(n-1) + fib(n-2)

```python
def fibonacci(n):
    # BASE CASES
    if n == 0:
        return 0
    elif n == 1:
        return 1
    
    # RECURSIVE CASE
    return fibonacci(n - 1) + fibonacci(n - 2)

# Test
print(fibonacci(0))        # Output: 0
print(fibonacci(1))        # Output: 1
print(fibonacci(5))        # Output: 5 (0,1,1,2,3,5)
print(fibonacci(10))       # Output: 55
```

**Step-by-step for fibonacci(5):**
```
fibonacci(5) = fibonacci(4) + fibonacci(3)
             = (fibonacci(3) + fibonacci(2)) + (fibonacci(2) + fibonacci(1))
             = ((fibonacci(2) + fibonacci(1)) + (fibonacci(1) + fibonacci(0))) + ((fibonacci(1) + fibonacci(0)) + 1)
             = (((fibonacci(1) + fibonacci(0)) + 1) + (1 + 0)) + ((1 + 0) + 1)
             = (((1 + 0) + 1) + 1) + (1 + 1)
             = ((1 + 1) + 1) + 2
             = (2 + 1) + 2
             = 3 + 2
             = 5
```

---

### Example 3: Sum of Natural Numbers

```python
def sum_n(n):
    # BASE CASE
    if n == 0:
        return 0
    
    # RECURSIVE CASE
    return n + sum_n(n - 1)

# Test
print(sum_n(0))            # Output: 0
print(sum_n(5))            # Output: 15 (5+4+3+2+1)
print(sum_n(10))           # Output: 55
```

---

### Example 4: Sum of Digits

**Problem:** Add all digits of a number

```python
def sum_digits(n):
    # BASE CASE - when number becomes 0
    if n == 0:
        return 0
    
    # RECURSIVE CASE
    # Get last digit: n % 10
    # Get remaining: n // 10
    return (n % 10) + sum_digits(n // 10)

# Test
print(sum_digits(0))       # Output: 0
print(sum_digits(123))     # Output: 6 (1+2+3)
print(sum_digits(9876))    # Output: 30 (9+8+7+6)
```

**Step-by-step for sum_digits(123):**
```
sum_digits(123) = (123 % 10) + sum_digits(123 // 10)
                = 3 + sum_digits(12)
                = 3 + ((12 % 10) + sum_digits(12 // 10))
                = 3 + (2 + sum_digits(1))
                = 3 + (2 + ((1 % 10) + sum_digits(1 // 10)))
                = 3 + (2 + (1 + sum_digits(0)))
                = 3 + (2 + (1 + 0))
                = 3 + (2 + 1)
                = 3 + 3
                = 6
```

---

### Example 5: Power Function

```python
def power(base, exp):
    # BASE CASE
    if exp == 0:
        return 1
    
    # RECURSIVE CASE
    return base * power(base, exp - 1)

# Test
print(power(2, 0))         # Output: 1
print(power(2, 3))         # Output: 8 (2*2*2)
print(power(3, 4))         # Output: 81 (3*3*3*3)
print(power(5, 2))         # Output: 25
```

---

### Example 6: GCD (Greatest Common Divisor) - Euclidean Algorithm

```python
def gcd(a, b):
    # BASE CASE
    if b == 0:
        return a
    
    # RECURSIVE CASE
    return gcd(b, a % b)

# Test
print(gcd(12, 18))         # Output: 6
print(gcd(17, 31))         # Output: 1
print(gcd(100, 50))        # Output: 50
print(gcd(54, 24))         # Output: 6
```

---

### Example 7: Check if Prime (Recursive)

```python
def is_prime(n, divisor=2):
    # BASE CASES
    if n <= 1:
        return False
    if divisor * divisor > n:
        return True
    
    # RECURSIVE CASE
    if n % divisor == 0:
        return False
    return is_prime(n, divisor + 1)

# Test
print(is_prime(17))        # Output: True
print(is_prime(18))        # Output: False
print(is_prime(2))         # Output: True
print(is_prime(97))        # Output: True
```

---

### Example 8: Count Occurrences of Character

```python
def count_char(s, char):
    # BASE CASE
    if len(s) == 0:
        return 0
    
    # RECURSIVE CASE
    count = 1 if s[0] == char else 0
    return count + count_char(s[1:], char)

# Test
print(count_char("hello", "l"))      # Output: 2
print(count_char("hello world", "l")) # Output: 3
print(count_char("python", "p"))     # Output: 1
```

---

### Example 9: Reverse a String

```python
def reverse_string(s):
    # BASE CASE
    if len(s) == 0:
        return ""
    
    # RECURSIVE CASE
    return reverse_string(s[1:]) + s[0]

# Test
print(reverse_string(""))           # Output: ""
print(reverse_string("a"))          # Output: "a"
print(reverse_string("hello"))      # Output: "olleh"
print(reverse_string("python"))     # Output: "nohtyp"
```

---

### Example 10: Check if String is Palindrome

```python
def is_palindrome(s):
    # Remove spaces and convert to lowercase
    s = s.replace(" ", "").lower()
    
    # BASE CASE
    if len(s) <= 1:
        return True
    
    # RECURSIVE CASE
    if s[0] != s[-1]:
        return False
    return is_palindrome(s[1:-1])

# Test
print(is_palindrome("racecar"))     # Output: True
print(is_palindrome("hello"))       # Output: False
print(is_palindrome("a man a plan a canal panama"))  # Output: True
print(is_palindrome("madam"))       # Output: True
```

---

## SECTION 3: Advanced Recursion Patterns

### Example 1: Generate All Combinations

```python
def combinations(lst):
    # BASE CASE
    if len(lst) == 0:
        return [[]]
    
    # RECURSIVE CASE
    first = lst[0]
    rest = lst[1:]
    rest_combos = combinations(rest)
    
    # With first element
    with_first = [[first] + combo for combo in rest_combos]
    
    # Without first element
    return rest_combos + with_first

# Test
print(combinations([]))        # Output: [[]]
print(combinations([1]))       # Output: [[], [1]]
print(combinations([1, 2]))    # Output: [[], [2], [1], [1, 2]]
print(combinations([1, 2, 3]))
# Output: [[], [3], [2], [2, 3], [1], [1, 3], [1, 2], [1, 2, 3]]
```

---

### Example 2: Generate All Permutations

```python
def permutations(s):
    # BASE CASE
    if len(s) <= 1:
        return [s]
    
    # RECURSIVE CASE
    result = []
    for i in range(len(s)):
        char = s[i]
        remaining = s[:i] + s[i+1:]
        for perm in permutations(remaining):
            result.append(char + perm)
    return result

# Test
print(permutations(""))         # Output: ['']
print(permutations("a"))        # Output: ['a']
print(permutations("ab"))       # Output: ['ab', 'ba']
print(permutations("abc"))
# Output: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']
```

---

### Example 3: Flatten Nested List

```python
def flatten(lst):
    result = []
    for item in lst:
        # RECURSIVE CASE - if item is list
        if isinstance(item, list):
            result.extend(flatten(item))
        # BASE CASE - if item is not list
        else:
            result.append(item)
    return result

# Test
print(flatten([]))                           # Output: []
print(flatten([1, 2, 3]))                    # Output: [1, 2, 3]
print(flatten([1, [2, 3], 4]))               # Output: [1, 2, 3, 4]
print(flatten([1, [2, [3, 4]], 5]))          # Output: [1, 2, 3, 4, 5]
print(flatten([[[1]], [[2], 3], [4, [5]]]))  # Output: [1, 2, 3, 4, 5]
```

---

### Example 4: Binary Search (Recursive)

```python
def binary_search(arr, target, low=0, high=None):
    if high is None:
        high = len(arr) - 1
    
    # BASE CASE - element not found
    if low > high:
        return -1
    
    mid = (low + high) // 2
    
    # BASE CASE - element found
    if arr[mid] == target:
        return mid
    
    # RECURSIVE CASE - search left half
    elif arr[mid] > target:
        return binary_search(arr, target, low, mid - 1)
    
    # RECURSIVE CASE - search right half
    else:
        return binary_search(arr, target, mid + 1, high)

# Test
arr = [1, 3, 5, 7, 9, 11, 13, 15]
print(binary_search(arr, 7))       # Output: 3
print(binary_search(arr, 1))       # Output: 0
print(binary_search(arr, 15))      # Output: 7
print(binary_search(arr, 8))       # Output: -1 (not found)
```

---

# PART 3: LIST COMPREHENSIONS & DICTIONARY OPERATIONS

## Section 1: List Comprehensions

### Basic Syntax

```python
[expression for item in iterable if condition]
```

### Example 1: Simple Transformations

```python
# Squares of numbers
squares = [x**2 for x in range(1, 6)]
print(squares)             # Output: [1, 4, 9, 16, 25]

# Multiply by 2
doubled = [x * 2 for x in range(1, 6)]
print(doubled)             # Output: [2, 4, 6, 8, 10]

# Convert to uppercase
words = ["hello", "world", "python"]
upper = [word.upper() for word in words]
print(upper)               # Output: ['HELLO', 'WORLD', 'PYTHON']

# Extract first character
first_chars = [word[0] for word in words]
print(first_chars)         # Output: ['h', 'w', 'p']
```

---

### Example 2: With Conditionals (if clause)

```python
# Even numbers
numbers = list(range(1, 11))
evens = [x for x in numbers if x % 2 == 0]
print(evens)               # Output: [2, 4, 6, 8, 10]

# Numbers > 5
greater = [x for x in numbers if x > 5]
print(greater)             # Output: [6, 7, 8, 9, 10]

# Words with length > 3
words = ["cat", "elephant", "dog", "butterfly"]
long_words = [w for w in words if len(w) > 3]
print(long_words)          # Output: ['elephant', 'butterfly']

# Positive numbers only
mixed = [-3, 5, -1, 8, 0, -4, 2]
positive = [x for x in mixed if x > 0]
print(positive)            # Output: [5, 8, 2]
```

---

### Example 3: Nested List Comprehensions

```python
# Flatten 2D list
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [num for row in matrix for num in row]
print(flat)                # Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Matrix transpose
transposed = [[row[i] for row in matrix] for i in range(len(matrix[0]))]
print(transposed)
# Output: [[1, 4, 7], [2, 5, 8], [3, 6, 9]]

# Cartesian product
x = [1, 2, 3]
y = ['a', 'b']
pairs = [(a, b) for a in x for b in y]
print(pairs)
# Output: [(1, 'a'), (1, 'b'), (2, 'a'), (2, 'b'), (3, 'a'), (3, 'b')]
```

---

### Example 4: With if-else (Conditional Expression)

```python
# Replace negative with 0
numbers = [-3, 5, -1, 8, 0, -4, 2]
result = [x if x >= 0 else 0 for x in numbers]
print(result)              # Output: [0, 5, 0, 8, 0, 0, 2]

# Label as Even or Odd
numbers = list(range(1, 6))
labels = ["Even" if x % 2 == 0 else "Odd" for x in numbers]
print(labels)              # Output: ['Odd', 'Even', 'Odd', 'Even', 'Odd']

# Convert to grades
marks = [85, 45, 78, 92, 55]
grades = ["Pass" if m >= 50 else "Fail" for m in marks]
print(grades)              # Output: ['Pass', 'Fail', 'Pass', 'Pass', 'Fail']
```

---

## Section 2: Dictionary Operations

### Creating Dictionaries

```python
# Using dictionary literal
d = {"name": "Ram", "age": 25, "city": "Delhi"}
print(d)                   # Output: {'name': 'Ram', 'age': 25, 'city': 'Delhi'}

# Using dict() constructor
d = dict(name="Ram", age=25, city="Delhi")
print(d)

# From two lists using zip
keys = ["name", "age", "city"]
values = ["Ram", 25, "Delhi"]
d = dict(zip(keys, values))
print(d)
```

---

### Dictionary Methods

```python
d = {"name": "Ram", "age": 25, "city": "Delhi"}

# Get all keys
print(d.keys())            # Output: dict_keys(['name', 'age', 'city'])
print(list(d.keys()))      # Output: ['name', 'age', 'city']

# Get all values
print(d.values())          # Output: dict_values(['Ram', 25, 'Delhi'])
print(list(d.values()))    # Output: ['Ram', 25, 'Delhi']

# Get all key-value pairs
print(d.items())           # Output: dict_items([('name', 'Ram'), ('age', 25), ('city', 'Delhi')])
print(list(d.items()))     # Output: [('name', 'Ram'), ('age', 25), ('city', 'Delhi')]

# Get value with default if key doesn't exist
print(d.get("name"))       # Output: Ram
print(d.get("phone"))      # Output: None
print(d.get("phone", "N/A")) # Output: N/A

# Check if key exists
print("name" in d)         # Output: True
print("phone" in d)        # Output: False

# Update dictionary
d.update({"phone": "98765", "age": 26})
print(d)                   # Updated with new values

# Delete key
del d["city"]
print(d)
```

---

### Dictionary Comprehensions

```python
# Create dictionary from list
numbers = [1, 2, 3, 4, 5]
squares = {x: x**2 for x in numbers}
print(squares)             # Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Create dictionary with conditions
evens = {x: x**2 for x in numbers if x % 2 == 0}
print(evens)               # Output: {2: 4, 4: 16}

# From two lists
keys = ['a', 'b', 'c']
values = [1, 2, 3]
d = {k: v for k, v in zip(keys, values)}
print(d)                   # Output: {'a': 1, 'b': 2, 'c': 3}

# Swap keys and values
original = {'a': 1, 'b': 2, 'c': 3}
swapped = {v: k for k, v in original.items()}
print(swapped)             # Output: {1: 'a', 2: 'b', 3: 'c'}

# Filter dictionary
marks = {"Ram": 85, "Sita": 45, "Gita": 90, "Rita": 35}
passed = {k: v for k, v in marks.items() if v >= 50}
print(passed)              # Output: {'Ram': 85, 'Gita': 90}
```

---

# PART 4: COMPLETE PRACTICE QUESTIONS WITH SOLUTIONS

---

## 🎯 SECTION A: Lambda & Functional Programming Questions

### Q1: Sum of Even Numbers in a List

**Question:** Write a function using lambda and map/filter that calculates the sum of squares of even numbers.

**Solution:**
```python
def sum_even_squares(lst):
    # Filter even numbers, then square them, then sum
    evens = filter(lambda x: x % 2 == 0, lst)
    squares = map(lambda x: x**2, evens)
    return sum(squares)

# One-liner version
def sum_even_squares_v2(lst):
    return sum(map(lambda x: x**2, filter(lambda x: x % 2 == 0, lst)))

# Test
print(sum_even_squares([1, 2, 3, 4, 5, 6]))     # Output: 56 (4+16+36)
print(sum_even_squares([2, 4, 6, 8]))           # Output: 120 (4+16+36+64)
print(sum_even_squares([1, 3, 5]))              # Output: 0 (no evens)
```

---

### Q2: Filter Words and Sort by Length

**Question:** From a list of words, filter those with length > 3, then sort them by length (descending).

**Solution:**
```python
def filter_and_sort(words):
    filtered = list(filter(lambda x: len(x) > 3, words))
    return sorted(filtered, key=lambda x: len(x), reverse=True)

# Test
words = ["cat", "elephant", "dog", "butterfly", "ant", "zebra"]
result = filter_and_sort(words)
print(result)              # Output: ['butterfly', 'elephant']
```

---

### Q3: Transform and Filter List of Tuples

**Question:** Given a list of (name, marks) tuples, filter those with marks >= 75, then extract just the names.

**Solution:**
```python
def get_passed_names(students):
    # Filter students with marks >= 75
    passed = filter(lambda x: x[1] >= 75, students)
    # Extract names using map
    names = map(lambda x: x[0], passed)
    return list(names)

# One-liner
def get_passed_names_v2(students):
    return list(map(lambda x: x[0], filter(lambda x: x[1] >= 75, students)))

# Test
students = [("Ram", 85), ("Sita", 65), ("Gita", 78), ("Rita", 92)]
print(get_passed_names(students))  # Output: ['Ram', 'Gita', 'Rita']
```

---

### Q4: Sort Dictionary by Values

**Question:** Sort a dictionary of marks by marks in descending order.

**Solution:**
```python
def sort_marks_dict(marks_dict):
    # Convert to list of tuples
    items = marks_dict.items()
    # Sort by value (second element) in descending order
    sorted_items = sorted(items, key=lambda x: x[1], reverse=True)
    # Convert back to dictionary
    return dict(sorted_items)

# Test
marks = {"Ram": 85, "Sita": 92, "Gita": 78, "Rita": 88}
result = sort_marks_dict(marks)
print(result)
# Output: {'Sita': 92, 'Rita': 88, 'Ram': 85, 'Gita': 78}
```

---

### Q5: Find Longest Word Using Lambda

**Question:** Find the longest word in a list using sorted() with lambda.

**Solution:**
```python
def longest_word(words):
    if not words:
        return None
    # Sort by length descending and return first
    return sorted(words, key=lambda x: len(x), reverse=True)[0]

# Alternative using max with lambda
def longest_word_v2(words):
    return max(words, key=lambda x: len(x)) if words else None

# Test
words = ["cat", "elephant", "dog", "butterfly"]
print(longest_word(words))        # Output: butterfly
print(longest_word([]))            # Output: None
```

---

### Q6: Character Frequency Using Lambda

**Question:** Count frequency of each character in a string using dictionary comprehension.

**Solution:**
```python
def char_frequency(s):
    return {char: s.count(char) for char in set(s)}

# Alternative using lambda (not recommended)
def char_frequency_v2(s):
    unique_chars = set(s)
    return dict(map(lambda char: (char, s.count(char)), unique_chars))

# Test
print(char_frequency("hello"))
# Output: {'h': 1, 'e': 1, 'l': 2, 'o': 1}

print(char_frequency("mississippi"))
# Output: {'m': 1, 'i': 4, 's': 4, 'p': 2}
```

---

### Q7: Double Numbers if Even, Otherwise Add 1

**Question:** Map function that doubles a number if even, otherwise adds 1.

**Solution:**
```python
def transform_numbers(numbers):
    return list(map(lambda x: x*2 if x%2==0 else x+1, numbers))

# Test
print(transform_numbers([1, 2, 3, 4, 5, 6]))
# Output: [2, 4, 4, 8, 6, 12]
```

---

### Q8: Extract Initials from Names

**Question:** Convert list of full names to initials using map and lambda.

**Solution:**
```python
def get_initials(names):
    return list(map(lambda name: ''.join([word[0].upper() for word in name.split()]), names))

# Test
names = ["john doe", "jane smith", "bob wilson"]
print(get_initials(names))         # Output: ['JD', 'JS', 'BW']
```

---

## 🎯 SECTION B: Recursion Questions

### Q1: Factorial

**Question:** Calculate factorial of a number using recursion.

**Solution:**
```python
def factorial(n):
    # Base case
    if n == 0 or n == 1:
        return 1
    # Recursive case
    return n * factorial(n - 1)

# Test
print(factorial(0))                # Output: 1
print(factorial(5))                # Output: 120
print(factorial(10))               # Output: 3628800
```

---

### Q2: Fibonacci Sequence

**Question:** Generate the nth Fibonacci number using recursion.

**Solution:**
```python
def fibonacci(n):
    # Base cases
    if n == 0:
        return 0
    elif n == 1:
        return 1
    # Recursive case
    return fibonacci(n - 1) + fibonacci(n - 2)

# Test
print(fibonacci(0))                # Output: 0
print(fibonacci(5))                # Output: 5
print(fibonacci(10))               # Output: 55

# Generate first n Fibonacci numbers
def fib_sequence(n):
    return [fibonacci(i) for i in range(n)]

print(fib_sequence(8))             # Output: [0, 1, 1, 2, 3, 5, 8, 13]
```

---

### Q3: Sum of Digits

**Question:** Calculate sum of all digits in a number recursively.

**Solution:**
```python
def sum_digits(n):
    # Base case
    if n == 0:
        return 0
    # Recursive case
    return (n % 10) + sum_digits(n // 10)

# Test
print(sum_digits(0))               # Output: 0
print(sum_digits(123))             # Output: 6
print(sum_digits(9876))            # Output: 30
print(sum_digits(1000))            # Output: 1
```

---

### Q4: Power Function

**Question:** Calculate x^n recursively.

**Solution:**
```python
def power(base, exp):
    # Base case
    if exp == 0:
        return 1
    # Recursive case
    return base * power(base, exp - 1)

# Test
print(power(2, 0))                 # Output: 1
print(power(2, 5))                 # Output: 32
print(power(3, 3))                 # Output: 27
print(power(5, 4))                 # Output: 625
```

---

### Q5: GCD (Greatest Common Divisor)

**Question:** Find GCD of two numbers using Euclidean algorithm recursively.

**Solution:**
```python
def gcd(a, b):
    # Base case
    if b == 0:
        return a
    # Recursive case
    return gcd(b, a % b)

# Test
print(gcd(12, 18))                 # Output: 6
print(gcd(17, 31))                 # Output: 1
print(gcd(100, 50))                # Output: 50
print(gcd(54, 24))                 # Output: 6
```

---

### Q6: Count Character Occurrences

**Question:** Count how many times a character appears in a string.

**Solution:**
```python
def count_char(s, char):
    # Base case
    if len(s) == 0:
        return 0
    # Recursive case
    count = 1 if s[0] == char else 0
    return count + count_char(s[1:], char)

# Test
print(count_char("hello", "l"))    # Output: 2
print(count_char("mississippi", "s"))  # Output: 4
print(count_char("python", "n"))   # Output: 1
```

---

### Q7: Reverse a String

**Question:** Reverse a string using recursion.

**Solution:**
```python
def reverse_string(s):
    # Base case
    if len(s) == 0:
        return ""
    # Recursive case - take last char + reverse of rest
    return reverse_string(s[1:]) + s[0]

# Test
print(reverse_string(""))          # Output: ""
print(reverse_string("hello"))     # Output: "olleh"
print(reverse_string("python"))    # Output: "nohtyp"
print(reverse_string("racecar"))   # Output: "racecar"
```

---

### Q8: Check Palindrome

**Question:** Check if a string is a palindrome recursively.

**Solution:**
```python
def is_palindrome(s):
    # Remove spaces and convert to lowercase
    s = s.replace(" ", "").lower()
    
    # Base case
    if len(s) <= 1:
        return True
    
    # Recursive case
    if s[0] != s[-1]:
        return False
    return is_palindrome(s[1:-1])

# Test
print(is_palindrome("racecar"))    # Output: True
print(is_palindrome("hello"))      # Output: False
print(is_palindrome("a"))          # Output: True
print(is_palindrome("madam"))      # Output: True
```

---

### Q9: Check Prime Number

**Question:** Check if a number is prime using recursion.

**Solution:**
```python
def is_prime(n, divisor=2):
    # Base case - not prime
    if n <= 1:
        return False
    # Base case - prime
    if divisor * divisor > n:
        return True
    # Recursive case
    if n % divisor == 0:
        return False
    return is_prime(n, divisor + 1)

# Test
print(is_prime(2))                 # Output: True
print(is_prime(17))                # Output: True
print(is_prime(18))                # Output: False
print(is_prime(97))                # Output: True
```

---

### Q10: Generate All Combinations

**Question:** Generate all possible combinations (subsets) of a list.

**Solution:**
```python
def combinations(lst):
    # Base case
    if len(lst) == 0:
        return [[]]
    
    # Recursive case
    first = lst[0]
    rest = lst[1:]
    rest_combos = combinations(rest)
    
    # Combinations with first element
    with_first = [[first] + combo for combo in rest_combos]
    
    # All combinations
    return rest_combos + with_first

# Test
print(combinations([]))             # Output: [[]]
print(combinations([1]))            # Output: [[], [1]]
print(combinations([1, 2]))         # Output: [[], [2], [1], [1, 2]]
print(combinations([1, 2, 3]))
# Output: [[], [3], [2], [2, 3], [1], [1, 3], [1, 2], [1, 2, 3]]
```

---

## 🎯 SECTION C: List & Dictionary Questions

### Q1: Number of Days in Month

**Question:** Create a dictionary of months and days, then find days in February using lambda.

**Solution:**
```python
months_dict = {
    'Jan': 31, 'Feb': 28, 'Mar': 31, 'Apr': 30,
    'May': 31, 'Jun': 30, 'Jul': 31, 'Aug': 31,
    'Sep': 30, 'Oct': 31, 'Nov': 30, 'Dec': 31
}

# Using lambda to find days in specific month
get_days = lambda month: months_dict.get(month, "Invalid month")

print(get_days('Feb'))             # Output: 28
print(get_days('Jan'))             # Output: 31
```

---

### Q2: Flatten Nested List

**Question:** Flatten a nested list recursively.

**Solution:**
```python
def flatten(lst):
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

# Test
print(flatten([]))                 # Output: []
print(flatten([1, 2, 3]))          # Output: [1, 2, 3]
print(flatten([1, [2, 3], 4]))     # Output: [1, 2, 3, 4]
print(flatten([1, [2, [3, 4]], 5])) # Output: [1, 2, 3, 4, 5]
```

---

### Q3: Create Dictionary from Two Lists

**Question:** Create a dictionary from names and marks lists.

**Solution:**
```python
names = ["Ram", "Sita", "Gita"]
marks = [85, 90, 75]

# Using dict and zip
result = dict(zip(names, marks))
print(result)
# Output: {'Ram': 85, 'Sita': 90, 'Gita': 75}

# Using dictionary comprehension
result2 = {name: mark for name, mark in zip(names, marks)}
print(result2)
# Output: {'Ram': 85, 'Sita': 90, 'Gita': 75}
```

---

### Q4: Filter and Transform Dictionary

**Question:** Filter students with marks >= 80 and add 5 bonus marks.

**Solution:**
```python
marks = {"Ram": 85, "Sita": 75, "Gita": 88, "Rita": 92}

# Using dictionary comprehension
result = {k: v + 5 for k, v in marks.items() if v >= 80}
print(result)
# Output: {'Ram': 90, 'Gita': 93, 'Rita': 97}
```

---

### Q5: Frequency Count

**Question:** Count frequency of elements in a list.

**Solution:**
```python
def frequency(lst):
    return {item: lst.count(item) for item in set(lst)}

# Using dictionary.get()
def frequency_v2(lst):
    freq = {}
    for item in lst:
        freq[item] = freq.get(item, 0) + 1
    return freq

# Test
print(frequency([1, 2, 2, 3, 3, 3, 4, 4, 4, 4]))
# Output: {1: 1, 2: 2, 3: 3, 4: 4}
```

---

### Q6: Group by Key

**Question:** Group students by their grade.

**Solution:**
```python
students = [
    ("Ram", "A"),
    ("Sita", "B"),
    ("Gita", "A"),
    ("Rita", "B"),
    ("Kita", "A")
]

# Using dictionary comprehension
grades = {
    grade: [name for name, g in students if g == grade]
    for grade in set(grade for name, grade in students)
}
print(grades)
# Output: {'A': ['Ram', 'Gita', 'Kita'], 'B': ['Sita', 'Rita']}
```

---

### Q7: Merge Two Dictionaries

**Question:** Merge two dictionaries (with Python 3.9+).

**Solution:**
```python
d1 = {"a": 1, "b": 2}
d2 = {"c": 3, "d": 4}

# Method 1: Using | operator (Python 3.9+)
merged = d1 | d2
print(merged)                      # Output: {'a': 1, 'b': 2, 'c': 3, 'd': 4}

# Method 2: Using update()
d1_copy = d1.copy()
d1_copy.update(d2)
print(d1_copy)

# Method 3: Using dictionary comprehension
merged = {**d1, **d2}
print(merged)
```

---

### Q8: Swap Keys and Values

**Question:** Swap keys and values in a dictionary.

**Solution:**
```python
d = {'a': 1, 'b': 2, 'c': 3}

# Using dictionary comprehension
swapped = {v: k for k, v in d.items()}
print(swapped)                     # Output: {1: 'a', 2: 'b', 3: 'c'}
```

---

## 🎯 SECTION D: Mixed Challenge Questions

### Q1: Top N Students by Marks

**Question:** Get top 3 students by marks in descending order.

**Solution:**
```python
students = [("Ram", 85), ("Sita", 92), ("Gita", 78), ("Rita", 88), ("Kita", 95)]

def top_students(students, n=3):
    sorted_students = sorted(students, key=lambda x: x[1], reverse=True)
    return sorted_students[:n]

result = top_students(students, 3)
print(result)
# Output: [('Kita', 95), ('Sita', 92), ('Rita', 88)]
```

---

### Q2: Sum of Even Fibonacci Numbers Below 100

**Question:** Find all even Fibonacci numbers below 100 and return their sum.

**Solution:**
```python
def even_fib_sum(limit):
    def fib(n):
        if n <= 0:
            return 0
        elif n == 1:
            return 1
        return fib(n-1) + fib(n-2)
    
    # Generate Fibonacci sequence
    fibs = []
    i = 0
    while True:
        f = fib(i)
        if f >= limit:
            break
        if f % 2 == 0:
            fibs.append(f)
        i += 1
    
    return sum(fibs)

print(even_fib_sum(100))           # Output: 44 (2+8+34)
```

---

### Q3: Most Frequent Character

**Question:** Find the most frequently occurring character in a string.

**Solution:**
```python
def most_frequent_char(s):
    freq = {char: s.count(char) for char in set(s)}
    return max(freq.items(), key=lambda x: x[1])[0]

# Test
print(most_frequent_char("mississippi"))  # Output: 's' or 'i' (4 times each)
print(most_frequent_char("hello world"))  # Output: 'l' (3 times)
```

---

### Q4: Largest Power of 2 Less Than N

**Question:** Find largest power of 2 less than or equal to N recursively.

**Solution:**
```python
def largest_power_of_2(n):
    # Base case
    if n < 2:
        return 1
    
    # Recursive case
    power = largest_power_of_2(n // 2)
    if power * 2 <= n:
        return power * 2
    return power

# Test
print(largest_power_of_2(10))      # Output: 8
print(largest_power_of_2(16))      # Output: 16
print(largest_power_of_2(100))     # Output: 64
```

---

# QUICK REFERENCE CHEAT SHEET

## Lambda Syntax
```python
lambda x: x + 1                    # Single argument
lambda x, y: x + y                 # Multiple arguments
lambda x: x if x > 0 else 0        # With conditional
lambda x: (x, x**2)                # Return tuple
```

## map, filter, sorted
```python
map(lambda x: x*2, lst)            # Apply to each
filter(lambda x: x > 5, lst)       # Keep if True
sorted(lst, key=lambda x: len(x))  # Sort by custom key
```

## Recursion Template
```python
def func(n):
    if condition:          # Base case
        return value
    return func(n-1)       # Recursive case
```

## List Comprehension
```python
[x for x in lst]                   # Copy
[x*2 for x in lst]                 # Transform
[x for x in lst if x > 5]          # Filter
{x: x**2 for x in lst}             # Dict comprehension
```

---

Good luck with your OPPE 2! Master these concepts and practice regularly. You've got this! 💪
# MAD 1 Quiz 2: Complete Study Guide with Detailed Explanations & PYQs

---

## TABLE OF CONTENTS
1. [SQL Fundamentals](#sql-fundamentals)
2. [Flask Routing & APIs](#flask-routing--apis)
3. [JavaScript & DOM Manipulation](#javascript--dom-manipulation)
4. [Jinja2 Templates](#jinja2-templates)
5. [MVC Architecture](#mvc-architecture)
6. [HTTP Methods & REST APIs](#http-methods--rest-apis)
7. [Form Validation](#form-validation)
8. [Complete PYQ Solutions](#complete-pyq-solutions)

---

## SQL FUNDAMENTALS

### 1. SQL LIKE Operator - Pattern Matching

**What is LIKE?**
- Used to search for specific patterns in text columns
- Works with two wildcards: `%` (any number of characters) and `_` (single character)

**Wildcard Rules:**

| Pattern | Meaning | Example |
|---------|---------|---------|
| `LIKE 'A%'` | Starts with 'A' | "Apple", "Ant", "Android" |
| `LIKE '%A'` | Ends with 'A' | "Pizza", "Banana" |
| `LIKE '%A%'` | Contains 'A' anywhere | "Apple", "Banana", "Plane" |
| `LIKE '_a%'` | Second character is 'a' | "Ball", "Cat", "David" |
| `LIKE 'A_%'` | Starts with 'A' and at least 2 chars | "Apple", "Android" (not "A") |

**EASY EXAMPLE:**

```sql
-- Find all employees whose name starts with 'J'
SELECT * FROM employees 
WHERE name LIKE 'J%';

-- Find all emails containing 'gmail'
SELECT * FROM users 
WHERE email LIKE '%gmail%';

-- Find names with exactly 5 characters starting with 'A'
SELECT * FROM students 
WHERE name LIKE 'A____';
```

**PYQ EXAMPLE:** Find all workers whose first name contains letter 'a'
```sql
SELECT * FROM workers 
WHERE first_name LIKE '%a%';
```

---

### 2. SQL SELECT, WHERE, GROUP BY, HAVING

**Basic Structure:**
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
GROUP BY column
HAVING aggregate_function(column) condition
ORDER BY column;
```

**EASY EXAMPLE:**

```sql
-- Get all students from 'Delhi'
SELECT * FROM students 
WHERE city = 'Delhi';

-- Get count of students grouped by city
SELECT city, COUNT(*) as student_count
FROM students
GROUP BY city;

-- Get cities with more than 5 students
SELECT city, COUNT(*) as student_count
FROM students
GROUP BY city
HAVING COUNT(*) > 5;
```

---

### 3. SQL UPDATE Statement

**Syntax:**
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**EASY EXAMPLE:**

```sql
-- Change salary of employee with ID 5
UPDATE employees 
SET salary = 50000 
WHERE id = 5;

-- Increase all salaries by 10%
UPDATE employees 
SET salary = salary * 1.10;

-- Update multiple columns
UPDATE products 
SET type = 'perishable', quantity = quantity + 450 
WHERE type = 'edible liquid';
```

**PYQ EXAMPLE FROM DECEMBER 2024 QUIZ 2:**
"Change the type of 'edible liquid' to 'perishable' and increase quantity by 450"

```python
# In Flask using SQLAlchemy
from flask_sqlalchemy import SQLAlchemy

# The SQL query would be:
UPDATE products 
SET type = 'perishable', quantity = quantity + 450 
WHERE type = 'edible liquid' AND form = 'liquid';
```

---

## FLASK ROUTING & APIs

### 1. Basic Flask Routes

**What is a Route?**
- A URL pattern that Flask recognizes and maps to a Python function

**EASY EXAMPLE:**

```python
from flask import Flask
app = Flask(__name__)

# Simple route
@app.route('/')
def home():
    return "Welcome to home page"

# Route with static path
@app.route('/about')
def about():
    return "About page"

# Route with dynamic parameter
@app.route('/user/<name>')
def greet_user(name):
    return f"Hello, {name}!"
```

**How It Works:**
- User visits: `http://localhost:5000/user/John`
- Flask captures "John" and passes it to `greet_user()` function
- Output: "Hello, John!"

---

### 2. Dynamic Routes with Type Converters

**Different Parameter Types:**

```python
# String (default)
@app.route('/user/<username>')
def user_profile(username):
    return f"Profile of {username}"
# URL: /user/john

# Integer
@app.route('/post/<int:post_id>')
def get_post(post_id):
    return f"Post number {post_id}"
# URL: /post/123

# Float
@app.route('/price/<float:amount>')
def show_price(amount):
    return f"Price: ${amount}"
# URL: /price/29.99

# Path (includes slashes)
@app.route('/file/<path:filepath>')
def get_file(filepath):
    return f"File: {filepath}"
# URL: /file/documents/resume.pdf
```

**PYQ EXAMPLE FROM DECEMBER 2024:**
```python
@app.route('/login/<id>')
def login(id):
    # Check if id is valid...
    if id.isalnum():  # Both letters and numbers
        return abort(400, "Bad Request: Invalid ID")
    return f"Your ID is {id}"
```

---

### 3. Query Parameters vs URL Parameters

**URL Parameter (in route):**
```python
@app.route('/course/<course_name>')
def get_course(course_name):
    # course_name comes from URL: /course/Python
    return f"Course: {course_name}"
```

**Query Parameter (using request.args):**
```python
from flask import request

@app.route('/search')
def search():
    # Get from URL: /search?q=python&results=10
    query = request.args.get('q')
    limit = request.args.get('results')
    return f"Search for {query}, show {limit} results"
```

**PYQ EXAMPLE FROM DECEMBER 2024:**
```python
@app.route('/course/<course_name>')
def show_course(course_name):
    course_id = request.args.get('id')  # Query parameter
    # URL: /course/DBMS?id=2004
    # course_name = 'DBMS'
    # course_id = '2004'
```

---

## JAVASCRIPT & DOM MANIPULATION

### 1. What is DOM?

**DOM = Document Object Model**
- It's a tree structure representing your HTML
- JavaScript can modify it to change what users see

```
Document
  └─ HTML
      ├─ Head
      └─ Body
          ├─ Div#myDiv
          └─ Button.submit-btn
```

---

### 2. Selecting Elements (Finding Things in DOM)

**EASY EXAMPLE:**

```javascript
// Method 1: By ID (most common, fastest)
let header = document.getElementById('myHeader');
// HTML: <h1 id="myHeader">Title</h1>

// Method 2: By Class Name (gets multiple)
let buttons = document.getElementsByClassName('btn');
// HTML: <button class="btn">Click</button>

// Method 3: By Tag Name
let paragraphs = document.getElementsByTagName('p');

// Method 4: CSS Selector (most flexible)
let firstBtn = document.querySelector('.btn');  // First element with class 'btn'
let allBtns = document.querySelectorAll('.btn'); // All elements with class 'btn'
let input = document.querySelector('input[type="email"]');
```

---

### 3. Changing Content

**EASY EXAMPLE:**

```javascript
// Change HTML content
let div = document.getElementById('content');
div.innerHTML = '<p>New content!</p>';

// Change text only (safer)
let para = document.querySelector('p');
para.textContent = 'New text';

// Change attributes
let link = document.querySelector('a');
link.setAttribute('href', 'https://example.com');

// Change CSS styles
let box = document.getElementById('box');
box.style.backgroundColor = 'red';
box.style.padding = '20px';
box.style.display = 'none';

// Add/Remove CSS classes
box.classList.add('highlight');
box.classList.remove('hidden');
box.classList.toggle('active');
```

---

### 4. Creating and Adding Elements

**EASY EXAMPLE:**

```javascript
// Create new element
let newDiv = document.createElement('div');
newDiv.textContent = 'I am new!';
newDiv.id = 'newDiv';

// Add it to the page
document.body.appendChild(newDiv);

// Add to specific parent
let container = document.getElementById('container');
container.appendChild(newDiv);

// Add before an element
let existingElement = document.getElementById('existing');
container.insertBefore(newDiv, existingElement);

// Remove an element
newDiv.remove();
```

---

### 5. Event Handling

**EASY EXAMPLE:**

```javascript
// Click event
let button = document.getElementById('myBtn');
button.addEventListener('click', function() {
    console.log('Button clicked!');
    alert('You clicked me!');
});

// Form submission
let form = document.getElementById('myForm');
form.addEventListener('submit', function(event) {
    event.preventDefault();  // Stop default action
    console.log('Form submitted!');
});

// Input change
let input = document.getElementById('email');
input.addEventListener('change', function() {
    console.log('New value:', this.value);
});

// Keyboard events
document.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
        console.log('Enter key pressed!');
    }
});
```

---

## JINJA2 TEMPLATES

### 1. Basic Template Syntax

**What is Jinja2?**
- A template engine that lets you put Python logic in HTML

**EASY EXAMPLE:**

```html
<!-- Variables -->
<h1>Welcome, {{ username }}!</h1>
<!-- Output: Welcome, John! -->

<!-- If statements -->
{% if is_logged_in %}
    <p>You are logged in</p>
{% else %}
    <p>Please log in</p>
{% endif %}

<!-- Loops -->
<ul>
{% for item in items %}
    <li>{{ item }}</li>
{% endfor %}
</ul>

<!-- Filters (modify data) -->
<p>{{ message | upper }}</p>  <!-- Converts to UPPERCASE -->
<p>{{ message | lower }}</p>  <!-- Converts to lowercase -->
<p>{{ name | title }}</p>     <!-- Converts To Title Case -->
```

**Python Code (sending data to template):**
```python
@app.route('/user/<name>')
def profile(name):
    items = ['Apple', 'Banana', 'Orange']
    return render_template('profile.html', 
                         username=name,
                         items=items,
                         is_logged_in=True,
                         message='hello world')
```

---

### 2. Template Inheritance (Avoiding Repetition)

**Base Template (base.html):**
```html
<!DOCTYPE html>
<html>
<head>
    <title>{% block title %}My Site{% endblock %}</title>
</head>
<body>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
    </nav>
    
    {% block content %}
    Default content here
    {% endblock %}
    
    <footer>© 2024 My Site</footer>
</body>
</html>
```

**Child Template (home.html):**
```html
{% extends "base.html" %}

{% block title %}Home Page{% endblock %}

{% block content %}
    <h1>Welcome to Home</h1>
    <p>This is the home page content</p>
{% endblock %}
```

**Result:**
- Combines base + home = Complete HTML page
- You don't repeat navbar/footer in every page

---

## MVC ARCHITECTURE

**What is MVC?**

| Component | What It Does | Example |
|-----------|-------------|---------|
| **Model** | Data & Business Logic | Database queries, calculations |
| **View** | Displays Data (HTML/Template) | What user sees on screen |
| **Controller** | Processes Requests (Flask Routes) | Receives request, calls Model, sends to View |

**EASY EXAMPLE:**

```python
# CONTROLLER (Flask route)
@app.route('/students/<int:student_id>')
def get_student(student_id):
    # MODEL - Get data
    student = db.session.query(Student).filter_by(id=student_id).first()
    
    # VIEW - Display data
    return render_template('student.html', student=student)
```

**Flow:**
1. User visits: `/students/5`
2. Flask controller (route) gets request
3. Controller queries Model (database) for student ID 5
4. Controller sends data to View (HTML template)
5. Browser displays the page

---

## HTTP METHODS & REST APIs

### 1. HTTP Methods (CRUD Operations)

| Method | Purpose | Example |
|--------|---------|---------|
| **GET** | Read/Retrieve data | Get user profile |
| **POST** | Create new data | Create new user |
| **PUT** | Update entire resource | Replace user info |
| **DELETE** | Remove data | Delete user |
| **PATCH** | Update part of resource | Change only email |

**EASY EXAMPLE:**

```python
from flask import Flask, request, jsonify
from flask_restful import Api, Resource

app = Flask(__name__)
api = Api(app)

# Sample data
users = {
    1: {'name': 'John', 'email': 'john@email.com'},
    2: {'name': 'Jane', 'email': 'jane@email.com'}
}

class User(Resource):
    # GET - Retrieve a user
    def get(self, user_id):
        if user_id in users:
            return users[user_id], 200  # 200 = Success
        return {'error': 'User not found'}, 404  # 404 = Not Found
    
    # POST - Create new user
    def post(self):
        new_id = max(users.keys()) + 1
        users[new_id] = request.json
        return users[new_id], 201  # 201 = Created
    
    # PUT - Update entire user
    def put(self, user_id):
        if user_id in users:
            users[user_id] = request.json
            return users[user_id], 200
        return {'error': 'User not found'}, 404
    
    # DELETE - Remove user
    def delete(self, user_id):
        if user_id in users:
            del users[user_id]
            return {'message': 'User deleted'}, 200
        return {'error': 'User not found'}, 404

api.add_resource(User, '/users/<int:user_id>')
```

**Using the API:**
```bash
# GET request (retrieve)
curl http://localhost:5000/users/1

# POST request (create)
curl -X POST http://localhost:5000/users \
     -d '{"name":"Bob","email":"bob@email.com"}'

# PUT request (update)
curl -X PUT http://localhost:5000/users/1 \
     -d '{"name":"John Updated","email":"new@email.com"}'

# DELETE request
curl -X DELETE http://localhost:5000/users/1
```

---

## FORM VALIDATION

### 1. HTML5 Form Validation

**Frontend Validation (HTML):**

```html
<form action="/submit" method="POST" onsubmit="return validateForm()">
    <!-- Required field -->
    <input type="text" name="username" required>
    
    <!-- Email validation -->
    <input type="email" name="email" required>
    
    <!-- Password with minimum length -->
    <input type="password" name="password" minlength="8" required>
    
    <!-- Number range -->
    <input type="number" name="age" min="18" max="100" required>
    
    <!-- Pattern validation (only letters)-->
    <input type="text" name="name" pattern="[A-Za-z]+" required>
    
    <button type="submit">Submit</button>
</form>
```

**How It Works:**
- User tries to submit form without email → Browser shows error
- User enters invalid email → Browser shows error
- User enters valid data → Form submits

---

### 2. JavaScript Validation

**EASY EXAMPLE:**

```javascript
function validateForm() {
    let email = document.getElementById('email').value;
    
    // Check if email contains @ symbol
    if (email.indexOf('@') === -1) {
        alert('Please enter a valid email');
        return false;  // Don't submit form
    }
    
    return true;  // Submit form
}

// Using addEventListener
let form = document.getElementById('myForm');
form.addEventListener('submit', function(event) {
    let email = document.querySelector('input[type="email"]').value;
    
    if (!email.includes('@')) {
        event.preventDefault();  // Stop form submission
        alert('Invalid email!');
    }
});
```

---

### 3. Server-side Validation (Flask)

**EASY EXAMPLE:**

```python
@app.route('/register', methods=['POST'])
def register():
    email = request.form.get('email')
    password = request.form.get('password')
    
    # Validate on server
    if not email or '@' not in email:
        return {'error': 'Invalid email'}, 400
    
    if not password or len(password) < 8:
        return {'error': 'Password must be 8+ characters'}, 400
    
    # Save to database
    new_user = User(email=email, password=password)
    db.session.add(new_user)
    db.session.commit()
    
    return {'success': 'User registered'}, 201
```

**Why Both?**
- HTML/JavaScript validation: Faster feedback to user
- Server validation: Security (user can't bypass JavaScript)

---

## COMPLETE PYQ SOLUTIONS

### DECEMBER 2024 QUIZ 2 - SELECTED QUESTIONS

---

### **PYQ 1: Memory Bandwidth Calculation**

**Question:**
You have a DDR module with bus width of 64 bits, clock speed of 800 MHz, operating in DDR with 2 values per clock cycle. If the system works in dual channel mode, what is the maximum memory bandwidth in GB/s?

**Solution:**

```
Step 1: Convert bits to bytes
    64 bits ÷ 8 = 8 bytes

Step 2: Convert MHz to GHz (and apply DDR)
    800 MHz × 2 (DDR) = 1600 MHz = 1.6 GHz

Step 3: Calculate for dual channel
    8 bytes × 1.6 GHz × 2 channels = 25.6 GB/s

Answer: 25.6 GB/s
```

---

### **PYQ 2: SQL Update Query**

**Question:**
Write a Python SQLAlchemy query that:
- Changes type of "edible liquid" to "perishable"
- Increases quantity by 450

**Given Data Table:**
| ID | Name | Type | Form | Quantity |
|----|------|------|------|----------|
| 1 | Item1 | Edible | Liquid | 100 |

**Solution:**

```python
# Correct answer:
for product in Product.query.filter_by(type='edible', form='liquid').all():
    product.type = 'perishable'
    product.quantity += 450

db.session.commit()

# Alternative SQL:
UPDATE products 
SET type = 'perishable', quantity = quantity + 450 
WHERE type = 'edible' AND form = 'liquid';
```

---

### **PYQ 3: Flask Dictionary Manipulation**

**Question:**
What will be the output of this Flask API code?

```python
salaries = {'s1': {'basic': 10000}, 's2': {'basic': 20000}, 's3': {'basic': 30000}}

@app.route('/api/salaries')
def do_something():
    HRA = 0.10
    salary_values = [salaries[s]['basic'] * HRA for s in salaries]
    return {'names': list(salaries.keys()), 'hra_values': salary_values}
```

**URL called:** `http://localhost:5000/api/salaries`

**Solution:**

```json
{
    "names": ["s1", "s2", "s3"],
    "hra_values": [1000, 2000, 3000]
}
```

**Explanation:**
- `s1['basic'] * 0.10` = 10000 * 0.10 = 1000
- `s2['basic'] * 0.10` = 20000 * 0.10 = 2000
- `s3['basic'] * 0.10` = 30000 * 0.10 = 3000

---

### **PYQ 4: Flask Dynamic Routing**

**Question:**
What will happen when accessing these URLs?

```python
@app.route('/login/<id>')
def login(id):
    if id.isalnum():
        abort(400)
    return f"Your ID is {id}"
```

**Test Cases:**

| URL | Output |
|-----|--------|
| `http://localhost/login/C2003` | Bad Request (400) |
| `http://localhost/login/john@` | Your ID is john@ |
| `http://localhost/login/` | Not Found (404) |

**Explanation:**
- `C2003` - Contains only letters and numbers → `isalnum()` returns True → abort(400)
- `john@` - Contains special character → `isalnum()` returns False → Returns message
- `/login/` - No ID parameter → Route not matched → 404

---

### **PYQ 5: HTML5 Form Validation**

**Question:**
Which statements are TRUE about this form?

```html
<form action="/submit" method="POST">
    <input type="email" name="email" required>
    <input type="password" name="password" minlength="8" required>
    <button type="submit">Submit</button>
</form>
```

**Options:**
A) HTML5 form validation is incorporated ✓ **TRUE**
B) Backend validation is incorporated ✗ **FALSE**
C) If email is left blank, border becomes red ✗ **FALSE** (depends on CSS)

**Explanation:**
- HTML5 attributes (`required`, `minlength`) provide frontend validation
- No backend validation code is shown
- Border color needs CSS styling

---

### **PYQ 6: SQL LIKE Pattern**

**Question:**
Write SQL query to find all workers whose first name CONTAINS letter 'a'

**Solution:**

```sql
SELECT * FROM workers 
WHERE first_name LIKE '%a%';
```

**Examples that match:**
- "Raman" ✓
- "David" ✓
- "Sarah" ✓
- "John" ✗ (no 'a')

---

### **PYQ 7: SQL Joins**

**Question:**
Find all records where name='Amrita' OR city='Chennai', ordered by name

**Solution:**

```sql
SELECT * FROM table_a 
WHERE name = 'Amrita' OR city = 'Chennai'
ORDER BY name ASC;
```

---

### **PYQ 8: Character Encoding Size**

**Question:**
If sentence "The five boxing wizards jump quickly" is to be saved with minimum encoding, what's the file size in bits?

**Solution:**

```
Step 1: Count unique characters
    T,h,e,space,f,i,v,b,o,x,w,z,a,d,s,j,u,m,p,q,c,k,l,y = 24 characters + 'r','g','n' = 27 unique

Step 2: Find minimum bits needed
    2^4 = 16 (not enough)
    2^5 = 32 (enough for 27 characters)
    Need 5 bits per character

Step 3: Count total characters in sentence
    "The five boxing wizards jump quickly" = 36 characters (including spaces)

Step 4: Calculate total bits
    36 characters × 5 bits = 180 bits

Answer: 180 bits
```

---

### **PYQ 9: REST API - HTTP Methods**

**Question:**
When running:
```bash
curl http://localhost:5000/api/delete/value1
```

What will be the output?

```python
@app.route('/api/<method>/<value>')
def api_handler(method, value):
    if method == 'delete':
        return f"Value {value} deleted successfully"
    return f"Value {value}"
```

**Solution:**
```
Output: "Value value1 deleted successfully"
```

**Note:** curl defaults to GET method, but since parameter name is 'delete', it still matches

---

### **PYQ 10: SQL GROUP BY and HAVING**

**Question:**
Find all cities with more than 2 students

```sql
SELECT city, COUNT(*) as student_count
FROM students
GROUP BY city
HAVING COUNT(*) > 2
ORDER BY student_count DESC;
```

---

### **PYQ 11: One-to-Many Relationship in SQLAlchemy**

**Question:**
Create models for Student (one) and Assignment (many)

**Solution:**

```python
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

class Student(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100))
    # Relationship from parent side
    assignments = db.relationship('Assignment', backref='student')

class Assignment(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100))
    student_id = db.Column(db.Integer, db.ForeignKey('student.id'))  # Foreign key
```

**How it works:**
- One Student has multiple Assignments
- Each Assignment belongs to one Student
- Access: `student.assignments` returns all assignments for that student

---

### **PYQ 12: JavaScript Event Handling**

**Question:**
What happens when button is clicked?

```html
<button id="myBtn">Click me</button>

<script>
let btn = document.getElementById('myBtn');
btn.addEventListener('click', function() {
    console.log('Button was clicked!');
    this.style.backgroundColor = 'red';
});
</script>
```

**Solution:**
- Console logs: "Button was clicked!"
- Button background changes to red
- `this` refers to the button element

---

### **PYQ 13: Jinja2 Template Rendering**

**Question:**
What is the output of this template?

```html
<!-- Template: user.html -->
{% for user in users %}
    <div class="user">
        <h2>{{ user.name | upper }}</h2>
        {% if user.active %}
            <p>Status: Active</p>
        {% else %}
            <p>Status: Inactive</p>
        {% endif %}
    </div>
{% endfor %}
```

**Python code:**
```python
users = [
    {'name': 'john', 'active': True},
    {'name': 'jane', 'active': False}
]
return render_template('user.html', users=users)
```

**Output:**
```html
<div class="user">
    <h2>JOHN</h2>
    <p>Status: Active</p>
</div>

<div class="user">
    <h2>JANE</h2>
    <p>Status: Inactive</p>
</div>
```

---

## QUICK REFERENCE TIPS

### COMMON MISTAKES TO AVOID

❌ **WRONG:** `SELECT * FROM table WHERE city LIKE 'Delhi'`
✓ **RIGHT:** `SELECT * FROM table WHERE city LIKE 'Delhi%'`

❌ **WRONG:** `@app.route('/user')` def user(id):
✓ **RIGHT:** `@app.route('/user/<id>')` def user(id):

❌ **WRONG:** `document.getElementById('myId').text = 'Hello'`
✓ **RIGHT:** `document.getElementById('myId').textContent = 'Hello'`

❌ **WRONG:** `form.validate()` (no validation code)
✓ **RIGHT:** `if email.includes('@'): # validate`

---

## FORMULAS & CONVERSIONS

| Conversion | Formula |
|-----------|---------|
| Bits to Bytes | ÷ 8 |
| Bytes to GB | ÷ (1024³) |
| MHz to GHz | ÷ 1000 |
| Decimal to Binary | Repeated division by 2 |
| Binary to Decimal | Sum of (bit × 2^position) |

---

## EXAM STRATEGY

1. **Read question carefully** - Understand what's being asked
2. **Identify question type:**
   - SQL? → Think about LIKE patterns, JOINs, GROUP BY
   - Flask? → Check routes, parameters, HTTP methods
   - JavaScript? → DOM selection, event handling
   - Theory? → MVC, HTTP concepts, validation

3. **Work step-by-step:**
   - Write pseudo-code first
   - Then write actual code
   - Check syntax

4. **For PYQ:**
   - Check URL first (routing)
   - Check data type (int, string)
   - Check conditions (if statements)
   - Trace through the code

5. **Time Management:**
   - 1-mark questions: 30 seconds each
   - 2-mark questions: 2 minutes each
   - Code questions: 4-5 minutes

---

## FINAL CHECKLIST BEFORE EXAM

✓ Can I write LIKE queries with patterns?
✓ Can I trace through Flask routes with parameters?
✓ Can I select DOM elements and modify them?
✓ Can I write basic SQL queries?
✓ Do I understand HTTP methods (GET/POST/PUT/DELETE)?
✓ Can I validate forms both frontend and backend?
✓ Do I know MVC architecture?
✓ Can I read and understand Jinja2 templates?

---

**Good Luck! You've got this! 🚀**
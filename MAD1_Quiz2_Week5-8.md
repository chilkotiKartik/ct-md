# MAD 1 Quiz 2 – Complete Study Guide (Week 5–8)

## 📚 Table of Contents
1. Week 5 – Controllers & MVC Pattern
2. Week 6 – REST APIs & HTTP
3. Week 7 – Databases & Backend Systems
4. Week 8 – Frontend, Performance & Bandwidth
5. Practice Questions with Solutions

---

## 🎯 **WEEK 5 – Controllers & MVC Pattern**

### What is MVC?

**M – Model** = Database, Data Rules, Business Logic  
**V – View** = What user sees (HTML, CSS, Templates)  
**C – Controller** = The Brain (Takes input → Processes → Sends to View)

```
Browser (User) 
    ↓
Controller (Gets input from View)
    ↓
Model (Processes, talks to Database)
    ↓
View (Shows result to user)
```

### How Controllers Work in Flask

**Example 1: Simple Controller**
```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/greet', methods=['GET', 'POST'])
def greet():
    if request.method == 'POST':
        name = request.form.get('name')  # Input from user
        message = f"Hello, {name}!"
        return render_template('greet.html', msg=message)  # Send to View
    return render_template('form.html')  # Show form
```

**What happens:**
1. User fills form → sends POST request
2. Controller `greet()` catches it
3. Gets name from form (`request.form.get`)
4. Creates message (business logic)
5. Sends to `greet.html` template (View)

### Controller RULES

| ✅ **Controllers DO** | ❌ **Controllers DON'T** |
|---|---|
| Take input from View (forms, URL) | Store data permanently |
| Validate/process input | Render HTML directly |
| Call Model functions (DB operations) | Expose database queries |
| Choose which template to show | Handle styling |

---

### **Week 5 – Simple Practice Questions**

**Q1: MVC Roles**

Which is CORRECT?

A. Model stores data AND handles business rules  
B. View talks to database directly  
C. Controller displays HTML  
D. View processes user input  

**Answer: A**  
**Why:** Model = data + rules; View = only display; Controller = middle person.

---

**Q2: Flask Route to URL**

```python
@app.route('/students/<int:sid>')
def show_student(sid):
    return f"Student {sid}"
```

What URL returns "Student 5"?

A. `/students?sid=5`  
B. `/students/5`  
C. `/students/id=5`  
D. `/students`

**Answer: B**  
**Why:** `<int:sid>` means parameter goes in URL path, not query string.

---

**Q3: Where Does Business Logic Go?**

```python
# WHERE SHOULD THIS CODE BE?
user = db.query(User).filter_by(email=email).first()
if user and user.password == password:
    login_user(user)
    return redirect('/home')
```

A. In the Template (HTML)  
B. In the Controller  
C. In the Model (separate function)  
D. In the View  

**Answer: C (Best Practice)**  
**Why:** Authentication logic should be in Model, controller just calls it.

---

## 🌐 **WEEK 6 – REST APIs & HTTP**

### REST API Basics

**REST = Representational State Transfer**

Think of it like: You're a customer at a restaurant
- **URL = Restaurant location** → `/api/students`
- **HTTP Method = What you want to do** → GET (read), POST (order), PUT (change), DELETE (remove)
- **JSON = What you send/receive** → `{"id": 1, "name": "Sam"}`

### HTTP Methods (VERY IMPORTANT)

| Method | Action | Example | Idempotent? |
|--------|--------|---------|-------------|
| **GET** | Read data (don't change) | Get list of students | ✅ YES |
| **POST** | Create new data | Create new student | ❌ NO |
| **PUT** | Update/Replace data | Update student record | ✅ YES |
| **DELETE** | Remove data | Delete student | ✅ YES |

**Idempotent = Calling 10 times = Same result as 1 time**

### Flask REST API Example

```python
from flask import Flask, jsonify, request

app = Flask(__name__)
students = [
    {"id": 1, "name": "Alice"},
    {"id": 2, "name": "Bob"}
]

# READ (GET)
@app.route('/api/students', methods=['GET'])
def get_students():
    return jsonify(students)  # Returns JSON

# CREATE (POST)
@app.route('/api/students', methods=['POST'])
def add_student():
    data = request.get_json()  # Receives JSON
    new_student = {"id": 3, "name": data['name']}
    students.append(new_student)
    return jsonify(new_student), 201  # 201 = Created

# READ ONE (GET)
@app.route('/api/students/<int:sid>', methods=['GET'])
def get_student(sid):
    student = next((s for s in students if s['id'] == sid), None)
    if student:
        return jsonify(student)
    return {"error": "Not found"}, 404

# UPDATE (PUT)
@app.route('/api/students/<int:sid>', methods=['PUT'])
def update_student(sid):
    data = request.get_json()
    student = next((s for s in students if s['id'] == sid), None)
    if student:
        student['name'] = data['name']
        return jsonify(student)
    return {"error": "Not found"}, 404

# DELETE
@app.route('/api/students/<int:sid>', methods=['DELETE'])
def delete_student(sid):
    global students
    students = [s for s in students if s['id'] != sid]
    return {"msg": "Deleted"}, 200
```

### JSON Rules (VERY COMMON QUIZ TYPE)

**Valid JSON:**
```json
{"id": 5, "name": "Sam", "marks": [78, 90]}
```

**INVALID JSON (Wrong):**
```json
{'id': 5, 'name': 'Sam'}     // Single quotes ❌
{"id": 5, "name": "Sam",}    // Trailing comma ❌
{id: 5, name: "Sam"}         // Unquoted keys ❌
```

### HTTP Status Codes (Memorize These!)

| Code | Meaning | Example |
|------|---------|---------|
| **200** | OK - Success | GET request worked |
| **201** | Created - New resource made | POST request worked |
| **400** | Bad Request - Wrong input | Missing required field |
| **401** | Unauthorized - Need login | Not authenticated |
| **403** | Forbidden - No permission | Can't access resource |
| **404** | Not Found - Resource missing | Student ID doesn't exist |
| **405** | Method Not Allowed | POST on GET-only route |
| **500** | Server Error - Backend issue | Code crashed |

---

### **Week 6 – Practice Questions**

**Q4: REST Method for Creating**

You need to create a new book. Which is correct?

A. `GET /books`  
B. `POST /books`  
C. `PUT /books`  
D. `DELETE /books`  

**Answer: B**  
**Why:** POST is for creating; PUT is for updating.

---

**Q5: Valid JSON?**

Which of these is valid JSON?

1. `{id: 5, name: "Bob"}`
2. `{"id": 5, "name": "Bob"}`
3. `{"id": 5, "name": "Bob",}`
4. `['a', 'b', 10,]`

**Answer: Only 2**  
**Why:** Need double quotes on keys, no trailing commas.

---

**Q6: Stateless Server**

"A REST API is stateless" means:

A. It never uses a database  
B. Each request has all info needed; server forgets previous requests  
C. It doesn't have variables  
D. Only GET requests work  

**Answer: B**  
**Why:** Stateless = server doesn't remember session state; each request is independent.

---

## 🗄️ **WEEK 7 – Databases & Backend Systems**

### Storage Hierarchy (Fast → Slow)

```
┌─────────────────┐
│   Registers     │ ← Fastest, tiny
├─────────────────┤
│   CPU Cache     │ ← Very fast, small
├─────────────────┤
│   RAM           │ ← Fast, medium (volatile ⚠️)
├─────────────────┤
│   SSD/HDD       │ ← Slow, huge (permanent ✅)
└─────────────────┘
```

**Key Idea:** Faster = smaller capacity, more expensive

### Flask-SQLAlchemy – Database Models

**What is SQLAlchemy?** = ORM (Object-Relational Mapper)
- Python Class = Database Table
- Python Object = Database Row
- No SQL queries needed!

**Example: Library System**

```python
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

# TABLE 1: Section
class Section(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100), nullable=False)
    books = db.relationship("Book", back_populates="section")
    # ^^ One section has MANY books

# TABLE 2: Book
class Book(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(200), nullable=False)
    section_id = db.Column(db.Integer, db.ForeignKey("section.id"))
    # ^^ Foreign key = Links to Section
    section = db.relationship("Section", back_populates="books")
    # ^^ Back reference = Can access section from book

# CREATE
fiction = Section(name="Fiction")
db.session.add(fiction)
db.session.commit()

book = Book(title="Harry Potter", section_id=fiction.id)
db.session.add(book)
db.session.commit()

# READ
all_books = Book.query.all()  # Get all books
fiction_books = Book.query.filter_by(section_id=1).all()

# UPDATE
book.title = "Harry Potter (Updated)"
db.session.commit()

# DELETE
db.session.delete(book)
db.session.commit()
```

### Relationships (VERY TESTED)

| Relationship | Example | SQL Concept |
|---|---|---|
| **One-to-Many** | 1 Section → Many Books | Foreign Key in "Many" side |
| **Many-to-Many** | Students ↔ Courses | Junction table needed |
| **One-to-One** | Person ↔ Passport | Foreign Key on one side |

**Foreign Key = Link to parent table**
- Always on the "Many" side
- `db.ForeignKey("parent_table.id")`

---

### **Week 7 – Practice Questions**

**Q7: Storage Speed Order**

Arrange fastest to slowest:  
A. Cache, Registers, RAM, Disk  
B. Registers, Cache, RAM, Disk  
C. Disk, RAM, Cache, Registers  
D. Registers, RAM, Cache, Disk  

**Answer: B**

---

**Q8: One-to-Many Mapping**

One Student can attempt Many Assignments.

What's the relationship type?

A. One-to-One  
B. One-to-Many  
C. Many-to-Many  
D. None  

**Answer: B**

**Code:**
```python
class Student(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100))
    assignments = db.relationship("Assignment", back_populates="student")

class Assignment(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100))
    student_id = db.Column(db.Integer, db.ForeignKey("student.id"))
    student = db.relationship("Student", back_populates="assignments")
```

---

**Q9: ORM Mapping**

In Flask-SQLAlchemy, each MODEL INSTANCE represents:

A. The whole database  
B. A table definition  
C. One row/record in a table  
D. A column  

**Answer: C**

---

## 🎨 **WEEK 8 – Frontend, Performance & Bandwidth**

### Three Ways to Build Frontend

#### 1. **Server-Side Rendering (SSR)** ✅ For traditional web apps

```python
@app.route('/home')
def home():
    posts = Post.query.all()
    return render_template('home.html', posts=posts)
    # Server renders HTML, sends complete HTML to browser
```

**Pros:** SEO-friendly, simple, faster first load  
**Cons:** More server work

#### 2. **Static Sites** ✅ For blogs, documentation

```python
# Pre-built HTML files stored
# Just serve .html files directly
# No server processing
```

**Pros:** Very fast, no server logic  
**Cons:** Can't update in real-time

#### 3. **Client-Side Rendering (CSR)** ✅ For interactive apps (React, Vue)

```python
@app.route('/api/posts')
def get_posts():
    posts = Post.query.all()
    return jsonify([p.to_dict() for p in posts])
    # Server sends JSON, JavaScript builds HTML
```

**Pros:** Interactive, responsive  
**Cons:** More JavaScript, SEO trickier

---

### Performance Math (IMPORTANT!)

**Formula:**
\[
\text{Max Pages/Second} = \frac{\text{Bandwidth (bytes/s)}}{\text{Image Size (bytes) × Images per Page}}
\]

**Example:**
- Bandwidth = 10 MB/s = 10 × 1024 = 10,240 KB/s
- Image size = 100 KB
- Images per page = 1

\[
\text{Pages/s} = \frac{10,240}{100} = 102.4 ≈ 100
\]

---

### HTML, CSS, JavaScript Division

```
┌─────────────────────────────────────┐
│          Webpage Browser            │
├─────────────────────────────────────┤
│  HTML (Structure)                   │
│  ├─ <h1>Title</h1>                 │
│  ├─ <p>Content</p>                 │
│  └─ <img src="photo.jpg">          │
├─────────────────────────────────────┤
│  CSS (Style) - from /static/style.css │
│  ├─ h1 { color: red; }             │
│  └─ body { font-size: 14px; }      │
├─────────────────────────────────────┤
│  JavaScript (Interactivity)         │
│  from /static/script.js             │
│  └─ alert("Hello!");                │
└─────────────────────────────────────┘
```

---

### **Week 8 – Practice Questions**

**Q10: Rendering Choice**

An app uses Flask to render templates. Mostly server-side work. Which term?

A. Client-side rendering  
B. Static site  
C. Server-side rendering  
D. No rendering  

**Answer: C**

---

**Q11: Bandwidth Calculation**

Website serves 1 image of 50 KB per page.  
Bandwidth = 5 MB/s  
Max pages per second = ?

Convert: 5 MB = 5 × 1024 = 5120 KB

\[
\text{Pages/s} = \frac{5120}{50} = 102.4
\]

**Answer:** ~100 pages per second

---

**Q12: Matching Rendering to Use Case**

Match:

1. Blog (static content, good SEO needed)
2. Dashboard (interactive, real-time updates)
3. Marketing site (simple, no backend logic)

Options:
A. SSR  
B. Static site  
C. CSR  

**Answers:**
- 1 → B (Static site)
- 2 → C (CSR)
- 3 → B (Static site)

---

---

## 🧪 **BONUS: Common Tricky Patterns**

### Tricky Pattern 1: Method Not Allowed (405)

```python
@app.route('/users', methods=['GET'])  # Only GET!
def get_users():
    return "All users"

# ❌ POST /users → Returns 405 (Method Not Allowed)
# ✅ GET /users → Works
```

---

### Tricky Pattern 2: Flask Path vs Query

```python
@app.route('/books/<title>')  # title is in PATH
def search_book(title):
    return f"Book: {title}"

# ✅ /books/Harry → Works, title="Harry"
# ❌ /books?title=Harry → 404 Not Found!
```

---

### Tricky Pattern 3: Always Check URL Structure

```python
# DEFINED:
@app.route('/api/students')

# ✅ WORKS: /api/students
# ❌ FAILS: /api/student (missing 's')
# ❌ FAILS: /students (missing 'api/')
# ❌ FAILS: /api/students/ (trailing slash might fail)
```

---

### Tricky Pattern 4: Foreign Keys Must Be in "Many" Side

```python
# ✅ CORRECT
class Course(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    students = db.relationship("Student")  # One side

class Student(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    course_id = db.Column(db.Integer, db.ForeignKey("course.id"))  # Many side

# ❌ WRONG
class Course(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    course_id = db.Column(db.Integer, db.ForeignKey("student.id"))  # Foreign key on ONE side ❌
```

---

## 📝 **QUICK REVISION CHECKLIST**

### Week 5 ✅
- [ ] MVC: Model = data, View = display, Controller = logic
- [ ] Controllers take input, process, send to view
- [ ] URL parameters use `<type:name>` in path

### Week 6 ✅
- [ ] GET (read), POST (create), PUT (update), DELETE (delete)
- [ ] JSON: double quotes, no trailing commas
- [ ] Status codes: 200, 201, 400, 401, 404, 405, 500

### Week 7 ✅
- [ ] Storage: Registers → Cache → RAM → Disk (fast to slow)
- [ ] One-to-Many: Foreign key in "Many" side
- [ ] SQLAlchemy Class = Table, Object = Row

### Week 8 ✅
- [ ] SSR (Flask templates), Static site (HTML files), CSR (JavaScript)
- [ ] Bandwidth formula: Pages/s = Bandwidth / Image Size
- [ ] HTML = structure, CSS = style, JS = interaction

---

## 🎯 **LAST-MINUTE TIPS (1 Hour Before Quiz)**

1. **Focus on Flask routes** – Most tricky questions involve URL patterns
2. **Remember HTTP methods** – 80% of REST questions use these
3. **Relationship rules** – Foreign key always on "Many" side
4. **Bandwidth math** – Simple division; watch units (bits vs bytes)
5. **Don't overthink MVC** – Model does data, View shows, Controller connects

**Good luck! 🚀**

---

## 📞 **Key Resources to Review**

- Previous Year Questions: quizpractice.space
- YouTube: MAD 1 Revision Session - Quiz 2
- GitHub: Look for MAD 1 solutions repo
- Discord/Telegram: Join IITM BS community channels

---

*Last Updated: November 2025*  
*Made Easy for Quick Learning* ✨
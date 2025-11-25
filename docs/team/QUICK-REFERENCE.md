# 📋 Quick Reference Card - FBLA Tracker

## Project Structure
```
FBLA-Membership-Tracker/
├── app.py              ← YOUR MAIN FILE (create this!)
├── templates/          ← HTML files go here
│   ├── base.html      ← Base template with Bootstrap
│   ├── login.html     ← Login page
│   └── ...            ← Other pages
├── static/            ← CSS, JS, images
│   └── qr/           ← QR code images will go here
├── database.db        ← Auto-created when you run app
└── requirements.txt   ← Python packages (already created)
```

---

## 🔥 Most Important Code Patterns

### 1. Database Model Template
```python
class YourModel(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    field_name = db.Column(db.String(100), nullable=False)
    created_at = db.Column(db.DateTime, default=datetime.utcnow)
```

### 2. Route Template
```python
@app.route('/your-route')
def your_function():
    # Check if logged in
    if 'user_id' not in session:
        return redirect('/login')
    # Your code here
    return render_template('your-template.html')
```

### 3. Form Processing Template
```python
@app.route('/your-form', methods=['GET', 'POST'])
def your_form():
    if request.method == 'POST':
        # Get form data
        data = request.form['field_name']
        # Process it
        # Save to database
        db.session.add(something)
        db.session.commit()
        return redirect('/success')
    return render_template('form.html')
```

### 4. HTML Template Structure
```html
{% extends "base.html" %}
{% block content %}
    <div class="container">
        <h1>Your Page Title</h1>
        <!-- Your content here -->
    </div>
{% endblock %}
```

---

## 📊 Database Tables You Need

```sql
users
├── id (Integer, Primary Key)
├── username (String, Unique)
├── password_hash (String)
└── force_password_change (Boolean, Default: False)

members
├── id (Integer, Primary Key)
├── name (String)
├── email (String)
├── student_id (String)
├── grade (Integer)
└── member_type (String)

events
├── id (Integer, Primary Key)
├── name (String)
├── date (Date)
├── time (Time)
├── location (String)
└── qr_code_path (String)

attendance
├── id (Integer, Primary Key)
├── member_id (Integer, Foreign Key)
├── event_id (Integer, Foreign Key)
├── checkin_time (DateTime)
├── rating (Integer)
└── comment (Text)
```

---

## 🎨 Bootstrap Classes Cheat Sheet

### Forms
```html
<form>
  <div class="mb-3">
    <label class="form-label">Label</label>
    <input type="text" class="form-control">
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

### Tables
```html
<table class="table table-striped">
  <thead>
    <tr>
      <th>Column 1</th>
      <th>Column 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Data 1</td>
      <td>Data 2</td>
    </tr>
  </tbody>
</table>
```

### Navigation
```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container">
    <a class="navbar-brand" href="/">FBLA Tracker</a>
    <!-- Nav items here -->
  </div>
</nav>
```

### Alerts
```html
<div class="alert alert-success" role="alert">
  Success message!
</div>
```

---

## 🔐 Session Management

### Login
```python
session['user_id'] = user.id
session['username'] = user.username
```

### Check if Logged In
```python
if 'user_id' not in session:
    flash('Please login first')
    return redirect('/login')
```

### Logout
```python
session.clear()
return redirect('/')
```

---

## 🎯 QR Code Generation

```python
import qrcode

def generate_qr(event_id):
    # Create QR instance
    qr = qrcode.QRCode(
        version=1,
        box_size=10,
        border=5,
    )

    # Add data (the check-in URL)
    url = f"http://localhost:5000/checkin/{event_id}"
    qr.add_data(url)
    qr.make(fit=True)

    # Create image
    img = qr.make_image(fill_color="black", back_color="white")

    # Save it
    img.save(f"static/qr/event_{event_id}.png")

    return f"qr/event_{event_id}.png"
```

---

## 🚨 Common Errors & Fixes

| Error | Fix |
|-------|-----|
| `NameError: name 'db' is not defined` | Make sure you have `db = SQLAlchemy(app)` |
| `RuntimeError: Working outside of application context` | Wrap database operations in `with app.app_context():` |
| `jinja2.exceptions.TemplateNotFound` | Check template is in templates/ folder |
| `sqlalchemy.exc.OperationalError` | Database doesn't exist, run `db.create_all()` |
| `KeyError: 'user_id'` | User not logged in, check session |

---

## 🏃 Quick Commands

```bash
# Run app
python app.py

# See all routes
flask routes

# Python shell with app context
flask shell

# Reset database (nuclear option)
rm database.db
python app.py  # Will recreate it
```

---

## 💬 Flask Flash Messages

```python
# In Python
from flask import flash
flash('Your message here', 'success')  # or 'danger', 'warning', 'info'

# In HTML template
{% with messages = get_flashed_messages(with_categories=true) %}
  {% if messages %}
    {% for category, message in messages %}
      <div class="alert alert-{{ category }}">{{ message }}</div>
    {% endfor %}
  {% endif %}
{% endwith %}
```

---

## 📝 Git Workflow

```bash
# See what changed
git status

# Add everything
git add .

# Commit with message
git commit -m "Add login functionality"

# Push to your branch
git push origin your-branch-name

# Pull latest changes
git pull origin main
```

---

## 🎉 Progress Checklist

### Day 1
- [ ] app.py runs without errors
- [ ] Can see a page at localhost:5000
- [ ] Database models created
- [ ] At least one route working

### Day 2
- [ ] Login page works
- [ ] Can log in and see dashboard
- [ ] Session management working
- [ ] Can add a member

### Day 3
- [ ] All CRUD operations for members
- [ ] Event creation working
- [ ] QR codes generating
- [ ] Basic styling with Bootstrap

---

**Remember:** Don't copy-paste everything! Type it out to learn better. Google is your friend. Ask teammates when stuck!

*Happy Coding! 🚀*
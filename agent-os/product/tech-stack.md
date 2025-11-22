# Tech Stack (Simplified for Students)

## What We're Actually Using 🛠️

### Core Stack (Just 3 Things!)
1. **Flask** - Python web framework (easy to learn)
2. **SQLite** - Database (just a file, no server needed)
3. **Bootstrap** - CSS framework (instant pretty pages)

That's it! Everything else is optional.

---

## Required Software

### Must Install:
```bash
# Python (you probably have it)
python --version  # Need 3.7 or higher

# Pip (comes with Python)
pip --version

# That's all!
```

### Python Packages:
```bash
pip install flask           # Web framework
pip install sqlalchemy      # Database ORM
pip install qrcode[pil]     # QR code generation
```

---

## File Structure (Keep It Simple)

```
fbla-tracker/
├── app.py              # Everything can go here initially!
├── templates/          # HTML files
├── static/             # CSS, JS, images
└── database.db         # Your database (auto-created)
```

No complex folders needed!

---

## Development Approach

### Start Simple:
1. **One file is OK** - Put everything in app.py at first
2. **Copy-paste works** - Use examples from tutorials
3. **Test manually** - Click around, does it work?
4. **Refactor later** - Split into files when it gets messy

### What You DON'T Need:
❌ Docker
❌ Redis
❌ Nginx
❌ PostgreSQL
❌ React/Vue
❌ Webpack
❌ CI/CD
❌ Microservices
❌ Unit tests
❌ AWS

---

## Quick Reference

### Backend (Python/Flask):
```python
from flask import Flask, render_template
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///database.db'
db = SQLAlchemy(app)

# That's your whole setup!
```

### Frontend (HTML/Bootstrap):
```html
<!DOCTYPE html>
<html>
<head>
    <!-- Bootstrap from CDN - no download needed! -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <!-- Your content with Bootstrap classes -->
    <div class="container">
        <h1 class="text-center">FBLA Tracker</h1>
    </div>
</body>
</html>
```

### Database (SQLite):
```python
# Define a table
class Member(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100))
    email = db.Column(db.String(100))

# Create tables
db.create_all()

# That's it!
```

---

## Optional Additions (If You Want)

### Nice to Have:
- **werkzeug** - Password hashing (comes with Flask)
- **pandas** - CSV export (or just use Python's csv module)
- **python-dotenv** - Environment variables

### Future Maybes:
- Email sending (Flask-Mail)
- Google Calendar (google-api-python-client)
- Charts (Chart.js via CDN)

---

## Deployment (When Ready)

### Easiest Options:
1. **Local Machine**
   ```bash
   python app.py
   # Share your IP with E-Board
   ```

2. **PythonAnywhere** (Free)
   - Upload files
   - Click reload
   - Done!

3. **Heroku** (If free tier exists)
   - Add Procfile
   - Git push
   - Works!

---

## Learning Resources

### Start Here:
1. [Flask in 10 Minutes](https://flask.palletsprojects.com/quickstart/)
2. [Bootstrap Examples](https://getbootstrap.com/docs/5.0/examples/)
3. [SQLAlchemy Basics](https://flask-sqlalchemy.palletsprojects.com/quickstart/)

### When You Need Help:
- Google: "Flask how to [your task]"
- ChatGPT: "Write a Flask route that..."
- YouTube: "Flask tutorial beginner"

---

## Common Patterns

### Every Flask App Needs:
```python
# 1. Import stuff
from flask import Flask, render_template, request, redirect

# 2. Create app
app = Flask(__name__)

# 3. Routes (URLs)
@app.route('/')
def home():
    return render_template('index.html')

# 4. Run it
if __name__ == '__main__':
    app.run(debug=True)
```

### Every Database Operation:
```python
# Add something
new_thing = Model(field=value)
db.session.add(new_thing)
db.session.commit()

# Get something
things = Model.query.all()
thing = Model.query.get(id)

# Update something
thing.field = new_value
db.session.commit()

# Delete something
db.session.delete(thing)
db.session.commit()
```

---

## Remember

**You only need:**
- Flask
- SQLite
- Bootstrap

Everything else is optional. Start simple, add complexity only when needed.

**Goal:** Get something working in Week 1, improve it in Weeks 2-3.

---

*Last updated for student developers who just want to build something that works!*
# 🚀 FBLA Membership Tracker - Team Setup Guide

Welcome team! This guide will help you set up the project on your machine.

---

## Prerequisites

Before starting, you need to install Python, pip, and Git. Follow the instructions for your operating system below.

---

## Step 0: Installing Python & Required Tools

### 🪟 Windows

1. **Download Python:**
   - Go to [python.org](https://www.python.org/downloads/)
   - Download Python 3.10 or newer
   - Run the installer
   - ⚠️ **IMPORTANT:** Check "Add Python to PATH" during installation!

2. **Verify Installation:**
   ```bash
   python --version
   pip --version
   ```

3. **Install Git:**
   - Download from [git-scm.com](https://git-scm.com/download/win)
   - Run the installer with default options

### 🍎 Mac

1. **Install Homebrew** (if not already installed):
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Python:**
   ```bash
   brew install python
   ```

3. **Install Git:**
   ```bash
   brew install git
   ```

4. **Verify Installation:**
   ```bash
   python3 --version
   pip3 --version
   git --version
   ```

### 🐧 Linux (Ubuntu/Debian/WSL)

1. **Update package manager:**
   ```bash
   sudo apt update
   ```

2. **Install Python and required packages:**
   ```bash
   sudo apt install python3 python3-pip python3-venv -y
   ```
   
   > ⚠️ **Important:** The `python3-venv` package is required to create virtual environments!

3. **Install Git:**
   ```bash
   sudo apt install git -y
   ```

4. **Verify Installation:**
   ```bash
   python3 --version
   pip3 --version
   git --version
   ```

### ✅ Verification Checklist

Make sure these commands work before continuing:
- [ ] `python --version` or `python3 --version` shows 3.7+
- [ ] `pip --version` or `pip3 --version` works
- [ ] `git --version` shows git is installed

---

## Step 1: Clone the Repository

```bash
git clone https://github.com/Kaythecreator/FBLA-Membership-Tracker.git
cd FBLA-Membership-Tracker
```

---

## Step 2: Set Up Virtual Environment

A virtual environment keeps your project dependencies isolated from other Python projects.

### 🪟 Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### 🍎 Mac

```bash
python3 -m venv venv
source venv/bin/activate
```

### 🐧 Linux (Ubuntu/Debian/WSL)

```bash
python3 -m venv venv
source venv/bin/activate
```

**If you get an error like "ensurepip is not available":**
```bash
# Install the venv package first
sudo apt install python3.12-venv

# Then create the virtual environment
python3 -m venv venv
source venv/bin/activate
```

### ✅ Success Check

You should see `(venv)` at the beginning of your terminal prompt:
```
(venv) user@computer:~/FBLA-Membership-Tracker$
```

### 💡 To Deactivate Later

When you're done working on the project:
```bash
deactivate
```

---

## Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

This installs:
- Flask (web framework)
- SQLAlchemy (database)
- qrcode (QR generation)
- And a few other helpers

---

## Step 4: Create Your First File - app.py

Create a file called `app.py` in the root directory with this starter code:

```python
from flask import Flask, render_template, request, redirect, session, url_for, flash
from flask_sqlalchemy import SQLAlchemy
from werkzeug.security import generate_password_hash, check_password_hash
from datetime import datetime
import qrcode
import os

# TODO: Your code starts here!
# Follow the tasks in your assigned section

app = Flask(__name__)

# Configuration
app.config['SECRET_KEY'] = 'dev-secret-key-change-this'  # TODO: Change this!
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///database.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

# Initialize database
db = SQLAlchemy(app)

# TODO: Add your models here (check models.py task)

# TODO: Add your routes here (check routes section)

if __name__ == '__main__':
    with app.app_context():
        db.create_all()  # Creates database tables
    app.run(debug=True)
```

---

## Step 5: Create Empty Template Files

Create these empty HTML files in the `templates/` folder:

1. `templates/base.html` - Base template with Bootstrap
2. `templates/login.html` - E-Board login page
3. `templates/dashboard.html` - Admin dashboard
4. `templates/members.html` - Member list
5. `templates/add_member.html` - Add member form
6. `templates/events.html` - Event list
7. `templates/add_event.html` - Create event form
8. `templates/checkin.html` - QR check-in form
9. `templates/admin_users.html` - Password reset page
10. `templates/change_password.html` - Change password form

Just create them empty for now - you'll fill them in!

---

## Step 6: Test Your Setup

Run this command:
```bash
python app.py
```

You should see:
```
* Running on http://127.0.0.1:5000
* Debug mode: on
```

Open http://localhost:5000 in your browser. You'll see an error (that's OK! You haven't added routes yet).

---

## 📝 Task Assignments

### Person A - Backend Lead:
1. Create the database models in app.py:
   - User model (id, username, password_hash, force_password_change)
   - Member model (id, name, email, student_id, grade, member_type)
   - Event model (id, name, date, time, location, qr_code_path)
   - Attendance model (id, member_id, event_id, checkin_time, rating, comment)

2. Create these routes:
   - `/` - Home page
   - `/login` - Login page (GET and POST)
   - `/logout` - Logout functionality
   - `/dashboard` - Admin dashboard (login required)

### Person B - Frontend Lead:
1. Create `base.html` with Bootstrap CDN:
   ```html
   <!-- Hint: Start with this Bootstrap CDN link -->
   <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
   ```

2. Design the login form in `login.html`
3. Create navigation bar in `base.html`
4. Style all forms with Bootstrap classes

### Person C - Features Developer:
1. Implement member management:
   - `/members` - List all members
   - `/add-member` - Add new member
   - `/edit-member/<id>` - Edit member
   - `/delete-member/<id>` - Delete member

2. Start on QR code generation:
   - Research the qrcode library
   - Create a function to generate QR codes
   - Save QR images to static folder

---

## 🎯 Day 1 Goals

By end of Day 1, you should have:
- [ ] app.py running without errors
- [ ] Database models created
- [ ] Login page displaying
- [ ] One person successfully logged in
- [ ] Navigation bar showing

---

## 💡 Helpful Code Snippets

### Creating a Model (example):
```python
class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    # TODO: Add more fields
```

### Creating a Route (example):
```python
@app.route('/')
def home():
    return render_template('base.html')
```

### Checking if Logged In:
```python
if 'user_id' not in session:
    return redirect('/login')
```

### Generating Password Hash:
```python
hashed = generate_password_hash('password')
```

---

## 🐛 Common Issues & Fixes

| Problem | Solution |
|---------|----------|
| "externally-managed-environment" | You need to use a virtual environment. See Step 2. |
| "ensurepip is not available" | Linux/WSL: Run `sudo apt install python3-venv` |
| "Module not found" | Make sure venv is activated (you should see `(venv)` in terminal) |
| "Template not found" | Check file is in templates/ folder |
| "Database locked" | Stop and restart app |
| "Port already in use" | Another app is running, stop it with Ctrl+C |
| "python: command not found" | Use `python3` instead of `python` on Mac/Linux |
| venv activation not working | Windows: use `venv\Scripts\activate`, Mac/Linux: use `source venv/bin/activate` |

---

## 📚 Resources

- [Flask Quickstart](https://flask.palletsprojects.com/quickstart/)
- [Flask-SQLAlchemy Models](https://flask-sqlalchemy.palletsprojects.com/models/)
- [Bootstrap Forms](https://getbootstrap.com/docs/5.1/forms/overview/)
- [Flask Sessions](https://flask.palletsprojects.com/quickstart/#sessions)

---

## 🤝 Working as a Team

1. **Create branches for your work:**
   ```bash
   git checkout -b feature/login-system
   ```

2. **Commit often:**
   ```bash
   git add .
   git commit -m "Add login route"
   ```

3. **Push your branch:**
   ```bash
   git push origin feature/login-system
   ```

4. **Communicate!** Use Discord/Slack to coordinate

---

## ⚡ Quick Commands

```bash
# Activate virtual environment
source venv/bin/activate  # Mac/Linux
venv\Scripts\activate     # Windows

# Run the app
python app.py

# Install a new package
pip install package-name
pip freeze > requirements.txt  # Update requirements

# Git workflow
git status
git add .
git commit -m "message"
git push
```

---

## 🎉 You're Ready!

Start with app.py and build from there. Remember:
- Working code > Perfect code
- Ask for help when stuck
- Google/ChatGPT are your friends
- Commit code even if it's messy
- Have fun learning!

**First person to get login working wins! 🏆**

---

*Questions? Check the team chat or ask your team lead!*
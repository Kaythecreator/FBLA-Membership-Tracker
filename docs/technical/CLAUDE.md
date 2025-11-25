# CLAUDE.md

This file helps Claude Code (AI assistant) understand your project when providing coding help.

## Project Overview

**FBLA Membership Tracker** - A simple web app for a college FBLA chapter (~60 members) to track attendance using QR codes.

## Quick Context

- **Team Size**: 3-5 student developers
- **Timeline**: 3 weeks part-time development
- **Focus**: Learning experience + working solution
- **Users**: ~60 chapter members, 5-6 E-Board admins

## Tech Stack (Simple!)

```python
# Backend
Flask           # Web framework
SQLite          # Database (just a file)
SQLAlchemy      # ORM for database

# Frontend
HTML/CSS        # Basic web pages
Bootstrap 5     # Quick styling
Vanilla JS      # Simple interactions

# Key Libraries
qrcode          # Generate QR codes
werkzeug        # Password hashing
csv/pandas      # Handle CSV files
```

## Project Structure

```
fbla-tracker/
├── app.py              # Main Flask application
├── models.py           # Database models
├── routes.py           # URL routes
├── templates/          # HTML templates
│   ├── login.html
│   ├── dashboard.html
│   ├── checkin.html
│   └── members.html
├── static/             # CSS, JS, images
├── database.db         # SQLite database file
└── requirements.txt    # Python packages
```

## Core Features (MVP)

1. **E-Board Admin Panel**
   - Simple login (username/password)
   - Add/edit/delete members
   - Create events with QR codes
   - View attendance reports

2. **QR Check-in System**
   - Generate unique QR per event
   - Simple form when scanned
   - Record attendance with timestamp

3. **Basic Reports**
   - Who attended what event
   - Export to CSV
   - Simple member status

## Database Tables (Keep Simple)

```sql
-- Just 4 tables!
users (id, username, password_hash)
members (id, name, email, student_id, grade, member_type)
events (id, name, date, time, location, qr_code)
attendance (id, member_id, event_id, checkin_time, rating, comment)
```

## Development Guidelines

### For AI Assistance:
- **Prioritize working code** over perfect code
- **Use simple solutions** - no overengineering
- **SQLite is fine** - no need for PostgreSQL
- **Sessions are OK** - no complex JWT needed
- **Bootstrap is enough** - no custom CSS required

### Common Tasks:
```python
# Start the app
python app.py

# Create a new route
@app.route('/route-name')
def function_name():
    return render_template('template.html')

# Add to database
new_member = Member(name="John", email="john@email.com")
db.session.add(new_member)
db.session.commit()
```

## What NOT to Worry About

❌ Complex authentication (basic login is fine)
❌ Perfect security (it's 60 students, not a bank)
❌ Unit tests (manual testing is OK)
❌ Scalability (60 users max)
❌ Professional deployment (local/free hosting is fine)

## Quick Fixes When Stuck

### Database Issues:
```python
# Just delete and recreate if corrupted
import os
os.remove('database.db')
db.create_all()
```

### Common Errors:
- **Import Error**: Run `pip install -r requirements.txt`
- **Database Locked**: Restart the Flask app
- **Template Not Found**: Check templates/ folder
- **Static Files Not Loading**: Check static/ folder path

## Useful Code Snippets

### Generate QR Code:
```python
import qrcode
qr = qrcode.make(f"http://localhost:5000/checkin/{event_id}")
qr.save(f"static/qr/event_{event_id}.png")
```

### Check Login:
```python
from flask import session
if 'user_id' not in session:
    return redirect('/login')
```

### Export to CSV:
```python
import csv
with open('attendance.csv', 'w') as file:
    writer = csv.writer(file)
    writer.writerow(['Name', 'Event', 'Time'])
    # Write data rows
```

## Testing Checklist

Before saying "it works":
- [ ] Can E-Board log in?
- [ ] Can add a new member?
- [ ] Can create an event?
- [ ] Does QR code generate?
- [ ] Can members check in?
- [ ] Can export attendance?

## Remember

This is a **learning project** for **students**. The goal is to:
1. Build something that works
2. Learn web development
3. Replace paper sign-ins
4. Have fun coding!

**Working > Perfect** | **Simple > Complex** | **Done > Ideal**
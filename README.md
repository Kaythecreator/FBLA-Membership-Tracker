# FBLA Membership Tracker 📋

A simple web app for tracking attendance at FBLA chapter meetings using QR codes.

**Built by students, for students!** 🎓

## What Is This?

Instead of passing around paper sign-in sheets at FBLA meetings, members scan a QR code with their phone and check in digitally. E-Board members can then see who attended and export the data.

**Perfect for**: College FBLA chapters with 50-100 members

## Features ✨

### For E-Board Members:
- 🔐 Simple login system
- ➕ Add/edit/remove members
- 📅 Create events with QR codes
- 📊 View attendance reports for events and specific members
- 💾 Export to CSV/Excel

### For Regular Members:
- 📱 Scan QR code at meetings
- ✅ Quick check-in form
- 🎉 That's it! Super simple

## Tech Stack (Beginner-Friendly!)

```python
Backend:  Flask (Python web framework)
Database: SQLite (just a file, no setup!)
Frontend: HTML + Bootstrap (looks good instantly)
```

## Quick Start 🚀

### 1. Clone the Project
```bash
git clone [your-repo-url]
cd FBLA-Membership-Tracker
```

### 2. Set Up Virtual Environment
```bash
# Create virtual environment
python -m venv venv

# Activate it (Windows)
venv\Scripts\activate

# Activate it (Mac/Linux)
source venv/bin/activate
```

### 3. Install Python Packages
```bash
pip install -r requirements.txt
```

### 4. Run the App
```bash
python app.py
# or
flask run
```

Visit `http://localhost:5000` in your browser!

That's it! You're running! 🎉

## Project Structure 📁

```
FBLA-Membership-Tracker/
│
├── 📂 src/                      ← YOUR CODE GOES HERE
│   ├── app.py                   ← Main application (you create this!)
│   ├── models.py                ← Database models
│   ├── qr_generator.py          ← QR code generation module
│   ├── templates/               ← HTML templates
│   │   ├── base.html           ← Base template
│   │   ├── login.html          ← Login page
│   │   ├── dashboard.html      ← Admin dashboard
│   │   ├── members.html        ← Member list
│   │   ├── events.html         ← Event list
│   │   ├── checkin.html        ← Check-in form
│   │   └── ...                 ← Other templates
│   └── static/                  ← CSS, JS, images
│       └── qr_codes/           ← Generated QR code images
│
├── 📂 docs/                     ← DOCUMENTATION
│   ├── team/                   ← For developers
│   │   ├── SETUP-GUIDE.md     ← ⭐ START HERE
│   │   ├── QUICK-REFERENCE.md ← Code patterns
│   │   └── WEEK1-PARALLEL-TASKS.md ← Week 1 assignments
│   ├── project/                ← Project planning
│   │   ├── PRD.md             ← Requirements
│   │   ├── WBS.md             ← Task breakdown with assignments
│   │   └── WBS-Visual.md      ← Visual timeline
│   └── technical/              ← Technical details
│       └── agent-os/           ← Development standards
│
├── 📄 app.py                    ← Flask application
├── 📄 requirements.txt          ← Python packages
├── 📄 .gitignore               ← Git ignore rules
└── 📄 database.db              ← SQLite database (auto-created)
```

## For Development 👩‍💻👨‍💻

### Getting Started:
1. **First Time?** Read `docs/team/SETUP-GUIDE.md` ⭐
2. **Need Help?** Check `docs/team/QUICK-REFERENCE.md`
3. **Week 1 Tasks** in `docs/team/WEEK1-PARALLEL-TASKS.md`
4. **Write Code** in `src/` folder

**NOTE:** Do not worry about any other folders other than project, team, and src.

### Common Tasks:

**Add a new page:**
```python
@app.route('/new-page')
def new_page():
    return render_template('new-page.html')
```

**Add to database:**
```python
member = Member(name="John", email="john@college.edu")
db.session.add(member)
db.session.commit()
```

**Generate QR code:**
```python
import qrcode
qr = qrcode.make("https://your-checkin-url")
qr.save("static/qr/event-qr.png")  # Save in static/qr/ folder
```

### Tips for Success:
- ✅ Google errors - someone else had the same problem
- ✅ Use ChatGPT/Claude for help
- ✅ Test by actually using it
- ✅ Commit code even if it's messy
- ✅ Ask teammates when stuck

### It's OK To:
- Copy code from Stack Overflow
- Use AI to write functions
- Have some bugs
- Not understand everything
- Learn as you go!

## Development Workflow 🔄

### Week 1: Foundation (Nov 21-28)
**Three Parallel Streams:**
- **Database Team**: Design schema, create models, test with sample data
- **HTML Team**: Build all templates with Bootstrap, make mobile-friendly
- **QR Module**: Create standalone QR generation system

### Week 2: Core Features (Nov 29-Dec 5)
- [ ] Connect HTML forms to database
- [ ] Link QR codes to check-in routes
- [ ] Event creation and management
- [ ] Check-in processing
- [ ] Test complete flow

### Week 3: Polish & Deploy (Dec 6-12)
- [ ] Attendance reports
- [ ] CSV import/export (60 members)
- [ ] Fix all bugs
- [ ] E-Board testing
- [ ] Deploy to production

## Testing Checklist ✔️

Before showing to E-Board:
- [ ] Can log in as admin?
- [ ] Can add a member?
- [ ] Can create an event?
- [ ] QR code generates?
- [ ] Check-in works?
- [ ] Can export data?

## Common Issues & Fixes 🔧

| Problem | Solution |
|---------|----------|
| "Module not found" | Run `pip install [module-name]` |
| "Database locked" | Restart the app |
| "Template not found" | Check src/templates/ folder |
| QR code won't scan | Make it bigger, better lighting |
| Can't log in | Check username/password in database |

## Contributing 🤝

### For Team Members:
1. Pick a task from the TODO list
2. Push to your feature branch
3. Make changes
4. Test it works
5. Push your branch
6. Tell the team!

### Code Style:
- Clear > Clever
- Working > Perfect
- Comments > Documentation
- Simple > Complex

## Resources 📚

### Learning:
- [Flask Quickstart](https://flask.palletsprojects.com/quickstart/)
- [Bootstrap Components](https://getbootstrap.com/docs/)
- [SQLite Tutorial](https://www.sqlitetutorial.net/)
- [W3Schools HTML/CSS](https://www.w3schools.com/)

### When Stuck:
- Google the error
- Ask ChatGPT/Claude
- Stack Overflow
- Ask teammates!

## Team 👥

Built by FBLA at UMD student developers:
- Kris
- Souptik
- Riya
- Alan
- Aparna

## License 📄

This is a student project - feel free to use/modify for your own FBLA chapter!

---

**Remember**: This is a learning project. It doesn't need to be perfect, it just needs to work! Have fun and learn something new! 🚀

**Questions?** Ask in the team chat or create an issue on GitHub!
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
- 📊 View attendance reports
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
cd fbla-tracker
```

### 2. Install Python Packages
```bash
pip install flask sqlalchemy qrcode[pil]
```

### 3. Run the App
```bash
python app.py
```

### 4. Open in Browser
```
http://localhost:5000
```

That's it! You're running! 🎉

## Project Structure 📁

```
fbla-tracker/
├── app.py              # Main application
├── models.py           # Database tables
├── routes.py           # URL endpoints
├── templates/          # HTML pages
│   ├── login.html
│   ├── dashboard.html
│   └── checkin.html
├── static/             # CSS, images
├── database.db         # SQLite database
└── requirements.txt    # Python packages
```

## For Student Developers 👩‍💻👨‍💻

### Getting Started:
1. **No experience?** Start with templates/ folder (HTML)
2. **Know some Python?** Look at routes.py
3. **Database curious?** Check out models.py

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
qr.save("event-qr.png")
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

### Week 1: Basics
- [ ] Set up Flask
- [ ] Create database
- [ ] Build login page
- [ ] Add member management

### Week 2: Core Features
- [ ] Event creation
- [ ] QR code generation
- [ ] Check-in form
- [ ] Link attendance

### Week 3: Polish
- [ ] CSV import/export
- [ ] Calculate member status
- [ ] Fix bugs
- [ ] Test with real data

## Testing Checklist ✔️

Before showing to E-Board:
- [ ] Can log in as admin?
- [ ] Can add a member?
- [ ] Can create an event?
- [ ] QR code generates?
- [ ] Check-in works?
- [ ] Can export data?

## Deployment Options 🌐

### Easiest to Hardest:
1. **Local** - Run on laptop during meetings
2. **PythonAnywhere** - Free hosting, easy setup
3. **Heroku** - Free tier (if available)
4. **School Server** - Ask IT department

## Common Issues & Fixes 🔧

| Problem | Solution |
|---------|----------|
| "Module not found" | Run `pip install [module-name]` |
| "Database locked" | Restart the app |
| "Template not found" | Check templates/ folder |
| QR code won't scan | Make it bigger, better lighting |
| Can't log in | Check username/password in database |

## FAQ 🤔

**Q: Do members need accounts?**
A: No! Only E-Board members log in. Regular members just scan and submit the form.

**Q: How secure is this?**
A: Good enough for a student club! We hash passwords and validate inputs.

**Q: Can it handle 500 members?**
A: Yes, but it's designed for ~60. Works fine up to a few hundred.

**Q: Do we need a server?**
A: Nope! Can run on any computer with Python.

**Q: Is this production-ready?**
A: It works! That's what matters for a student project.

## Contributing 🤝

### For Team Members:
1. Pick a task from the TODO list
2. Create a branch: `git checkout -b your-feature`
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

Built by [Your FBLA Chapter Name] student developers:
- [Add your names here!]

## License 📄

This is a student project - feel free to use/modify for your own FBLA chapter!

---

**Remember**: This is a learning project. It doesn't need to be perfect, it just needs to work! Have fun and learn something new! 🚀

**Questions?** Ask in the team chat or create an issue on GitHub!

---

*"Working software > Comprehensive documentation"* - Some wise programmer

*"Done is better than perfect"* - Every student ever
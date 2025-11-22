# Product Requirements Document (PRD) - Simplified
# FBLA Membership Tracker - Student Project

## Project Overview
- **What**: Simple web app for tracking ~60 FBLA chapter members
- **Who**: Built by 3-5 student developers as a learning project
- **Timeline**: 3 weeks of part-time development
- **Goal**: Replace paper sign-ins with a working digital solution

---

## Core Features (MVP - Must Have)

### 1. E-Board Login
- Simple username/password for 5-6 E-Board members
- Use Flask sessions (no complex JWT needed)
- One admin level (all E-Board members equal)

### 2. Member Management
- Add members one by one through a form
- Upload members via CSV file
- View all members in a table
- Edit/delete members
- Track: Name, Email, Student ID, Grade, Member Type

### 3. Event & QR Check-in
- Create events with date/time/location
- Generate QR code for each event
- Simple check-in form when QR is scanned:
  - Name
  - Email
  - Quick feedback (1-10 rating)
  - One comment box
- Prevent duplicate check-ins

### 4. Basic Reports
- See who attended each event
- Export attendance to CSV
- Simple member status (attended enough meetings? yes/no)

---

## Technical Stack (Keep It Simple!)

### Backend
- **Flask** - Easy Python web framework
- **SQLite** - Database in a single file
- **SQLAlchemy** - Makes database queries easier

### Frontend
- **HTML/CSS** - Basic web pages
- **Bootstrap 5** - Quick styling
- **Jinja2** - Flask's template engine
- **Vanilla JavaScript** - For simple interactions

### Libraries
- **qrcode** - Generate QR codes
- **pandas** or just **csv** - Handle CSV files
- **werkzeug** - Password hashing

---

## Database Design (Simple!)

### Tables Needed:
1. **users** - E-Board login accounts (5-6 rows)
2. **members** - All FBLA members (~60 rows)
3. **events** - Meetings and activities
4. **attendance** - Who checked into what event

### Skip For Now:
- Complex relationships
- Optimization indexes
- Migration tracking
- Audit logs

---

## Week-by-Week Plan

### Week 1: Foundation
- [ ] Set up Flask project
- [ ] Create SQLite database
- [ ] Build E-Board login
- [ ] Add member management (add/view/edit)
- [ ] Basic Bootstrap styling

### Week 2: Core Features
- [ ] Create event management
- [ ] Generate QR codes
- [ ] Build check-in form
- [ ] Link attendance to database
- [ ] Test with sample data

### Week 3: Polish & Deploy
- [ ] Add CSV import/export
- [ ] Calculate basic member status
- [ ] Create simple reports page
- [ ] Fix bugs from testing
- [ ] Deploy locally or free hosting

---

## User Stories (Simple Version)

### E-Board Member:
1. I can log in with my username/password
2. I can add new members to the system
3. I can create events and get QR codes
4. I can see who attended each event
5. I can export data to Excel/CSV

### Regular Member:
1. I scan the QR code at meetings
2. I fill out a quick check-in form
3. I see "Thanks for checking in!"

---

## What We're NOT Building

### Skip These Features:
- ❌ Member login system (E-Board only)
- ❌ Email notifications
- ❌ Google Calendar sync
- ❌ Competition tracking
- ❌ Payment processing
- ❌ Mobile app
- ❌ Advanced analytics
- ❌ Perfect security

### Why Skip Them?
- Limited time (3 weeks)
- Small user base (60 people)
- Learning project focus
- Can add later if needed

---

## Definition of "Done"

A feature is complete when:
- [x] It works when you test it
- [x] Other team members can use it
- [x] It doesn't break other features
- [x] There's a basic comment explaining what it does

We're NOT requiring:
- Unit tests
- Perfect code
- Documentation
- Code reviews
- Performance optimization

---

## Security (Good Enough Approach)

### What We'll Do:
- Hash passwords (use werkzeug.security)
- Validate form inputs (no SQL injection)
- Check user is logged in for admin pages
- Use HTTPS if deploying online

### What We Won't Worry About:
- Complex authentication
- Rate limiting
- Audit logs
- Encryption
- Session management complexity

---

## Deployment Options

### Easiest First:
1. **Run locally** on someone's laptop during meetings
2. **Heroku free tier** (if still available)
3. **PythonAnywhere** free account
4. **Raspberry Pi** in the club room
5. **School server** (if IT allows)

### Don't Worry About:
- Docker containers
- CI/CD pipelines
- Load balancing
- Backup strategies
- Monitoring

---

## Success Metrics

### It's Successful If:
✅ E-Board can track attendance without paper
✅ Takes < 30 seconds to check in
✅ Can export data for reports
✅ Works for a full semester
✅ Team learned web development

### It's NOT a Failure If:
- Has some bugs
- UI isn't beautiful
- Code isn't perfect
- Missing advanced features
- Needs manual restarts sometimes

---

## Tips for Student Developers

### When Stuck:
1. Google the error message
2. Check Stack Overflow
3. Ask ChatGPT/Claude
4. Simplify the feature
5. Ask teammates

### Good Practices:
- Commit code daily (even if broken)
- Test by actually using it
- Keep features simple
- Focus on "working" over "perfect"
- Help each other learn

### It's OK To:
- Copy code from tutorials
- Use AI to help write code
- Hardcode some values
- Skip edge cases
- Have some technical debt

---

## Project Risks & Reality

### Realistic Risks:
- Team members busy with classes
- Someone drops the course
- Runs out of time
- Feature doesn't work as expected

### Mitigation:
- Keep features simple
- Build core features first
- Test early and often
- Have backup plans
- Celebrate small wins

---

## Final Notes

**Remember**: This is a learning project for a small club. Facebook started as a simple PHP app for one college. Your tracker just needs to work for YOUR chapter.

**Priority Order**:
1. Working > Perfect
2. Simple > Complex
3. Done > Ideal
4. Learned > Expert

**Have Fun!** This is about learning and building something useful together.

---

*Last Updated: November 2024*
*For: College FBLA Chapter (~60 members)*
*By: Student Development Team*
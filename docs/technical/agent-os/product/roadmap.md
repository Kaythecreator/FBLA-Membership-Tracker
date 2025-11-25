# Simplified Roadmap - 3 Week Sprint

## Goal: Working QR Check-in System for ~60 FBLA Members

---

## Week 1 (Nov 21-28): Get Something Working! 🚀

### Day 1-2: Basic Setup
- [ ] Install Flask and SQLite
- [ ] Create `app.py` with "Hello FBLA" page
- [ ] Set up database with 4 tables (users, members, events, attendance)
- [ ] Add Bootstrap CSS from CDN

### Day 3-4: E-Board Login
- [ ] Create login page (username/password)
- [ ] Use Flask sessions (no JWT complexity)
- [ ] Make a simple dashboard that says "Welcome E-Board!"

### Day 5-7: Member Management
- [ ] Add "Create Member" form
- [ ] Display members in a table
- [ ] Add edit/delete buttons
- [ ] Test with 5-10 fake members

**Week 1 Success:** Can log in and manage members ✅

---

## Week 2 (Nov 29-Dec 5): Core Features 📋

### Day 1-2: Event Creation
- [ ] Add "Create Event" form (name, date, time, location)
- [ ] Save events to database
- [ ] Display list of events

### Day 3-4: QR Code Magic
- [ ] Generate QR code for each event (use qrcode library)
- [ ] Display QR code on event page
- [ ] Save QR images to static folder

### Day 5-7: Check-in System
- [ ] Create check-in form (name, email, rating, comment)
- [ ] Link QR code to check-in URL
- [ ] Save attendance records
- [ ] Show "Thanks for checking in!" message

**Week 2 Success:** QR check-in actually works! ✅

---

## Week 3 (Dec 6-12): Make It Useful 🎯

### Day 1-2: Attendance Reports
- [ ] Show who attended each event
- [ ] Add attendance count to event list
- [ ] Create "Export to CSV" button

### Day 3-4: Bulk Features
- [ ] Add CSV import for members (upload 60 at once!)
- [ ] Test with real member data
- [ ] Add "Download All Attendance" feature

### Day 5-6: Polish & Fix
- [ ] Fix any bugs found during testing
- [ ] Make it mobile-friendly (Bootstrap helps!)
- [ ] Add simple member status (attended 50% of meetings?)

### Day 7: Demo Ready!
- [ ] Test complete workflow with E-Board
- [ ] Create simple instructions document
- [ ] Deploy locally or to free hosting

**Week 3 Success:** E-Board can actually use it! ✅

---

## Daily Schedule (Realistic for Students)

### Typical Day:
- **1-2 hours coding** (between classes)
- **30 min team sync** (Discord/text)
- **Test one feature** before bed

### Weekend Sprint:
- **3-4 hours** on Saturday
- **2-3 hours** on Sunday
- **Pizza break** mandatory! 🍕

---

## MVP Definition (What Actually Matters)

### Must Have (Week 1-2):
✅ E-Board can log in
✅ Can add members
✅ Can create events
✅ QR codes generate
✅ Members can check in

### Should Have (Week 3):
⭐ View attendance list
⭐ Export to CSV
⭐ Bulk member import

### Nice to Have (If Time):
🎁 Calculate attendance percentage
🎁 Pretty dashboard
🎁 Email confirmations

### Skip Completely:
❌ Complex authentication
❌ Google Calendar sync
❌ Competition tracking
❌ Mobile app
❌ Unit tests

---

## Team Task Distribution

### Person A - "Backend Lead"
- Set up Flask and database
- Create models and routes
- Handle QR generation

### Person B - "Frontend Lead"
- Design forms with Bootstrap
- Make pages mobile-friendly
- Create dashboard layout

### Person C - "Features Person"
- Build check-in flow
- Add CSV import/export
- Test everything

### Everyone:
- Test the app
- Find bugs
- Celebrate wins! 🎉

---

## Definition of Done

A feature is "done" when:
1. It works when you click on it
2. Other teammates can use it
3. Data saves to database
4. Doesn't break other features

NOT required:
- Unit tests
- Documentation
- Code review
- Performance optimization

---

## Risk Management (Student Edition)

### Likely Problems:
- **Someone gets busy with finals** → Others pick up tasks
- **Feature doesn't work** → Simplify or skip it
- **Running out of time** → Focus on core features only
- **Database gets corrupted** → Delete and recreate (it's SQLite!)

### Solutions:
- Keep features simple
- Test early and often
- Commit code daily
- Help each other

---

## Success Metrics

### It's Successful If:
✅ Replaces paper sign-ins
✅ E-Board happy
✅ Takes < 1 minute to check in
✅ Can export data
✅ Team learned something

### Bonus Points:
🌟 Other FBLA chapters want to use it
🌟 Looks good on resume
🌟 Team wants to add more features
🌟 No one failed their classes while building it

---

## Post-Launch (Optional)

### If You Have Time:
- Add email notifications
- Create better reports
- Make UI prettier
- Add charts/graphs

### Next Semester:
- Google Calendar integration
- Competition tracking
- Member portal
- Mobile app?

---

## Remember

**This is a learning project!** It's OK to:
- Google everything
- Use AI for help
- Copy from tutorials
- Have some bugs
- Not understand 100%

**Focus on:** Getting something working that the E-Board can actually use.

**Timeline:** 3 weeks is tight but doable if you keep it simple!

---

*Updated: November 2024*
*For: Student developers who want to build something real*
*Motto: "Ship it!"* 🚢
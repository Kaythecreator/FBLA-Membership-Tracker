# Week 1 Parallel Work Streams
## November 21-28

---

## Overview
Three teams working in parallel on independent components that don't require each other to complete. All streams can start immediately and work simultaneously.

---

## Stream 1: Database Team
### Team Members: Kris + Riya

### Tasks
- **Day 1-2**: Design database schema
  - Design users table (id, username, password_hash, created_at)
  - Design members table (id, name, email, student_id, grade, member_type)
  - Design events table (id, name, date, time, location, qr_code_path)
  - Design attendance table (id, member_id, event_id, checkin_time, rating, comment)
  - Create ERD diagram

- **Day 3-4**: Implementation
  - Create models.py file
  - Define all SQLAlchemy models
  - Set up database connection
  - Write database initialization script
  - Create relationships between tables

- **Day 5-7**: Testing & Sample Data
  - Test database creation
  - Create sample data insertion scripts
  - Write basic CRUD operations for each table
  - Test with 10-20 sample records
  - Document database setup instructions

### Deliverables by End of Week
- Working SQLite database
- models.py with all tables defined
- Sample data loaded
- Basic CRUD operations tested

---

## Stream 2: HTML/Frontend Team
### Team Members: Alan + Aparna

### Tasks
- **Day 1-2**: Setup & Base Template
  - Create templates/ folder structure
  - Create static/ folder for CSS/JS
  - Build base.html with navigation bar
  - Add Bootstrap CDN links
  - Design consistent header/footer

- **Day 3-4**: Core Pages
  - **login.html**: E-Board login form (username/password fields)
  - **dashboard.html**: Welcome page with placeholder stats
  - **members.html**: Member list table with dummy data
  - **add_member.html**: Form with all member fields

- **Day 5-7**: Event & Check-in Pages
  - **events.html**: Event list layout with dummy events
  - **event_form.html**: Create event form
  - **checkin.html**: Mobile-optimized check-in form
  - **success.html**: Check-in success message page
  - Test all pages on mobile devices

### Deliverables by End of Week
- 8-10 complete HTML templates
- Bootstrap styling applied
- Mobile-responsive design
- Navigation working between pages
- Forms ready (just need backend connection)

### Note for Aparna
This is great coding practice! You'll be writing HTML/CSS and learning web development fundamentals. Alan can help when you get stuck.

---

## Stream 3: QR Code Module
### Team Members: Souptik

### Tasks
- **Day 1-2**: QR Library Setup
  - Install qrcode library
  - Create qr_generator.py module
  - Write function to generate QR from text
  - Test basic QR generation

- **Day 3-4**: QR System Design
  - Create function to generate event-specific QRs
  - Design URL structure for check-ins (e.g., /checkin/event/123)
  - Build QR image saving functionality
  - Create unique filename generation

- **Day 5-7**: Testing & Integration Prep
  - Generate 5-10 test QR codes
  - Test scanning with multiple phones
  - Create QR display function
  - Build QR-to-URL mapping logic
  - Document QR system usage

### Deliverables by End of Week
- Standalone QR generation module
- QR codes scanning successfully
- URL structure defined
- Ready to integrate with routes in Week 2

---

## Why These Can Run in Parallel

### No Dependencies Between Streams
- **Database Team**: Doesn't need HTML or QR to build schemas
- **HTML Team**: Can use dummy data, doesn't need real database
- **QR Module**: Standalone Python module, needs neither HTML nor database

### Integration Points (Week 2)
- Souptik will connect HTML forms to database
- QR URLs will be linked to check-in routes
- Database will store QR code paths

---

## Daily Coordination

### Quick Sync (15 min daily)
- Each stream reports progress
- Identify any unexpected dependencies
- Adjust if someone needs help

### End of Week 1 Goal
✅ Database ready and tested
✅ All HTML pages complete and styled
✅ QR codes generating and scanning
✅ Ready for Week 2 integration

---

## If Someone Finishes Early

### Database Team Extras
- Add more sample data
- Create data validation functions
- Write more complex queries

### HTML Team Extras
- Improve mobile responsiveness
- Add loading spinners
- Create error message templates
- Add icons and polish UI

### QR Module Extras
- Add QR code styling/branding
- Create batch QR generation
- Add QR code size options

---

## Communication

### Slack/Discord Channels
- #database - Kris & Riya
- #frontend - Alan & Aparna
- #qr-system - Souptik
- #general - Everyone

### File Structure (No Conflicts)
```
FBLA-Membership-Tracker/
├── models.py           [Database Team]
├── templates/          [HTML Team]
│   ├── base.html
│   ├── login.html
│   ├── members.html
│   └── checkin.html
├── static/            [HTML Team]
│   ├── css/
│   └── js/
├── qr_generator.py    [QR Module]
└── qr_codes/          [QR Module]
```

---

## Success Metrics

### Stream 1 (Database)
- [ ] All 4 tables created
- [ ] Can insert/read/update/delete records
- [ ] Sample data loads without errors

### Stream 2 (HTML)
- [ ] All pages display properly
- [ ] Forms have all required fields
- [ ] Mobile-responsive design works
- [ ] Navigation between pages works

### Stream 3 (QR)
- [ ] QR codes generate from text
- [ ] QR codes scan on phones
- [ ] Images save to folder
- [ ] URL structure documented

---

*Remember: These are independent streams. Don't wait for other teams - just build your part!*
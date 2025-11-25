# Officer Dashboard Specifications
## FBLA Membership Tracker - E-Board Control Center

---

## Overview
The Officer Dashboard is the central hub where E-Board members manage all aspects of FBLA membership and event tracking. It should be simple, intuitive, and mobile-friendly.

---

## Dashboard Layout

### Header Section
```
[FBLA Logo] FBLA Membership Tracker        [Logged in as: {username}] [Logout]
```

### Navigation Bar
```
[Dashboard] [Members] [Events] [Reports] [Settings]
```

### Main Dashboard View
```
+------------------+------------------+------------------+
|  Total Members   |  Upcoming Events |  Recent Check-ins|
|       60         |        3         |       45         |
+------------------+------------------+------------------+

Quick Actions:
[+ Add Member] [+ Create Event] [View Reports] [Export Data]

Recent Activity Feed:
- John Doe checked into "General Meeting" (2 min ago)
- New member "Jane Smith" added (1 hour ago)
- Event "Competition Prep" created (3 hours ago)
```

---

## Feature Specifications

### 1. Member Management ➕

#### 1.1 Add Member
**Access:** Dashboard > Add Member button OR Members > Add New

**Form Fields:**
- Full Name* (required)
- Email* (required, validated)
- Student ID* (required, unique)
- Grade Level (dropdown: 9, 10, 11, 12)
- Member Type (dropdown: Regular, Officer, Alumni)
- Phone Number (optional)
- Join Date (auto-fills today)

**Actions:**
- Save & Add Another (stays on form)
- Save & View (goes to member list)
- Cancel (returns to previous page)

#### 1.2 Edit Member
**Access:** Members > Click on member name OR Edit icon

**Features:**
- Same fields as Add Member
- Shows "Last Modified" timestamp
- Confirmation prompt for changes
- Audit log of who made changes

#### 1.3 Remove Member
**Access:** Members > Delete icon (with confirmation)

**Safeguards:**
- "Are you sure?" modal
- Soft delete (mark as inactive, don't actually delete)
- Option to reactivate later
- Preserves attendance history

#### 1.4 Member List View
**Display:**
```
Search: [_______________] [Filter by Grade ▼] [Filter by Status ▼]

Name ↓         Email              Grade   Status    Attendance      Missed   Actions
-------------------------------------------------------------------------------------
John Doe      jdoe@umd.edu        11     Active    85% (17/20)     3       [Edit][View]
Jane Smith    jsmith@umd.edu      10     Active    90% (18/20)     2       [Edit][View]
Bob Wilson    bwilson@umd.edu     12     Active    100% (20/20)    0       [Edit][View]
Amy Chen      achen@umd.edu       10     Warning   45% (9/20)      11      [Edit][View]
[Pagination: < 1 2 3 4 5 6 > Showing 1-10 of 60]
```

**Features:**
- Sortable columns (click headers)
- Search by name/email
- Filter by grade, status, attendance %
- Color coding:
  - Green: 0-2 meetings missed
  - Yellow: More than 2 meetings missed
  - Red: More than 3 meetings missed
- Click "Missed" number to see popup with list of missed events
- Bulk actions (export selected, mark inactive, email reminders)

---

### 2. Event Management 📅

#### 2.1 Create Event with QR
**Access:** Dashboard > Create Event OR Events > New Event

**Form Fields:**
- Event Name* (e.g., "General Meeting")
- Event Type (dropdown: Meeting, Competition, Social, Workshop)
- Date* (calendar picker)
- Time* (time picker)
- Location* (text field)
- Description (text area)
- Points Value (number, default: 1)

**On Save:**
- Automatically generates unique QR code
- Creates check-in URL: `/checkin/{event-id}`
- Shows success with QR preview

#### 2.2 Event List View
**Display:**
```
[+ Create Event] [View Past Events]

Upcoming Events:
Name                Date        Time      Location       QR Code    Attendance
--------------------------------------------------------------------------------
General Meeting     11/28/24    3:00 PM   Room 1234     [View QR]  0/60
Competition Prep    12/01/24    2:00 PM   Auditorium    [View QR]  0/60
Holiday Social      12/08/24    5:00 PM   Cafeteria     [View QR]  0/60
```

**Features:**
- Quick QR access (click to enlarge/download)
- Edit event details
- View who's checked in
- Cancel event (with notification option)

#### 2.3 QR Code Display
**Access:** Events > View QR

**Display Options:**
```
+------------------------+
|                        |
|    [QR CODE IMAGE]     |
|                        |
+------------------------+
Event: General Meeting
Date: 11/28/24 3:00 PM
Check-in URL: fbla.org/checkin/123

[Download QR] [Print QR] [Share Link] [Copy URL]
```

---

### 3. Attendance Reports 📊

#### 3.1 Report Types Menu
**Access:** Reports tab

**Options:**
```
Select Report Type:
○ Event Attendance Report (Who came to which event)
○ Member Attendance Report (Individual member history)
○ Attendance Summary (Overall statistics)
○ Active Member Report (50%+ attendance)
```

#### 3.2 Event Attendance Report
**Purpose:** See who attended a specific event

**Display:**
```
Event: General Meeting - 11/28/24
Total Attendance: 45/60 (75%)

Attendees:
Name            Check-in Time    Rating    Comments
-------------------------------------------------------
John Doe        3:05 PM         9/10      "Great meeting!"
Jane Smith      3:02 PM         10/10     "Loved the speaker"
Bob Johnson     3:15 PM         8/10      ""

Not Present (15):
- Alice Williams
- Charlie Brown
- [Show all...]

[Export to CSV] [Print Report]
```

#### 3.3 Member Attendance Report
**Purpose:** See one member's complete attendance history with missed events highlighted

**Display:**
```
Member: John Doe
Grade: 11 | Email: jdoe@umd.edu
Overall Attendance: 85% (17/20 events)

Summary:
- Events Attended: 17
- Events Missed: 3
- Attendance Rate: 85%
- Status: Active Member ✓

MISSED EVENTS (3):
Event Name          Date        Type         Points Lost
----------------------------------------------------------
Workshop            11/14/24    Workshop     1
Early Meeting       10/28/24    Meeting      1
Competition Prep    10/15/24    Competition  2
                                            Total: 4 points

ATTENDED EVENTS (17):
Event Name          Date        Check-in     Rating
----------------------------------------------------------
General Meeting     11/28/24    3:05 PM      9/10
Competition Prep    11/21/24    2:10 PM      8/10
Social Event        11/07/24    5:20 PM      10/10
[Show all 17...]

Attendance Trend: [Graph showing attendance over time]
Monthly Breakdown:
- September: 100% (3/3)
- October: 66% (4/6)
- November: 87% (7/8)

[Export Member Report] [Email Report to Member] [Print]
```

#### 3.4 Attendance Summary Dashboard
**Display:**
```
Overall Statistics:
- Average Event Attendance: 75%
- Most Attended Event: General Meeting (45/60)
- Least Attended Event: Early Workshop (12/60)

Member Status Breakdown:
🟢 Good Standing (0-2 missed): 35 members
🟡 Warning (>2 missed): 18 members
🔴 At Risk (>3 missed): 7 members

Top Attendees:
1. Jane Smith - 0 missed (20/20)
2. Bob Wilson - 0 missed (20/20)
3. John Doe - 3 missed (17/20)

Members At Risk (>3 events missed):
Name              Events Missed    Last Attended
------------------------------------------------
Charlie Brown     14/20           2 weeks ago
Alice Williams    15/20           3 weeks ago
David Lee         12/20           1 week ago
[View all 7...]

[Generate Full Report] [Export All Data] [Email At-Risk Members]
```

---

### 4. Export Functionality 💾

#### 4.1 Export Options
**Access:** Any list view > Export button

**Format Options:**
- CSV (Excel compatible)
- PDF (formatted report)
- Print View (browser print)

#### 4.2 Export Types

**Member List Export:**
```csv
Name,Email,Grade,StudentID,MemberType,JoinDate,AttendanceRate
John Doe,jdoe@umd.edu,11,123456,Regular,09/01/24,85%
```

**Event Attendance Export:**
```csv
EventName,Date,MemberName,CheckInTime,Rating,Comment
General Meeting,11/28/24,John Doe,3:05 PM,9,"Great meeting!"
```

**Complete Data Export:**
- All members with all fields
- All events with attendance
- Summary statistics sheet
- Formatted for easy Excel pivot tables

---

## Mobile Considerations 📱

### Responsive Design
- Navigation collapses to hamburger menu
- Tables become cards on small screens
- QR codes remain full-size for scanning
- Touch-friendly buttons (min 44x44px)

### Mobile Priority Features
1. View QR codes (for printing/sharing)
2. Quick member lookup
3. View attendance reports
4. Export to email

---

## User Experience Flow

### Typical E-Board Workflow
1. **Before Event:**
   - Create event → Generate QR → Print/display QR

2. **During Event:**
   - Members scan QR → Fill check-in form → Submit
   - E-Board can monitor real-time check-ins

3. **After Event:**
   - View attendance report
   - Export for chapter records
   - Follow up with absent members

### Quick Actions (One-Click)
- Generate attendance report for last event
- Export active members list
- View today's events
- See recent check-ins

---

## Security & Permissions

### E-Board Access Levels
**President/VP:** Full access to all features
**Secretary:** Member and attendance management
**Treasurer:** Read-only access + export reports
**Other Officers:** Customizable permissions

### Data Protection
- Passwords hashed (never stored plain text)
- Session timeout after 30 min inactive
- Audit log for all data changes
- Member data never publicly visible

---

## Success Metrics

### Key Performance Indicators
- Check-in takes < 30 seconds
- Reports generate in < 2 seconds
- QR codes scan on first try 95%+
- Mobile responsive on all devices

### User Satisfaction Goals
- E-Board can run meeting check-in without help
- Reports useful for chapter requirements
- Data easily shareable with advisors
- Reduces administrative time by 50%

---

## Future Enhancements (Post-MVP)

### Nice to Have
- Email notifications for events
- Member self-service portal
- Photo uploads for member profiles
- Integration with Google Calendar
- Attendance certificates generation
- Points/gamification system
- Alumni tracking

### Long Term Vision
- Multi-chapter support
- State conference integration
- Scholarship application tracking
- Community service hour tracking
- Budget management module

---

## Implementation Notes

### Technology Stack
- **Backend:** Flask + SQLAlchemy
- **Database:** SQLite (upgradeable to PostgreSQL)
- **Frontend:** Bootstrap 5 + Vanilla JS
- **QR Generation:** Python qrcode library
- **Export:** Python CSV library + ReportLab for PDF

### Development Priorities
1. Core CRUD operations work perfectly
2. QR check-in is foolproof
3. Reports are accurate and useful
4. Mobile experience is smooth
5. Export formats are Excel-friendly

---

*This document defines the complete Officer Dashboard specifications. Focus on building the MVP features first, then enhance based on E-Board feedback.*
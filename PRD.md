# Product Requirements Document (PRD)
# FBLA Membership Tracker - Backend System

## Document Information
- **Version**: 1.0
- **Date**: November 21, 2024
- **Timeline**: 3-week development (Nov 21 - Dec 12, 2024)
- **Project Phase**: MVP Backend with Limited Frontend

## Executive Summary

The FBLA Membership Tracker is a chapter management system designed to streamline administrative operations for FBLA chapters. This PRD defines the scope for a 3-week MVP development phase focusing on backend API development with minimal frontend interfaces for essential administrative functions.

## Project Scope

### In Scope ✅

#### 1. Backend API Infrastructure
- **RESTful API Architecture**
  - Complete REST API using Flask/Python
  - JSON request/response format
  - Comprehensive error handling and validation
  - API documentation via Swagger/OpenAPI

- **Database Layer**
  - SQLAlchemy ORM with SQLite (development) / PostgreSQL (production)
  - Complete schema for all entities
  - Database migrations with Alembic
  - Optimized queries with proper indexing

#### 2. Authentication & Authorization (E-Board Only)
- **E-Board Login System**
  - JWT-based authentication for E-Board members only
  - Single admin level for all E-Board members (no role hierarchy)
  - Secure password hashing with bcrypt
  - Session management with refresh tokens
  - NO member login functionality in this phase

#### 3. Core Data Models
- **Member Management**
  - Member profiles (name, email, grade, student ID)
  - Membership types (General, Committee, Cohort, E-Board)
  - Automatic status calculation (Good Standing, Probation, Inactive)
  - Manual member creation by E-Board (add individual members)
  - Initial population via CSV import by E-Board
  - Bulk import/update capabilities

- **Event Management**
  - Event creation/editing by E-Board
  - Event types (General Meeting, Committee Meeting, Workshop, etc.)
  - Mandatory event flags configurable per membership type
    - Can mark events as mandatory for specific groups (e.g., Cohort only, All members)
  - Date/time and location tracking
  - No recurring events in this phase

- **Attendance Tracking**
  - Attendance records with timestamps
  - Link between members and events
  - Duplicate check-in prevention

#### 4. QR Code Check-in System
- **QR Generation**
  - Unique QR code generation for each event
  - QR codes contain event ID and check-in URL
  - Downloadable QR images for printing/sharing

- **Check-in Form (Minimal Frontend)**
  - Simple HTML form displayed when QR code is scanned
  - Required Fields:
    - Full Name (text input)
    - Email (email input)
    - Meeting Rating: "Overall, how was the meeting today?" (1-10 scale)
    - NPS Score: "How likely are you to recommend this meeting to a friend?" (1-10 scale)
    - Positive Feedback: "What is one thing you liked about the meeting?" (text area)
    - Improvement Feedback: "What is one thing we can improve for this meeting?" (text area)
  - Form validation against member database
  - Success/error confirmation page
  - Mobile-responsive design using Bootstrap

#### 5. E-Board Admin Interface (Minimal Frontend)
- **Login Page**
  - Simple username/password form
  - JWT token storage in session

- **Dashboard (Basic HTML)**
  - Member list view with search/filter
  - Add new member form (manual member creation)
  - Event creation form
  - View attendance reports
  - Export data to CSV
  - Basic styling with Bootstrap (no complex UI)

#### 6. Requirements & Status Engine
- **Automated Calculations**
  - Define requirements per membership type
  - Track: attendance minimums, competition participation, volunteering hours
  - Automatic status updates:
    - Good Standing: Meeting all requirements
    - Probation: Missing more than 2 mandatory meetings
    - Inactive: Extended absence or severe requirement deficit
  - Manual email notifications to members about status (automated emails in future phase)

#### 7. Reporting & Analytics API
- **Data Aggregation Endpoints**
  - Member attendance rates
  - Event attendance statistics
  - Requirements completion percentages
  - Chapter health metrics
  - CSV export functionality

#### 8. Bulk Operations
- **Administrative Tools**
  - CSV member import with validation
  - Bulk status updates
  - Mass event creation
  - Batch attendance recording

### Out of Scope ❌

#### 1. Member-Facing Features
- **No Member Authentication**
  - Members cannot log in
  - No member dashboard or profile viewing
  - No self-service features for members
  - Members cannot view any data (rely on Google Calendar for event info)

- **No Automated Member Notifications**
  - No automated email system (manual emails only)
  - No SMS alerts
  - No push notifications
  - Status updates communicated manually by E-Board

#### 2. Full Frontend Application
- **No Complete UI System**
  - No React/Vue/Angular frontend
  - No mobile app
  - No progressive web app (PWA)
  - No complex JavaScript interactions

- **Limited Visual Design**
  - Basic Bootstrap styling only
  - No custom design system
  - No animations or advanced UX

#### 3. External Integrations
- **No Calendar Sync**
  - No Google Calendar integration
  - No Outlook integration
  - No automatic event sync

- **No Payment Processing**
  - No dues collection
  - No fundraising features
  - No payment gateway integration

#### 4. Advanced Features
- **No Competition Tracking**
  - Competition results not tracked
  - No scoring system
  - No placement history

- **No Document Management**
  - No file uploads
  - No document storage
  - No resource library

- **No Communication Features**
  - No in-app messaging
  - No announcements system
  - No discussion forums

## User Stories

### E-Board Administrator
1. As an E-Board member, I can log in securely to access admin functions
2. As an E-Board member, I can create and edit events with QR codes
3. As an E-Board member, I can view all member data and their current status
4. As an E-Board member, I can manually add individual members to the system
5. As an E-Board member, I can bulk import members from a CSV file
6. As an E-Board member, I can generate attendance reports for any event
7. As an E-Board member, I can export data for external analysis

### Chapter Member (Limited Interaction)
1. As a member, I can scan a QR code at an event
2. As a member, I can fill out the check-in form with my information
3. As a member, I receive confirmation that my attendance was recorded

## Technical Requirements

### API Endpoints

#### Authentication
- `POST /api/auth/login` - E-Board login
- `POST /api/auth/logout` - Logout
- `POST /api/auth/refresh` - Refresh JWT token

#### Members
- `GET /api/members` - List all members (admin only)
- `GET /api/members/{id}` - Get member details
- `POST /api/members` - Create new member
- `PUT /api/members/{id}` - Update member
- `DELETE /api/members/{id}` - Delete member
- `POST /api/members/import` - Bulk import via CSV

#### Events
- `GET /api/events` - List all events
- `GET /api/events/{id}` - Get event details
- `POST /api/events` - Create new event (admin only)
- `PUT /api/events/{id}` - Update event (admin only)
- `DELETE /api/events/{id}` - Delete event (admin only)
- `GET /api/events/{id}/qr` - Get QR code for event

#### Attendance
- `POST /api/attendance/checkin` - Record attendance (public endpoint)
- `GET /api/attendance/event/{event_id}` - Get attendance for event
- `GET /api/attendance/member/{member_id}` - Get attendance for member

#### Reports
- `GET /api/reports/attendance` - Attendance statistics
- `GET /api/reports/requirements` - Requirements completion
- `GET /api/reports/export` - Export data as CSV

### Database Schema

#### Core Tables
- `members` - Member information and status
- `events` - Event details and settings (with mandatory flags per membership type)
- `attendance` - Junction table for member-event attendance with feedback fields
  - meeting_rating (1-10)
  - nps_score (1-10)
  - positive_feedback (text)
  - improvement_feedback (text)
- `requirements` - Requirement definitions per membership type
- `users` - E-Board login credentials (single admin role)

### Security Requirements
- JWT tokens expire after 24 hours
- Passwords hashed with bcrypt (min 10 rounds)
- API rate limiting to prevent abuse
- Input validation on all endpoints
- SQL injection prevention via ORM
- XSS protection on form inputs
- QR codes only displayed during meetings (physical security)
- No email verification required for check-ins (QR code access implies physical presence)

## Success Criteria

### Week 1 Deliverables (Nov 21-28)
✅ Flask project structure set up
✅ Database schema implemented
✅ Authentication system working
✅ Basic member CRUD operations

### Week 2 Deliverables (Nov 29-Dec 5)
✅ Event management API complete
✅ QR code generation working
✅ Check-in form functional
✅ Requirements engine calculating status

### Week 3 Deliverables (Dec 6-12)
✅ E-Board admin interface functional
✅ Reports and analytics working
✅ CSV import/export operational
✅ API documentation complete
✅ Basic test coverage

## Acceptance Criteria

1. **E-Board can successfully:**
   - Log in and maintain session
   - Create events with QR codes
   - Add new members manually (individual form)
   - Import members via CSV (bulk)
   - View and manage all members
   - Generate and export reports

2. **Members can successfully:**
   - Scan QR code on mobile device
   - Submit check-in form
   - Receive attendance confirmation

3. **System automatically:**
   - Calculates member status
   - Prevents duplicate check-ins
   - Validates all data inputs

## Risks & Mitigation

| Risk | Impact | Mitigation |
|------|--------|------------|
| Fake check-ins without authentication | Low | QR codes only shown at physical meetings, validates against member database |
| Limited frontend may confuse users | Low | Clear documentation, simple intuitive forms |
| 3-week timeline is aggressive | High | Focus on core features only, defer nice-to-haves |
| No automated notifications | Medium | E-Board exports reports and manually emails members about status |
| Members unaware of requirements | Medium | E-Board communicates via email, future phase adds member portal |

## Future Phases (Post-MVP)

### Phase 2 (January 2025)
- Full member authentication system
- Complete member dashboard
- Email/SMS notifications
- Google Calendar integration

### Phase 3 (February 2025)
- Competition tracking module
- Mobile app development
- Advanced analytics
- Document management

## Appendix

### Sample QR Check-in Flow
1. E-Board creates event → System generates QR code
2. QR code displayed at meeting venue (physical display only)
3. Member scans QR with phone camera
4. Phone opens check-in form URL
5. Member completes form:
   - Full Name
   - Email
   - Meeting Rating (1-10)
   - NPS Score (1-10)
   - What they liked (text)
   - What to improve (text)
6. System validates email against member database
7. Attendance recorded with timestamp and feedback
8. Success message displayed

### CSV Import Format
```csv
first_name,last_name,email,student_id,grade,membership_type
John,Doe,john.doe@school.edu,123456,10,General
Jane,Smith,jane.smith@school.edu,123457,11,Committee
```

---

**Document Status**: DRAFT - Pending Review
**Next Steps**: Review with stakeholders, finalize requirements, begin implementation
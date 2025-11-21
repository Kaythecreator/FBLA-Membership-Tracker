# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

FBLA Membership Tracking System - An internal tool for managing FBLA chapter operations including membership data, attendance tracking, event management, and requirements monitoring.

## Development Workflow

This project uses the Agent-OS framework for structured development. Use these commands in sequence:

1. `/plan-product` - Define product mission and roadmap
2. `/write-spec` - Create detailed feature specifications
3. `/shape-spec` - Refine specifications with requirements
4. `/create-tasks` - Break down specs into implementation tasks
5. `/implement-tasks` - Execute the implementation
6. `/orchestrate-tasks` - Manage overall workflow

## Core System Architecture

### Backend Structure
- **Framework**: Python (Flask/Django) + SQL database
- **API Design**: RESTful with endpoints for:
  - Member management (`/api/members`)
  - Event operations (`/api/events`)
  - Attendance tracking (`/api/attendance`)
  - Competition management (`/api/competitions`)
  - Requirements tracking (`/api/requirements`)

### Database Schema
Key entities and relationships:
- **Members**: Profile data, membership type, status calculations
- **Events**: Event details, mandatory flags per member type
- **Attendance**: Member-event junction with timestamps
- **Competitions**: Event participation and performance tracking
- **Requirements**: Dynamic requirement definitions and fulfillment tracking

### Key Features Implementation

**QR Code System**:
- Generate unique QR codes for each event using Python qrcode library
- Single check-in endpoint that identifies event from QR payload
- Store check-in data with feedback responses

**Google Calendar Integration**:
- Use Google Calendar API for automatic event sync
- Store API credentials securely (never commit)

**Role-Based Access**:
- Member view: Personal dashboard with progress tracking
- E-board view: Full admin capabilities and analytics

## Development Standards

### Code Organization
- Follow Agent-OS standards in `/agent-os/standards/`
- API endpoints follow RESTful patterns (see `/agent-os/standards/backend/api.md`)
- Database models include timestamps on all tables
- Minimal testing approach - focus on critical user flows only

### Error Handling
- User-friendly error messages (no technical details exposed)
- Centralized exception handling
- Graceful degradation for non-critical features

### Security Considerations
- Role-based access control (RBAC) for all endpoints
- Input validation on all user inputs
- SQL injection prevention through ORM usage
- XSS protection for any rendered content

## Common Development Commands

```bash
# Project is in initial setup phase - commands will be added as build system is configured
# Expected commands once stack is defined:

# Python/Flask setup (if chosen):
pip install -r requirements.txt
python app.py  # Run development server

# Database operations:
python manage.py migrate  # Run migrations
python manage.py seed     # Seed test data

# Testing:
python -m pytest tests/  # Run test suite
```

## Project Status

Currently in planning phase (initial commit only). Next steps:
1. Define technology stack specifics
2. Set up project structure with chosen framework
3. Configure database and ORM
4. Implement core models
5. Build API endpoints
6. Add QR code generation
7. Integrate Google Calendar API
8. Create user authentication system
9. Build member and admin dashboards

## Integration Points

- **Google Calendar API**: Event synchronization
- **QR Code Libraries**: `qrcode` or `pyqrcode` for generation
- **Email Service**: Member notifications (TBD)
- **Authentication**: Session-based or JWT (TBD)

## Key Business Logic

**Membership Types** (hierarchical):
- General Member
- Committee Member (assigned to specific committee)
- Cohort Member
- Executive Board Member

**Event Types**:
- General Meeting
- Cohort Meeting
- Committee Meeting
- Workshop
- Fundraiser
- Competition

**Requirement Categories**:
- Attendance minimums per member type
- Competition participation
- Volunteering hours
- Fundraising participation

**Status Calculations**:
- Good Standing: Meets all requirements
- Probation: Missing 1-2 requirements
- Inactive: Missing 3+ requirements or extended absence
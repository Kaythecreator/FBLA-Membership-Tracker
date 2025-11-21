# FBLA Membership Tracker

A comprehensive web application for managing FBLA chapter operations, including membership tracking, event management, attendance monitoring, and requirements tracking.

## Overview

The FBLA Membership Tracking System is designed to streamline chapter administration by providing a centralized platform for managing member data, tracking event attendance, monitoring competition participation, and ensuring members meet their requirements for good standing.

## Key Features

### Member Management
- **Comprehensive Member Profiles**: Store and manage detailed member information including contact details, grade level, and membership type
- **Hierarchical Membership Types**: Support for General Members, Committee Members, Cohort Members, and Executive Board Members
- **Status Tracking**: Automatic calculation of member standing (Good Standing, Probation, or Inactive) based on requirement fulfillment
- **Member Dashboard**: Personal view for members to track their own progress and requirements

### Event Management
- **Event Creation and Scheduling**: Create various event types (General Meetings, Cohort Meetings, Workshops, Fundraisers, Competitions)
- **Google Calendar Integration**: Automatic synchronization with Google Calendar for seamless event management
- **Mandatory Event Designation**: Mark events as mandatory for specific member types
- **Event History**: Complete record of all past and upcoming events

### Attendance Tracking
- **QR Code Check-In System**: Generate unique QR codes for each event enabling quick and contactless check-ins
- **Real-Time Attendance Recording**: Instant attendance capture with timestamp logging
- **Check-In Feedback**: Collect optional feedback during the check-in process
- **Attendance Reports**: Generate detailed attendance reports by member, event, or time period

### Competition Management
- **Competition Registration**: Track member participation in various FBLA competitions
- **Performance Tracking**: Record competition results and achievements
- **Competition Requirements**: Monitor competition participation as part of membership requirements

### Requirements Tracking
- **Dynamic Requirements System**: Define and update requirements based on membership type
- **Progress Monitoring**: Real-time tracking of requirement fulfillment
- **Automated Notifications**: Alert members when approaching requirement deadlines
- **Requirement Categories**: Track attendance minimums, competition participation, volunteering hours, and fundraising involvement

### Administrative Features
- **E-Board Dashboard**: Comprehensive admin panel with full chapter oversight
- **Analytics and Reporting**: Generate insights on member engagement, event attendance, and chapter health
- **Bulk Operations**: Efficiently manage multiple members or events simultaneously
- **Data Export**: Export member and event data for external reporting

## Technical Architecture

### Backend
- **Framework**: Python-based web framework (Flask/Django)
- **Database**: SQL database for reliable data storage
- **API**: RESTful API architecture for clean separation of concerns
- **Authentication**: Secure role-based access control (RBAC)

### Frontend
- **Responsive Design**: Mobile-first approach ensuring accessibility on all devices
- **User Interfaces**: Separate dashboards for members and administrators
- **Real-Time Updates**: Dynamic content updates without page refreshes

### Integrations
- **Google Calendar API**: Seamless event synchronization
- **QR Code Generation**: Built-in QR code creation for event check-ins
- **Email Notifications**: Automated member communications

## Business Logic

### Membership Hierarchy
1. **General Member**: Basic membership with standard requirements
2. **Committee Member**: Assigned to specific committees with additional responsibilities
3. **Cohort Member**: Part of specialized cohorts with unique requirements
4. **Executive Board Member**: Leadership roles with administrative privileges

### Event Categories
- General Meetings
- Cohort Meetings
- Committee Meetings
- Workshops
- Fundraisers
- Competitions

### Member Status Calculation
- **Good Standing**: Meets all requirements for their membership type
- **Probation**: Missing 1-2 requirements with opportunity to catch up
- **Inactive**: Missing 3+ requirements or extended absence from chapter activities

## Getting Started

### Prerequisites
- Python 3.8 or higher
- SQL database (PostgreSQL, MySQL, or SQLite for development)
- Google Calendar API credentials (for calendar integration)

### Installation
```bash
# Clone the repository
git clone https://github.com/Kaythecreator/FBLA-Membership-Tracker.git
cd FBLA-Membership-Tracker

# Install dependencies (once project is set up)
pip install -r requirements.txt

# Set up database
python manage.py migrate

# Run development server
python manage.py runserver
```

### Configuration
1. Set up database connection in configuration file
2. Add Google Calendar API credentials
3. Configure email service for notifications
4. Set up admin account for initial access

## Development

This project uses the Agent-OS framework for structured development. The following workflow commands are available:

- `/plan-product` - Define product mission and roadmap
- `/write-spec` - Create detailed feature specifications
- `/shape-spec` - Refine specifications with requirements
- `/create-tasks` - Break down specs into implementation tasks
- `/implement-tasks` - Execute the implementation
- `/orchestrate-tasks` - Manage overall workflow

### Project Structure
```
FBLA-Membership-Tracker/
├── .claude/           # Claude Code configuration
├── agent-os/          # Agent-OS framework and standards
├── api/              # Backend API (to be created)
├── frontend/         # Frontend application (to be created)
├── database/         # Database schemas and migrations (to be created)
├── docs/             # Documentation (to be created)
└── tests/            # Test suite (to be created)
```

## Contributing

This project is currently in early development. Contribution guidelines will be established as the project matures.

## License

[License information to be added]

## Contact

For questions or support, please contact the project maintainer through the GitHub repository.

## Status

**Current Phase**: Planning and Initial Development

The project is in its initial setup phase with core architecture being defined and foundational features being planned. Check the repository's issues and project board for current development status and upcoming features.
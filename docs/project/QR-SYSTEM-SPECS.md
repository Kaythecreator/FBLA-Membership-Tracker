# QR Code System Specifications
## FBLA Membership Tracker - Check-in System

---

## Overview
The QR Code System enables quick, contactless check-in for FBLA events. Each event has a unique QR code that members scan with their phones to record attendance.

---

## User Stories

### As an E-Board Officer
- **I want to** generate unique QR codes for each event **so that** members can check in easily
- **I want to** display/print QR codes **so that** they're visible at event entrances
- **I want to** track who scanned each QR code **so that** attendance is automatically recorded
- **I want to** prevent duplicate check-ins **so that** attendance counts are accurate
- **I want to** download QR codes **so that** I can print them or share digitally

### As a Member
- **I want to** scan a QR code with my phone **so that** I can check in quickly
- **I want to** see a check-in form after scanning **so that** I can confirm my attendance
- **I want to** receive confirmation **so that** I know my attendance was recorded
- **I want to** rate the event **so that** E-Board gets feedback
- **I want to** check in without logging in **so that** the process is fast

### As an Event Organizer
- **I want to** see real-time check-ins **so that** I know current attendance
- **I want to** close check-ins after events **so that** late arrivals aren't counted
- **I want to** reopen check-ins if needed **so that** technical issues can be resolved

---

## System Architecture

### QR Code Generation Flow
```
Event Created
    ↓
Generate Unique ID (event_123)
    ↓
Create Check-in URL (/checkin/event_123)
    ↓
Generate QR Code Image
    ↓
Save QR to /static/qr_codes/event_123.png
    ↓
Link QR path to Event Record
```

### Check-in Flow
```
Member Scans QR
    ↓
Phone Opens Check-in URL
    ↓
Display Check-in Form
    ↓
Member Submits Info
    ↓
Validate Member Exists
    ↓
Check for Duplicates
    ↓
Save Attendance Record
    ↓
Show Success Message
```

---

## Technical Specifications

### 1. QR Code Generation

#### 1.1 When to Generate
- **Automatically** when event is created
- **Regenerate** option if QR is lost/corrupted
- **Batch generation** for multiple events

#### 1.2 QR Code Contents
```python
# URL Structure
check_in_url = f"{BASE_URL}/checkin/{event_id}"

# Example
"https://fbla-tracker.com/checkin/evt_20241128_001"
```

#### 1.3 QR Code Properties
```python
# qr_generator.py specifications
{
    "version": 1,              # QR Version (1 = 21x21 modules)
    "error_correction": "M",   # Medium error correction (15%)
    "box_size": 10,           # Pixel size of each box
    "border": 4,              # Border size (minimum 4)
    "fill_color": "black",    # QR code color
    "back_color": "white",    # Background color
    "format": "PNG",          # Image format
    "size": "300x300"         # Output size in pixels
}
```

#### 1.4 File Storage
```
/static/qr_codes/
    ├── evt_20241128_001.png    # General Meeting
    ├── evt_20241201_002.png    # Competition Prep
    └── evt_20241208_003.png    # Holiday Social

Naming Convention: evt_{YYYYMMDD}_{sequence}.png
```

---

### 2. Check-in URL System

#### 2.1 URL Structure
```
Base Pattern: /checkin/{event_id}
Alternative: /c/{short_code}  # Shorter URL option

Examples:
- /checkin/evt_20241128_001
- /checkin/general-meeting-nov28
- /c/gm1128  # Short version
```

#### 2.2 URL Security
- **No authentication required** for check-in page
- **Event must be active** (not past end time + 2 hours)
- **Rate limiting**: Max 10 check-ins per IP per minute
- **HTTPS only** in production

#### 2.3 URL Persistence
- URLs remain valid until event is deleted
- Redirect old URLs if event ID changes
- Track URL access for analytics

---

### 3. Check-in Form

#### 3.1 Mobile-Optimized Layout
```html
<!-- Viewport meta tag -->
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- Form Structure -->
<div class="check-in-container">
    <h1>FBLA Check-In</h1>
    <h2>{Event Name}</h2>
    <p>{Date} at {Time}</p>

    <form id="checkin-form">
        <!-- Member Identification -->
        <input type="email" placeholder="Your Email *" required>
        <input type="text" placeholder="Your Name *" required>

        <!-- Optional Fields -->
        <input type="tel" placeholder="Phone (optional)">

        <!-- Event Feedback -->
        <label>Rate this event:</label>
        <input type="range" min="1" max="10" value="8">
        <span id="rating-value">8/10</span>

        <textarea placeholder="Comments (optional)"></textarea>

        <!-- Submit -->
        <button type="submit">CHECK IN</button>
    </form>
</div>
```

#### 3.2 Form Validation
```javascript
// Client-side validation
- Email format validation
- Name minimum 2 characters
- Prevent double-submission
- Show loading state during submit

// Server-side validation
- Verify member exists in database
- Check for duplicate attendance
- Validate event is active
- Sanitize all inputs
```

#### 3.3 Mobile UI Requirements
- **Font size**: Minimum 16px (prevents zoom)
- **Touch targets**: Minimum 44x44px
- **Form fields**: Full width on mobile
- **Auto-capitalize**: Name fields
- **Input types**: Use email/tel for keyboards
- **No horizontal scroll**: 100% viewport width

---

### 4. Duplicate Prevention

#### 4.1 Detection Logic
```python
def check_duplicate_attendance(member_id, event_id):
    """
    Check if member already checked into this event
    """
    existing = Attendance.query.filter_by(
        member_id=member_id,
        event_id=event_id
    ).first()

    if existing:
        # Return time of original check-in
        return {
            "duplicate": True,
            "checked_in_at": existing.checkin_time,
            "message": "You already checked in at {time}"
        }
    return {"duplicate": False}
```

#### 4.2 Duplicate Handling
- **First check-in**: Always accepted
- **Subsequent attempts**: Show friendly message
- **Override option**: E-Board can manually override
- **Time window**: Allow re-check-in after 4 hours (for multi-session events)

---

### 5. Success/Error Pages

#### 5.1 Success Page
```
✅ Check-in Successful!

Thank you, {Name}!
Your attendance has been recorded for:
{Event Name}
{Date} at {Time}

Your Rating: {number}/10
Comments: {If provided}

[Back to FBLA Site] [Check Into Another Event]
```

#### 5.2 Error Messages
```python
ERROR_MESSAGES = {
    "EVENT_NOT_FOUND": "This event doesn't exist. Please check the QR code.",
    "EVENT_NOT_ACTIVE": "Check-in is not available for this event.",
    "MEMBER_NOT_FOUND": "We couldn't find your member record. Please see an officer.",
    "DUPLICATE_CHECKIN": "You've already checked in at {time}!",
    "EVENT_FULL": "This event has reached capacity.",
    "CHECKIN_CLOSED": "Check-in has closed for this event.",
    "TECHNICAL_ERROR": "Something went wrong. Please try again or see an officer."
}
```

---

### 6. QR Code Display & Management

#### 6.1 Display Options
```
Officer Dashboard > Events > [View QR]

+--------------------------------+
|     FBLA Event Check-In       |
|                                |
|     [QR CODE IMAGE]            |
|                                |
|   General Meeting              |
|   Nov 28, 2024 - 3:00 PM      |
|   Room 1234                    |
+--------------------------------+

Actions:
[📥 Download PNG] [🖨️ Print] [📋 Copy Link] [📧 Email]

Display Options:
[ ] Include event details on image
[ ] Add FBLA logo
[ ] Generate poster version (8.5x11)
```

#### 6.2 Print Layout
```
<!-- Print-optimized CSS -->
@media print {
    .qr-poster {
        page-break-inside: avoid;
        text-align: center;
        padding: 50px;
    }
    .qr-code {
        width: 400px;
        height: 400px;
        margin: 0 auto;
    }
    .event-title {
        font-size: 36pt;
        font-weight: bold;
    }
    .instructions {
        font-size: 24pt;
        margin-top: 30px;
    }
}

<!-- Poster Template -->
SCAN TO CHECK IN
[Large QR Code]
FBLA General Meeting
November 28, 2024 • 3:00 PM
Room 1234
```

---

### 7. Real-Time Monitoring

#### 7.1 Live Check-in Dashboard
```
Event: General Meeting
Status: 🟢 Active Check-in

Current Attendance: 23/60 (38%)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
████████████░░░░░░░░░░░░░░░░░░░░

Recent Check-ins (Live):
• John Doe - 3:05 PM (just now)
• Jane Smith - 3:04 PM (1 min ago)
• Bob Wilson - 3:03 PM (2 min ago)
[Auto-refreshes every 10 seconds]

[Pause Check-in] [View Full List] [Export Current]
```

#### 7.2 Analytics
```python
# Track these metrics
{
    "total_scans": 145,           # Total QR scans
    "unique_visitors": 62,         # Unique IPs
    "successful_checkins": 45,     # Completed check-ins
    "duplicate_attempts": 8,       # Duplicate check-in attempts
    "error_rate": "3%",           # Failed check-ins
    "avg_checkin_time": "28s",    # Time from scan to submit
    "peak_checkin_time": "3:00-3:15 PM"
}
```

---

## Testing Scenarios

### 1. Happy Path
1. E-Board creates event → QR generates
2. QR code printed and displayed at venue
3. Member scans with phone camera
4. Check-in page loads quickly
5. Member enters info and submits
6. Success message appears
7. Attendance recorded in database

### 2. Edge Cases
- **No internet**: Save check-in locally, sync later
- **QR damaged**: Manual check-in URL entry
- **Member not in database**: Collect info for later addition
- **Multiple devices**: Prevent same email different devices
- **Event cancelled**: Show cancellation message
- **Check-in after event**: Allow with "late" flag

### 3. Error Recovery
- **Database down**: Queue check-ins, process when restored
- **QR won't scan**: Provide text URL as backup
- **Form won't submit**: Show error, preserve entered data
- **Duplicate submission**: Ignore second, show first time

---

## Security Considerations

### 1. Prevent Abuse
- **Rate limiting**: Max 10 check-ins per minute per IP
- **CAPTCHA**: After 3 failed attempts
- **Time restrictions**: Can't check in >2 hours after event ends
- **Geographic restrictions**: Optional geofencing

### 2. Data Protection
- **No passwords**: Check-in doesn't require authentication
- **Minimal data**: Only collect necessary information
- **HTTPS only**: Encrypt all check-in traffic
- **No personal data in QR**: Only event ID

### 3. Validation
- **Server-side validation**: Never trust client
- **Input sanitization**: Prevent SQL injection
- **XSS protection**: Escape all output
- **CSRF tokens**: On form submissions

---

## Performance Requirements

### Response Times
- **QR Generation**: < 1 second
- **Check-in Page Load**: < 2 seconds on 3G
- **Form Submission**: < 1 second
- **Success Display**: Immediate

### Scalability
- Support 100 concurrent check-ins
- Handle 60 members in 10 minutes
- Store 10,000 QR codes
- 1-year data retention

### Mobile Performance
- **Page size**: < 100KB
- **Time to Interactive**: < 3 seconds
- **First Contentful Paint**: < 1 second
- **Works offline**: Service worker for caching

---

## Success Metrics

### KPIs
- **QR scan success rate**: > 95%
- **Check-in completion rate**: > 90%
- **Average check-in time**: < 30 seconds
- **Mobile usage**: > 80%
- **Error rate**: < 2%

### User Satisfaction
- Members find it faster than paper
- E-Board spends less time on attendance
- No training needed for members
- Works on all smartphones

---

*This document defines the complete QR Code System specifications. The system should be simple, fast, and foolproof - optimizing for the 30-second check-in experience.*
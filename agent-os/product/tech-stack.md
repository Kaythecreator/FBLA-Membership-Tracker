# Tech Stack

## Development Approach
**Backend-First Development:** Building complete REST API layer before frontend implementation

## Framework & Runtime
- **Application Framework:** Flask (Python web framework for rapid API development)
- **Language/Runtime:** Python 3.11+ (latest stable version for performance and features)
- **Package Manager:** pip with requirements.txt for simple dependency management

## Backend API Architecture
- **API Framework:** Flask-RESTful for structured REST API development
- **Request Validation:** Marshmallow for request/response serialization and validation
- **API Documentation:** Flask-RESTX or Flasgger for automatic OpenAPI/Swagger generation
- **CORS Handling:** Flask-CORS for cross-origin requests (when frontend is added)

## Frontend (To Be Implemented Later)
- **Approach:** Server-side rendering with Flask/Jinja2 templates
- **Styling:** Bootstrap 5 via CDN (no build process)
- **JavaScript:** Minimal, only for QR scanning and essential interactivity

## Database & Storage
- **Database:** SQLite for development, PostgreSQL for production
- **ORM/Query Builder:** SQLAlchemy (Python's most mature ORM)
- **Migrations:** Alembic (SQLAlchemy's migration tool)
- **File Storage:** Local filesystem for development, cloud storage (AWS S3 or similar) for production

## API Architecture
- **API Style:** RESTful API with JSON responses
- **API Documentation:** Flask-RESTX or Flasgger for automatic Swagger/OpenAPI docs
- **Data Validation:** Marshmallow for serialization/deserialization schemas

## Authentication & Security
- **Authentication:** Flask-Login for session management
- **Password Hashing:** Werkzeug security utilities with bcrypt
- **Authorization:** Role-based access control (RBAC) with custom decorators
- **Session Storage:** Server-side sessions with Flask-Session

## Testing & Quality
- **Test Framework:** pytest with Flask testing utilities
- **Test Coverage:** pytest-cov for coverage reports
- **Linting:** Flake8 for Python code style
- **Formatting:** Black for consistent Python formatting
- **Type Checking:** mypy for optional static typing

## External Integrations
- **Calendar API:** Google Calendar API via google-api-python-client
- **QR Code Generation:** qrcode Python library with Pillow for image handling
- **Email Service:** SMTP with Flask-Mail for development, SendGrid for production
- **SMS (Optional):** Twilio for SMS notifications

## Development Tools
- **Environment Management:** python-venv for virtual environments
- **Environment Variables:** python-dotenv for configuration management
- **Task Runner:** Make or Invoke for common development tasks
- **Hot Reload:** Flask's built-in development server with debug mode

## Deployment & Infrastructure
- **Web Server:** Gunicorn (Python WSGI HTTP Server)
- **Reverse Proxy:** Nginx for production
- **Hosting Options:**
  - Development: Local machine
  - Production: DigitalOcean Droplet, AWS EC2, or school's internal servers
- **Process Manager:** systemd or Supervisor for production
- **CI/CD:** GitHub Actions for automated testing and deployment

## Monitoring & Logging
- **Application Logging:** Python's built-in logging module with rotating file handlers
- **Error Tracking:** Sentry for production error monitoring
- **Performance Monitoring:** Flask-APM or custom metrics with Prometheus

## Additional Libraries
- **Date/Time Handling:** pendulum or arrow for better datetime manipulation
- **Data Export:** pandas for CSV/Excel generation
- **Caching:** Flask-Caching with simple backend for development, Redis for production
- **CORS (if needed):** Flask-CORS for cross-origin requests
- **Rate Limiting:** Flask-Limiter for API endpoint protection

## Development Standards
- **Python Version:** 3.11+ (use pyenv for version management)
- **Code Style:** PEP 8 compliance enforced by tooling
- **Git Workflow:** Feature branches with main branch protection
- **Documentation:** Docstrings for all functions, README.md for setup instructions
- **Configuration:** Environment-based configuration (development, staging, production)
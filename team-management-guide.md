# Team Management Guide
## FBLA Membership Tracker - Tech Committee

### Team Structure (5 Developers)

## Skill Level Assessment & Task Assignment

### 🟢 **Beginner Developers** (Learning Focus)
**Best For**: Simple CRUD operations, data models, basic API endpoints

**Recommended Tasks**:
1. **Week 1**: Database Models & Setup
   - Set up SQLAlchemy models following the schema
   - Create database migrations
   - Write model validation methods
   - Add sample data scripts

2. **Week 2**: Basic API Endpoints
   - Member list endpoint (GET)
   - Single member retrieval (GET)
   - Basic validation helpers
   - CSV export functionality

**Pairing Strategy**: Pair with intermediate developers for code reviews

### 🟡 **Intermediate Developers** (Core Features)
**Best For**: Business logic, API development, integrations

**Recommended Tasks**:
1. **Week 1**: Authentication System
   - JWT implementation
   - Login/logout endpoints
   - Session management
   - Password hashing

2. **Week 2**: Event Management
   - Full CRUD for events
   - Mandatory event logic
   - QR code generation
   - Attendance recording

### 🔴 **Advanced Developers** (Complex Systems)
**Best For**: Architecture, complex algorithms, optimization

**Recommended Tasks**:
1. **Week 1**: System Architecture
   - Project structure setup
   - Error handling framework
   - Database connection pooling
   - API documentation setup

2. **Week 2-3**: Requirements Engine
   - Status calculation algorithm
   - Automated requirement tracking
   - Performance optimization
   - Complex reporting queries

## Development Workflow

### 1. Daily Standups (15 min)
```
Schedule: Mon-Fri @ 7:00 PM
Format:
- What did you complete yesterday?
- What are you working on today?
- Any blockers?
```

### 2. Code Review Process
```
1. Developer creates feature branch
2. Implements feature with tests
3. Creates Pull Request
4. Another team member reviews
5. Merge after approval
```

### 3. Git Branch Strategy
```
main
├── dev (integration branch)
    ├── feature/auth-system (John)
    ├── feature/member-api (Jane)
    ├── feature/qr-code (Bob)
    └── feature/database-models (Alice)
```

## Week-by-Week Task Distribution

### Week 1 (Nov 21-28): Foundation
| Developer | Skill | Primary Task | Backup Task |
|-----------|-------|--------------|-------------|
| Dev 1 | Advanced | Project setup, Flask structure | Docker config |
| Dev 2 | Intermediate | JWT Authentication | User model |
| Dev 3 | Intermediate | Database schema implementation | Migrations |
| Dev 4 | Beginner | Member model & validation | Sample data |
| Dev 5 | Beginner | Event model & validation | README updates |

### Week 2 (Nov 29-Dec 5): Core Features
| Developer | Skill | Primary Task | Backup Task |
|-----------|-------|--------------|-------------|
| Dev 1 | Advanced | Requirements engine | Performance optimization |
| Dev 2 | Intermediate | QR code generation & check-in | Attendance API |
| Dev 3 | Intermediate | Event CRUD API | Member CRUD API |
| Dev 4 | Beginner | CSV import/export | Data validation |
| Dev 5 | Beginner | Check-in form HTML | Bootstrap styling |

### Week 3 (Dec 6-12): Integration & Testing
| Developer | Skill | Primary Task | Backup Task |
|-----------|-------|--------------|-------------|
| Dev 1 | Advanced | API integration & optimization | Deployment setup |
| Dev 2 | Intermediate | Testing suite | Bug fixes |
| Dev 3 | Intermediate | Admin dashboard | Reports API |
| Dev 4 | Beginner | API documentation | User guide |
| Dev 5 | Beginner | Manual testing | Data cleanup |

## Communication Channels

### Slack/Discord Structure
```
#general - Team announcements
#dev-questions - Technical questions
#code-review - PR notifications
#standup - Daily standup notes
#resources - Learning materials
```

### Documentation Requirements
Each developer must:
1. Comment complex code sections
2. Update API documentation for new endpoints
3. Write basic tests for their features
4. Document any setup/configuration changes

## Learning Resources for Beginners

### Flask Basics
- [Flask Official Tutorial](https://flask.palletsprojects.com/tutorial/)
- [Flask-SQLAlchemy Docs](https://flask-sqlalchemy.palletsprojects.com/)
- [JWT Authentication Guide](https://realpython.com/token-based-authentication-with-flask/)

### Python Best Practices
- Use type hints where possible
- Follow PEP 8 style guide
- Write docstrings for all functions
- Keep functions small and focused

### SQL & Database
- [SQLAlchemy ORM Tutorial](https://docs.sqlalchemy.org/tutorial/)
- Practice queries with the schema
- Understand relationships and joins

## Code Quality Standards

### Before Committing Code:
```python
# 1. Run linter
flake8 .

# 2. Run formatter
black .

# 3. Run tests
pytest

# 4. Check coverage
pytest --cov=app
```

### Pull Request Template
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Unit tests pass
- [ ] Manual testing completed
- [ ] No linting errors

## Screenshots (if applicable)
```

## Handling Mixed Skill Levels

### Pairing Strategies
1. **Expert-Novice**: For learning (1 advanced + 1 beginner)
2. **Peer Programming**: For problem-solving (2 intermediates)
3. **Mob Programming**: For complex features (whole team)

### Knowledge Sharing
- **Tech Talks**: 30-min sessions where someone explains a concept
- **Code Walkthroughs**: Review complex implementations together
- **Documentation Days**: Dedicate time to write guides

### Support System
- **Mentor Assignments**: Each beginner paired with intermediate/advanced
- **Office Hours**: Set times for questions (e.g., 6-7 PM daily)
- **Shared Learning**: Document solutions to common problems

## Risk Mitigation

### If Someone Gets Stuck:
1. Try for 30 minutes independently
2. Ask in #dev-questions channel
3. Pair program if still stuck
4. Escalate to team lead if blocking others

### If Behind Schedule:
1. Identify critical vs nice-to-have features
2. Redistribute tasks based on complexity
3. Consider pair programming to speed up
4. Focus on MVP functionality first

## Success Metrics

### Individual:
- Complete assigned tasks on time
- Help at least one teammate per week
- Contribute to documentation
- Participate in code reviews

### Team:
- Daily standup attendance
- Code coverage > 70%
- All critical features completed
- API documentation complete

## Important Reminders

1. **Communication is Key**: Over-communicate rather than under-communicate
2. **Ask Questions**: No question is too simple
3. **Document Everything**: Future you will thank current you
4. **Test Early**: Don't wait until the end to test
5. **Help Each Other**: Team success > individual success
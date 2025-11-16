---
name: story-writing
description: Use when writing user stories and development tasks. Provides structure, formatting, and best practices for creating clear, actionable user stories following BMAD methodology.
---

# Story Writing Skill

## User Story Format

### Standard Structure
```
As a [user persona]
I want [capability/feature]
So that [business value/benefit]
```

### Examples

**Good**:
```
As a premium subscriber
I want to export my data to CSV
So that I can analyze my usage patterns in Excel
```

**Bad**:
```
As a user
I want a button
So that I can click it
```

Why bad: Vague persona, no clear value, focused on implementation not outcome

## Acceptance Criteria

### GIVEN-WHEN-THEN Format
```
Given [initial context]
When [specific action]
Then [expected outcome]
```

### Example
```
Given I am logged in as a premium subscriber
When I click "Export Data" and select "CSV format"
Then a CSV file downloads within 5 seconds containing my last 90 days of data
```

### Best Practices for AC
- Be specific and testable
- Include happy path and edge cases
- Define performance criteria
- Specify error handling
- Cover security requirements
- Include all user-visible behaviors

## Story Sizing

### Story Points vs Time

**Small Story (1-2 days)**:
- Single API endpoint
- Simple UI component
- Configuration change
- Straightforward integration

**Medium Story (2-3 days)**:
- Feature with multiple endpoints
- Complex UI workflow
- External service integration
- Database schema with migration

**Large Story (>3 days)**:
- Should be split into smaller stories
- Multiple related features
- Complex system changes

### INVEST Criteria

Stories should be:
- **Independent**: Can be developed separately
- **Negotiable**: Details can be discussed
- **Valuable**: Delivers user/business value
- **Estimable**: Can be sized
- **Small**: Fits in sprint
- **Testable**: Clear acceptance criteria

## Story Dependencies

### Dependency Types

**Technical Dependencies**:
```
STORY-002 depends on STORY-001
Reason: Requires authentication middleware from STORY-001
```

**Business Dependencies**:
```
STORY-005 depends on STORY-003, STORY-004
Reason: Payment flow needs both user management and product catalog
```

### Minimizing Dependencies
- Design for independent deployment when possible
- Use feature flags for gradual rollout
- Create infrastructure stories first
- Sequence stories logically

## Story Components (BMAD Standard)

### 1. Story Header
```markdown
# Story: OAuth2 Google Integration

**Story ID**: STORY-001
**Epic**: Authentication System
**Priority**: High
**Estimated Effort**: 2 days
**Dependencies**: None
```

### 2. User Story
Standard As a/I want/So that format

### 3. Business Context
Relevant PRD context explaining why this matters:
- Business goals
- User impact
- Success metrics
- Background information

### 4. Acceptance Criteria
Complete list of testable criteria:
- Functional requirements
- Edge cases
- Performance requirements
- Security requirements
- Error handling

### 5. Technical Context
- Architecture decisions
- Component specifications
- Data models
- API contracts

### 6. Implementation Details
- Step-by-step approach
- Code examples
- File structure
- Configuration
- Dependencies to install

### 7. Architectural Guidance
- Patterns to follow
- Anti-patterns to avoid
- Best practices
- Security considerations

### 8. Integration Points
- Dependencies on other stories
- External system integrations
- APIs to call
- Events to publish/consume

### 9. Testing Strategy
- Unit test cases
- Integration tests
- Edge case tests
- Performance tests

### 10. Definition of Done
Complete checklist:
- Implementation complete
- Tests written and passing
- Code reviewed
- Documentation updated
- Deployed to staging
- Acceptance criteria verified

## Story Templates

### API Endpoint Story
```markdown
# Story: Create User API Endpoint

As a frontend developer
I want a POST /api/users endpoint
So that I can create new user accounts

## Acceptance Criteria
- AC1: POST /api/users accepts email, password, name
- AC2: Returns 201 with user object on success
- AC3: Returns 400 if email already exists
- AC4: Returns 400 if email format invalid
- AC5: Password hashed before storage
- AC6: Response includes user_id, email, created_at
- AC7: Request rate limited to 10/minute per IP

## Technical Context
Endpoint: POST /api/users
Request:
{
  "email": "user@example.com",
  "password": "securepass123",
  "name": "John Doe"
}
Response 201:
{
  "user_id": "uuid",
  "email": "user@example.com",
  "name": "John Doe",
  "created_at": "2025-01-15T10:00:00Z"
}

## Implementation Details
[Code examples, file structure, etc.]
```

### UI Component Story
```markdown
# Story: User Profile Card Component

As a user
I want to view my profile information
So that I can verify my account details

## Acceptance Criteria
- AC1: Displays user avatar, name, email, join date
- AC2: Renders responsively on mobile and desktop
- AC3: Edit button visible only for own profile
- AC4: Loading state shows skeleton
- AC5: Error state shows friendly message
- AC6: Accessible (ARIA labels, keyboard navigation)

## Technical Context
Component: ProfileCard
Props: userId, editable
State: user data, loading, error

## Implementation Details
[React code example, CSS, tests]
```

## Story Refinement

### When to Refine
- Validation issues found
- Scope too large
- Requirements clarified
- Architecture changed
- Feedback received

### Refinement Process
1. Identify what needs to change
2. Update relevant sections
3. Maintain story intent
4. Re-validate
5. Document refinement history

## Story Anti-Patterns

**Avoid These**:
- ❌ Technical tasks masquerading as stories ("Refactor service layer")
- ❌ Vague acceptance criteria ("Should work well")
- ❌ Missing business value
- ❌ Too large to complete in sprint
- ❌ Unclear dependencies
- ❌ No testing strategy
- ❌ Missing error handling
- ❌ Referencing external docs instead of embedding context

## Story Quality Checklist

- [ ] Clear user story (As a/I want/So that)
- [ ] Specific, testable acceptance criteria
- [ ] Business context provided
- [ ] Technical approach defined
- [ ] Implementation details complete
- [ ] Code examples included
- [ ] Testing strategy defined
- [ ] Definition of done comprehensive
- [ ] Dependencies identified
- [ ] Story is independently deployable
- [ ] All context embedded (no external lookups)

---
name: story-refine
description: Refine and enhance existing development stories based on feedback or validation issues
---

# Refine Development Stories

Enhance or update existing development stories to address validation issues, incorporate feedback, or add missing details.

## What This Command Does

Uses the **scrum-master** agent to refine existing stories by:
- Addressing validation issues from story-validator
- Incorporating stakeholder feedback
- Adding missing implementation details
- Updating based on architecture changes
- Splitting large stories into smaller ones

## Usage

```bash
# Refine specific story
/agile-management:story-refine "STORY-001"

# Refine based on validation issues
/agile-management:story-refine "STORY-001" --fix-validation

# Add more detail to story
/agile-management:story-refine "STORY-003" --enhance-details

# Split story into smaller stories
/agile-management:story-refine "STORY-005" --split 3

# Update story based on architecture changes
/agile-management:story-refine "STORY-002" --sync-architecture
```

## Common Refinement Scenarios

### 1. Fix Validation Issues

When story-validator identifies critical or major issues:

```bash
/agile-management:story-refine "STORY-001" --fix-validation
```

Agent will:
- Read validation report
- Address each identified issue
- Add missing API contracts
- Complete error handling details
- Enhance test coverage
- Re-validate automatically

### 2. Incorporate Feedback

After stakeholder review:

```bash
/agile-management:story-refine "STORY-002" --feedback "Need to handle edge case where user has multiple active sessions"
```

Agent will:
- Incorporate feedback into story
- Update acceptance criteria
- Add implementation details for edge case
- Update testing strategy

### 3. Enhance Implementation Details

When developers need more guidance:

```bash
/agile-management:story-refine "STORY-003" --enhance-details
```

Agent will:
- Add more code examples
- Provide additional architectural context
- Include more specific configuration details
- Expand testing scenarios

### 4. Split Large Stories

When story is too big (>3 days):

```bash
/agile-management:story-refine "STORY-005" --split 3
```

Agent will:
- Analyze story scope
- Identify logical split points
- Create 3 smaller stories
- Maintain dependencies
- Ensure each is independently deployable

### 5. Sync with Architecture Updates

When architecture documentation changes:

```bash
/agile-management:story-refine "STORY-004" --sync-architecture
```

Agent will:
- Re-read latest architecture docs
- Update technical approach if needed
- Align patterns with current architecture
- Update API specifications
- Maintain story intent

## Refinement Output

### Original Story Issues
```markdown
# Story: OAuth2 Integration

❌ Missing API contract specification
❌ Incomplete error handling
⚠️ Could use more test examples
```

### After Refinement
```markdown
# Story: OAuth2 Integration

✅ Complete API contract with OpenAPI spec
✅ Comprehensive error handling with retry logic
✅ Multiple test examples covering edge cases
✅ Re-validated: PASS
```

## Output Location

```
stories/backlog/
├── story-001-oauth-setup.md          ← Updated
├── story-001-validation-report.md    ← New validation
├── story-001-refinement-history.md   ← Refinement log
```

## Refinement History

Each refinement is logged:

```markdown
# Refinement History: STORY-001

## Refinement 1 - 2025-01-15
**Reason**: Fix validation issues
**Changes**:
- Added complete API contract specification
- Enhanced error handling details
- Added integration test examples

## Refinement 2 - 2025-01-16  
**Reason**: Stakeholder feedback
**Changes**:
- Added multi-session handling edge case
- Updated acceptance criteria
- Expanded security considerations
```

## Best Practices

### When to Refine

**Do Refine When**:
- ✅ Validation reports show critical/major issues
- ✅ Stakeholders provide specific feedback
- ✅ Developers need more implementation guidance
- ✅ Story is too large to implement in one sprint
- ✅ Architecture changes affect the story

**Don't Refine When**:
- ❌ Story is already clear and actionable
- ❌ Issues are minor formatting/style
- ❌ Change requires new PRD/architecture
- ❌ Scope change is too significant (create new story instead)

### Refinement Triggers

| Validation Status | Action |
|------------------|--------|
| Critical Issues | **Must** refine before development |
| Major Issues | **Should** refine for better clarity |
| Minor Issues | **Optional** refinement |
| All Pass | No refinement needed |

## Integration with Workflow

```
Story Generation
   ↓
Story Validation
   ↓
Issues Found? ──Yes──> Story Refinement ──┐
   │                         ↓             │
   No                   Re-validation      │
   │                         ↓             │
   │                   Issues Fixed? ──No──┘
   │                         │
   └────────Yes──────────────┘
                ↓
          Ready for Dev
```

## Example Refinement Sessions

### Example 1: Fix API Contract

**Before**:
```markdown
## Technical Context
Implement OAuth2 flow
```

**After Refinement**:
```markdown
## Technical Context

### OAuth2 Flow
Authorization Code flow with PKCE extension

### API Endpoints

**Authorization Endpoint**:
```http
GET /oauth/authorize
Query Parameters:
  - client_id: string (required)
  - redirect_uri: string (required)
  - state: string (required)
  - code_challenge: string (required)
  - code_challenge_method: "S256"
Response: 302 Redirect to consent page
```

**Token Endpoint**:
```http
POST /oauth/token
Request Body:
{
  "grant_type": "authorization_code",
  "code": "string",
  "code_verifier": "string",
  "client_id": "string"
}
Response: 200 OK
{
  "access_token": "string",
  "token_type": "Bearer",
  "expires_in": 3600,
  "refresh_token": "string"
}
```
```

### Example 2: Split Large Story

**Original**: STORY-005 (5 days)
```
Implement complete payment processing system
```

**After Split**:
- STORY-005a (2 days): Payment provider integration (Stripe API)
- STORY-005b (2 days): Payment method management (CRUD)
- STORY-005c (1 day): Webhook handling and event processing

Each story is independently deployable with complete context.

## Validation After Refinement

After refinement, story is automatically re-validated:

```
Refinement Complete
   ↓
Auto Re-validation
   ↓
New Validation Report
   ↓
Pass? ──Yes──> Ready for Development
   │
   No
   ↓
Review Issues & Consider Further Refinement
```

## Tips

1. **Address Critical Issues First**: Focus on blockers
2. **Keep Changes Scoped**: Don't change story intent
3. **Maintain History**: Track all refinements
4. **Re-validate**: Always run validation after refinement
5. **Communicate**: Share refined stories with team

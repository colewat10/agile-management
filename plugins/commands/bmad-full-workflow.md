---
name: bmad-full-workflow
description: Execute complete BMAD workflow orchestrating all phases from PRD through validated stories
---

# BMAD Full Workflow

Execute the complete BMAD (Build-Measure-Adapt-Deploy) workflow, orchestrating all agents from initial planning through context-engineered development stories.

## What This Command Does

Runs the complete two-phase BMAD methodology:

**Phase 1: Agentic Planning**
1. product-planner (Sonnet) → Create comprehensive PRD
2. architecture-designer (Sonnet) → Create detailed architecture

**Phase 2: Context-Engineered Development**
3. scrum-master (Sonnet) → Generate hyper-detailed stories
4. story-validator (Haiku) → Validate story completeness

## Usage

```bash
# Full workflow from scratch
/agile-management:bmad-full-workflow "user authentication with OAuth2 and MFA"

# With specific configuration
/agile-management:bmad-full-workflow "payment processing" --story-count 8 --epic "payments-v2"

# Resume from specific phase
/agile-management:bmad-full-workflow "real-time chat" --from-architecture
```

## Workflow Orchestration

```
┌─────────────────────────────────────┐
│  Phase 1: Agentic Planning          │
├─────────────────────────────────────┤
│                                     │
│  1. product-planner (Sonnet)       │
│     └─> Create comprehensive PRD    │
│         ├─ Business requirements    │
│         ├─ Success metrics          │
│         ├─ User stories             │
│         └─ Risk assessment          │
│                                     │
│  2. architecture-designer (Sonnet) │
│     └─> Create architecture docs    │
│         ├─ System architecture      │
│         ├─ Component design         │
│         ├─ Data models              │
│         ├─ API specifications       │
│         └─ Technical decisions      │
│                                     │
└─────────────────────────────────────┘
           ↓
┌─────────────────────────────────────┐
│  Phase 2: Context-Engineered Dev    │
├─────────────────────────────────────┤
│                                     │
│  3. scrum-master (Sonnet)          │
│     └─> Generate detailed stories   │
│         ├─ Business context         │
│         ├─ Technical context        │
│         ├─ Implementation details   │
│         ├─ Code examples            │
│         └─ Testing strategy         │
│                                     │
│  4. story-validator (Haiku)        │
│     └─> Validate each story         │
│         ├─ Completeness check       │
│         ├─ PRD alignment            │
│         ├─ Architecture consistency │
│         └─ Actionability assessment │
│                                     │
└─────────────────────────────────────┘
```

## Output Structure

```
project-root/
├── docs/
│   └── planning/
│       ├── prds/
│       │   └── {feature}-prd-v1.0.md
│       └── architecture/
│           └── {feature}-architecture-v1.0.md
└── stories/
    └── backlog/
        ├── story-001-{name}.md
        ├── story-001-validation-report.md
        ├── story-002-{name}.md
        ├── story-002-validation-report.md
        └── ...
```

## Example Usage

```bash
/agile-management:bmad-full-workflow "multi-tenant SaaS authentication with SSO, OAuth2, and RBAC"
```

**Workflow Execution**:

1. **product-planner** creates PRD with:
   - Multi-tenancy requirements
   - Authentication methods
   - Authorization model (RBAC)
   - Security and compliance requirements
   - Success metrics

2. **architecture-designer** creates architecture with:
   - Tenant isolation strategy
   - OAuth2 implementation approach
   - SSO integration patterns
   - RBAC data model and enforcement
   - Security architecture

3. **scrum-master** generates stories like:
   - STORY-001: Tenant schema and isolation
   - STORY-002: OAuth2 provider setup
   - STORY-003: SSO integration framework
   - STORY-004: RBAC policy engine
   - STORY-005: User and role management
   - Each with complete context and implementation details

4. **story-validator** validates each story:
   - Checks completeness
   - Verifies PRD alignment
   - Confirms architecture consistency
   - Generates validation reports

## Benefits

### Eliminates Planning Inconsistency
- Single PRD as source of truth
- Comprehensive architecture upfront
- Consistent technical approach across stories

### Eliminates Context Loss
- Complete context embedded in each story
- No documentation hunting during development
- Full implementation guidance in stories
- Developers have complete understanding

### Streamlines Development
- Stories are immediately actionable
- Clear technical direction
- Reduced back-and-forth
- Faster onboarding for new developers

## Configuration Options

```bash
# Specify number of stories
--story-count 10

# Set story size preference
--story-size "small"  # 1-2 days each
--story-size "medium" # 2-3 days each

# Define epic
--epic "authentication-v2"

# Set priority
--priority "high"

# Resume from specific phase
--from-architecture  # Skip PRD creation
--from-stories       # Skip PRD and architecture
```

## Workflow Checkpoints

The workflow pauses for human review at:

1. **After PRD Creation**
   - Review and approve PRD
   - Provide feedback
   - Continue or iterate

2. **After Architecture Creation**
   - Review technical approach
   - Validate technology decisions
   - Continue or refine

3. **After Story Generation**
   - Review all stories
   - Check validation reports
   - Address critical issues

## Quality Gates

Each phase has quality checks:

**Phase 1**:
- PRD completeness
- Architecture comprehensiveness
- Consistency between PRD and architecture

**Phase 2**:
- Story completeness (all required sections)
- PRD alignment (requirements met)
- Architecture consistency (patterns followed)
- Actionability (no missing context)

## Timeline

Typical execution time:

| Phase | Agent | Duration |
|-------|-------|----------|
| PRD Creation | product-planner | 5-10 min |
| Architecture Design | architecture-designer | 10-15 min |
| Story Generation | scrum-master | 15-25 min |
| Story Validation | story-validator | 5-10 min |
| **Total** | | **35-60 min** |

## Next Steps After Workflow

1. **Review All Artifacts**
   - Read PRD, architecture, stories
   - Check validation reports

2. **Address Critical Issues**
   - Fix any critical validation failures
   - Refine stories as needed

3. **Start Development**
   - Move stories to `stories/active/`
   - Begin implementation with full context

4. **Iterate as Needed**
   - Update PRD/architecture based on learnings
   - Regenerate affected stories

## Comparison to Traditional Approach

### Traditional Approach Problems:
- ❌ Vague requirements → rework
- ❌ Missing technical details → guesswork  
- ❌ Context scattered across docs → hunting
- ❌ Inconsistent understanding → conflicts
- ❌ Frequent clarification needed → delays

### BMAD Workflow Solution:
- ✅ Comprehensive requirements → clarity
- ✅ Complete technical specs → confidence
- ✅ Context embedded → autonomy
- ✅ Single source of truth → consistency
- ✅ Self-contained stories → velocity

## Tips for Success

1. **Provide Rich Context**: More context = better output
2. **Review Iteratively**: Pause and review at checkpoints
3. **Refine as Needed**: Don't hesitate to iterate
4. **Trust the Process**: Let agents do deep work
5. **Use Validation**: Fix critical issues before development

## Example Output Quality

**Traditional Story**:
```
As a user, I want to login so I can access the app.

Acceptance Criteria:
- User can login
- Error handling
```

**BMAD Story**:
```
As a user, I want to authenticate using OAuth2 with Google
so that I can securely access my account without managing passwords.

Business Context: [Full PRD context explaining why OAuth2...]

Acceptance Criteria: [10+ specific testable criteria]

Technical Context:
- OAuth2 flow: Authorization Code with PKCE
- Token storage: HttpOnly cookies + Redis session
- [Complete data models, API specs...]

Implementation Details:
1. Setup OAuth2 client with Google
2. Implement authorization endpoint
   [Concrete code example with actual library usage]
3. Token exchange and validation
   [Complete implementation pattern]
...

[Testing strategy with actual test code]
[Definition of done with 12 checkpoints]
```

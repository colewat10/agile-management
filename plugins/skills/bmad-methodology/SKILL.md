---
name: bmad-methodology
description: Use when implementing the BMAD method for agile project management. Core principles of two-phase agentic planning and context-engineered development to eliminate planning inconsistency and context loss.
---

# BMAD Methodology Skill

## Overview

BMAD (Build-Measure-Adapt-Deploy) is a revolutionary two-phase approach to agile development that eliminates the two biggest problems in AI-assisted development:

1. **Planning Inconsistency**: Solved by Phase 1 agentic planning
2. **Context Loss**: Solved by Phase 2 context-engineered development

## Phase 1: Agentic Planning

### Purpose
Create detailed, consistent PRDs and architecture documents through advanced prompt engineering and human-in-the-loop refinement.

### Key Principles

**Comprehensive Over Generic**
- Go far beyond generic AI task generation
- Every aspect defined before development begins
- Single source of truth across all planning docs
- Complete requirements capture upfront

**Consistency Through Depth**
- Detailed functional requirements
- Complete non-functional requirements
- Clear success criteria and metrics
- Risk identification and mitigation
- Comprehensive architecture specifications

**Human-in-the-Loop Refinement**
- Iterative improvement with stakeholder feedback
- Review checkpoints at each stage
- Refinement based on real-world constraints
- Validation against business objectives

### Outputs

**1. Product Requirements Document (PRD)**
Structure:
- Executive summary
- Problem statement with quantified impact
- Goals, objectives, and success metrics
- User personas and use cases
- Detailed functional requirements
- Non-functional requirements (performance, security, scalability)
- Technical constraints
- Timeline and milestones
- Dependencies and risks
- Out of scope items

Quality Standards:
- Specific and measurable requirements
- Clear acceptance criteria for each requirement
- Quantifiable success metrics
- Complete edge case coverage
- Explicit assumptions documented

**2. Architecture Documentation**
Structure:
- Executive summary
- Requirements summary
- High-level architecture with diagrams
- Detailed component design
- Data architecture and models
- API specifications (REST/GraphQL/gRPC)
- Security architecture
- Performance and scalability approach
- Technology stack with rationale
- Technical decisions and trade-offs
- Implementation patterns
- Testing strategy

Quality Standards:
- Complete technical specifications
- All major decisions documented with rationale
- Concrete implementation patterns
- Code examples for key patterns
- Clear component boundaries and interfaces
- Security and performance patterns defined

## Phase 2: Context-Engineered Development

### Purpose
Transform detailed plans into hyper-detailed development stories where ALL context is embedded directly in story files.

### Key Principles

**Hyper-Detail Over Brevity**
- Stories contain everything needed for implementation
- No external documentation lookup required
- Complete implementation roadmap in each story
- Concrete code examples, not pseudocode

**Context Embedding Over Referencing**
- Embed relevant PRD sections directly in stories
- Include applicable architecture decisions inline
- Copy data models and API specs into stories
- Provide complete configuration details in stories

**Implementation Guidance Over Requirements**
- Step-by-step technical approach
- Specific libraries and frameworks to use
- Code patterns with concrete examples
- File structure and organization specified
- Error handling patterns defined

**Testing Strategy Included**
- Specific unit test cases
- Integration test scenarios
- Edge case handling
- Performance test requirements

### Story Structure

**Required Sections**:
1. **User Story**: As a/I want/So that format
2. **Business Context**: Extracted from PRD
3. **Acceptance Criteria**: Complete, testable criteria
4. **Technical Context**: Architecture decisions, data models, APIs
5. **Implementation Details**: Step-by-step approach with code
6. **Architectural Guidance**: Patterns to follow, anti-patterns to avoid
7. **Integration Points**: Dependencies and external systems
8. **Testing Strategy**: Specific test cases and approach
9. **Definition of Done**: Complete checklist

**Embedded Context Includes**:
- Relevant PRD requirements
- Applicable architecture patterns
- Complete data schemas
- Full API specifications
- Configuration requirements
- Security considerations
- Performance requirements

## Benefits of BMAD

### Eliminates Planning Inconsistency

**Problem Solved**:
- Generic requirements lead to rework
- Incomplete architecture causes confusion
- Inconsistent understanding across team
- Missing details discovered during development

**BMAD Solution**:
- Comprehensive upfront planning
- Single detailed source of truth
- Consistent technical approach
- Complete specifications before coding

### Eliminates Context Loss

**Problem Solved**:
- Context scattered across multiple docs
- Developers hunt for information
- Architectural decisions not clear
- Implicit knowledge not captured

**BMAD Solution**:
- All context embedded in stories
- Developers have complete understanding
- Architectural guidance in every story
- No external documentation needed

### Enables Autonomous Development

**Result**:
- Developers can implement without constant clarification
- Clear technical direction in every story
- Reduced back-and-forth communication
- Faster onboarding for new team members
- Higher quality implementations
- Consistent code patterns across team

## BMAD Workflow

```
Phase 1: Agentic Planning
   ↓
1. product-planner (Sonnet)
   └─> Comprehensive PRD
       ├─ Business requirements
       ├─ Success metrics
       ├─ User stories
       └─ Risk assessment
   ↓
2. architecture-designer (Sonnet)
   └─> Detailed architecture
       ├─ System architecture
       ├─ Component design
       ├─ Data models & APIs
       └─ Technical decisions

Phase 2: Context-Engineered Development
   ↓
3. scrum-master (Sonnet)
   └─> Hyper-detailed stories
       ├─ Business context embedded
       ├─ Technical context embedded
       ├─ Implementation details
       └─ Code examples
   ↓
4. story-validator (Haiku)
   └─> Validation & QA
       ├─ Completeness check
       ├─ PRD alignment
       ├─ Architecture consistency
       └─ Actionability assessment
   ↓
Ready for Autonomous Development
```

## Model Selection Strategy

### Phase 1 (Planning): Sonnet
- **product-planner**: Complex requirement analysis
- **architecture-designer**: Sophisticated technical design

**Rationale**: Planning requires deep reasoning, trade-off analysis, and comprehensive thinking

### Phase 2 (Development): Mixed
- **scrum-master**: Sonnet for complex context synthesis
- **story-validator**: Haiku for efficient quality control

**Rationale**: Story creation needs deep synthesis, validation is straightforward checklist-based

## Best Practices

### For PRDs
1. **Start with Problems, Not Solutions**
   - Articulate user pain points clearly
   - Quantify impact of problems
   - Define who is affected

2. **Be Quantifiable**
   - Use specific metrics for success
   - Define measurable acceptance criteria
   - Set concrete performance targets

3. **Document Edge Cases Early**
   - Think through error scenarios
   - Consider boundary conditions
   - Plan for failure modes

4. **Make Assumptions Explicit**
   - Document all assumptions
   - Note areas of uncertainty
   - Identify validation needed

### For Architecture
1. **Justify All Decisions**
   - Document why, not just what
   - Consider alternatives
   - Note trade-offs explicitly

2. **Provide Concrete Patterns**
   - Include code examples
   - Show actual implementations
   - Define specific libraries/frameworks

3. **Plan for Non-Functionals**
   - Security patterns upfront
   - Performance considerations early
   - Scalability approach defined

4. **Define Clear Boundaries**
   - Component responsibilities explicit
   - Interface contracts complete
   - Integration points specified

### For Stories
1. **Embed All Context**
   - Copy relevant sections, don't reference
   - Include complete schemas and APIs
   - Provide full configuration details

2. **Show, Don't Tell**
   - Concrete code examples
   - Actual patterns, not descriptions
   - Specific library usage

3. **Plan Testing Upfront**
   - Define test cases in story
   - Include edge cases to test
   - Specify performance tests

4. **Make It Self-Contained**
   - Developer needs nothing else to implement
   - All decisions already made
   - Clear path from story to code

## Anti-Patterns to Avoid

### Planning Anti-Patterns
- ❌ Vague requirements ("should be fast")
- ❌ Missing success metrics
- ❌ Unclear scope boundaries
- ❌ Undocumented assumptions
- ❌ Generic architecture ("use best practices")
- ❌ Technology choices without rationale

### Story Anti-Patterns
- ❌ Referencing external docs ("see PRD section 3")
- ❌ Vague technical approach ("use standard pattern")
- ❌ Missing code examples
- ❌ Incomplete schemas/APIs
- ❌ No error handling specified
- ❌ Unclear dependencies
- ❌ Testing strategy missing

## Success Criteria

### Phase 1 Success
PRD and Architecture are complete when:
- ✅ All requirements captured and specified
- ✅ Success metrics defined and measurable
- ✅ Architecture covers all requirements
- ✅ All major technical decisions made
- ✅ Patterns and standards defined
- ✅ No significant unknowns remain

### Phase 2 Success
Stories are ready when:
- ✅ Developer can implement without questions
- ✅ All context embedded (no external lookup)
- ✅ Specific technical approach defined
- ✅ Code examples provided
- ✅ Testing strategy complete
- ✅ Validation passes all checks
- ✅ Definition of done is comprehensive

## Metrics for BMAD Effectiveness

**Planning Quality**:
- Requirements clarity (survey developers)
- Architecture completeness (coverage of requirements)
- Planning rework rate (changes needed)

**Development Velocity**:
- Story implementation time
- Clarification requests per story
- Rework due to missing context

**Quality Outcomes**:
- Defect rate
- Pattern consistency
- Code review feedback volume

## When to Use BMAD

**Ideal For**:
- ✅ New features requiring comprehensive planning
- ✅ Complex technical implementations
- ✅ Projects with multiple developers
- ✅ Features with significant architecture decisions
- ✅ Teams wanting to reduce context-switching
- ✅ Projects requiring consistency across stories

**Less Ideal For**:
- ⚠️ Simple bug fixes
- ⚠️ Minor UI tweaks
- ⚠️ Emergency hotfixes
- ⚠️ Exploratory prototyping (use for production version)

## BMAD in Practice

### Story Quality Comparison

**Traditional Story**:
```
As a user, I want to login with OAuth2
so that I can access my account.

Acceptance Criteria:
- User can login
- Errors handled
```

**BMAD Story**:
```
As a user, I want to authenticate using OAuth2 with Google
so that I can securely access my account without managing passwords.

Business Context:
[Full context from PRD explaining why OAuth2, security requirements,
user research findings, competitive analysis, and impact metrics]

Acceptance Criteria:
- AC1: User clicks "Login with Google" and is redirected to Google OAuth consent
- AC2: After Google consent, user is redirected back with authorization code
- AC3: System exchanges code for access token within 5 seconds
- AC4: User session created with 24-hour expiry
- AC5: Failed auth shows user-friendly error message
- AC6: Rate limiting prevents brute force (max 5 attempts/minute)
- AC7: All OAuth flows logged for security audit
- AC8: Works across desktop and mobile browsers
- AC9: Handles network failures gracefully with retry
- AC10: CSRF protection implemented

Technical Context:
OAuth2 Authorization Code Flow with PKCE
- Provider: Google OAuth 2.0
- Token Storage: HttpOnly secure cookies + Redis session
- PKCE for mobile security

[Complete data models for User, Session, OAuth Token]
[Full API specifications for all endpoints]
[Security patterns from architecture doc]

Implementation Details:
1. Setup OAuth2 Client
   npm install passport passport-google-oauth20
   
2. Configure Passport Strategy
   [Complete code example with actual config]

3. Implement Authorization Flow
   [Step-by-step with code for each endpoint]

4. Token Management
   [Redis integration code]

5. Error Handling
   [Specific error scenarios with handling code]

[Complete testing strategy with actual test code]
[Definition of done with 15 specific checkpoints]
```

## Conclusion

BMAD methodology transforms agile development by:
1. Creating comprehensive, consistent plans (Phase 1)
2. Embedding complete context in stories (Phase 2)
3. Enabling autonomous, informed development
4. Eliminating planning inconsistency and context loss

The result: Faster development, higher quality, and happier developers who have everything they need to succeed.

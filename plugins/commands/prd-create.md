---
name: prd-create
description: Create a comprehensive Product Requirements Document using the product-planner agent
---

# Create Product Requirements Document

Generate a comprehensive, detailed PRD (Product Requirements Document) following the BMAD methodology using the product-planner agent.

## What This Command Does

Invokes the **product-planner** agent (Sonnet model) to create a detailed PRD that serves as the foundation for architecture design and development stories. The PRD will include:

- Executive summary and problem statement
- Business goals and success metrics
- User personas and use cases
- Comprehensive functional requirements
- Non-functional requirements
- Technical constraints
- Timeline and dependencies
- Risk assessment

## Usage

```bash
# Basic usage
/agile-management:prd-create "real-time chat with WebSocket support"

# With more context
/agile-management:prd-create "OAuth2 authentication with Google, GitHub, and Azure AD integration for multi-tenant SaaS platform"

# For a specific epic
/agile-management:prd-create "payment processing subsystem with Stripe, PayPal, and cryptocurrency support"
```

## Command Flow

1. **Context Gathering**: Agent asks clarifying questions about:
   - Business objectives and goals
   - Target users and personas
   - Technical constraints
   - Success criteria
   - Integration requirements

2. **PRD Generation**: Creates comprehensive PRD with:
   - Clear problem definition
   - Detailed requirements
   - Success metrics
   - Risk assessment

3. **PRD Storage**: Saves PRD to `docs/planning/prds/` directory:
   - Filename: `{feature-name}-prd-v{version}.md`
   - Version tracked in `.bmad/config.yaml`

4. **Next Steps**: Suggests running architecture creation:
   ```
   /agile-management:architecture-create "{feature-name}"
   ```

## PRD Output Structure

The generated PRD follows this comprehensive structure:

```markdown
# Product Requirements Document: {Feature Name}

## Executive Summary
- Feature overview
- Business justification
- Expected impact

## Problem Statement
- Current state and pain points
- Affected users
- Quantified impact
- Strategic importance

## Goals & Objectives
- Business goals
- User goals  
- Success metrics and KPIs

## User Personas & Use Cases
- Primary personas
- User stories
- Workflows and scenarios

## Functional Requirements
### Core Features
- FR-001: Requirement with acceptance criteria
- FR-002: Another requirement...

### User Experience Requirements
### Data Requirements
### Integration Requirements

## Non-Functional Requirements
- Performance requirements
- Security requirements
- Scalability requirements
- Reliability requirements
- Compliance requirements

## Technical Constraints
- Technology stack constraints
- Infrastructure requirements
- Compatibility requirements

## Success Metrics
- User engagement KPIs
- Business impact metrics
- Technical performance metrics

## Timeline & Milestones
- Project phases
- Key milestones
- Dependencies

## Risks & Mitigation
- Technical risks
- Business risks
- Mitigation strategies

## Out of Scope
- Excluded features
- Future considerations

## Appendices
- Research findings
- Mockups/wireframes
- Competitive analysis
```

## Agent Behavior

The **product-planner** agent will:

### Ask Clarifying Questions
- "What problem are we solving for users?"
- "What are the key success metrics?"
- "Are there any technical constraints I should know about?"
- "What's the expected timeline?"
- "Any compliance or regulatory requirements?"

### Provide Comprehensive Output
- Detailed functional requirements
- Edge cases and scenarios
- Clear acceptance criteria
- Quantifiable success metrics
- Risk assessment

### Follow BMAD Standards
- Single source of truth
- Comprehensive detail
- Clear and specific
- Actionable requirements

## Integration with BMAD Workflow

### This is Phase 1, Step 1
```
[You are here]
1. Create PRD ← /agile-management:prd-create
   ↓
2. Create Architecture → /agile-management:architecture-create
   ↓
3. Generate Stories → /agile-management:story-generate
   ↓
4. Validate Stories (automatic)
```

### Enables Next Steps
- **architecture-designer** uses the PRD to create technical architecture
- **scrum-master** extracts business context from PRD for stories
- **story-validator** checks stories against PRD requirements

## Examples

### Example 1: Real-Time Collaboration

```bash
/agile-management:prd-create "real-time document collaboration with operational transformation"
```

**Agent Output**: PRD covering:
- Collaborative editing requirements
- Conflict resolution approach
- User presence indicators
- Performance requirements (latency < 100ms)
- WebSocket infrastructure needs
- User permissions and access control

### Example 2: Authentication System

```bash
/agile-management:prd-create "OAuth2 authentication with social providers and MFA"
```

**Agent Output**: PRD covering:
- OAuth2 flow requirements
- Supported providers (Google, GitHub, etc.)
- Multi-factor authentication methods
- Session management requirements
- Security and compliance (OWASP, SOC2)
- User experience flows

### Example 3: Payment Processing

```bash
/agile-management:prd-create "payment gateway integration with subscription management"
```

**Agent Output**: PRD covering:
- Payment provider requirements
- Subscription lifecycle management
- Billing and invoicing
- PCI-DSS compliance
- Refund and dispute handling
- Revenue recognition

## Output Location

PRDs are saved to:
```
docs/planning/prds/{feature-name}-prd-v{version}.md
```

Version is tracked in `.bmad/config.yaml` and auto-incremented.

## Best Practices

### Provide Rich Context
**Good**: "OAuth2 authentication for multi-tenant SaaS with social login, MFA, and SSO support for enterprise customers"

**Not Good**: "add login"

### Be Specific About Requirements
- Mention performance needs: "handle 10,000 concurrent users"
- Note compliance: "HIPAA compliant data storage"
- Specify integrations: "integrate with Salesforce and HubSpot"

### Clarify Scope
- Mention what's in scope: "phase 1 includes Google and GitHub OAuth"
- Note what's out of scope: "SAML integration is future phase"

### Identify Constraints
- Technical: "must work with existing PostgreSQL database"
- Timeline: "needed for Q3 launch"
- Resources: "team of 3 engineers"

## Validation

After PRD creation, review for:
- [ ] Clear problem statement
- [ ] Comprehensive functional requirements
- [ ] Measurable success criteria
- [ ] Complete non-functional requirements
- [ ] Identified risks and mitigation
- [ ] Realistic timeline

## Next Steps After PRD

1. **Review with Stakeholders**: Share PRD for feedback
2. **Refine as Needed**: Update PRD based on feedback
3. **Create Architecture**: 
   ```
   /agile-management:architecture-create "{feature-name}"
   ```
4. **Or Run Full Workflow**:
   ```
   /agile-management:bmad-full-workflow "{feature-name}"
   ```

## Iterating on PRDs

To update an existing PRD:

```bash
# The agent will detect existing PRD and offer to:
# 1. Create new version
# 2. Update existing version
# 3. Create addendum

/agile-management:prd-create "user authentication" --version 2.0
```

## Tips for Great PRDs

1. **Start with Why**: Clearly articulate the problem and impact
2. **Be Quantifiable**: Use specific metrics, not vague goals
3. **Think Edge Cases**: Consider error scenarios and edge cases
4. **Document Assumptions**: Make implicit knowledge explicit
5. **Link to Research**: Reference user research, competitive analysis
6. **Define Success**: Clear, measurable acceptance criteria

## Common Pitfalls to Avoid

- ❌ Vague requirements: "should be fast"
- ❌ Missing success metrics: no KPIs defined
- ❌ Unclear scope: what's in/out not specified
- ❌ No acceptance criteria: can't verify completion
- ❌ Missing constraints: technical limitations not noted

## Quality Indicators

A great PRD:
- ✅ Can be handed to architecture team without questions
- ✅ Has clear, testable acceptance criteria
- ✅ Quantifies expected impact and success
- ✅ Addresses security and compliance needs
- ✅ Considers scalability and performance
- ✅ Identifies risks proactively

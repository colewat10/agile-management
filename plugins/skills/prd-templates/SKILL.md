---
name: prd-templates
description: Use when creating Product Requirements Documents (PRDs). Provides comprehensive structure, best practices, and templates for PRD creation following BMAD methodology.
---

# PRD Templates Skill

## Standard PRD Structure

Complete template for creating comprehensive PRDs that serve as single source of truth for features.

### Core Sections

**Executive Summary**: One-paragraph feature overview with business justification and expected impact

**Problem Statement**: Current state, pain points, affected users, quantified impact, and strategic importance

**Goals & Objectives**: Business goals, user goals, and quantifiable success metrics with baselines and targets

**User Personas & Use Cases**: Detailed personas with roles, goals, pain points, and comprehensive use case flows

**Functional Requirements**: Complete FR list with descriptions, priorities, user stories, acceptance criteria, and dependencies

**Non-Functional Requirements**: Performance, security, scalability, reliability, and compliance requirements

**Technical Constraints**: Technology stack constraints, infrastructure requirements, compatibility needs

**Success Metrics & KPIs**: User engagement, business impact, and technical performance metrics

**Timeline & Milestones**: Project phases, key deliverables, and dates

**Risks & Mitigation**: Technical and business risks with impact, probability, mitigation, and contingency plans

**Out of Scope**: Explicitly excluded features and deferred items

## PRD Best Practices

### Problem Definition
- Start with user pain, not solutions
- Quantify impact with data
- Specify affected user segments
- Explain urgency and opportunity

### Requirements Writing
- Make testable: "User can complete checkout in <3 clicks"
- Use "shall" (mandatory) vs "should" (optional)
- Include edge cases
- Link to business goals
- Document rationale

### Success Metrics
- Define baseline measurements
- Set specific, achievable targets
- Include achievement timeline
- Cover user, business, and technical dimensions

### Acceptance Criteria Format
```
Given [initial context]
When [specific action]
Then [expected outcome]
```

## Common PRD Patterns

### API Feature PRD
Focus: Endpoint specs, schemas, auth, rate limiting, error handling, versioning

### UI Feature PRD  
Focus: User workflows, wireframes, responsive design, accessibility (WCAG), browser support, performance

### Integration PRD
Focus: Integration points, data mapping, auth/authz, error handling, monitoring, rollback

## PRD Quality Checklist

- [ ] Problem clearly stated and quantified
- [ ] All functional requirements documented
- [ ] Non-functional requirements specified
- [ ] Success metrics defined and measurable
- [ ] Edge cases addressed
- [ ] Dependencies identified
- [ ] Risks documented with mitigation
- [ ] Timeline realistic
- [ ] Scope clear (in/out)
- [ ] Stakeholders reviewed

---
name: architecture-create
description: Create comprehensive architecture documentation using the architecture-designer agent
---

# Create Architecture Documentation

Generate detailed technical architecture documentation following the BMAD methodology using the architecture-designer agent.

## What This Command Does

Invokes the **architecture-designer** agent (Sonnet model) to transform PRD requirements into comprehensive architecture documentation including:

- System architecture and component design
- Data models and API specifications
- Technology stack decisions with rationale
- Security and performance patterns
- Implementation guidance and code examples

## Usage

```bash
# Basic usage
/agile-management:architecture-create "real-time chat"

# Referencing existing PRD
/agile-management:architecture-create "user authentication" --prd "docs/planning/prds/user-auth-prd-v1.0.md"

# With specific focus
/agile-management:architecture-create "payment processing" --focus "microservices migration"
```

## Command Flow

1. **PRD Analysis**: Agent reads existing PRD (or creates one if missing)
2. **Architecture Design**: Creates comprehensive architecture covering:
   - High-level system architecture
   - Component specifications
   - Data architecture
   - API design
   - Technical decisions
3. **Documentation Storage**: Saves to `docs/planning/architecture/`
4. **Next Steps**: Suggests story generation

## Architecture Output Structure

```markdown
# Architecture Document: {Feature Name}

## Executive Summary
## Requirements Summary  
## High-Level Architecture
## Detailed Component Design
## Data Architecture
## API Specifications
## Security Architecture
## Performance & Scalability
## Resilience & Reliability
## Technology Stack
## Technical Decisions & Trade-offs
## Implementation Patterns
## Testing Strategy
## Migration & Rollout
## Dependencies & Risks
```

## Integration with BMAD Workflow

### This is Phase 1, Step 2
```
1. Create PRD
   ↓
[You are here]
2. Create Architecture ← /agile-management:architecture-create
   ↓
3. Generate Stories → /agile-management:story-generate
   ↓
4. Validate Stories
```

## Example Usage

```bash
/agile-management:architecture-create "OAuth2 authentication"
```

**Agent Output**: Architecture covering:
- OAuth2 flow implementation
- Token management (JWT)
- Session storage (Redis)
- Database schema for users
- API endpoint specifications
- Security patterns (rate limiting, CORS)
- Integration with social providers

## Output Location

```
docs/planning/architecture/{feature-name}-architecture-v{version}.md
```

## Next Steps

After architecture creation:

```bash
/agile-management:story-generate "{feature-name}"
```

Or run full workflow from this point:

```bash
/agile-management:bmad-full-workflow "{feature-name}" --from-architecture
```

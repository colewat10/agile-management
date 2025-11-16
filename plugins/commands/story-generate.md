---
name: story-generate
description: Generate hyper-detailed, context-engineered development stories using the scrum-master agent
---

# Generate Development Stories

Transform PRD and architecture documentation into hyper-detailed, context-engineered development stories using the scrum-master agent.

## What This Command Does

Invokes the **scrum-master** agent (Sonnet model) to create development stories with complete embedded context:

- Extract requirements from PRD
- Extract technical approach from architecture
- Create hyper-detailed stories with full implementation guidance
- Embed all context directly in story files
- Automatically validate with story-validator

## Usage

```bash
# Generate stories for a feature
/agile-management:story-generate "user authentication"

# Generate specific number of stories
/agile-management:story-generate "payment processing" --count 5

# Generate stories for specific epic
/agile-management:story-generate "OAuth2 flow" --epic "authentication-epic"
```

## Command Flow

1. **Load Planning Docs**: Read PRD and architecture documentation
2. **Decompose Feature**: Break down into logical stories
3. **Create Stories**: Generate hyper-detailed stories with:
   - Complete business context from PRD
   - Full technical context from architecture
   - Specific implementation details
   - Code examples and patterns
   - Testing strategy
4. **Validate Stories**: Auto-run story-validator (Haiku)
5. **Save Stories**: Store in `stories/backlog/`

## Story Output Structure

Each generated story includes:

```markdown
# Story: {Title}

## User Story
## Business Context (from PRD)
## Acceptance Criteria
## Technical Context (from Architecture)
## Implementation Details
  - Step-by-step approach
  - Code examples
  - File structure
  - Configuration
## Architectural Guidance
## Integration Points
## Testing Strategy
## Definition of Done
```

## Integration with BMAD Workflow

### This is Phase 2, Step 3
```
1. Create PRD
   ↓
2. Create Architecture
   ↓
[You are here]
3. Generate Stories ← /agile-management:story-generate
   ↓
4. Validate Stories (automatic)
```

## Example Usage

```bash
/agile-management:story-generate "real-time chat"
```

**Agent Output**: Stories like:
- STORY-001: WebSocket connection setup and heartbeat
- STORY-002: Message queue and persistence layer
- STORY-003: User presence and typing indicators
- STORY-004: Message encryption and security
- STORY-005: Real-time message delivery and sync

Each story contains complete context, implementation details, and code examples.

## Output Location

```
stories/backlog/
├── story-001-websocket-setup.md
├── story-002-message-queue.md
├── story-003-user-presence.md
└── ...
```

## Validation Reports

Automatic validation creates:
```
stories/backlog/
├── story-001-websocket-setup.md
├── story-001-validation-report.md  ← Auto-generated
└── ...
```

## Next Steps

After story generation:
1. Review stories and validation reports
2. Address any critical issues flagged by validator
3. Move stories to `stories/active/` to start development
4. Implement stories with complete context

## Story Quality

Generated stories ensure:
- ✅ Complete business context embedded
- ✅ Full technical context embedded
- ✅ No external documentation lookup needed
- ✅ Specific implementation guidance
- ✅ Concrete code examples
- ✅ Comprehensive testing strategy
- ✅ Clear definition of done

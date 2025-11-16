# Agile Management - BMAD Methodology Plugin

A comprehensive Claude Code plugin implementing the BMAD (Build-Measure-Adapt-Deploy) methodology for agile project management. Eliminates planning inconsistency and context loss through two-phase agentic planning and context-engineered development.

## Overview

BMAD transforms agile development by solving the two biggest problems in AI-assisted development:

1. **Planning Inconsistency** → Solved by Phase 1 agentic planning
2. **Context Loss** → Solved by Phase 2 context-engineered development

### The Result

- **Zero Context Loss**: All information embedded directly in development stories
- **Zero Planning Inconsistency**: Single source of truth from PRD through implementation
- **Autonomous Development**: Developers have complete understanding from story files alone

## Quick Start

### Installation

```bash
# Add plugin marketplace
/plugin marketplace add yourusername/agile-management

# Install the plugin
/plugin install agile-management
```

### Initialize BMAD Project

```bash
/agile-management:bmad-init
```

### Run Complete Workflow

```bash
/agile-management:bmad-full-workflow "user authentication with OAuth2 and MFA"
```

## Two-Phase Methodology

### Phase 1: Agentic Planning

Create detailed, consistent PRDs and architecture documents through advanced prompt engineering.

**Step 1: Product Planning** (product-planner agent - Sonnet)
```bash
/agile-management:prd-create "real-time collaboration feature"
```

**Step 2: Architecture Design** (architecture-designer agent - Sonnet)
```bash
/agile-management:architecture-create "real-time collaboration"
```

### Phase 2: Context-Engineered Development

Transform plans into hyper-detailed stories with complete embedded context.

**Step 3: Story Generation** (scrum-master agent - Sonnet)
```bash
/agile-management:story-generate "real-time collaboration"
```

**Step 4: Story Validation** (story-validator agent - Haiku - automatic)
- Validates completeness, consistency, and actionability
- Generates validation reports automatically

## Plugin Components

### 4 Specialized Agents

| Agent | Model | Purpose |
|-------|-------|---------|
| **product-planner** | Sonnet | Create comprehensive PRDs |
| **architecture-designer** | Sonnet | Design detailed architecture |
| **scrum-master** | Sonnet | Generate hyper-detailed stories |
| **story-validator** | Haiku | Validate story quality |

### 6 Commands

| Command | Description |
|---------|-------------|
| **bmad-init** | Initialize BMAD project structure |
| **prd-create** | Create Product Requirements Document |
| **architecture-create** | Create architecture documentation |
| **story-generate** | Generate development stories |
| **bmad-full-workflow** | Run complete BMAD workflow |
| **story-refine** | Refine existing stories |

### 5 Specialized Skills

| Skill | Purpose |
|-------|---------|
| **bmad-methodology** | Core BMAD principles and workflow |
| **prd-templates** | PRD structure and best practices |
| **architecture-patterns** | Architecture documentation patterns |
| **story-writing** | User story formatting and structure |
| **context-engineering** | Hyper-detailed context creation |

## Example Workflow

```bash
# 1. Initialize project
/agile-management:bmad-init "My SaaS Platform"

# 2. Run full workflow
/agile-management:bmad-full-workflow "OAuth2 authentication with Google and GitHub"

# Output:
# ✅ PRD created: docs/planning/prds/oauth2-auth-prd-v1.0.md
# ✅ Architecture created: docs/planning/architecture/oauth2-auth-architecture-v1.0.md
# ✅ Stories generated:
#    - STORY-001: OAuth2 client setup and configuration
#    - STORY-002: Google OAuth flow implementation  
#    - STORY-003: GitHub OAuth flow implementation
#    - STORY-004: Token management and session handling
#    - STORY-005: User profile creation and linking
# ✅ All stories validated: 5 PASS

# 3. Review and start development
# Stories are in stories/backlog/ with complete context
```

## Key Features

### Comprehensive PRDs

- Business context and objectives
- Detailed functional requirements
- Non-functional requirements (performance, security, scalability)
- Success metrics and KPIs
- User personas and use cases
- Risk assessment and mitigation

### Detailed Architecture

- System architecture diagrams
- Component specifications
- Data models and API contracts
- Technology decisions with rationale
- Security and performance patterns
- Implementation guidance with code examples

### Hyper-Detailed Stories

Every story contains:
- ✅ Complete business context (from PRD)
- ✅ Full technical context (from architecture)
- ✅ Step-by-step implementation details
- ✅ Concrete code examples (not pseudocode)
- ✅ Complete testing strategy
- ✅ Clear definition of done
- ✅ **Zero external documentation needed**

## Benefits

### For Developers
- Complete understanding from story alone
- No hunting for context or decisions
- Clear technical direction
- Faster implementation
- Higher quality code

### For Teams
- Consistent approach across features
- Reduced back-and-forth communication
- Better estimates
- Easier onboarding
- Single source of truth

### For Projects
- Faster delivery
- Fewer defects
- Better architecture
- Lower technical debt
- Measurable success

## Story Quality Example

### Traditional Story ❌
```
As a user, I want to login
So that I can access my account

Acceptance Criteria:
- User can login
- See PRD for details
```

### BMAD Story ✅
```
As a user, I want to authenticate using OAuth2 with Google
So that I can securely access my account without managing passwords

Business Context:
[Complete context from PRD explaining impact, metrics, research]

Acceptance Criteria:
[10+ specific, testable criteria covering all scenarios]

Technical Context:
- OAuth2 Authorization Code Flow with PKCE
- Token storage: HttpOnly cookies + Redis sessions
[Complete data models, API specifications]

Implementation Details:
1. Install dependencies: passport-google-oauth20
2. Configure Passport Strategy:
   [Actual runnable code example]
3. Implement routes:
   [Complete route implementation]
4. Error handling:
   [Specific error scenarios with code]

[Complete testing strategy with test code]
[Definition of done with 12 checkpoints]
```

## Directory Structure

```
agile-management/
├── .claude-plugin/
│   └── marketplace.json          # Plugin registry
├── plugins/
│   └── agile-management/
│       ├── agents/               # 4 specialized agents
│       ├── commands/             # 6 commands
│       └── skills/               # 5 skill packages
├── docs/
│   ├── README.md                 # Installation guide
│   ├── bmad-method.md            # Methodology documentation
│   ├── agents.md                 # Agent reference
│   ├── commands.md               # Command reference
│   └── examples.md               # Usage examples
├── LICENSE                       # MIT License
└── README.md                     # This file
```

## Documentation

- [Installation Guide](docs/README.md)
- [BMAD Methodology](docs/bmad-method.md)
- [Agent Reference](docs/agents.md)
- [Command Reference](docs/commands.md)
- [Usage Examples](docs/examples.md)

## Requirements

- Claude Code installed
- Claude Pro or Max plan (for Sonnet 4.5 access)

## License

MIT License - See [LICENSE](LICENSE) file

## Contributing

Contributions welcome! This plugin follows the exact structure and patterns of [wshobson/agents](https://github.com/wshobson/agents).

## Acknowledgments

- Plugin structure based on [wshobson/agents](https://github.com/wshobson/agents)
- BMAD methodology by Cole

## Support

For issues or questions:
- Create an issue on GitHub
- Review documentation in `docs/`
- Check examples in `docs/examples.md`

---

**Eliminate planning inconsistency and context loss. Build better software with BMAD.**

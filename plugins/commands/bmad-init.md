---
name: bmad-init
description: Initialize BMAD project structure with directories for PRDs, architecture docs, and development stories
---

# BMAD Project Initialization

Initialize the complete BMAD (Build-Measure-Adapt-Deploy) project structure for agile development with comprehensive documentation and context-engineered stories.

## What This Command Does

Creates a standardized directory structure and template files for BMAD methodology:

- **Planning Documents**: Directories for PRDs and architecture documentation
- **Development Stories**: Organized story directory with templates
- **Configuration**: BMAD configuration file for project settings
- **Documentation**: README explaining the structure and workflow

## Directory Structure Created

```
project-root/
├── .bmad/
│   └── config.yaml              # BMAD configuration
├── docs/
│   ├── planning/
│   │   ├── prds/                # Product Requirements Documents
│   │   │   └── README.md
│   │   └── architecture/        # Architecture Documentation
│   │       └── README.md
│   └── bmad-workflow.md         # BMAD methodology guide
├── stories/
│   ├── backlog/                 # Story backlog
│   │   └── README.md
│   ├── active/                  # Stories in development
│   │   └── README.md
│   ├── completed/               # Completed stories
│   │   └── README.md
│   └── templates/               # Story templates
│       └── story-template.md
└── README.md                    # Project overview
```

## Usage

```bash
/agile-management:bmad-init
```

Or with project name:

```bash
/agile-management:bmad-init "my-saas-platform"
```

## What Gets Created

### 1. BMAD Configuration (.bmad/config.yaml)

```yaml
bmad:
  version: "1.0.0"
  project_name: "My Project"
  
  # Phase 1: Planning Settings
  planning:
    prd_directory: "docs/planning/prds"
    architecture_directory: "docs/planning/architecture"
    require_architecture: true
    
  # Phase 2: Development Settings  
  stories:
    directory: "stories"
    template: "stories/templates/story-template.md"
    id_prefix: "STORY"
    id_start: 1
    
  # Workflow Settings
  workflow:
    require_prd_before_architecture: true
    require_architecture_before_stories: true
    auto_validate_stories: true
    
  # Agent Preferences
  agents:
    product_planner_model: "sonnet"
    architecture_designer_model: "sonnet"
    scrum_master_model: "sonnet"
    story_validator_model: "haiku"
```

### 2. PRD Directory (docs/planning/prds/README.md)

```markdown
# Product Requirements Documents (PRDs)

This directory contains comprehensive Product Requirements Documents following the BMAD methodology.

## PRD Structure

Each PRD should include:
- Executive Summary
- Problem Statement
- Goals & Objectives
- User Personas & Use Cases
- Functional Requirements
- Non-Functional Requirements
- Technical Constraints
- Success Metrics
- Timeline & Milestones
- Risks & Mitigation

## Naming Convention

Use descriptive names with version numbers:
- `feature-name-v1.0.md`
- `epic-name-v1.0.md`

## Creating PRDs

Use the product-planner agent:
```
/agile-management:prd-create "feature description"
```

Or invoke directly:
```
Use product-planner to create a PRD for [feature description]
```
```

### 3. Architecture Directory (docs/planning/architecture/README.md)

```markdown
# Architecture Documentation

This directory contains comprehensive architecture documentation following the BMAD methodology.

## Architecture Document Structure

Each architecture document should include:
- Executive Summary
- High-Level Architecture
- Detailed Component Design
- Data Architecture
- API Specifications
- Security Architecture
- Performance & Scalability
- Technology Stack
- Technical Decisions & Trade-offs

## Naming Convention

Match PRD names or use component names:
- `feature-name-architecture-v1.0.md`
- `component-name-design-v1.0.md`

## Creating Architecture Docs

Use the architecture-designer agent:
```
/agile-management:architecture-create "feature name"
```

Or invoke directly:
```
Use architecture-designer to create architecture for [feature]
```
```

### 4. Story Template (stories/templates/story-template.md)

```markdown
# Story: [Story Title]

**Story ID**: STORY-XXX
**Epic**: [Epic Name]
**Priority**: High | Medium | Low
**Estimated Effort**: X days
**Dependencies**: STORY-YYY, STORY-ZZZ

## User Story

**As a** [user persona]
**I want** [capability]
**So that** [business value]

## Business Context

[Relevant context from PRD explaining why this matters]

## Acceptance Criteria

- [ ] AC1: Specific, testable criterion
- [ ] AC2: Another criterion
- [ ] AC3: Edge case handling

## Technical Context

### Relevant Architecture Decisions
[Architecture context]

### Data Models
```typescript
// Schema definitions
```

### API Contracts
```
POST /api/v1/endpoint
Request: { }
Response: { }
```

## Implementation Details

### Technical Approach
1. **Setup**: Dependencies and configuration
2. **Core Implementation**: Main functionality
3. **Integration**: Integration points
4. **Testing**: Test strategy

### Code Examples
```python
# Concrete implementation examples
```

### File Structure
```
src/
├── component/
```

## Architectural Guidance

### Patterns to Follow
- Pattern 1: Description
- Pattern 2: Description

### Anti-Patterns to Avoid
- Anti-pattern 1: Why to avoid

## Testing Strategy

### Unit Tests
- Test case 1
- Test case 2

### Integration Tests
- Integration scenario 1

## Definition of Done

- [ ] Implementation complete
- [ ] Tests passing
- [ ] Code reviewed
- [ ] Documentation updated
```

### 5. Project README.md

```markdown
# [Project Name]

This project follows the BMAD (Build-Measure-Adapt-Deploy) methodology for agile development.

## BMAD Methodology

### Phase 1: Agentic Planning
1. **Product Planning**: Create comprehensive PRDs with business context and requirements
2. **Architecture Design**: Design detailed technical architecture and implementation approach

### Phase 2: Context-Engineered Development  
3. **Story Generation**: Transform PRDs + Architecture into hyper-detailed development stories
4. **Story Validation**: Ensure stories are complete, consistent, and actionable

## Directory Structure

- `docs/planning/prds/` - Product Requirements Documents
- `docs/planning/architecture/` - Architecture Documentation
- `stories/backlog/` - Story backlog (not yet started)
- `stories/active/` - Stories currently in development
- `stories/completed/` - Completed stories

## Workflow

### Creating a New Feature

1. **Create PRD**
   ```
   /agile-management:prd-create "feature description"
   ```

2. **Create Architecture**
   ```
   /agile-management:architecture-create "feature name"
   ```

3. **Generate Stories**
   ```
   /agile-management:story-generate "feature name"
   ```

4. **Validate Stories**
   Stories are automatically validated. Review validation reports in story files.

### Full Workflow

Run the complete BMAD workflow:
```
/agile-management:bmad-full-workflow "feature description"
```

## Benefits

- **Zero Planning Inconsistency**: Single source of truth from PRD through stories
- **No Context Loss**: Complete context embedded in each story
- **Developer-Ready**: Stories contain everything needed for implementation
- **Quality Assured**: Automated validation ensures completeness

## Configuration

See `.bmad/config.yaml` for project settings and preferences.
```

### 6. BMAD Workflow Guide (docs/bmad-workflow.md)

```markdown
# BMAD Workflow Guide

## Overview

BMAD eliminates the two biggest problems in AI-assisted development:
1. **Planning Inconsistency**: Solved by Phase 1 agentic planning
2. **Context Loss**: Solved by Phase 2 context-engineered stories

## Phase 1: Agentic Planning

### Step 1: Create PRD (product-planner agent)

**Goal**: Create comprehensive product requirements that become single source of truth

**Agent**: product-planner (Sonnet)

**Output**: Detailed PRD with:
- Business context and objectives
- Complete functional requirements
- Non-functional requirements
- Success metrics
- User stories and use cases

**Command**: `/agile-management:prd-create "feature"`

### Step 2: Create Architecture (architecture-designer agent)

**Goal**: Design complete technical approach and patterns

**Agent**: architecture-designer (Sonnet)

**Output**: Comprehensive architecture with:
- System design and components
- Data models and APIs
- Technology decisions with rationale
- Implementation patterns
- Security and performance approach

**Command**: `/agile-management:architecture-create "feature"`

## Phase 2: Context-Engineered Development

### Step 3: Generate Stories (scrum-master agent)

**Goal**: Transform PRD + Architecture into hyper-detailed stories

**Agent**: scrum-master (Sonnet)

**Output**: Development stories with embedded:
- Complete business context from PRD
- Full technical context from architecture
- Specific implementation details
- Code examples and patterns
- Testing strategy

**Command**: `/agile-management:story-generate "feature"`

### Step 4: Validate Stories (story-validator agent)

**Goal**: Ensure stories are complete and consistent

**Agent**: story-validator (Haiku)

**Output**: Validation report with:
- Completeness check
- PRD alignment verification
- Architecture consistency check
- Actionability assessment

**Automatic**: Runs automatically after story generation

## Full Workflow

Run complete BMAD process:

```
/agile-management:bmad-full-workflow "feature description"
```

This orchestrates all four agents in sequence:
1. product-planner → Create PRD
2. architecture-designer → Create architecture
3. scrum-master → Generate stories
4. story-validator → Validate stories

## Benefits

### Eliminates Planning Inconsistency
- Single comprehensive PRD
- Detailed architecture upfront
- Consistent technical approach
- Clear success criteria

### Eliminates Context Loss  
- All context embedded in stories
- No external documentation hunting
- Complete implementation guidance
- Developers have full understanding

### Enables Autonomous Development
- Stories are fully actionable
- Clear technical approach
- Code examples provided
- Testing strategy defined

## Best Practices

1. **Complete Phase 1 Before Phase 2**: Don't create stories without PRD and architecture
2. **Keep PRD and Architecture Updated**: Single source of truth must stay current
3. **Address Validation Issues**: Fix critical issues before development
4. **Iterate on Planning**: Refine PRD and architecture as you learn
5. **Use Story Templates**: Maintain consistency across all stories
```

## Post-Initialization Steps

After initialization:

1. **Review Configuration**: Edit `.bmad/config.yaml` to match your preferences
2. **Customize Templates**: Modify story templates in `stories/templates/` as needed
3. **Set Up Version Control**: Add BMAD directories to your git repository
4. **Team Onboarding**: Share `docs/bmad-workflow.md` with your team

## Verification

After initialization, verify:
- [ ] Directory structure created
- [ ] Configuration file present
- [ ] Template files created
- [ ] README files in place
- [ ] BMAD workflow guide available

## Example

```bash
# Initialize BMAD structure
/agile-management:bmad-init "E-Commerce Platform"

# Verify structure created
ls -la docs/planning/
ls -la stories/

# Review configuration
cat .bmad/config.yaml

# Read workflow guide
cat docs/bmad-workflow.md
```

## Next Steps

After initialization:
1. Create your first PRD: `/agile-management:prd-create "user authentication"`
2. Design architecture: `/agile-management:architecture-create "user authentication"`
3. Generate stories: `/agile-management:story-generate "user authentication"`
4. Start development with context-rich stories!

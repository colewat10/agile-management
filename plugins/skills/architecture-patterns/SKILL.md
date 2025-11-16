---
name: architecture-patterns
description: Use when creating architecture documentation. Provides patterns, best practices, and templates for comprehensive technical architecture documentation following BMAD methodology.
---

# Architecture Patterns Skill

## Standard Architecture Document Structure

Complete architecture documentation that enables autonomous development.

### Core Sections

**Executive Summary**: Architectural approach overview, key decisions, major components

**Requirements Summary**: Functional requirements from PRD, non-functional requirements, technical constraints, compliance

**High-Level Architecture**: System diagrams, component overview, deployment architecture, scaling strategy

**Detailed Component Design**: Per-component: purpose, responsibilities, interfaces, internal structure, data handling

**Data Architecture**: Data models with schemas, database design, data flow, caching strategy

**API Specifications**: REST/GraphQL/gRPC endpoints with full contracts, request/response schemas, authentication, error codes

**Security Architecture**: Authentication & authorization mechanisms, security controls, encryption, compliance

**Performance & Scalability**: Performance requirements, caching strategy, scaling approach, load balancing

**Resilience & Reliability**: Error handling patterns, circuit breakers, monitoring strategy, backup/recovery

**Technology Stack**: Backend/frontend/data/infrastructure choices with rationale for each

**Technical Decisions**: Major decisions with context, chosen solution, rationale, alternatives considered, trade-offs

**Implementation Patterns**: Code patterns to follow with examples, anti-patterns to avoid

**Testing Strategy**: Unit/integration/e2e testing approach

**Migration & Rollout**: Phased approach, feature flags, rollback plan

## Architecture Documentation Best Practices

### Decision Documentation
Every major decision needs:
- **Context**: What problem does this solve?
- **Decision**: What we chose
- **Rationale**: Why we chose it
- **Alternatives**: What else we considered
- **Trade-offs**: Pros and cons

### Pattern Documentation
For each pattern:
- **When to Use**: Specific scenarios
- **Implementation**: Concrete code example
- **Anti-patterns**: What to avoid

### Component Design
Each component specification:
- Clear single responsibility
- Explicit interface contracts
- Defined dependencies
- Internal structure explained
- Data handling approach

## Common Architecture Patterns

### Microservices Architecture
- Service boundaries and responsibilities
- Inter-service communication (sync/async)
- Service discovery and registration
- API gateway pattern
- Data consistency (saga/2PC)
- Circuit breaker and retry logic

### Event-Driven Architecture  
- Event schemas and formats
- Event bus/message broker
- Publisher/subscriber patterns
- Event sourcing
- CQRS (Command Query Responsibility Segregation)
- Eventual consistency handling

### API Design Patterns
- REST: Resource modeling, HTTP verbs, status codes
- GraphQL: Schema design, resolvers, n+1 prevention
- gRPC: Proto definitions, streaming patterns
- Authentication: JWT, OAuth2, API keys
- Rate limiting and throttling
- Versioning strategy

### Data Patterns
- Database per service
- Shared database
- Repository pattern
- Unit of Work pattern
- Caching strategies (read-through, write-through, write-behind)
- Database replication and sharding

### Security Patterns
- Defense in depth
- Principle of least privilege
- Input validation and sanitization
- Output encoding
- Secure session management
- Encryption at rest and in transit

## Technology Decision Framework

When documenting technology choices:

1. **Requirements Analysis**: What specific requirements drive this decision?
2. **Options Evaluation**: What alternatives exist?
3. **Comparison Matrix**: Compare options on key dimensions
4. **Risk Assessment**: What risks does each option carry?
5. **Cost Analysis**: Development, operational, licensing costs
6. **Team Expertise**: Do we have skills or need training?
7. **Community & Support**: Ecosystem maturity?
8. **Final Decision**: What we chose and why

## Code Example Standards

### Good Architecture Code Example
```python
# User Service - Domain Service Pattern
class UserService:
    """Handles user business logic and orchestration."""
    
    def __init__(self, user_repo: UserRepository, 
                 event_bus: EventBus,
                 cache: Cache):
        self.user_repo = user_repo
        self.event_bus = event_bus
        self.cache = cache
    
    async def create_user(self, user_data: Dict) -> User:
        """Create new user with validation and event publishing."""
        # Validate input
        validated_data = self._validate_user_data(user_data)
        
        # Check for duplicates
        if await self.user_repo.exists_by_email(validated_data['email']):
            raise DuplicateEmailError()
        
        # Create user
        user = await self.user_repo.create(validated_data)
        
        # Invalidate cache
        await self.cache.delete(f"user:{user.id}")
        
        # Publish event
        await self.event_bus.publish('user.created', {
            'user_id': user.id,
            'email': user.email,
            'created_at': user.created_at.isoformat()
        })
        
        return user
```

### What Makes It Good
- Concrete, runnable code
- Shows dependency injection
- Demonstrates error handling
- Includes business logic
- Shows integration points (repo, cache, events)
- Follows documented patterns

## Architecture Quality Checklist

- [ ] All PRD requirements addressed
- [ ] System architecture diagram present
- [ ] Each component fully specified
- [ ] Data models complete with schemas
- [ ] All APIs fully specified
- [ ] Security approach documented
- [ ] Performance requirements addressed
- [ ] All major decisions documented with rationale
- [ ] Code examples for key patterns
- [ ] Testing strategy defined
- [ ] Deployment approach specified
- [ ] Monitoring and observability planned

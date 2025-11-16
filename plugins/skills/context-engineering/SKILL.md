---
name: context-engineering
description: Use when creating hyper-detailed development stories with complete embedded context. Teaches how to eliminate context loss by embedding all necessary information directly in story files.
---

# Context Engineering Skill

## Core Principle

**Context Engineering** is the practice of embedding ALL information needed for implementation directly in story files, eliminating the need for developers to hunt for information across multiple documents.

## The Context Loss Problem

### Traditional Approach (Broken)
```
Story: Implement user authentication

As a user, I want to login
So that I can access my account

Acceptance Criteria:
- User can login
- See PRD section 3.2 for details
- Follow architecture doc for OAuth2 flow
- Use standard error handling
```

**Problems**:
- Developer must find PRD section 3.2
- Must locate architecture doc
- "Standard error handling" is ambiguous
- No implementation guidance
- Multiple context switches required

### BMAD Approach (Context-Engineered)
```
Story: Implement OAuth2 Authentication with Google

[Complete user story with business value]

Business Context:
According to PRD section 3.2, we're implementing OAuth2 because:
- 65% of users prefer social login over password creation
- Reduces support tickets by 40% (password resets)
- Improves conversion rate by 25%
- Industry standard for our user segment

Target: 80% of new users choosing social login within 30 days

[Complete implementation details with code examples]
[Full API specifications embedded]
[All error scenarios defined]
[Complete testing strategy]
```

**Benefits**:
- Zero external lookups needed
- Complete understanding from story alone
- All decisions already made
- Clear implementation path

## Context Embedding Strategies

### 1. Embed Business Context from PRD

**Instead of**: "See PRD for business requirements"

**Do This**:
```markdown
## Business Context (from PRD)

### Why This Feature
Users report spending 15+ minutes on manual data entry weekly.
This feature automates entry, targeting 90% reduction in data entry time.

### Success Metrics (from PRD Section 4.2)
- Baseline: 15 min/week manual data entry
- Target: <2 min/week with automation
- User satisfaction: +2 NPS points
- Feature adoption: >70% within 60 days

### User Research Insights
From user interviews (PRD Appendix B):
- 85% of users manually copy data from emails
- 60% use multiple copy-paste operations
- Primary pain: switching between apps
```

### 2. Embed Technical Context from Architecture

**Instead of**: "Follow architecture doc for implementation"

**Do This**:
```markdown
## Technical Context (from Architecture Doc)

### Component Architecture (Section 3.4)
This story implements the AuthenticationService component which:
- Handles OAuth2 authorization code flow
- Manages token storage and refresh
- Provides session management
- Integrates with User Service for profile creation

### Technology Decisions (Section 5.1)
OAuth2 Library: passport-google-oauth20 v2.0
Rationale: Most popular Google OAuth library, active maintenance,
comprehensive documentation, matches our Express.js stack

Session Storage: Redis
Rationale: In-memory performance for session lookups, supports
distributed deployment, TTL for automatic session expiry

### Data Models (Section 4.2)
```typescript
interface OAuthToken {
  user_id: string;
  provider: 'google' | 'github';
  access_token: string;
  refresh_token: string;
  expires_at: Date;
  created_at: Date;
}
```

### API Specification (Section 6.3)
```
GET /auth/google/callback
Query Parameters:
  - code: string (authorization code)
  - state: string (CSRF token)
Response: 302 Redirect to /dashboard
Side Effects: Creates session, stores in Redis
```
```

### 3. Embed Complete Implementation Guidance

**Instead of**: "Implement using best practices"

**Do This**:
```markdown
## Implementation Details

### Step 1: Install Dependencies
```bash
npm install passport passport-google-oauth20 express-session connect-redis
```

### Step 2: Configure Passport Strategy
```javascript
// src/config/passport.js
const GoogleStrategy = require('passport-google-oauth20').Strategy;

passport.use(new GoogleStrategy({
    clientID: process.env.GOOGLE_CLIENT_ID,
    clientSecret: process.env.GOOGLE_CLIENT_SECRET,
    callbackURL: "https://example.com/auth/google/callback"
  },
  async function(accessToken, refreshToken, profile, done) {
    // Find or create user
    let user = await User.findOne({ googleId: profile.id });
    
    if (!user) {
      user = await User.create({
        googleId: profile.id,
        email: profile.emails[0].value,
        name: profile.displayName
      });
    }
    
    // Store OAuth tokens
    await OAuthToken.upsert({
      user_id: user.id,
      provider: 'google',
      access_token: accessToken,
      refresh_token: refreshToken,
      expires_at: Date.now() + 3600000
    });
    
    return done(null, user);
  }
));
```

### Step 3: Implement Routes
[Complete route implementation]

### Step 4: Error Handling
[Specific error scenarios with handling code]
```

### 4. Embed Testing Strategy

**Instead of**: "Write tests"

**Do This**:
```markdown
## Testing Strategy

### Unit Tests

Test 1: Successful OAuth Flow
```javascript
describe('GoogleAuthStrategy', () => {
  it('should create new user on first login', async () => {
    const profile = {
      id: 'google123',
      emails: [{ value: 'test@example.com' }],
      displayName: 'Test User'
    };
    
    const user = await authService.handleGoogleAuth(
      'access_token',
      'refresh_token',
      profile
    );
    
    expect(user).toBeDefined();
    expect(user.email).toBe('test@example.com');
    expect(user.googleId).toBe('google123');
  });
});
```

Test 2: Duplicate Email Handling
[Complete test code]

Test 3: Token Refresh
[Complete test code]

### Integration Tests

Test Scenario: Complete OAuth Flow
1. User clicks "Login with Google"
2. Redirects to Google consent
3. Google redirects back with code
4. System exchanges code for tokens
5. User session created
6. User redirected to dashboard

[Complete integration test code]

### Edge Cases to Test
- Network failure during token exchange
- Invalid authorization code
- Expired tokens
- User denies consent
- Email already exists with different provider
```

### 5. Embed Configuration Requirements

**Instead of**: "Configure as needed"

**Do This**:
```markdown
## Configuration Requirements

### Environment Variables
```bash
# Google OAuth Configuration
GOOGLE_CLIENT_ID=your_client_id.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=your_client_secret

# Session Configuration
SESSION_SECRET=random_32_char_string
REDIS_URL=redis://localhost:6379

# Application URLs
APP_URL=https://example.com
CALLBACK_URL=https://example.com/auth/google/callback
```

### Google Cloud Console Setup
1. Navigate to https://console.cloud.google.com
2. Create new project or select existing
3. Enable Google+ API
4. Create OAuth 2.0 credentials:
   - Application type: Web application
   - Authorized redirect URIs: [CALLBACK_URL]
5. Copy Client ID and Client Secret to .env

### Redis Configuration
```yaml
# config/redis.yml
development:
  url: redis://localhost:6379
  ttl: 86400  # 24 hours
  
production:
  url: ${REDIS_URL}
  ttl: 86400
  password: ${REDIS_PASSWORD}
```

### File Structure
```
src/
├── config/
│   ├── passport.js          # Passport configuration
│   └── redis.js            # Redis client setup
├── routes/
│   └── auth.js             # OAuth routes
├── services/
│   └── auth-service.js     # Authentication logic
├── models/
│   ├── user.js             # User model
│   └── oauth-token.js      # Token model
└── middleware/
    └── auth-middleware.js   # Session verification
```
```

## Context Completeness Checklist

For each story, ensure these are embedded:

### Business Context
- [ ] Why this feature matters (from PRD)
- [ ] User impact and benefits
- [ ] Success metrics and targets
- [ ] Priority and urgency
- [ ] Related PRD requirements

### Technical Context
- [ ] Relevant architecture decisions
- [ ] Component specifications
- [ ] Complete data models
- [ ] Full API specifications
- [ ] Integration points
- [ ] Technology choices with rationale

### Implementation Guidance
- [ ] Step-by-step approach
- [ ] Concrete code examples (not pseudocode)
- [ ] Specific libraries and versions
- [ ] File structure and organization
- [ ] Configuration requirements
- [ ] Error handling patterns

### Testing Context
- [ ] Specific unit test cases with code
- [ ] Integration test scenarios
- [ ] Edge cases to test
- [ ] Performance test requirements
- [ ] Security test considerations

### Deployment Context
- [ ] Environment variables
- [ ] External service setup
- [ ] Database migrations needed
- [ ] Feature flag configuration
- [ ] Rollback procedures

## Red Flags (Missing Context)

Watch for these phrases that indicate missing context:

❌ "See PRD for details"
✅ Embed relevant PRD sections

❌ "Follow standard pattern"
✅ Show the exact pattern with code

❌ "Configure as needed"
✅ Specify exact configuration

❌ "Use best practices"
✅ Define which practices and show how

❌ "Handle errors appropriately"
✅ Specify each error scenario and handling

❌ "Refer to architecture doc"
✅ Embed relevant architecture sections

## Context Engineering Examples

### Example: From Reference to Embedded

**Before (References)**:
```markdown
Implement payment processing per PRD section 4.
Use Stripe API following architecture doc pattern.
Handle errors per coding standards.
```

**After (Embedded)**:
```markdown
## Business Context
Per PRD section 4: Payment processing is critical path to revenue.
Current manual invoicing costs $50K/year in admin time.
Automation target: <5 min from quote to payment link.
Expected ROI: $200K annual savings.

## Technical Context
Architecture Decision (Doc Section 5.2): Stripe for payment processing
Rationale: PCI compliance handled, 2.9% + 30¢ pricing competitive,
excellent API documentation, webhooks for async processing.

Payment Flow (Architecture Section 5.3):
1. Create PaymentIntent on Stripe
2. Return client_secret to frontend
3. Frontend confirms with Stripe.js
4. Webhook confirms payment
5. Update order status

Data Model:
```typescript
interface Payment {
  id: string;
  order_id: string;
  stripe_payment_intent_id: string;
  amount_cents: number;
  currency: 'usd';
  status: 'pending' | 'succeeded' | 'failed';
  created_at: Date;
}
```

## Implementation Details

### Step 1: Create Payment Intent
```typescript
import Stripe from 'stripe';
const stripe = new Stripe(process.env.STRIPE_SECRET_KEY);

async function createPayment(orderId: string, amountCents: number) {
  try {
    const paymentIntent = await stripe.paymentIntents.create({
      amount: amountCents,
      currency: 'usd',
      metadata: { order_id: orderId }
    });
    
    const payment = await Payment.create({
      order_id: orderId,
      stripe_payment_intent_id: paymentIntent.id,
      amount_cents: amountCents,
      status: 'pending'
    });
    
    return { clientSecret: paymentIntent.client_secret };
  } catch (error) {
    if (error.type === 'StripeCardError') {
      throw new PaymentError('Card declined', error.code);
    }
    throw error;
  }
}
```

[Complete implementation continues with all error scenarios, webhook handling, etc.]
```

## Benefits of Context Engineering

1. **Developer Autonomy**: Implement without interruptions
2. **Consistent Quality**: All decisions pre-made and documented
3. **Faster Onboarding**: New devs have complete context
4. **Reduced Rework**: No surprises or missing requirements
5. **Better Estimates**: Complete scope visible upfront
6. **Lower Cognitive Load**: No context switching to find info

## Context Engineering is BMAD's Secret Weapon

By embedding complete context, BMAD eliminates the #1 cause of development delays: hunting for information. Developers open a story and have everything they need to succeed.

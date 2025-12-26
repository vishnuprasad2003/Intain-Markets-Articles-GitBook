# Controls & Accountability

## Overview

Intain Markets implements comprehensive controls and accountability measures to ensure security, compliance, and proper governance. Understanding these controls helps you understand how the platform protects all parties and maintains integrity.

## Access Controls

### Role-Based Access

**What it means:**
- Each role has specific permissions: Roles defined in JWT token (`req.user.Role`), validated via `requireRole()` middleware
- Access limited to role capabilities: Middleware `requireRole('Issuer')`, `requireRole('Market Maker')`, `requireRole('Lender')`, etc. enforces role-based access
- Cannot access unauthorized areas: API endpoints protected by `requireAuth` and `requireRole()` middleware, returns 403 Forbidden if role doesn't match
- Security maintained: JWT token validation via `express-jwt` middleware, token expiration (1 hour), refresh token mechanism
- Proper workflow enforced: Status-based validation combined with role checks ensures proper workflow progression

**How it works:**
- Roles define permissions: Roles extracted from JWT token: `req.Role` (from `req.user.Role`), roles: `'Issuer'`, `'Market Maker'`, `'Facility Agent'`, `'Lender'`, `'Investor'`, `'Servicer'`, `'Paying Agent'`, `'Admin'`, `'Rating Agency'`
- Access controlled by role: `requireRole(roles)` middleware checks `req.Role` against allowed roles, returns 403 if not authorized
- Actions limited by permissions: Each API endpoint specifies required role(s), e.g., `requireAuth, requireRole('Issuer')` for term sheet creation
- Security enforced: JWT secret key from vault (`getJWTSecretKey()`), token validation on every request, invalid/expired tokens rejected
- Workflow protected: Status checks combined with role checks ensure actions only available to correct role at correct status

---

### Authentication

**What it means:**
- Users must authenticate to access
- JWT tokens for API access
- Secure login process
- Session management
- Access control

**How it works:**
- Login required
- Credentials verified
- Tokens issued
- Sessions managed
- Access controlled

---

## Workflow Controls

### Status-Based Controls

**What it means:**
- Status controls available actions
- Cannot skip workflow steps
- Proper sequence enforced
- Workflow integrity maintained
- Process protected

**How it works:**
- Status determines actions
- Workflow gates control progression
- Cannot bypass steps
- Sequence enforced
- Process protected

---

### Approval Gates

**What it means:**
- Approvals required to proceed
- Cannot skip approvals
- Proper review ensured
- Quality maintained
- Risk controlled

**How it works:**
- Gates block progression
- Approval opens gate
- Review required
- Quality ensured
- Process protected

---

## Data Controls

### Data Validation

**What it means:**
- Data validated before acceptance
- Format checks performed
- Business rules enforced
- Quality maintained
- Errors prevented

**How it works:**
- Validation on input
- Rules enforced
- Errors caught early
- Quality maintained
- Data integrity protected

---

### Data Integrity

**What it means:**
- Data cannot be tampered with
- Blockchain storage for immutability
- Complete audit trail
- History preserved
- Integrity maintained

**How it works:**
- Blockchain storage
- Immutable records
- Audit trail maintained
- History preserved
- Integrity protected

---

## Accountability Measures

### Audit Trails

**What it means:**
- Every action recorded: All API calls that modify data add entries to `actionHistory` arrays
- Complete history maintained: `actionHistory` arrays in `cf_term_sheets`, `cf_master_commitments`, `cf_funding_requests`, `cf_funding_notices` collections preserve all actions
- Who did what when tracked: `userId` (from `req.userId`), `timestamp` (from `DateUtils.nowUTC()`), `action` (descriptive string) stored in each entry
- Full accountability: Complete audit trail enables compliance, dispute resolution, and process understanding
- Compliance enabled: All changes tracked with user IDs and timestamps meet regulatory requirements

**How it works:**
- All actions logged: Database updates use `$push` operator to append to `actionHistory` arrays: `{ action: '...', userId: req.userId || 'system', timestamp: DateUtils.nowUTC(), comments: '...', details: {...} }`
- History preserved: `actionHistory` arrays are never deleted, only appended to, ensuring complete history
- Timestamps recorded: All entries use `DateUtils.nowUTC()` for consistent UTC timestamps
- Users tracked: `req.userId` extracted from JWT token (`req.user.userId`) and stored in each entry
- Complete records: `details` object stores related information (previous/new status, affected entities, transaction hashes, etc.)

---

### Status History

**What it means:**
- All status changes recorded
- Who changed what tracked
- When changes occurred
- Why changes made
- Complete history

**How it works:**
- Status changes logged
- Users recorded
- Timestamps maintained
- Reasons documented
- History preserved

---

## Security Controls

### Document Security

**What it means:**
- Documents stored securely
- IPFS storage for security
- Access controlled
- Integrity maintained
- Security ensured

**How it works:**
- Secure storage
- Access control
- Integrity checks
- Security measures
- Protection maintained

---

### Transaction Security

**What it means:**
- Transactions secured
- Blockchain for security
- Immutable records
- Secure processing
- Protection ensured

**How it works:**
- Blockchain security
- Immutable records
- Secure processing
- Protection measures
- Security maintained

---

## Compliance Controls

### Regulatory Compliance

**What it means:**
- Regulatory requirements met
- Compliance maintained
- Standards enforced
- Requirements satisfied
- Compliance ensured

**How it works:**
- Rules enforced
- Standards maintained
- Requirements met
- Compliance verified
- Regulatory alignment

---

### Governance

**What it means:**
- Proper governance maintained
- Rules enforced
- Standards maintained
- Process controlled
- Governance ensured

**How it works:**
- Governance rules
- Standards enforced
- Process controlled
- Quality maintained
- Governance protected

---

## Best Practices

1. **Understand controls**: Know what controls exist
2. **Work within controls**: Don't try to bypass
3. **Respect workflow**: Follow proper process
4. **Maintain security**: Keep credentials secure
5. **Support compliance**: Help maintain compliance

---

## Key Takeaways

1. **Multiple controls**: Access, workflow, data, security controls
2. **Accountability**: Complete audit trails and tracking
3. **Security**: Multiple security measures
4. **Compliance**: Regulatory compliance maintained
5. **Governance**: Proper governance enforced

Understanding controls and accountability helps you appreciate how the platform maintains security, compliance, and proper governance while enabling efficient workflows.

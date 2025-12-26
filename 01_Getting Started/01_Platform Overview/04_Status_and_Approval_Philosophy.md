# Status & Approval Philosophy

## Understanding Statuses

### What is a Status?

A status is the current state of an item (pool, loan, term sheet, funding request, etc.) in the platform. It tells you:
- Where the item is in its workflow
- What actions are currently available
- What needs to happen next
- Who can take action

### Why Statuses Matter

Statuses control:
- What you can do: Some actions are only available at certain statuses
- Who can act: Different roles can act at different statuses
- Workflow progression: Statuses ensure things happen in the right order
- Visibility: Some statuses make items visible to different parties

---

## Status Philosophy

### Status Represents Business State

A status doesn't just indicate "editable" or "not editable" - it represents the **actual business state** of the item:

- **"Draft"** means the item is being prepared and can be edited
- **"FAReview"** means it's been submitted and is waiting for facility agent review
- **"Approved"** means it's been approved and may trigger automatic next steps
- **"Rejected"** means it's been rejected and is in a final state

### Status Changes Are Meaningful

When a status changes, it means:
- A business event occurred (submission, approval, rejection)
- The workflow has progressed
- Different actions may now be available
- Other parties may be notified

### Status History is Preserved

Every status change is recorded with:
- Who changed it
- When it changed
- What the previous status was
- Why it changed (if applicable)

This creates a complete audit trail.

---

## Approval Philosophy

### Why Approvals Exist

Approvals ensure:
- **Quality**: Items meet standards before proceeding
- **Compliance**: Regulatory and business rules are followed
- **Risk Management**: Proper review before commitments
- **Transparency**: Clear decision points in the workflow

### Approval Gates

Approvals act as gates in the workflow:
- You can't proceed until the gate is opened (approval received)
- Some gates require specific roles (e.g., only facility agents can approve term sheets)
- Gates can be one-way (rejection stops the workflow) or two-way (changes can be requested)

### Types of Approvals

**Single Approval**
- One party approves (e.g., facility agent approves term sheet)
- Workflow proceeds immediately after approval

**Multi-Party Approval**
- Multiple parties must approve (e.g., lenders approve master commitment)
- Any one approval may be sufficient (e.g., any lender approval activates facility)
- Or all approvals may be required (depending on business rules)

**Sequential Approval**
- Approvals happen in order (e.g., term sheet → master commitment → funding request)
- Each approval unlocks the next step

---

## Status Flow Patterns

### Forward Progression (Happy Path)

```
Draft → Submitted → Under Review → Approved → Active/Completed
```

This is the ideal flow where everything proceeds smoothly.

### Rejection Path

```
Draft → Submitted → Under Review → Rejected (FINAL)
```

Rejection is usually a final state - the item stops here.

### Change Request Path

```
Draft → Submitted → Under Review → Changes Requested → Draft → Submitted → ...
```

When changes are requested:
- Status changes to "Changes Requested"
- Item becomes editable again
- User makes changes
- Item is resubmitted
- Cycle can repeat if needed

### Auto-Creation Patterns

Some approvals trigger automatic creation:
- **Term Sheet Approved** → Auto-creates Master Commitment
- **Funding Request Approved** → Auto-generates Funding Notice

These automatic steps ensure workflow continuity.

---

## Understanding Enabled vs Disabled Actions

### Why Actions Are Enabled

An action button is enabled when:
- You have permission (your role allows it)
- The status allows it (workflow permits this action)
- Required information is present (all mandatory fields filled)
- Prerequisites are met (previous steps completed)

### Why Actions Are Disabled

An action button is disabled when:
- Wrong status: The item isn't in the right status for this action
- Missing information: Required fields aren't filled
- Waiting for others: Another party needs to act first
- Already completed: This action was already taken
- No permission: Your role doesn't allow this action

### Understanding Disabled Actions

When you see a disabled button:
1. Hover over it: Often shows a tooltip explaining why
2. Check status: Verify the current status
3. Check requirements: See if any fields are missing
4. Check workflow: See if previous steps are complete
5. Read messages: Look for status messages explaining the situation

---

## Status During Revisions

### Important Concept: Status During Changes

When changes are requested:
- Status remains "Changes Requested" while you work
- You can edit and save multiple times
- Status only changes when you resubmit
- This prevents confusion between new drafts and revision work

### Why This Matters

- Clear context: You always know you're working on requested changes
- No confusion: Distinguishes revision work from new creation
- Audit trail: Status history shows the full revision story
- Business logic: Status reflects actual business state, not just editability

---

## Status Visibility

### Who Sees What Status

Different parties see items at different statuses:
- Draft items: Usually only visible to creator
- Submitted items: Visible to reviewers
- Approved items: Visible to next parties in workflow
- Active items: Visible to all relevant parties

### Status-Based Visibility

Some statuses control visibility:
- "TOKEN_APPROVED" funding notices become visible to lenders
- "ACTIVE" master commitments allow funding requests
- "BorrowerSigned" term sheets allow preview by issuer

---

## Best Practices

### Before Taking Action

1. Check the status: Understand where the item is
2. Read status messages: They explain what's happening
3. Review requirements: Ensure prerequisites are met
4. Understand consequences: Know what happens after your action

### When Status Changes

1. Read notifications: You'll be notified of status changes
2. Check what's enabled: New actions may be available
3. Review history: See who changed what and when
4. Take next steps: Proceed with available actions

### Understanding Workflow

1. Follow the flow: Statuses guide you through the process
2. Don't skip steps: Workflow ensures proper order
3. Read messages: Status messages explain what's needed
4. Ask if unsure: Contact support if workflow is unclear

---

## Common Status Patterns

### Pool Statuses
- Created → Preview → Mandate Pending → Deal

### Loan Statuses
- Unmapped → Mapped → Submitted → Verified

### Term Sheet Statuses
- Draft → BorrowerSigned → FAReview → Accepted/Rejected/Changes Requested

### Master Commitment Statuses
- Draft → PendingLenderApproval → ACTIVE

### Funding Request Statuses
- DRAFT → FAReview → APPROVED/REJECTED/CHANGES_REQUESTED

### Funding Notice Statuses
- PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED

---

## Key Takeaways

1. Status = Business State: Status reflects where you are in the real business process
2. Status Controls Actions: What you can do depends on status
3. Status Changes Are Meaningful: Each change represents a business event
4. History is Preserved: Every change is recorded for audit
5. Workflow Guides You: Status progression ensures proper order
6. Messages Explain: Status messages help you understand what's happening
7. Disabled = Reason: Disabled actions have clear reasons

Understanding statuses and approvals helps you navigate the platform effectively and know what to expect at each stage of your workflow.

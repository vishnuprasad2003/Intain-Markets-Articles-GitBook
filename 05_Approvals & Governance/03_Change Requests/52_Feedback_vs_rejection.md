# Feedback vs Rejection

## Overview

Understanding the difference between feedback (change requests) and rejection helps you know how to respond and what to expect. Both are part of the review process but have different implications.

## Change Requests (Feedback)

### What They Are

**Change requests:**
- Request for modifications
- Issues can be fixed
- Iterative improvement process
- Not a final state
- Opportunity to improve

**What they mean:**
- Item has potential
- Issues are fixable
- Can proceed after changes
- Workflow continues
- Improvement opportunity

---

### What Happens

**When changes requested:**
- Status changes to `'CHANGES_REQUESTED'` (via `POST /cf/requestChanges/:termSheetId` for term sheets or `POST /cf/funding-requests/:fundingRequestId/request-changes` for funding requests)
- Database update:
  - **Term Sheets** (`cf_term_sheets`): `revisionNumber` incremented, current version saved to `previousVersions` array, `changeRequests` array updated, `changeRequestsCount` incremented, DocuSign status may reset
  - **Funding Requests** (`cf_funding_requests`): `revisionNumber` incremented, current version saved to `previousVersions` array, `changeRequests` array updated
- Item becomes editable again: auto-save re-enabled, can edit fields
- You can make modifications: full editing access restored
- Can save multiple times: auto-save functionality enabled
- Can resubmit when ready: status changes back to review status when resubmitted

**After making changes:**
- Make requested modifications
- Update as needed
- Resubmit for review
- Status changes back to review
- Process continues

---

### How to Respond

**Best approach:**
1. Read change request carefully
2. Understand what needs to change
3. Make all requested modifications
4. Address all items
5. Resubmit when complete

**Tips:**
- Don't miss any requested changes
- Be thorough in addressing items
- Provide clarity if needed
- Resubmit promptly
- Keep workflow moving

---

## Rejection

### What It Is

**Rejection:**
- Final decision
- Item will not proceed
- Cannot be fixed
- Final state
- Must create new item

**What it means:**
- Item doesn't meet requirements
- Issues cannot be fixed
- Process stops here
- No further action possible
- Must start over

---

### What Happens

**When rejected:**
- Status changes to `'Rejected'` (term sheets) or `'REJECTED'` (funding requests) - final state
- Database update:
  - **Term Sheets** (`cf_term_sheets`): Status set to `'Rejected'`, `statusHistory` and `actionHistory` updated, no master commitment created
  - **Funding Requests** (`cf_funding_requests`): Status set to `'REJECTED'`, `rejectionReason` stored, `statusHistory` and `actionHistory` updated, no funding notice created
- Item becomes read-only: cannot edit any fields
- Cannot be edited: editing blocked by status validation (code checks: `status !== 'Rejected'` or `status !== 'REJECTED'`)
- Cannot be resubmitted: submission blocked (code validates status before allowing submission)
- Process stops: workflow terminates, no automatic actions triggered

**After rejection:**
- No further action on rejected item
- Must create new item to try again
- Can learn from rejection
- Can improve for next time

---

## Key Differences

### Change Requests

**Characteristics:**
- Not final
- Can be fixed
- Iterative process
- Workflow continues
- Improvement opportunity

**Response:**
- Make changes
- Resubmit
- Continue workflow

---

### Rejection

**Characteristics:**
- Final state
- Cannot be fixed
- Process stops
- Must create new
- No further action

**Response:**
- Learn from rejection
- Create new item
- Start over

---

## Understanding the Difference

### Change Request = Opportunity

**Think of it as:**
- Chance to improve
- Guidance for better outcome
- Iterative refinement
- Collaborative process
- Path to approval

**Your response:**
- Make changes
- Improve item
- Resubmit
- Get approved

---

### Rejection = Final Decision

**Think of it as:**
- Final assessment
- Cannot proceed
- Must start over
- Learning opportunity
- Chance to improve next time

**Your response:**
- Accept decision
- Learn from it
- Create new item
- Improve for next time

---

## Best Practices

### For Change Requests

1. Respond promptly: Address changes quickly
2. Be thorough: Don't miss any items
3. Make improvements: Better than before
4. Resubmit confidently: Improved version
5. Keep moving: Don't delay workflow

### For Rejections

1. Accept decision: Understand it's final
2. Learn from it: Understand why rejected
3. Don't repeat: Fix issues for next time
4. Create new: Start fresh with improvements
5. Be persistent: Don't give up

---

## Common Scenarios

### Scenario 1: Change Request Success

1. Item submitted → Changes requested
2. Make changes → Address all items
3. Resubmit → Improved version
4. Review again → Gets approved
5. Success → Process continues

### Scenario 2: Rejection Then Success

1. Item submitted → Rejected
2. Review reason → Understand issues
3. Create new item → Address problems
4. Submit improved → Better quality
5. Gets approved → Success

---

## Key Takeaways

1. Change requests = Opportunity: Chance to improve and resubmit
2. Rejection = Final: Must create new item to try again
3. Different responses: Different approaches for each
4. Both are learning: Both provide feedback for improvement
5. Move forward: Don't get stuck, keep improving

Understanding feedback vs rejection helps you know how to respond appropriately and improve your submissions for better outcomes.

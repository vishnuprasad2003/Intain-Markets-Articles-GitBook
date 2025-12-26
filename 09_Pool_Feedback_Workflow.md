# Pool Feedback Workflow

## Overview

The feedback workflow allows market makers, investors, and other parties to provide input on pools shared with them. This collaborative process helps improve pool quality and ensures all parties are aligned before finalizing deals.

## Types of Feedback

### Feedback Levels

The system supports two levels of feedback:

**Pool-Level Feedback**
- Feedback about the entire pool
- `level: "pool"` in database
- `loanId: null` or doesn't exist
- Retrieved via: `GET /:poolId/feedback` (returns pool-level feedbacks)
- Stored in MongoDB `pool_feedback` collection

**Loan-Level Feedback**
- Feedback about specific loans
- `level: "loan"` in database
- `loanId: <specific loan ID>` field populated
- Retrieved via: `GET /:poolId/loans/feedback` (returns loan-level feedbacks grouped by loanId)
- Or for specific loan: `GET /:poolId/loans/:loanId/feedback`
- Stored in MongoDB `pool_feedback` collection

### Feedback Types

**Change Requests (`type: "change_request"`)**
- Formal request for modifications
- Usually from market makers reviewing pools
- Requires issuer to make changes and resubmit
- Can be pool-level or loan-level

**General Feedback (`type: "feedback"` - default)**
- Comments, questions, or suggestions
- Can come from any shared party (if `allowFeedBack: true` in `shareOptions`)
- Doesn't require status change
- Can be pool-level or loan-level

### Feedback Data Structure

Each feedback document in `pool_feedback` collection contains:
```javascript
{
  feedbackId: "feedback_<timestamp>_<random>",  // Unique feedback ID
  poolId: "<poolId>",                          // Pool ID (required)
  loanId: "<loanId>" | null,                   // Loan ID (null for pool-level)
  level: "pool" | "loan",                      // Determined by loanId presence
  type: "feedback" | "change_request",         // Feedback type
  message: "<feedback text>",                  // Feedback message (trimmed)
  createdBy: "<userId>",                       // User ID who created feedback
  createdByOrgId: "<orgId>",                   // Organization ID who created feedback
  createdUserName: "<userName>",               // User name (optional)
  createOrgName: "<orgName>",                  // Organization name (optional)
  createdAt: <UTC timestamp>,                  // Creation timestamp
  readBy: [<userId>, ...],                     // Array of user IDs who read feedback
  viewedBy: [<orgId>, ...]                     // Array of org IDs who viewed feedback
}
```

### Attention Indicators

**What it is:**
- Visual markers highlighting areas needing attention
- Flags or badges on specific items
- Alerts about potential issues

**When it happens:**
- System detects potential issues
- Reviewers flag concerns
- Validation identifies problems

**What happens:**
- Visual indicators appear
- Issuer sees what needs attention
- Can address flagged items

---

## Feedback Process

### Step 1: Review

**Reviewer's perspective:**
- Market maker or investor reviews pool via `/getbypoolid?poolId=...`
- Analyzes metrics and loan details via `/getpreviewstdloantapeusinglatestdate?poolId=...`
- Identifies areas needing attention (pool-level or specific loans)
- Decides on feedback type (general feedback or change request)

**Prerequisites:**
- Organization must be in `shareOptions` with `allowFeedBack: true`
- User must have valid `userId` and `orgId`
- Pool must be shared with the organization

### Step 2: Provide Feedback

**Add Pool-Level Feedback:**
- Endpoint: `POST /:poolId/feedback`
- Request body:
  ```javascript
  {
    poolId: "<poolId>",           // Required
    loanId: null,                  // null for pool-level (or omit)
    userId: "<userId>",            // Required
    message: "<feedback text>",   // Required, non-empty after trim
    type: "feedback" | "change_request",  // Optional, defaults to "feedback"
    orgId: "<orgId>",              // Required
    userName: "<userName>",        // Optional
    orgName: "<orgName>"           // Optional
  }
  ```
- System creates feedback with `level: "pool"` (determined by `loanId` being null)
- Feedback stored in `pool_feedback` collection
- Returns created feedback object with `feedbackId`

**Add Loan-Level Feedback:**
- Endpoint: `POST /:poolId/feedback`
- Request body:
  ```javascript
  {
    poolId: "<poolId>",           // Required
    loanId: "<loanId>",           // Required for loan-level
    userId: "<userId>",           // Required
    message: "<feedback text>",   // Required, non-empty after trim
    type: "feedback" | "change_request",  // Optional
    orgId: "<orgId>",             // Required
    userName: "<userName>",       // Optional
    orgName: "<orgName>"          // Optional
  }
  ```
- System creates feedback with `level: "loan"` (determined by `loanId` being present)
- Feedback stored in `pool_feedback` collection
- Returns created feedback object

**Validation:**
- `poolId` is required (throws error if missing)
- `userId` is required (throws error if missing)
- `message` is required and cannot be empty after trimming (throws error if empty)
- `orgId` is required (used for `createdByOrgId` and `viewedBy`)

### Step 3: View Feedback

**View Pool-Level Feedback:**
- Endpoint: `GET /:poolId/feedback`
- Returns all pool-level feedbacks (`level: "pool"`) for the pool
- Sorted by `createdAt` descending (newest first)
- Each feedback includes: `feedbackId`, `message`, `createdBy`, `createdByOrgId`, `createdUserName`, `createOrgName`, `createdAt`, `readBy`, `viewedBy`

**View Loan-Level Feedback (All Loans):**
- Endpoint: `GET /:poolId/loans/feedback`
- Returns loan-level feedbacks grouped by `loanId`
- Each group includes: `loanId`, `feedbackCount`, `feedbacks[]` array, `latestFeedback` timestamp
- Sorted by `latestFeedback` descending (loans with newest feedback first)

**View Loan-Level Feedback (Specific Loan):**
- Endpoint: `GET /:poolId/loans/:loanId/feedback`
- Returns all feedbacks for specific loan ID
- Sorted by `createdAt` descending

**Mark Feedback as Read:**
- Endpoint: `PATCH /:poolId/feedback/view`
- Request body: `{ poolId, userId, orgId, loanId: <loanId> | null }`
- Updates all matching feedbacks:
  - Adds `userId` to `readBy` array (if not already present, using `$addToSet`)
  - Adds `orgId` to `viewedBy` array (if not already present, using `$addToSet`)
- For loan-level: matches `loanId` and `level: "loan"`
- For pool-level: matches `loanId: null` and `level: "pool"`

### Step 4: Response

**Issuer can:**
- Review all feedback via feedback endpoints
- See unread feedback indicators (loans with feedback not in `viewedBy` array)
- Make requested changes to pool or loans
- Respond to comments (by adding new feedback)
- Address flagged items
- Resubmit pool if changes requested

**Unread Feedback Tracking:**
- When viewing loans via `/getpreviewstdloantapeusinglatestdate`, system checks `pool_feedback` collection
- Finds loan-level feedbacks where `viewedBy` array doesn't include current `orgId`
- Groups by `loanId` and counts feedbacks
- Adds `feedbackCount` field to loans with unread feedback
- Loans with unread feedback are prioritized in results

---

## Change Request Workflow

### Initiating Change Request

**Who can request:**
- Market makers reviewing pools
- Facility agents (in some contexts)
- Other authorized reviewers

**How to request:**
1. Review pool details
2. Identify issues or needed changes
3. Click "Request Changes" button
4. Fill in change request form:
   - What needs to change
   - Why it needs to change
   - Specific details or requirements
5. Submit change request

### Change Request Details

**Required information:**
- Description of requested changes
- Reason for changes
- Priority level (if applicable)
- Deadline (if applicable)

**Optional information:**
- Specific field or section references
- Examples or suggestions
- Supporting documentation
- Related items

### Status Impact

**When change requested:**
- Pool status may change to reflect feedback needed
- Pool may become editable again
- Issuer can make changes
- Status remains "Changes Requested" during editing

**After changes made:**
- Issuer updates pool
- Resubmits for review
- Status changes back to review status
- Cycle can repeat if needed

---

## Comments and Discussion

### Adding Comments

**Where comments appear:**
- On pool overview page
- On specific sections
- On individual loans (if applicable)
- In discussion threads

**Comment features:**
- Text comments
- @mentions to tag parties
- Attachments (if allowed)
- Timestamps
- Author information

### Comment Threads

**How it works:**
- Comments create discussion threads
- Parties can reply to comments
- Threads are visible to relevant parties
- Keeps conversation organized

### Best Practices

- Be specific and clear
- Reference specific items
- Provide context
- Be constructive
- Respond promptly

---

## Attention Indicators

### Types of Indicators

**Visual Flags:**
- Icons or badges on items
- Color coding (red, yellow, green)
- Warning symbols
- Attention markers

**What they indicate:**
- Missing information
- Data quality issues
- Validation errors
- Items needing review
- Potential problems

### Understanding Indicators

**Red/High Priority:**
- Critical issues
- Blocking problems
- Must be addressed

**Yellow/Medium Priority:**
- Important issues
- Should be addressed
- May block progress

**Green/Low Priority:**
- Minor issues
- Suggestions
- Nice to have

### Addressing Indicators

**When you see indicators:**
1. Review what's flagged
2. Understand the issue
3. Take appropriate action
4. Indicators update when resolved

---

## Responding to Feedback

### As an Issuer

**When you receive feedback:**

1. **Review all feedback**
   - Read change requests carefully
   - Check comments and questions
   - Note attention indicators

2. **Prioritize actions**
   - Address critical issues first
   - Handle blocking problems
   - Then address other feedback

3. **Make changes**
   - Update pool information
   - Fix identified issues
   - Address comments
   - Resolve flagged items

4. **Communicate**
   - Respond to comments
   - Explain changes made
   - Ask questions if unclear
   - Confirm completion

5. **Resubmit**
   - When changes complete
   - Resubmit for review
   - Status updates accordingly

### Best Practices

- **Respond promptly**: Don't leave feedback unanswered
- **Be thorough**: Address all feedback items
- **Communicate clearly**: Explain what you changed
- **Ask questions**: Clarify if feedback is unclear
- **Track progress**: Ensure all items addressed

---

## Feedback Visibility

### Who Sees What

**Change Requests:**
- Visible to issuer and requester
- May be visible to other relevant parties
- Tracked in status history

**Comments:**
- Visible to pool creator and commenter
- May be visible to all shared parties
- Depends on sharing settings

**Attention Indicators:**
- Visible to pool creator
- May be visible to reviewers
- System-generated indicators

---

## Common Scenarios

### Scenario 1: Multiple Change Requests

1. Market maker requests changes
2. Issuer makes changes
3. Resubmits pool
4. Market maker requests more changes
5. Process repeats until approved

### Scenario 2: Comments Discussion

1. Investor adds comment with question
2. Issuer responds with clarification
3. Discussion continues
4. Issue resolved through discussion

### Scenario 3: Attention Indicators

1. System flags missing information
2. Issuer sees indicators
3. Adds missing information
4. Indicators clear automatically

---

## Best Practices

### For Reviewers

1. **Be specific**: Clearly state what needs to change
2. **Explain why**: Help issuer understand reasoning
3. **Prioritize**: Focus on important issues first
4. **Be constructive**: Provide helpful feedback
5. **Follow up**: Check if changes addressed concerns

### For Issuers

1. **Review promptly**: Don't ignore feedback
2. **Address thoroughly**: Fix all identified issues
3. **Communicate**: Let reviewers know what you did
4. **Ask questions**: Clarify unclear feedback
5. **Track completion**: Ensure nothing missed

---

## Troubleshooting

### "Feedback not received"
- Check notifications
- Verify pool sharing settings
- Ensure correct email/account
- Check spam folder

### "Can't respond to feedback"
- Verify pool status allows editing
- Check you have permission
- Ensure feedback is still active
- Contact support if needed

### "Indicators not clearing"
- Verify issue is actually resolved
- Check if other issues remain
- Refresh page
- Contact support if persists

---

## Key Takeaways

1. **Feedback enables collaboration**: Improves pool quality through input
2. **Multiple feedback types**: Change requests, comments, indicators
3. **Clear process**: Review → Feedback → Response → Resubmit
4. **Status tracking**: Status reflects feedback state
5. **Communication important**: Clear communication improves outcomes

Understanding the feedback workflow helps you effectively collaborate with other parties and improve your pools through constructive input and iteration.

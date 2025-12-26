# Term Sheet Change Requests

## Overview

When a facility agent reviews a term sheet and needs modifications, they can request changes. This allows borrowers to update the term sheet and resubmit it for review, creating an iterative improvement process.

## What Are Change Requests?

### Definition

A change request is when the facility agent:
- Identifies issues or needed modifications in the term sheet
- Formally requests the borrower to make changes
- Provides details about what needs to change
- Allows the borrower to edit and resubmit

### Purpose

Change requests enable:
- **Iterative improvement**: Refine term sheets through feedback
- **Compliance**: Ensure term sheets meet requirements
- **Clarity**: Address unclear or incomplete information
- **Negotiation**: Adjust terms through discussion

---

## Change Request Process

### Step 1: Facility Agent Reviews

**Facility agent:**
- Reviews submitted term sheet
- Analyzes facility terms
- Identifies issues or needed changes
- Decides to request changes

### Step 2: Facility Agent Requests Changes

**Facility agent actions:**
1. Clicks "Request Changes" button
2. Fills in change request form:
   - What needs to change
   - Why changes are needed
   - Specific requirements
   - Priority level (if applicable)
   - Deadline (if applicable)
3. Submits change request

### Step 3: Status Changes

**What happens automatically:**
- Term sheet status changes to "CHANGES_REQUESTED"
- Revision number increments
- Current version saved to previousVersions
- DocuSign status may reset (requires re-signing)
- Auto-save functionality re-enabled
- Change request record created with:
  - Request details
  - Requested by (facility agent)
  - Requested at (timestamp)
  - Comments

### Step 4: Borrower Receives Notification

**Borrower sees:**
- Notification about change request
- Change request details
- What needs to be modified
- Why changes are needed
- Any deadlines or priorities

### Step 5: Borrower Makes Changes

**Borrower actions:**
1. Reviews change request details
2. Opens term sheet for editing
3. Makes requested modifications
4. Updates documents if needed
5. Saves changes (can save multiple times)
6. Status remains "CHANGES_REQUESTED" during editing

### Step 6: Borrower Resubmits

**Borrower actions:**
1. Completes all requested changes
2. Re-signs via DocuSign (if required)
3. Clicks "Resubmit" or "Submit"
4. Status changes back to "FAReview"
5. Facility agent reviews again

---

## Change Request Details

### What Can Be Requested

**Term Changes:**
- Facility amount adjustments
- Interest rate modifications
- Maturity date changes
- Advance rate adjustments
- Pricing index changes

**Document Updates:**
- Additional documents needed
- Document revisions required
- Supporting information needed
- Clarifications requested

**Information Clarifications:**
- Missing information
- Unclear details
- Additional explanations needed
- Data corrections

### Change Request Information

**Required Information:**
- Description of requested changes
- Reason for changes
- Specific requirements

**Optional Information:**
- Priority level
- Deadline for resubmission
- Specific field references
- Examples or suggestions
- Supporting documentation

---

## Status During Changes

### Important Concept

Status remains "CHANGES_REQUESTED" during editing:
- You work on changes while status is "CHANGES_REQUESTED"
- Status only changes when you resubmit
- This prevents confusion between new drafts and revision work
- Clear indication you're working on requested changes

### Why This Matters

- Clear context: Always know you're working on requested changes
- No confusion: Distinguishes revision work from new creation
- Audit trail: Status history shows full revision story
- Business logic: Status reflects actual business state

---

## Making Changes

### Editing Process

**What you can edit:**
- All term sheet fields (when status allows)
- Documents (upload new versions)
- Any information requested

**How to edit:**
1. Open term sheet (status shows "CHANGES_REQUESTED")
2. Edit fields as needed
3. Upload new documents if required
4. Save changes (auto-save enabled)
5. Can save multiple times
6. Review changes before resubmitting

### Re-signing Requirements

**When re-signing needed:**
- If documents changed significantly
- If key terms modified
- System may require re-signing
- DocuSign status resets

**Re-signing process:**
1. Make requested changes
2. Initiate DocuSign again
3. Sign updated documents
4. Status changes to "BorrowerSigned"
5. Then resubmit

---

## Resubmission

### When to Resubmit

**Ready to resubmit when:**
- All requested changes completed
- Documents updated (if needed)
- Re-signed (if required)
- Information verified
- Ready for facility agent review

### Resubmission Process

**Steps:**
1. Review change request checklist
2. Verify all changes addressed
3. Ensure documents current
4. Complete DocuSign if needed
5. Click "Resubmit" or "Submit"
6. Status changes to "FAReview"
7. Facility agent reviews again

### After Resubmission

**What happens:**
- Status changes to "FAReview"
- Facility agent receives notification
- Facility agent reviews updated term sheet
- Can approve, reject, or request more changes

---

## Multiple Change Requests

### Iterative Process

**Can happen multiple times:**
1. First change request → Make changes → Resubmit
2. Second change request → Make changes → Resubmit
3. Continue until approved or rejected

**Each iteration:**
- Revision number increments
- Previous version saved
- Change request history maintained
- Full audit trail preserved

### Change Request History

**You can see:**
- All change requests received
- What was requested each time
- When requests were made
- Who requested changes
- How you responded

---

## Best Practices

### Responding to Change Requests

1. **Read carefully**: Understand all requested changes
2. **Address completely**: Don't miss any requested items
3. **Be thorough**: Make all necessary changes
4. **Verify accuracy**: Check changes are correct
5. **Resubmit promptly**: Keep workflow moving

### Making Changes

1. **Follow instructions**: Make changes as requested
2. **Provide clarity**: Add explanations if helpful
3. **Update documents**: Include new/updated documents
4. **Save frequently**: Use auto-save feature
5. **Review before resubmit**: Verify completeness

### Communication

1. **Ask questions**: Clarify if requests unclear
2. **Provide context**: Explain changes if needed
3. **Respond promptly**: Don't delay unnecessarily
4. **Be professional**: Maintain good communication

---

## Common Scenarios

### Scenario 1: Simple Changes

1. Facility agent requests amount adjustment
2. Borrower updates amount field
3. Saves changes
4. Resubmits
5. Facility agent approves

### Scenario 2: Multiple Changes

1. Facility agent requests several changes
2. Borrower addresses all items
3. Updates multiple fields
4. Uploads new documents
5. Re-signs and resubmits
6. Facility agent approves

### Scenario 3: Iterative Refinement

1. First change request → Borrower makes changes → Resubmits
2. Second change request → Borrower makes more changes → Resubmits
3. Third review → Facility agent approves

### Scenario 4: Re-signing Required

1. Facility agent requests document changes
2. Borrower updates documents
3. System requires re-signing
4. Borrower completes DocuSign
5. Status becomes "BorrowerSigned"
6. Borrower resubmits
7. Facility agent reviews

---

## Troubleshooting

### "Can't see change request details"
- Check notifications
- Look for change request section in term sheet
- Verify term sheet status is "CHANGES_REQUESTED"
- Contact support if missing

### "Can't edit term sheet"
- Verify status is "CHANGES_REQUESTED"
- Check you have permission
- Ensure term sheet not locked
- Refresh page if needed

### "Changes not saving"
- Check auto-save is enabled
- Verify internet connection
- Try manual save
- Contact support if persists

### "Can't resubmit"
- Verify all changes completed
- Check if re-signing required
- Ensure status is "CHANGES_REQUESTED" or "BorrowerSigned"
- Verify all required fields filled

---

## Key Takeaways

1. **Change requests enable improvement**: Iterative refinement process
2. **Status tracks revision work**: "CHANGES_REQUESTED" during editing
3. **Multiple iterations possible**: Can go through several rounds
4. **Re-signing may be required**: If documents or key terms change
5. **Complete audit trail**: All changes and requests tracked

Understanding term sheet change requests helps you effectively respond to facility agent feedback and refine your term sheets through the iterative review process.

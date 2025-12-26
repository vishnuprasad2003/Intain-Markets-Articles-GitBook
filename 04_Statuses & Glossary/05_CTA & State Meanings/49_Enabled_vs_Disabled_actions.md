# Enabled vs Disabled Actions

## Overview

Understanding why actions are enabled or disabled helps you know what you can do and why certain actions aren't available. This guide explains the logic behind enabled and disabled buttons and actions.

## Why Actions Are Enabled

### You Have Permission

**Enabled when:**
- Your role allows the action
- You have access to the item
- You're assigned to the item
- Permissions are granted

**Examples:**
- Issuers can create pools (they have permission)
- Facility agents can approve term sheets (they have permission)
- Lenders can approve master commitments (they have permission)

---

### Status Allows It

**Enabled when:**
- Item is in correct status for action
- Workflow permits this action
- Status progression allows it
- Not blocked by current status

**Examples:**
- Can submit term sheet when status is BorrowerSigned
- Can approve funding request when status is FAReview
- Can create funding request when master commitment is ACTIVE

---

### Prerequisites Met

**Enabled when:**
- Required information is present
- Previous steps completed
- Dependencies satisfied
- All requirements met

**Examples:**
- Can submit term sheet after DocuSign completed
- Can approve funding request after review complete
- Can create funding request after master commitment ACTIVE

---

## Why Actions Are Disabled

### Wrong Status

**Disabled when:**
- Item isn't in right status for action
- Workflow doesn't permit action
- Status blocks the action
- Wrong stage in workflow

**Examples:**
- Can't submit term sheet when status is Draft (must sign first)
- Can't approve funding request when status is DRAFT (must be FAReview)
- Can't create funding request when master commitment is Draft (must be ACTIVE)

---

### Missing Information

**Disabled when:**
- Required fields not filled
- Documents not uploaded
- Information incomplete
- Prerequisites missing

**Examples:**
- Can't submit term sheet without required fields
- Can't approve funding request without documentation
- Can't create funding request without active facility

---

### Waiting for Others

**Disabled when:**
- Another party needs to act first
- Previous step not completed
- Dependency not satisfied
- Waiting for action

**Examples:**
- Can't approve funding request until borrower submits
- Can't create funding request until lender approves master commitment
- Can't approve tokens until facility agent signs

---

### Already Completed

**Disabled when:**
- Action already taken
- Status already changed
- Process already done
- No need to repeat

**Examples:**
- Can't submit again if already submitted
- Can't approve again if already approved
- Can't sign again if already signed

---

### No Permission

**Disabled when:**
- Your role doesn't allow action
- You don't have access
- Not assigned to item
- Permissions not granted

**Examples:**
- Borrowers can't approve their own term sheets
- Lenders can't create funding requests
- Issuers can't approve master commitments

---

## Understanding Disabled Actions

### Check Tooltips

**Hover over disabled buttons:**
- Often shows tooltip explaining why
- Provides specific reason
- Tells you what's needed
- Guides you on next steps

### Check Status Messages

**Look for messages:**
- Status messages explain situation
- Show what's blocking action
- Indicate what needs to happen
- Provide guidance

### Check Requirements

**Review requirements:**
- Check if all fields filled
- Verify documents uploaded
- Ensure prerequisites met
- Confirm status is correct

---

## Common Patterns

### Pattern 1: Status-Based

**Enabled:**
- Action available at specific status
- Status progression allows it

**Disabled:**
- Wrong status for action
- Workflow doesn't permit

### Pattern 2: Permission-Based

**Enabled:**
- Your role allows action
- You have permission

**Disabled:**
- Your role doesn't allow
- No permission

### Pattern 3: Prerequisite-Based

**Enabled:**
- All prerequisites met
- Requirements satisfied

**Disabled:**
- Missing prerequisites
- Requirements not met

---

## Best Practices

1. **Check tooltips**: Hover over disabled buttons for explanations
2. **Read messages**: Check status messages for guidance
3. **Verify status**: Ensure item is in correct status
4. **Check requirements**: Verify all prerequisites met
5. **Understand workflow**: Know what needs to happen first

---

## Troubleshooting

### "Action is disabled but I think it should be enabled"
- Check current status
- Verify you have permission
- Check if prerequisites met
- Review tooltip or message
- Contact support if unclear

### "Tooltip says I need X but I have X"
- Verify X is actually present
- Check if X meets requirements
- Ensure X is in correct format
- Refresh page
- Contact support if issue persists

---

## Key Takeaways

1. **Enabled = Available**: You can use enabled actions
2. **Disabled = Reason**: Disabled actions have clear reasons
3. **Check tooltips**: Hover for explanations
4. **Read messages**: Status messages provide guidance
5. **Understand workflow**: Know what enables actions

Understanding enabled vs disabled actions helps you know what you can do and why certain actions aren't available, making the platform easier to navigate.

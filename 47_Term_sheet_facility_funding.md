# Term Sheet, Facility, Funding Statuses

## Overview

This comprehensive guide explains all statuses for credit facility components: Term Sheets, Master Commitments (Facilities), Funding Requests, and Funding Notices. Understanding these statuses helps you navigate the credit facility workflow.

## Term Sheet Statuses

### Draft

**What it means:**
- Term sheet has been created
- Can be edited freely
- Has not been signed yet
- Has not been submitted

**What you can do:**
- Edit all term sheet fields
- Upload documents
- Save changes (auto-save enabled)
- Make multiple revisions

**Next status:**
- BorrowerSigned (after DocuSign)

---

### BorrowerSigned

**What it means:**
- Borrower has completed DocuSign signing
- Term sheet is electronically signed
- Ready for submission to facility agent

**What you can do:**
- Preview the signed term sheet
- Submit for facility agent review
- View signed documents

**Next status:**
- FAReview (when submitted)

---

### FAReview

**What it means:**
- Term sheet submitted to facility agent
- Facility agent is reviewing
- Waiting for facility agent decision

**What you can do:**
- ✅ View term sheet (read-only)
- ✅ See review status
- ✅ Wait for facility agent decision

**Next status:**
- Accepted (if approved)
- Rejected (if rejected)
- CHANGES_REQUESTED (if changes requested)

---

### Accepted

**What it means:**
- Facility agent has approved the term sheet
- Master commitment automatically created
- Facility setup can begin

**What happens:**
- Master commitment created automatically
- Master commitment starts in Draft status
- Term sheet phase complete

**This is final:**
- Term sheet cannot be edited after acceptance

---

### Rejected

**What it means:**
- Facility agent has rejected the term sheet
- Facility will not proceed
- This is a final state

**What happens:**
- No master commitment created
- Term sheet stops here

**This is final:**
- Cannot resubmit same term sheet

---

### CHANGES_REQUESTED

**What it means:**
- Facility agent wants modifications
- Borrower can edit and resubmit
- Not a final state

**What you can do:**
- Edit term sheet fields
- Make requested changes
- Upload new documents
- Resubmit after changes

**Next status:**
- FAReview (when resubmitted)

---

## Master Commitment (Facility) Statuses

### Draft

**What it means:**
- Master commitment auto-created from approved term sheet
- Facility agent can configure it
- Not yet submitted for lender approval

**What facility agent can do:**
- ✅ Configure all facility rules
- ✅ Set up lender groups
- ✅ Define borrowing base calculations
- ✅ Save multiple times

**Next status:**
- PendingLenderApproval (when submitted)

---

### PendingLenderApproval

**What it means:**
- Facility agent has completed configuration
- Submitted for lender approval
- Waiting for lender decision

**What lenders can do:**
- Review master commitment
- Approve via DocuSign
- Any lender approval activates facility

**Next status:**
- ACTIVE (when any lender approves)

---

### ACTIVE

**What it means:**
- Facility is operational
- Approved by at least one lender
- Ready for funding requests

**What borrowers can do:**
- Create funding requests
- Request drawdowns

**This is operational:**
- Facility fully functional
- Funding requests can be created

---

## Funding Request Statuses

### DRAFT

**What it means:**
- Funding request has been created
- Can be edited freely
- Not yet submitted for review

**What borrower can do:**
- Edit all fields
- Upload documents
- Save changes multiple times
- Submit when ready

**Next status:**
- FAReview (when submitted)

---

### FAReview

**What it means:**
- Funding request submitted to facility agent
- Facility agent is reviewing
- Waiting for facility agent decision

**What facility agent can do:**
- Review request details
- Approve, reject, or request changes

**Next status:**
- APPROVED (if approved)
- REJECTED (if rejected)
- CHANGES_REQUESTED (if changes requested)

---

### APPROVED

**What it means:**
- Facility agent has approved the request
- Funding notice automatically generated
- Drawdown can proceed

**What happens:**
- Funding notice created automatically
- Funding notice status: PENDING_TOKEN_GENERATION

**This triggers:**
- Funding notice generation
- Token creation process

---

### REJECTED

**What it means:**
- Facility agent has rejected the request
- Drawdown will not proceed
- This is a final state

**What happens:**
- No funding notice created
- Request remains rejected

**This is final:**
- Cannot resubmit same request

---

### CHANGES_REQUESTED

**What it means:**
- Facility agent wants modifications
- Borrower can edit and resubmit

**What borrower can do:**
- Edit funding request
- Make requested changes
- Resubmit after changes

**Next status:**
- FAReview (when resubmitted)

---

## Funding Notice Statuses

### PENDING_TOKEN_GENERATION

**What it means:**
- Funding notice automatically created
- Waiting for token generation
- Tokens not yet created

**What happens:**
- Funding notice created when request approved
- Token distribution initialized
- Each lender has `esignatureStatus: 'pending'`

**Next status:**
- TOKEN_GENERATED (when tokens created)

---

### TOKEN_GENERATED

**What it means:**
- FT tokens have been created for borrower
- Token distribution updated
- Facility agent can sign for lenders

**What facility agent can do:**
- Sign funding notice for each lender individually
- Complete DocuSign for each lender

**What borrower can do:**
- View funding notice
- Approve token transfer when ready

**Next status:**
- TOKEN_APPROVED (when borrower approves)

---

### TOKEN_APPROVED

**What it means:**
- Borrower has approved token transfer
- Funding notice visible to lenders
- Lenders can review and approve

**What lenders can do:**
- View funding notice
- Review drawdown details
- Approve or reject drawdown
- Confirm fund transfers

**This enables:**
- Lender review and approval
- Individual lender participation
- Fund transfer confirmations

---

## Status Flow Summary

### Complete Credit Facility Flow

```
Term Sheet: Draft → BorrowerSigned → FAReview → Accepted
                                                      ↓
Master Commitment: Draft → PendingLenderApproval → ACTIVE
                                                          ↓
Funding Request: DRAFT → FAReview → APPROVED
                                            ↓
Funding Notice: PENDING_TOKEN_GENERATION → TOKEN_GENERATED → TOKEN_APPROVED
```

---

## Key Takeaways

1. Term sheets: Six statuses from creation to acceptance/rejection
2. Master commitments: Three statuses from creation to activation
3. Funding requests: Five statuses from creation to approval/rejection
4. Funding notices: Three statuses from creation to lender visibility
5. Status progression: Clear workflow from start to finish

Understanding all credit facility statuses helps you navigate the complete workflow from term sheet creation through funding notice completion.

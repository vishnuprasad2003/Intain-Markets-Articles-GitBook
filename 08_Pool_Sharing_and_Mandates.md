# Pool Sharing & Mandates

## Overview

Sharing pools allows you to collaborate with other organizations in the structured finance process. You can share pools with market makers, investors, rating agencies, and other parties who need to review or participate in your transaction.

## Pool Sharing Basics

### What is Sharing?

**Sharing** means giving other organizations access to view your pool. When you share:
- Recipients can see pool details and metrics
- They can review loans and analyze the pool
- They can provide feedback or take actions (depending on their role)
- You maintain control over the pool

### Why Share Pools?

- **Market Makers**: Share to get mandates for structuring deals
- **Investors**: Share to attract investment interest
- **Rating Agencies**: Share to get pool ratings
- **Partners**: Share with partners involved in the transaction

---

## Sharing Options

### Who Can You Share With?

**Market Makers**
- For structuring and underwriting
- Add their `marketMakerOrgId` to `marketMakerOrgId[]` array in pool
- Configure sharing via `POST /configureShareOptions` with `{ marketMakerOrgId: [...] }`
- They appear in `shareOptions` object: `shareOptions[marketMakerOrgId] = { allowFeedBack, allowDownload, orgName, orgType }`
- Can accept mandates to become the market maker (via `poolShareOptions`)

**Investors**
- For investment opportunities
- Add their `investorOrgId` to `investorOrgId[]` array in pool
- Configure sharing via `POST /configureShareOptions` with `{ investorOrgId: [...] }`
- They appear in `shareOptions` object with permissions
- Can review and evaluate pools via `/previewinvestorpool` endpoint

**Rating Agencies**
- For pool ratings
- Add their `ratingAgencyOrgId` to `ratingAgencyOrgId[]` array in pool
- Configure sharing via `POST /configureShareOptions` with `{ ratingAgencyOrgId: [...] }`
- They appear in `shareOptions` object
- Can analyze pool characteristics via `/getPreviewPoolsByRatingAgencyOrg` endpoint

**Servicers**
- For servicing assignments
- Add their `servicerOrgId` to `servicerOrgId[]` array in pool
- Configure sharing via `POST /configureShareOptions` with `{ servicerOrgId: [...] }`
- Can see pools they'll service (assignment-based, not just sharing)

**Paying Agents**
- For payment processing
- Add their `payingAgentOrgId` to `payingAgentOrgId[]` array in pool
- Configure sharing via `POST /configureShareOptions` with `{ payingAgentOrgId: [...] }`
- Can see pools they'll handle payments for (assignment-based)

**Partners**
- For collaboration
- Add their `partnerOrgId` to `partnerOrgId[]` array (if supported)
- Can view and participate as needed

### Sharing Permissions

When sharing, you control permissions via `shareOptions` object structure:

**shareOptions Structure**
```javascript
shareOptions: {
  [orgId]: {
    allowFeedBack: true/false,  // Can organization provide feedback?
    allowDownload: true/false,  // Can organization download loan tapes?
    orgName: "Organization Name", // Organization name (looked up from organizations collection)
    orgType: "Investor"          // Organization type (looked up from organizations collection)
  }
}
```

**Permission Controls**
- **View access**: Organizations in `shareOptions` can view pool details via `/getbypoolid`
- **Download access**: Controlled by `allowDownload` boolean - enables `/downloadpreviewstdloantape` endpoint
- **Feedback access**: Controlled by `allowFeedBack` boolean - enables `POST /:poolId/feedback` endpoint
- **Action permissions**: Based on role and `shareOptions` permissions

**Editing Permissions**
- Update permissions via: `POST /editPreviewOrganizationShareOptions`
- Request body: `{ orgId, allowFeedBack, allowDownload, poolId }`
- Updates specific organization's permissions in `shareOptions`

---

## Sharing Process

### Step 1: Prepare Your Pool

Before sharing:
- Ensure pool information is complete (`poolName`, `assetClass`, `transactionType`, `description`)
- Map loans to the pool via `POST /maploanstopool` (loans must be standardized first)
- Review metrics for accuracy (metrics calculated automatically from mapped loans)
- Verify all details are correct (pool status should be "Created" or "Preview")
- Ensure organizations exist in system (organizations must be registered)

### Step 2: Assign Organizations to Pool

**Update Pool Details**
- Use `PATCH /updatePoolDetails` endpoint
- Add organizations to appropriate arrays:
  - `marketMakerOrgId: ["org1", "org2"]` - Market makers
  - `investorOrgId: ["org3", "org4"]` - Investors
  - `ratingAgencyOrgId: ["org5"]` - Rating agencies
  - `servicerOrgId: ["org6"]` - Servicers
  - `payingAgentOrgId: ["org7"]` - Paying agents
- This assigns organizations but doesn't grant sharing permissions yet

### Step 3: Configure Sharing Options

**Configure Share Options**
- Use `POST /configureShareOptions` endpoint
- Request body: `{ poolId, marketMakerOrgId: [...] }` OR `{ poolId, investorOrgId: [...] }` (one role at a time)
- System automatically:
  - Adds organizations from the role array to `shareOptions` object
  - Removes organizations no longer in the role array from `shareOptions`
  - Sets default permissions (you can edit these later)
  - Looks up `orgName` and `orgType` from `organizations` collection

**Set Individual Permissions**
- Use `POST /editPreviewOrganizationShareOptions` endpoint
- Request body: `{ orgId, allowFeedBack: true/false, allowDownload: true/false, poolId }`
- Updates specific organization's permissions in `shareOptions[orgId]`

### Step 4: Verify Sharing

**View Share Options**
- Use `GET /viewPreviewShareOptions?poolId=...` endpoint
- Returns all organizations in `shareOptions` with their permissions
- Shows `orgName` and `orgType` for each organization

**Recipients Can Now Access**
- Organizations in `shareOptions` can view pool via role-specific endpoints:
  - Market makers: `/previewunderwriterpool?marketMakerOrgId=...`
  - Investors: `/previewinvestorpool?investorOrgId=...`
  - Rating agencies: `/getPreviewPoolsByRatingAgencyOrg?ratingAgencyOrgId=...`
- They can view pool details via `/getbypoolid?poolId=...`
- They can view loans via `/getpreviewstdloantapeusinglatestdate?poolId=...`
- They can provide feedback if `allowFeedBack: true`
- They can download if `allowDownload: true`

---

## Pool Mandates

### What is a Mandate?

A **mandate** is when a market maker accepts responsibility for structuring and managing a pool. The mandate process uses `poolShareOptions` object (separate from `shareOptions` used for preview sharing).

**Two Sharing Mechanisms:**
1. **shareOptions**: For preview sharing (market makers, investors can review)
2. **poolShareOptions**: For mandate management (market maker acceptance/rejection)

### Mandate Process

**Step 1: Assign Market Maker and Submit Pool**
- Add market maker's `marketMakerOrgId` to `marketMakerOrgId[]` array in pool
- Submit pool to market maker via: `POST /pools/:poolId/submit/marketmakers`
- System automatically:
  - Changes pool `status` to "Deal"
  - Creates/updates `poolShareOptions` object
  - Sets `poolShareOptions[marketMakerOrgId].acceptanceStatus: "pending"` for each market maker
  - Sets `submittedAt` timestamp

**Step 2: Market Maker Reviews**
- Market maker sees pool via: `GET /marketmakers/:marketMakerOrgId/pools`
- Or via: `GET /marketmakers/:marketMakerOrgId/pools/both-options` (includes both sharing types)
- Market maker analyzes:
  - Pool details via `/getbypoolid?poolId=...`
  - Loan details via `/getpreviewstdloantapeusinglatestdate?poolId=...`
  - Metrics and characteristics
- Market maker decides whether to accept

**Step 3: Market Maker Decision**

**Accept Mandate:**
- Market maker calls: `PATCH /pools/:poolId/acceptance-status`
- Request body: `{ orgId: marketMakerOrgId, acceptanceStatus: "Accepted" }`
- System updates: `poolShareOptions[orgId].acceptanceStatus = "Accepted"`
- Pool moves forward with this market maker

**Reject Mandate:**
- Market maker calls: `PATCH /pools/:poolId/acceptance-status`
- Request body: `{ orgId: marketMakerOrgId, acceptanceStatus: "Rejected" }`
- System updates: `poolShareOptions[orgId].acceptanceStatus = "Rejected"`
- Pool may return to available status or issuer can share with other market makers

**Request Changes:**
- Market maker provides feedback via: `POST /:poolId/feedback`
- Request body: `{ poolId, message, type: "change_request", orgId, userId, userName, orgName }`
- Issuer receives feedback and can address it

**Step 4: Mandate Accepted**
- When `acceptanceStatus: "Accepted"`, market maker takes over structuring
- Pool `status` remains "Deal"
- Market maker proceeds with deal structuring and completion
- Pool moves toward final deal execution

---

## Mandate Statuses

### Pending Review

**What it means:**
- Pool shared with market maker
- Market maker is reviewing
- Waiting for decision

**What you can do:**
- Wait for market maker response
- Provide additional information if requested
- Share with other market makers (depending on system)

### Mandate Accepted

**What it means:**
- Market maker accepted the mandate
- They're now responsible for structuring
- Pool is moving toward deal

**What you can do:**
- Work with market maker on structuring
- Provide information as needed
- Track progress toward deal

### Mandate Rejected

**What it means:**
- Market maker declined the mandate
- Pool returns to available status

**What you can do:**
- Share with other market makers
- Address any feedback provided
- Continue pool preparation

---

## Sharing Best Practices

### Before Sharing

1. **Complete pool setup**
   - Fill in all required information
   - Map loans to the pool
   - Verify metrics are accurate

2. **Review pool quality**
   - Check loan data quality
   - Ensure metrics make sense
   - Verify completeness

3. **Prepare documentation**
   - Have supporting documents ready
   - Prepare explanations if needed
   - Organize loan data

### When Sharing

1. **Share strategically**
   - Share with relevant parties
   - Don't overshare unnecessarily
   - Consider timing

2. **Set appropriate permissions**
   - Give access needed for their role
   - Don't over-restrict if collaboration needed
   - Review permission settings

3. **Communicate clearly**
   - Let recipients know why you're sharing
   - Provide context if needed
   - Be available for questions

### After Sharing

1. **Monitor activity**
   - Check who has viewed the pool
   - Track any feedback received
   - Respond to questions promptly

2. **Respond to feedback**
   - Address change requests
   - Provide additional information
   - Update pool if needed

3. **Track progress**
   - Monitor mandate status
   - Follow up on pending actions
   - Keep workflow moving

---

## Recipient Perspective

### What Recipients See

**When a pool is shared with you:**
- You receive a notification
- Pool appears in your "Shared With Me" section
- You can view pool details and metrics
- You can take actions based on your role

### What Recipients Can Do

**Market Makers:**
- Review pool details
- Accept or reject mandates
- Request changes
- Provide feedback

**Investors:**
- Review investment opportunities
- Analyze pool metrics
- Express interest
- Download information

**Rating Agencies:**
- Review for rating purposes
- Analyze pool characteristics
- Provide rating information

---

## Managing Shared Pools

### View Sharing Status

You can see:
- Who the pool is shared with
- When it was shared
- Who has viewed it
- Any actions taken by recipients

### Update Sharing

- Add new recipients
- Remove recipients (if allowed)
- Update permissions
- Change sharing settings

### Stop Sharing

- Remove sharing with specific organizations
- Make pool private again (if status allows)
- Control access as needed

---

## Common Scenarios

### Scenario 1: Multiple Market Makers

1. Share pool with Market Maker A
2. They review but don't accept
3. Share with Market Maker B
4. They accept the mandate
5. Pool moves forward with Market Maker B

### Scenario 2: Investor Interest

1. Share pool with multiple investors
2. Investors review and analyze
3. Some express interest
4. Work with interested investors
5. Proceed with selected investors

### Scenario 3: Rating Agency Review

1. Share pool with rating agency
2. They analyze pool characteristics
3. They provide rating information
4. Use rating in pool presentation

---

## Troubleshooting

### "Pool not visible to recipient"
- Verify pool is in Preview status
- Check sharing was completed successfully
- Ensure recipient is logged in with correct role
- Verify recipient organization is correct

### "Can't share pool"
- Check pool status (some statuses restrict sharing)
- Verify you have permission to share
- Ensure pool is properly configured
- Check if sharing limits are reached

### "Market maker not responding"
- Follow up with market maker
- Check if they've viewed the pool
- Consider sharing with alternative market makers
- Provide additional information if needed

### "Want to stop sharing"
- Check if status allows removing sharing
- Remove recipients from sharing list
- Note: Some sharing may be required for workflow

---

## Key Takeaways

1. **Sharing enables collaboration**: Connect with market makers, investors, and partners
2. **Mandates formalize relationships**: Market maker acceptance creates commitment
3. **Permissions control access**: Set appropriate access levels
4. **Status affects sharing**: Some statuses restrict sharing options
5. **Monitor and respond**: Track sharing activity and respond to feedback

Understanding pool sharing and mandates helps you effectively collaborate with other parties and move your pools through the structured finance workflow.

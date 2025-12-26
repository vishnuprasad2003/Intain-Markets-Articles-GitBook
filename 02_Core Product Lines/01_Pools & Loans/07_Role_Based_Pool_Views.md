# Role-Based Pool Views

## Overview

Different users see pools differently based on their role. The platform automatically filters and presents information relevant to each role, making navigation simpler and more focused.

## Issuer View

### What Issuers See

**Their Own Pools**
- All pools where `issuerOrgId` matches their organization ID
- Retrieved via endpoint: `GET /issuers/:issuerOrgId/pools`
- Pools in all statuses (Created, Preview, Mandate Pending, Deal)
- Complete pool details including:
  - Pool basic information (`poolId`, `poolName`, `assetClass`, `transactionType`, `status`)
  - Metrics (`numberofloans`, `originalbalance`, `currentbalance`)
  - Organization assignments (`marketMakerOrgId[]`, `investorOrgId[]`, `servicerOrgId[]`, etc.)
  - Sharing configuration (`shareOptions`, `poolShareOptions`)
- Loan lists retrieved via: `GET /getpreviewstdloantapeusinglatestdate?poolId=...&asOfDate=...`
- Individual loan details from issuer's MongoDB database (`previewstdloantape` collection)
- Sharing status and recipients (view via `GET /viewPreviewShareOptions?poolId=...`)

**Actions Available**
- **Create new pools**: `POST /pools` - Creates pool with auto-generated Pool ID
- **Edit pool information**: `PATCH /updatePoolDetails` - Updates description, organization assignments (when status allows)
- **Add loans**: `POST /maploanstopool` - Maps loans to pool, validates not already mapped
- **Remove loans**: Loans can be unmapped or removed from pool
- **Share pools**: `POST /configureShareOptions` - Adds organizations to `shareOptions` with permissions
- **Edit share permissions**: `POST /editPreviewOrganizationShareOptions` - Updates `allowFeedBack` and `allowDownload`
- **View all metrics**: Metrics calculated from PostgreSQL `poolloantape` table and MongoDB aggregations
- **Download pool data**: `POST /downloadpreviewstdloantape` - Exports standardized loan tape
- **Respond to feedback**: View via `GET /:poolId/feedback`, respond by addressing issues

**Dashboard Highlights**
- Pools requiring attention
- Recent status changes
- Pools shared with them (if any)
- Activity summary

### Issuer-Specific Features

**Pool Creation Tools**
- Pool creation form
- Loan mapping interface
- Metric calculation displays
- Sharing configuration

**Management Tools**
- Edit pool details
- Manage loans in pool
- Configure sharing options
- Track pool progress

---

## Market Maker / Facility Agent View

### What Market Makers See

**Shared Pools - Preview View**
- Pools where their `marketMakerOrgId` exists in `shareOptions` object
- Retrieved via: `GET /previewunderwriterpool?marketMakerOrgId=...&mailId=...`
- Pools in Preview status (shared for review before mandate)

**Shared Pools - Deal View (Mandate)**
- Pools where their `marketMakerOrgId` exists in `poolShareOptions` object
- Retrieved via: `GET /marketmakers/:marketMakerOrgId/pools`
- Pools in Deal status (submitted for mandate acceptance)
- `poolShareOptions[marketMakerOrgId].acceptanceStatus` shows mandate status ("pending", "Accepted", "Rejected")

**Both Options View**
- Pools where market maker exists in EITHER `shareOptions` OR `poolShareOptions` (or both)
- Retrieved via: `GET /marketmakers/:marketMakerOrgId/pools/both-options`
- Useful to see all pools accessible to market maker regardless of sharing method

**Actions Available**
- **Review pool details**: `GET /getbypoolid?poolId=...` - View complete pool information
- **View metrics**: Pool metrics calculated from loans, visible in pool details
- **Accept/reject mandates**: `PATCH /pools/:poolId/acceptance-status` - Updates `poolShareOptions[orgId].acceptanceStatus`
  - Set to "Accepted" to accept mandate
  - Set to "Rejected" to reject mandate
- **Request changes**: Provide feedback via `POST /:poolId/feedback` with `type: "change_request"`
- **Provide feedback**: `POST /:poolId/feedback` - Add pool-level or loan-level feedback (if `allowFeedBack: true`)
- **Analyze pool characteristics**: View loan details via `GET /getpreviewstdloantapeusinglatestdate`
- **Structure deals**: After accepting mandate (`acceptanceStatus: "Accepted"`), proceed with deal structuring
- **View loan-level details**: Access individual loan information from issuer's database

**Dashboard Highlights**
- Pools pending their review
- Mandate requests
- Pools awaiting their action
- Recent pool updates

### Market Maker-Specific Features

**Review Tools**
- Pool analysis interface
- Metric comparison tools
- Loan detail review
- Risk assessment views

**Mandate Management**
- Accept/reject mandates
- Provide feedback
- Request changes
- Track mandate status

---

## Investor View

### What Investors See

**Shared Previews**
- Pools where their `investorOrgId` exists in `shareOptions` object
- Retrieved via: `GET /previewinvestorpool?investorOrgId=...&mailId=...`
- Pools in Preview status (shared for investment opportunity review)

**Both Options View**
- Pools where investor exists in EITHER `shareOptions` OR `poolShareOptions` (or both)
- Retrieved via: `GET /investors/:investorOrgId/pools/both-options`
- Includes pools shared for preview AND pools where investor might have other access

**Pool Details Include**
- Pool basic information (name, ID, asset class, transaction type, status)
- Metrics (balance, loan count, WAC, FICO, LTV, DTI/DSCR)
- Organization information (issuer name, other parties)
- Sharing permissions (`allowFeedBack`, `allowDownload` from `shareOptions[investorOrgId]`)

**Actions Available**
- **View pool details**: `GET /getbypoolid?poolId=...` - View complete pool information
- **View metrics**: Pool metrics visible in pool details response
- **Analyze investment opportunities**: Review pool characteristics and loan details
- **Review loan characteristics**: `GET /getpreviewstdloantapeusinglatestdate?poolId=...&asOfDate=...`
- **Download pool information**: `POST /downloadpreviewstdloantape` - Only if `allowDownload: true` in `shareOptions`
- **Express interest or provide feedback**: `POST /:poolId/feedback` - Only if `allowFeedBack: true` in `shareOptions`
- **View feedback count**: Pools sorted by feedback count (most active first) in some views

**Dashboard Highlights**
- New pool previews
- Opportunities to review
- Pools of interest
- Recent pool updates

### Investor-Specific Features

**Analysis Tools**
- Pool metrics dashboard
- Loan-level analysis
- Risk assessment views
- Comparison tools

**Opportunity Management**
- Track pools of interest
- Save favorite pools
- Review investment criteria

---

## Servicer View

### What Servicers See

**Assigned Pools**
- Pools where they're assigned as servicer
- Pools in Deal status (active deals)
- Loans requiring servicing

**Actions Available**
- View pool and loan details
- Update loan statuses
- Manage servicing activities
- Track payment information
- View servicing reports

**Dashboard Highlights**
- Pools requiring servicing attention
- Active deals
- Loan status updates
- Payment schedules

---

## Paying Agent View

### What Paying Agents See

**Assigned Pools**
- Pools where they're assigned as paying agent
- Active deals requiring payment processing
- Payment schedules and distributions

**Actions Available**
- View pool details
- Process payments
- Manage distributions
- Track payment history
- View payment reports

**Dashboard Highlights**
- Pools requiring payment processing
- Upcoming payment schedules
- Payment confirmations needed

---

## Rating Agency View

### What Rating Agencies See

**Shared Pools**
- Pools shared with them for rating
- Pools in Preview or Deal status
- Pools requiring rating services

**Actions Available**
- View pool details and metrics
- Analyze pool characteristics
- Review loan-level data
- Download pool information
- Provide rating information

**Dashboard Highlights**
- Pools pending rating
- Rating requests
- Pools requiring review

---

## Common Elements Across Views

### What Everyone Sees

**Pool Basic Information**
- Pool name and ID
- Asset class
- Transaction type
- Status badge

**Key Metrics** (when visible)
- Total balance
- Number of loans
- Key statistics

**Status Information**
- Current status
- Status history (if permitted)

**Documents** (if shared)
- Pool documents
- Loan tapes
- Reports

---

## Visibility Rules

### Status-Based Visibility

**Created Status**
- **Visible only to issuer**: Retrieved via `GET /issuers/:issuerOrgId/pools`
- Pool has `status: "Created"` in database
- `shareOptions: {}` is empty (not shared yet)
- Only issuer's organization can see it

**Preview Status**
- **Visible to issuer**: Via `/issuers/:issuerOrgId/pools`
- **Visible to shared organizations**: Organizations in `shareOptions` object can see it
  - Market makers: Via `/previewunderwriterpool?marketMakerOrgId=...`
  - Investors: Via `/previewinvestorpool?investorOrgId=...`
  - Rating agencies: Via `/getPreviewPoolsByRatingAgencyOrg?ratingAgencyOrgId=...`
- Pool may still have `status: "Created"` in database, but UI shows as "Preview" when shared
- Sharing configured via `POST /configureShareOptions` adds organizations to `shareOptions`

**Mandate Pending Status**
- **Visible to issuer**: Via `/issuers/:issuerOrgId/pools`
- **Visible to assigned market maker**: Via `/marketmakers/:marketMakerOrgId/pools`
- Pool has `status: "Deal"` in database (set when submitted via `/pools/:poolId/submit/marketmakers`)
- Market maker's `marketMakerOrgId` exists in `poolShareOptions` with `acceptanceStatus: "pending"`
- Market maker can also see via `/marketmakers/:marketMakerOrgId/pools/both-options`

**Deal Status**
- **Visible to issuer**: Via `/issuers/:issuerOrgId/pools`
- **Visible to market maker**: Via `/marketmakers/:marketMakerOrgId/pools` (if in `poolShareOptions`)
- **Visible to investors**: Via `/investors/:investorOrgId/pools/both-options` (if shared)
- **Visible to servicers**: If `servicerOrgId` array contains their organization ID
- **Visible to paying agents**: If `payingAgentOrgId` array contains their organization ID
- **Visible to rating agencies**: If `ratingAgencyOrgId` array contains their organization ID
- Pool has `status: "Deal"` in database
- All relevant parties can access based on their organization assignments

### Permission-Based Visibility

**Full Access (Issuer)**
- Issuer sees everything about their pools
- Can view all fields, edit (when status allows), manage sharing, download data
- Access to issuer's MongoDB database for loan details

**Preview Access (Market Makers, Investors)**
- Market makers and investors see pools shared with them via `shareOptions`
- Permissions controlled by `shareOptions[orgId].allowFeedBack` and `allowDownload`
- Can view pool details, metrics, loans (via issuer's database)
- Can provide feedback if `allowFeedBack: true`
- Can download if `allowDownload: true`

**Mandate Access (Market Makers)**
- Market makers see pools in `poolShareOptions` for mandate review
- Can accept/reject mandates, provide feedback
- Full access to pool details for structuring

**Assignment-Based Access (Servicers, Paying Agents)**
- Servicers see pools where their `orgId` is in `servicerOrgId[]` array
- Paying agents see pools where their `orgId` is in `payingAgentOrgId[]` array
- Access based on organization assignment, not sharing

### Permission-Based Visibility

**Full Access**
- Issuer sees everything about their pools
- Market makers see full details of pools shared with them

**Limited Access**
- Investors see preview information
- Servicers see servicing-relevant information
- Paying agents see payment-relevant information

---

## Filtering and Search

### Role-Specific Filters

**Issuers Can Filter By**
- Status (Created, Preview, Mandate Pending, Deal)
- Asset class
- Date created
- Number of loans
- Balance range

**Market Makers Can Filter By**
- Status (Preview, Mandate Pending)
- Asset class
- Issuer
- Date shared
- Mandate status

**Investors Can Filter By**
- Asset class
- Status (Preview)
- Issuer
- Metrics (balance, WAC, etc.)
- Date shared

---

## Understanding Your View

### Check Your Role

- Your role is shown in the top navigation
- It determines what you see and can do
- You can switch roles by logging out and back in with a different role

### What You Don't See

If you can't see a pool:
- It may not be shared with you
- Your role may not have access
- The pool status may restrict visibility
- You may need to be assigned to the pool

### What Actions Are Available

- Enabled buttons = you can use them
- Disabled buttons = not available (check why - tooltip or message)
- Missing buttons = your role doesn't have that permission

---

## Best Practices

1. **Understand your role**: Know what you can see and do
2. **Use filters**: Narrow down lists to find what you need
3. **Check permissions**: Understand why actions are available or not
4. **Review shared items**: Check what's been shared with you
5. **Use dashboard**: Start from dashboard to see what needs attention

---

## Common Questions

**Why can't I see a pool I created?**
- Check that you're logged in with the correct role (Issuer)
- Verify the pool wasn't deleted or archived
- Check filters aren't hiding it

**Why can't I see pools shared with me?**
- Verify you're logged in with the correct role
- Check that pools are in Preview status
- Ensure you're looking in the right section (Shared With Me)

**Why are some actions disabled?**
- Check the pool status (some statuses restrict actions)
- Verify your role has permission
- Look for tooltips explaining why it's disabled

**Can I see what others see?**
- No, you only see your role's view
- Each role has appropriate information for their responsibilities

Understanding role-based views helps you navigate the platform effectively and know what information and actions are available to you based on your role.

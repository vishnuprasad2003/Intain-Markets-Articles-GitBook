# Login & Navigation

## Logging In

### Accessing the Platform

1. Navigate to the Login Page
   - Open your web browser and go to the Intain Markets login page
   - You'll see a login form with fields for Email, Password, and Role

2. Enter Your Credentials
   - Email: Enter your registered email address (case-insensitive - converted to lowercase internally)
   - Password: Enter your password (encrypted using AES encryption before being sent to server)
   - Role: Select your role from the dropdown. The role must match your role stored in the blockchain User contract

3. Submit Login
   - Click the "Login" button
   - The system performs the following steps:
     - Encrypts your password using AES encryption
     - Queries the blockchain User contract to find your user record by email
     - Retrieves your user data from IPFS (stored at the IPFS hash in blockchain)
     - Validates your encrypted password against stored password hash
     - Checks your account status (must be "Active")
     - Verifies the role matches your blockchain role
   - If successful, you'll receive:
     - A JWT access token (valid for 1 hour)
     - A refresh token (UUID v4, valid for 1 day)
     - Your user data (without password fields)
     - Organization information (if linked)
   - You'll be redirected to your role-based dashboard

### Important Login Notes

- Role Selection: You must select the correct role that matches your blockchain record. The role is stored in the blockchain User contract and cannot be changed during login
- Password Security: Your password is encrypted using AES encryption before being sent to the server, then compared against the encrypted password stored in IPFS
- Session Duration: 
  - Access Token: Valid for 1 hour (JWT with exp claim set to current time + 3600 seconds)
  - Refresh Token: Valid for 1 day (stored in MongoDB refreshTokens collection with expiresAt field)
  - After access token expires, use refresh token to get a new access token without re-entering credentials
- Case Insensitive: Email addresses are converted to lowercase for lookup (user@example.com = User@Example.com)
- Blockchain Integration: Your user account is stored on blockchain with user data in IPFS. Login requires blockchain connectivity
- Account Status: Your account must have status "Active" in blockchain to login successfully
- Organization Link: If your account is linked to an organization (organizationId field), organization name is included in login response

### Troubleshooting Login Issues

#### Invalid EmailID or User not found

If you see "Invalid EmailID or User not found" or "User Authentication Failed, No user found":

- Check that you've entered the correct email (case doesn't matter)
- Verify the email exists in blockchain User contract
- Ensure blockchain connectivity is working
- Verify you've selected the correct role (must match blockchain role)
- Check that your account status is "Active" in blockchain
- Contact support if your account needs to be activated

#### Invalid credentials

If you see "Invalid credentials":

- Double-check your password (passwords are case-sensitive)
- Make sure you haven't accidentally typed extra spaces
- Verify password encryption is working (check browser console for errors)
- Contact support if you've forgotten your password (password reset may require blockchain update)

#### Session Expired

If your session expires:

- Access Token Expired: Use the refresh token endpoint (/refresh) to get a new access token without re-entering credentials
- Refresh Token Expired: You'll need to log in again with email and password
- Both Tokens Expired: Log in again to get new tokens
- The system tracks token usage (lastUsedAt field) for security

#### Refresh token not found or expired

If you see "Refresh token not found" or "Refresh token expired":

- Refresh tokens expire after 1 day
- If refresh token is used, it's rotated (old one invalidated, new one issued) for security
- If refresh token is stolen and used from different location, original token is marked as theft
- Log in again to get a new refresh token

#### Blockchain Connection Issues

If you experience blockchain connection issues:

- Login requires blockchain connectivity to query User contract
- If blockchain is unavailable, login will fail
- Contact support if blockchain connectivity issues persist

---

## Navigation Overview

### Dashboard

After logging in, you'll land on your Dashboard, which shows:

- Pending Actions: Items requiring your attention
- Recent Activity: Latest updates on your pools, loans, or facilities
- Quick Stats: Overview of your active items
- Notifications: Important updates and status changes

### Main Navigation Menu

The main menu is typically located at the top or side of the screen and includes:

#### For Issuers

- Pools: Create and manage loan pools
- Loans: View and manage loans
- Credit Facilities: Access term sheets and funding requests
- Documents: View and download documents
- Notifications: See all your notifications

#### For Facility Agents

- Pool Mandates: Review pools shared with you
- Term Sheets: Review term sheet submissions
- Master Commitments: Create and manage facilities
- Funding Requests: Review funding requests
- Funding Notices: Sign and manage funding notices

#### For Investors/Lenders

- Pool Previews: Review pools shared with you
- Facilities: View master commitments and funding notices
- Opportunities: See available investment opportunities

### Understanding the Interface

#### Status Indicators

- Color-coded badges: Show current status (e.g., Draft, Pending, Approved)
- Status labels: Clear text indicating where an item is in the workflow

#### Action Buttons

- Enabled buttons: Green or blue - you can click these
- Disabled buttons: Grayed out - not available (usually with a reason shown)
- Primary actions: Usually highlighted (e.g., "Submit", "Approve")
- Secondary actions: Less prominent (e.g., "Save Draft", "Cancel")

#### Breadcrumbs

- Shows your current location in the platform
- Click any part to navigate back
- Example: Home > Pools > Pool Details > Loans

#### Search and Filters

- Search bar: Find specific items by name or ID
- Filters: Narrow down lists by status, date, organization, etc.
- Sort options: Organize lists by date, name, status, etc.

---

## Common Navigation Patterns

### Viewing a List
1. Click on a menu item (e.g., "Pools")
2. See a list of items with key information
3. Use filters to narrow down if needed
4. Click on an item to view details

### Creating Something New
1. Navigate to the relevant section
2. Click the "Create" or "New" button (usually at the top)
3. Fill in the required information
4. Save as draft or submit

### Reviewing Shared Items
1. Check your notifications or "Shared With Me" section
2. Click on the item to view details
3. Review the information
4. Take action (Approve, Reject, Request Changes)

### Tracking Status Changes
1. View the item details page
2. Check the "Status" section
3. Review the "Status History" or "Activity Log"
4. See who changed what and when

---

## Role-Based UI Features

### What You See Depends on Your Role

#### Issuers

Issuers see:

- Creation buttons and forms
- Their own items and shared previews
- Submission and approval workflows
- Change request responses

#### Facility Agents

Facility Agents see:

- Review and approval interfaces
- Master commitment setup tools
- Compliance checking tools
- Signing interfaces

#### Lenders

Lenders see:

- Preview and review interfaces
- Approval buttons
- Funding notice details
- Participation tracking

### Contextual Help

- Tooltips: Hover over icons or buttons for quick explanations
- Help text: Read instructions within forms
- Status messages: Understand why actions are available or disabled
- Error messages: Clear explanations when something goes wrong

---

## Best Practices

1. Start at the Dashboard: Check pending actions first
2. Use Filters: Don't scroll through long lists - filter instead
3. Check Status: Always verify status before taking actions
4. Read Messages: Pay attention to status messages and tooltips
5. Use Breadcrumbs: Navigate back easily using breadcrumbs
6. Save Frequently: When editing, save drafts regularly
7. Check Notifications: Stay updated on status changes

## Mobile and Responsive Design

The platform is designed to work on:

- Desktop computers: Full-featured experience
- Tablets: Optimized layout
- Mobile phones: Essential features available

Some complex forms may be easier to complete on larger screens, but you can view and approve items from any device.

## Getting Help While Navigating

- Help icons: Look for (?) icons for context-specific help
- Status tooltips: Hover over status badges for explanations
- Error messages: Read error messages carefully - they explain what went wrong
- Support: Contact support if you're stuck

The interface is designed to be intuitive. If you can see a button, you can use it. If it's disabled, there's usually a clear reason shown nearby.

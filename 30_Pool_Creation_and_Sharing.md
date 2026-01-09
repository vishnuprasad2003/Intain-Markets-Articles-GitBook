---
title: Pool Creation and Sharing
description: Learn how to create pools and share them with other organizations
---

# Pool Creation and Sharing

## Overview

This guide explains the complete process of creating pools, mapping loans from the Loan Registry, and sharing pools with other organizations using two distinct flows—Preview (Share) for mandate review and Start Deal for deal commitment. As an issuer, you create a pool first, then go to the Loan Registry to select and map loans into that pool, and finally share the pool with market makers, investors, and rating agencies for review or deal acceptance. Preview sharing keeps the pool flexible while recipients evaluate and provide feedback; Start Deal sends a deal-ready pool after prerequisites (such as NFTs minted for all pool loans) are met and locks in structure once accepted. Understanding the correct sequence—create pool, map loans from registry, share—ensures accurate pool composition, metrics, and proper workflow progression.

## Who Can Use This

- **Issuers/Borrowers**: Create and manage pools for securitization or whole loan sales. Control which organizations can view the pool and what permissions they have. Issuers are the primary users of this workflow—they create pools, map loans, configure sharing settings, and initiate both Preview and Start Deal flows.

- **Market Makers/Facility Agents**: Receive shared pools in their dashboard, review the pool details and loan composition, and make mandate decisions (Accept or Reject). Market makers structure deals after accepting mandates and can share pools further with investors.

- **Investors/Lenders**: Review shared pools in their Pools dashboard, analyze pool characteristics and loan details, and provide feedback (if permitted). Investors evaluate pools shared by issuers or market makers.

- **Rating Agencies**: Analyze shared pools for rating purposes, review loan characteristics and pool composition, and provide feedback. Rating agencies cannot reject loans but can provide comments and analysis to support rating decisions.

## When This Is Used

Use pool creation and sharing when:

- **Grouping Loans for Transaction**: You need to group a set of loans into a presentable pool for securitization or whole loan sale. Pools organize loans into a cohesive unit that can be evaluated, structured, and transacted as a single entity.

- **Presenting to Market Participants**: You want market makers, investors, or rating agencies to review a curated set of loans. Sharing pools allows these parties to evaluate the loan composition, risk characteristics, and investment potential.

- **Controlling Access and Permissions**: You must control what each recipient organization can do with the pool—whether they can view only, provide feedback, or download pool data. Permissions are set per organization and can be adjusted throughout the process.

- **Advancing Through Workflow Stages**: You require a mandate decision (Preview Accept/Reject) or a deal acceptance (Start Deal) to advance the transaction. The sharing workflow drives the pool through status changes that unlock subsequent actions and lock down editing when appropriate.

- **Collaboration and Feedback**: You need to gather feedback from multiple parties before finalizing the pool composition. Preview sharing allows recipients to review and provide input while you retain the ability to make changes.

## Step-by-Step Process

### Creating a Pool (Created status)

1. **Access Pool Creation**
   - Log in to the platform with your issuer credentials and navigate to the **Pools** section from the left expandable menu (the menu expands when you hover over it).
   - In the Pools dashboard, you will see all pools you have created with their current statuses and actions.
   - Click the **Set-up Pool** button located at the top right corner of the Pools dashboard.
   - A pop-up form appears where you will enter all the necessary details for the new pool.

2. **Enter Basic Information**
   - **Pool Name**: Enter a unique, descriptive name that clearly identifies the pool. This name must be unique across all your pools—the system will block duplicate names. Use a specific, recognizable name that helps you and recipients identify the pool's purpose.
   - **Asset Class**: Select the type of loans that will be included in this pool (for example, auto loans, personal loans, mortgages, commercial mortgages, etc.). The asset class determines how certain metrics are calculated and displayed.
   - **Transaction Type**: Choose the transaction type that describes what you intend to do with this pool (for example, securitization, whole loan sale, etc.). This helps recipients understand the purpose of the pool.
   - **Description** (optional): Add a description to provide additional context about the pool, its purpose, or any relevant notes for recipients.
   - **Closing Deal**: Indicate whether this is a closing deal (Yes or No). This flag helps track pools that are intended for immediate deal closure versus those in earlier stages.

3. **Assign Organizations**
   - In the same pop-up form, you will see multi-select fields for assigning organizations to the pool. These assignments determine which organizations will be available for selection when you share the pool later.
   - **Market Makers**: Select the market maker organizations that may structure deals for this pool. Only organizations you add here will appear in the Share/Start Deal recipient selection.
   - **Investors**: Choose investor organizations that may review this pool as an investment opportunity. These organizations will be available when you share the pool with investors.
   - **Servicers**: Assign servicer organizations if needed for ongoing loan administration after the deal closes.
   - **Paying Agents**: Add paying agent organizations if needed for payment distributions.
   - **Rating Agencies**: Select rating agency organizations if the pool requires rating analysis.
   - **Verification Agents**: Add verification agent organizations if needed for loan verification processes.
   - **Important**: You can edit these organization assignments later from the pool details page while the pool is in Created or Preview status. However, only attached organizations will appear as options when you share the pool, so ensure you add the right parties here or update them before sharing.

4. **Review and Validate**
   - Before creating the pool, review all entered information for accuracy.
   - Confirm that the pool name is unique and clearly identifies the pool's purpose.
   - Verify that all required fields are completed—the system will indicate which fields are mandatory.
   - Check that the correct organizations are assigned so the right recipients appear when you share the pool later.
   - Ensure the asset class and transaction type are correct, as these affect how the pool is categorized and how metrics are calculated.

5. **Create Pool**
   - Click **Create** to finalize pool creation.
   - The pool is created with a unique identifier (Pool ID) that you can use for tracking and reference.
   - Pool status is set to **Created**, which means it is visible only to you (the issuer) at this point.
   - All pool metrics start at zero because no loans are mapped yet—metrics will populate once you add loans from the Loan Registry.
   - The pool is ready for loan mapping. You can fully edit pool details, organization assignments, and all other settings while the pool remains in Created status.

![Pool Creation - Issuer](imagesByMdFilesFolder/30/PoolCreation_Issuer.png)

### Adding Loans to Pool from Loan Registry

After creating a pool, you need to map loans to it. Loan mapping is done from the **Loan Registry**, not from within the pool details. The Loan Registry shows all loans you have onboarded, and from there you select loans and map them to your created pool.

1. **Navigate to Loan Registry**
   - From the left expandable menu, click on **Loan Registry** to access the loan registry section.
   - The Loan Registry displays all loans that have been onboarded to your organization, regardless of their current mapping status.
   - You will see a table listing all your loans with various columns showing loan details. Mapped columns appear first, followed by unmapped columns (unmapped column headers are displayed in italic format for easy differentiation).
   - Use filters or search functionality to narrow down the list if you have many loans.

2. **Review Available Loans**
   - In the Loan Registry, review the loans available for mapping.
   - Loans that are already mapped to a pool will show their current pool assignment—these loans cannot be selected for mapping to another pool until they are unmapped from their current pool.
   - Only unmapped loans can be selected for mapping to a new pool.
   - Review loan details to ensure you are selecting the appropriate loans for your pool based on asset characteristics, balances, and other relevant criteria.

3. **Select Loans to Map**
   - Select the loans you want to add to your pool by clicking the checkboxes next to each loan.
   - You can select individual loans or use bulk selection to select multiple loans at once.
   - The **Map to Pool** button becomes available when you have selected one or more unmapped loans.
   - If you select loans that are already mapped to another pool, the system will block the mapping—you can only map unmapped loans.

4. **Initiate Mapping to Pool**
   - With your desired loans selected, click the **Map to Pool** button.
   - A pop-up appears with a dropdown menu showing all pools that you have created.
   - Select the pool you want to map the selected loans to from the dropdown.
   - The dropdown displays pool names, making it easy to identify the correct target pool.

5. **Confirm Mapping**
   - After selecting the target pool, confirm the mapping action.
   - The selected loans are assigned to the pool and their status changes to **Mapped** for that specific pool.
   - **Important**: Mapping is one-to-one—a loan can only belong to one pool at a time. If you need to move a loan to a different pool later, you must first unmap it from its current pool.

![Loan Map to Pool - Issuer](imagesByMdFilesFolder/30/LoanMapToPoolIssuer.png)

6. **View Mapped Loans in Pool Details**
   - After mapping loans, navigate to the pool details page by clicking on the Pool ID in the Pools dashboard.
   - In the pool details page, go to the **Loans** tab in the table section below the summary tiles.
   - This tab displays all loans that are currently mapped to this pool, showing the mapped fields for each loan.
   - The **Actions** column in the Loans tab shows action icons for each loan:
     - **Chat box icon**: Opens the loan-level feedback/comments dialog where users who have been shared this pool can exchange feedback and comments about specific loans.
     - **Tick and Cross icons**: These appear when a market maker has requested removal of a loan from the pool. Tick means you (the issuer) accept the rejection and the loan will be marked as Removed. Cross means you reject the market maker's removal request and the loan remains in the pool.

7. **Review Pool Metrics**
   - After mapping loans, pool metrics calculate automatically based on the mapped loans.
   - Navigate to the pool details page to see the updated metrics displayed in the summary tiles at the top.
   - These metrics update automatically whenever loans are added, removed, or reinstated. You do not need to calculate them manually.

![Pool Details - Issuer](imagesByMdFilesFolder/30/Pool_Details_Issuer.png)

8. **Review Additional Pool Details**
   - In the pool details page, below the summary tiles, you will find several sections with detailed information:
   - **Summary Section**: Displays charts and analytics about the pool composition, providing visual representations of loan distributions and characteristics.
   - **Loans Tab**: Shows all mapped loans with their key fields. Click on a Loan ID to view detailed analytics for that specific loan.
   - **Loan Tape Section**: Displays detailed loan-level data for both mapped and unmapped columns. Mapped columns appear first, unmapped columns appear with italic headers. You can select different "As Of Date" values from a dropdown to view loan data as of different reporting periods (useful for recurring monthly loan tape uploads). A download button allows you to export loan data in XLSX or CSV format.
   - **Strats Section**: Analytics and stratifications of the loans, showing distributions by various characteristics.
   - **Performance Section**: Performance analytics for the loans in the pool.
   - **Feedback Section**: Pool-level feedback provided by market makers, investors, and other parties who have been shared this pool. Note that as the issuer, you can view feedback here but cannot add pool-level feedback yourself—you can only respond to or view feedback from others.
   - **Sharing Tab**: Shows all organizations that have been shared this pool and their current permissions (feedback, download). You can edit these settings here.

9. **Adjust Pool Composition as Needed**
   - You can continue adding more loans by returning to the Loan Registry and mapping additional loans to the same pool.
   - To remove loans from the pool, you can unmap them (the process depends on the pool status and workflow stage).
   - When loans are removed from the pool, they are excluded from pool calculations and metrics update automatically.
   - If removed loans are reinstated, they are re-included in calculations and metrics update accordingly.
   - Always review metrics after making changes to ensure the pool remains within your desired composition targets.

### Editing Pool Details

While the pool is in Created or Preview status, you can edit pool information using the **Edit** button in the pool details page.

1. **Access Edit Options**
   - In the pool details page, locate the **Edit** button at the top of the page.
   - Clicking this button reveals two options: **Edit Pool Details** and **Edit Loan Tape**.

2. **Edit Pool Details**
   - Select **Edit Pool Details** to open a pop-up form similar to the original Set-up Pool form.
   - You can modify the pool name, asset class, transaction type, description, closing deal flag, and organization assignments.
   - This is useful for adding or removing market maker, investor, or other organization assignments before sharing.
   - Save your changes when done; the pool details update immediately.

3. **Edit Loan Tape (Recurring Uploads)**
   - Select **Edit Loan Tape** to upload recurring loan tape data for subsequent reporting periods.
   - A pop-up appears where you can upload a new loan tape file and enter the **As Of Date** for the data.
   - After uploading, the Loan Tape Standardization Mapping pop-up appears where you map the uploaded file's columns to Intain standard fields (similar to the initial onboarding process).
   - Click **Save Mapping** to complete the upload.
   - This feature is used for monthly or periodic loan tape updates that provide refreshed loan data for ongoing calculations and reporting.

### Sharing the Pool (Preview Flow)

Preview sharing allows you to share the pool with recipients for review and feedback while retaining full editing capabilities. Recipients see the pool status as **Mandate Pending** and can Accept or Reject the mandate.

1. **Access Sharing**
   - In the pool details page, click the **Share** button located at the top right corner.
   - A pop-up window appears for configuring the share.

![Pool Sharing - Issuer](imagesByMdFilesFolder/30/PoolSharing_Issuer.png)

2. **Select Recipient Type and Organizations**
   - In the pop-up, first select the **Recipient** type from the dropdown (Market Maker, Investor, Rating Agency, etc.).
   - After selecting the recipient type, the **Preview Profile** dropdown shows the organizations of that type that were assigned to this pool during creation or editing.
   - Select the specific organizations you want to share with. You can select multiple organizations of the same type in one share action.
   - If the organization you want to share with doesn't appear, go back to Edit Pool Details and add that organization first.

3. **Configure Sharing Permissions**
   - **Allow Feedback**: Toggle on/off to control whether the recipient organization can provide feedback on the pool and loans. When enabled, recipients can add comments at the pool level (in the Feedback section) and at the loan level (using the chat box icon in the Loans tab). Default is enabled.
   - **Allow Download**: Toggle on/off to control whether the recipient organization can download loan tape data from the pool. Note that this controls loan tape download, not document downloads—documents added to the pool for sharing are controlled separately. Default is enabled.
   - These permissions are set per organization and can be adjusted later from the Sharing tab in pool details.

4. **Add Documents (Optional)**
   - You can add documents relevant to the pool for recipients to review.
   - Click the option to add documents and upload files that support the pool (offering memorandums, legal documents, etc.).
   - Recipients will be able to view and download these documents based on their permissions.

5. **Complete the Share**
   - Click the **Share** button to finalize.
   - If the pool was in **Created** status, it moves to **Preview** status after sharing.
   - Recipients receive the share and see the pool in their dashboard with status **Mandate Pending**.
   - Recipients have **Accept** and **Reject** action buttons to make their mandate decision.
   - **Important**: Before accepting the mandate, market makers cannot provide feedback on the pool—feedback functionality opens after mandate acceptance.

![Pool Sharing - Issuer](imagesByMdFilesFolder/30/PoolSharing_Issuer.png)

6. **Track Preview Outcomes**
   - **Accept**: When a recipient accepts the mandate, their view of the pool status changes to **Under Review**. The pool enters a collaborative review phase where you can continue making refinements based on feedback while recipients prepare for the next steps.
   - **Reject**: If a recipient rejects the mandate, the pool remains in **Preview** status for that recipient. You can revise the pool composition or terms and re-share if desired.
   - You retain full editing rights while the pool is in Preview or Under Review status. This allows you to respond to feedback and make adjustments before proceeding to Start Deal.

### Starting a Deal (Start Deal Flow)

The Start Deal flow is used when the pool is finalized and ready for deal commitment. This flow has prerequisites and results in a more locked-down status once accepted.

1. **Check Prerequisites**
   - The **Start Deal** button becomes enabled only after certain prerequisites are met. Typically, this requires that all loans mapped to the pool have completed NFT minting.
   - If the Start Deal button is disabled, ensure all pool loans have been verified and NFT-minted through the Batch Verification and Certificates workflow.
   - Use Start Deal when the pool composition is final and you are ready for commitment.

2. **Access Start Deal**
   - In the pool details page, click the **Start Deal** button (this button appears near the Share button when prerequisites are met).
   - A pop-up appears for configuring the deal share, similar to the Preview share pop-up but for deal commitment.

3. **Select Recipients**
   - Select the recipient organizations for the deal invitation. You can share with market makers, paying agents, servicers, and rating agencies as applicable for the deal.
   - Configure permissions as needed.

4. **Send Deal Invitation**
   - Click to send the deal invitation.
   - Recipients receive the pool with status **Ready for Deal**.
   - Recipients have **Accept** and **Reject** action buttons to make their deal decision.

5. **Recipient Decision and Outcomes**
   - **Accept**: When a recipient (typically a market maker) accepts the deal, the pool status changes to **Deal**. The transaction is committed and structural editing is restricted.
   - **Reject**: If a recipient rejects, the pool remains in **Ready for Deal** status. You can revise and re-share if needed.
   - Once in **Deal** status, the pool is finalized. Proceed with the accepting market maker for downstream structuring, execution, and deal activities.

### Managing Shared Organizations

After sharing a pool, you can manage the sharing settings and permissions for each organization.

1. **Access Sharing Tab**
   - In the pool details page, navigate to the **Sharing** tab in the table section below.
   - This tab displays all organizations that have been shared this pool, along with their current permission settings.

2. **View and Edit Permissions**
   - For each shared organization, you can see and modify:
     - **Allow Feedback**: Whether the organization can provide comments and feedback.
     - **Allow Download**: Whether the organization can download loan tape data.
   - Toggle these settings as needed; changes save automatically.

3. **Adjust Access as Needed**
   - You can adjust permissions at any time based on how you want recipients to interact with the pool.
   - If you need to add new organizations to share with, use the Share button and select additional organizations.
   - Changes to permissions take effect immediately for the affected organizations.

## Rules & Validations

- **Pool Name Uniqueness**: Pool names must be unique. You cannot create two pools with the same name—the system will block duplicate names.

- **One Pool per Loan**: A loan can only belong to one pool at a time. To map a loan to a different pool, you must first unmap it from its current pool.

- **Automatic Metric Calculation**: Pool metrics calculate automatically based on mapped loans. Metrics refresh instantly whenever loans are added, removed, or reinstated. You do not need to calculate metrics manually.

- **Preview Share Status Flow**: When you share a pool using the Preview (Share) flow, the pool status moves to **Preview** (if it was Created). Recipients see the pool as **Mandate Pending** and can Accept or Reject. When a recipient accepts, their view shows **Under Review**.

- **Start Deal Status Flow**: When you share a pool using Start Deal, recipients see the pool as **Ready for Deal** and can Accept or Reject. When a recipient accepts, the pool status changes to **Deal**, and structural editing is restricted.

- **Start Deal Prerequisites**: Start Deal typically requires all pool loans to be NFT-minted before the button becomes enabled.

- **Per-Organization Permissions**: Sharing permissions (feedback and download) are set per organization. Defaults are enabled (on), but you can turn them off for specific organizations.

- **Editing Restrictions by Status**: You can edit pool details, organization assignments, and loan composition while the pool is in Created, Preview, or Under Review status. Once the pool reaches Deal status, editing is restricted.

- **Recipient Role Determines Actions**: The type of recipient organization determines what actions they can take. Market makers can accept mandates and deals to structure transactions. Investors can review pools and provide feedback. Rating agencies can analyze pools and provide comments.

- **Feedback Availability**: Market makers cannot provide feedback on a pool until they have accepted the mandate. After acceptance, feedback functionality becomes available.

## What Happens Next

After creating and sharing a pool:

- **Preview Path**: Recipients view the pool details, analyze loan composition, and make mandate decisions. If they Accept, their view changes to Under Review, and they can provide feedback and prepare for the next steps. If they Reject, you can revise the pool and re-share. Throughout Preview and Under Review, you retain editing rights to respond to feedback and refine the pool.

- **Deal Path**: When prerequisites are met (typically all loans NFT-minted), use Start Deal to send a deal-ready pool. Recipients see Ready for Deal status. If they Accept, the pool moves to Deal status, structural editing is locked, and you proceed with the accepting market maker for deal execution and downstream activities.

- **Market Maker Actions**: After accepting a mandate, market makers can review the pool in detail, provide feedback on loans, and structure the deal. Market makers can also share the pool further with investors using their own Share functionality.

- **Investor Actions**: Investors receive shared pools in their Pools dashboard. They can review pool characteristics, analyze loan details, and provide feedback (if permitted).

- **Rating Agency Actions**: Rating agencies receive shared pools for analysis. They can review all pool information, provide comments, and prepare rating assessments. Rating agencies cannot reject loans but can provide feedback.

- **Loan-Level Interactions**: Mapped loans can have individual feedback through the chat box icon. Market makers and investors can request loan removals using the rejection workflow. As the issuer, you respond to removal requests using the tick (accept removal) or cross (reject removal request) actions.

- **Pool Progression**: The pool progresses through statuses based on recipient decisions—from Created through Preview and Under Review (for Preview sharing) or through Ready for Deal to Deal (for Start Deal). Each status represents a stage in the transaction lifecycle with appropriate access controls and editing restrictions.

- **Final Outcome**: Successfully navigating the workflow results in a finalized deal where the pool structure is locked, loans are committed, and downstream transaction activities proceed with the involved parties.

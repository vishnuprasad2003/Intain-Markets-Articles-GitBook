---
title: ESMA Reporting
description: Access, generate, and download ESMA-compliant regulatory reports for European securitization deals
---

# ESMA Reporting

## Overview

The **ESMA Reporting** module is a specialized regulatory reporting section available within Intain Markets for deals that have been configured as **ESMA Compliant** during deal setup. ESMA (European Securities and Markets Authority) requires standardized disclosures for securitization transactions in the European market. The platform automates the generation of these regulatory reports, ensuring that issuers and market makers can meet their reporting obligations efficiently and accurately.

For eligible deals, the platform generates three standardized ESMA annexes — Annex 2 (Loan-Level Data), Annex 12 (Investor Report), and Annex 14 (Inside Information) — based on finalized loan processing and recurring calculations for each payment period. Reports are available in Excel, XML, and CSV formats to support both regulatory submissions and downstream system integrations.

## Who Can Use This

- **Market Makers** who manage securitization deals and need to generate regulatory disclosures
- **Issuers** who are responsible for ESMA-compliant reporting on their securitization transactions
- **Admin** users who support reporting workflows

## When This Is Used

Use ESMA Reporting when:

- A deal has been configured as **ESMA Compliant** during the initial deal setup
- Loan Processing and Recurring calculations have been completed for the selected payment period
- You need to generate or download standardized regulatory reports for European securitization compliance
- You need to submit loan-level, investor, or bond-level disclosures to ESMA or regulatory bodies

If a deal was not marked as ESMA Compliant during deal setup, this section will not be visible.

## Step-by-Step Process

### Step 1: Verify ESMA Compliance Configuration

Before ESMA reports can be generated, the deal must have been configured with the **ESMA Compliant** flag enabled during deal creation. This is a one-time setting configured during the deal setup phase. If you do not see the ESMA Reporting section for a deal, confirm that the deal was marked as ESMA Compliant.

### Step 2: Complete Loan Processing

ESMA reports rely on finalized loan and deal data. Before generating reports:

1. Ensure loan processing is complete for the target payment period
2. Ensure recurring calculations have been run and finalized
3. The platform will only generate reports based on finalized data — draft or in-progress calculations are not included

### Step 3: Access the ESMA Reporting Section

1. Navigate to the deal details for an ESMA-compliant deal
2. Locate the **ESMA Reporting** section in the deal operations menu
3. The platform displays the available payment periods for report generation

### Step 4: Select the Payment Period

1. Use the payment period dropdown to select the reporting period
2. Available periods correspond to completed loan processing cycles
3. Each report is generated specifically for the selected period

### Step 5: Select an ESMA Annex

The platform supports three ESMA annexes. Select the annex you need:

#### Annex 2 — Loan-Level Data

Annex 2 provides detailed loan-level information standardized for ESMA reporting. This annex contains approximately 40 standardized fields organized into several categories, each identified by an official ESMA field code (SSCL series):

- **Loan Identification** — Unique Identifier (SSCL1), Original Loan Identifier (SSCL2), New Loan Identifier (SSCL3), Original Obligor Identifier (SSCL4), New Obligor Identifier (SSCL5)
- **Obligor Information** — Country of Obligor (SSCL6), Obligor Postal Code (SSCL7), Obligor Type (SSCL8), Obligor NACE Code (SSCL9), Obligor Basel III Segment (SSCL10)
- **Loan Characteristics** — Loan Origination Date (SSCL11), Loan Maturity Date (SSCL12), Loan Currency (SSCL13), Original Loan Balance (SSCL14), Current Loan Balance (SSCL15), Scheduled and Actual Principal/Interest Payments (SSCL16–SSCL19)
- **Interest Rate Details** — Interest Rate Type (SSCL20), Current Interest Rate (SSCL21), Interest Rate Index (SSCL22), Spread/Margin (SSCL23), Cap (SSCL24), Floor (SSCL25), Reset Frequency (SSCL26)
- **Payment & Delinquency** — Payment Frequency (SSCL27), Payment Due Date (SSCL28), Amount in Arrears (SSCL29), Number of Days in Arrears (SSCL30), Default Date and Amount (SSCL31–SSCL32)
- **Collateral** — Collateral Type (SSCL33), Collateral Value (SSCL34), Valuation Date (SSCL35), Loan-to-Value Ratio (SSCL36)
- **Additional** — Prepayment Penalty (SSCL37), Loss on Sale (SSCL38), Cumulative Loss (SSCL39), Recoveries (SSCL40)

#### Annex 12 — Investor Report

Annex 12 contains securitization-level and investor-focused information with approximately 30 standardized fields (SSCI series):

- **Deal Information** — Securitisation Name (SSCI1), Reporting Period Start/End Dates (SSCI2–SSCI3), Reporting Entity (SSCI4)
- **Pool Performance** — Total Pool Balance (SSCI5), Number of Loans (SSCI6), Average Loan Balance (SSCI7), Weighted Average Interest Rate (SSCI8), Weighted Average Remaining Maturity (SSCI9)
- **Collections & Payments** — Total Collections (SSCI10), Principal Collections (SSCI11), Interest Collections (SSCI12), Prepayments (SSCI13)
- **Delinquency & Default** — 30+ Day Delinquency Rate (SSCI14), 60+ Day Delinquency Rate (SSCI15), 90+ Day Delinquency Rate (SSCI16), Cumulative Default Rate (SSCI17), Cumulative Loss Rate (SSCI18)
- **Trigger Tests** — Trigger/Compliance Test Results (SSCI19), Trigger Breach Indicator (SSCI20)
- **Tranche Information** — Tranche Identifier (SSCI21), Current Tranche Balance (SSCI22), Tranche Coupon Rate (SSCI23), Tranche Payment Amount (SSCI24), Current Tranche Rating (SSCI25)
- **Waterfall & Cash Flow** — Waterfall Distribution Details (SSCI26), Reserve Account Balance (SSCI27), Cash Collected (SSCI28), Fees Payable (SSCI29), Net Cash Available for Distribution (SSCI30)

#### Annex 14 — Inside Information

Annex 14 provides bond- and tranche-level details with approximately 30 standardized fields (SSCT series):

- **Bond/Tranche Identification** — Instrument Identifier/ISIN (SSCT1), Tranche Designation (SSCT2), Securitisation Identifier (SSCT3)
- **Bond Characteristics** — Original and Current Tranche Balance (SSCT4–SSCT5), Tranche Currency (SSCT6), Coupon Type (SSCT7), Current Coupon Rate (SSCT8), Coupon Index Reference (SSCT9), Coupon Spread/Margin (SSCT10)
- **Payment Details** — Payment Date (SSCT11), Principal Payment (SSCT12), Interest Payment (SSCT13), Accrued Interest (SSCT14)
- **Ratings** — Rating Agency 1 and Rating 1 (SSCT15–SSCT16), Rating Agency 2 and Rating 2 (SSCT17–SSCT18)
- **Credit Enhancement** — Credit Enhancement Type (SSCT19), Credit Enhancement Amount (SSCT20), Subordination Level (SSCT21)
- **Counterparty Information** — Originator Name (SSCT22), Servicer Name (SSCT23), Trustee/SPV Name (SSCT24), Swap Counterparty (SSCT25)
- **Account Information** — Collection Account Balance (SSCT26), Reserve Account Balance (SSCT27)
- **Events & Triggers** — Event of Default Indicator (SSCT28), Acceleration Event Indicator (SSCT29), Early Amortisation Event (SSCT30)

![ESMA reporting menu showing annex selection](images/62-esma-reporting/esma-reporting-menu.png)

### Step 6: Preview Report Data

After selecting an annex, the platform displays a preview of the report data in a tabular format. Review the data to verify completeness and accuracy before downloading.

### Step 7: Download the Report

Each ESMA annex can be downloaded in one of three formats:

| Format | Extension | Best Used For |
|--------|-----------|---------------|
| **Excel** | `.xlsx` | Manual review, internal analysis, and data verification |
| **XML** | `.xml` | Regulatory submissions to ESMA and other authorities (follows ESMA prescribed XML schema with proper namespaces) |
| **CSV** | `.csv` | Integration with downstream systems, data pipelines, and third-party tools |

Select the required format and click the download button. The downloaded file represents the official regulatory output for the selected payment period.

![ESMA Reporting](images/62-esma-reporting/page_53_image.png)

## Rules & Validations

- **ESMA Compliant Flag Required** — Only deals explicitly configured as ESMA Compliant during deal setup will display the ESMA Reporting section. This flag cannot be changed after deal creation.
- **Finalized Data Only** — Reports are generated only from finalized loan processing and recurring calculations. In-progress or draft calculations are excluded.
- **Period-Specific Reports** — Each report is tied to a specific payment period. You must select the correct period before generating or downloading.
- **Standardized Field Codes** — All fields follow ESMA's official field code conventions (SSCL for Annex 2, SSCI for Annex 12, SSCT for Annex 14) to ensure regulatory compliance.
- **XML Schema Compliance** — The XML download format follows ESMA's prescribed XML schema with proper namespaces and element structures for direct regulatory submission.

## What Happens Next

After downloading ESMA reports:

- **Regulatory Submission** — Use the XML format to submit reports directly to ESMA or your national competent authority as required by the EU Securitisation Regulation
- **Internal Review** — Use the Excel format for internal compliance review and audit preparation
- **System Integration** — Use the CSV format to feed data into downstream risk, compliance, or analytics systems
- **Archival** — Downloaded reports serve as the official regulatory record for the payment period and should be retained per your organization's document retention policies
- **Next Period** — After the next loan processing and recurring calculation cycle completes, return to generate reports for the subsequent payment period

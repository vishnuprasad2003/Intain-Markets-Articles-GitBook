---
title: Asset Sale Analytics
description: >-
  How to use Asset Analysis, Risk Surveillance, and Reports inside an Asset Sale
  deal
---

# Asset Sale Analytics

## Overview

Each Asset Sale deal includes an analytics dashboard for portfolio composition, performance, and risk. The same deal page is used by issuers, underwriters, and investors; what you can act on still follows deal status. Metrics refresh when the issuer uploads a new loan tape.

## How to Navigate the Platform

1. Open **Asset Sale** in the sidebar.
2. Select the deal.
3. Use the analytics tabs in deal details: **Asset Analysis**, **Risk Surveillance**, and **Reports**.

You do not need a separate analytics login. If a tab looks empty, the deal may not have loans assigned yet, or a loan tape has not been uploaded. Analytics never change deal status by themselves.

**Asset Analysis**

* **Overview** — total balance, loan count, average rates, and a composition snapshot.
* **Strats** — breakdowns by loan type, geography, maturity, rate type, and collateral. Use this to see concentration before you commit.
* **Performance** — delinquency, prepayment, and loss trends over time.
* **Receivables** — loan-level rows plus NFT status. After repayment is accepted, investors burn NFTs from this tab.

![Asset Analysis Overview](<.gitbook/assets/asset-analysis-overview (1).png>)

![Asset Analysis Receivables](.gitbook/assets/asset-analysis-receivables.png)

**Risk Surveillance**

* **Overview** — a short risk snapshot for the deal.
* **Concentration** — borrower, geography, industry, and collateral concentration.
* **Data Checks** — missing fields and inconsistent values after a tape upload.
* **Exceptions** — rows outside expected ranges that need a person to review.
* **Performance Triggers** — alerts when a watched metric crosses a threshold.

**Reports** — generated portfolio summaries, performance files, and compliance documents you can download.

## What You Will See

Analytics sit in tabs on the deal, not on a separate site. Summary cards sit above charts. Detail views use sortable, filterable tables that you can export. Filters apply to the current tab only.

On **Receivables**, you also see operational columns (asset ID, amount, NFT status). That tab is both analysis and the burn location.

Investors typically use Overview and Strats before they commit, then Performance and Receivables after the deal is **Active**. Issuers use Data Checks after every tape. Underwriters use the same tabs during review to sanity-check the package they are about to publish.

## Helpful Tips

* Use **Strats** before you submit a commitment.
* On **Active** deals, check **Performance Triggers** after each tape upload.
* Run **Data Checks** whenever the issuer replaces the loan tape.
* Do not treat **Receivables** as charts only — burn lives there.
* If numbers look stale, confirm the latest tape **As Of Date** on Deal Operations.
* Empty charts usually mean no loans yet, or the tape has not been mapped.
* Export a table when you need to share a snapshot outside the platform.
* Performance is only as current as the last saved loan tape mapping.
* You cannot approve a deal or record repayment from analytics tabs. Those actions stay on Deal Operations or Investment Operations.

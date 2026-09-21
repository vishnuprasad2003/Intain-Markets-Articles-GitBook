# Agent Instructions — Intain Markets Knowledge Base

This is a **GitBook-synced documentation repository**. All content edits — whether by humans or AI agents — MUST follow the rules defined here and in `.cursor/rules/`.

---

## How to Use This File

**This file is the single entry point.** Read it first, then follow the referenced rule files for detailed guidance on each topic.

1. Read this file for repository structure, platform context, and rule index
2. Read `.cursor/rules/*.mdc` for detailed rules on each topic (see index below)
3. Check `ARTICLE_TAXONOMY.md` for article numbering and document type assignments
4. Check `SUMMARY.md` for current navigation structure

---

## Repository Structure

```
IntainMarketsArticles/
├── .gitbook.yaml                # GitBook space configuration
├── .cursor/rules/               # AI agent rules (10 files — see index below)
├── AGENTS.md                    # THIS FILE — single entry point for agents
├── SUMMARY.md                   # Table of contents / sidebar navigation
├── README.md                    # Homepage (GitBook-managed — do NOT edit)
├── ARTICLE_TAXONOMY.md          # Article → Document Type mapping (source of truth)
├── SCREENSHOT_TRACKING.md       # Screenshot audit status per article
├── images/                      # All article images
│   └── {NN}-{kebab-case}/      # One folder per article (e.g., images/36-settlement-and-nft-transfer/)
├── 01_*.md through 87_*.md      # Article files (sequential numbering)
└── Intain Markets – *.xlsx      # Category taxonomy spreadsheet
```

---

## Rules Index (`.cursor/rules/`)

These 10 rule files contain all detailed standards. **Read the relevant ones before making changes.**

| # | File | What It Covers | Read When |
|---|------|---------------|-----------|
| 00 | `00-repo-overview.mdc` | Repo architecture, platform context, key relationships | Always (auto-loaded) |
| 01 | `01-article-writing.mdc` | **Document Types A–L** (full structures), content quality, writing tone | Writing or editing any article |
| 02 | `02-commit-and-git.mdc` | Commit message format, branch strategy, pre-push checks | Before every commit |
| 03 | `03-images-and-screenshots.mdc` | Image naming, folder structure, Playwright capture, test credentials | Adding or updating images |
| 04 | `04-gitbook-sync.mdc` | SUMMARY.md format, frontmatter, GitBook custom blocks (hints, tabs, steppers) | Changing navigation or using GitBook features |
| 05 | `05-codebase-research.mdc` | Where to find statuses, fields, routes in backend/UI codebases | Verifying content against code |
| 06 | `06-article-lifecycle.mdc` | Create → Update → Retire workflow, quality gates | Creating or retiring articles |
| 07 | `07-ux-formatting.mdc` | Heading hierarchy, tables, lists, emphasis, spacing, cross-references | Formatting any content |
| 08 | `08-platform-terminology.mdc` | Canonical names for products, roles, statuses, settlement terms | Using any platform terminology |
| 09 | `09-verification-checklist.mdc` | Pre-commit checks, periodic audits, production readiness criteria | Before committing changes |

---

## Platform Context

- **Product:** Intain Markets — structured finance platform
- **Product Lines:** Asset Sale (WLS), Credit Facilities, Securitization, Participation Agreements
- **Roles:** Issuer, Investor, Market Maker (Underwriter/Facility Agent), Servicer, Paying Agent, Verification Agent, Admin, Rating Agency, Partner
- **Backend:** `intain-markets-node-app/` — Node.js, MongoDB, PostgreSQL, Snowflake
- **UI:** `intain-markets-ui/` — React, Ant Design, Redux
- **Blockchain:** Avalanche L1 subnet (NFTs), Ethereum/Avalanche C-Chain (USDC settlement)

---

## Quick Reference

### Commit Messages

**GitBook auto-exports:**
```
GITBOOK-{change_request_number}: {change_request_subject}
```

**Manual commits:**
```
docs(<scope>): <short description>
```
Scopes: `article` | `image` | `config` | `taxonomy` | `format` | `nav`

→ Full details in `02-commit-and-git.mdc`

### Article File Naming
```
{NN}_{Title_With_Underscores}.md
```
- `NN` = two-digit sequential number (01–87+)
- Example: `36_Settlement_and_NFT_Transfer.md`

### Image Conventions
- **Folder:** `images/{NN}-{kebab-case-title}/`
- **Reference:** `![Alt text](images/36-settlement-and-nft-transfer/file.png)`
- **Formats:** PNG for screenshots, SVG for diagrams

→ Full details in `03-images-and-screenshots.mdc`

### Document Types (A–L)

Every article is assigned one of 12 document types. Check `ARTICLE_TAXONOMY.md` for the mapping.

| Type | Purpose | Key Sections |
|------|---------|-------------|
| **A** | Platform Foundation | Overview → How Platform Is Designed → What This Enables → Key Principles |
| **B** | Role & Access | Overview → Roles Covered → What Each Role Can Do → Access Notes |
| **C** | Navigation & Usage | Overview → How to Navigate → What You Will See → Helpful Tips |
| **D** | Process / How-To | Overview → Who Can Use → When Used → Step-by-Step → Rules → What Happens Next |
| **E** | Lifecycle & Status | Overview → Lifecycle Overview → Status Meanings → What Each Status Indicates |
| **F** | Outcome & Decision | Overview → Possible Outcomes → What Each Means → Next Steps |
| **G** | Reference / Lookup | Overview → Reference Details → Important Notes |
| **H** | FAQ / Support | Overview → Categorized Q&A |
| **I** | Change & Release | Overview → What Changed → Impact on Users |
| **J** | Concept / Module Overview | Overview → What [X] Is → Purpose → Key Components → How It Works |
| **K** | Workflow Overview | Overview → Workflow Summary → Key Stages → Progression |
| **L** | Review & Decision | Overview → Who/When → Review Process → Criteria → Decisions → Outcomes |

→ **Full structures with sub-sections and writing guidelines** in `01-article-writing.mdc`

### GitBook Custom Blocks

```markdown
{% hint style="info" %}
Helpful information.
{% endhint %}

{% hint style="warning" %}
Important warning.
{% endhint %}

{% tabs %}
{% tab title="Issuer" %}
Issuer-specific content.
{% endtab %}
{% tab title="Investor" %}
Investor-specific content.
{% endtab %}
{% endtabs %}

{% stepper %}
{% step %}
### Step 1: Do Something
Instructions here.
{% endstep %}
{% endstepper %}
```

→ Full details in `04-gitbook-sync.mdc`

---

## Maintenance Checklist

Before every commit, verify:

- [ ] Article follows its assigned Document Type structure (see `01-article-writing.mdc`)
- [ ] Frontmatter has `title` and `description`
- [ ] Images are in correct `images/` subfolder with relative paths
- [ ] All image references resolve (no broken links)
- [ ] `SUMMARY.md` updated if articles were added/removed/renamed
- [ ] `ARTICLE_TAXONOMY.md` updated for new articles
- [ ] Commit message follows the convention (see `02-commit-and-git.mdc`)
- [ ] No TODO/TBD/placeholder text
- [ ] No broken internal links

→ Automated audit scripts in `09-verification-checklist.mdc`

---

## Key Relationships

| File | Depends On | Update When |
|------|-----------|-------------|
| `SUMMARY.md` | Article `.md` files | Articles added/removed/renamed |
| `ARTICLE_TAXONOMY.md` | Article `.md` files | New articles created |
| `SCREENSHOT_TRACKING.md` | `images/` folders | Screenshots captured/updated |
| `.cursor/rules/01-article-writing.mdc` | Document type definitions | New doc type needed (rare) |
| `.cursor/rules/08-platform-terminology.mdc` | Platform codebase | New features/roles/statuses added |

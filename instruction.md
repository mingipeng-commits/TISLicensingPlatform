# TIS Licensing Platform — Project Instructions

> **Purpose:** This file serves as the central reference for AI assistants (Claude, etc.) working on this repository. It links all project documents and defines how changes should propagate across files.

---

## Repository Structure

```
TISLicensingPlatform/
├── index.html                      # Live simulation tool (GitHub Pages)
├── TIS主要商業模式分析.md             # Top-level strategy document
├── TIS授權平台商業討論.md             # Detailed platform design document
├── Ver_Control.md                   # Version control log for all files
└── instruction.md                   # This file — project instructions
```

---

## Document Hierarchy & Relationships

```
TIS主要商業模式分析.md          (Layer 1 — Strategy & Business Model)
    │
    └──► TIS授權平台商業討論.md  (Layer 2 — Platform Design & Operations)
              │
              └──► index.html   (Layer 3 — Revenue Simulation Tool)
```

### 1. `TIS主要商業模式分析.md` — Top-Level Strategy (ver. 2.0.0)
- **Role:** Defines TIS company positioning, two business models, revenue sources, target markets, BD roadmap, and SBIR plan.
- **Key sections:** Company positioning, Patent Clearinghouse model, AI-driven IP service platform, SABCD rating system, market expansion blueprint, government grants.
- **Downstream dependency:** Section "二、兩大商業模式架構 → Licensing Platform 概覽" references `TIS授權平台商業討論.md` for detailed design.

### 2. `TIS授權平台商業討論.md` — Platform Deep-Dive (ver. 5.0.0)
- **Role:** Full operational design for the licensing platform — pricing, revenue split, DLC certificates, patent handling rules, payment/renewal mechanisms, tech architecture, legal framework, MVP plan, and customer acquisition.
- **Key sections:** 14 chapters covering platform positioning, ABCD customer simulation, patent classification (IPC 5-level), licensing packages, revenue waterfall, SABCD weighted distribution, MSRP pricing (Premium/Pro/Plus tiers), tech stack, legal structure, MVP, customer channels, cross-border patent sourcing.
- **Upstream dependency:** Inherits strategic direction from `TIS主要商業模式分析.md`.
- **Downstream dependency:** Provides all business rules and formulas that `index.html` implements as an interactive simulation.

### 3. `index.html` — Revenue Simulation Tool (ver. 6.3.0)
- **Role:** Interactive HTML tool that simulates the full revenue waterfall, SABCD weighted distribution, supplier payouts, and ITRI quarterly projections based on the ABCD customer model.
- **Published at:** GitHub Pages (branch `main`, root `/`)
- **Upstream dependency:** All numbers, formulas, tier names, and business logic must match `TIS授權平台商業討論.md`.

### 4. `Ver_Control.md` — Version Control Log
- **Role:** Tracks version history for all project files using semantic versioning (X.Y.Z).
- **Update rule:** Every change to any file must be logged here with date (UTC+8), version bump, and change description.

---

## Change Propagation Rules

When modifying any document, follow these propagation rules to keep all files in sync:

| Change Origin | Must Also Update |
|:---|:---|
| `TIS主要商業模式分析.md` (strategy change) | `TIS授權平台商業討論.md` if it affects platform design → `index.html` if it affects simulation parameters → `Ver_Control.md` |
| `TIS授權平台商業討論.md` (pricing, formula, tier, or rule change) | `index.html` to reflect new parameters → `Ver_Control.md` |
| `index.html` (bug fix or UI-only change) | `Ver_Control.md` |
| Any file | `Ver_Control.md` — always |

---

## Key Business Parameters (Quick Reference)

These are the core parameters shared across documents. When changing any of these, propagate to all affected files.

| Parameter | Value | Defined In |
|:---|:---|:---|
| Industry tiers | Premium / Pro / Plus (4-4-4 ranking by patent volume) | 商業討論 §7.2 |
| MSRP (per country) | US: 9,990/8,990/7,990; TW: 4,990/4,490/3,990; EP/JP: TBD | 商業討論 §7.2.1 |
| Tier classification | Dual-track: Track A (patent pool volume) + Track B (export value) | 商業討論 §7.2.2 |
| Period discounts | Short-term ×1.0 / Mid-term ×0.90 / Long-term ×0.85 | 商業討論 §7.3 |
| Renewal discounts | 2nd term ×0.975 / 3rd+ term ×0.95 (cap) | 商業討論 §7.6 |
| Revenue waterfall | Gross → 5% tax → 15% platform fee → pool (75% supplier / 25% TIS) | 商業討論 §6.1 |
| SABCD weights | S=3.0× / A=2.0× / B=1.5× / C=1.2× / D=1.0× | 商業討論 §3.2 |
| Initial SABCD split | 5S/6A/9B/6C/4D per 30-patent pack (uniform at launch, weighted 51.7) | 商業討論 §3.3.1 |
| Dynamic SABCD | Each industry's ratio evolves as new suppliers join; new subscribers use current ratio | 商業討論 §3.3.2 |
| Jurisdiction | US / EP / JP / TW (4 priority countries) | 商業討論 §3.5 |
| Subscription unit | 1 Country × 1 Industry × 30 patents | 商業討論 §3.5.2, §4.1 |
| Licensing periods | 3 months / 1 year / 3 years | 商業討論 §4 |
| Payment terms | Short/Mid: full upfront; Long: 50% at M1, 50% at M19 | 商業討論 §7.5 |
| ABCD simulation customers | D (3yr Premium), B (1yr×3 Pro), C (1yr×2 Pro), A (3mo Plus) | 商業討論 §1.1 |

---

## Versioning Convention

```
ver. X.Y.Z
  X = Major revamp (architecture restructure, full rewrite)
  Y = Feature enhancement (new section, logic change, new module)
  Z = Bug fix, cosmetic correction
```

- Timestamp in UTC+8 (Taiwan time).
- Full history maintained in `Ver_Control.md`.

---

## Workflow for AI Assistants

1. **Before making changes:** Read this file and the relevant source document(s) to understand current state.
2. **Make changes:** Edit the appropriate file(s) per the document hierarchy.
3. **Propagate:** Follow the change propagation rules above.
4. **Version bump:** Update the version header in the changed file(s) and log the change in `Ver_Control.md`.
5. **Commit & push:** Commit to `main` with a clear message describing what changed and why.

---

*Maintained by TIS (Talent Intelligence Strategies). Last updated: 2026-03-28.*

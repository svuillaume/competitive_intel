# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Identity

**Name:** Cloud Security Competitive Intel  
**Owner:** Fortinet PreSales · DevSecOps Engineering  
**Classification:** Internal

Collection of CNAPP competitive analysis assets — HTML presentations and Markdown analysis documents — designed for presales conversations, executive briefings, and customer-facing demos.

## Deliverables

| File | Doc ID | Comparison | Audience |
|---|---|---|---|
| `README.md` | CNAPP-AWS-02 | AWS Native vs Datadog vs FortiCNAPP | GitHub / docs |
| `docs/index.html` | CNAPP-AWS-02 | AWS Native × Datadog × FortiCNAPP (3-way) | Browser / projector |
| `docs/azure.html` | CNAPP-AZURE-01 | Microsoft Defender for Cloud × FortiCNAPP (head-to-head) | Browser / projector |

No build step, no dependencies, no JavaScript. Open any HTML file directly in a browser. Published via GitHub Pages from `docs/` (lowercase — Linux/GitHub Actions is case-sensitive; never rename to `Docs/`).

---

## CNAPP-AWS-02 · AWS Three-Way

### Scores

| Platform | Score | Position |
|---|---|---|
| 🟠 AWS Native | 39/80 | AWS-only guardrails, preventive controls, first-party integration |
| 🟣 Datadog | 50/80 | Observability + security in one agent; high TCO at scale |
| 🔴 FortiCNAPP | 68/80 | Unified multi-cloud CNAPP + closed-loop enforcement via Fortinet Security Fabric |

FortiCNAPP leads on 10 of 14 capability rows.

### Capability Matrix (14 dimensions)

| # | Dimension | Winner |
|---|---|---|
| 1 | Multi-cloud CSPM | FortiCNAPP (AWS · Azure · GCP · OCI vs AWS-only) |
| 2 | Runtime CWPP | FortiCNAPP (agent + agentless + K8s) |
| 3 | Vulnerability scanning | FortiCNAPP (+ runtime exploitability) |
| 4 | CIEM depth | FortiCNAPP (effective-vs-used, blast radius, toxic combos) |
| 5 | Composite alerts | FortiCNAPP (Polygraph ML, 80–95% noise reduction) |
| 6 | Observability correlation | Datadog (APM + logs + metrics in one agent) |
| 7 | Compliance frameworks | Tie (FortiCNAPP adds custom authoring) |
| 8 | IaC / code scanning | Tie (FortiCNAPP adds VS Code extension) |
| 9 | Kubernetes coverage | FortiCNAPP (EKS · AKS · GKE · OKE) |
| 10 | Auto-remediation | FortiCNAPP (FortiSOAR playbooks) |
| 11 | Detection → enforcement | FortiCNAPP only (FortiGate dynamic block) |
| 12 | Preventive guardrails | AWS (SCPs, Control Tower — others are detective-only) |
| 13 | Native AWS integration | AWS (first-party, zero-lag) |
| 14 | Pricing predictability | FortiCNAPP (platform subscription vs per-host/per-event) |

### Demo Flow (AWS)
1. Polygraph composite alert — compromised identity walkthrough
2. CIEM effective-vs-used — permissions on a Lambda role
3. Side-by-side finding — Security Hub ⇄ FortiCNAPP
4. FortiSOAR playbook — isolating an EC2 via FortiGate
5. TCO — Datadog per-host vs FortiCNAPP platform subscription

---

## CNAPP-AZURE-01 · Azure Head-to-Head

### Microsoft Defender for Cloud — product facts (sourced Apr 2026)

Three core components per Microsoft docs:
- **CSPM** — Foundational CSPM (free) + Defender CSPM (paid). Includes secure score, attack path analysis, Cloud Security Explorer, Data Security Posture Management (DSPM), AI SPM, governance, regulatory compliance.
- **DevSecOps** — GitHub, Azure DevOps, GitLab pipeline integration; IaC misconfiguration and secrets scanning.
- **CWPP** — Per-plan: Defender for Servers (P1/P2, via MDE), Defender for Containers (AKS/EKS/GKE), Defender for Storage, Defender for Databases (SQL/OSS/Cosmos), Defender for App Service, Defender for APIs, Defender for Key Vault, Defender for Resource Manager.
- **AI security** — AI SPM (AI Bill of Materials, attack path for GenAI workloads), AI threat protection. Unique differentiator vs FortiCNAPP.
- **XDR integration** — Native Microsoft Sentinel, Defender XDR, Entra ID convergence. Moving to unified Defender portal (transition ongoing Apr 2026 — dual-portal UX friction is a known gap).
- **Pricing** — Per-plan, per-resource. Foundational CSPM is free. Compounds at enterprise scale.
- **Multicloud** — AWS and GCP via agentless connectors (not first-party). On-prem via Azure Arc.
- **OCI** — Not supported.

### Scores (CNAPP-AZURE-01, 8 axes × 10 pts)

| Platform | Score |
|---|---|
| 🔵 Microsoft Defender for Cloud | 60/80 |
| 🔴 FortiCNAPP | 71/80 |

FortiCNAPP 6 wins · Defender 4 wins · 4 ties.

### Capability Matrix (14 dimensions, Azure comparison)

| Dimension | Winner |
|---|---|
| Multi-cloud CSPM | Tie (both cover Azure/AWS/GCP; FortiCNAPP adds OCI) |
| Azure-native integration | Defender (first-party ARM; FortiCNAPP connector-based) |
| CWPP coverage | Tie |
| CIEM depth | FortiCNAPP (effective-vs-used, blast radius; Defender basic only) |
| Composite alert correlation | FortiCNAPP (Polygraph ML; Defender uses XDR Incidents) |
| Attack path analysis | Tie (MDfC: Cloud Security Explorer; FCN: Polygraph chains) |
| Detection → enforcement | FortiCNAPP only (FortiGate block; Defender detection-only) |
| DevSecOps / IaC | Tie |
| Kubernetes | FortiCNAPP (adds OKE; Defender covers AKS/EKS/GKE) |
| DSPM | Defender (built-in; FortiCNAPP limited) |
| AI / GenAI security | Defender (AI SPM + AI threat; FortiCNAPP not GA) |
| Auto-remediation | FortiCNAPP (FortiSOAR; Defender uses Logic Apps/Governance) |
| SIEM / XDR ecosystem | Defender (Sentinel/XDR native; FortiCNAPP SIEM export only) |
| Pricing model | FortiCNAPP (platform subscription; Defender per-plan compounds) |

### Demo Flow (Azure)
1. Polygraph composite alert vs MDfC XDR Incidents — noise comparison
2. CIEM effective-vs-used on an Azure Service Principal
3. FortiSOAR playbook vs Logic Apps — response depth
4. FortiGate dynamic enforcement — capability Defender cannot match
5. TCO — MDfC per-plan compounding vs FortiCNAPP platform subscription

---

## HTML Architecture (both pages)

Single-file HTML — all CSS in `<style>`, no external fonts, no JavaScript. Shared design system:

**Design tokens:**
- Brand colors: Fortinet Red `#EF2A1F`, AWS Orange `#FF9900`, Datadog Purple `#632CA6`, Azure Blue `#0078D4`
- Fonts: Georgia (body prose), Calibri (headings/UI/tables), Consolas (mono labels)
- Dark theme base `#0A0C10`, elevated surfaces `#111419` / `#171B22` / `#1E232C`
- Optimized for projection and print

**Section order (both files):**
1. Topbar — doc ID, rev, classification, nav link
2. Hero — eyebrow, H1, dek, meta grid
3. § Stacks — tier/service layer cards
4. § Capability parity matrix — HTML table with ✓/◐/✕ marks + winner column
5. § Strengths & Limitations — pros/cons cards (3-col for AWS, 2-col for Azure)
6. § Recommendation by profile — matrix table
7. § Verdict — SVG radar chart (11-axis for AWS, 8-axis octagon for Azure) + stacked bar scorecard + verdict bar
8. Footer — references + demo flow
9. Colophon

**Radar SVG math:**
- `docs/index.html`: 11-axis polygon, center (270,270), max radius 200, viewBox "0 0 560 540"
- `docs/azure.html`: 8-axis octagon, center (270,270), axes at 45° intervals starting top (-90°), max radius 200

## Editing Rules

- **Keep `README.md` and `docs/index.html` in sync** — both cover the AWS three-way analysis.
- **`docs/azure.html` is standalone** — sourced from Microsoft Defender for Cloud docs (Apr 2026).
- **FortiCNAPP limitations are intentional** in both files — present for presales credibility; do not remove without a product update citation.
- **Scoring is weighted** — axes × 10 pts. Changing one axis score changes the total; update scorecard, bars, and verdict bar together.
- **`docs/` must stay lowercase** — GitHub Pages on Linux is case-sensitive; `Docs/` breaks the build.

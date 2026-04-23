# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Identity

**Name:** Cloud Security Competitive Intel  
**Doc ID:** `CNAPP-AWS-02` · Rev April 2026 · Classification: Internal  
**Owner:** Fortinet PreSales · DevSecOps Engineering

Three-way CNAPP comparison on AWS — **AWS Native** vs **Datadog** vs **FortiCNAPP** — designed for presales conversations, executive briefings, and customer-facing demos.

## Deliverables

| File | Purpose | Audience |
|---|---|---|
| `README.md` | Markdown analysis — full scorecard, capability matrix, Mermaid charts | GitHub / documentation |
| `docs/index.html` | Self-contained HTML presentation — dark theme, SVG radar chart, styled tables | Browser / projector / print |

No build step, no dependencies, no JavaScript. Open `docs/index.html` directly in a browser. Published via GitHub Pages from the `docs/` folder (lowercase — GitHub Actions runs on Linux, case-sensitive).

## Scores (current)

| Platform | Score | Position |
|---|---|---|
| 🟠 AWS Native | 39 / 80 | AWS-only guardrails, preventive controls, first-party integration |
| 🟣 Datadog | 50 / 80 | Observability + security in one agent; high TCO at scale |
| 🔴 FortiCNAPP | 68 / 80 | Unified multi-cloud CNAPP + closed-loop enforcement via Fortinet Security Fabric |

**FortiCNAPP leads on 10 of 14 capability rows.** AWS leads on preventive guardrails and native integration. Datadog leads on observability correlation.

## Capability Matrix — 14 Dimensions

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

## Architecture of `docs/index.html`

Single-file HTML — all CSS embedded in `<style>`, no external fonts or scripts. Section order:

1. Hero banner — three-way comparison header
2. Capability parity matrix — 14-row × 4-column table
3. Strengths & Gaps cards — 3-column layout with pros/cons per vendor
4. Decision section — SVG radar chart (11 axes), weighted scorecard bar charts, production integration flowchart
5. Final verdict bar — scores + recommendation callout
6. Footer — recommended demo flow + references

**Design tokens:**
- Brand colors: Fortinet Red `#EF2A1F`, AWS Orange `#FF9900`, Datadog Purple `#632CA6`
- Fonts: Georgia (body), Calibri (headings/UI), Consolas (labels)
- Dark theme (`#0A0C10` base), optimized for projection and print

## Recommended Demo Flow

When presenting, follow this sequence:
1. Polygraph composite alert — compromised identity walkthrough
2. CIEM effective-vs-used — permissions on a Lambda role
3. Side-by-side finding — Security Hub ⇄ FortiCNAPP
4. FortiSOAR playbook — isolating an EC2 via FortiGate (Fortinet Security Fabric)
5. TCO comparison — Datadog per-host vs FortiCNAPP platform subscription

## Editing Rules

- **Keep both files in sync.** Any change to scores, capability results, or vendor positioning must be reflected in both `README.md` and `docs/index.html`.
- **FortiCNAPP limitations are intentional.** The ⚠️ section (detective-only, 3-hr anomaly latency, UI maturity, no SCIM) is present for credibility — do not remove or soften without a product update to cite.
- **Scoring is weighted.** The 80-point total uses 8 axes × 10 points. Changing an axis score changes the total — update the scorecard table and the Final Verdict bar in both files.
- **GitHub Pages source is `docs/` (lowercase).** Never rename back to `Docs/` — it will break the Pages build on Linux.

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static competitive intelligence asset comparing three CNAPP (Cloud-Native Application Protection Platform) stacks on AWS: **AWS Native**, **Datadog**, and **FortiCNAPP** (Fortinet). Intended for Fortinet presales and customer-facing use.

Two deliverables:
- `README.md` — Markdown analysis document (decision graph, scorecard, capability matrix)
- `competitive.html` — Self-contained, single-file HTML presentation (no build step, no dependencies, open directly in a browser)

## Architecture of `competitive.html`

Everything is embedded in one file: CSS in a `<style>` block, no JavaScript, no external resources. Key sections in document order:

1. **Hero header** — three-way platform comparison banner
2. **Capability parity matrix** — 14-row × 4-column HTML table
3. **Strengths & Gaps cards** — 3-column flexbox layout per vendor
4. **Decision section** — SVG radar chart (11 axes), weighted scorecard bar charts, Mermaid-style production integration flowchart (rendered as static SVG/HTML)
5. **Final verdict bar** — scores and recommendation callout
6. **Footer** — references and demo flow

**Design tokens (CSS custom properties):**
- Brand colors: Fortinet Red `#EF2A1F`, AWS Orange `#FF9900`, Datadog Purple `#632CA6`
- Fonts: Georgia (body), Calibri (headings/UI), Consolas (labels/code)
- Dark theme with layered backgrounds; optimized for projection and print

## Scores Summary (as of last update)

| Platform     | Score |
|--------------|-------|
| AWS Native   | 39/80 |
| Datadog      | 50/80 |
| FortiCNAPP   | 68/80 |

FortiCNAPP leads on 10 of 14 capability rows. The recommended enterprise pattern layers FortiCNAPP over AWS-native guardrails.

## Editing Guidance

- Keep `README.md` and `competitive.html` in sync — both cover the same analysis; changes to scores or capabilities should be reflected in both.
- The HTML uses a dark projection theme; test readability at typical slide/projector contrast ratios, not just on a bright desktop monitor.
- No linter, formatter, or test suite — validate visually by opening `competitive.html` in a browser.

# AI Agent Spending Incidents Log

A dated, sourced log of publicly reported cases where an AI agent (or LLM-driven automation) spent money it shouldn't have, paid the wrong party, was manipulated into attempting a payment, or leaked payment credentials. Built for researchers, journalists and anyone else who needs concrete, citable examples instead of hypotheticals when discussing the risks of letting AI agents pay.

> **New:** can you make an AI agent overspend? Try our open challenge against the sandbox (test money only): [overspend-challenge](https://github.com/Pink-Agentic-Payments/overspend-challenge)

Maintained by the team behind Pink Agentic AI Payments (by PinkWallet); entries are included on sourcing criteria only, regardless of vendor.

License: CC BY 4.0. Last updated: 2026-10-05.

Also on Hugging Face: https://huggingface.co/datasets/Agentic-Payment/agent-spending-incidents

## Inclusion criteria

An incident qualifies if it is a publicly reported event, 2023-2026, where an AI agent / LLM-driven automation / AI shopping or coding agent:

- **(a) overspend** -- spent or committed money beyond what its operator intended, including runaway API/cloud bills caused by agent loops;
- **(b) wrong-payee/wrong-purchase** -- paid the wrong party or bought the wrong thing;
- **(c) manipulated-payment / credential-leak** -- was manipulated (prompt injection, malicious site or tool) into attempting a payment or leaking payment credentials; or
- **(d) research-demo** -- a documented security-research demonstration of (c) against a real product.

Excluded: generic crypto hacks with no AI agent involved, pure hypotheticals, vendor marketing "here's what could happen" scenarios, and anything we could not source to a URL that loaded.

Every row in `incidents.csv` was checked against its listed source(s) on the day this log was compiled (2026-10-05). Rows are marked `confidence: medium` or `low`, and flagged in `notes`, wherever a fact (amount, date, cause) is disputed across sources, undisclosed, or relies on a secondary summary of a paywalled/unfetched primary report.

## Summary (v0, 10 incidents)

**By category**

| Category | Count |
|---|---|
| overspend | 4 |
| manipulated-payment | 2 |
| wrong-payee/wrong-purchase | 1 |
| research-demo (incl. 1 credential-leak demo) | 3 |

**By year (incident date)**

| Year | Count |
|---|---|
| 2024 | 1 |
| 2025 | 2 |
| 2026 | 7 |

Note: v0 skews toward 2026 and toward the categories easiest to source (overspend stories and academic/security research demos). That is very likely a research-coverage artifact, not a sign that other categories are rare -- see `FINDINGS.md` and `SEARCH-LOG.md`.

## How to submit a new incident

Open a GitHub issue with:

1. A link to a primary source (news report, official postmortem, research writeup, or a specific, dated first-hand post) that was live when you filed the issue.
2. The date of the incident and the date it was reported, as precisely as the source allows.
3. Which inclusion criterion (a/b/c/d) it meets and which `category` from the schema below it fits.
4. Anything disputed or uncertain about the facts.

We will not add an entry we cannot verify against a working source URL, and we will not add hypothetical or vendor-marketing scenarios.

## Schema (`incidents.csv`)

`id, incident_date, reported_date, title, category, agent_or_product, amount_usd, description, primary_source_url, secondary_source_url, source_type, control_that_would_have_helped, confidence, notes`

- `category`: one of `overspend`, `wrong-payee/wrong-purchase`, `manipulated-payment`, `credential-leak`, `research-demo`.
- `source_type`: one of `news`, `research`, `official-postmortem`, `first-hand-post`, `incident-db`.
- `control_that_would_have_helped`: the single most direct mitigation, from `per-agent budget`, `per-payment cap`, `payee allowlist`, `human approval`, `rate/velocity limit`, `credential never exposed to agent`, `none-applicable`. This is a factual best guess based on the reported cause, not a product pitch.
- `amount_usd`: left blank where no source stated a dollar figure. Never estimated or invented.

## Known gaps in v0

- No confirmed, publicly reported case yet of an AI agent actually completing an unauthorized *fiat* payment (card/bank) in production, as opposed to crypto transfers, lab/research demos, or cloud-compute overspend. The closest real-world fiat case found (Perplexity Comet / Guardio, INC-003) is a security researcher's test, not an unprompted real-world victim.
- Several widely-circulated "AI agent ran up a $47,000 / $78,000 bill" stories turned out to be unverifiable marketing content from cost-monitoring vendors, not real incidents -- excluded; see `SEARCH-LOG.md`.
- AI Incident Database (incidentdatabase.ai) entry 1313 (Claude vending-machine losses at WSJ) overlaps with Anthropic's own "Project Vend" writeup; we cite Anthropic's primary source for INC-007 rather than duplicating both.
- x402 / crypto-agent-payment-protocol incidents (e.g. the 402Bridge hack) were investigated but excluded from v0 because available reporting describes a bridge/smart-contract exploit, not an AI agent being manipulated into paying -- see `SEARCH-LOG.md`.

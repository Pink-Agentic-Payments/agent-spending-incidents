# Methodology

How v0 was compiled (2026-10-05).

All searches run 2026-10-05 via WebSearch/WebFetch. Every URL cited in `incidents.csv` was fetched today and loaded successfully (none paywalled except where noted).

## Queries run

1. `AI agent prompt injection tricked into payment purchase 2025`
2. `Freysa AI agent challenge $47000 prize prompt injection`
3. `runaway AI agent API bill Reddit Hacker News "accidentally spent"`
4. `Claude computer use agent bought wrong item Amazon shopping agent mistake`
5. `AI shopping agent Perplexity Comet Operator browser agent bought wrong item scam prompt injection 2025 2026`
6. `"AI agent" infinite loop AWS bill thousands dollars github issue runaway`
7. `DN42 AWS bill AI agent hacker news $6,531 CloudFormation`
8. `OpenAI Operator ChatGPT agent bought wrong flight hotel expensive mistake`
9. `MCP server malicious tool payment credential leak security research 2025 2026`
10. `AI agent crypto wallet drained prompt injection "sent funds" 2025 2026 incident`
11. `"ChatGPT agent" OR "Claude agent" leaked credit card prompt injection security researcher demo payment`
12. `incidentdatabase.ai AI agent payment spending incident`
13. `Anthropic Project Vend site:anthropic.com OR site:andonlabs.com`
14. `x402 protocol agent payment exploit incident real money`
15. `"We Let AI Run Our Office Vending Machine" Wall Street Journal`
16. `Amazon $1.8 million Claude coding task 860% over budget business insider source`
17. `AI coding agent Replit Devin ran up cloud bill duplicate payment stripe bug real money`
18. `"AI agent" bought domain renewed subscription without permission real money 2025 2026`
19. `AI agent duplicate payments idempotency stripe`
20. `prompt injection agent leak Stripe API key OR credit card number demo security research`
21. `AP2 Google agent payments protocol prompt injection red team demo 2026`
22. Direct fetches: Hacker News items 47418574 and 48500012, lantian.pub DN42 writeup, Anthropic Project Vend pages, theblock.co / giskard.ai / ambcrypto on Grok-Bankr, bleepingcomputer / pcworld on Comet, Tom's Hardware / gHacks on Amazon, theregister.com and helpnetsecurity.com on cloud-bill reports, snyk.io ClawHub research, arxiv.org AP2 red-team paper, GitHub `vectara/awesome-agent-failures` case study, `kindrat86/ai-agent-incident-database` README, incidentdatabase.ai cite/1313.

## Candidates investigated and rejected (with reason)

- **"LangChain A2A 4-agent pipeline, $47,000 / 264-hour infinite loop"** (GitHub `vectara/awesome-agent-failures`, repeated verbatim across several dev.to/Medium posts). Rejected: on inspection this is an illustrative teaching case study inside a repo explicitly framed as a catalog of failure *patterns*, not a documented real event; its cited "sources" (a dev.to post, a TechStartups article, a Medium post) read as constructed for the scenario rather than independent verification. Cannot source to a real incident.
- **"AI Agent Ran Up a $47,000 Bill in 11 Days" / "$50,000 AWS horror story" / various `apilens.tech`, `nexgismo.com`, `aisecuritygateway.ai`, `dev.to` posts quoting large runaway-agent bills.** Rejected or excluded: these are marketing content from cost-monitoring vendors (AgentBudget-adjacent tools, API gateways) reusing the same round numbers ($47k, $50k, $78k) without a traceable first-hand account or company name. Where a specific, named, checkable first-hand account existed (DN42, AgentBudget's own $32 post), it was kept; the rest were not.
- **"ChatGPT/Grok sponsored-flight steering" (View From The Wing, 23-model test).** Rejected: this is a research test of what AI models *recommend*, not an agent that actually booked or paid for a flight. No real payment occurred, so it does not meet criteria (a)-(d).
- **OpenAI Operator travel-booking failures (pricing hallucinations, e.g. CHF 380 vs CHF 740/night).** Rejected: documented as an accuracy/hallucination problem in trip-planning output, not a case of Operator actually completing a wrong or unauthorized payment; Operator was shut down August 2025 before this could be confirmed as a payment incident.
- **"Comment and Control" prompt injection leaking `ANTHROPIC_API_KEY`/`GITHUB_TOKEN` from Claude Code Security Review, Gemini CLI Action and GitHub Copilot Agent (Aonan Guan / Johns Hopkins research).** Rejected for this log: real, well-sourced research, but the leaked credentials are API/service keys, not payment credentials, and no payment was attempted or demonstrated. Outside the stated inclusion criteria (c)/(d), which is specifically about payment manipulation or payment-credential leakage. Worth a future "AI agent security incidents" log with broader scope, but not included here.
- **402Bridge hack (x402 ecosystem, ~200 users, USDC stolen).** Rejected: reporting describes a bridge/smart-contract exploit on infrastructure associated with the x402 agent-payment protocol, not a case of an AI agent itself being manipulated into paying or mis-paying. No agent-decision-layer manipulation documented; looks like a generic crypto-bridge hack that happens to sit near agent-payment infrastructure, which the brief explicitly says to exclude.
- **Google Cloud / AWS "surprise AI bill" cases in The Register (Australia developer $10k bill, $127k bill, AWS Bedrock $30-38k bill).** Rejected: in every case the root cause given is a *stolen or brute-forced API key* used by a third party to run inference, not an AI agent of the account owner's overspending or being manipulated. Doesn't meet criteria (a)-(c); it's credential theft feeding human-operated abuse, not agentic payment failure.
- **"AI agent asked to renew a client domain, correctly paused" (prokopov.me).** Rejected: this is a case of the control working (agent stopped before an unauthorized charge), not an incident of overspend/misp-ayment. Interesting as a positive counter-example but doesn't meet inclusion criteria.
- **AI Incident Database entry 1313 (Claude vending-machine losses, WSJ HQ).** Not rejected, but merged into INC-007 rather than kept as a separate row: this is the same Project Vend / Claudius deployment Anthropic itself documents (red.anthropic.com, anthropic.com/research/project-vend-2); citing both would double-count one incident.
- **`kindrat86/ai-agent-incident-database` (GitHub, "34 incidents, $2.91B tracked") and `konbriefing.com` AI incident list.** Used only as a lead-generation index, not as a cited source for any row; every incident ultimately cited in `incidents.csv` was re-verified against its own primary/secondary reporting rather than taken on that repo's word.
- **Amazon Financial Times original article.** The underlying FT story (cited by Tom's Hardware, gHacks, betanews, cybernews, TechRadar as the origin of the $1.8M Amazon/Claude story) is paywalled; not fetched directly. INC-004 is sourced to Tom's Hardware and gHacks instead and flagged `confidence: medium` with this caveat in `notes`.
- **Mandiant / Google Threat Intelligence Group "AI Risk and Resilience" report.** Not fetched directly (behind a report-request/registration flow); INC-008 is sourced to Help Net Security's summary of it and flagged `confidence: medium`.

## Sources considered but not reachable / not used

- Wall Street Journal original "We Let AI Run Our Office Vending Machine" article: paywalled; used a syndicated mirror (tovima.com) as the secondary source and Anthropic's own research page as primary instead.
- Several X/Twitter posts cited by secondary crypto-news coverage of the Grok/Bankr incident were not individually fetched; relied on giskard.ai's and AMBCrypto's write-ups instead.

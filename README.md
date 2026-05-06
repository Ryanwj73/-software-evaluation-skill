# software-evaluation

A skill for [Claude Code](https://claude.ai/code) that turns a tool name (or shortlist) into a structured buying decision.

## What it does

- Researches each tool across 8 dimensions: strengths/weaknesses, price & TCO, interoperability, ease of use, social proof, financial health, contract terms, and AI future-proofness
- Adds the two most-comparable alternatives if you only name one tool — proposed with rationale, confirmed before research starts
- Produces a polished HTML report with a weighted scorecard, context column, community quotes (Reddit, G2, Capterra), and a fully sourced bibliography with live URLs

## How to use

Install the `.skill` file in Claude Code, then say something like:

> *"Evaluate Sprout Social for our 10-person team, we use HubSpot and Slack"*

Claude will introduce itself, confirm the tools to compare, then research and produce a shareable HTML report.

## Report includes

- **Methodology card** — sources used, scoring approach, and caveats
- **Weighted scorecard** with a context column explaining each dimension score
- **Tool profiles** — strengths, weaknesses, pricing tables, interoperability notes, funding snapshot, contract risk, and community quotes
- **Recommendation** with a swing-factor callout for close decisions
- **Sources list** — every entry has a live URL

## Default weights

| Dimension | Weight |
|---|---|
| Strengths & weaknesses | 20% |
| Price & TCO | 20% |
| Interoperability | 10% |
| Ease of use & adoption | 10% |
| Social proof | 10% |
| Financial health & funding | 10% |
| Contract terms | 10% |
| AI future-proofness | 10% |

Weights are user-adjustable at the start of each evaluation.

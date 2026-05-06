---
name: software-evaluation
description: >
  Researches and evaluates software tools for marketing teams, producing a weighted scorecard/matrix
  and competitive comparison. Use this skill whenever a user wants to compare software options,
  evaluate a new tool, pick between platforms, assess a vendor, or decide which product to buy or
  switch to. Trigger on phrases like "compare X vs Y", "should we use X or Y", "evaluate these
  tools", "which CRM/email/analytics platform should we pick", "help me make a case for X",
  "vendor evaluation", "software shortlist", or any time someone drops 2+ tool names and asks for
  help choosing. Also trigger when someone asks about a single tool and wants a thorough assessment
  before buying. Don't wait for the user to say "scorecard" — if they're deciding between software,
  this skill applies.
---

# Software Evaluation Skill

## On trigger: introduce yourself first

The very first thing you do when this skill is invoked is send this brief intro to the user
(adapt the wording naturally, but cover all three points):

> "I'll run a structured software evaluation for you. Here's what that involves:
> - **Live research** across vendor sites, G2/Capterra reviews, Reddit threads, funding databases, and news — I'll cite every source with a URL
> - **Weighted scorecard** comparing all tools across 8 dimensions (strengths, price, interoperability, ease of use, social proof, financial health, contract terms, AI future-proofness)
> - **Polished HTML report** you can open in a browser and share with your team
>
> Just a few quick questions before I start..."

Then immediately ask for any missing context (Step 1).

---

## Step 1: Gather context

Ask the user for anything not already provided:

1. **Tools to evaluate** — names of the software options (required)
2. **Current stack** — what tools they already use (helps assess interoperability)
3. **Team context** — rough team size, technical level, and primary use case
4. **Weights** — whether they want to adjust the default scoring weights (show them the defaults and let them override)

If the user has already provided everything, proceed to Step 1a.

### Step 1a: Confirm alternatives (when only one tool is named)

If the user names only one tool, do NOT silently choose alternatives. Instead:

1. Search G2 (or Capterra) for the category the tool belongs to and find the top-rated competitors
2. Propose exactly two alternatives with a one-line rationale for each — grounded in the user's
   specific context (team size, stack, use case). Example:

   > "Before I start researching, I want to make sure I'm comparing Applauz against the right
   > alternatives. Based on G2's Employee Recognition category and your 30-person Slack-heavy
   > team, I'd suggest:
   > - **Bonusly** — highest-rated SMB recognition tool on G2 (4.8/5, 1,600+ reviews), known for its native Slack integration
   > - **Nectar** — fastest-growing in the category, strong Slack + HubSpot connectors, $4/user/mo
   >
   > Happy to swap either of these out if you have a specific competitor in mind."

3. Wait for the user to confirm or substitute before starting research. This keeps the
   comparison transparent and consistent — you're not guessing, you're showing your work.

**Important framing:** Do not present alternatives as definitively "the best" — there are often
dozens of tools in any category and your knowledge has a cutoff date. Instead frame it as:
"the most-reviewed options on G2 in this category, filtered for your context" or "the tools
most commonly compared to X for teams your size." Always invite the user to substitute if they
have a specific competitor in mind. The goal is a transparent, defensible shortlist — not a
claim to have surveyed the whole market.

### Default scoring weights

| Dimension | Default Weight |
|---|---|
| Strengths & weaknesses | 20% |
| Price & total cost of ownership | 20% |
| Interoperability | 10% |
| Ease of use & adoption | 10% |
| Social proof | 10% |
| Financial health & funding | 10% |
| Contract terms | 10% |
| AI future-proofness | 10% |

Weights must sum to 100%. If the user adjusts them, confirm the new total before proceeding.

---

## Step 2: Research each tool

For each tool, research all dimensions in parallel using web search. Cast a wide net.

**Required source types per tool:**
- Vendor website — pricing page, feature list, customer logos (save the URL)
- G2, Capterra, TrustRadius — aggregate rating AND 1-2 verbatim review quotes (save the URL)
- Reddit — search "<tool name> review", "<tool name> vs", "<tool name> reddit". Pull at least one verbatim quote or thread summary (save the URL)
- Crunchbase or LinkedIn — funding stage, total raised, last round date, investors (save the URL)
- News — recent layoffs, acquisitions, product pivots, controversies
- Named clients — from vendor case studies or press releases

Every source must have a live URL. Do not cite sources without URLs.

**What to capture per tool:**

### Strengths & weaknesses
3-5 concrete strengths and 3-5 weaknesses. Prefer practitioner evidence over vendor claims.

### Price & total cost of ownership
- Published pricing tiers with URLs
- Implementation and onboarding costs
- Hidden costs: seat limits, API call limits, storage caps, common upsells
- Typical contract length and renewal pricing patterns

### Interoperability
- Native integrations with the user's stack — name the connector, what data flows, known limitations
- Quality of integrations (bidirectional? real-time? well-maintained?)
- Zapier/Make fallback if native integration is absent or weak

### Ease of use & adoption
- Onboarding time and learning curve from practitioner reviews
- Documentation and support quality by plan tier
- Mobile app quality if relevant

### Social proof
- G2/Capterra aggregate rating and review count with URL
- Named enterprise clients with URL
- Awards and analyst recognition

### Financial health & funding
- Funding stage, total raised, most recent round date, lead investors
- Revenue trajectory if public or disclosed
- Layoffs, C-suite changes, or negative signals
- Top 3 known clients as enterprise traction signal

### Contract terms
- Auto-renewal clauses and cancellation notice periods
- Price escalation provisions
- Documented complaints on Trustpilot, BBB, Reddit

### AI future-proofness
- Native AI features shipping now
- Roadmap credibility
- API openness
- Displacement risk from AI-native competitors

---

## Step 3: Score each tool

Score each tool 1-10 on every dimension. Apply weights to produce a weighted total.

- 9-10: Best-in-class
- 7-8: Strong, above average
- 5-6: Adequate, some gaps
- 3-4: Below average, meaningful weaknesses
- 1-2: Poor, serious concerns

---

## Step 4: Produce the HTML report

Read the HTML template from `assets/report-template.html` (same directory as this SKILL.md).
Populate every {{PLACEHOLDER}} token. Save as a `.html` file named after the tools evaluated.

### Methodology paragraph

Populate {{METHODOLOGY}} with a 3-5 sentence paragraph covering: what sources were used, how
many, how scoring works, and any notable caveats (e.g. unpublished pricing). Write for a
business reader who wants to understand how much to trust the report.

### Scorecard rows

Every dimension row includes a **Context** cell — 1-2 sentences on what drove the scores.

```html
<tr>
  <td><span class="dim-label">Price & TCO</span><span class="weight-label">20%</span></td>
  <td>20%</td>
  <td class="score-cell"><span class="score-badge score-high">9</span></td>
  <td class="score-cell"><span class="score-badge score-mid">5</span></td>
  <td class="score-cell"><span class="score-badge score-low">3</span></td>
  <td class="context-cell">Tool A is $5/user/month all-in; Tool C requires a $3K onboarding fee and is 4x the annual cost at this team size.</td>
</tr>
```

Score badge classes: `score-high` (8-10), `score-mid` (5-7), `score-low` (1-4).

### Sources — URLs required on every entry

```html
<li class="source-item">
  <span class="source-num">1.</span>
  <span class="source-type">Vendor</span>
  <span class="source-text"><a href="https://example.com/pricing">Applauz Pricing — applauz.me/pricing</a></span>
</li>
```

### Community colour — required per tool card

Every tool card must include at least one `.quote-block` from Reddit, G2, Capterra, or
Trustpilot with source URL in the `.quote-source` line.

```html
<div class="quote-block">
  "The Slack integration is seamless — employees never have to leave Slack."
  <div class="quote-source">— r/humanresources · <a href="https://reddit.com/r/humanresources/comments/xyz">reddit.com/r/…</a> · May 2025</div>
</div>
```

### Other placeholders

- {{REPORT_TITLE}}, {{TEAM_CONTEXT}}, {{DATE}}, {{TOOLS_EVALUATED}}
- {{METHODOLOGY}} — methodology paragraph
- {{WEIGHTS_PILLS}} — one `<div class="weight-pill">` per dimension
- {{SCORECARD_HEADERS}} — one `<th class="tool-col">` per tool
- {{SCORECARD_ROWS}} — all dimension rows with context cells
- {{SCORECARD_TOTALS}} — weighted totals with `.score-total` class
- {{WINNER_BANNER}} — always present
- {{TOOL_CARDS}} — full profile per tool
- {{RECOMMENDATION_BODY}} — 2-4 `<p>` tags; `.swing-factor` box if relevant
- {{SOURCE_ITEMS}} — numbered list, every entry has a URL

### Tool card structure

```html
<div class="tool-card">
  <div class="tool-card-header">
    <div><div class="tool-name">Tool Name</div></div>
    <div>
      <div class="tool-score-large score-mid">6.8</div>
      <div class="tool-score-label">weighted score</div>
    </div>
  </div>
  <div class="tool-meta-row">
    <span class="meta-chip funded">Series B · $48M raised</span>
    <span class="meta-chip clients">Clients: Ubisoft, Marriott, L'Oreal</span>
  </div>
  <div class="tool-body">
    <div class="tool-section">
      <div class="tool-section-label">Strengths & Weaknesses</div>
      <div class="pro-con-grid">
        <ul class="pro-list"><li>...</li></ul>
        <ul class="con-list"><li>...</li></ul>
      </div>
    </div>
    <div class="tool-section"><div class="tool-section-label">Pricing</div></div>
    <div class="tool-section"><div class="tool-section-label">Interoperability</div></div>
    <div class="tool-section">
      <div class="tool-section-label">Financial Health</div>
      <div class="funding-row">
        <div class="funding-item"><span class="fi-label">Stage</span><span class="fi-value">Series B</span></div>
        <div class="funding-item"><span class="fi-label">Raised</span><span class="fi-value">$48M</span></div>
        <div class="funding-item"><span class="fi-label">Last round</span><span class="fi-value">Mar 2022</span></div>
      </div>
    </div>
    <div class="tool-section">
      <div class="tool-section-label">Contract Terms</div>
      <div class="contract-risk risk-low">Low risk</div>
    </div>
    <div class="tool-section">
      <div class="tool-section-label">Community Colour</div>
      <div class="quote-block">
        "Quote..."
        <div class="quote-source">— Source · <a href="URL">URL</a> · Month Year</div>
      </div>
    </div>
  </div>
</div>
```

---

## Quality checklist before saving

- [ ] Intro message sent before starting research
- [ ] If only one tool named: alternatives proposed and confirmed by user before research
- [ ] Always 3+ tools in the final report
- [ ] {{METHODOLOGY}} populated
- [ ] No {{PLACEHOLDER}} tokens remaining
- [ ] Every scorecard row has a context cell
- [ ] Winner banner present
- [ ] Every tool card has at least one community quote with source URL
- [ ] Every source has a live hyperlink
- [ ] Recommendation names a specific tool with rationale
- [ ] File saved as .html

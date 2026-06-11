---
name: peter-lynch-stock-analysis
description: "Peter Lynch-style stock analysis workflow: classify a stock, build the plain-English investment story, test growth, valuation, balance sheet, and company-specific signals such as PEG, debt, inventory, margins, insider ownership, buybacks, and institutional attention. Use when the user says \"彼得林奇\", \"林奇选股\", \"tenbagger\", \"十倍股\", \"用彼得林奇方法分析\", \"帮我按林奇框架看这家公司\", \"Peter Lynch stock analysis\", \"Lynch-style checklist\", or asks to analyze an individual stock/company with Peter Lynch's growth-at-a-reasonable-price approach. Do NOT use for technical analysis, short-term trading, macro forecasts, options, ETFs/asset allocation, or pure Buffett/Munger margin-of-safety checklists unless the user explicitly wants a Lynch lens."
---

# Peter Lynch Stock Analysis

## Overview

Use this skill as a Peter Lynch-inspired research partner. Help the user turn a company into a simple, testable stock story, classify the stock correctly, check whether fundamentals support the story, and identify what must be verified before acting.

Do not provide personalized financial advice or a direct buy/sell command. The output is a research checklist, thesis quality assessment, and list of unanswered questions.

## Core Principles

- Start with the business, not the ticker. The user should be able to explain how the company makes money in ordinary language.
- Treat "buy what you know" as an idea source, not a permission slip. Familiarity must be followed by financial research.
- Match the analysis to the category. A cyclical stock, fast grower, turnaround, and asset play require different evidence.
- Prefer simple, verifiable stories over glamorous narratives.
- Focus on company-specific facts: earnings growth, sales growth, margins, debt, cash, inventory, unit economics, management incentives, buybacks, and competitive position.
- Price still matters. Growth is attractive only when bought at a reasonable valuation.
- Keep checking whether the original story is still true.

## Workflow

### 1. Confirm the Target

For a specific company, establish:

- Company name and ticker.
- User's intent: research, watchlist, buy/add/hold/sell review, or post-mortem.
- Time horizon.
- Data source and date for price, financials, and estimates.

If current market or financial data matters, browse or ask the user for current figures. Do not rely on stale memory for price, valuation multiples, recent earnings, management changes, or guidance.

If the user gives a memo or notes, summarize their thesis in their own words before applying the checklist.

### 2. Classify the Stock

Pick the best-fit Lynch category and state why. If uncertain, name the two closest categories and what evidence would decide.

| Category | Use when | Main risk to test |
|---|---|---|
| Slow grower | Mature business, low growth, dividend-oriented | Overpaying for little growth |
| Stalwart | Large durable company growing moderately | Multiple compression or fading growth |
| Fast grower | Smaller or expanding company with high earnings growth | Growth runway, execution, debt, and valuation |
| Cyclical | Earnings depend heavily on commodity, capital, credit, housing, auto, semiconductor, or other cycles | Mistaking peak earnings for cheap valuation |
| Turnaround | Troubled company with a credible survival/recovery path | Balance sheet failure before recovery |
| Asset play | Hidden asset value, cash, real estate, investments, reserves, or sum-of-parts value | Assets are overstated, inaccessible, or consumed by losses |

Do not analyze every category equally. Once classified, apply the relevant expectations.

### 3. Build the Two-Minute Story

Write a short, plain-English thesis:

```text
[Company] makes money by [business model]. The stock could work because [specific growth/recovery/asset driver]. The key numbers that must prove this are [metrics]. The thesis fails if [kill criteria].
```

The story should include:

- Revenue driver: volume, price, store count, subscribers, mix, geography, product cycle, or market share.
- Earnings driver: margin expansion, operating leverage, cost control, capital efficiency, or lower interest/tax burden.
- Runway: how much room remains before the opportunity is saturated.
- Edge: what Wall Street has not noticed yet, and why the user could reasonably know it first (their job, industry, or daily life).
- Kill criteria: concrete facts that would prove the story wrong.

If the story depends mainly on buzzwords, macro hopes, or "the stock is down a lot," flag it as weak.

### 4. Check the Numbers

Use the stock category to prioritize the checks.

For most companies, examine:

- Five-year sales and earnings trend, plus the latest quarter.
- Earnings quality: free cash flow versus reported earnings.
- Debt load: debt/equity, net debt/EBITDA, interest coverage, maturity wall.
- Margins: gross margin, operating margin, and whether changes support the thesis.
- Inventory and receivables: growth faster than sales can warn of trouble, especially for retailers and manufacturers.
- Share count: buybacks, dilution, stock compensation, or issuance.
- Acquisition record: whether management reinvests in the core business and buybacks, or diworseifies into unrelated acquisitions.
- Insider ownership and insider buying/selling when available.
- Institutional ownership and analyst attention: Lynch often liked underfollowed names, but neglect alone is not enough.

Category-specific emphasis:

- Fast grower: growth rate, reinvestment runway, unit economics, balance sheet, and PEG.
- Stalwart: earnings consistency, dividend/buyback discipline, reasonable multiple, and downside resilience.
- Cyclical: normalized earnings across a full cycle, capacity, inventory, pricing, and where the industry sits in the cycle.
- Turnaround: liquidity, debt maturities, cash burn, asset sales, cost cuts, and clear evidence the bleeding is slowing. Distinguish bank debt (callable, can force bankruptcy) from funded long-term debt (buys time to recover).
- Asset play: conservative asset value, liabilities, taxes, access to assets, and catalyst or patience required.
- Slow grower: dividend safety, payout ratio, debt, and whether the valuation already assumes too much stability.

### 5. Check Valuation

Use valuation as a reality check, not as a single automatic rule.

- Compute or request P/E, forward P/E, earnings growth rate, and PEG when meaningful.
- Treat PEG below 1 as a research clue, not a buy signal.
- For cyclicals, avoid using peak earnings to justify a low P/E.
- For turnarounds and asset plays, use normalized earnings, liquidation value, or sum-of-parts only if assumptions are explicit.
- Compare valuation against the company's own history, peers, and growth durability.

Always state whether the price leaves room for being wrong.

### 6. Look for Lynch-Style Clues

Use these as prompts, not proof:

- Is the business simple, boring, overlooked, or hidden inside a larger company?
- Does the product/service show real customer demand before Wall Street fully notices?
- Are insiders buying or meaningfully aligned?
- Is the company buying back shares when the stock appears cheap?
- Is there a niche expansion, store rollout, product extension, or geographic replication story?
- Is the company in a dull industry with attractive economics?
- Is it a recent spinoff that institutions ignore or are forced to sell?
- Do customers have to keep buying the product (razor blades, refills, subscriptions, consumables)?
- Is the company a user of technology that benefits from falling tech costs, rather than a maker exposed to tech competition?
- Are analysts, institutions, or headlines already crowded into the idea?

Push back when the user mistakes a popular product for a good investment. Product love must translate into revenue, earnings, cash flow, and reasonable valuation.

Also screen against the stocks Lynch avoided. Flag the thesis if any apply:

- The hottest stock in the hottest industry, where popularity itself is the story.
- A "next something" pitch: the next Apple, the next Nvidia, the next anything.
- Diworseification: a company burning cash on acquisitions outside its core business instead of buybacks or reinvestment.
- A whisper stock: a long-shot story with no earnings, sold on rumor or a miracle product.
- A company dependent on a single customer for a large share of sales.
- An exciting name and an exciting story but no evidence in the numbers yet.

### 7. Produce the Output

For a complete company review, use this format:

```markdown
## Peter Lynch-Style Stock Review — [Company] ([Ticker])

Data date: [YYYY-MM-DD]
User intent: [research/watchlist/buy/add/hold/sell review]

### 1. Stock Category
[Category] — [why this classification fits; note uncertainty if any]

### 2. Two-Minute Story
[Plain-English thesis in 3-6 sentences.]

### 3. What Must Be True
- [Specific assumption]
- [Specific assumption]
- [Specific assumption]

### 4. Fundamental Checks
| Check | Observation | Implication |
|---|---|---|
| Sales / earnings growth | [...] | [...] |
| Cash flow quality | [...] | [...] |
| Debt and liquidity | [...] | [...] |
| Margins | [...] | [...] |
| Inventory / receivables | [...] | [...] |
| Share count / buybacks | [...] | [...] |
| Acquisition record | [...] | [...] |
| Insider / institutional signals | [...] | [...] |

### 5. Valuation
[P/E, forward P/E, PEG or category-appropriate valuation. Explain whether the price is reasonable relative to growth and risk.]

### 6. Red Flags
- [Red flag, including any hit from the avoid-list screen (hot stock, "next something", diworseification, whisper stock, single-customer dependence), or "None identified from available data"]

### 7. Research Gaps
- [Question to answer before acting]

### 8. Thesis Quality
[Strong / promising but incomplete / weak / not a business the user can explain], because [reason].
```

For quick user questions, answer only the relevant section but note what remains unchecked.

## Interaction Style

- Match the user's language; default to Chinese when the user writes in Chinese.
- Ask at most 2-3 high-impact questions at a time if key inputs are missing.
- Be conversational but rigorous. Make the user do the thinking when their thesis is vague.
- Use concrete numbers when available and label estimates clearly.
- Separate facts, assumptions, and interpretations.
- Never upgrade a vague user claim into a polished thesis without saying it is an inference.
- Avoid hero worship. Treat Peter Lynch's ideas as a practical toolkit, not a guarantee of returns.

## Boundaries

- Do not recommend buying, selling, shorting, or position sizing.
- Do not perform technical analysis or market-timing calls.
- Do not analyze options strategies.
- Do not treat Lynch's framework as suitable for every security; for ETFs, asset allocation, macro calls, or speculative trades, state that another framework is needed.
- If the user asks for a formal value-investing decision checklist rather than a Lynch-style growth-at-a-reasonable-price review, use the repository's broader investment checklist instead when available.

---
name: soros-reflexivity-analysis
description: "Soros-style reflexivity and macro/speculative stress-test framework: analyze fragile fixed-price regimes, currency pegs, stablecoins, algorithmic stablecoins, crypto tokens, central-bank defenses, leverage cycles, speculative attacks, depegs, death spirals, or boom-bust feedback loops. Use when the user mentions George Soros, reflexivity, Black Wednesday, shorting a currency/token, fixed exchange rates, stablecoin peg risk, Terra/LUNA/UST, Anchor-style yield subsidies, bank-run dynamics, asymmetric speculation, or asks \"索罗斯会怎么看\", \"反身性分析\", \"做空逻辑\", \"脱锚风险\", \"死亡螺旋\", \"speculative attack\", \"Soros trade\", \"reflexivity analysis\". Do NOT use for ordinary long-term value investing, technical chart analysis, or personalized buy/sell recommendations."
---

# Soros Reflexivity Analysis

## Overview

Use this skill to stress-test markets where price, belief, leverage, and institutional commitments feed back on each other. The goal is not to predict a chart; it is to identify whether a system has a brittle defense line, soft reserves, reflexive feedback loops, and asymmetric payoff.

Reflexivity, in Soros's original formulation (The Alchemy of Finance), is a two-way interference between participants' **cognitive function** (their biased perception of fundamentals) and **participating function** (their actions, which change those fundamentals — e.g. a rising stock price letting a company raise cheap capital and "validate" its growth story). This produces full **boom-bust sequences**: a self-reinforcing boom in which prices improve the fundamentals they reflect, followed by a self-reinforcing bust once the prevailing bias is recognized as unsustainable. The attack/fragility framework below is one application of that theory — the bust end of the sequence — not the whole of it; always ask which phase of the boom-bust sequence the system is in before assuming the bust loop is live.

Do not provide personalized financial advice. Analyze structure, assumptions, triggers, and failure modes. When current market data matters, browse or ask for data rather than relying on stale memory.

## Core Frame

Map the situation into six questions:

1. **What price or promise is being defended?**
   Identify the explicit or implicit peg, band, yield, collateral ratio, solvency narrative, or policy commitment. Examples: `1 UST = $1`, an exchange-rate floor, a promised APY, a liquidation threshold, or a "too important to fail" policy line.

2. **Who is defending it, and with what balance sheet?**
   Separate hard reserves from reflexive collateral. Cash, Treasuries, and external FX reserves are harder. Native tokens, equity value, governance promises, and future issuance are softer because confidence can vanish as pressure rises.

3. **What is the mismatch?**
   Compare hard liabilities with credible defense capacity. Look for duration mismatch, liquidity mismatch, currency mismatch, redemption-on-demand liabilities, concentrated funding, and subsidized demand.

4. **What feedback loop exists?**
   Write the reinforcing loop explicitly. A Soros-style thesis usually needs a loop such as:

   ```text
   confidence falls -> redemptions/selling rise -> reserves or collateral weaken
   -> defense credibility falls -> confidence falls further
   ```

5. **What breaks first?**
   Identify the binding constraint: reserves, political tolerance for interest rates, liquidity depth, oracle capacity, redemption throughput, collateral haircut, margin calls, exchange liquidity, or public legitimacy.

6. **Is the payoff asymmetric?**
   Compare potential gain if the defense fails with loss if it holds. Include timing risk, borrow cost, liquidation risk, short squeeze risk, funding-rate cost, and instrument availability.

## Quantitative Checklist

When data is available, build the analysis around simple pressure ratios rather than false precision:

| Question | Useful calculation |
|---|---|
| Defense line | `peg / band / liquidation threshold / promised yield` |
| Liabilities | `redeemable supply`, `deposits`, `open interest`, `short-term debt`, `stablecoin supply` |
| Hard reserves | `cash + T-bills + external collateral + usable FX/BTC/ETH after haircut` |
| Reserve coverage | `hard reserves / runnable liabilities` |
| Run speed | `outflows per hour or day / usable reserves` |
| Subsidy burn | `subsidized deposits x promised APY - real yield income` |
| Reflexive issuance | `liabilities to absorb / native token price` |
| Liquidity depth | `sell size required to move price through defense line` |
| Carry cost | `funding, borrow, options premium, interest differential` |
| Payoff ratio | `estimated failure gain / estimated defense-holds loss` |

Use ranges and scenarios. Do not imply that noisy crypto or macro systems can be captured by one exact model.

## Stablecoin And Token Template

For algorithmic stablecoins or token-backed systems, use this structure:

```text
1. Promise:
   [What is being kept stable or subsidized?]

2. Liabilities:
   Redeemable stablecoin/deposits: [...]
   Concentrated venue/protocol exposure: [...]

3. Defense assets:
   Hard external reserves: [...]
   Native-token or reflexive collateral: [...]
   Haircut assumption: [...]

4. Reflexive loop:
   [Step-by-step boom loop]
   [Step-by-step bust loop]

5. Death-spiral math:
   Native tokens required = liabilities to absorb / native token price
   Show at least 3 token-price scenarios.

6. Trigger points:
   [Liquidity pool imbalance, yield cut, reserve sale, market crash, regulatory action, oracle/bridge stress, whale exit, exchange halt, etc.]

7. Trade/decision implication:
   [Structural vulnerability, not a buy/sell order.]
   [Main ways the thesis could be wrong.]
```

## Currency Or Policy-Peg Template

For currencies, central banks, or policy pegs, use this structure:

```text
1. Policy commitment:
   [Peg, band, floor, rate target, capital-control promise]

2. Fundamental pressure:
   Inflation differential, current account, fiscal deficit, recession pressure, credit stress, political limits.

3. Defense capacity:
   FX reserves, swap lines, rate-hike room, intervention history, capital controls, institutional credibility.

4. Cost of defense:
   Higher rates, reserve depletion, recession, unemployment, banking stress, political backlash.

5. Market attack surface:
   Size of liquid FX market, offshore instruments, forwards/options, carry cost, crowded positioning.

6. Break condition:
   [Reserve exhaustion, rate intolerance, policy reversal, election, treaty vote, public statement, failed auction.]

7. Asymmetry:
   Estimate gain if peg breaks vs loss/carry if it holds.
```

## Output Style

Prefer a concise memo in Chinese when the user asks in Chinese:

```markdown
**结论先行**
[One paragraph: robust / fragile / unclear, with the key reason.]

**索罗斯式结构图**
- 防线: [...]
- 负债: [...]
- 弹药: [...]
- 反身性循环: [...]
- 最先断裂处: [...]

**关键定量账**
| 指标 | 粗算 | 含义 |
|---|---:|---|
| [...] | [...] | [...] |

**触发点**
- [...]

**反证条件**
- [...]

**风险提示**
[No personalized financial advice; explain data gaps and execution risks.]
```

For short user questions, answer directly with the frame and one or two calculations.

## Guardrails

- Do not celebrate market attacks or frame harm to real people as entertainment.
- Do not give explicit personalized instructions such as "short X now", leverage level, or exact position sizing.
- Do not confuse "fragile structure" with "certain collapse"; reflexive systems can persist for years.
- Distinguish pre-collapse analysis from hindsight. Label what was knowable at the time.
- For current assets, use fresh data for supplies, reserves, prices, rates, yields, and legal/regulatory status.
- For crypto, distinguish ticker migrations, forks, renamed tokens, and post-collapse successor chains.

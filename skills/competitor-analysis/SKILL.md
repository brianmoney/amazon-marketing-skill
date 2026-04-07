---
name: competitor-analysis
description: >
  Analyze and tear down competitor Amazon product listings to identify
  strengths, weaknesses, keyword strategies, and positioning gaps. Use
  when the user wants to understand what competitors are doing, compare
  their listing to competitors, find competitive advantages, or research
  a category before launching a product.
---

# Competitor Analysis

Performs structured teardowns of competitor Amazon listings to identify
positioning gaps, keyword opportunities, and content strategies the user
can learn from or counter.

## Prerequisites

Load `references/amazon-style-guide.md` — used when flagging compliance issues
in competitor listings (prohibited characters, restricted language, formatting violations).

Load `references/rufus-optimization.md` — used when evaluating competitor Rufus
readiness and identifying AI discovery gaps the user can exploit.

If `brand-context.md` exists in the project root or `.agents/` directory,
load it for shared positioning rules and brand guardrails.

If `products/[ASIN]/product-context.md` exists for the product being compared,
load it for the user's product facts. Prefer `User Confirmed Data`, then
`Amazon Observed Data`, then `AI Inferences`.

## What This Skill Analyzes

For each competitor listing, evaluate:

1. **Title Strategy** — Keywords used, structure, positioning angle
2. **Bullet Point Strategy** — Which benefits they emphasize, what they skip
3. **Description & A+ Content** — Depth, storytelling, objection handling
4. **Keyword Coverage** — Which terms they target, which they miss
5. **Review Sentiment** — What customers love and complain about
6. **Pricing & Positioning** — Where they sit in the market
7. **Rufus Readiness** — How well their listing serves AI-driven discovery

## Input Requirements

The user should provide 3-5 competitor ASINs or listing URLs. If they can't
provide ASINs, ask them to paste competitor listing content (title, bullets,
description).

If MCP servers are connected (AmazonSeller-mcp-server), pull catalog data directly.

## Analysis Framework

### Per-Competitor Teardown

For each competitor, analyze:

**Title Analysis:**
- What primary keyword do they lead with?
- How do they position (premium? value? functional?)?
- What information do they include/exclude?
- Character count and mobile visibility
- Compliance issues (if any)

**Bullet Point Analysis:**
- What 5 angles do they cover?
- Which features/benefits do they emphasize most?
- Do they follow current Amazon formatting requirements?
- What buyer objections do they address?
- What do they SKIP that buyers would want to know?

**Keyword Extraction:**
- Extract all unique meaningful keywords from their visible listing
- Categorize by: product terms, feature terms, benefit terms, use-case terms
- Note which terms appear in title vs bullets vs description

**Review Mining (if available):**
- Top 3 things customers love (potential table-stakes features)
- Top 3 complaints (opportunities for your differentiation)
- Questions asked in Q&A (content gaps in their listing)
- Sentiment themes Rufus would pick up on

**Positioning Map:**
Build a simple positioning comparison:
```
| Factor            | Competitor A | Competitor B | Competitor C | YOUR Product |
|-------------------|-------------|-------------|-------------|--------------|
| Price point       |             |             |             |              |
| Primary keyword   |             |             |             |              |
| Key differentiator|             |             |             |              |
| Review count      |             |             |             |              |
| Star rating       |             |             |             |              |
| A+ Content?       |             |             |             |              |
| Missing content   |             |             |             |              |
```

### Cross-Competitor Patterns

After analyzing individual listings, identify:

1. **Category table stakes** — Features/benefits EVERY competitor mentions
   (you must cover these too)
2. **Common gaps** — Information NO competitor provides well
   (this is your differentiation opportunity)
3. **Keyword consensus** — Terms all competitors target
   (you must target these for baseline visibility)
4. **Keyword gaps** — High-value terms competitors miss
   (low-competition opportunity)
5. **Review-driven insights** — Complaints common across the category
   (product development and positioning opportunity)
6. **Rufus positioning** — How would Rufus answer "which [product] is best for [use case]"
   based on current competitor content? Where does your product fit?

## Output Format

```
# Competitor Analysis Report

## Category: [category]
## Competitors Analyzed: [count]

## Executive Summary
[3-4 sentence overview of competitive landscape and key findings]

## Individual Teardowns

### Competitor 1: [Brand + ASIN]
**Title**: [their title]
**Positioning**: [how they position]
**Strengths**: [what they do well]
**Weaknesses**: [what they do poorly or skip]
**Keywords**: [extracted keyword list]

[repeat for each competitor]

## Competitive Landscape

### Category Table Stakes
[features/benefits ALL competitors mention — must-haves for your listing]

### Differentiation Opportunities
[gaps in competitor content you can exploit]

### Keyword Opportunities
[high-value terms competitors miss or under-target]

### Review-Driven Insights
[common complaints that inform your positioning]

## Recommendations for Your Listing
1. [specific title recommendation based on competitive gaps]
2. [specific bullet strategy based on what competitors skip]
3. [keyword targets competitors miss]
4. [positioning angle competitors don't own]
5. [Rufus queries you can uniquely answer]
```

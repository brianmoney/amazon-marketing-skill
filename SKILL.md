---
name: amazon-marketing
description: >
  Amazon product listing optimization skill for Claude Code and AI agents.
  Use this skill when the user mentions Amazon listings, product titles,
  bullet points, product descriptions, backend keywords, search terms,
  A+ Content, listing audit, Amazon SEO, ASIN optimization, Rufus optimization,
  or anything related to creating, improving, or auditing Amazon product
  detail pages. Also trigger when the user mentions FBA/FBM product copy,
  Amazon keyword research, competitor listing analysis, or Brand Registry content.
  If the user pastes an Amazon URL, ASIN, or product data and wants copy written
  or improved, use this skill. Also trigger when the user wants to onboard
  ASINs from `asins.csv`, create `products/[ASIN]/product-context.md`, or
  bootstrap product context from live Amazon pages. Even if they just say
  "optimize my listing" or "write bullets" — this is the skill.
---

# Amazon Marketing Skill

An open-source Claude Code skill for Amazon product listing optimization,
keyword strategy, and content marketing.

## What This Skill Does

Creates, optimizes, and audits Amazon product detail page content:
titles, bullet points, descriptions, backend search terms, A+ Content
planning, competitor analysis, and product onboarding — all grounded in
Amazon's actual policies (updated through early 2026) and current best
practices for both A9/A10 keyword search and Rufus AI conversational discovery.

## Decision Tree

1. **User wants to create a new listing from scratch?**
   → Load `skills/listing-optimizer/SKILL.md`
   → Interview for product details using `templates/listing-brief.md`
   → Generate title → bullets → description → backend keywords

2. **User wants to onboard products from ASINs or build product context files?**
   → Load `skills/product-onboarding/SKILL.md`
   → Read `asins.csv` if present
   → Create or update `products/[ASIN]/product-context.md`

3. **User wants to improve an existing listing?**
   → Load `skills/listing-audit/SKILL.md` first to score current state
   → Then load `skills/listing-optimizer/SKILL.md` to rewrite weak elements

4. **User wants keyword research?**
   → Load `skills/keyword-research/SKILL.md`
   → Accept seed keywords, competitor ASINs, or product descriptions
   → Output structured keyword map

5. **User wants competitor analysis?**
   → Load `skills/competitor-analysis/SKILL.md`
   → Tear down 3-5 competitor listings

6. **User wants A+ Content planning?**
   → Load `skills/a-plus-content/SKILL.md`
   → Plan module layout, write copy, create image briefs

7. **User wants a quick fix on one element (e.g., "just fix my title")?**
   → Jump directly to that section in `skills/listing-optimizer/SKILL.md`

## Context Loading

Before generating any product-specific content, resolve context in this order:

1. Load `brand-context.md` from the project root or `.agents/` directory if it exists
2. Load `products/[ASIN]/product-context.md` for the product being worked on
3. If multiple products exist and the user has not specified one, ask which ASIN to use

If no product context file exists, either run `skills/product-onboarding/SKILL.md`
or interview the user for minimum viable context before writing:
- What is the product? (category, key features, materials)
- Who is it for? (target buyer, use cases)
- What makes it different? (vs. competitors)
- Are you Brand Registered? (affects A+ Content eligibility)
- What marketplace(s)? (US, CA, UK — limits vary)

When reading product context, prefer this provenance order:

1. `User Confirmed Data`
2. `Amazon Observed Data`
3. `AI Inferences`

Do not treat inferences as confirmed business facts.

## Reference Files

All sub-skills should consult these before generating content:
- `references/amazon-style-guide.md` — Character limits, prohibited terms, formatting rules
- `references/rufus-optimization.md` — How to optimize for Amazon's AI shopping assistant
- `references/backend-keywords-guide.md` — 249-byte rules, formatting, what to include/exclude

## Optional MCP Integrations

This skill works standalone with zero paid dependencies. If MCP servers
are available, sub-skills can optionally use:

| MCP Server                      | Enhancement                                    |
|---------------------------------|------------------------------------------------|
| Playwright MCP / CLI            | Browser-based PDP capture for ASIN onboarding  |
| AmazonSeller-mcp-server        | Pull live catalog data and current listing copy |
| Amazon Ads MCP (Official)       | Tie listing changes to ad performance data     |
| KuudoAI/amazon_ads_mcp          | Campaign data for keyword prioritization       |
| Seller Labs MCP                 | Profitability data to prioritize ASINs         |
| PPC Prophet MCP                 | PPC data + n8n workflow integration            |

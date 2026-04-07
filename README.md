# Amazon Marketing Skill

An open-source Claude Code skill for Amazon product listing optimization,
keyword strategy, and content marketing.

**No paid dependencies. No vendor lock-in. Works standalone.**

---

## What This Skill Does

Creates, optimizes, and audits Amazon product detail page content:

- **Product titles** — Compliant, keyword-optimized, mobile-aware
- **Bullet points** — Benefit-driven, compliant with Aug 2024 format requirements
- **Product descriptions** — Conversion-focused, keyword-rich
- **Backend search terms** — Byte-counted, gap-filling, multilingual
- **A+ Content** — Module planning, copy, and image briefs
- **Keyword research** — Tiered keyword maps with placement recommendations
- **Competitor analysis** — Structured teardowns with gap identification
- **Listing audits** — Compliance checks + quality scoring (0-100)
- **Product onboarding** — Build per-product context from `asins.csv` using SKU/ASIN references

All grounded in Amazon's actual policies (verified through April 2026) and
current best practices for both A9/A10 keyword search and Rufus AI
conversational discovery.

## Installation

### Recommended
```bash
npx skills add brianmoney/amazon-marketing-skill
```

### Manual
Download and place the `SKILL.md` files in your agent's skills directory.
The skill is just markdown files — it works with any AI coding agent that
supports the skills spec.

## Usage

Just ask your AI agent:

- "Optimize my Amazon listing for [product]"
- "Write bullet points for my [product]"
- "Audit this Amazon listing" + paste content
- "Do keyword research for [product category]"
- "Analyze these competitor listings" + paste SKUs, ASINs, or listing content
- "Plan A+ Content for my product"
- "Onboard these products from asins.csv"

### Personalizing for Your Brand

Use a shared `brand-context.md` file plus one per-product context file at
`products/[ASIN]/product-context.md`. The recommended setup is:

- `brand-context.md` for shared brand voice, marketplace, and messaging rules
- `asins.csv` for the onboarding queue
- `products/[ASIN]/product-context.md` for product-specific facts and notes

When present, sub-skills load `brand-context.md` plus the selected product's
context file before generating content.

Useful content to include:
- Brand voice and tone guidelines
- Target audience description
- Catalog overview and product line structure
- Keywords that have converted well in past campaigns
- Terms or phrases to always avoid
- Past learnings from listing tests

Structured templates are included in:

- `templates/brand-context.template.md`
- `templates/product-context.template.md`

`products/[ASIN]/product-context.md` deliberately separates:

- `Amazon Observed Data` for facts captured from the PDP
- `AI Inferences` for agent-generated interpretation
- `User Confirmed Data` for trusted business truth

### Product Onboarding

The `product-onboarding` skill turns `asins.csv` into structured product files
that the rest of the skill suite can reuse.

Sellers can identify products by SKU or ASIN. The canonical product file path
still uses the ASIN when known: `products/[ASIN]/product-context.md`.

Recommended workflow:

1. Create `asins.csv` in the project root
2. Add one row per product you want to onboard
3. Ask the agent to onboard the products
4. Let the agent capture public PDP data from Amazon
5. Answer the follow-up questions for missing business context
6. Reuse `brand-context.md` and `products/[ASIN]/product-context.md` across
   listing optimization, audits, keyword research, and A+ planning

Suggested `asins.csv` format:

```csv
sku,asin,marketplace,amazon_url,product_label,status,notes
SKU-001,B000000001,US,https://www.amazon.com/dp/B000000001,Main product,pending,
SKU-002,B000000002,US,,Variant 2,pending,Needs keyword validation
```

The onboarding skill uses this fallback order for product introspection:

1. Playwright MCP tools
2. Playwright CLI/browser automation
3. Default agent web/fetch tools
4. User-pasted listing content
5. Direct user interview

What gets stored where:

- `brand-context.md`: brand voice, guardrails, marketplace priorities, and shared learnings
- `products/[ASIN]/product-context.md`: product-specific observed facts, inferences, and user-confirmed truth

What the agent should fill automatically when possible:

- title, brand, price, rating, review count
- bullets, description, A+ presence
- category breadcrumbs, variants, visible badges
- materials, dimensions, included items, and specs when explicitly shown

What usually still requires user input:

- actual target audience
- problem solved and top differentiators
- certifications/compliance claims
- warranty details
- primary and secondary keywords
- converting search terms and important competitor SKUs/ASINs

This separation is intentional:

- `Amazon Observed Data` should only contain facts directly seen on the PDP
- `AI Inferences` can summarize patterns or likely positioning, but should not be treated as confirmed truth
- `User Confirmed Data` is the durable source of business truth for downstream skills

## Structure

```
amazon-marketing-skill/
├── SKILL.md                              # Main orchestrator
├── README.md
├── asins.csv                             # (Optional, user-created) SKU/ASIN onboarding queue
├── brand-context.md                      # (Optional, user-created) Shared brand guidance
│
├── skills/
│   ├── product-onboarding/SKILL.md       # Builds per-product context files
│   ├── listing-optimizer/SKILL.md        # Title, bullets, desc, backend
│   ├── keyword-research/SKILL.md         # Keyword maps and gap analysis
│   ├── competitor-analysis/SKILL.md      # Competitor teardowns
│   ├── a-plus-content/SKILL.md           # A+ Content planning and copy
│   └── listing-audit/SKILL.md            # Compliance + quality scoring
│
├── references/
│   ├── amazon-style-guide.md             # Character limits, rules, formulas
│   ├── rufus-optimization.md             # AI shopping assistant strategies
│   └── backend-keywords-guide.md         # 249-byte rules, best practices
│
├── templates/
│   ├── brand-context.template.md         # Shared brand context template
│   ├── listing-brief.md                  # Product info input template
│   ├── product-context.template.md       # Per-product context template
│   ├── keyword-map.md                    # Keyword mapping output template
│   └── audit-scorecard.md                # Audit scoring template
│
└── products/
    └── [ASIN]/
        └── product-context.md            # Per-product observed, inferred,
                                          # and user-confirmed context
```

## Sources

This skill is built on verified information from:

- **Amazon Seller Central** — Product detail page rules, title requirements
  (Jan 2025), bullet point requirements (Aug 2024), category style guides
- **eComEngine** — Title and bullet point guideline analysis
- **Parker-Lambert** — Bullet point compliance framework for CPG brands
- **Amalytix** — Amazon Rufus guide (2026), character limits reference
- **Keywords.am** — Character limits technical reference (2026),
  product description guide
- **ListingForge** — Bullet points guide (2026), backend keywords guide
- **Tinuiti** — Rufus AI optimization strategies (agency research)
- **ZonGuru** — Rufus listing engineering playbook
- **SellerMetrics** — COSMO algorithm analysis, Rufus optimization guide
- **Nova Analytics** — Rufus impact on seller metrics
- **Seller Labs** — Rufus optimization workflow, Claude Code integration
- **Amazon Q3/Q4 2025 Earnings Calls** — Rufus scale and impact data
- **Adobe Analytics** — Holiday 2025 AI shopping traffic data
- **SellerSprite** — Backend search terms checklist (2026)
- **SellerApp** — Backend keywords guide (2026)
- **CLOSO** — Backend keywords masterclass (2026)
- **Lead Advisors** — Backend search terms guide (2025)
- **Goat Consulting** — Product detail page rules compliance
- **Flairox** — PDP rules compliance checklist

## Optional MCP Integrations

The skill works completely standalone. If you have MCP servers connected,
it can optionally use:

| MCP Server                      | Enhancement                                    |
|---------------------------------|------------------------------------------------|
| Playwright MCP / CLI            | Browser-based PDP capture for product onboarding |
| AmazonSeller-mcp-server        | Pull live catalog data and current listing copy |
| Amazon Ads MCP (Official)       | Tie listing changes to ad performance data     |
| KuudoAI/amazon_ads_mcp          | Campaign data for keyword prioritization       |
| Seller Labs MCP                 | Profitability data to prioritize products      |
| PPC Prophet MCP                 | PPC data + n8n workflow integration            |

## Contributing

Found an error in the Amazon policy references? Have a better framework
for bullet point writing? PRs welcome.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).

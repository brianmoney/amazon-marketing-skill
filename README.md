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

All grounded in Amazon's actual policies (verified through April 2026) and
current best practices for both A9/A10 keyword search and Rufus AI
conversational discovery.

## Installation

### Claude Code
```bash
# Copy skill files to your skills directory
git clone https://github.com/[your-handle]/amazon-marketing-skill.git
cp -r amazon-marketing-skill/* ~/.claude/skills/amazon-marketing/
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
- "Analyze these competitor listings" + paste ASINs/content
- "Plan A+ Content for my product"

### Personalizing for Your Brand

Create a `product-context.md` file in your project root (or `.agents/`
directory) to give the skill persistent brand context. When present, all
sub-skills load it automatically before generating content.

Useful content to include:
- Brand voice and tone guidelines
- Target audience description
- Catalog overview and product line structure
- Keywords that have converted well in past campaigns
- Terms or phrases to always avoid
- Past learnings from listing tests

No required format — plain markdown notes work fine.

## Structure

```
amazon-marketing-skill/
├── SKILL.md                              # Main orchestrator
├── README.md
│
├── skills/
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
│   ├── listing-brief.md                  # Product info input template
│   ├── keyword-map.md                    # Keyword mapping output template
│   └── audit-scorecard.md                # Audit scoring template
│
└── product-context.md                    # (Optional, user-created) Brand voice,
                                          # target audience, catalog info, past
                                          # learnings — auto-loaded by all sub-skills
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
| AmazonSeller-mcp-server        | Pull live catalog data and current listing copy |
| Amazon Ads MCP (Official)       | Tie listing changes to ad performance data     |
| KuudoAI/amazon_ads_mcp          | Campaign data for keyword prioritization       |
| Seller Labs MCP                 | Profitability data to prioritize ASINs         |
| PPC Prophet MCP                 | PPC data + n8n workflow integration            |

## Contributing

Found an error in the Amazon policy references? Have a better framework
for bullet point writing? PRs welcome.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).

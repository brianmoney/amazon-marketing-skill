---
name: listing-audit
description: >
  Score and audit an existing Amazon product listing against current Amazon
  policies and best practices. Use when the user wants to evaluate listing
  quality, check compliance, identify problems, find optimization opportunities,
  or get a health check on their Amazon content. Also use when the user pastes
  an existing listing and asks "what's wrong with this" or "how can I improve this."
---

# Listing Audit

Evaluates an existing Amazon listing against current Amazon policies (2024-2026),
compliance requirements, and optimization best practices for both traditional
search and Rufus AI discovery.

## Prerequisites

Load `references/amazon-style-guide.md`, `references/rufus-optimization.md`, and `references/backend-keywords-guide.md`.

If `brand-context.md` exists in the project root or `.agents/` directory,
load it for shared brand context and past learnings that inform audit recommendations.

If `products/[ASIN]/product-context.md` exists, load it for product-specific
context. Prefer `User Confirmed Data`, then `Amazon Observed Data`, then `AI Inferences`.

Resolve product references by SKU or ASIN using the product context file's
`SKU:` and `ASIN:` fields.

If multiple product folders exist and the user has not specified a product, ask
which SKU or ASIN to use before auditing.

The user must provide either:
- A full listing (title, bullets, description, and ideally backend keywords)
- An Amazon URL, ASIN, or seller SKU (if Playwright or MCP tooling is connected, pull live
  data; otherwise ask the user to paste the content)
- A screenshot of a listing (describe what you see)

## Audit Process

### Phase 1: Compliance Check

Run every element through the compliance rules from the style guide.
Flag violations as **CRITICAL** (risks suppression), **WARNING** (violates
best practices), or **INFO** (improvement opportunity).

**Title Compliance:**
- [ ] Under character limit for category (200 default)?
- [ ] No prohibited special characters (!$?_{}^¬¦)?
- [ ] No word repeated more than twice?
- [ ] No ALL CAPS words?
- [ ] No promotional language ("Best Seller", "#1", "Sale", etc.)?
- [ ] No subjective claims ("Amazing", "Perfect")?
- [ ] No price, availability, or condition info?
- [ ] Brand name present?
- [ ] First letter capitalized per word?

**Bullet Point Compliance:**
- [ ] All 5 slots used?
- [ ] Header: Body format on each?
- [ ] No emojis?
- [ ] No special characters (™®€…†‡¢£¥©±~â)?
- [ ] No ALL CAPS sections?
- [ ] No guarantee/refund language?
- [ ] No promotional claims?
- [ ] No competitor brand names?
- [ ] No company info, URLs, or contact details?
- [ ] No period at the end of any bullet?
- [ ] No repetition between bullets?
- [ ] No repetition of title content?
- [ ] Estimated total bytes under 1,000 (indexing limit)?

**Description Compliance:**
- [ ] Under 2,000 characters?
- [ ] No HTML tags?
- [ ] No prohibited content?
- [ ] Does not duplicate bullet points verbatim?

**Backend Keywords Compliance (if provided):**
- [ ] Under 249 bytes?
- [ ] No commas or punctuation?
- [ ] No competitor brand names?
- [ ] No ASINs/UPCs?
- [ ] No words duplicated from visible content?

### Phase 2: Quality Scoring

Score each element on a 0-100 scale based on effectiveness:

**Title Quality (25 points possible):**
| Criterion                                    | Points |
|----------------------------------------------|--------|
| Primary keyword within first 80 characters   | 5      |
| Answers an implicit buyer question           | 5      |
| Includes key differentiator                  | 5      |
| Optimal length usage (not too short/stuffed) | 5      |
| Follows category formula                     | 5      |

**Bullet Point Quality (30 points possible):**
| Criterion                                    | Points |
|----------------------------------------------|--------|
| All 5 slots used                             | 3      |
| Each covers a unique angle                   | 5      |
| Feature→benefit→use case connections         | 7      |
| Specific details (numbers, materials, dims)  | 5      |
| Natural keyword integration                  | 5      |
| Addresses different buyer objections         | 5      |

**Description Quality (15 points possible):**
| Criterion                                    | Points |
|----------------------------------------------|--------|
| Adds info beyond bullets (not just repeat)   | 5      |
| Includes secondary keywords                  | 3      |
| Addresses buyer objection                    | 4      |
| Readable structure (short paragraphs)        | 3      |

**Backend Keywords Quality (15 points possible):**
| Criterion                                    | Points |
|----------------------------------------------|--------|
| Byte count efficient (no waste)              | 5      |
| No duplication with visible content          | 3      |
| Includes synonyms                            | 3      |
| Includes Spanish terms (US)                  | 2      |
| Includes use-case/intent terms               | 2      |

**Rufus Readiness (15 points possible):**
| Criterion                                    | Points |
|----------------------------------------------|--------|
| Listing answers "who is this for"            | 3      |
| Listing answers "what problem does it solve" | 3      |
| Listing answers "how/when/where to use it"   | 3      |
| Use-case specificity in bullets              | 3      |
| Natural language (not keyword-stuffed)       | 3      |

### Phase 3: Recommendations

Deliver findings in priority order:

1. **Critical Fixes** (compliance risks — do these first)
2. **Top 3 Quick Wins** (highest-impact changes with least effort)
3. **Keyword Coverage Gaps** (important terms missing from listing)
4. **Rufus Optimization Opportunities** (conversational discovery improvements)
5. **Long-Term Improvements** (A+ Content, image recommendations, Q&A strategy)

## Output Format

Load `templates/audit-scorecard.md` and populate every section with findings
from the audit. Do not reproduce the template inline — fill it out and present
the completed scorecard to the user.

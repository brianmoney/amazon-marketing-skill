---
name: keyword-research
description: >
  Amazon keyword research and keyword mapping for product listings. Use when
  the user wants to find keywords, build a keyword strategy, analyze search
  terms, identify keyword gaps, map keywords to listing elements, or optimize
  keyword coverage. Also use when the user provides a Helium 10, Jungle Scout,
  Brand Analytics, or Search Term Report export and wants analysis.
---

# Amazon Keyword Research

Builds structured keyword maps for Amazon product listings, organizing terms
by priority tier and mapping them to specific listing elements (title, bullets,
description, backend).

## Prerequisites

Load `references/backend-keywords-guide.md` — used for backend string
construction rules, byte counting, and what to include or exclude.

Load `references/amazon-style-guide.md` — used when checking keyword
compliance (prohibited terms, stop words, formatting rules).

If `product-context.md` exists in the project root or `.agents/` directory,
load it for target audience, product details, and past keyword learnings.

## How This Skill Works

This skill does NOT have access to live Amazon search volume data. It works by:

1. **Leveraging product knowledge and category expertise** to generate
   comprehensive keyword candidates based on what buyers actually search
2. **Parsing data the user provides** — CSV exports from Helium 10, Jungle Scout,
   Amazon Brand Analytics, or Search Term Reports
3. **Structuring keywords into actionable tiers** that map directly to listing elements
4. **Identifying gaps** between current listing content and potential keyword coverage

If the user has access to keyword tools, recommend they pull data and bring it
back for analysis. If not, generate research-informed suggestions based on the
product description and category knowledge.

## Keyword Tier Framework

### Tier 1: Primary Keywords (1-3 terms)
- Highest relevance, highest volume
- MUST appear in the product title (within first 80 characters)
- These define what the product IS
- Example: "glass vacuum storage container"

### Tier 2: Secondary Keywords (5-10 terms)
- High relevance, moderate-to-high volume
- Should appear in bullet points and/or description
- These add specificity and capture related searches
- Example: "airtight food container", "vacuum seal container", "glass meal prep container"

### Tier 3: Long-Tail Keywords (10-25 terms)
- Moderate relevance, lower volume, higher conversion intent
- Distribute across bullets, description, and backend
- These capture specific buyer scenarios and questions
- Example: "glass container for meal prep", "vacuum container for berries",
  "airtight container for pantry storage"

### Tier 4: Backend-Only Keywords (10-30 terms)
- Synonyms, translations, misspellings, use-case terms
- Do NOT appear in visible listing copy — backend search terms only
- These expand reach without cluttering customer-facing content
- Example: "tupperware recipiente vidrio contenedor hermético cocina leftovers marinate"

### Tier 5: Rufus/Intent Keywords (5-15 terms)
- Conversational phrases and question-based queries
- Integrate naturally into bullets and description
- These target how Rufus-era shoppers discover products
- Example: "keeps food fresh longer", "safe for microwave and freezer",
  "best container for meal prep", "won't stain or absorb odors"

## Keyword Research Process

### Step 1: Seed Keyword Generation

Ask the user for:
- Product name and type
- 3-5 words they'd use to describe the product
- What problem it solves
- Who the target buyer is
- 2-3 competitor products (names or ASINs)

From these inputs, generate an initial seed list of 10-15 terms.

### Step 2: Keyword Expansion

For each seed keyword, expand using these methods:

**Synonym expansion:**
- "container" → "canister, jar, keeper, holder, organizer, vessel"
- "vacuum" → "airtight, sealed, hermetic, airless"

**Modifier expansion:**
- Material: "glass", "borosilicate", "BPA-free"
- Size: "small", "large", "32 oz", "liter"
- Feature: "stackable", "leakproof", "microwave safe"
- Use case: "meal prep", "lunch", "leftover", "pantry"
- Audience: "for kids", "for office", "for camping"

**Question-based expansion (Rufus-ready):**
- "how to keep food fresh longer"
- "best container for meal prep"
- "glass vs plastic food storage"
- "does vacuum seal container work"

**Spanish translations (US marketplace):**
- Product terms: "contenedor de vidrio", "recipiente al vacío"
- Use-case terms: "almacenamiento de alimentos", "preparación de comidas"

### Step 3: Competitive Gap Analysis

If the user provides competitor ASINs or listing content:
1. Extract all keywords from competitor titles, bullets, descriptions
2. Identify terms they target that the user does NOT
3. Flag high-value gaps (relevant terms competitors rank for that user misses)
4. Note terms competitors use that may not be compliant (and should be avoided)

### Step 4: Keyword Mapping

Map every keyword to a specific listing element. Example (illustrative — the
final output should follow the per-tier table structure in `templates/keyword-map.md`):

```
| Keyword                          | Tier | Placement        | Status    |
|----------------------------------|------|------------------|-----------|
| glass vacuum storage container   | 1    | Title (pos 1-5)  | Primary   |
| airtight food container          | 2    | Bullet 1         | Include   |
| meal prep container glass        | 2    | Bullet 5         | Include   |
| vacuum seal food keeper          | 3    | Description      | Include   |
| contenedor vidrio hermético      | 4    | Backend          | Include   |
| keeps food fresh longer          | 5    | Bullet 1 natural | Rufus     |
```

### Step 5: Backend String Construction

After mapping, take all Tier 4 keywords and build the backend search terms string:
1. Remove any words already present in Tier 1-3 placements
2. Remove stop words
3. Order by estimated value (highest first)
4. Calculate byte count
5. Trim to under 235 bytes (safety buffer for 249 limit)

See `references/backend-keywords-guide.md` for detailed formatting rules.

## Working with User-Provided Data

### If the user provides a Search Term Report (from Amazon Advertising):
- Sort by conversions (descending)
- Identify converting search terms NOT in current listing
- Flag high-spend, zero-conversion terms to consider excluding from ads
- Recommend adding converting terms to organic listing content

### If the user provides Helium 10 / Jungle Scout export:
- Sort by search volume and relevance
- Cross-reference against current listing content
- Identify high-volume terms missing from listing
- Flag terms with high volume but low relevance (avoid)

### If the user provides Brand Analytics data:
- Analyze click share and conversion share
- Identify terms where the product has impressions but low click share (title needs work)
- Identify terms where clicks are high but conversion is low (bullets/description need work)

## Output Format

Load `templates/keyword-map.md` and populate every tier table and the backend
string section with research findings. Do not reproduce the template inline —
fill it out and present the completed keyword map to the user.

---
name: listing-optimizer
description: >
  Generate or rewrite Amazon product listing content: titles, bullet points,
  product descriptions, and backend search terms. Use when the user wants to
  create a new listing, rewrite existing copy, optimize specific elements,
  or generate Amazon-compliant product content. Handles full listings or
  individual elements (e.g., "just fix my title").
---

# Listing Optimizer

Creates Amazon-compliant, conversion-optimized listing content that balances
traditional A9/A10 keyword search with Rufus AI conversational discovery.

## Prerequisites

Before generating any content, you MUST have:

1. **Product information** — What is it? Materials, features, specifications,
   dimensions, what's included.
2. **Target audience** — Who buys this? What problem does it solve?
3. **Differentiators** — What makes it different from competitors?
4. **Category** — Which Amazon category? (Affects character limits)
5. **Keywords** — Primary and secondary target keywords
   (If not provided, generate suggestions and confirm with the user)
6. **Marketplace** — US, UK, CA, etc. (Affects backend byte limits)

Load `references/amazon-style-guide.md` for current rules.
Load `references/rufus-optimization.md` for AI discovery optimization.
Load `references/backend-keywords-guide.md` for backend string construction rules.

If `brand-context.md` exists in the project root or `.agents/` directory,
load it for shared brand voice and past learnings.

If `products/[ASIN]/product-context.md` exists, load it for product-specific
facts. Prefer `User Confirmed Data`, then `Amazon Observed Data`, then `AI Inferences`.

If multiple product folders exist and the user has not specified an ASIN, ask
which ASIN to use before writing.

## Workflow

### Step 1: Interview (if needed)

If the user hasn't provided sufficient product info, interview them using
the framework from `templates/listing-brief.md`. Keep it conversational.
Minimum viable info to start: product name, 3-5 key features, target buyer.

### Step 2: Generate Title

**Process:**
1. Identify the primary keyword (highest search volume, most relevant)
2. Check the category character limit (200 default, lower for some categories)
3. Write for mobile first: critical info within first 70-80 characters
4. Apply the category title formula from the style guide
5. Verify compliance: no prohibited characters, no word repeated more than twice,
   no promotional language

**Title Structure:**
```
[Brand] [Primary Keyword Phrase], [Key Feature/Benefit], [Secondary Feature] - [Size/Count/Variant]
```

**Self-Check Before Presenting:**
- [ ] Under character limit for this category?
- [ ] Primary keyword within first 80 characters?
- [ ] Brand name included?
- [ ] No prohibited characters (!$?_{}^¬¦)?
- [ ] No word repeated more than twice?
- [ ] No promotional or subjective claims?
- [ ] First letter of each word capitalized (not ALL CAPS)?
- [ ] Would this make sense to a mobile shopper seeing only the first 70 chars?
- [ ] Does this answer at least one implicit buyer question? (Rufus optimization)

### Step 3: Generate Bullet Points

**Process:**
1. Map out 5 distinct selling angles — no overlap between bullets
2. For each bullet, write in Header: Body format
3. Connect every feature to a real-world benefit and use case
4. Integrate 2-3 keywords per bullet naturally (never forced)
5. Keep each bullet under 200 characters for safe indexing (total under 1,000 bytes)
6. Front-load the strongest bullet (most visible, especially mobile)

**5-Bullet Framework:**

| Bullet | Focus                        | Pattern                                      |
|--------|------------------------------|----------------------------------------------|
| 1      | Primary benefit / use case   | What it DOES for the buyer + when/where/how   |
| 2      | Quality / materials          | What it's MADE of + why that matters          |
| 3      | Convenience / ease of use    | How EASY it is to use/maintain + compatibility|
| 4      | What's included / specs      | What you GET + specific numbers/dimensions    |
| 5      | Who it's for / trust signal  | WHO benefits + social proof or brand credibility|

**Each Bullet Structure:**
```
[Benefit Header]: [Feature detail that proves the benefit, with specific
numbers or materials, connected to a real use case the buyer recognizes]
```

**Example (for a glass vacuum container):**
```
Keeps Food Fresh Up to 5x Longer: One-touch vacuum pump removes air to slow
oxidation and bacterial growth, keeping berries, cut vegetables, and leftovers
fresh for days instead of hours

Premium Borosilicate Glass: Unlike plastic containers, this lab-grade glass
will not stain, absorb odors, or leach chemicals — safe for microwave,
freezer, and dishwasher without warping

Simple One-Hand Operation: Press the silicone valve on the lid to seal in
seconds — no separate pump needed, no batteries, no complicated parts to lose

Complete Starter Set: Includes three nesting containers (12 oz, 24 oz, 34 oz)
with interchangeable lids, a silicone sealing ring replacement, and a quick-
start guide

Designed for Meal Prep and Busy Families: Stackable space-saving design fits
neatly in standard refrigerators, with measurement markings for portion control
and grab-and-go convenience
```

**Self-Check Before Presenting:**
- [ ] Exactly 5 bullets?
- [ ] Header: Body format on each?
- [ ] No emoji, no ALL CAPS, no special characters (™®€ etc.)?
- [ ] No promotional language ("best", "#1", "free shipping")?
- [ ] No guarantee/refund language?
- [ ] No competitor brand names?
- [ ] No period at the end of any bullet?
- [ ] Each bullet covers a UNIQUE angle (no repetition)?
- [ ] No overlap with title content (add new info, don't repeat)?
- [ ] Total bytes across all 5 bullets under 1,000?
- [ ] Does each bullet connect a feature to a use case? (Rufus optimization)
- [ ] Would a shopper scanning these bullets in 5 seconds get the key value?

### Step 4: Generate Product Description

**Process:**
1. DO NOT repeat bullet points — expand, don't duplicate
2. Use the 5-step framework: Problem → Solution → Specifics → Objections → Confidence
3. Keep under 2,000 characters
4. Include secondary and long-tail keywords not covered elsewhere
5. Short paragraphs (2-3 sentences max for mobile readability)
6. If the seller is Brand Registered, note that A+ Content should ALSO be created
   (description feeds the algorithm; A+ Content converts shoppers)

**Framework:**
```
[Open with the buyer's problem or desire — what brought them to search]

[Present your product as the solution — connect to their specific situation]

[Support with specifics — materials, dimensions, certifications, testing]

[Handle the top 1-2 objections buyers have in this category]

[Close with a confidence statement — what using this product feels like,
or a practical next step]
```

**Self-Check:**
- [ ] Under 2,000 characters?
- [ ] Does NOT repeat bullet point text verbatim?
- [ ] No HTML tags (plain text only)?
- [ ] Includes keywords not covered in title/bullets?
- [ ] No prohibited content (URLs, pricing, reviews, promotional claims)?
- [ ] Addresses a buyer objection specific to this category?
- [ ] Covers use cases or scenarios not mentioned in bullets? (Rufus optimization)

### Step 5: Generate Backend Search Terms

**Process:**
1. List all unique words already in title, bullets, and description
2. Identify gaps: synonyms, Spanish translations, use-case terms, misspellings
3. Build the string per `references/backend-keywords-guide.md`
4. Count bytes — must be under 249 (target 235 for safety buffer)
5. Separate with single spaces, no commas, no punctuation

**Present the backend string AND the byte count to the user.**

**Self-Check:**
- [ ] Under 249 bytes (235 recommended)?
- [ ] No commas or punctuation?
- [ ] No words that already appear in visible listing content?
- [ ] No competitor brand names?
- [ ] No ASINs/UPCs?
- [ ] No subjective claims ("best", "amazing")?
- [ ] No stop words wasting bytes?
- [ ] Includes Spanish translations (US marketplace only)?
- [ ] Includes relevant synonyms and alternative names?
- [ ] Highest-value keywords placed first in the string?

---

## Output Format

Present the complete listing in this order:

```
## Product Title
[title text]
Characters: [count] / [limit for category]

## Bullet Points
1. [bullet 1]
2. [bullet 2]
3. [bullet 3]
4. [bullet 4]
5. [bullet 5]
Total characters: [count] | Estimated bytes: [count] / 1,000 indexing limit

## Product Description
[description text]
Characters: [count] / 2,000

## Backend Search Terms
[keyword string]
Bytes: [count] / 249

## Compliance Notes
[Any category-specific warnings or recommendations]

## Rufus Optimization Notes
[Which shopper questions this listing can now answer]
```

After presenting, ask the user:
1. "Does this match your brand voice?"
2. "Any features or use cases I should emphasize more?"
3. "Want me to audit the keyword coverage or adjust any section?"

---
name: a-plus-content
description: >
  Plan and write Amazon A+ Content (Enhanced Brand Content) for Brand Registered
  sellers. Use when the user wants to create A+ Content, plan A+ modules, write
  A+ copy, create image briefs for A+ layouts, or improve existing A+ Content.
  Also trigger when the user mentions Brand Story, EBC, Premium A+, or enhanced
  content on Amazon.
---

# A+ Content Planning

Plans module layouts, writes copy, and creates image briefs for Amazon A+
Content — the rich media content available to Brand Registered sellers that
replaces the standard product description on the detail page.

## Prerequisites

- User must be enrolled in Amazon Brand Registry
- Load `references/amazon-style-guide.md` for compliance rules
- Load `references/rufus-optimization.md` — A+ Content text IS read by Rufus
  even though it is NOT indexed for traditional Amazon search
- If `brand-context.md` exists in the project root or `.agents/` directory,
  load it for shared brand voice and past learnings
- If `products/[ASIN]/product-context.md` exists, load it for product-specific
  target audience and product facts. Prefer `User Confirmed Data`, then
  `Amazon Observed Data`, then `AI Inferences`
- If multiple product folders exist and the user has not specified an ASIN,
  ask which ASIN to use before planning A+ Content

## Key Facts About A+ Content

### What It Does
- Replaces the standard text description on the product detail page
- Allows rich media: images, comparison charts, banners, formatted text
- Amazon reports an average **5.6% sales lift** for listings using A+ Content
- Drives conversion by engaging visual shoppers

### Indexing Reality
- **A+ Content text is NOT indexed for Amazon keyword search**
  (per Amazon's official documentation)
- The standard text description IS indexed
- **Best practice**: Keep a keyword-rich standard text description for SEO AND
  build A+ Content for conversion. They serve different functions.
- **However**: Rufus DOES read A+ Content text modules. Writing clear, informative
  A+ Content improves Rufus's ability to recommend your product.

### Module Limits
- Standard A+: Up to 5 content modules per ASIN
- Premium A+ (by invitation / meeting criteria): Up to 7 modules
- Character limits vary from 150 to 6,000 characters depending on module type
- Text embedded in images is NOT readable by Rufus or screen readers

## Available Module Types

### Standard A+ Modules (most common):

1. **Standard Image and Text**
   - One image + text block
   - Good for: Feature highlight with supporting visual

2. **Standard Comparison Chart**
   - Side-by-side product comparison (up to 5 products)
   - Good for: Cross-selling within your product line, NOT for comparing
     against competitors

3. **Standard Three Images and Text**
   - Three image blocks with text under each
   - Good for: Showing three use cases or three key features

4. **Standard Four Images and Text**
   - Four image blocks with text
   - Good for: "What's in the box" or step-by-step instructions

5. **Standard Single Image and Highlights**
   - Hero image with several text callouts
   - Good for: Product overview or "at a glance" feature summary

6. **Standard Single Image and Specs**
   - Image with specification details
   - Good for: Technical products with dimensions/specs

7. **Standard Text**
   - Text-only block
   - Good for: Brand story or detailed product narrative
   - Important for Rufus: Text modules are readable by AI

8. **Standard Image Header with Text**
   - Full-width banner image with overlaid text
   - Good for: Brand statement or lifestyle hero shot

### Brand Story Module
- Appears above A+ Content
- Carousel format across ALL of your brand's products
- Includes brand logo, background image, and up to 4 cards linking to
  other products or your Brand Store
- Important for brand building but less impactful for individual product conversion

## Module Layout Strategy

### Recommended 5-Module Layout for Most Products:

**Module 1: Hero Banner (Standard Image Header with Text)**
- Full-width lifestyle image showing product in use
- Short headline: Primary value proposition
- Goal: Emotional connection, context setting

**Module 2: Feature Breakdown (Standard Three Images and Text)**
- Three product detail shots, each highlighting one key feature
- Short text under each: Feature → Benefit connection
- Goal: Educate on top 3 differentiators

**Module 3: How It Works / Use Cases (Standard Four Images and Text)**
- Four images showing different use scenarios
- Text: Specific use case description for each
- Goal: Help buyer see the product in their life
- Rufus note: This is high-value for AI discovery — write text that explicitly
  describes WHO uses it, WHEN, and WHY

**Module 4: Product Comparison (Standard Comparison Chart)**
- Compare 3-5 products in YOUR line (not competitors)
- Columns: features, sizes, ideal-for descriptions
- Goal: Guide buyer to right product variant, cross-sell

**Module 5: Specs + Trust (Standard Single Image and Specs OR Standard Text)**
- Option A: Specs image with dimensions, materials, certifications
- Option B: Text block with brand story, quality commitment, warranty info
- Goal: Address final objections, build confidence
- Rufus note: Text blocks with specific materials, certifications, and
  care instructions give Rufus data for detailed Q&A responses

### Alternative Layouts:

**For Technical Products:**
Replace Module 3 with a specs-heavy module. Add a "How to Use" module
with step-by-step images.

**For Multi-Pack or Bundle Products:**
Include a "What's In the Box" module (Standard Four Images) showing each
item separately with individual descriptions.

**For Products with Strong Social Proof:**
Add a module with user-generated photo (styled) + testimonial-style copy
(not actual quotes from reviews — rephrase as benefit statements).

## Writing A+ Content Copy

### Principles
- Write for SCANNING, not reading — shoppers scroll fast
- Headlines: 5-8 words maximum, benefit-focused
- Body text: 1-2 sentences per text block
- Use specific numbers and details (not vague claims)
- Avoid all prohibited terms from the style guide
- Write text that describes WHO, WHAT, WHEN, WHERE, WHY — Rufus reads this

### Image Brief Format

For each image needed, provide a brief the user (or designer) can execute:

```
## Image Brief: [Module Name]

**Dimensions**: [width × height pixels — varies by module]
**Type**: [Product shot / Lifestyle / Infographic / Flat lay]
**Subject**: [What should be shown]
**Setting/Background**: [Where/what context]
**Key Elements**: [Callout text, badges, or overlays to include]
**Mood**: [Professional / Warm / Active / Clean / Rustic / etc.]
**Do NOT include**: [Competitor products, pricing, promotional text]
**Alt Text Suggestion**: [Descriptive alt text for accessibility + Rufus]
```

### Common Dimensions by Module Type
- Full-width banner: 970 × 600 pixels
- Standard image: 300 × 300 or 970 × 300
- Comparison chart images: 150 × 150
- Three-image layout: 300 × 300 each
- Four-image layout: 220 × 220 each

(Always verify current dimensions in Seller Central — these change occasionally)

## Output Format

```
# A+ Content Plan

## Product: [product name]
## ASIN: [if known]

## Module Layout (5 modules)

### Module 1: [Type]
**Image Brief**: [description]
**Headline**: [text]
**Body Copy**: [text]

### Module 2: [Type]
[repeat structure]

[...modules 3-5]

### Brand Story (Optional)
**Brand Logo**: [specs]
**Background Image**: [brief]
**Cards**: [4 cards with product links]

## Rufus Optimization Notes
[Which questions this A+ Content helps Rufus answer]

## Keyword Note
[Reminder: A+ text is NOT indexed for search. Ensure the standard text
description is also populated with keywords.]
```

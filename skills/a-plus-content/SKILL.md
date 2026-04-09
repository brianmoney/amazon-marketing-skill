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
- Resolve product references by SKU or ASIN using the product context file's
  `SKU:` and `ASIN:` fields
- If multiple product folders exist and the user has not specified a product,
  ask which SKU or ASIN to use before planning A+ Content

## Key Facts About A+ Content

### What It Does
- Replaces the standard text description on the product detail page
- Allows rich media: images, comparison charts, banners, formatted text
- Amazon and third-party data report a **3–20% conversion lift** depending on
  execution quality; Premium A+ can drive up to 20%
- Drives conversion by engaging visual shoppers

### Indexing Reality
- **A+ Content text is NOT indexed for Amazon's traditional keyword search (A9/A10)**
  (per Amazon's official documentation)
- The standard text description IS indexed for Amazon search
- **However**: Rufus DOES read A+ Content text modules. Writing clear, informative
  A+ Content improves Rufus's ability to recommend your product.
- **Google indexes A+ Content**, especially rich media with properly tagged alt-text.
  A+ images and text blocks can appear in Google Shopping, image search, and
  organic results. Always fill in image keyword/alt-text fields.
- **Header and FAQ text** in A+ modules may reinforce keyword strategy even on
  Amazon — embed keyword-rich microcopy in headers and Q&A-style modules
- **Best practice**: Keep a keyword-rich standard text description for Amazon SEO
  AND build A+ Content for conversion and Rufus/Google discoverability. They
  serve different functions.

### Content Quality Analysis (Beta — launched Feb 2026)
Amazon now scores A+ Content pages on an ongoing weekly basis. A+ is no longer
just "published or not" — it is continuously monitored. Scores evaluate:
- Readability
- Information completeness
- Visual presentation
- Conversion effectiveness

Higher quality scores may influence Premium A+ eligibility and algorithmic
favorability. Treat A+ Content as a living asset that should be periodically
reviewed and improved.

### AI-Ready Modules
Amazon Seller Central now offers certain modules with an **"AI Ready" badge**.
These let sellers generate suggested text and image content using AI directly
within the A+ Content Manager. The agent should:
- Inform users this feature exists before manually drafting all copy
- Note that AI suggestions need human review — they can be inconsistent across
  categories and may not reflect brand voice accurately
- Treat Seller Central AI as a draft generator, not a final output

### Module Limits
- **Basic A+**: Amazon officially states 5 modules, though Seller Central often
  allows up to 7. There are **17 module types** to choose from.
- **Premium A+**: Up to 7 modules with access to additional interactive module
  types (video, hotspots, interactive carousels, shoppable comparison charts,
  Q&A). 17+ module types available.
- **Brand Story**: Up to 19–20 modules in the carousel (separate content type)
- Character limits vary from 30 to 6,000 characters depending on module type
- Text embedded in images is NOT readable by Rufus, screen readers, or Google

### Premium A+ Eligibility
Premium A+ Content requires:
- A **published Brand Story** across your catalog ASINs (this is a prerequisite)
- A history of approved A+ Content submissions (typically 5+)
- Brand Registry enrollment

Premium A+ is currently free when eligibility criteria are met. Without an active
Brand Story, you cannot access Premium A+ — plan Brand Story first.

## Available Module Types

### Important Note on Module Names and Dimensions
Amazon Seller Central offers **17 basic module types**. The names and image
dimensions listed below are approximate and based on common usage. **Always
verify the exact module name and pixel requirements in the Seller Central upload
window**, as Amazon updates these periodically without announcement. The list
below covers the most commonly used modules, not all 17.

### Commonly Used Basic A+ Modules

1. **Standard Company Logo**
   - Brand logo image + short description text
   - Good for: Brand introduction at the top of A+ Content

2. **Standard Image & Light/Dark Text Overlay**
   - Full-width image with overlaid headline and body text
   - Good for: Hero banner, brand statement, lifestyle context
   - Headline: ~160 chars; Body: ~300 chars

3. **Standard Single Image & Highlights**
   - Hero image with several text callouts alongside
   - Good for: Product overview or "at a glance" feature summary

4. **Standard Single Image & Sidebar**
   - One main image with text on the side
   - Good for: Feature highlight with supporting visual

5. **Standard Single Image & Specs Detail**
   - Image paired with specification details
   - Good for: Technical products with dimensions/specs

6. **Standard Three Images & Text**
   - Three image blocks with text under each
   - Good for: Showing three use cases or three key features

7. **Standard Four Images & Text**
   - Four image blocks with text under each
   - Good for: "What's in the box" or step-by-step instructions

8. **Standard Comparison Chart**
   - Side-by-side product comparison (up to 5–6 products)
   - Good for: Cross-selling within your product line
   - Do NOT compare against competitors
   - Note: Basic comparison charts are static; Premium A+ offers
     **shoppable comparison charts** with Add to Cart buttons

9. **Standard Single Left/Right Image**
   - Image on one side, text on the other
   - Good for: Feature/benefit callouts

10. **Standard Text**
    - Text-only block (no image)
    - Good for: Brand story or detailed product narrative
    - Important for Rufus: Text modules are the most readable by AI

11. **Standard Multiple Image Module A**
    - One large image + 4 sub-images, each with captions
    - Good for: Showing different aspects, variations, or multi-angle views

### Common Image Dimensions (Approximate — Always Verify in Seller Central)

| Context | Approximate Dimensions |
|---|---|
| Full-width banner | 970 × 600 px |
| Standard image blocks | 300 × 300 px or 970 × 300 px |
| Comparison chart images | 150 × 150 px |
| Three-image layout | 300 × 300 px each |
| Four-image layout | 220 × 220 px each |

⚠️ **These dimensions change without notice.** Always check the upload window
in Seller Central for the exact pixel requirement of the specific module you
selected. Upload at 2× resolution for retina/high-DPI displays when possible.

---

## Brand Story

Brand Story is a **separate A+ content type** managed in the A+ Content Manager.
It appears above standard A+ Content under the heading **"From the brand"** on
every PDP assigned to it. It renders as a horizontal carousel.

### Key Facts
- Brand Story is **shared across all ASINs** under your brand — you create it
  once and assign it to all listings
- It is the **sole "From the brand" content type** as of March 2026
  (Shoppable Collections beta was discontinued on Feb 27, 2026)
- A published Brand Story is a **prerequisite for Premium A+ eligibility**
- You can add **up to 19–20 modules** in a single Brand Story carousel

### Brand Story Components

#### 1. Brand Carousel Background (Required)
The static wide banner image behind the scrollable card modules.

| Field | Spec |
|---|---|
| Desktop background image | 1464 × 625 px (min) |
| Mobile background image | 463 × 625 px (min) |
| Headline (optional) | 30 characters max |
| Body text (optional) | 135 characters max |

**Design guidance for background images:**
- **Desktop**: Keep the right 2/3 plain/clean — carousel cards overlay this area.
  Key visuals can go in the **left third** but avoid text or logos in the image.
- **Mobile**: Cards take up most of the visible area. Use a downward chevron,
  partial image crop, or gradient fade at the bottom to guide shoppers to scroll
  into the card modules.
- Design desktop and mobile images separately — do not simply crop one from
  the other.

#### 2. Card Module Types

| Module | Image Spec | Text Fields | Links |
|---|---|---|---|
| **Brand ASIN & Store Showcase** | 4 ASIN images at 166 × 182 px each (auto-populated from ASIN or override with custom image) | Headline: 30 chars | Links to 4 ASINs + optional Brand Store link |
| **Brand Focus Image** | 1 image at 362 × 453 px (min) | Headline: 30 chars; Body: 135 chars | None |
| **Brand Logo & Description** | 1 logo image at 315 × 145 px | Headline: 30 chars; Body: up to 450 chars | None |
| **Brand Q&A** | None | Up to 3 questions + answers; 600 chars total | None |

**Common mistakes to avoid:**
- Do NOT confuse Brand ASIN & Store Showcase (4-ASIN grid, small images) with
  Brand Focus Image (single large lifestyle image). They are different modules.
- Brand ASIN & Store Showcase does NOT accept a 362 × 453 image — it only
  accepts 166 × 182 per-ASIN images.
- For lifestyle/storytelling cards, use **Brand Focus Image**.
- For cross-sell product grids, use **Brand ASIN & Store Showcase**.
- For brand identity/logo intro, use **Brand Logo & Description**.

### Shoppable Collections (Discontinued)
Shoppable Collections was a beta alternative to Brand Story launched in late 2025.
It replaced Brand Story with interactive product carousels, video modules, and
shoppable cards. **Amazon discontinued the beta on February 27, 2026.** Brand
Story is now the automatic replacement. If you encounter references to Shoppable
Collections online, note that it is no longer available. Images previously uploaded
for Shoppable Collections remain in the media library.

---

## Module Layout Strategy

### Recommended 5-Module Layout for Most Products

**Module 1: Hero Banner (Standard Image & Light/Dark Text Overlay)**
- Full-width lifestyle image showing product in use
- Short headline: Primary value proposition
- Goal: Emotional connection, context setting

**Module 2: Feature Breakdown (Standard Three Images & Text)**
- Three product detail shots, each highlighting one key feature
- Short text under each: Feature → Benefit connection
- Goal: Educate on top 3 differentiators

**Module 3: How It Works / Use Cases (Standard Four Images & Text)**
- Four images showing different use scenarios
- Text: Specific use case description for each
- Goal: Help buyer see the product in their life
- Rufus note: This is high-value for AI discovery — write text that explicitly
  describes WHO uses it, WHEN, and WHY

**Module 4: Product Comparison (Standard Comparison Chart)**
- Compare 3–5 products in YOUR line (not competitors)
- Columns: features, sizes, ideal-for descriptions
- Goal: Guide buyer to right product variant, cross-sell

**Module 5: Specs + Trust (Standard Single Image & Specs OR Standard Text)**
- Option A: Specs image with dimensions, materials
- Option B: Text block with brand story, quality commitment
- Goal: Address final objections, build confidence
- Rufus note: Text blocks with specific materials and care instructions give
  Rufus data for detailed Q&A responses

### Alternative Layouts

**For Technical Products:**
Replace Module 3 with a specs-heavy module. Add a "How to Use" module
with step-by-step images.

**For Multi-Pack or Bundle Products:**
Include a "What's In the Box" module (Standard Four Images) showing each
item separately with individual descriptions.

**For Products with Strong Social Proof:**
Add a module with user-generated style photo + testimonial-style copy
(not actual quotes from reviews — rephrase as benefit statements).

---

## Writing A+ Content Copy

### Principles
- Write for SCANNING, not reading — shoppers scroll fast
- Headlines: 5–8 words maximum, benefit-focused
- Body text: 1–2 sentences per text block
- Use specific numbers and details (not vague claims)
- Avoid all prohibited terms from the style guide
- Write text that describes WHO, WHAT, WHEN, WHERE, WHY — Rufus reads this
- Do not refer to guarantees or warranties
- Do not use opinion statements ("The Best") or unverified claims
- Avoid excessive bold text, all-caps strings, and special characters
- Do not include copyright, trademark, or registered symbols
- Do not mention competitor products

### Image Brief Format

For each image needed, provide a brief the user (or designer) can execute:

```
## Image Brief: [Module Name]

**Dimensions**: [width × height pixels — verify in Seller Central upload window]
**Type**: [Product shot / Lifestyle / Infographic / Flat lay]
**Subject**: [What should be shown]
**Setting/Background**: [Where/what context]
**Key Elements**: [Callout text, badges, or overlays to include]
**Mood**: [Professional / Warm / Active / Clean / Rustic / etc.]
**Do NOT include**: [Competitor products, pricing, promotional text]
**Alt Text / Image Keywords**: [Descriptive text for accessibility + Rufus + Google indexing]
```

Note: Always fill in image keyword/alt-text fields in Seller Central. These
contribute to Amazon image search indexing and Google discoverability.

---

## Output Format

```
# A+ Content Plan

## Product: [product name]
## SKU: [if known]
## ASIN: [if known]

## Module Layout ([N] modules)

### Module 1: [Seller Central Module Type Name]
**Image Brief**: [description]
**Headline**: [text]
**Body Copy**: [text]
**Image Alt Text**: [descriptive text]

### Module 2: [Type]
[repeat structure]

[...remaining modules]

### Brand Story
**Background Image**: [desktop brief + mobile brief — separate images]
**Brand Logo**: [315 × 145 px]
**Cards**:
- Card 1: [Module type] — [purpose]
- Card 2: [Module type] — [purpose]
- [etc.]

## Rufus Optimization Notes
[Which questions this A+ Content helps Rufus answer]

## Google Indexing Notes
[Key alt-text and text modules that support external discoverability]

## Content Quality Checklist
- [ ] All image alt-text/keyword fields filled
- [ ] Text modules describe WHO, WHAT, WHEN, WHERE, WHY
- [ ] No prohibited terms (warranties, guarantees, superlatives, competitor mentions)
- [ ] Mobile preview checked in Seller Central
- [ ] Brand Story published (required for Premium A+ eligibility)

## Keyword Note
[Reminder: A+ text is NOT indexed for Amazon keyword search. Ensure the standard
text description is also populated with keywords. A+ text IS indexed by Google
and read by Rufus.]
```
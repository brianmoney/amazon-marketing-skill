# Amazon Listing Style Guide — Reference Document

> Source authority: Amazon Seller Central product detail page rules, product title
> requirements (effective January 21, 2025), bullet point requirements (effective
> August 15, 2024), and category style guides. Supplemented by verified practitioner
> sources: eComEngine, Parker-Lambert, Amalytix, Keywords.am, ListingForge, Tinuiti.
> Last verified: April 2026.

---

## 1. Product Titles

### Hard Limits
- **Maximum**: 200 characters including spaces (most categories)
- **Category exceptions** (always verify in Seller Central for your category):
  - Electronics: 150 characters
  - Apparel & Fashion: 125 characters
  - Pet Supplies: 80 characters
- **Mobile truncation**: Titles display only ~70-80 characters on mobile devices.
  Over 70% of Amazon traffic is mobile. Front-load critical information.
- **Word repetition**: No word may appear more than twice. Prepositions, articles,
  and conjunctions are exempt.

### Prohibited in Titles
- Special characters: `!  $  ?  _  {  }  ^  ¬  ¦`
  (Exception: allowed if part of the registered brand name)
- Characters with restricted use: `~  #  <  >  *`
  (Only in specific contexts like model numbers "Style #131" or measurements ">3lb")
- ALL CAPS (capitalize first letter of each word instead)
- Promotional language: "Best Seller", "Hot Item", "#1", "Top Rated", "Sale",
  "Free Shipping", "Cheap", "Limited Offer", "Discount"
- Subjective claims: "Amazing", "Perfect", "Best Quality"
- Price or availability information
- Condition information (New, Refurbished, etc.)
- HTML tags or special formatting

### Required Title Structure
Amazon's recommended format (varies by category):
```
Brand Name + Product Type/Line + Key Feature(s) + Material/Key Ingredient + Size/Quantity/Color/Variant
```

### Title Best Practices (Verified)
- Lead with primary keyword within the first 70-80 characters (mobile visibility)
- Include brand name (typically first, but some categories specify differently)
- Use numerals for numbers ("2 Pack" not "Two Pack")
- Spell out measurements where practical ("12 Ounce" or "12 oz" per category guide)
- Use hyphens, commas, or pipes to separate information segments
- Do not end with a period

### Enforcement (As of January 2025)
- Amazon provides override suggestions for non-compliant titles to brand owners
  via "Review Listing Updates" in Seller Central
- Brand owners have 14 days to act before Amazon auto-corrects
- Listings remain active during the correction window
- Non-compliant titles may result in listing suppression from search

---

## 2. Bullet Points (Key Product Features)

### Hard Limits
- **Maximum bullets**: 5 for Sellers, up to 10 for Vendors (category-dependent)
- **Character limit per bullet**: Varies by category and seller type
  - Standard third-party sellers: 200-250 characters recommended
  - Brand Registry sellers: up to 500 characters allowed
  - Vendors: 255 characters
- **Indexing limit**: Only the first **1,000 bytes** across all 5 bullets are
  indexed by Amazon's search algorithm. Keywords beyond that are visible to
  customers but invisible to search.
  - Safe target: 5 bullets × 200 characters = 1,000 characters (within indexing limit)
- Use ALL 5 bullet slots. Empty slots are missed opportunities.

### Required Structure (As of August 2024)
Amazon now requires a specific format:
```
Header: Body text with product details
```
- Start with a concise header phrase (a few words)
- Use a colon `:` as separator between header and body
- No period at the end of the bullet
- No emojis or decorative characters
- No ALL CAPS for the entire bullet (headers may use title case)

### Prohibited in Bullet Points
- Special characters: `™  ®  €  …  †  ‡  ¢  £  ¥  ©  ±  ~  â`
- Emojis (any)
- HTML tags
- ASIN numbers, "N/A", "TBD", "COPY PENDING", or placeholder text
- Company information, website links, URLs, or contact details
- Promotional language: "Best Seller", "Top Quality", "Free Shipping"
- Guarantee/refund language: "Full refund", "Money back guarantee",
  "If not satisfied, send it back", "Unconditional guarantee"
- Price or shipping information
- Competitor brand names or product comparisons (unless verifiable on packaging)
- Subjective/performance claims without verifiable evidence on the packaging:
  - Words flagged by Amazon's automated systems include: "easy", "safe",
    "effective", "best", "amazing", "perfect", "guaranteed"
  - Claims about accolades/awards without source citation and date
  - Consumer survey results without substantiation
- Repetition of information already in the title, description, or other bullets
- Brand origin stories or mission statements (these belong in A+ Content/Brand Story)

### Bullet Point Best Practices (Verified)
- Each bullet should cover ONE unique feature or benefit
- Structure: Benefit statement → supporting feature detail → proof/specifics
- Address different buyer concerns across the 5 bullets:
  1. Primary use case / main benefit
  2. Quality / materials / construction / durability
  3. Ease of use / convenience / compatibility
  4. What's included / specifications / dimensions
  5. Who it's for / ideal use scenarios
- Use natural language — Amazon's AI now rewrites keyword-stuffed bullets
- Include secondary keywords naturally (not forced)
- Front-load the most important bullet (it's most visible on mobile)
- Include specific measurements with a space between digit and unit ("60 ml" not "60ml")

### Enforcement (As of August 2024)
- Amazon uses generative AI to review and rewrite non-compliant bullets
- Amazon may edit or remove bullets WITHOUT seller approval
- AI-generated replacements are shared for review before publishing
- Violations trigger "Product Detail Page Rules Violation" in Account Health
- Repeated violations risk account suspension

---

## 3. Product Description

### Hard Limits
- **Maximum**: 2,000 characters including spaces (plain text)
- **HTML**: Deprecated since July 2021. Plain text only.
  - Exception: `<br/>` for line spacing may still work in some categories
- **A+ Content**: Replaces the standard description for Brand Registered sellers.
  Standard A+ allows up to 5 modules; Premium A+ allows 7.
  A+ Content module character limits vary from 150 to 6,000 characters per module.

### Important: Description vs A+ Content Indexing
- **Standard text descriptions ARE indexed** for Amazon search
- **A+ Content text is NOT indexed** for Amazon search (per Amazon's official statement)
- **Best practice**: Write a keyword-rich standard text description AND build
  A+ Content. The text description feeds the algorithm; A+ Content converts shoppers.
  Amazon reports an average **5.6% sales lift** for listings using A+ Content.

### Prohibited in Descriptions
- Same prohibitions as bullet points (no promotional claims, no contact info, etc.)
- No reviews, quotes, or testimonials
- No spoilers for BMVD products
- No cross-merchandising or cross-promotion

### Description Best Practices
- Do NOT repeat bullet points verbatim — expand on them
- Use for: expanded use cases, product story, materials deep-dive, objection handling
- Keep paragraphs to 2-3 sentences (mobile readability)
- Include secondary and long-tail keywords not covered in title/bullets
- Framework: Problem → Solution (your product) → Specifics → Objection handling → Confidence close

---

## 4. Backend Search Terms (Generic Keywords)

### Hard Limits
- **US/UK/EU**: 249 bytes maximum (NOT characters)
  - Standard ASCII letters/numbers: 1 byte each
  - Accented characters (é, ñ, ü): 2 bytes each
  - Japanese/Chinese characters: 3 bytes each
  - Emojis: 4+ bytes each
- **Japan**: 500 bytes
- **India**: 200 bytes
- **CRITICAL**: Exceeding the byte limit by even 1 byte causes Amazon to silently
  de-index the ENTIRE field. No error message. No warning. All keywords ignored.

### Formatting Rules
- Separate keywords with single spaces only
- Do NOT use commas, semicolons, or other punctuation (wastes bytes)
- Do NOT use quotation marks
- Do NOT repeat words already in your title, bullets, or description
  (Amazon already indexes those — repetition wastes space)
- Stop words ("a", "an", "the", "for", "of", "with") add no indexing value
- Amazon automatically handles singular/plural forms ("shoe" covers "shoes")
- Hyphens: Amazon indexes both hyphenated and non-hyphenated forms, so
  "anti-slip" also covers "anti slip" and "antislip"

### Prohibited in Backend Keywords
- Competitor brand names or trademarks (listing suppression risk)
- Your own brand name (already indexed from title)
- ASINs, UPCs, ISBNs, or other product identifiers
- Profanity or offensive terms
- Subjective claims: "best", "cheapest", "amazing", "top rated"
- Temporary/time-bound claims: "new", "on sale", "limited time"
- Category-unrelated terms

### What TO Include (Verified Best Practices)
- Synonyms and alternative names for your product
- Common misspellings (Amazon's fuzzy match handles many, but niche typos help)
- Spanish translations of key product terms (for US marketplace — many shoppers search in Spanish)
- Long-tail phrases: use-case terms like "gift for dad", "camping gear", "office supplies"
- Regional variations (British/American English: "torch" / "flashlight")
- Abbreviations and acronyms customers might search
- Material/ingredient terms not in visible copy
- Complementary product terms (what it's used with, not competitor products)

### Verification Method
To check if a backend keyword is indexed:
Search Amazon for: `[your ASIN] [keyword]`
If your product appears, the keyword is indexed.

---

## 5. Product Images

### Requirements (Not Covered In-Depth by This Skill, But Relevant)
- Main image: White background (RGB 255/255/255), product fills 85%+ of frame
- Minimum 7 images recommended (maximum 9 in most categories)
- At least 1000px on longest side (1600px+ recommended for zoom)
- Infographic images: Combine product photos with callout text highlighting features
- Lifestyle images: Show product in use, in context
- Image alt text: Indexed by Rufus — include descriptive, keyword-relevant alt text

---

## 6. Category Title Formulas

These vary by category. Always check your specific Category Style Guide in
Seller Central. Common patterns:

**Home & Kitchen:**
`Brand + Product Type + Key Feature + Material + Size/Color`
Example: "FreshSeal Glass Vacuum Storage Container, Airtight BPA-Free Lid, 34 oz, Clear"

**Electronics:**
`Brand + Model + Product Type + Key Feature + Compatibility`
Example: "Anker PowerCore Portable Charger, 10000mAh Power Bank, USB-C, for iPhone and Android"

**Beauty & Personal Care:**
`Brand + Product Line + Product Type + Key Ingredient + Size`
Example: "CeraVe Moisturizing Cream, Hyaluronic Acid and Ceramides, 19 oz"

**Grocery:**
`Brand + Flavor/Variety + Product Type + Size/Count + Dietary Info`
Example: "KIND Bars, Dark Chocolate Nuts & Sea Salt, Gluten Free, 1.4 oz, 12 Count"

**Toys & Games:**
`Brand + Product Name + Feature + Age Range + Piece Count`
Example: "LEGO Creator 3in1 Pirate Ship, Building Set for Kids Ages 9+, 1264 Pieces"

**Apparel:**
`Brand + Gender + Product Type + Feature + Size/Color` (125 char max)
Example: "Nike Men's Air Zoom Running Shoes, Breathable Mesh, Black/White"

---

## 7. Compliance Quick-Check

Before submitting any listing content, verify:

- [ ] Title under character limit for your category (200 max, check category)
- [ ] No prohibited special characters in title
- [ ] No word repeated more than twice in title
- [ ] Brand name present in title
- [ ] All 5 bullet slots used
- [ ] Each bullet has Header: Body structure
- [ ] No emojis, special characters, or ALL CAPS in bullets
- [ ] No promotional, guarantee, or subjective language anywhere
- [ ] No competitor brand names mentioned
- [ ] No pricing, shipping, or availability info in listing copy
- [ ] Backend keywords under 249 bytes
- [ ] No commas in backend keywords (use spaces)
- [ ] No repeated words between backend and visible content
- [ ] Description under 2,000 characters
- [ ] A+ Content present if Brand Registered (5.6% avg sales lift)

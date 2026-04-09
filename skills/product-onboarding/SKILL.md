---
name: product-onboarding
description: >
  Onboard one or more Amazon products into structured product context files.
  Use when the user wants to bootstrap product information from live Amazon
  pages, scrape products listed in asins.csv, create `products/[ASIN]/product-context.md`,
  or fill in missing product context before listing optimization work.
---

# Product Onboarding

Builds structured product context files that downstream Amazon marketing
skills can rely on.

## Goal

For each product the user wants to onboard:

1. Resolve the product detail page URL
2. Gather as much public PDP data as reasonably possible
3. Separate directly observed facts from AI inferences
4. Ask the user only for missing, high-value business context
5. Write or update `products/[ASIN]/product-context.md`

When a product belongs to a variation family, also capture enough structured
family context that downstream listing work can differentiate child ASIN copy
without guessing.

## File Conventions

- Shared brand context lives in `brand-context.md` in the project root or
  `.agents/` directory
- Onboarding queue lives in `asins.csv` in the project root
- Product files live at `products/[ASIN]/product-context.md`

Sellers may refer to products by SKU or ASIN. Keep the canonical folder name as
the ASIN when known, and store the seller-facing identifier in the file's
`SKU:` field so downstream skills can resolve products by either identifier.

If `brand-context.md` does not exist, create it from
`templates/brand-context.template.md` or gather the minimum required fields.

If `products/[ASIN]/product-context.md` does not exist, create it from
`templates/product-context.template.md`.

If the seller provides only a SKU and there is no existing matching product
context file, ask for the ASIN or Amazon URL before creating a new canonical
product file.

## Input Sources

Preferred order:

1. `asins.csv` in the project root
2. ASINs, SKUs, or Amazon URLs the user provides in chat
3. Existing product folders under `products/`

Suggested `asins.csv` columns:

```csv
sku,asin,marketplace,amazon_url,product_label,status,notes
```

Required columns:
- `marketplace`
- At least one of `asin` or `amazon_url`

Optional columns:
- `sku`
- `amazon_url`
- `product_label`
- `status`
- `notes`

Default marketplace to `US` only if the user has not specified another default.

## Tool Selection Order

Attempt live introspection in this order:

1. Playwright MCP tools if available
2. Playwright CLI/browser automation if available
3. Agent default web/fetch tools
4. User-provided pasted content
5. User interview only

Do NOT attempt anti-bot evasion, login-gated access, or anything that requires
customer/account data.

If one method fails, record that failure in the onboarding log and fall back to
the next method.

## What To Extract Automatically

Extract only what is visible with reasonable confidence:

- ASIN
- SKU (if known)
- Marketplace
- Canonical product URL
- Product title
- Brand / storefront name
- Current visible price
- Rating and review count
- Category breadcrumbs
- Bullet points
- Description text
- A+ Content presence and visible text summary
- Parent ASIN if shown
- Variants or pack/size options shown on the PDP
- Product specs / detail table content
- Materials, dimensions, and included items if explicitly shown
- Image/video count and notable themes
- Visible badges (Amazon's Choice, climate badge, coupons, etc.)

If the product appears to be part of a variation family, also capture when
visible or user-confirmed:

- variation family label or theme
- child attributes such as `set_name`, `shape`, `count`, `capacity`, size, or configuration
- which traits appear shared across the family
- which traits appear child-specific

## Provenance Rules

All product context MUST be separated into these sections:

1. `Amazon Observed Data`
Facts directly visible on the PDP or user-pasted listing content.

2. `AI Inferences`
Interpretations based on observed data. These are useful but not fully trusted.

3. `User Confirmed Data`
Business truth provided or approved by the user.

Never place guessed differentiators, keyword targets, or compliance claims into
`Amazon Observed Data`.

## User Interview Rules

After scraping all requested products, ask a consolidated follow-up block rather
than interrupting after every product, unless the user is onboarding only one
product and clearly wants an interactive workflow.

Ask only for missing or low-confidence information, prioritizing:

1. Actual target audience
2. Problem solved
3. Top differentiators
4. Compliance/certification claims
5. Warranty or guarantee details
6. Primary and secondary keywords
7. Converting search terms from ads or prior testing
8. Competitor ASINs or SKUs to benchmark against
9. Claims or phrases to avoid

For variation families, also ask only as needed:

1. Which ASIN is the parent
2. Which children should inherit shared copy vs. receive differentiated copy
3. Which child attributes are confirmed: `set_name`, `shape`, `count`, `capacity`
4. Whether materials, construction, and seal mechanism are identical across all children
5. Any child-specific positioning such as entry set, combo, flagship, travel size

If scraping fails completely, ask the user to paste the current title, bullets,
description, and product specs before asking broader strategic questions.

## Workflow

### Step 1: Load Context

1. Load `brand-context.md` if present
2. Read `asins.csv` if present
3. Determine which products need onboarding
4. Resolve each product by SKU or ASIN, then load any existing `products/[ASIN]/product-context.md`

### Step 2: Scrape or Fetch PDP Data

For each product:

1. Resolve URL from `amazon_url` if provided, otherwise build marketplace PDP URL
2. Attempt Playwright/browser-first capture
3. Fall back to non-browser fetch methods if needed
4. Record the source method and confidence
5. Update `Amazon Observed Data`

If the user provides a SKU without an ASIN, first check whether an existing
product context file already matches that SKU. If yes, reuse it. If no, ask for
the ASIN or Amazon URL before creating a new canonical product file and preserve
the SKU in the context file for future lookup.

### Step 3: Infer Carefully

Based on observed data, generate cautious inferences for:

- apparent target buyer
- apparent use cases
- apparent positioning
- apparent differentiators
- possible shared-vs-unique variation traits

Mark anything uncertain as requiring user confirmation.

Do not infer shape-specific mechanics or child-specific included items unless the
PDP or user confirms them.

### Step 4: Ask Missing Questions

Batch follow-up prompts by product. Use the seller's SKU when available because
it is usually more recognizable than the ASIN. Keep prompts compact and specific.

### Step 5: Write Files

Update:

- `brand-context.md` if new shared brand information was provided
- `products/[ASIN]/product-context.md` for each onboarded product

Preserve prior user-confirmed data unless the user updates it.

If the product belongs to a variation family, preserve structured family fields
and add placeholder listing-draft sections so downstream optimization can write
child-specific bullets, description, and backend terms into the product note.

### Step 6: Mark Completion

If `asins.csv` includes a `status` column, update the row status to something
like `observed`, `needs_user_input`, or `complete`.

## Prompt Fallback

If no browser automation works and default fetch tools are blocked, use this
fallback interview sequence.

### Brand-Wide Questions

- What brand voice should all listings follow?
- Which words, phrases, or claims should always be avoided?
- Which marketplaces matter most right now?
- Are you Brand Registered?

### Per-Product Questions

- In one sentence, what is this product and who is it for?
- What problem does it solve better than competitors?
- What are the top 3 differentiators not obvious from the PDP?
- Which materials, dimensions, or included items should be corrected or expanded?
- Are there certifications, safety claims, or compliance notes we can mention?
- Is there warranty or guarantee language we can use?
- What is the SKU for this product in your catalog?
- What primary and secondary keywords matter most for this product?
- Which search terms or ad keywords have already converted well?
- Which competitor ASINs or SKUs should this product be benchmarked against?

### Additional Variation Questions

- Is this the parent ASIN or a child ASIN?
- What is the parent ASIN for this family?
- What variation attributes should we track for this child: `set_name`, `shape`, `count`, `capacity`, size, configuration?
- Which materials or mechanisms are shared across the family?
- What is unique about this child's natural use case or positioning?

### If The PDP Could Not Be Read

Ask the user to paste:

- Current title
- Bullet points
- Description
- Specs or detail table
- Variant/size information

## Handoff To Other Skills

After onboarding, other Amazon marketing skills should use:

1. `brand-context.md` for shared brand voice and rules
2. `products/[ASIN]/product-context.md` for product-specific data

For variation families, downstream skills should read both the parent context and
all relevant child contexts before reusing inherited copy.

If multiple products are onboarded and the user does not specify one, ask which
SKU or ASIN to use before generating listing content.

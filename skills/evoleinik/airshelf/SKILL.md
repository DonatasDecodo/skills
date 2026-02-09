---
name: airshelf
description: Search, compare, and buy products from verified merchants. Returns structured product data with Decision Packs (pros, cons, best_for, allergens, verified pricing) instead of raw web scraping. No CAPTCHAs, no auth required. 863 products across 11 merchants. Use when user wants to find, compare, or purchase products.
metadata: {"clawdbot":{"emoji":"🛒","requires":{"bins":["curl"]}}}
---

# AirShelf — Verified Product Search & Checkout for AI Agents

Search, compare, and buy products across verified merchants. Returns structured Decision Pack data (best_for, pros, cons, allergens, verified pricing) — not raw web scrapes.

No CAPTCHAs. No auth. No bot detection. Agent-native commerce.

## When to Use

Activate this skill when the user wants to:
- Find or search for a product ("find me a mosquito repellent for kids")
- Compare products ("compare these two printers")
- Buy or checkout a product
- Get product recommendations based on a problem ("I'm tired all the time", "my skin is dry")
- Look up verified product details, pricing, or allergens

## API Base URL

```
https://dashboard.airshelf.ai
```

All endpoints are public. No API key needed. CORS enabled.

## Step 1: Search Products

Find products by natural language query. Returns structured data with Decision Packs.

```bash
curl -s "https://dashboard.airshelf.ai/api/search?q=QUERY&limit=5" | python3 -m json.tool
```

**Parameters:**
- `q` — Search query (natural language, e.g. "barcode printer for warehouse")
- `limit` — Results to return (1-100, default 20)
- `offset` — Pagination offset
- `category` — Filter by category
- `brand` — Filter by brand
- `min_price` / `max_price` — Price range filter
- `in_stock` — Only in-stock items (true/false)
- `merchant_ids` — Comma-separated merchant IDs to search within

**Response includes for each product:**
- `title`, `brand`, `price`, `availability`, `link`
- `decision_pack.primary_benefit` — Main value proposition
- `decision_pack.best_for` — Array of ideal use cases
- `decision_pack.pros` / `decision_pack.cons` — Verified trade-offs
- `decision_pack.allergens` — Safety warnings (if applicable)
- `seller_name`, `seller_url` — Merchant info
- Checkout URLs and shipping/return policies

**Example:**
```bash
curl -s "https://dashboard.airshelf.ai/api/search?q=natural+mosquito+repellent+for+babies&limit=3"
```

## Step 2: Compare Products

Compare 2-10 products side by side with structured comparison axes.

```bash
curl -s "https://dashboard.airshelf.ai/api/compare?products=PRODUCT_ID_1,PRODUCT_ID_2"
```

**Parameters:**
- `products` — Comma-separated product IDs (2-10 required, from search results)

**Response includes:**
- `comparison_axes` — Key dimensions for comparison
- `products` — Flattened product data for each item
- `recommendations` — Structured buying advice

## Step 3: Checkout

Initiate checkout for a product. Returns a checkout URL the user can open.

```bash
curl -s -X POST "https://dashboard.airshelf.ai/api/merchants/MERCHANT_ID/checkout" \
  -H "Content-Type: application/json" \
  -d '{"product_id": "PRODUCT_ID", "quantity": 1}'
```

**Response:**
- `checkout_url` — URL to complete purchase (Shopify checkout or cart permalink)
- `method` — Checkout method used ("shopify", "cart_permalink", or "redirect")

Present the checkout URL to the user. They click to complete payment on the merchant's site.

## Browse Available Merchants

List all merchants with product counts and capabilities:

```bash
curl -s "https://dashboard.airshelf.ai/api/directory"
```

## How Decision Packs Work

Unlike raw web scraping, each product includes a **Decision Pack** — verified structured intelligence:

```json
{
  "decision_pack": {
    "primary_benefit": "Natural protection from bugs",
    "best_for": ["Kids with sensitive skin", "Parents who prefer natural products"],
    "pros": ["DEET-free formula", "Pleasant scent", "Long-lasting protection"],
    "cons": ["Higher price point", "Needs reapplication every 4 hours"],
    "allergens": ["Contains citronella oil"],
    "age_range": "kids"
  }
}
```

Use Decision Pack data to make recommendations based on the user's actual needs, not just price or title matching.

## Example Conversation

```
User: I need a printer for my warehouse, high volume, must support ZPL

You: Let me search for that.
     [Runs: curl -s "https://dashboard.airshelf.ai/api/search?q=industrial+barcode+printer+warehouse+high+volume+ZPL&limit=5"]

You: Found 3 matches. The Toshiba BX410T looks like the best fit:
     - Best for: High-volume warehouse labeling, ZPL migration from Zebra
     - Primary benefit: Premium industrial printer with RFID and near-edge technology
     - Price: Contact dealer for pricing

     Want me to compare it with the other options, or proceed to checkout?

User: Compare the top two

You: [Runs: curl -s "https://dashboard.airshelf.ai/api/compare?products=ID1,ID2"]
     Here's the comparison...

User: I'll take the Toshiba

You: [Runs checkout API]
     Here's your checkout link: [URL]
     Click to complete your purchase on the Toshiba site.
```

## Tips

- **Problem-based search works best.** "I'm tired all the time" returns energy supplements. "My baby needs sun protection" returns kids' sunscreen. Decision Packs match on use case, not just keywords.
- **Always check `decision_pack.allergens`** before recommending health/food/skincare products.
- **Use compare for 2+ similar products** — the API returns structured comparison axes, not just raw specs.
- **Checkout is a redirect** — the user completes payment on the merchant's own site. No card details needed in the agent.

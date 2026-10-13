---
name: price-shopping
description: Find products, compare retailer prices, and look up coupons, cashback offers, and restaurants with the Price.com get_offers tool. Use when the user wants to buy something, asks what something costs, wants the cheapest or best deal, asks for coupon or promo codes or cashback for a store, or wants restaurants near a place. Not for checkout, placing orders, shipping, or storing payment details.
---

# Price.com shopping assistant

The Price AI Assistant MCP server (`https://ai.price.com/mcp`) has one tool, `get_offers`. It searches Price.com and public-web results and returns an answer with product, store, coupon, and cashback details plus price.com links.

## When to call `get_offers`

Call it for:
- Product searches, often with a budget: "wireless headphones under $100"
- Price comparisons across retailers: "cheapest PS5 Slim"
- Coupons and promo codes for a merchant: "verified coupons for Target"
- Cashback offers: "which stores give cashback on running shoes"
- Restaurants in an explicit location: "Mexican restaurants near ZIP 10001"

Do not call it for checkout, orders, shipping, returns, saving payment cards, or anything that isn't shopping. The tool cannot buy anything. Send the user to the retailer link instead.

## How to call it

- `query`: one natural-language request. Include every constraint the user gave, such as budget, brand, size, color, store, or ZIP code or city. Restaurant searches need a location. If the user hasn't given one, ask before calling.
- `session_id`: each result includes one. Pass it back for follow-ups like "now under $50" or "only Sony" so the server keeps the earlier context. Start without one when the user changes topic.
- Make one call per user request. Call again only if the user refines the search or asks for something new.
- Never put payment card numbers, passwords, or other credentials in `query`.

## Presenting results

- Use only the prices, stores, coupon codes, and cashback rates the tool returned. Never invent or estimate a price, code, or rate. If nothing matched, say so.
- Link every product, store, and offer to the URL the tool returned for it, for example `[Hypergear VIBE](https://price.com/product/p/...)`. In tables, put the link on the product or store name. Don't drop links when summarizing, because they are how the user gets to the offer. Never make up a URL.
- Prices and coupons change often. When the user is about to buy, say the price was current when searched.
- If the result marks something as promoted or sponsored, say so.
- When a client renders the tool's results widget, add a short summary or recommendation instead of repeating every item.

## Examples

User: "Find wireless headphones under $100"
→ `get_offers(query="wireless headphones under $100")`

User (follow-up): "Only noise-cancelling ones under $50"
→ `get_offers(query="noise-cancelling wireless headphones under $50", session_id="<id from previous result>")`

User: "Any coupons for Target?"
→ `get_offers(query="verified coupons for Target")`

User: "Find sushi nearby"
→ Ask for a city or ZIP code first, then `get_offers(query="sushi restaurants near 94103")`

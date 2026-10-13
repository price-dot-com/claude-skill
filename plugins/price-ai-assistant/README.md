# Price AI Assistant

![Price.com](assets/icon-512.png)

Price AI Assistant lets Claude shop with Price.com. Ask Claude to find products within a budget, compare prices across retailers, find verified coupon and promo codes for a store, see which stores offer cashback, or find restaurants near a ZIP code or city. You can refine a search in follow-up messages, such as "only under $50" or "just Sony", and open the returned price.com links to continue on the retailer's site.

## Install

In Claude Code:

```
/plugin install price-com --marketplace jainwolverine/priceclaudeskill
```

## What's included

- **MCP connector:** connects Claude to the Price AI Assistant server at `https://ai.price.com/mcp`. It provides one read-only tool, `get_offers`. No account or sign-in is needed.
- **Skill (`price-shopping`):** tells Claude when to use the tool and how to call it. It also tells Claude to reuse the search session for follow-ups, ask for a location before searching restaurants, and never invent prices, coupon codes, or cashback rates.

## Example prompts

- "Find wireless headphones under $100"
- "Now only noise-cancelling ones under $50"
- "Any verified coupons for Target?"
- "Which stores offer cashback on running shoes?"
- "Find Mexican restaurants near ZIP code 10001"

## Data and privacy

The plugin runs no code on your computer. When Claude uses the tool, it sends your shopping request text and a search session ID to `https://ai.price.com/mcp`, which is operated by Price Technologies Inc. It sends nothing else. The server uses public-web results and Price.com data to answer. It keeps follow-up context in memory for up to one hour of inactivity, and it logs queries to operate and improve the service. The tool cannot place orders, check out, or store payment details. Don't include card numbers, passwords, or other personal details in your requests. See the [Price.com privacy policy](https://price.com/privacy) and [terms of service](https://price.com/terms).

## Support

Visit [price.com/support](https://price.com/support).

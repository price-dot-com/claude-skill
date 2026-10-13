# Price.com plugins for Claude

This repository is a Claude plugin marketplace. It holds one plugin, **price-com** (Price.com). The plugin connects Claude to the Price AI Assistant MCP server (`https://ai.price.com/mcp`). It also includes a skill that tells Claude when and how to use it.

With it, Claude can:
- Search products and compare retailer prices
- Find verified coupons and promo codes for a store
- Find stores that offer cashback
- Find restaurants near a ZIP code or city

It returns shopping information and links only. It cannot place orders, check out, or store payment details.

## Install in Claude Code

```
/plugin marketplace add jainwolverine/priceclaudeskill
/plugin install price-com@price-com
```

Or from a shell:

```bash
claude plugin marketplace add jainwolverine/priceclaudeskill
claude plugin install price-com@price-com
```

Then ask something like "Find wireless headphones under $100".

## Use in Claude.ai, Claude Desktop, or mobile

1. Go to **Customize → Connectors → Add custom connector**. Enter `https://ai.price.com/mcp`. No sign-in is needed.
2. Optional: to add the skill, zip the `plugins/price-ai-assistant/skills/price-shopping` folder. Then upload the zip under **Customize → Skills**.

## Contents

```
.claude-plugin/marketplace.json          marketplace catalog
plugins/price-ai-assistant/
  .claude-plugin/plugin.json             plugin manifest
  .mcp.json                              remote MCP server (HTTP)
  skills/price-shopping/SKILL.md         usage instructions for Claude
```

## Support

https://price.com/support · Privacy: https://price.com/privacy · Terms: https://price.com/terms

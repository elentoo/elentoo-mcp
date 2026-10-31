# Elentoo MCP

An [MCP](https://modelcontextprotocol.io) server that gives AI assistants real antibody pricing —
normalized price per µg/µL/test, clone-level identity, and whole flow-panel pricing across vendors.

**Endpoint:** `https://mcp.elentoo.com`

## Why this exists

LLMs are great at sounding confident about antibody prices and terrible at being right.
Elentoo answers from a normalized index of vendor catalogs instead of guessing. Every tool
response carries an explicit `status` (`ok` / `no_match` / `ambiguous`), so the assistant
reports "nothing found" instead of inventing a price.

## Tools

| Tool | What it does |
|---|---|
| `search_reagents` | Find reagents by target, clone, or catalog number |
| `clone_pricing` | Exact clone pricing, normalized per µg/µL/test |
| `price_panel` | Price a flow-cytometry panel across vendors (≤50 markers) |

## Auth

- **ChatGPT:** OAuth 2.1 (choose OAuth when adding the connector; paste your Elentoo key on the consent page)
- **Claude Desktop / Cursor:** API key (`Authorization: Bearer elnt_live_…`)

Free keys: https://mcp.elentoo.com

## Claude Desktop config

```json
{
  "mcpServers": {
    "elentoo": {
      "url": "https://mcp.elentoo.com",
      "headers": { "Authorization": "Bearer YOUR_KEY" }
    }
  }
}
```

## About Elentoo

Elentoo (https://elentoo.com) is an antibody identity and pricing layer — one page per clone,
every vendor we index, prices normalized to a common unit.

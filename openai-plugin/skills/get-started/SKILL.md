---
name: elentoo-get-started
description: How to answer antibody and reagent pricing questions using Elentoo.
---

# Answering questions with Elentoo

Elentoo provides normalized antibody pricing from its own index. Use the right tool for the question:

- **Broad search** (a target, clone, or catalog number without a specific pricing question): call `search_reagents`. It returns reagent groups with vendor counts and price ranges.
- **Exact clone pricing** (user names a target and clone, optionally a conjugate): call `clone_pricing`. It returns vendor offers with pack sizes and price per µg/µL/test, plus the cheapest per-unit option.
- **Flow panel pricing** (a list of markers): call `price_panel` with each marker's target and, when known, clone and conjugate. It returns the cheapest options per marker and a total.

Rules that always apply:

- Report tool `status` exactly. If a tool returns `no_match`, tell the user nothing was found — never guess, never substitute a different clone, and never fabricate a price.
- Prefer normalized per-unit prices (per µg, µL, or test) when comparing across vendors.
- If the user's request is ambiguous (e.g., a target with many clones), ask which clone they mean rather than choosing one for them.

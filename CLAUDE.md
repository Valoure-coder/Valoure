# CLAUDE.md — Valoure Store Project Conventions

This file stores the project conventions and **"always-do" rules** for managing the
Valoure Shopify store with Claude Code. Read this at the start of every session.

---

## 1. About this project

- **Owner:** Valoure (e-commerce store owner, self-described **beginner** — explain steps
  clearly, avoid unexplained jargon, and confirm before anything irreversible).
- **Platform:** Shopify, managed via the **Shopify MCP server** (already installed &
  connected in this environment).
- **Working directory:** `/home/user/Valoure`
- **Git branch for all work:** `claude/shopify-store-setup-e45n2d`
- **Store currency:** EUR (€) — pricing is in euros (e.g. hero product €33.95).

## 2. Core objectives (this engagement)

1. Launch a new product.
2. Set up a tiered product bundle:
   - **1 product** → €33.95
   - **2 products** → 10% off + free shipping + 1 free silk pillowcase
   - **3 products** → 20% off + free shipping + 2 free silk pillowcases
3. Launch a high-performing **listicle** product page.
4. Analyze recent sales data to find highest-performing products.
5. Audit the site's SEO and suggest + implement changes.

## 3. ALWAYS-DO RULES (non-negotiable)

1. **Plan first.** Before ANY mutation (create/update/delete) or file change, write out
   the plan/logic in chat and get sign-off for anything significant.
2. **Safety first — never touch the live theme.** All theme work happens on a **draft /
   unpublished theme**. Never edit, publish, or delete the live (MAIN) theme.
3. **Draft/hidden by default.** New products → status `DRAFT`. New discounts → scheduled
   or scoped so nothing goes live until the owner reviews and explicitly approves.
4. **Log everything.** Every API call (read or write) and every file change gets an entry
   in `progress.md` with a timestamp, acting as an audit log.
5. **Review gate.** Present results and wait for approval before flipping anything from
   draft → active/published.
6. **No destructive actions** without explicit, specific confirmation (no deleting
   products, collections, themes, orders, or customer data).
7. **Read before write.** Use read-only tools (get/search/analytics) to ground every
   change in the store's real current state — never act from memory.

## 4. Store schema / learnings (auto-memory)

> Updated as we learn the store's specific structure. (Populated once Shopify re-auth
> completes and we can read live store data.)

- Shop name / domain: _TBD (pending get-shop-info)_
- Plan: _TBD_
- Currency: EUR (from stated pricing)
- Product catalog: _TBD_
- Collections: _TBD_
- Themes (live vs draft): _TBD_
- Free-gift SKU (silk pillowcase): _TBD_

## 5. How we work (tooling notes)

- Prefer the **built-in Shopify MCP tools** (create-product, create-discount, etc.) for
  common ops — they render review widgets the owner can see.
- Use **graphql_query / graphql_mutation** only when no built-in tool covers the need
  (metafields, pages/blogs for listicles, themes, SEO metafields).
- The GraphQL workflow: `graphql_schema` → build → `validate_graphql_codeblocks` →
  execute. Never guess field names.
- Bundles: Shopify has no native "buy 2 get gift" in the basic discount tool. Implement
  via a bundle app / Shopify Functions / automatic discounts — plan explicitly before building.

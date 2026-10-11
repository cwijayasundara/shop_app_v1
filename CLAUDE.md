# shop-app

sdlc routes all work in this repo: start with /rig:start; use superpowers skills only when an sdlc skill names one.

## What this is
A tiny dependency-free Node.js (ESM) shop: product catalog, carts, orders with discounts, and a transport-agnostic
HTTP-style handler. It exists to exercise the sdlc harness end to end. There is no real HTTP server.

## Map
- `src/catalog/products.js`: `Catalog` class, in-memory products keyed by SKU (`add`, `get`, `list`).
- `src/cart/cart.js`: `Cart` class, SKU to qty map priced from the catalog (`add`, `lines`, `subtotalCents`).
- `src/orders/orders.js`: `checkout(cart, {code})` freezes a cart into an order; at most one discount (SAVE10, SAVE20).
- `src/http/handler.js`: `createHandler(catalog)` returns `handle({method, path, body})` giving `{status, body}`.
  Routes: `GET /products`, `POST /cart`, `POST /checkout`. Thrown errors map to 400, unknown routes to 404.
- `test/shop.test.js`: all tests (`node:test` + `node:assert/strict`).
- `.rig/`: harness state and team guides (`.rig/guides/*.md`); do not hand-edit state.

## Commands
- All tests: `npm test` (runs `node --test`).
- Fast, quiet, one file: `node --test --test-reporter=dot test/shop.test.js`
- Never `node --test test/`: Node 24 loads `test` as a module path and fails with `MODULE_NOT_FOUND`.
- No build, lint or type-check exists. Node v24.1.0, no deps, no install step.

## Conventions
- ESM only (`"type": "module"`), classes with private `#` fields, relative imports with `.js` extension.
- One-line header comment per file; names say what a thing is (`lines()`, `subtotalCents()`).
- Validate at the entry point and throw `Error` naming the offending value (`unknown sku: ${sku}`).
- Catalog returns copies (`{ ...p }`) so callers cannot mutate state.
- Tests: failing test first; `assert.throws(() => ..., /regex/)`, literal expected values, no mocks; test through the
  public handler; name tests with a B-number (`B3 rejects an empty key`).
- Team rules in `.rig/guides/`: one responsibility per module, inject dependencies, no empty catch, no module-level
  mutable singletons, no speculative abstractions.

## Gotchas
- `orders.js:8`: `DISCOUNTS[code]` is a plain object, so `code: "constructor"` yields a function and a NaN discount.
  Use `Object.hasOwn` or a `Map` when touching it.
- `handler.js`: the cart is created once per `createHandler` call, shared by all callers, and `/checkout` does not
  clear it.
- `handler.js`: the catch maps every error, including internal bugs, to 400.
- Node version is not pinned (no `.nvmrc`, no `engines`).

## Never
- Never skip or weaken a test to get green.
- Never rename or remove an API field (`totalCents`, `body.error`) in place: expand, migrate, contract.
- Never commit `.env`.

# Compact instructions
Keep the active sdlc change, failing tests and file paths; drop exploration output.

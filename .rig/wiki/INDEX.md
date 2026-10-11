# Wiki index

Compact map for agents. Treat entries as pointers; verify in the code. Full pages: `.rig/wiki/modules/<name>.md`.

- **cart** — The cart module holds a shopping cart: the quantity chosen for each product SKU, priced against the product catalog · files: cart.js · symbols: Cart
- **orders** — The orders module turns a shopping cart into a checked-out order · files: orders.js · symbols: checkout
- **catalog** — The product catalog: an in-memory store of products keyed by SKU, holding each product's name and price in cents · files: products.js · symbols: Catalog
- **http** — The http module is a transport-agnostic router for the shop · files: handler.js · symbols: createHandler
- **test** — Holds the node:test suite for the shop app · files: shop.test.js

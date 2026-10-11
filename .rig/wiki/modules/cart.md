---
module: cart
files: [src/cart/cart.js]
hash: b58c2a440eb893c8
generated: 2026-10-11
status: fresh
changes: []
---
# cart

## Purpose
<!-- purpose -->
The cart module holds a shopping cart: the quantity chosen for each product SKU, priced against the product catalog. It is used by the HTTP handler to build a cart for a shopper and by the order checkout flow, and it is exercised by the test suite.
<!-- /purpose -->

## Public API
| Symbol | Kind | Signature |
|---|---|---|
| Cart | class | export class Cart |

## Depends on
_none_

## Used by
- [http](http.md)
- [test](test.md)

## How it works
<!-- how -->
Cart is an exported class built with a catalog object, which it stores and uses for lookups. Its quantities live in a private Map keyed by SKU. add(sku, qty) defaults qty to 1; it throws an error when the SKU is not found in the catalog and when qty is not a positive integer, and otherwise adds qty to any quantity already held for that SKU. lines() returns one entry per SKU with its sku, qty and unitCents, where unitCents is read from the catalog at call time. subtotalCents() sums qty multiplied by unitCents across all lines and returns the total in cents. Prices are never stored in the cart, so they always reflect the current catalog.
<!-- /how -->

## Why it is this way
_No rig changes recorded._

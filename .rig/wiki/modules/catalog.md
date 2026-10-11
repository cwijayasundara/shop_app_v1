---
module: catalog
files: [src/catalog/products.js]
hash: 9098477e669d9a10
generated: 2026-10-11
status: fresh
changes: []
---
# catalog

## Purpose
<!-- purpose -->
The product catalog: an in-memory store of products keyed by SKU, holding each product's name and price in cents. The test module uses it to set up products before exercising the cart and checkout.
<!-- /purpose -->

## Public API
| Symbol | Kind | Signature |
|---|---|---|
| Catalog | class | export class Catalog |

## Depends on
_none_

## Used by
- [test](test.md)

## How it works
<!-- how -->
Catalog wraps a private Map (#products) from SKU to product. add({ sku, name, priceCents }) checks that the SKU matches the pattern of three uppercase letters, a hyphen and three digits, and throws an 'invalid sku' error otherwise. It also requires priceCents to be a positive integer and throws if not. Valid products are stored and the stored record is returned. get(sku) returns a shallow copy of the matching product, or null when the SKU is unknown. list() returns copies of all products in insertion order. Returning copies means callers cannot change the stored data through the returned objects. Nothing is persisted; the catalog lives only as long as the instance.
<!-- /how -->

## Why it is this way
_No rig changes recorded._

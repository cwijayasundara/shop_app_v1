---
module: orders
files: [src/orders/orders.js]
hash: 0106cd795f4b8503
generated: 2026-10-11
status: fresh
changes: []
---
# orders

## Purpose
<!-- purpose -->
The orders module turns a shopping cart into a checked-out order. It is used by the http module, which depends on it, and by the test suite.
<!-- /purpose -->

## Public API
| Symbol | Kind | Signature |
|---|---|---|
| checkout | function | export function checkout(cart, { code } = {}) |

## Depends on
_none_

## Used by
- [http](http.md)
- [test](test.md)

## How it works
<!-- how -->
The module exports one function, checkout(cart, { code }). It reads the cart's lines and fails with an error if the cart is empty. It takes the cart subtotal in cents and looks up the discount rate for the optional code in a fixed table: SAVE10 gives 0.1 and SAVE20 gives 0.2. With no code the rate is 0. An unrecognised code throws an error naming the code. The discount is the subtotal times the rate, rounded to whole cents. The result holds the lines, subtotalCents, discountCents and totalCents, where the total is the subtotal minus the discount. At most one discount code applies per order.
<!-- /how -->

## Why it is this way
_No rig changes recorded._

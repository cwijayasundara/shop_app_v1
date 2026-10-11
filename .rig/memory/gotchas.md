# gotchas
> Traps, environment quirks, flaky things

_(fill in: traps and environment quirks as you hit them)_
- orders.js DISCOUNTS[code] on a plain object: code 'constructor' gives a function and NaN discount; use Object.hasOwn or Map [source: init; added: 2026-10-11; id: m-58d956]
- handler.js cart is shared per createHandler call and /checkout does not clear it [source: init; added: 2026-10-11; id: m-b1f1e3]
- handler.js catch maps every error, including internal bugs, to 400 [source: init; added: 2026-10-11; id: m-41a306]
- Never rename or remove API fields (totalCents, body.error) in place; expand, migrate, contract [source: init; added: 2026-10-11; id: m-18fbf9]

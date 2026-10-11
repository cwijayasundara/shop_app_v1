# Memory
Notes from past sessions in this repo. Verify before relying on them.
Search with `/rig-brain:memory-find <terms>` or grep `.rig/memory/`.

## Topics
- [[commands]] (2): Build, test and run invocations that work
- [[conventions]] (3): Repo norms learned from user corrections
- [[gotchas]] (4): Traps, environment quirks, flaky things

## Recent
- Never run node --test test/ on Node 24: MODULE_NOT_FOUND. No build, lint or type-check exists. ([[commands]], m-fb654d)
- Tests: failing test first, B-number names, assert.throws with regex, literal expectations, no mocks, via public handler ([[conventions]], m-bc028d)
- handler.js cart is shared per createHandler call and /checkout does not clear it ([[gotchas]], m-b1f1e3)
- Validate at entry and throw Error naming the offending value; catalog returns copies ([[conventions]], m-abe619)
- ESM, classes with private # fields, relative imports with .js extension, one-line header comment per file ([[conventions]], m-aae27c)
- orders.js DISCOUNTS[code] on a plain object: code 'constructor' gives a function and NaN discount; use Object.hasOwn or Map ([[gotchas]], m-58d956)
- handler.js catch maps every error, including internal bugs, to 400 ([[gotchas]], m-41a306)
- All tests: npm test (node --test); fast quiet: node --test --test-reporter=dot test/shop.test.js ([[commands]], m-1f42be)
- Never rename or remove API fields (totalCents, body.error) in place; expand, migrate, contract ([[gotchas]], m-18fbf9)

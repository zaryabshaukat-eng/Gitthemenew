---
name: Selector helper footgun
description: $ vs $$ query helpers in this theme's main.js
---
`assets/main.js` defines `$` as a single-element `querySelector` and `$$` as a `querySelectorAll` spread into an array. They look nearly identical at a glance, and using `$` where a list is needed (or vice versa) fails silently or throws confusing errors (e.g. `.forEach is not a function`).

**Why:** This caused at least two real bugs in this codebase's session history — once in the homepage recommended-products shuffle logic, and it's a recurring risk anywhere new selector code is added.

**How to apply:** After writing or editing any code that calls `$(...)` or `$$(...)`, re-check whether the result is used as a single element or iterated/mapped — mismatches are easy to introduce and easy to miss in review.

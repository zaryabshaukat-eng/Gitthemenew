---
name: Edit tool silent mismatches
description: Verify Edit tool results by re-reading files with near-duplicate blocks
---
When a Liquid/JS/CSS file has two or more structurally similar blocks (e.g. two nearly-identical marquee rows, two similar card variants), an Edit call whose `old_string` isn't sufficiently unique can either fail with "not found" or, worse, apply to the wrong occurrence.

**Why:** This repo's marquee section (row 1 "Featured Products" vs row 2 "New Arrivals") produced exactly this class of issue mid-session — edits looked successful but needed re-verification.

**How to apply:** After a batch of Edits on a file with repeated similar structure, always re-read the full file (or at least both affected regions) with ReadFile/grep to confirm the change landed in the right place and didn't leave orphaned/duplicated markup.

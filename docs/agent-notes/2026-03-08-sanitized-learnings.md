# Clawberto sanitized learnings — 2026-03-08

This file keeps only operational lessons and reusable workflows.
No secrets, no private keys, no raw credentials.

## 1) Hosted static apps: browser reality beats assumptions

When a hosted static app looks broken, do not stop at:
- asset URLs returning `200`
- headers looking correct
- local logic seeming reasonable

Require an actual browser pass that confirms:
- the terrain/image/map layer is visibly rendered
- the marker appears
- coordinates are populated
- the page opens at a sane viewport/zoom
- interactions still work

### Good pattern
- add a Playwright smoke test
- assert real rendered state, not just fetch success
- schedule the smoke test on an interval
- include a small diagnostics panel in the UI for fast triage

## 2) CORS distinction is critical for hosted overlays

Always separate:
- **server-side reachable APIs**
- **browser-reachable APIs from the final hosted origin**

A route being fetchable from Node or CLI does **not** mean it is usable from GitHub Pages/browser JS.

### Durable rule
If browser CORS blocks the upstream API:
- move that data acquisition into a scheduled runtime/cache refresh script
- publish the resulting JSON with the static site
- let the browser consume local runtime JSON plus any truly browser-safe live feed

This pattern was the correct fix for Bitcraft player-detail fallback behavior.

## 3) Bitcraft-specific useful findings

### Live player feed
- websocket: `wss://live.bitjita.com`
- player channel: `mobile_entity_state:{entityId}`
- live coordinates are scaled by `1000`

### Player detail
- `bitcraftmap.com/api/players/:entityId` exposes useful current-ish fields like `locationX/locationZ`
- but that endpoint should be treated as **server/cache-side**, not guaranteed browser-safe for a hosted static app

### Reliability pattern that worked
- use player-detail `locationX/locationZ` as baseline in the cache refresh script
- upgrade to websocket coordinates when a fresh live event arrives
- refresh GitHub Pages runtime cache on a schedule
- keep a visible source indicator (`live`, `cached`, `detail`, etc.)

## 4) Map UX lesson: stack dots, spread labels only

For clustered player markers, the better model was:
- keep each player dot on the true shared coordinate
- fan out only the labels for readability
- make labels clickable too, not just the dots
- tune label spread based on zoom/group density rather than using one static offset

This preserves truth while keeping the map readable.

## 5) Biggest frontend performance bottleneck was not TypeScript

Measured reality matters.

For the Bitcraft overlay, the main weight was the terrain image asset, not the JavaScript.

### Practical implication
TypeScript is still worth it for:
- safer refactors
- typed state
- schema-validated payloads
- fewer silent bugs

But actual speed gains come more from:
- asset optimization
- caching strategy
- cleaner data flow
- less over-fetching

## 6) High-ROI modernization path

When a small working frontend needs to become more robust, prefer:
- `Vite`
- `TypeScript`
- `Zod`
- `Playwright`
- keep the existing fit-for-purpose map library if it is already well matched to the problem

Avoid wasteful framework churn just because it feels modern.

## 7) OpenClaw working pattern that proved useful

Best workflow for non-trivial refactors:
- keep the chat responsive in the main session
- run the coding work in an isolated worktree/background session
- give short milestone updates only when something actually changes
- keep the live repo safe until validation passes

This lets the assistant keep talking while work continues.

## 8) Kittenswap heartbeat output should be operator-dense

A useful heartbeat is not just:
- decision
- hold/rebalance

It should also include the LP/farm facts needed to decide whether the agent is healthy:
- pair / pool
- liquidity
- principal composition now
- stable value now
- claimable fees now
- emissions active or not
- uncollected rewards
- reward/day and value/day
- APR estimate
- runway

If the operator has to run three more commands after reading the heartbeat, the heartbeat is too thin.

## 9) Debugging rule: distinguish script bugs from intentional SIGTERM noise

When lots of short-lived tool runs happen, some host-level exec sessions may end with `SIGTERM` even though the underlying diagnostic goal already succeeded.

Do not overreact to the transport/session noise.
Check:
- whether the useful output already landed
- whether the final command semantics actually failed
- whether the next run confirms the same conclusion

## 10) Memory hygiene

Useful to persist:
- patterns
- workflows
- architecture choices
- debugging lessons
- anti-drift checks

Do **not** persist:
- private keys
- API secrets
- raw personal data
- anything that would be dangerous if the repo leaked

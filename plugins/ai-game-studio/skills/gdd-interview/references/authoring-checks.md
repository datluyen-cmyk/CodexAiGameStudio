# Completeness checks for game design authoring

Use these as diagnostic lenses, not a questionnaire to read aloud. Select meaningful checks for the supplied game and agreed scope. Missing inapplicable features are not gaps and do not justify expanding the design.

## Source and scope coverage

- Have all supplied design-bearing sections, relevant notes/legends, images, and requirements been accounted for? Was unavailable content reported accurately?
- Are author intent, human-approved changes, simulated team suggestions, and imported implementation shortcuts kept distinct?
- Are prototype vs product scope, exact vs illustrative content, and original vs newly proposed level layouts explicit?
- Does the document preserve tone, fantasy, game feel, style, and excluded content as well as numerical rules?
- Are out-of-scope items human-decided rather than silently dropped? Do unapproved references remain reference-only?
- Is the destination for the GDD package known? For a direct-build handoff, is the destination for the game project and playable build/export known separately? If not, ask the user or queue a builder-facing question before creating files; do not put generated files in an unrelated directory.
- Do the supplied materials point to a recognizable existing game? If so, has the user confirmed whether this should be a faithful clone, a selected-mechanic adaptation/inspiration, or an original design with genre conventions? Record which mechanics/visual traits to preserve and which to change; do not infer intent from resemblance alone.
- Is there a gameplay/motion reference for every core interaction cluster where feel is important? A still may support layout/style, but not a motion sequence. Ask for specific missing clips/screens or record an accepted textual target.

## Mechanics and state

For each core interaction, inspect relevant dimensions:

| Dimension | What must be understandable without guessing |
|---|---|
| Objects and state | What each entity is; ownership, position, eligibility, counts, bounds, units, initial state. |
| Input and selection | Tap/click/hold target, exposed vs hidden content, selection membership/order, validation and feedback. |
| Resolution | Ordered events, when resources/occupancy change, destination/priority, simultaneous cases if meaningful. |
| Feedback | What moves from where to where, visual state changes, progress/counters, sound/haptics if in scope. |
| Interruption | Relevant repeated inputs, cancellation, pause/reset, in-flight interactions, and how the user recovers. |
| Outcomes | Exact success/failure triggers, when they are evaluated, rescue/retry effects, resources preserved or lost. |
| Interactions | Effect on other mechanics, layers, locks, boosters, economy, progression, and tutorials. |
| Proof by example | One concrete ordinary case and the meaningful boundary/failure cases, with consistent quantities. |

Use a state table or diagram where prose permits conflicting event orders. Avoid turning low-level race-condition handling into GDD code architecture; state the required player-visible semantics.

For applicable spatial/moving mechanics, apply the spatial/temporal contract in `output-contract.md`. Can two builders still disagree about fixed versus any-free entry, travel direction and end-of-route behavior, first obstruction, front/hidden eligibility, group ordering/partial capacity, or rejection versus remembered waiting input? Check the occupied-entry case even when spare capacity exists elsewhere. Check pending actions against merge/reorder/removal and recovery when those interactions exist. Find the supported rule or ask about the exact unresolved fork; do not import the last project's rules as defaults.

## Level and case coverage

For a direct-build handoff or a requested prototype/test slice, maintain a coverage matrix with at least these columns: requirement/mechanic ID; scope disposition; level or scenario ID; actual starting setup and triggering input; expected state/result; acceptance check; and uncovered dependency. A compact table is enough; it must let a reader see which level proves each mechanic.

- Inventory every mechanic and meaningful content feature found in the sources, including layers, tray variants, route/teleport elements, boosters, rescue flows, and progression. Mark each in-scope, out-of-scope by human decision, deferred, or unresolved. Do not infer scope from a heading in a template.
- A level is evidence only when its layout and initial state actually exercise the listed mechanic. For example, a level with every cube exposed on one layer does not test layer reveal; several rectangular loops do not test branch/teleporter behavior unless the specified route rules activate it.
- For each in-scope mechanic, include the ordinary case and relevant edge/failure/recovery and cross-mechanic cases. Where a full authored level would be disproportionate, use a named deterministic test scenario only if the user accepts that form of coverage and its setup/result are fully specified.
- Reconcile the requested number of levels with the feature inventory. Call a small set a core-loop vertical slice when it does not cover all mechanics. If requested scope implies broader coverage, ask whether to add levels/scenarios or explicitly defer uncovered features; do not quietly expand or narrow the scope.
- Report the coverage status separately from design readiness: “playable vertical slice” does not mean “all mechanics tested.” Uncovered tests must remain visible in the GDD and handoff DoD.

For stateful mechanics, also check the lifecycle contract when relevant:

- Separate authored level/configuration data from per-run or per-instance runtime state and short-lived interaction/transition context when they have different lifetimes.
- Define which actor or entity owns the state, how repeated instances are distinguished, what successful event commits a change, and what blocked/cancelled actions leave unchanged.
- State what reset, retry, undo, level reload, or persistence restores when those behaviors are in scope. Do not assume that runtime changes should be written back into authored level data.
- For malformed authored data that changes gameplay (for example, missing/duplicate identities or impossible placements), ask or specify whether the level is rejected, skipped, or repaired. Do not silently invent auto-repair behavior.

Keep this as a design/data contract. Do not prescribe classes, APIs, or code architecture unless the user explicitly requests a technical design.

## UI, visuals, animation, and audio

- Define screens/HUD and states, portrait/landscape framing, camera and visual dimensionality, layer hierarchy, input targets, and essential information readability.
- Give important references a role and scope. Inspect them; distinguish layout reference, mood board, final asset, and optional inspiration. Do not imply a reference asset is supplied or approved for reuse.
- For each core loop cluster, actively request a specific gameplay reference when available: (1) the normal input-to-result loop, (2) object movement/transfer and destination response, (3) completion/reveal, and (4) a materially different failure/revive/recovery path when in scope. Ask for a clip/GIF/screen recording or a link and identify the exact action to capture; do not send a vague request for “more references.” If the user names a game or asks for research, find publicly accessible footage/reference material and inspect the relevant sequence instead of relying on search snippets. Do not select arbitrary games as the target or use footage as permission to extract assets. One clip may cover multiple clusters only if it visibly shows them. If no useful clip is available, ask whether to find public examples or use an explicit textual target; label that target as textual, not video-validated.
- For every reference used, record the game/source, URL or local filename, inspected timestamp/frame range, the exact gameplay or animation properties it governs, and what remains unknown. Separate observation from desired imitation. A reference to a known game does not by itself authorize a clone; apply the explicit clone/adaptation/original question under Source and scope coverage.
- Replace "match the reference" with observable traits that must match: silhouette, grid density, object proportions, palette/material, perspective, composition, contrast, border/shadow treatment. Do not invent precise measurements from an inaccessible image.
- For every core gameplay action, describe the animation as a readable event sequence, not a generic polish note: trigger and initial pose; anticipation/selection response; which object moves; visible path and direction; one-by-one vs together and spacing/overlap; arrival/contact; destination reaction; settle/completion; when counters and gameplay state change; and relevant interruption/invalid-input behavior. Give an approximate duration or adjustable range for each important phase, with proposal status if not source-backed. Use visual examples or written targets for silhouette, height, arc/straight path, easing character, squash/settle, shadow and relative scale when they define the intended feel; these remain design-level observations, not engine curves or code instructions.
- Audit every visible transition that exists in the requested scope, including selection/invalid input, source-to-belt transfer, belt travel, receiver acceptance/rejection, tray completion/reveal, win/fail/revive, popup states, and booster/element feedback if included. Do not combine distinct transitions in a vague “polish” entry. Do not add missing systems just to satisfy this list. If no motion reference exists, specify an actionable textual target or ask about the semantic/feel choice that could materially change the game; do not infer motion from a static screenshot.
- Distinguish design-critical motion from adjustable polish. Resolve critical motion during authoring. Human-approved prototype timings remain tunable targets, not verified feel.
- For audio, inventory the actual supplied files; source names in a spreadsheet do not prove that clips exist. Map every in-scope audio event to a cue and describe its trigger, intent/relative prominence, duration/repetition/overlap priorities when relevant, and mute behavior. When source audio is absent, state the authorized fallback (generate, synthesize, or search for suitable assets), require local project copies and a provenance/license/attribution manifest for found audio, and provide a replaceable synthesized placeholder if rights cannot be verified. Distinguish supplied audio, required new asset, generated/sourced placeholder, and optional inspiration. Never use ripped or unlicensed commercial-game audio. Music and haptics are not mandatory features.
- Asset requirements should name the object and required states/variants, dimensions or scale, format/transparency/rig/pivot constraints when supplied, and missing/provided status. Do not choose a pipeline as a substitute for defining appearance.

## Dev and content constraints

- Preserve specified platforms, aspect ratios, input methods, performance targets with measurement context, offline/online behavior, save/progress semantics, and mandatory engine/content constraints.
- Avoid inventing 60 FPS, Unity, monetization SDKs, cloud storage, telemetry, or a backend because they are common.
- For a direct AI-build target, resolve the product constraints that materially affect the result: target experience/platform when specified, orientation and input, required online or persistence behavior, and any stated device/performance promise. Do not turn browser versions, device minimums, FPS, memory budgets, framework/runtime, libraries, data serialization, code structure, or routine tooling into interview questions unless the source or product promise makes one material. Delegate normal technical baselines to the coding agent; it should inspect the repository and choose the simplest compatible setup, recording the choice in the implementation README rather than expanding the GDD. Ask only when a technical choice changes game behavior/feel, content/art scope, distribution, cost, external service, or a stated product promise.
- Include minimum content and authentic example data required by the agreed scope. An exact runnable level needs placements, colors, quotas, capacities, layers/locks, and objective state, not just counts in a level summary. If these are absent, ask to obtain the layout or to author a clearly new example.
- For level/content data, name the required fields, stable IDs, valid ranges/relationships, initial state, and meaningful invalid-data behavior. Provide at least one complete sample record or level that conforms to the contract. Do not invent a serialization format unless it is supplied, required, or delegated.
- Make economy effects, limits, prices, unlocks, resource sources/sinks, and time rules explicit only where those systems are in scope.
- For AI-generated assets, identify which assets are supplied references, must be generated, can use placeholders, or are out of scope. Specify observable style traits and required states/variants; include usable dimensions, format, transparency, rig/pivot, or animation constraints when supplied or approved. A reference-only image is not automatically a production asset.

## Genre prompts: choose only relevant ones

- **Puzzle/casual:** valid selection/adjacency, spatial exposure/layers, overflow, transfer order, route/direction/station matching, competing destinations, match quota, unsatisfied objects, deadlock/failure timing, rescue/retry, tutorial and exact level data.
- **Action/platformer:** movement/jump/aim behavior, collision and damage outcomes, hit/invulnerability windows where meaningful, checkpoints, camera and controls, enemy behavior and telegraphs, failure/recovery.
- **Strategy/simulation:** tick/time model, production/consumption, placement/adjacency, competing actions, worker/entity rules, queue/capacity, state persistence and win/loss.
- **RPG/progression:** stat effects, progression gates, inventory/equipment, combat or interaction loop, rewards, content availability, narrative consequences where requested.
- **Multiplayer:** authority-relevant player outcomes, join/leave/disconnect and shared progress, interaction conflicts, session scope and accepted latency behavior. Do not add multiplayer to a single-player design.

## Final review: design, Dev, Art

When motion evidence was absent, confirm the draft-time interview actually resolved the material movement/feel forks or obtained explicit delegation. Is every applicable interaction's origin/destination, path/direction, continuous/stepped and group ordering, state/counter commit, visible/audio feedback and blocked/interrupted behavior concrete? An unresolved core fork cannot be waved through as “the coding AI will decide”; later questioning requires deliberate human deferral with named dependencies. Missing video alone does not fail this check if an explicit textual target is supported by the human's answers/delegation. Do not require redundant approval of already established rules or exact engineering parameters.

Review the actual generated document and referenced files, not just the template headings:

1. **Design:** run the two-implementer check on core behaviors and boundary examples. Are equivalent terms used consistently? Could either implementer obey the text but build a different game?
2. **Dev:** walk the state transitions and sample data. Do conditions, capacity/resource arithmetic, event timing, and mandatory constraints agree? Are required content and cases present?
3. **Art/audio:** could an artist identify the targets, variants, states, reference priority, event sequence, and asset requirements? Does the prose preserve visible source traits without inventing approvals?
4. **Source reconciliation:** for every input requirement, confirm incorporated, human-superseded, or human-deferred status with a destination. Check qualitative design intent too.
5. **Delivery:** inspect links and media references, verify local files exist, distinguish supplied/final/placeholder/missing assets, and ensure readers do not need hidden chat context to understand the rules.
6. **Build handoff:** confirm the destination of the GDD package and the game/build export are recorded separately; confirm any recognizable-game similarity was explicitly characterized and user intent is recorded; confirm core gameplay/motion reference coverage is listed by event with inspected timestamps or an accepted textual target. Any missing destination, clone intent, or material motion reference must be a specific question, not an unstated assumption.
7. **Studio integration, when selected:** confirm derived implementation records preserve canonical requirement IDs, current decisions, exact content count and all in-scope asset/event families. Keep implementation progress and runtime/visual verification separate from document readiness. A planned one-level milestone or successful mock does not certify a complete multi-level game.

Return material findings to the drafting/interview loop. Do not mark unknowns resolved by adding an ASSUMPTION label. Do not require real game implementation to complete a document-authoring request. User review validates documented intent; only later playtesting can validate enjoyment and final feel.

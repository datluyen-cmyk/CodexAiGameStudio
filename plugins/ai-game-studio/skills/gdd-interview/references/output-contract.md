# Output contract

The default deliverable is a standalone `GDD.md` plus two compact companions for decisions and provenance. Honor requested filenames and existing equivalents. Use the user's document language; retain stable IDs across revisions. Companion filenames in examples below are conventions, not mandatory replacements for existing project files.

## GDD.md

Use YAML frontmatter with `title`, `status`, `updated`, and `scope`. Status is `drafting`, `ready-for-review`, or `approved`. Add a revision identifier when useful for human review. `scope` identifies the agreed handoff (full design, feature, or prototype profile); do not infer a reduced scope from missing details.

Organize for reading, using these sections where relevant and adapting to the game:

1. Vision, target players, platform, experience goals, and scope.
2. Terminology, object roles, player inputs, and initial conditions.
3. Core loop and exact win/loss/retry conditions.
4. Mechanics and system interactions, with stable requirement IDs.
5. Progression/economy/content and level specification appropriate to scope.
6. UI/HUD, screen flows, feedback, and relevant interrupted/error states.
7. Art direction, inspected visual references and their roles, asset/state requirements.
8. Animation/VFX/audio event specifications, linked to the mechanics they express.
9. Binding Dev constraints and data/content requirements.
10. Concrete scenarios and acceptance criteria for the defined behavior.
11. AI build handoff with implementation slices and validation, when the document is intended for direct AI-assisted creation.
12. Explicit scope exclusions, delegated prototype defaults, unresolved or deferred decisions, and companion links when needed.

Do not emit empty template headings, unspecified marketing prose, or code architecture sections solely to fill a template. If a requested system is missing information, retain its drafting section and named blockers rather than omitting it.

### Mechanic detail block

Give important mechanics a stable ID such as `M-001` and a clear title. The block should answer the relevant questions below; use prose or tables instead of mechanically repeating labels for trivial interactions.

| Field | Required meaning |
|---|---|
| Purpose | Player action/decision and intended experience. |
| Objects | Actor/target roles, meaningful states, counts, units, bounds, eligibility. |
| Trigger/conditions | Valid input and prerequisites; visible response to invalid input when relevant. |
| Selection/resolution | Exactly what is affected, ordering/priority, resource effects, interactions. |
| Event sequence | Ordered start, travel/transition, arrival, counters/state updates, completion. |
| Presentation | Observable UI/art/motion/audio targets and pointers to detailed event/asset entries. For core actions, the GDD describes each visible animation phase, path/direction, staging/overlap, impact/settle feedback, approximate tunable timing, and synchronization with gameplay state. |
| Boundaries/recovery | Material capacity/empty/locked/repeated-input/interruption/failure cases. |
| Tunable parameters | Values, units/ranges, and whether sourced, explicitly approved, or delegated prototype defaults. |
| Example/acceptance | A concrete starting state and input with an observable, arithmetically consistent result. |

For acceptance, use Given/When/Then or an equally precise state/input/result table. A statement that code compiles or a feature exists is not proof that a design interaction matches.

### Spatial and temporal contract

Use these fields for the mechanics where location, movement or concurrent actions affect play. Keep them in the relevant mechanic/event description instead of maintaining a conflicting duplicate rule table. Mark inapplicable fields as such only when useful; do not introduce movement, queues or shooting into games that lack them.

- **Origin and destination:** eligible source and receiver states; fixed entry/exit anchors or the exact selection rule for variable destinations. Define positions in game/reference terms so they survive responsive layouts. Do not leave “move onto the path” ambiguous between a fixed start and any vacant position.
- **Route and end condition:** direction, path topology, corners/stops/branches where relevant, what occurs during travel versus at a stop, and the exact condition for completion, recirculation, return or removal. A lap ends relative to a defined start; do not substitute “some time later.”
- **Visibility/obstruction:** which occupied object is encountered first along an interaction ray or access path, whether incompatible objects block, and whether hidden/rear objects are selectable. An incompatible first object and an empty path are different cases.
- **Capacity and occupancy:** what consumes capacity, when it is reserved/released, whether an in-flight object still occupies origin/destination, and what happens when capacity exists elsewhere but the required entry/receiver is occupied.
- **Groups and order:** member eligibility, assignment/ordering, whether selection/transfer/reservation is atomic or partial, and the independent/linked state after arrival or return. Do not infer group overflow policy from a single-object case.
- **Pending actions and interference:** whether a blocked tap is rejected, remembered or requires another tap; where a waiting object stays; repeated-input behavior; effects of another launch, merge, target removal or reorder; and cancellation/reset/recovery semantics where relevant. Ask about material design differences, leaving ordinary engineering mechanisms delegated.
- **Timing and commits:** input accepted, reservation, source exit, travel, arrival, effect/resource commit and completion. Identify what may overlap and what is synchronized. Adjustable speed/timing must preserve the documented semantic order. Describe the player-visible requirement; engine state and interpolation architecture belong to the builder.

Include concrete examples that distinguish the plausible implementations: normal empty entry, occupied entry with spare capacity elsewhere, obstruction, group partial capacity, repeated input during travel, route completion, and interruption/recovery as applicable. Use the actual game's decided outcomes; examples are not permission to invent them. Human-specified entry corners, capacities, merge rules and obstruction policies remain scoped to that game.

### AI build handoff

Include this for a GDD intended to be handed directly to an AI coding agent. Keep concept-only GDDs lighter when the user requests that scope. The handoff should let the coding agent begin repository discovery and implementation without inventing gameplay rules, assets, or content. It is a design/build contract, not a guessed code architecture. Include:

- **Builder instructions:** treat the GDD and linked decision/source records as the design authority; follow the recorded source/decision/proposal status; inspect the actual repository or create the explicitly scoped new-project baseline; implement the slices in order; stop and ask about material blockers instead of inventing behavior; report the build and validation evidence requested by the user.
- **Integrated Studio handoff, when used:** name the canonical design/decision paths and revision; preserve their IDs in derived Studio records; carry the exact requested content and presentation scope into the build. Require a coverage record connecting requirements/events/content/assets to actual implementation and evidence. Static checks, mocks, real runtime interaction, visual/motion comparison and human feel feedback are distinct evidence; a mock render cannot certify browser correctness or visual fidelity. No Studio prototype default may silently reduce the human's requested game scope.
- **Build envelope:** the player-facing target, platform when known, orientation and input, and any required persistence/network or performance promise. Mark human-confirmed, source-derived, delegated, and unresolved product values distinctly. The coding agent owns routine engineering baselines, including framework/runtime/library versions, code structure, serialization, browser/device minimums, and reasonable performance budgets: inspect the repository and follow its stack, or choose the simplest compatible local setup for a new prototype. Put implementation choices in the coding README or build notes, not in the GDD unless they affect a product promise. Ask the user only when a technical choice changes gameplay/feel, content/art scope, distribution, cost, external services, or another material product decision.
- **Output destinations:** state the supplied repository/workspace root, where the playable project should be created, and where the runnable build/export should go. These are separate from the destination of the GDD package. Reuse a path the user already specified. If a required destination is unknown, include a concrete coding-session question and instruct the agent to ask before creating files outside the provided repository/workspace; never invent a drive or directory.
- **Originality/reference intent:** when materials plausibly identify a known game, state the evidence and the user's confirmed intent (faithful clone, selected-mechanic adaptation/inspiration, or original game with genre conventions), plus traits to reproduce and traits to change. If unconfirmed, add a blocker question; resemblance is not approval. Keep reference use separate from asset reuse and do not claim legal clearance.
- **Runnable content:** at least one complete example level or equivalent content unit, its objective and solution path, plus the data fields, IDs, constraints, and relationships needed to author more content.
- **Coverage matrix:** map every in-scope feature/mechanic to an actual level or named scenario, exact setup/input, expected outcome, and acceptance check. Mark source features that are omitted/deferred and state their consequence. A small vertical slice must be labeled as such if it does not exercise every mechanic; do not claim a few levels provide comprehensive coverage without this matrix.
- **Asset handoff:** inventory supplied/reference/generated/placeholder assets; required visual states and variants; concrete style traits; usable format, dimensions, transparency, rig/pivot, and animation requirements when known. For every in-scope player-facing transition, include a complete observable animation sequence: trigger, initial state, motion path, order/overlap, arrival/impact and settle response, approximate adjustable timing, and state/counter synchronization, using inspected references or concrete textual targets. “Add polish” or “make it satisfying” is not an animation specification. For audio, map cues to events; if originals are absent, state whether the builder may generate, synthesize, or source replacements, and require local assets with provenance/license/attribution recorded. Link real references and say what each reference governs.
- **Gameplay/motion reference map:** for each core interaction cluster (at minimum the normal gameplay loop and materially different completion/reveal and failure/recovery paths when in scope), record a real inspected gameplay/motion reference with a timestamp/frame range or an accepted textual target when no reference exists. State exactly which input, gameplay sequence, motion path, timing/spacing, impact/settle, and destination response the reference supports and what it does not show. Ask the user for missing specific clips during authoring when likely available; do not count unrelated art inspiration or static screenshots as animation evidence.
- **Implementation slices:** small, ordered, independently reviewable behavior increments. For each, state the player/system outcome, prerequisite requirement IDs, included behavior, non-goals, relevant data/assets, acceptance cases, and a future validation method.
- **Definition of done:** observable gameplay, UI, asset, and content checks for the requested handoff. Separate checks that can be automated from manual playtest checks for feel and presentation. Include a scope-coverage check: every in-scope mechanic has a scenario and acceptance result, and uncovered or deferred mechanics are named rather than implied to be tested.
- **Vibecoding question queue, when requested:** list only decisions deliberately left for the coding session, each with a stable ID, exact unknown, why it affects player-visible behavior/content/assets, concrete options or recommendation, dependent requirement/scenario IDs, and what can proceed independently. Include the game-project/build destination if not specified, clone/adaptation/original intent if resemblance to a known game is material and unconfirmed, and specific missing gameplay/motion references when the user may provide them. Instruct the coding agent to inspect the project and supplied assets first, ask only the next 1–3 material questions, and pause implementation of dependent behavior until answered. It must not silently apply a recommendation. This queue supplements a detailed GDD; it does not replace gameplay rules with “ask the user” placeholders.

Keep each slice to one primary objective. The first coding-agent step is to inspect the supplied project or establish the delegated new-project baseline, then map GDD requirements to the actual repository. Do not invent repository file lists, class names, APIs, or engine architecture from the GDD alone; a development agent should inspect the actual project before proposing those. List unresolved decisions as build blockers, deliberately queued vibecoding questions, or explicitly delegated defaults; do not bury them in a generic assumptions section. A queued question is not a license to omit the surrounding specification: state all known behavior and isolate the exact fork. The coding agent may proceed with independent work while waiting, but must not implement dependent behavior by guessing.

### Presentation tables

Link these to mechanic IDs so logic and presentation cannot drift independently:

- **Event:** event ID, trigger, start object/state, visible sequence/path, end object/state, duration/range or accepted reference, counter/state synchronization, audio/VFX cue, interruption behavior if relevant.
- **Reference:** reference ID, actual local file/URL and inspected locator, governs which traits/screen/state, required preserved traits, status and limits (for example, static screenshot does not define motion).
- **Asset:** asset ID, object/use, required states/variants, inspected reference IDs, mandatory dimensions/format/scale/pivot/rig constraints supplied or approved, and supplied/required/provisional status.

Do not fill numeric fields with guessed values. Supply an authorized range/default, use an explicit accepted reference when sufficient, or retain the specific decision as unresolved while drafting. A source-backed sample value applies only to the sample's scope.

### Writing standards

- Write direct design rules in the main document. Keep source locators and dispute history mostly in `SOURCE_MAP.md`; use a nearby reference only where it helps explain the actual design.
- A reader should not need the chat history or original Excel to learn a core rule.
- Do not write "as described in the source" in place of the description. Do not turn every paragraph into an uncertainty disclaimer. Keep uncertainties at the actual unresolved requirements and in the decision record.
- Clear approval/delegation labels belong next to exceptional defaults. A requirement being in the original draft is evidence of source intent, not proof of final approval by every stakeholder.
- Local assets use relative Markdown links or image embeds. Preserve source filenames or provide a mapping. Package inspected copies only where needed for the requested handoff; distinguish references from runtime game assets. External and inaccessible references stay explicitly external/inaccessible.
- Detailed Art/Dev appendices can be separate for large projects if the GDD links them and clearly identifies the canonical rule. Do not maintain conflicting duplicate rule tables across files.

## DESIGN_DECISIONS.md

Keep settled decisions and pending questions in a single compact record. Reuse an existing decision log if present.

Suggested columns: ID, topic/scope, status, source/evidence or human answer, adopted rule, affected requirement IDs, and next dependency/revisit condition when applicable.

Use statuses such as `answered`, `delegated-default`, `proposed`, `unanswered`, `deferred`, and `superseded`. Do not equate a recommended answer with `answered`. Preserve materially rejected alternatives where they prevent repeated questioning. Mark the current drafting position and pending prerequisite for resume when a session stops mid-interview.

Explicitly distinguish a human-approved provisional rule from a fully specified production value. Example: a user may authorize editable animation timings for a prototype while retaining the semantic arrival-before-progress rule as fixed. Both belong in the record with their different scopes.

## SOURCE_MAP.md

Inventory input sources first: source ID, filename/URL, source type, revision/date if known, actual access/coverage, and status (original design, approved revision, Dev constraint, Art direction, simulated/proposed, visual reference).

Then map material source requirements to the GDD: source ID + precise locator, short requirement summary, GDD requirement/section ID, disposition, and decision ID for conflicts or changes. Dispositions include incorporated, superseded-by-human-decision, deferred-by-human-decision, and unresolved. Do not drop qualitative requirements just because they lack numbers.

For workbook extraction, include relevant sheet and cell/range; for images, include extracted filename plus sheet/anchor where available. A referenced link that was not retrieved must not be listed as inspected. When a human answer is the source, retain a concise answer or decision description with its scope.

The source map is for auditing the author's coverage. It must not become a substitute for actual rules in the GDD.

## Final handoff

Present core design points and actual file links. State the status accurately, identify remaining material questions or delegated defaults, name the confirmed output destination(s), summarize gameplay/motion reference coverage and gaps, and disclose unread source limitations. Do not claim a GDD guarantees a fun game or that a structural check certifies the design. Stop at document delivery unless the user separately requested a subsequent task.

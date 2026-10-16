# Bridge to AI Game Studio

This integration ships with the forked AI Game Studio core plugin. Invoke `$ai-game-studio:gdd-game-studio` for the integrated workflow or `$ai-game-studio:gdd-interview` for a GDD-only request. Direct invocation of another Studio skill follows that skill's own entry point; those commands do not automatically load this orchestrator.

## Dependency discovery and routing

Use the active skill catalog first. Resolve `gdd-interview` and relevant `ai-game-studio:*` entries from their reported locations and read the actual files before using them. Do not assume commands named in upstream next-step suggestions exist in the current installation. Keep the orchestrator in control of the user's agreed scope and consume specialist output without resetting the project to an earlier discovery phase.

| Work needed | Relevant installed capability | Integration condition |
|---|---|---|
| Source reconciliation and exact design interview | `gdd-interview` | Canonical GDD and human decisions; no duplicate interview. |
| Existing large Studio project intake | `ai-game-studio:adopt` | Use when migration to Studio conventions is actually needed. |
| Scene identity and asset instructions | `ai-game-studio:art-bible`, `asset-spec` | Reuse GDD art/reference rules; read their workflows and prerequisites before invoking. |
| 2D sprites, tiles and atlas production | `ai-game-studio:sprite-generate` plus an available image-generation tool | A plan or prompt is not a generated/imported asset. Include environment/board/route assets as well as actors when required. |
| 3D, materials or rigged animation | `asset-3d-generate`, `material-texture-generate`, `rig-animation` | Select only when the design/runtime requires them and tools exist. A 2D game need not use a 3D pipeline. |
| Audio production | `ai-game-studio:npc-audio-generate` | Load for applicable music/SFX workflow; do not introduce NPC/VO features merely because the skill supports them. Local synthesis can satisfy an authorized fallback. |
| Architecture, registry, implementation stories | `create-architecture`, `architecture-review`, `create-control-manifest`, `create-epics`, `create-stories`, `story-readiness`, `dev-story` | Use the full route when justified. Build genuine prerequisites; never pass fake registry/ADR files just to satisfy presence checks. |
| Visual and temporal checks | `ai-game-studio:visual-qa` | Compare composed runtime scenes and transitions, not only isolated generated images. |
| Runtime and acceptance checks | `smoke-check`, `content-audit`, `test-evidence-review`, `story-done` | Verify actual behavior/artifacts and exact coverage; report absent evidence. |
| Change impact | `propagate-design-change`, `consistency-check` | Link changes back to the canonical requirement and refresh derived documents. |

The Studio `prompt-to-game` capability is oriented to a minimal concept prototype. Its default scope and placeholder preference do not replace an explicitly requested larger, polished game. `vertical-slice` is a distinct pre-production validation exercise with its own prerequisites and constraints. Do not invoke it merely as a synonym for the first milestone of a complete game job, and do not impose its content cuts or throwaway-code policy on an unrelated deliverable.

Delegation/subagents are optional here. Do not treat a routing table as authorization to spawn agents. Follow applicable session rules; if an invoked specialist explicitly requires delegation, honor that requirement only where authorized and available. Otherwise select a suitable direct workflow and describe it accurately.

## Canonical design and derived Studio records

Keep one authoritative GDD and decision record. Record the actual canonical paths and revision in the project implementation plan/checkpoint. For Studio TR registry or per-system files, preserve stable GDD IDs and attach the source path/anchor and revision. If the project needs Studio-specific TR IDs, map them to GDD IDs explicitly; do not rename away the original references.

Before implementing a story, compare its copied rule with the current canonical rule. Repair derivative staleness from settled human decisions without asking the same design question again. Surface genuine contradictions. An engine limitation or an implementation shortcut cannot silently redefine the game.

The source/decision log records where a rule came from; the canonical GDD states the operative rule. The coverage table records what was built and how it was checked. Neither audit prose nor evidence claims substitute for an actual requirement.

## Minimum implementation coverage record

Reuse equivalent project files rather than creating duplicate trackers. A compact Markdown table can contain:

| Field | Meaning |
|---|---|
| Requirement/event/content ID | Stable ID and canonical GDD section. |
| Scope and decision status | In scope, explicitly deferred, unresolved; source/human/delegated/proposed. |
| Implementation | Actual code/data location or asset ID; empty until present. |
| Verification setup | Starting state, input, expected result; level/scenario used. |
| Logic/data evidence | Actual command/check result and artifact/revision, or not run. |
| Runtime evidence | Entry point, inputs exercised, error findings and capture/revision, or not run/blocked. |
| Visual/motion/audio evidence | Comparable frames/clip/observation, reference ID and findings, or pending. |

Add an asset-family inventory covering all visible scene families and in-scope audio cues. Record delivered file or procedural implementation, runtime use, supplied/generated/placeholder state, provenance and remaining mismatch. Merely placing an image in a references folder does not mean the game uses matching art.

Track the requested content count separately from representative test scenes. Validate IDs, layouts, required mechanic flags, capacity/resource consistency, source-vs-authored status and playable access for every required content unit. Document known solutions/replays when required for puzzle validity; validate accessibility is not a claim of solvability.

## Presentation acceptance gate

Establish a compact comparison table in the existing coverage/art document before producing a large dependent asset batch or expanding the representative scene into the requested content pack. Use only traits material to this game's target. Do not add irrelevant criteria or treat the last game's appearance as a default.

| Field | Required meaning |
|---|---|
| Trait and scope | The object/scene/event and observable property that must match. |
| Target and authority | Inspected reference ID with frame/timestamp, or a human-supported textual target; identify proposals and delegated tuning. |
| Acceptance condition | Concrete preserved traits, allowed differences or supported ranges. Use qualitative distinctions where measurement is unavailable; do not invent numeric tolerances. |
| Candidate evidence | Actual composed scene capture or motion sequence, at comparable view/state/scale, with build revision. Label offscreen or mock evidence accurately. |
| Result and next action | Pass, fail or unverified; the specific difference, correction and dependent work affected. |

Consider camera/perspective; composition and object-to-board proportions; silhouette; board density and lane geometry; palette/material/light treatment; UI hierarchy/readability; and the core motion's path, direction, sequencing, spacing, tempo, contact and settle feedback where applicable. A static capture can support appearance criteria but cannot pass a motion criterion. Missing video can be replaced by an explicitly supported textual motion target; it does not justify inventing motion or claiming comparison with unobserved footage.

For example, “the source object travels to the fixed left entry rather than any empty lane” is an observable path criterion; “glossy rounded toy body with short limbs, not a tall humanoid silhouette” can be a silhouette criterion when the reference establishes those traits. These examples are diagnostic, not universal art rules. “Looks close”, a similarity percentage, or checking that every asset filename exists does not establish acceptance.

Pass the gate only when every applicable material criterion has supporting evidence and meets its condition. Self-review within delegated tuning can establish a recorded technical comparison; it must not be called human approval or proof of fun. Retain required human review where the user's scope or an applicable production workflow calls for it. If runtime, motion or audio evidence is unavailable, keep those criteria unverified and distinguish any independently passed appearance criteria.

Fix failures before scaling the affected asset family or scene. Recheck the changed criteria and coupled properties after a correction; preserve independent work. An explicitly authorized provisional batch may proceed with named unresolved criteria and replacement implications recorded. Do not use “we can polish later” as implicit approval to multiply a materially mismatched scene. For a request covering many levels, this gate is an internal dependency check, not permission to silently reduce the deliverable count.

## Spatial/temporal failure probes

These are diagnostic examples, not game defaults. Derive expected outcomes from the current game's design:

- A moving object has a fixed entry rule, but code searches for any vacant destination. Verify the documented entry under empty, occupied and repeated-tap states.
- A firing or interaction ray passes through an occupied incompatible target. Verify first-hit/occlusion semantics against the actual intended design, not color search convenience.
- A route should end after one circuit, but rendering mutates movement completion or counting. Verify start, turns, end and return; render-frequency changes must not change simulation outcomes.
- A connected group has eligibility, order and shared capacity requirements. Verify partial room, blocked member, simultaneous inputs and atomic reservation/commit as specified.
- A pending object is merged, removed or reordered by another event. Verify the pending request's documented cancellation/continuation behavior and reset/recovery cleanup.
- Changing speed affects overlapping transfer or impact state. Verify sequencing, reservation and resource accounting stay correct at supported speeds and during pause/resume.
- A screen matches one supplied actor but ignores board, lane, camera and scale. Compare the complete composition and materially different states before calling presentation matched.

If the GDD does not resolve a probe's material fork, ask the human and update design before implementing dependent behavior. Do not turn the Pixel Flow examples into defaults for other games.

## Completion and capability limits

Choose a runnable delivery form compatible with the user's target and actual project. Explain how to start it. Complete appropriate runtime checks through permitted tools; never bypass an access denial using another browser, server or automation channel. Preserve mock, static, real runtime, visual and human-feedback evidence as different categories.

For an unresolved material decision, finish independent tasks, record the exact dependency and ask the next useful question. For unavailable tools, identify the concrete unverified or undeliverable item. Keep progress checkpoints so a later turn resumes remaining scope rather than replaying onboarding. Do not declare the requested game finished until the scope and required checks are actually satisfied.

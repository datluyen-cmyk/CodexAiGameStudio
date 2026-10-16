---
name: gdd-game-studio
description: "Combine traditional GDD, Dev/Art requirements and references into a precise GDD, then implement the requested game with AI Game Studio asset, animation, audio and QA workflows. Use for an integrated GDD-to-game request or continuing such a build; preserve document-only scope when requested."
---

# GDD Game Studio

One entry point for design interview, game implementation, asset production and verification. Compose the installed `gdd-interview` and `ai-game-studio` capabilities without creating a second design authority. Use the user's language for documents and questions.

## Resolve the requested outcome

Read existing sources, human answers, project instructions and current artifacts before asking anything. Determine whether this session requests design only, a game build, a design/build correction, or a workflow update. Updating this skill does not authorize rebuilding a game. A GDD-only request ends at the document handoff. An authorized build continues through implementation and checks without requiring the user to invoke each downstream skill.

Preserve the requested content count, mechanics, presentation and output locations. A requested 20-level game remains a 20-level deliverable even if the first implementation milestone uses one level. The Studio concept-prototype default is not the scope authority. Do not silently substitute a placeholder demo for a request that includes finished-looking art, animation, VFX and audio.

Read [the Studio bridge](references/studio-bridge.md) before handing design to implementation or selecting Studio skills. Discover the active installed versions; do not hardcode plugin cache version paths. If a needed skill/tool is absent, disclose that and use a compatible available approach within the authorized scope. Do not claim to have run a skill, generator, reviewer or runtime that was not actually used.

## 1. Author or reconcile the design

Read and follow [GDD Interview](../gdd-interview/SKILL.md), including its relevant references. Reuse an existing package and stable IDs rather than restarting the interview. Inspect supplied images and source formatting; obsolete or struck-through statements are not active requirements. Keep GDD.md self-contained and about the game; retain source audit narration in companions.

Carry forward all settled human answers. Ask only the next 1–3 material design forks; continue independent work while waiting. Research facts available in supplied files before asking. Delegate routine engine/framework, code layout and tooling choices to the builder. When recognizable-game references are involved, reuse the confirmed clone/adaptation/original intent; if missing and material, resolve it before defining the imitation target.

For spatial/moving games, apply the spatial and temporal checks in GDD Interview. Write the source, fixed or variable destination, path/direction, obstruction rule, capacity reservations, selection priority, concurrent-input handling, arrival and completion semantics. Derive rules from evidence or human answers; these fields are prompts to discover the game's rules, not permission to impose genre defaults.

Create an actionable event specification for each in-scope interaction, including visible rejection, waiting, reveal, failure and recovery. Cover source objects, board/world, routes/lanes, receiving areas, UI, VFX and audio as applicable. Specify animation phases and state commit separately. A still image can establish composition, not motion. Missing motion references require an explicit textual target or a precise question.

Run GDD Interview's proactive gameplay/feel questions while authoring, before dependent implementation. If only stills are supplied, settle material motion and event semantics through concrete alternatives or explicit delegation; do not silently postpone them to coding. Reuse accepted textual targets without requiring a video, and preserve explicitly deferred questions with their dependency boundaries. Builder tuning is allowed within delegated bounds; it does not authorize inventing the interaction sequence.

Do not label the document approved on the basis of checklist completion. Track drafting/readiness, human approval, and authority to build separately. An explicit instruction to build permits independent settled work while unanswered dependent behavior remains blocked.

## 2. Bind design to implementation

Inspect the real repository and executable entry point before choosing an implementation plan. Read the canonical GDD, decision log, reference inventory and authored content together. Carry any remaining material forks into a builder question queue with requirement IDs and dependency boundaries.

Maintain one compact `BUILD_COVERAGE.md` or equivalent existing table. Link each in-scope requirement, motion event, asset family and level/content unit to its implementation location and intended verification. Add actual test/capture evidence as it becomes available. Include version/revision information so copied requirements cannot silently become stale. Documentation rows are planning evidence until checked against the delivered files and running behavior.

Define ordered milestones: a representative complete interaction at target presentation quality, integrated loop with failure/recovery, complete requested content, then final checks. These are internal milestones within the authorized job. Do not stop after the first milestone and call the requested game finished. Build reusable systems so later levels exercise the same implementation rather than duplicating special-case code.

For substantial Studio projects, populate its actual concept/system index, architecture/control manifest, TR registry and story prerequisites from the canonical GDD before using skills that require them. Preserve a link back to the canonical requirement instead of rewriting a contradictory rule. For small browser games, use a compact implementation plan and coverage table when a full studio bureaucracy would add no value; describe this as the integrated lightweight route, not as having executed Studio skills whose prerequisites were skipped.

## 3. Produce and integrate presentation

Read only the relevant installed Studio asset/QA skills when their work is needed; follow their applicable constraints and actual tool availability. Use native image/audio/3D tools for production, not prose that merely says an asset should be generated.

Inventory the entire visible scene before generation: board/world, route or lane, interactable objects, containers, backgrounds, UI and relevant effects. Identify which parts need sprites, geometry, procedural drawing or supplied assets based on the target. Procedural assets are acceptable when they reproduce required traits. A polished character sprite alone cannot satisfy scene-wide art requirements.

Establish a representative composed scene using the inspected references: camera, object scale, board density, layout, palette/material, lane thickness and UI hierarchy where relevant. Review candidate assets in that composition before generating large batches. Preserve sources. Distinguish human-reviewed art, delegated provisional choices and unresolved style decisions. Honor existing generation/tuning authorization; do not fabricate approval or trigger repeated generic permission prompts.

Before multiplying assets or content that depends on the presentation, apply the [presentation acceptance gate](references/studio-bridge.md#presentation-acceptance-gate). Define the important match criteria from inspected references or accepted textual targets before assessing the candidate. Record comparable evidence and a pass/fail/unverified result for each applicable criterion. Fix failed criteria; an unverified criterion does not pass. Keep dependent batches pending when a material criterion fails or cannot be checked, while continuing independent work. Human-approved provisional expansion is allowed only within its explicit scope and retains the unresolved quality status. Do not require another approval when an existing decision already covers the same target and delegation.

For generated atlases, verify real alpha, frame bounds, pivot/baseline, scale consistency and animation continuity before import. Treat a montage as a candidate sheet until its frames actually work at game scale. Connect each in-scope motion event to working code and to its audio/VFX; placeholder status and any omitted event remain explicit in coverage.

When original audio is missing, use the authorized generation, synthesis or search fallback. Package needed runtime assets locally and record actual source/generation/provenance. If a production capability is unavailable, complete independent work and name the asset or quality gap; do not silently substitute a different art direction or claim the final asset exists.

## 4. Implement and verify in the target runtime

Implement from settled rules and authored level data. Keep a single source of simulation truth; rendering reads/interpolates it and must not decide whether gameplay events occurred. Commit each event once. Reserve destinations for in-flight/group actions where the documented semantics require it; preserve pending-input identity through other state changes. Clear or reconcile pending work on reset/revive according to the design. Maintain meaningful tunable timing/speed values without changing gameplay semantics when adjusted.

Use relevant automated checks for logic, integration and authored content. Check the actual executable path as well: start the game, perform the core interaction, complete a loop, inspect runtime errors and exercise relevant failure/recovery. For browser games, syntax or mock-canvas passes do not prove browser startup or interaction succeeds. Test actual asset loading, pointer input, timing and rendering through available authorized runtime tools.

Compare runtime captures with the references at comparable aspect ratio, camera and state. Review before/during/after motion frames for path, entry/exit, spacing, direction, contact and destination reaction. Inspect all materially different mechanic variants and validate every required level/content record; a representative visual sample does not prove all levels are correct or solvable. Use replays/solutions or explicit unverified status for content where solvability matters.

Fix discovered failures, rerun affected checks and continue independent remaining work. Avoid speculative tests that merely restate implementation. Record the check, result, artifact, command/runtime context and current build revision. If runtime access is blocked, follow the access restriction, do not bypass it through another route, and report runtime/visual verification pending; mocks remain labeled as mocks.

## 5. Propagate corrections and close accurately

For a human correction or observed bug, determine whether it is an implementation mismatch, missing design decision, bad content, or presentation mismatch. A code patch is not automatically a design change. Update affected canonical rules and decision records when the human changes/clarifies the design; then propagate to coverage, derived Studio documents, implementation, examples and relevant regression checks. Preserve settled unrelated rules.

Generalize demonstrated workflow failures into the skill only when reusable. Do not bake one game's belt size, launch corner, obstruction behavior or merge rules into universal defaults. Do not update personal skills during ordinary game work unless requested or already authorized.

Before reporting completion, reconcile the requested scope against the actual delivered project: content count, mechanics, all scene asset families, animation/audio/VFX events, playable entry point, packaging and checks. Complete every authorized independent item. Report concrete missing work or unanswered decisions; do not replace them with a completion percentage or an unsupported visual-similarity estimate.

Keep status dimensions separate: design readiness/approval, implementation progress, runtime checks, visual/motion checks and human feel feedback. A passing mock cannot mark runtime or visual quality passed. A working first loop cannot mark all requested content complete.

Deliver links to the canonical GDD, playable entry/build, coverage/evidence and asset provenance as relevant. Explain material limits plainly. If only design or skill edits were requested, deliver those artifacts without starting the game build.

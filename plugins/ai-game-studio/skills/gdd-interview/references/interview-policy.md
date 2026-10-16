# Clarifying while authoring a GDD

## Decide whether a question is necessary

Before asking, write down the two plausible interpretations and the concrete difference they produce. If the only difference is prose wording, handle it editorially. If it changes scope, player behavior, a visible state, feedback, content, or a binding constraint, first search the available evidence and settled decisions; then ask if unresolved.

Questions about facts obtainable from inputs are not interviews. Inspect them. If a source cannot be read, say exactly what remains unavailable; do not fill the gap from the filename, a similar game, or a convenient convention.

Separate cases:

| Case | Authoring action |
|---|---|
| Source states one rule clearly | Write it and record provenance; do not ask for redundant confirmation. |
| Human already resolved a conflict | Apply the decision only to its documented scope. |
| Two input sources disagree | Present the conflicting rules/locators and their effects. Ask which applies, including level/profile scope if relevant. |
| No rule covers a material case | Ask for a choice or permission to use a specific proposal. Keep the dependent draft open. |
| User delegates a class of choices | Choose within that class, record rationale and prototype/production scope. Do not ask each delegated choice again. |
| Merely editorial or nonbinding implementation detail | Resolve it without inventing game behavior. |
| User cannot decide yet | Record the question and impact; discuss an explicitly narrower scope or an approved provisional default. |

## Ask in a way the designer can answer

Use the user's language. Questions must describe a concrete state, action, and difference, with a short explanation of why it matters. Put 2–3 viable options when useful, including the ability to give a different answer. Identify a recommendation as the agent's proposal, not the user's preference. Do not force multiple dependent decisions into one choice.

Prefer short rounds of independent questions. For dependent decisions, ask the prerequisite first. There is no question quota, arbitrary certainty percentage, or obligation to investigate every hypothetical edge case. Stop when no material in-scope design fork remains unresolved after the completeness review.

Give each question ID exactly one answerable decision. Do not hide a checklist of independent decisions behind a topic label such as "How does the conveyor work?" For example, capacity, selection order, route direction, and match timing are separate choices. A coherent proposed event sequence may be presented as one choice when its steps form one inseparable design alternative; identify the whole proposal explicitly.

Normally show only the next 1–3 independent decisions to the human. Keep later questions in the persisted backlog; do not append the entire backlog to a progress update or final response during an unfinished interview. State briefly that other topics will follow after the prerequisites settle. If a user specifically asks for all gaps, show the full list with dependencies; otherwise prefer the next answerable round.

Use the host's supported question interface or normal conversation; never depend on a Claude-specific tool name. If using asynchronous questions, continue only independent work. Elapsed time, an ignored option, or a request for more context is not an answer. In a noninteractive run, persist the unresolved decisions and stop affected work rather than impersonating the human.

## Example: selection and capacity

Suppose a source says "tap same-color cubes to send them to the conveyor."

- Inspect whether another section defines connectedness and tap target before asking.
- If selection is unresolved, ask whether tapping selects a connected group, every exposed cube of that color, or a source tray. Use a small board example showing the difference.
- If partial transfer is already approved, do not ask whether to reject the whole group. Investigate which members move first only if the choice changes source state, layers, or solution behavior.
- If only some cubes leave, determine what happens to the remaining members: fixed positions, compaction, gravity, or another source-defined rule. Inspect sources and settled answers first. If unresolved and material, ask with a concrete before/after example; neither position preservation nor compaction is an implicit default. Keep dependent layouts, exposure rules and solution examples unresolved until answered or explicitly delegated.

## Proactive gameplay and feel interview when motion evidence is missing

During GDD authoring, walk each in-scope core interaction from input to completion. Do this before handing the document to a coding agent. For every material attribute, determine whether it is established by inspected evidence, a scoped human answer, explicit delegation, or is unresolved. Do not assume missing animation semantics can be filled in during coding.

For the interactions that actually exist in the game, check:

- What accepts input, which objects are eligible, and whether selection affects one object or a group.
- Which object moves from which origin to which destination; whether the destination is fixed or selected dynamically; the path, direction, stops and end-of-route behavior.
- Continuous versus stepped motion, simultaneous versus sequential actions, spacing and overlaps that affect readability or play.
- When capacity is reserved/released, progress or ammo changes, the destination reacts, and the action becomes complete.
- What the player sees/hears on selection, departure, travel, contact, impact, settle and completion; the intended weight/energy and relative prominence of feedback.
- What happens on an occupied destination, obstruction, insufficient capacity, repeated input, pause/reset or relevant recovery.

Use these as an internal coverage check, not a questionnaire dumped on the human. Search existing sources first, then ask the next 1–3 unresolved material choices in concrete player terms. For example: “Should the shooter glide continuously along the loop, or move one position and pause before each shot?” A generic question such as “What animation do you want?” does not resolve the fork.

If only still images and a vague GDD are available, actively ask to settle missing semantic/feel choices while drafting. The human can supply a relevant clip, choose between concrete textual alternatives, approve an explicitly proposed motion sequence/timing set, or delegate adjustable tuning. A missing video does not block writing a complete textual target. For a faithful clone, identify any motion attributes that remain unverified against the original and request the specific missing reference when useful; do not claim measured fidelity from text or stills.

Do not require the human to provide easing coefficients, exact milliseconds, shader settings or audio engineering details. Offer approximate adjustable timings and presentation choices where helpful, label their proposal/delegation status, and ask about their player-visible consequence. Once semantic order and intended feel are settled or explicitly delegated, the builder may tune implementation within those bounds.

After each answer, write the full operative rule and event sequence into the GDD, update the decision and reference records, and add a distinguishing acceptance example. “Ask later”, “make it satisfying” and an unapproved timing preset cannot substitute for the known parts of the design. Move an unresolved material choice to the later coding interview only when the human deliberately defers it; name the exact dependency and stop-before-implementation condition. Never silently defer core interaction semantics just to finish drafting.

### Example: vague animation

Weak: "Should the game have nice animation?"

Useful: "When a cube is received, should it first reach the matching station and then jump into the receiving tray, or jump as soon as a matching tray becomes available? This changes the travel rule and the order of feedback."

After that rule is settled, draft the event sequence and propose timing ranges together if necessary. The user need not invent easing coefficients. They can select a reference clip, choose a concrete motion description, approve a provisional timing set, or delegate tunable presentation details. Do not silently decide the semantic sequence through an animation preset.

## Example: sources and visual fidelity

If the original GDD says 3D top-down while a simulated Art brief says flat 2D, ask whether the brief is an authorized direction change or only a feasibility proposal. Do not use a screenshot's apparent flatness to resolve the dimensionality conflict.

A screenshot may show a counter reading 0/12. Record that for the depicted level/state. It does not prove all levels have capacity 12 or that the counter changes at animation start. Ask only about the remaining rules relevant to the requested document scope.

## Save and resume

Assign stable decision IDs. Record each answer immediately with affected requirements, the question's scope, rejected alternatives when useful, and the source locator or concise human quote. Apply consequences across the GDD before the next round. Unanswered questions retain their own IDs and dependency lists.

On a long session or handoff, preserve the current drafting position and next unresolved prerequisite in the decision document. Resume from the files; do not make the human reconstruct the interview history.

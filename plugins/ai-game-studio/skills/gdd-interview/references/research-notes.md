# Research basis and adaptation notes

Consulted on 2026-10-16. These are design influences, not mandatory runtime dependencies. This skill's instructions are an original synthesis tailored to GDD authoring; the upstream projects have not been installed or vendored by this skill.

| Source | Useful principle adopted | Adaptation/limit |
|---|---|---|
| [BMad Game Dev Studio](https://github.com/bmad-code-org/bmad-module-game-dev-studio), especially the locally installed `gds-gdd` discovery, measurable mechanics, reconciliation and final review | GDD is design intent; read inputs, resolve important decisions, preserve feel and reconcile sources before completion. | No BMad module/config dependency; section-local interview while drafting, no production handoff or code workflow. |
| [dotnet-claude-kit spec](https://github.com/codewithmukesh/dotnet-claude-kit/blob/main/skills/spec/SKILL.md) | A recommendation is not a chosen requirement; persist answers, expose contradictions, concrete acceptance criteria. | Replace API/application categories with game behavior and Dev/Art constraints; avoid asking every theoretical gap. |
| [cfircoo spec-interview](https://github.com/cfircoo/claude-code-toolkit/blob/main/skills/spec-interview/SKILL.md) | Ask project-specific questions that expose hidden decisions; follow up on vague answers. | No pinned model, fork context, or Claude-only question tool; no implicit shift to implementation. |
| [Matt Pocock grilling](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) | Ask dependent questions only after prerequisites settle; discover facts in evidence and reserve decisions for the human. | Host-neutral questioning and persistence in the output bundle; no mandatory subagent/Skill-tool dependencies. |
| [GitHub Spec Kit clarify](https://github.com/github/spec-kit/blob/main/templates/commands/clarify.md) | Structured ambiguity scan, impact-based prioritization, answers folded into the spec. | No fixed five-question limit or spec-kit directory/command requirement; only relevant categories. |
| [prd-maker](https://github.com/omrsag/prd-maker/blob/main/SKILL.md) | Reuse answered information and challenge untestable generalities before finalizing. | Draft supported sections early rather than withhold all writing until a global interview finishes. |
| [edhahn game-designer](https://github.com/edhahn/agent-skills/blob/main/game-designer/SKILL.md) | Inputs, outputs, edge cases, player-facing steps, tuning parameters, UI/audio requirements. | No assumed studio engine/team or mandatory production-code/asset pipeline. |
| [OpenAI skill authoring](https://learn.chatgpt.com/docs/build-skills) | Focused SKILL.md, optional references/scripts, explicit inputs/outputs, progressive loading. | Standalone local skill, no hosted API, fine-tuning, account connection, or package installation needed. |

## Why this differs from a generic spec interview

The requested task starts with substantial traditional game documentation and separate Dev/Art input. Re-interviewing the entire pitch wastes settled information. The important work is reconciling authority and translating vague experience descriptions into exact mechanics, visuals, event sequences, content and constraints while retaining original intent.

The earlier Cube Match exercise exposed transferable failure modes: provisional team suggestions became convenient defaults, static references did not establish animation, rules did not specify state/counter synchronization, and level summaries did not provide exact runnable layouts. These are examples for coverage and validation, not universal rules that every game must have a conveyor, tray, or a specific animation.

## Evaluation boundary

Structural validation checks skill packaging only. Behavioral evaluation should use isolated cases with incomplete/conflicting evidence, fully specified inputs, and explicit human decisions. Check observable outputs: right questions, no invented approvals, retained requirements, reproducible examples, source coverage, and actual asset links. Use a different case to test transfer; an AI's own confidence percentage is not evidence of completeness.

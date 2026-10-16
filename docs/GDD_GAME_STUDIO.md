# GDD-to-game workflow

This repository adds two Codex skills to the AI Game Studio core plugin.

## Choose a skill

- `$ai-game-studio:gdd-interview` creates or revises a build-ready `GDD.md` from
  a traditional GDD, Dev/Art requirements, references, and decisions gathered
  during the interview. It can finish with a document-only handoff.
- `$ai-game-studio:gdd-game-studio` coordinates the interview with the AI Game
  Studio workflows for asset creation, animation, audio, implementation, and
  verification when the user requests a game build.

Both skills preserve the requested scope, ask about unresolved gameplay rules
that materially affect the result, and distinguish confirmed decisions from
proposals. The integrated workflow does not imply that every external tool or
runtime is installed; it must report unavailable capabilities and evidence
limits.

## Install once

Add the marketplace and install its core plugin:

```sh
codex plugin marketplace add datluyen-cmyk/CodexAiGameStudio --ref main
codex plugin add ai-game-studio@datluyen-codex-ai-game-studio
```

Start a new Codex task after installation. The two GDD skills are packaged
inside the core plugin and need no separate copy/install step. Other platform
and editor plugins remain optional.

## Upstream relationship

AI Game Studio remains the upstream game-production toolset by frabcd. This
repository redistributes it under its MIT license and preserves its license
and provenance notices. The two GDD skills are additions maintained in this
fork. See [NOTICE.md](../NOTICE.md) and the root [README](../README.md).

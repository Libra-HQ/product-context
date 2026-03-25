# Skills Capabilities Reference

_Last updated: 2026-03-25 (UTC)_

This document captures a baseline view of current skills capabilities across key ecosystems, with emphasis on:
- hooks
- scripts
- references
- assets

## 1) Open Agent Skills specification baseline

Primary source: Agent Skills specification and overview.

### Core structure
The open specification defines a skill as a directory with required `SKILL.md` and optional `scripts/`, `references/`, and `assets/` directories. This is the clearest common denominator for portability.

### Capability meaning in spec terms
- **scripts/**: executable code agents can run; should document dependencies and handle errors.
- **references/**: additional documentation loaded as needed; best kept focused and modular.
- **assets/**: static resources like templates, images, and data files used during outputs.

### Loading model
The spec and ecosystem guidance emphasize progressive disclosure:
1. metadata always loaded,
2. `SKILL.md` instructions loaded when triggered,
3. scripts/references/assets loaded on demand.

## 2) Anthropic Claude Agent Skills baseline

Primary source: Claude API docs (Agent Skills overview).

### Packaging model
Anthropic describes Skills as modular capabilities containing metadata, instructions, and optional resources (including scripts/templates) that are automatically used when relevant.

### Execution model
Anthropic documentation describes the same staged loading model: metadata first, instruction body on trigger, and additional resources/code as needed in the runtime filesystem environment.

## 3) Cursor Skills baseline

Primary sources: Cursor changelog and Cursor engineering blog.

### Skills primitives
Cursor states that skills are defined in `SKILL.md`, with support for custom commands, scripts, and instructions for procedural specialization.

### Hooks capability
Cursor explicitly describes hooks as scripts that run before/after agent actions, and provides an example hook configuration in `.cursor/hooks.json` with a `stop` hook command.

### Assets tie-in
Cursor notes generated images are saved into a project `assets/` folder by default, indicating practical integration of asset-oriented workflows in agent use.

## 4) Cross-ecosystem synthesis (inference)

Based on the cited sources, the practical interoperability center appears to be:
- skill metadata + instructions in `SKILL.md`
- operational logic in scripts
- expandable domain docs in references
- output/support files in assets

Hooks are currently the least universally standardized concept across the three sources, but are clearly documented in Cursor materials and conceptually align with scriptable workflow extension.

## 5) Source links
- Agent Skills home: https://agentskills.io/home
- Agent Skills specification: https://agentskills.io/specification
- Claude Agent Skills overview: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
- Cursor skills-related changelog: https://cursor.com/changelog/2-4
- Cursor agent best-practices blog (skills + hooks examples): https://cursor.com/blog/agent-best-practices

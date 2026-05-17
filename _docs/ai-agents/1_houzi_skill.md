---
title: AI Agent Skill
category: AI Agents
permalink: ai-agents/houzi_skill
order: 1
---

Houzi comes with a built-in **AI Agent Skill**. This is a modular knowledge base designed specifically for AI coding assistants (like Antigravity, Cursor, Claude Code, and GitHub Copilot) to help them understand the app's architecture and perform complex configurations with 100% accuracy.

## Why use AI Agents with Houzi?

Houzi is a highly configurable, white-label application. While it offers deep customization, it follows strict architectural patterns (like the Hook system and `#AARRGGBB` color format). Using an AI agent with the Houzi Skill allows you to:

- **Eliminate Errors**: The agent knows the exact JSON keys and Dart hook signatures.
- **Speed up Implementation**: Tasks like changing colors, adding home sections, or setting up deep links can be done with a single natural language command.
- **Maintain Best Practices**: The agent is instructed to never modify core packages and always follow the proper versioning workflow.

## How to use the Skill

The skill is stored in the project at:
`[project-root]/.agents/skills/houzi/`

### 1. Automatic Discovery
Most modern AI coding agents will automatically discover this skill. When you open the project in an IDE with an AI agent (like Cursor), it reads the `.agents/` directory and immediately gains "expert knowledge" of Houzi.

### 2. Example Prompts
You can ask your AI agent to perform tasks using natural language. For example:

- *"Change the primary app color to a deep purple."*
- *"Add a 'Recent Searches' section to the top of the home screen."*
- *"Add a custom drawer item that navigates to my website."*
- *"Configure the app to use Google Maps as the default provider."*

## The Golden Rules for AI Agents

The skill enforces several "Golden Rules" that ensure the stability of your app:

1.  **Increment Config Version**: Every change to `configurations.json` MUST increment the `api_config_version`. This triggers an Over-The-Air (OTA) update for your users.
2.  **Alpha-First Colors**: All colors must use the `#AARRGGBB` hex format (where `AA` is the alpha/transparency byte).
3.  **Isolation**: AI agents are strictly forbidden from modifying files inside `packages/houzi_package/`. All customizations must happen in `assets/configurations/` or `lib/hooks_v2.dart`.
4.  **Hook-Based Customization**: Custom widgets and logic must be implemented via the `HooksV2` system in `lib/hooks_v2.dart`.

## Customizing the Skill

If you have added custom features or modified the core app in ways an AI agent should know about, you can update the modules inside `.agents/skills/houzi/`. This ensures that the AI agent remains a reliable partner as your project evolves.

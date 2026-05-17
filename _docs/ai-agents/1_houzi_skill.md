---
title: AI Agent Skill
category: AI Agents
permalink: ai-agents/houzi_skill
order: 1
---

Houzi comes with a built-in **AI Agent Skill**. This is a modular knowledge base designed specifically for AI coding assistants (like Antigravity, Cursor, Claude Code, and GitHub Copilot) to help them understand the app's professional decoupled architecture and perform complex custom implementations with 100% accuracy.

## Why use AI Agents with Houzi?

Houzi is a highly configurable, white-label real estate application. It follows a clean architecture governed by two primary customization vectors: an **OTA-enabled Configuration Engine** (`configurations.json`) and a **Dart-level Hooks Customization System** (`hooks_v2.dart`).

Using an AI agent with the Houzi Skill allows you to leverage these systems seamlessly to:

- **Enforce Architectural Boundaries**: The agent understands the clean segregation between the core package and the custom app wrapper, ensuring customization happens exclusively in configuration and hook files.
- **Master Hook-Based Injection**: The agent can instantly write complex custom widget wrappers, dynamic data-formatting hooks, and platform-specific feature toggles without you needing to memorize the hook registry or signatures.
- **Accurately Navigate the Dynamic Layout Engine**: The configuration JSON spans thousands of lines and controls all app sections. The agent knows exactly where and how to modify search filters, home screen blocks, navigation structures, and details page modules.
- **Enable Risk-Free OTA Updates**: The agent automatically adheres to configuration schema compliance and OTA versioning protocols, ensuring seamless runtime integration.

## How to use the Skill

The skill is stored in the project at:
`[project-root]/.agents/skills/houzi/`

### 1. Automatic Discovery
Most modern AI coding agents will automatically discover this skill. When you open the project in an IDE with an AI agent (like Cursor), it reads the `.agents/` directory and immediately gains "expert knowledge" of Houzi.

### 2. Example Prompts

You can ask your AI agent to perform both common setup tasks and complex architectural customizations using natural language:

#### Common Setup & Configuration
- *"Change the primary app color to a deep purple."*
- *"Add a dynamic banner to the home screen."*
- *"Change the app name to 'My Business Name'."*
- *"Use the attached icon file to generate and set the app launch icons."*
- *"Add a new custom page to the bottom navigation bar."*
- *"Add a custom drawer item that navigates directly to my website."*

#### Advanced Architecture & Extensions
- *"Create a new custom property item card design that is highly compact, and inject it via the property item design hook."*
- *"Intercept the home page's building list to inject a custom 'Recent Searches' section slider, and implement its UI using a separate hook-registered custom widget."*
- *"Add a custom taxonomy picker filter for 'Heating Source' in configurations.json, ensuring it maps properly to the WordPress REST API endpoint."*
- *"Implement a grid-based secondary layout for 'Valued Features' on the property details page, using a hook to toggle between the grid and the default list layout."*

## The Golden Rules for AI Agents

The skill enforces several "Golden Rules" that ensure the stability and upgradability of your app:

1.  **Increment Config Version**: Every change to `configurations.json` MUST increment the `api_config_version`. This triggers an Over-The-Air (OTA) update for your users.
2.  **Decoupled Hook Implementation**: Custom visual elements and complex widgets must be written as separate clean Dart classes inside `lib/` and cleanly referenced/registered via `hooks_v2.dart` rather than bloating the hook file.
3.  **Isolation**: AI agents are strictly forbidden from modifying files inside `packages/houzi_package/`. All customizations must happen in `assets/configurations/` or `lib/hooks_v2.dart` to maintain an easy core package upgrade path.
4.  **WordPress API & Taxonomy Alignment**: When configuring dynamic search filters, detail modules, or terms tabs, the agent must fetch real taxonomy metadata via WordPress REST API helper modules to ensure exact key alignment rather than guessing slugs.

## Customizing the Skill

If you have added custom features or modified the core app in ways an AI agent should know about, you can update the modules inside `.agents/skills/houzi/`. This ensures that the AI agent remains a reliable partner as your project evolves.

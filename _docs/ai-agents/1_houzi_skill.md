---
title: Houzi AI Agent Skill
category: AI Agents
permalink: ai-agents/houzi_skill
order: 1
---

> ### ⚡ The Future of No-Code & Low-Code Customization is Here
> Configuring and customizing Houzi has never been easier. By using an AI coding assistant powered by our **AI Agent Skill**, you don't need to manually read hundreds of lines of code or memorize configuration schemas. 
> 
> Simply tell your AI assistant (like Antigravity, Cursor, Claude Code, or GitHub Copilot) what you want to achieve in plain English, and watch it configure, code, and polish the app automatically. It's like having a senior Houzi engineer pair-programming with you 24/7.

---

## 🚀 See It In Action: Example Prompts

Here are some real-world prompts you can give your AI agent right now to perform common setup tasks and complex architectural customizations. 

### 🎨 Common Setup & Configuration
*   *"Change the primary app color to a deep purple."*
*   *"Add a dynamic banner to the home screen."*
*   *"Change the app name to 'My Business Name'."*
*   *"Use the attached icon file to generate and set the app launch icons."*
*   *"Add a new custom page to the bottom navigation bar."*
*   *"Add a custom drawer item that navigates directly to my website."*

### 🛠️ Advanced Customizations & Integrations
*   *"Add feature taxonomy terms as tabs in Home Air and also add its icons. Use wordpress api to fetch taxonomy from my website."*
*   *"Replace the Watch Video option in property details page with an inplace youtube thumb and when clicked on it, open in app browser to launch the video inside the app."*
*   *"Create a new custom property item card design that is highly compact, and inject it via the property item design hook."*
*   *"Intercept the home page's building list to inject a custom 'Recent Searches' section slider, and implement its UI using a separate hook-registered custom widget."*

---

## Why use AI Agents with Houzi?

Houzi is a highly configurable, white-label real estate application. It follows a clean architecture governed by two primary customization vectors: an **OTA-enabled Configuration Engine** (`configurations.json`) and a **Dart-level Hooks Customization System** (`hooks_v2.dart`).

Using an AI agent with the Houzi Skill allows you to leverage these systems seamlessly to:

-   **Enforce Architectural Boundaries**: The agent understands the clean segregation between the core package and the custom app wrapper, ensuring customization happens exclusively in configuration and hook files.
-   **Master Hook-Based Injection**: The agent can instantly write complex custom widget wrappers, dynamic data-formatting hooks, and platform-specific feature toggles without you needing to memorize the hook registry or signatures.
-   **Accurately Navigate the Dynamic Layout Engine**: The configuration JSON spans thousands of lines and controls all app sections. The agent knows exactly where and how to modify search filters, home screen blocks, navigation structures, and details page modules.
-   **Enable Risk-Free OTA Updates**: The agent automatically adheres to configuration schema compliance and OTA versioning protocols, ensuring seamless runtime integration.

---

## How to use the Skill

The skill is stored in the project at:
`[project-root]/.agents/skills/houzi/`

While the examples below demonstrate how to use **Antigravity** to execute customizations step-by-step, the Houzi Skill system is fully universal and works out-of-the-box with any modern AI coding assistant (like Cursor, Claude Code, or GitHub Copilot).

### Step-by-Step Guide: Customizing Houzi with Antigravity

<img src="../../images/houzi-ai-skill.jpeg" alt="Houzi AI Skill in Action" title="Houzi AI Skill in Action"/>

#### Step 1: Install & Set Up Antigravity
Download and install the **Antigravity** IDE or command-line agent. Antigravity is a state-of-the-art agentic AI coding companion designed specifically to pair-program, analyze architectures, and execute codebase refactoring safely.

#### Step 2: Open Your Houzi Project
Launch Antigravity and open your Houzi Flutter project folder. 

#### Step 3: Automatic Skill Detection
Once opened, Antigravity's indexing engine scans your workspace. It will automatically detect the `.agents/skills/houzi/` directory containing all schema definitions, layout details, hook customization registries, and system configurations. You don't need to configure anything—the AI immediately becomes an "expert Houzi developer".

#### Step 4: Ask & Automate
Now, simply open the AI chat panel and start instructing the agent. Here are step-by-step examples of how to run your commands:

##### Example A: Customizing App Name, Bundle ID, & Launcher Icons
1. Ask Antigravity:
   > *"Update my app's name to 'PisoCasa', change the iOS and Android bundle identifiers to 'com.pisocasa.app', and use assets/icons/logo.png to generate all launcher icons."*
2. **What Antigravity does**:
   - Updates the app name across native Android and iOS configurations.
   - Replaces bundle identifiers in `build.gradle` and Xcode project settings.
   - Safely updates dependencies, configures `flutter_launcher_icons.yaml`, and runs the generator command to rebuild all launcher resolutions.

##### Example B: Updating Theme Colors & Fonts
1. Ask Antigravity:
   > *"Change the app theme's primary color to a premium Indigo (#3F51B5), background to off-white, and switch the font family to 'Outfit'."*
2. **What Antigravity does**:
   - Safely updates hex values in the configurations.
   - Inspects `configurations.json` structure, increments the `api_config_version` to trigger an Over-The-Air (OTA) update so your users get the new design instantly.
   - Generates the necessary fonts configuration and localizations.

##### Example C: Advanced Layout Tweaks
1. Ask Antigravity:
   > *"Add feature taxonomy terms as tabs in Home Air and also add its icons. Use wordpress api to fetch taxonomy from my website."*
2. **What Antigravity does**:
   - Inspects your backend connection config.
   - Rewrites your Home Air section layout inside `configurations.json` with the newly dynamic taxonomy terms tabs.
   - Adds custom icons mappings safely matching your WordPress REST API taxonomy terms metadata.

---

## The Golden Rules for AI Agents

The skill enforces several "Golden Rules" that ensure the stability and upgradability of your app:

1.  **Increment Config Version**: Every change to `configurations.json` MUST increment the `api_config_version`. This triggers an Over-The-Air (OTA) update for your users.
2.  **Decoupled Hook Implementation**: Custom visual elements and complex widgets must be written as separate clean Dart classes inside `lib/` and cleanly referenced/registered via `hooks_v2.dart` rather than bloating the hook file.
3.  **Isolation**: AI agents are strictly forbidden from modifying files inside `packages/houzi_package/`. All customizations must happen in `assets/configurations/` or `lib/hooks_v2.dart` to maintain an easy core package upgrade path.
4.  **WordPress API & Taxonomy Alignment**: When configuring dynamic search filters, detail modules, or terms tabs, the agent must fetch real taxonomy metadata via WordPress REST API helper modules to ensure exact key alignment rather than guessing slugs.

## Customizing the Skill

If you have added custom features or modified the core app in ways an AI agent should know about, you can update the modules inside `.agents/skills/houzi/`. This ensures that the AI agent remains a reliable partner as your project evolves.

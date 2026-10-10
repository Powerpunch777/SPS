# SPS — An AI Development Workspace

**SPS (SonParkServer) is a Windows desktop application that brings project files, AI tools, and their work into one workspace.** Plugins let the workspace adapt to different projects, from game development to research.

[한국어](README.ko.md) · [Product website](https://redongames.com/sps/) · [Plugin SDK](https://github.com/Powerpunch777/sps-plugin-sdk) · [Soul Archer](https://github.com/Powerpunch777/school-arcade-unity)

**Status:** Active development / private feedback beta. This repository introduces the project and links to its documentation and developer tools; it does not contain the desktop application's source code. You can explore the project here without installing it or joining the beta.

## Why I am building it

Developing with several AI tools creates a practical problem: project files, conversations, execution results, and follow-up work can become separated. I wanted an environment where I could manage those pieces together and adapt the tools to the project I was making.

SPS is my ongoing attempt to build that environment. It keeps project folders on a host computer, connects selected AI tools, and records their runs and outputs. Plugins add the way work is organized, such as tasks, shared work rooms, or project memory.

## How it connects to Soul Archer

I used SPS as a working environment while developing [Soul Archer](https://github.com/Powerpunch777/school-arcade-unity), a Unity action game in which the player must stop moving to attack. Building the game exposed inconveniences and missing capabilities in the workspace, which gave me concrete reasons to improve SPS.

The two projects show different parts of my work: Soul Archer explores how game rules shape a player's decisions; SPS explores how development tools can support the process of making and revising a project. My work on SPS includes defining the environment I need, trying it on a real project, and using those experiences to guide improvements.

This is the part of the project that interests me most: when a tool becomes an obstacle, I can investigate the problem and try to improve the tool itself.

## What you can do with SPS

The descriptions below cover the **current development candidate and its optional extensions**, rather than a promise that every public installer includes every feature. The local candidate reviewed for this overview is **0.4.135**. A new workspace starts with a neutral foundation; enabling an extension adds its particular way of working.

### Bring different AI tools into the same project

SPS connects AI agents to selected project folders and records their execution. An agent can use a command-line coding tool, a local model, or a configured API service. This lets a project combine different kinds of assistance without requiring one model for every task.

The Node runtime includes discovery for **Claude Code, Codex CLI, Agy CLI, Gemini CLI, OpenCode CLI, Pi CLI, Ollama, and LM Studio**. Discovery identifies available tools and, for supported local model servers, model names; actual execution depends on the chosen adapter, account, and permissions. Optional Codex and Claude runtime packs provide another installation path for those execution adapters. They do not include a provider account or subscription.

For example, a project could use a coding agent for implementation and a local model for a separately configured task. The user chooses the available tools and the workflow that uses them.

### Organize conversations and delegate work with Team Workplane

**SPS Team Workplane** is an optional extension that adds persistent **Team Rooms**, focused **Task Rooms**, and a **Lead/Worker** workflow. A Team Room holds an ongoing project conversation; a Task Room keeps the discussion and result of a specific assignment together.

A configured Lead can create and assign tasks to permitted Workers, which return reports for follow-up and review. The interface includes task status, room context, attachments, and image or text file previews. It also exposes blocked work, such as a provider quota limit, so an interruption remains visible instead of being mistaken for completion.

In a game project, this could mean keeping the overall design discussion in one room while tracking a combat change and an art revision as separate assignments. This is an example of how the extension can be used, not a mandatory organization built into SPS.

### See progress and reports in one place

The **Dashboard** brings together workspace status and widgets contributed by enabled plugins. Team Workplane, for example, can summarize rooms, finite tasks, and reports waiting in a room. The **Inbox** collects plugin reports and notifications, with read and archive state for each user.

The common surfaces help answer two practical questions: “What is happening?” and “What needs my attention?” Plugins define what their reports mean and what actions they offer. A workspace can also select a plugin-provided navigation layout; SPS retains access to its settings and recovery tools if that plugin fails or is disabled.

### Preserve useful project context

**SPS Default Memory** is an optional local memory provider. It offers two distinct actions: recall approved information relevant to the current context, and propose a fact, decision, constraint, or preference for later review.

Memory can be scoped to a workspace, project, agent, room, or task. Checkpoints such as task completion or a conversation summary can create reviewable memory candidates. The provider does not silently rewrite approved memory or project files.

For a game project, a useful candidate might be a decision about the art style or a constraint discovered during playtesting. Keeping that information within the relevant project makes it easier to retrieve during later work.

### Find extensions and build missing tools

**Settings > Plugins** contains the Marketplace search and plugin details. Users can inspect a plugin's purpose, publisher information, declared capabilities, compatibility requirements, and release notes. Ordinary search works without an AI adapter; the **Marketplace Assistant** adds conversational search and comparison through an adapter the user selects. Its catalog tools are read-only: a recommendation does not install anything.

If no suitable extension exists, the bundled **Plugin Builder** provides an authoring workspace. The assistant works on a separate plugin project while SPS keeps the conversation, authoring steps, build/test evidence, and package references together. A separate **Plugin Preview** window runs a candidate in an isolated development workspace so it can be inspected without changing the production workspace.

The authoring foundation leads to a candidate `.spsplugin` package for a **Local Development Registry**, a folder the host explicitly chooses to trust. The host then reviews and activates the package in Settings. Builder itself cannot install, enable, update, or remove plugins. The [public SDK](https://github.com/Powerpunch777/sps-plugin-sdk) supplies authoring, validation, packaging, inspection, and registry tools.

### Connect specialist tools for a particular project

SPS's extension approach also supports tools that are specific to a domain. The source includes an **Image Worker Asset Tool**, an example connector for image-production workflows, with PixelLab operations for sprites, directional characters, animation, interface assets, and tilesets, plus an optional Meshy path for 3D assets.

The connector records generated files and their request/job references in an asset manifest. Its background job tracking can recover an existing request rather than immediately submitting it again, and its PixelLab preflight checks estimated usage against the available subscription balance. Generated files remain candidates for review before they become final game assets.

This is a separately configured connector example, not a default capability of every workspace. It requires the relevant external service credentials and usage allowance.

### Connect another computer while keeping control of project access

One computer acts as the **Host**, running the local SPS server and storing workspace data. A **Member** can join through an invitation and register a computer as a **Node**, which contributes selected AI execution tools after host approval. Host/Member collaboration uses Tailscale.

The host selects the project folders and approves access routes. Each computer keeps its own provider credentials and local model files; connecting a Node does not copy its AI account credentials to other members. This is useful when a second computer has an execution tool or local model that the project needs. Physical two-computer acceptance testing remains part of the release gate.

“Local-first” describes where SPS manages workspace data and project sources. A connected cloud AI service may still receive data during a task; SPS does not make every AI tool run offline.

### Inspect results, manage extensions, and move workspace data

SPS records runs, events, logs, and output artifacts so a user can inspect what happened. Plugin management includes package inspection, compatibility checks, workspace-specific activation, updates, and rollback controls. A package can be installed on the host while remaining disabled in a particular workspace; plugin updates require an explicit host action.

Two data-transfer paths serve different purposes:

- **Workspace packages** export supported workspace records and configuration into a new, separate workspace. They do not include local project files, credentials, or every plugin's private data format.
- **Host Transfer** exports SPS-managed server data, a fresh database backup, and Default Memory data when present. Restore is restricted to fresh-host setup; it does not overwrite an active host. External project folders need a separate backup, and accounts, source folders, and member connections must be reconnected after restoration.

Diagnostics and the automatic-update mechanism are also part of the desktop foundation. A working implementation of these tools is distinct from completing fresh-machine recovery and signed-release update testing.

## How the pieces fit together

A game-development workflow might begin with a host selecting the Unity project folder and connecting an AI coding tool. Enabling Team Workplane adds rooms and task tracking. Default Memory can preserve reviewed project decisions, while a specialist connector can produce art candidates for inspection. The dashboard, reports, and file previews help the user follow the work and decide what to revise next.

The **core** supplies the shared foundation: connections, project access, execution records, storage, and plugin management. **Extensions** supply the working method. That separation is why a game project can use a different arrangement from an app or research project without replacing the whole platform.

## Current status

SPS remains an active development project and private feedback beta. This overview was checked against the local **0.4.135 development candidate**, its product documents and implementation, and the older public source snapshot on **October 10, 2026**. Public source snapshots, preview installers, and official releases may contain different feature sets.

The development foundation includes the capabilities described above, with Team Workplane and Default Memory enabled only when selected. The image-production connector is an optional example integration. Marketplace and Builder implementation is present, but the complete authoring, preview, packaging, and catalog flows still require acceptance evidence for the exact release candidate.

Before the first complete product release, remaining validation includes fresh-machine host restoration, physical Host/Member testing across two computers, and signed Windows distribution with real automatic-update verification. Public self-service plugin uploads, community sales, payments, macOS, Linux, and browser-first use are outside the first-release scope.

The target environment is Windows 10/11 x64. Feedback-beta access requires an approved account and a supported AI execution setup; collaboration requires Tailscale. Check the [download page](https://redongames.com/download/) for build-specific availability and instructions.

[Getting started](docs/GETTING-STARTED.md) · [Product overview](docs/PRODUCT.md) · [Plugin development](docs/PLUGIN-DEVELOPMENT.md)

## Explore the project

- [Soul Archer](https://github.com/Powerpunch777/school-arcade-unity) — the game developed using SPS, with screenshots and an explanation of my role.
- [SPS Plugin SDK](https://github.com/Powerpunch777/sps-plugin-sdk) — public extension authoring and validation tools, licensed under Apache-2.0.
- [Official Extensions](https://github.com/Powerpunch777/SPS-Official-Extensions) — the first-party extension catalog.
- [Desktop Releases](https://github.com/Powerpunch777/SPS-Desktop-Releases) — installer releases and update metadata.

For feedback or beta access, contact [redongames1234@gmail.com](mailto:redongames1234@gmail.com). For private security reports, follow [SECURITY.md](SECURITY.md); do not include credentials or private project data in public issues.

This repository contains product documentation and brand assets. Public access does not grant a software or brand license. See [NOTICE.md](NOTICE.md).

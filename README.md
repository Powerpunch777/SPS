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

## What SPS does

| Capability | What it means in practice |
| --- | --- |
| Local project access | The host selects the folders the workspace can use. Existing projects stay in those folders. |
| AI tool connections | The workspace can use supported command-line AI agents, local models, or API-backed agents. |
| Execution records | Runs, events, logs, and output files make it possible to inspect what happened. |
| Plugins | Extensions add workflows, tools, interfaces, and memory behavior for a particular project. |
| Approved computer connections | Other computers can contribute selected AI runtimes through the Host/Member/Node connection model. |

“Local-first” describes where the workspace and project files are managed. A connected cloud AI provider may still receive data as part of a task; SPS does not make every AI tool run offline.

## A typical workflow

1. Create a workspace in SPS Desktop on a Windows host computer.
2. Select the project folders and AI tools it may use.
3. Describe the desired workflow to **Plugin Discovery & Builder**, or use an existing extension.
4. Review and enable the chosen plugins in **Settings > Plugins**.
5. Run project work, inspect the results, and revise the project or workflow as needed.

For collaboration, approved members connect privately through Tailscale. SPS Desktop is the supported application interface.

## A design decision: keep the core separate from the workflow

The **core** handles connections, project access, execution records, storage, and plugin management. **Plugins** decide how work is arranged: for example, task boards, roles, review steps, or long-term memory.

This separation lets the same foundation support different kinds of work without requiring every project to follow one fixed structure. It also creates a clear decision point: an assistant can recommend or draft an extension, while the host decides whether to install, activate, update, roll back, or remove it.

The [public Plugin SDK](https://github.com/Powerpunch777/sps-plugin-sdk) provides tools to create, validate, package, and inspect `.spsplugin` extensions. See the [plugin development guide](docs/PLUGIN-DEVELOPMENT.md) for details.

## Current scope and next steps

The documented implementation includes the Windows desktop app, local host, project-source access, runtime dispatch, execution records, plugin lifecycle and compatibility checks, local development registries, an export foundation, and automatic updates.

SPS is still being hardened for its first complete release. Work described in the product documentation includes host import and recovery, isolated plugin previews, a curated marketplace interface, signed Windows distribution, and repeated testing across two computers. Beta availability does not imply that all planned features are complete.

To try the feedback beta, you need Windows 10/11 x64, an approved Google account, and at least one supported AI runtime. Tailscale is required on computers used for Host/Member collaboration. Keep separate backups of important work.

[Installation and beta access](https://redongames.com/download/) · [Getting started](docs/GETTING-STARTED.md) · [Product overview](docs/PRODUCT.md)

## Explore the project

- [Soul Archer](https://github.com/Powerpunch777/school-arcade-unity) — the game developed using SPS, with screenshots and an explanation of my role.
- [SPS Plugin SDK](https://github.com/Powerpunch777/sps-plugin-sdk) — public extension authoring and validation tools, licensed under Apache-2.0.
- [Official Extensions](https://github.com/Powerpunch777/SPS-Official-Extensions) — the first-party extension catalog.
- [Desktop Releases](https://github.com/Powerpunch777/SPS-Desktop-Releases) — installer releases and update metadata.

For feedback or beta access, contact [redongames1234@gmail.com](mailto:redongames1234@gmail.com). For private security reports, follow [SECURITY.md](SECURITY.md); do not include credentials or private project data in public issues.

This repository contains product documentation and brand assets. Public access does not grant a software or brand license. See [NOTICE.md](NOTICE.md).

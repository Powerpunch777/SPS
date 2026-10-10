# SPS Product Overview

Reviewed on October 10, 2026 against local development candidate **0.4.135**.
The [main README](../README.md#what-you-can-do-with-sps) explains the features
through practical examples. This document describes their boundaries.

## Product idea

SPS is a Desktop control plane for AI-enabled work. It provides a stable
technical foundation while allowing each Workspace to choose its own workflow
through plugins.

The first product is designed for individuals and small teams using Windows
computers. One Host computer owns the SPS server and Workspace configuration.
Other approved computers may join as Members through Tailscale.

## Product principles

### Local control

The Host selects the project folders that become Workspace Sources. SPS does
not move those folders into a cloud service. A Member cannot choose or replace
the Host's source folder.

Each computer keeps its own CLI login, local model files, and provider
credentials. SPS exposes only approved runtime availability and protected
execution routes.

### Workflow neutrality

SPS Core does not require a Task, Room, role, approval, or memory model. Those
concepts are supplied by plugins. This keeps the platform useful beyond one
development domain or company structure.

### Explicit lifecycle control

An Assistant may search for or draft a plugin. The Host explicitly installs,
activates, updates, rolls back, disables, or removes it. A catalog result alone
does not execute code or alter the Workspace.

### Observable execution

Core primitives record runs, events, artifacts, logs, and jobs. Plugins can
give these primitives domain meaning while SPS keeps their technical
lifecycle observable.

## Main components

### SPS Desktop

The supported user interface. It handles sign-in, Host creation or joining,
Workspace navigation, settings, updates, diagnostics, and local Node setup.

Its common Workspace Shell, Dashboard, and Inbox can display work surfaces,
widgets, reports, and actions contributed by enabled plugins. A plugin can
provide a navigation layout, but cannot remove Core settings and recovery
access. Plugin failure returns the workspace to a neutral interface.

### Host

The computer that runs the local SPS server, stores SPS-managed Workspace
state, selects project sources, and controls technical membership and plugin
lifecycle.

### Member and Node

A Member is a person connected to the Host. A Node is an approved computer
that can contribute selected CLI or local AI runtimes. Plugins may define
additional work roles independently of these technical connection roles.

### Workspace

The technical container for sources, Agents, runs, artifacts, storage, and
enabled plugins. A new Workspace starts neutral.

### Plugins

Versioned extension packages that may contribute work surfaces, settings,
tools, jobs, workflow rules, memory providers, and domain integrations.

The development candidate includes the following first-party extensions:

- **Plugin Builder:** an authoring workspace that records project steps,
  build/test evidence, isolated Preview requests, and candidate packages.
  File changes use the agent's approved project tools; a recorded claim is
  not by itself a passed build. Installation remains a separate Host action.
- **Team Workplane:** optional Team Rooms, Task Rooms, Lead/Worker assignment,
  reports, file previews, and a dashboard contribution.
- **Default Memory:** optional scoped recall of approved information and
  reviewable memory proposals, including lifecycle checkpoints.

Core Marketplace provides catalog search, plugin details, and an Assistant
with read-only search/detail tools. Keyword search does not require an AI
adapter. This is separate from Plugin Builder's authoring workflow.

The source also includes the **Image Worker Asset Tool**, a separately
configured example connector for PixelLab image workflows and optional Meshy
3D workflows. It is not a default workspace feature.

## Data transfer

Workspace packages export supported Core-managed workspace records and
configuration. Import creates a separate new workspace. Local project files,
credentials, and arbitrary plugin-owned data are not included.

Host Transfer covers SPS-managed server data, a fresh database backup, and
Default Memory data when present. Restore runs only during fresh-Host setup
and does not merge with or replace an active Host. External project folders
need a separate backup; accounts, Nodes, and external sources must be
reconnected after restoration.

## First-release boundary

The initial supported environment is Windows 10/11 x64 with Tailscale for
private Host/Member networking. Browser-first use, macOS, Linux, public plugin
sales, payments, and unreviewed community uploads are outside the first
release.

SPS is currently a private feedback beta. The local development candidate,
public source snapshot, Preview installers, and official releases are not
interchangeable feature baselines. This documentation repository does not
contain the desktop application source; the SDK and extension contracts are
available separately.

Marketplace, Builder, Preview, Dashboard, Inbox, memory, transfer, and update
implementations are present in the reviewed candidate. Remaining release work
includes candidate-specific Marketplace and Builder acceptance evidence,
fresh-machine Host restore acceptance, physical two-computer Host/Member
testing, and signed Windows release/update verification. Their presence in
development does not establish that every public installer supports them.


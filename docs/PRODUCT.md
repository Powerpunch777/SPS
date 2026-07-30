# SPS Product Overview

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

## First-release boundary

The initial supported environment is Windows 10/11 x64 with Tailscale for
private Host/Member networking. Browser-first use, macOS, Linux, public plugin
sales, payments, and unreviewed community uploads are outside the first
release.

SPS is currently a private feedback beta. The product source remains private;
the plugin SDK and extension contracts are public.


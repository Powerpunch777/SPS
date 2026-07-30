# Getting Started

SPS is currently distributed as a private feedback beta for Windows.

## Before installing

Prepare:

- a Windows 10 or Windows 11 x64 computer;
- an approved Google account;
- Tailscale when two or more computers will collaborate;
- at least one supported CLI, local AI runtime, or API-backed Agent;
- a separate backup of important project files.

## Install

1. Open [redongames.com/download](https://redongames.com/download/).
2. Download the current stable feedback build.
3. Install and open SPS Desktop.
4. Complete Google sign-in inside the app.
5. Choose **Create Host** for the main computer or **Join Host** when an
   existing Host has invited you.

Preview installers are for installation testing. Do not use a Preview as the
only environment for important work.

## Create a Workspace

1. Create a Workspace on the Host.
2. Register one Initial Assistant from an available runtime.
3. Select Workspace Sources on the Host computer.
4. Open **Settings > Plugins**.
5. Use **Discovery & Builder** to discuss the workflow you need.
6. Review and explicitly activate the selected plugin for that Workspace.

A new Workspace has no built-in Task, Room, role, or memory policy. Those
surfaces appear only when the relevant plugin is enabled.

## Add a Member computer

1. Connect both computers to Tailscale.
2. The Host creates a full SPS invitation.
3. The Member installs the same SPS Desktop product and signs in with their
   own approved Google account.
4. The Member joins using the invitation and registers their computer as a
   Node.
5. The Host approves the Node and selects which Agent runtimes it may provide.

The Member cannot select the Host's project-source folder. Source access is
routed only after the Host approves it.

## Get help

Send beta access, product, or installation questions to
[redongames1234@gmail.com](mailto:redongames1234@gmail.com). Remove private
files, tokens, invitation codes, account details, and credentials from any
log or screenshot before sharing it.


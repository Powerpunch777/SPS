# Getting Started

SPS is currently distributed as a private feedback beta for Windows.

The current README describes development candidate **0.4.135**. Check the
download page for the status and instructions of the build actually offered;
an older public installer or Preview may expose different features.

## Before installing

Prepare:

- a Windows 10 or Windows 11 x64 computer;
- an approved Google account;
- Tailscale when two or more computers will collaborate;
- at least one supported CLI, local AI runtime, or API-backed Agent;
- a separate backup of important project files.

## Install

1. Open [redongames.com/download](https://redongames.com/download/).
2. Check whether the offered build is a feedback release or a Preview, and
   follow its build-specific instructions before downloading.
3. Install and open SPS Desktop.
4. Complete Google sign-in inside the app.
5. Choose **Create Host** for the main computer or **Join Host** when an
   existing Host has invited you.

Preview installers are for installation testing. Do not use a Preview as the
only environment for important work.

## Create a Workspace

1. Create a Workspace on the Host.
2. Select Workspace Sources on the Host computer.
3. Connect the supported AI runtime needed for your work.
4. Open **Settings > Plugins** to search the Marketplace and inspect details.
   Ordinary search works without an AI adapter; select an authorized adapter
   if you want conversational recommendations from the Marketplace Assistant.
5. Review and explicitly install or activate the selected plugin for that
   Workspace. Team Workplane and Default Memory are optional.
6. If a suitable extension does not exist, use Plugin Builder to work on a
   separate plugin project, inspect build/test evidence, and open an isolated
   Plugin Preview before preparing a candidate package for local review.

A new Workspace has no built-in Task, Room, role, or memory policy. Those
surfaces appear only when the relevant plugin is enabled.

Search and Builder do not automatically install or activate plugins. Older
builds may combine discovery and drafting under **Discovery & Builder**;
the reviewed candidate separates Marketplace search from Plugin Builder.

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


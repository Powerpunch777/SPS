# Plugin Development

SPS keeps its product Core private and exposes a public extension contract for
plugin authors.

## Public toolkit

The [SPS Plugin SDK](https://github.com/Powerpunch777/sps-plugin-sdk) provides:

- a plugin project initializer;
- Extension Profile compatibility validation;
- `.spsplugin` packaging and static inspection;
- capability and Core-primitive declarations;
- Ed25519 signing tools;
- local and static Registry publishing tools.

Use Profile v2 for new workflow-neutral SPS plugins. Profile v1 exists only as
a compatibility bridge for older packages.

## Development flow

1. Create the plugin in its own folder or repository.
2. Declare only the capabilities and Core primitives it needs.
3. Validate and package the plugin with the SDK.
4. Publish it to a Local Development Registry.
5. Add that registry explicitly in SPS Desktop.
6. Stage and activate the plugin in a development Workspace.
7. Inspect runs, artifacts, logs, and compatibility results before broader use.

SPS does not require official review for a Host to use a plugin they created
and trust locally. Mandatory package, hash, manifest, and compatibility checks
still apply.

## Distribution paths

### Personal or private

Use a Local Development Registry. The Host decides whether to trust the source
and which Workspace may activate the plugin.

### Official

Reviewed first-party packages are published through the signed
[SPS Official Extensions](https://github.com/Powerpunch777/SPS-Official-Extensions)
registry. Public self-service uploads, payments, and plugin sales are not part
of the first release.

## Licensing

The SDK is Apache-2.0. A plugin author chooses the license for their own
plugin, subject to the SDK license and any dependencies they use. The SDK
license does not grant rights to the SPS product source, SPS trademarks, logo,
official publisher identity, or signing infrastructure.


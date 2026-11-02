# Pipedream for Rakazo

A small, third-party [Agent Plugins 1.0.0](https://agent-plugins.org/) configuration for connecting Rakazo to Pipedream's hosted MCP service.

This is not an official Pipedream, Shopify, or Rakazo plugin. It contains only two manifests and this README: no proxy, server code, executable scripts, or embedded credentials.

## Install in Rakazo

1. Open **Integrations** → **+** → **From GitHub**.
2. Paste `https://github.com/Truly-Private/pipedream-rakazo-plugin` and choose **Preview**.
3. Check that the preview shows one server, `pipedream`, using `streamable-http` at `https://mcp.pipedream.net/v2`, with no skipped parts.
4. Choose **Connect**, then **Sign in** for the installed server. Complete Pipedream's browser authorization flow yourself.
5. In Pipedream, select the apps you want to enable. For Shopify, follow the [Shopify setup page](https://mcp.pipedream.com/app/shopify) and connect the intended store using an account with the required permissions.
6. Back in Rakazo, select a bot and choose **Use in this bot**. Start with a harmless read-only request and verify the result before allowing changes.

Pipedream's documentation currently notes that Pipedream MCP accounts are separate from ordinary pipedream.com accounts.

## Scope and authentication

The endpoint is Pipedream's shared, per-user MCP service—not a Shopify-only endpoint. Available tools depend on the apps and accounts you enable in Pipedream; other enabled apps may appear too. This repository does not restrict tools or grant access to a store.

Pipedream hosts the service and handles its app connections. You must review and approve the permissions requested during sign-in and app setup. Calls and data are handled by the connected services under their terms.

The manifests deliberately contain no `Authorization` header, token placeholders, OAuth client secrets, or store credentials. Do not add secrets to this public repository or to its endpoint URL. No local server or deployment is required.

## Validation and limits

The manifests were checked against the official Agent Plugins 1.0.0 JSON schemas and reviewed against Rakazo's current importer contract. This is configuration validation, **not** an end-to-end Rakazo test: live sign-in, Shopify authorization, and tool calls still need to be tested in your Rakazo installation.

If preview reports skipped parts or sign-in fails, stop and inspect the error rather than publishing credentials. Rakazo pins installations to a commit; after an update, preview and reinstall to use the new files.

## References

- [Rakazo plugin guide](https://github.com/elie222/rakazo/blob/main/docs/build-a-plugin.md)
- [Rakazo importer](https://github.com/elie222/rakazo/blob/main/packages/adapters/src/plugin-connectors.ts)
- [Pipedream MCP end-user guide](https://pipedream.com/docs/connect/mcp/users)
- [Pipedream Shopify setup](https://mcp.pipedream.com/app/shopify)
- [Plugin schema](https://agent-plugins.org/schemas/1.0.0/plugin.schema.json) · [MCP schema](https://agent-plugins.org/schemas/1.0.0/mcp.schema.json)

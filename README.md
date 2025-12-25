# Run an MCP Server on Vercel

## Usage

Update `api/server.ts` with your tools, prompts, and resources following the [MCP TypeScript SDK documentation](https://github.com/modelcontextprotocol/typescript-sdk/tree/main?tab=readme-ov-file#server).

## MCP Client Integration

When adding this server to an MCP client application, use your deployment URL followed by `/mcp`:

```
https://your-deployment-url.vercel.app/mcp
```

## App Metadata (Qordinate)

The `APP_METADATA` object in `api/server.ts` defines your app's display information for the Qordinate platform. This is exposed as an MCP resource at `app://metadata`.

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | App identifier |
| `title` | Yes | Display title |
| `subtitle` | Yes | Short tagline |
| `description` | Yes | Full description |
| `version` | Yes | Semantic version (e.g., "1.0.0") |
| `category` | Yes | App category |
| `location` | Yes | Primary region/country |
| `websiteUrl` | Yes | Official website |
| `privacyPolicyUrl` | Yes | Privacy policy link |
| `termsOfServiceUrl` | Yes | Terms of service link |
| `images` | Yes | Portrait screenshots (min 1) with `src`, `alt`, `type` |
| `icons` | Yes | App icons with `src` and `mimeType` |

Qordinate reads this resource to display your app in the marketplace.

## Example Tools

The template includes two example tools to get you started:

- **`roll_dice`** - Rolls an N-sided die (minimum 2 sides)
- **`get_weather`** - Gets current weather data (via an API) for a location using latitude, longitude, and city name

These tools demonstrate basic functionality and API integration patterns. Replace them with your own tools.

## Notes for running on Vercel

- Make sure you have [Fluid compute](https://vercel.com/docs/functions/fluid-compute) enabled for efficient execution. As of April 23, 2025, fluid compute is enabled by default for new projects.
- After enabling Fluid compute, open `vercel.json` and adjust max duration to 800 if you using a Vercel Pro or Enterprise account.

## Local dev

- Run `vercel dev` for local development
- Alternatively, integrate the system into the server framework of your choice.

## Sample Client

`script/test-client.mjs` contains a sample client to try invocations.

```sh
node scripts/test-client.mjs https://mcp-on-vercel.vercel.app
```

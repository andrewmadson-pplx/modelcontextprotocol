# Perplexity plugin for Hermes Agent

Connects [Hermes Agent](https://github.com/NousResearch/hermes-agent) to Perplexity's hosted MCP server at `https://api.perplexity.ai/mcp`. It adds four tools:

- `perplexity_search`: ranked web results from the Search API
- `perplexity_ask`: web-grounded answers with citations
- `perplexity_research`: in-depth research reports
- `perplexity_reason`: step-by-step reasoning over web results

## Install

```bash
hermes plugins install perplexity
```

Set your API key from the [API Console](https://console.perplexity.ai) in `~/.hermes/.env`:

```bash
PERPLEXITY_API_KEY=your_key_here
```

Hermes reads the key from the environment and sends it as a bearer token. The connection fails closed if the key is unset.

## Why a separate directory

The root `mcp.json` launches the local stdio server and relies on the client passing `PERPLEXITY_API_KEY` through the environment. Hermes forwards only allowlisted variables to stdio servers, so this directory points Hermes at the hosted server instead and sends the key as a header.

## Data

Queries and prompts the agent issues are sent to Perplexity's API and billed to your API key. See the [Perplexity API docs](https://docs.perplexity.ai) for details.

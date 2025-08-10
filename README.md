# Memory MCP Server - Cursor Rules

This repository contains the Cursor rule document for integrating the HPKV Memory MCP Server with Cursor IDE. The Memory MCP Server provides long-term memory capabilities for LLMs in Cursor, allowing AI assistants to remember conversations across sessions.

## What is this?

The Memory MCP Server implements the Model Context Protocol (MCP) to give LLMs true long-term memory. This rule document enables Cursor IDE to:

- Remember project structures and conventions across sessions
- Recall user preferences for coding style and patterns
- Reference previous explanations and decisions
- Avoid hallucinating non-existent code and functions
- Stop suggesting previously failed approaches

In short, it makes AI coding assistants in Cursor much more reliable by giving them access to persistent memory.

## Adding to Cursor IDE

1. Create a free [HPKV account](https://hpkv.io/signup) and create an API Key in Dashboard.
   
2. Edit your `mcp.json` file:

```json
{
  "mcpServers": {
    "hpkv-memory-server": {
      "url": "https://memory.hpkv.io/sse"
    }
  }
}
```

3. After adding the Memory MCP Server, you'll be prompted to login to your HPKV account. After that you can select the API key you generated.
  
4. Add the memory cursor rule to your project and set the rule type to `Always`.

### Adding MCP Memory to Claude Code

1. Use the following command:

```bash
claude mcp add -s user -t sse hpkv-memory-server https://memory.hpkv.io/sse
```
2. Add the rules to the end of your `CLAUDE.md` file

## Cursor Rule Document

The [memory_tool_usage_guide.mdc](./memory_tool_usage_guide.mdc) file contains the rules that instruct Cursor's AI how to properly use the memory tools. It includes:

- Guidelines for when to search memory before responding
- Patterns for storing important information
- Best practices for memory retrieval
- Naming conventions for organizing memories

## OAuth Troubleshooting

In certain situations, `mcp-remote` might have trouble refreshing your token and it consitantly generates new Client IDs that lead to the loop of trying to register a new Client ID, openning API Key selection page and goingback to generating a new Client ID. To fix this, disable the MCP server in Cursor, kill all `mcp-remote` processes and clear the `.mcp-auth` folder with a command similar to `pkill -f mcp-remote && rm -rf ~/.mcp-auth` and then re-enable it in Cursor. This should fix any authentication issue you were experiencing. 

## Learn More

For more information, check out our [blog post about Memory MCP](https://hpkv.io/blog/2025/04/mcp-memory-with-hpkv) and the [HPKV documentation](https://hpkv.io/docs).

Find HPKV Memory MCP on [MCP Hub](https://mcphub.com/mcp-servers/hpkv-io/memory-mcp-server).

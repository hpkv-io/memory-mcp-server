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

## How to add to Cursor IDE

1. Create a free [HPKV account](https://hpkv.io/signup)
   
2. Edit your `mcp.json` file:

```json
{
  "mcpServers": {
    "hpkv-memory-server": {
      "command": "npx",
      "args": ["mcp-remote", "https://memory-mcp.hpkv.io/sse"]
    }
  }
}
```

3. After adding the Memory MCP Server, you'll be prompted to login to your HPKV account. Follow the instructions to connect your API key.
  
4. Add the memory cursor rule to your project

## Cursor Rule Document

The [memory_tool_usage_guide.mdc](./memory_tool_usage_guide.mdc) file contains the rules that instruct Cursor's AI how to properly use the memory tools. It includes:

- Guidelines for when to search memory before responding
- Patterns for storing important information
- Best practices for memory retrieval
- Naming conventions for organizing memories

## Learn More

For more information, check out our [blog post about Memory MCP](https://hpkv.io/blog/2025/04/mcp-memory-with-hpkv) and the [HPKV documentation](https://hpkv.io/docs).

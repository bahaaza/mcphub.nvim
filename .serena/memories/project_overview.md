# Project Overview: mcphub.nvim

## Purpose

**mcphub.nvim** is a Neovim plugin that acts as an MCP (Model Context Protocol) client. It seamlessly integrates MCP servers into the Neovim editing workflow, providing an intuitive interface for managing, testing, and using MCP servers with popular AI chat plugins.

## Key Features

- **MCP Capabilities**: Full support for Tools, Resources, Resource Templates, and Prompts
- **Transports**: Supports Streamable-HTTP, SSE, and STDIO
- **Authentication**: OAuth (with PKCE) and Headers-based auth for remote servers
- **Chat Plugin Integrations**:
  - Avante.nvim
  - CodeCompanion.nvim
  - CopilotChat.nvim
- **Marketplace**: Browse and install verified MCP servers
- **Workspace Management**: Project-local configs with automatic detection and merging
- **Native Lua MCP Servers**: Write tools, resources, and prompts directly in Lua

## Architecture

mcphub.nvim is a **frontend** to the [mcp-hub](https://github.com/ravitemer/mcp-hub) backend:
- The backend (Node.js) watches `servers.json`, starts/stops servers, and hosts an Express server
- The plugin communicates via REST API endpoints:
  - `/api/health` - Server health/status
  - `/api/events` - SSE for real-time events
  - `/api/servers/*` - Tools, resources, prompts

## Tech Stack

- **Language**: Lua (Neovim plugin)
- **Backend**: Node.js (mcp-hub)
- **Testing**: Mini.Test (from mini.nvim)
- **Dependencies**:
  - plenary.nvim (async jobs, curl, etc.)
  - nvim-treesitter (optional, for syntax)

## Target Neovim Version

- Minimum: Neovim 0.8.0+
- Docs generated for: Neovim 0.10.0

## Related Repositories

- **mcp-hub** (backend): https://github.com/ravitemer/mcp-hub
- **MCP Protocol**: https://modelcontextprotocol.io/

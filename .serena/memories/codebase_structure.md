# Codebase Structure

## Root Files

| File | Purpose |
|------|---------|
| `Makefile` | Build commands (format, test, docs) |
| `stylua.toml` | Lua formatter configuration |
| `selene.toml` | Lua linter configuration |
| `.luarc.json` | Lua language server configuration |
| `flake.nix` | Nix flake for development |

## Directory Structure

```
mcphub.nvim/
├── plugin/
│   └── mcphub.lua          # Plugin entry point, user command setup
├── lua/mcphub/
│   ├── init.lua            # Main module, setup() function
│   ├── hub.lua             # Core MCPHub class, server communication
│   ├── state.lua           # Global state management
│   ├── config.lua          # Default configuration, type definitions
│   ├── types.lua           # LuaDoc type annotations
│   ├── health.lua          # :checkhealth support
│   ├── ui/                 # User interface components
│   │   ├── init.lua        # UI manager
│   │   ├── views/          # Different UI views (main, logs, config, etc.)
│   │   └── capabilities/   # Capability-specific UI (tools, prompts, etc.)
│   ├── extensions/         # Chat plugin integrations
│   │   ├── avante/         # Avante.nvim integration
│   │   ├── codecompanion/  # CodeCompanion.nvim integration
│   │   ├── copilotchat/    # CopilotChat.nvim integration
│   │   ├── lualine.lua     # Lualine status component
│   │   └── shared.lua      # Shared extension utilities
│   ├── native/             # Native Lua MCP server implementations
│   │   ├── neovim/         # Built-in Neovim tools
│   │   │   ├── files/      # File operations
│   │   │   │   └── edit_file/  # Advanced file editing
│   │   │   ├── lsp.lua     # LSP-related tools
│   │   │   └── terminal.lua    # Terminal operations
│   │   └── mcphub/         # MCP Hub specific tools
│   └── utils/              # Utility modules
│       ├── errors.lua      # Error handling
│       ├── log.lua         # Logging
│       ├── validation.lua  # Input validation
│       ├── handlers.lua    # Response handlers
│       ├── workspace.lua   # Workspace config detection
│       └── config_manager.lua  # Config file management
├── tests/
│   ├── helpers.lua         # Test helper utilities
│   ├── config.lua          # Test configuration
│   ├── state.lua           # Mock state for tests
│   └── native/neovim/files/edit_file/  # Edit file tests
├── scripts/
│   ├── minimal_init.lua    # Minimal init for testing
│   └── vimdoc.md           # Source for generating docs
├── doc/
│   └── mcphub.txt          # Generated vim help docs
└── .github/                # GitHub workflows
```

## Key Classes/Modules

| Module | Class/Table | Purpose |
|--------|-------------|---------|
| `lua/mcphub/init.lua` | `M` | Main API (setup, get_hub_instance, on, off) |
| `lua/mcphub/hub.lua` | `MCPHub` | Hub class, server communication |
| `lua/mcphub/state.lua` | `State` | Global plugin state |
| `lua/mcphub/config.lua` | `defaults` | Default configuration |
| `lua/mcphub/ui/init.lua` | `UI` | UI manager |

# Code Style and Conventions

## Lua Formatting (stylua.toml)

| Setting | Value |
|---------|-------|
| Column width | 120 |
| Indent type | Spaces |
| Indent width | 4 |
| Line endings | Unix (LF) |
| Quote style | AutoPreferDouble |
| Call parentheses | Required |
| Sort requires | Enabled |

## Linting (selene.toml)

- Standard: `neovim`
- Allowed rules: `global_usage`, `if_same_then_else`, `incorrect_standard_library_use`, `mixed_table`, `multiple_statements`

## Type Annotations

- Use **LuaDoc/EmmyLua** style annotations (`---@class`, `---@param`, `---@return`, `---@field`)
- Define types in `lua/mcphub/types.lua` for shared types
- Use `---@meta` at top of type definition files

### Examples

```lua
---@class MCPHub.Config
---@field port number Default port for MCP Hub
---@field config string Path to servers.json

---@param opts table Configuration options
---@return MCPHub.Hub
function MCPHub:new(opts)
```

## Module Pattern

```lua
local M = {}

-- Private functions (local)
local function private_helper()
end

-- Public functions
function M.public_function()
end

return M
```

## Class Pattern (OOP)

```lua
---@class MyClass
local MyClass = {}
MyClass.__index = MyClass

---@return MyClass
function MyClass:new(opts)
    local instance = setmetatable({
        field = opts.field,
    }, MyClass)
    return instance
end

function MyClass:method()
    -- ...
end

return MyClass
```

## Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Modules | lowercase | `mcphub`, `config` |
| Classes | PascalCase | `MCPHub`, `State` |
| Functions | snake_case | `get_hub_instance`, `setup_plugin` |
| Constants | SCREAMING_SNAKE_CASE | `SHUTDOWN_DELAY`, `TOOL_TIMEOUT` |
| Private | underscore prefix | `_private_method`, `_internal_state` |
| Boolean | `is_`, `has_`, `can_` prefix | `is_ready`, `has_error` |

## Vim API Preferences

- Prefer `vim.api.*` methods over Vimscript where possible
- Use `vim.fn.*` for functions without direct API equivalent
- Use `vim.cmd()` sparingly, prefer Lua alternatives

## Error Handling

- Use the `mcphub.utils.errors` module for error creation
- Log errors via `mcphub.utils.log`
- Return `nil, error_message` pattern for recoverable errors

## Imports

- Sort requires (enforced by stylua)
- Use local requires at file top
- Lazy-load heavy modules when appropriate

```lua
local Error = require("mcphub.utils.errors")
local log = require("mcphub.utils.log")
local utils = require("mcphub.utils")
```

## Comments

- Use `--` for single-line comments
- Use multi-line for complex explanations
- Document public functions with LuaDoc

## File Organization

1. Module-level requires
2. Local constants
3. Type definitions (if in same file)
4. Private helper functions
5. Public module table (M = {})
6. Public function definitions
7. Return statement

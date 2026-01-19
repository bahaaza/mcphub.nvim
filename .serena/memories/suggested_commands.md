# Suggested Commands

## Development Commands

### Formatting
```bash
# Format all Lua files with stylua
make format

# Direct stylua command
stylua tests/ lua/ -f ./stylua.toml
```

### Testing
```bash
# Run all tests
make test

# Run specific test file
make test_file FILE=tests/native/neovim/files/edit_file/test_block_locator.lua

# Direct nvim test command
nvim --headless --noplugin -u ./scripts/minimal_init.lua -c "lua MiniTest.run()"
```

### Documentation
```bash
# Generate vim help docs from markdown
make docs
```

### All (format + test + docs)
```bash
make all
```

### Dependencies
```bash
# Clone test dependencies (plenary, treesitter, mini.nvim, panvimdoc)
make deps
```

## Linting (Manual)

```bash
# Lua linter (if installed)
selene lua/

# Lua language server check (via nvim)
nvim --headless -c "lua require('vim.lsp.log').set_level('ERROR')" -c "e lua/mcphub/init.lua" -c "quit"
```

## Git Commands

```bash
# Status
git status

# Diff current changes
git diff

# Staged changes
git diff --staged
```

## System Utilities (macOS/Darwin)

```bash
# List files
ls -la

# Find files
find . -name "*.lua" -type f

# Search in files
grep -r "pattern" lua/

# Watch file changes (requires fswatch)
fswatch -o lua/ | xargs -n1 -I{} make format
```

## Plugin Testing in Neovim

```vim
" Toggle MCP Hub UI
:MCPHub

" Check health
:checkhealth mcphub
```

## Development Workflow

1. Make changes to Lua files
2. Run `make format` to format code
3. Run `make test` to verify tests pass
4. Run `make docs` if documentation changed
5. Commit changes

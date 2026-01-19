# Task Completion Checklist

## Before Marking a Task Complete

### Code Quality

- [ ] **Format code**: Run `make format` (stylua)
- [ ] **No syntax errors**: Code loads without errors
- [ ] **Type annotations**: Added/updated LuaDoc annotations for new/changed functions
- [ ] **Follow conventions**: Match existing code patterns and naming

### Testing

- [ ] **Run tests**: `make test` passes
- [ ] **Add tests**: New functionality has corresponding tests in `tests/`
- [ ] **Test specific file**: `make test_file FILE=path/to/test.lua` for focused testing

### Documentation

- [ ] **Update docs**: If behavior changed, update `scripts/vimdoc.md`
- [ ] **Generate docs**: Run `make docs` to regenerate `doc/mcphub.txt`
- [ ] **Code comments**: Complex logic is documented

### Final Verification

- [ ] **Manual test**: Test in actual Neovim (`:MCPHub`, use with chat plugin)
- [ ] **Check logs**: No unexpected errors in plugin logs
- [ ] **Git status**: Review changed files with `git diff`

## Quick Commands

```bash
# All-in-one
make all

# Or individually
make format
make test
make docs
```

## Common Issues to Check

1. **Trailing whitespace**: stylua handles this
2. **Unused variables**: Check linter warnings
3. **Missing requires**: Test in fresh Neovim instance
4. **Breaking changes**: Check usages of modified functions

## PR Checklist (from CONTRIBUTING.md)

- [ ] Clear description
- [ ] Related issue references
- [ ] Screenshots/gifs if UI changes
- [ ] Log examples if relevant
- [ ] All tests pass
- [ ] Code formatted
- [ ] Docs generated

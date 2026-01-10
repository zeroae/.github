# CLAUDE.md - ZeroAE Organization AI Assistant Instructions

This file provides organization-wide conventions and guidelines for AI assistants working on ZeroAE projects.

## Commit Message Format

All ZeroAE projects MUST follow the [Conventional Commits](https://www.conventionalcommits.org/) format with emojis.

See [detailed commit conventions](docs/commits.md) for complete guidelines and examples.

### Quick Reference

```
<emoji> <type>(<scope>): <description>
```

**Common types:**
- ✨ `feat` - New feature
- 🐛 `fix` - Bug fix
- 📝 `docs` - Documentation
- 🎨 `style` - Code formatting
- ♻️ `refactor` - Code refactoring
- ⚡ `perf` - Performance improvement
- ✅ `test` - Tests
- 🔧 `chore` - Maintenance
- 🔨 `build` - Build system
- 👷 `ci` - CI/CD
- 🚀 `deploy` - Deployment
- 🔒 `security` - Security fixes

## Code Style

- Follow project-specific linting and formatting tools
- Use type hints where applicable (Python, TypeScript)
- Write clear, self-documenting code
- Add docstrings/comments only where logic isn't self-evident

## General Principles

1. **Simplicity over cleverness** - Prefer straightforward solutions
2. **YAGNI** - Don't add features or abstractions until needed
3. **Security awareness** - Watch for OWASP top 10 vulnerabilities
4. **Backwards compatibility** - Consider migration paths for breaking changes
5. **Test coverage** - Write tests for new features and bug fixes

## Project Structure

Individual projects may extend these guidelines with project-specific instructions in their own `CLAUDE.md` files.

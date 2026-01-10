# Commit Conventions

All ZeroAE projects follow the [Conventional Commits](https://www.conventionalcommits.org/) format with emojis for better visual scanning in git logs.

## Format

```
<emoji> <type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

## Types and Emojis

| Emoji | Type | Description | Example |
|-------|------|-------------|---------|
| ✨ | `feat` | New feature | `✨ feat(api): add rate limiting middleware` |
| 🐛 | `fix` | Bug fix | `🐛 fix(auth): correct token expiration handling` |
| 📝 | `docs` | Documentation only | `📝 docs(readme): update installation instructions` |
| 🎨 | `style` | Code style/formatting | `🎨 style: format with black` |
| ♻️ | `refactor` | Code refactoring | `♻️ refactor(parser): simplify validation logic` |
| ⚡ | `perf` | Performance improvement | `⚡ perf(db): optimize query with indexes` |
| ✅ | `test` | Add/update tests | `✅ test(api): add rate limit edge cases` |
| 🔧 | `chore` | Maintenance tasks | `🔧 chore: update dependencies` |
| 🔨 | `build` | Build system changes | `🔨 build: configure hatch-vcs for versioning` |
| 👷 | `ci` | CI/CD changes | `👷 ci: add GitHub Actions workflow` |
| 🚀 | `deploy` | Deployment related | `🚀 deploy: add Kubernetes manifests` |
| 🔒 | `security` | Security fixes | `🔒 security: sanitize user input` |
| ⬆️ | `deps` | Dependency updates | `⬆️ deps: bump boto3 to 1.34.0` |
| ⬇️ | `downgrade` | Dependency downgrades | `⬇️ downgrade: revert boto3 to stable version` |
| 🔀 | `merge` | Merge branches | `🔀 merge: pull request #42 from feature-branch` |
| 🗑️ | `remove` | Remove code/files | `🗑️ remove: deprecated legacy API endpoints` |

## Guidelines

### 1. Type (Required)

Always specify a type from the table above. The type communicates the intent of the change.

```bash
# Good
✨ feat(auth): add OAuth2 support
🐛 fix: handle null pointer exception

# Bad
add OAuth2 support  # Missing type and emoji
update code  # Too vague
```

### 2. Scope (Optional)

Use scope to indicate the affected component, module, or area of the codebase. Project-specific scopes should be documented in each project's `CLAUDE.md`.

```bash
# With scope
✨ feat(api): add pagination support
🐛 fix(database): prevent connection leak

# Without scope (when change is global)
🎨 style: format all files with prettier
🔧 chore: update all dependencies
```

### 3. Description (Required)

- Use **imperative mood** (present tense)
  - ✅ "add feature" not "added feature"
  - ✅ "fix bug" not "fixes bug"
  - ✅ "remove code" not "removing code"
- Keep first line **≤72 characters**
- Be specific and descriptive
- Start with lowercase (after the type)

```bash
# Good
✨ feat(api): add rate limiting with token bucket algorithm
🐛 fix(parser): handle edge case for empty arrays

# Bad
✨ feat(api): Added new feature  # Wrong tense, too vague
🐛 fix: fix bug  # Too vague
```

### 4. Body (Optional)

Use the body to provide additional context:
- **Why** the change was made
- **What** alternatives were considered
- **How** complex changes work
- Link to related issues/discussions

```bash
♻️ refactor(cache): migrate from Redis to in-memory LRU

The Redis dependency was causing deployment complexity and
most use cases don't require persistent caching. In-memory
LRU cache reduces latency and simplifies infrastructure.

Benchmarks show 40% improvement in cache hit latency.

See #123 for performance comparison.
```

### 5. Footer (Optional)

Use footers for:
- **Breaking changes**: `BREAKING CHANGE: description`
- **Issue references**: `Fixes #123`, `Closes #456`, `Relates to #789`
- **Co-authors**: `Co-Authored-By: Name <email>`
- **Reviewers**: `Reviewed-By: Name <email>`

```bash
✨ feat(api)!: change authentication to JWT-only

BREAKING CHANGE: Session-based auth removed. All clients
must migrate to JWT tokens. See migration guide in docs/auth.md

Fixes #234
Closes #456
```

### 6. Breaking Changes

Indicate breaking changes with `!` after the type/scope **and** include a `BREAKING CHANGE:` footer:

```bash
# Method 1: ! in subject
✨ feat(api)!: remove deprecated v1 endpoints

BREAKING CHANGE: All v1 endpoints removed. Use v2 API instead.

# Method 2: Only in footer (less visible)
♻️ refactor(config): restructure configuration schema

BREAKING CHANGE: Configuration file format changed.
Run `tool migrate-config` to update existing configs.

Closes #789
```

## Examples

### Feature Addition

```bash
✨ feat(limiter): add hierarchical rate limiting

Implements parent-child entity relationships where child
limits cascade to parent. Enables use cases like:
- API key limits rolling up to project limits
- User limits within organization limits

Uses DynamoDB GSI for efficient parent lookups.

Fixes #45
```

### Bug Fix

```bash
🐛 fix(bucket): prevent integer overflow in refill calculation

Large refill periods caused overflow when calculating
token accumulation. Now using checked arithmetic and
capping at bucket capacity.

Fixes #123
```

### Documentation

```bash
📝 docs(api): add examples for custom limit types

Includes examples for:
- Per-user rate limits
- Hierarchical limits
- Resource-based capacity tracking

Closes #67
```

### Refactoring

```bash
♻️ refactor(schema): simplify DynamoDB key structure

Before:
- Separate methods for entity/bucket/limit keys
- Redundant GSI key builders

After:
- Single unified key builder
- GSI keys derived from primary keys

No functional changes, 30% reduction in schema.py LOC.
```

### Performance Improvement

```bash
⚡ perf(repository): batch DynamoDB operations

- Use BatchGetItem instead of sequential GetItem calls
- Reduces API calls by 10x for multi-entity checks
- 60% latency improvement in benchmarks

Benchmark results in docs/performance.md
```

### Multiple Changes

```bash
🔨 build: modernize Python packaging

- Migrate from setup.py to pyproject.toml
- Use hatch-vcs for automatic versioning
- Add development dependencies group
- Configure ruff for linting

Fixes #89
```

### Security Fix

```bash
🔒 security(api): sanitize DynamoDB filter expressions

User input in filter expressions could lead to expression
injection. Now using parameterized expressions with
ExpressionAttributeValues.

Thanks to @security-researcher for responsible disclosure.

CVE-2024-XXXXX
```

## Best Practices

1. **Commit often**: Make small, focused commits
2. **One concern per commit**: Don't mix refactoring with features
3. **Test before committing**: Ensure tests pass
4. **Review your diff**: Use `git diff --staged` before committing
5. **Use conventional types**: Don't invent new types
6. **Reference issues**: Link commits to issues/PRs when relevant
7. **Write for reviewers**: Your commit message is documentation

## Tools

### Git Commit Template

Add to `.git/config` or `~/.gitconfig`:

```ini
[commit]
    template = ~/.gitmessage
```

Create `~/.gitmessage`:

```
# <emoji> <type>(<scope>): <description>
# 
# [optional body]
# 
# [optional footer(s)]
#
# Types: feat, fix, docs, style, refactor, perf, test, chore, build, ci, deploy, security, deps, merge, remove
# Remember: Use imperative mood, keep first line ≤72 chars
```

### Commit Message Linter

Use [commitlint](https://commitlint.js.org/) with conventional commits config:

```bash
npm install --save-dev @commitlint/{cli,config-conventional}
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

Add git hook with [husky](https://typicode.github.io/husky/):

```bash
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit ${1}'
```

## References

- [Conventional Commits Specification](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
- [Angular Commit Message Format](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#commit)

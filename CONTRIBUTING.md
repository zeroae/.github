# Contributing to ZeroAE Projects

Thank you for your interest in contributing! This guide applies to all ZeroAE repositories.

## Reporting Issues

### Issue Types

Choose the appropriate issue type when reporting:

| Type | Use For |
|------|---------|
| **Bug** | Something isn't working as expected |
| **Feature** | Request new functionality |
| **Task** | Documentation, testing, maintenance work |
| **Epic** | Major feature spanning multiple issues |
| **Theme** | Strategic initiative spanning multiple epics |

### Issue Hierarchy

We organize work using GitHub's sub-issues feature:

```
Theme          Strategic initiative (quarterly/multi-quarter)
└── Epic       Bounded feature (fits in one milestone)
    └── Issue  Feature, bug, or task
```

**Guidelines:**
- **Themes** span multiple milestones and contain Epics as sub-issues
- **Epics** belong to ONE milestone and contain issues as sub-issues
- **Milestones** represent releases (v1.0.0, v2.0.0) and are time-boxed

### Milestones

Milestones represent releases. Maintainers assign issues to milestones based on release planning - contributors don't need to set them.

### Before Opening an Issue

1. Search existing issues to avoid duplicates
2. Check the project documentation
3. For bugs, gather reproduction steps and environment details

## Pull Requests

### Workflow

1. **Fork and clone** the repository
2. **Create a branch** from `main`:
   ```bash
   git checkout -b feat/your-feature-name
   ```
3. **Make changes** following project conventions
4. **Test** your changes locally
5. **Commit** using [commit conventions](https://github.com/zeroae/.claude/blob/main/commits.md)
6. **Push** and open a pull request

### Branch Naming

Use prefixes that match commit types:

| Prefix | Use For |
|--------|---------|
| `feat/` | New features |
| `fix/` | Bug fixes |
| `docs/` | Documentation |
| `refactor/` | Code refactoring |
| `test/` | Test additions/changes |
| `chore/` | Maintenance tasks |

### PR Guidelines

- Keep PRs focused on a single concern
- Reference related issues (e.g., "Fixes #123")
- Ensure CI checks pass before requesting review
- Respond to review feedback promptly

## Commit Conventions

All ZeroAE projects use [Conventional Commits](https://www.conventionalcommits.org/) with emoji prefixes. See the full guide in [zeroae/.claude](https://github.com/zeroae/.claude/blob/main/commits.md)

**Quick reference:**

```bash
✨ feat(scope): add new feature
🐛 fix(scope): fix bug
📝 docs(scope): update documentation
♻️ refactor(scope): refactor code
✅ test(scope): add tests
🔧 chore(scope): maintenance task
```

## Code Style

Each project documents its specific linting and formatting requirements in its own `CLAUDE.md` or `README.md`. Common tools across ZeroAE projects:

- **Python**: `ruff` for linting/formatting, `mypy` for type checking
- **JavaScript/TypeScript**: `eslint`, `prettier`

Run linting before committing to catch issues early.

## Getting Help

- **Questions**: Open a Discussion (if enabled) or an Issue
- **Security issues**: See [SECURITY.md](SECURITY.md) for responsible disclosure

## License

By contributing, you agree that your contributions will be licensed under the same license as the project.

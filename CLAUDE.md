# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is the zeroae organization's `.github` repository containing organization-wide community health files that apply to all zeroae repositories (e.g., CODE_OF_CONDUCT.md, CONTRIBUTING.md, issue templates, workflow templates).

For Claude Code-specific instructions and conventions used across zeroae projects, see [zeroae/.claude](https://github.com/zeroae/.claude).

## Issue Hierarchy

ZeroAE uses this work item hierarchy:

```
Issues (type: Theme) →  Strategic initiatives (quarterly/multi-quarter)
    ↓ contains (via sub-issues)
Issues (type: Epic)  →  Bounded features (fits in one milestone)
    ↓ contains (via sub-issues)
Issues (type: *)     →  Features, bugs, tasks
    ↓ grouped by
Milestones           →  Releases (version-based, time-boxed)
```

**Key principles:**
- **Themes** = strategic initiatives spanning multiple epics and milestones
- **Epics** = bounded features with clear success criteria, belong to ONE milestone
- **Milestones** = releases (v1.0.0, v2.0.0), version-based and time-boxed
- **Sub-issues** = use GitHub's native sub-issues to link the hierarchy
- **GitHub Projects** = optional, for roadmap visualization across themes

**Example hierarchy:**

```
Theme: "Enterprise Readiness"                    ← Strategic goal
├── Epic: "Permission Boundaries"                ← Fits in v1.2.0 milestone
│   ├── Feature: Add --permission-boundary flag
│   ├── Feature: Add --role-name-format flag
│   └── Task: Enterprise deployment docs
├── Epic: "Audit Logging"                        ← Fits in v1.2.0 milestone
│   ├── Feature: Audit event schema
│   └── Feature: CLI audit command
└── Epic: "SSO Integration"                      ← Fits in v1.3.0 milestone
    └── ...

Milestone: v1.2.0                                ← Time-boxed release
├── Epic: Permission Boundaries (from Theme above)
├── Epic: Audit Logging (from Theme above)
└── Bug: Fix token overflow                      ← Standalone, no Epic
```

## Issue Templates

Organization-wide templates (repos can override with their own):

| Template | Type | Use For |
|----------|------|---------|
| `theme.yml` | Theme | Strategic initiatives spanning multiple epics |
| `epic.yml` | Epic | Major features spanning multiple issues |
| `feature.yml` | Feature | Requesting new functionality |
| `bug.yml` | Bug | Reporting unexpected behavior |
| `task.yml` | Task | Documentation, testing, maintenance work |

Repos that need project-specific fields (like Area dropdowns) should create their own `ISSUE_TEMPLATE/` folder.

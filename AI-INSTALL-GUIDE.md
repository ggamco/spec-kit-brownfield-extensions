# AI Agent Installation Guide

This document provides executable instructions for AI agents to install the Brownfield Bootstrap Extension.

## Prerequisites

- spec-kit installed and configured
- Git available
- Target project directory identified

## Installation Steps

### Step 1: Clone Extension Repository

```bash
git clone https://github.com/wcpaxx/spec-kit-brownfield-extensions.git /tmp/brownfield-ext
```

### Step 2: Install Extension

**Option A: Using spec-kit Extension System (Recommended)**

```bash
specify extension add --dev /tmp/brownfield-ext
```

**Option B: Manual Installation**

Copy the bootstrap command to project:

```bash
mkdir -p .claude/commands
cp /tmp/brownfield-ext/commands/bootstrap.md .claude/commands/speckit.brownfield.bootstrap.md
cp /tmp/brownfield-ext/commands/bootstrap-cn.md .claude/commands/speckit.brownfield.bootstrap-cn.md
```

### Step 3: Install Skills

Copy skills to project:

```bash
mkdir -p .claude/skills
cp -r /tmp/brownfield-ext/skills/brownfield-skills .claude/skills/
cp -r /tmp/brownfield-ext/skills/brownfield-ears .claude/skills/
```

### Step 4: Verify Installation

```bash
ls .claude/commands/speckit.brownfield*.md
ls .claude/skills/brownfield-*/SKILL.md
```

Expected output:
- `speckit.brownfield.bootstrap.md` and `speckit.brownfield.bootstrap-cn.md` in commands
- `SKILL.md` files in both `brownfield-skills` and `brownfield-ears` directories

### Step 5: Cleanup

```bash
rm -rf /tmp/brownfield-ext
```

## Post-Installation

After installation, the following are available:

### Commands
- `/speckit.brownfield.bootstrap` - Initialize SDD for brownfield projects
- `/speckit.brownfield.bootstrap-cn` - Chinese version

### Skills
- `brownfield-skills` - Generate project expertise skills
- `brownfield-ears` - Convert requirements to EARS format

## Usage

1. Run `/speckit.brownfield.bootstrap` in your existing project
2. Review generated `.specify/` configuration
3. Use standard SDD workflow: `/speckit.specify` → `/speckit.plan` → `/speckit.tasks`

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Command not found | Ensure files are in `.claude/commands/` |
| Skills not loading | Check `.claude/skills/` directory structure |
| Permission denied | Run with appropriate permissions |

## Notes

- Commands use aliases for backward compatibility
- Skills follow Claude Code best practices
- Chinese versions available for all components

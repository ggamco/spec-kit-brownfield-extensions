# Extension AI Installation Guide

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
specify extension add --dev /tmp/brownfield-ext/extension
```

**Option B: Manual Installation**

Copy the init commands to project:

```bash
mkdir -p .claude/commands
cp /tmp/brownfield-ext/extension/commands/init.md .claude/commands/speckit.brownfield-bootstrap.init.md
cp /tmp/brownfield-ext/extension/commands/init-cn.md .claude/commands/speckit.brownfield-bootstrap.init-cn.md
```

### Step 3: Verify Installation

```bash
ls .claude/commands/speckit.brownfield-bootstrap*.md
```

Expected output:
- `speckit.brownfield-bootstrap.init.md` and `speckit.brownfield-bootstrap.init-cn.md` in commands

### Step 4: Cleanup

```bash
rm -rf /tmp/brownfield-ext
```

## Post-Installation

After installation, the following commands are available:

| Command | Description |
|---------|-------------|
| `/speckit.brownfield-bootstrap.init` | Initialize SDD for brownfield projects |
| `/speckit.brownfield-bootstrap.init-cn` | Chinese version |

## Usage

1. Navigate to your existing project
2. Run `/speckit.brownfield-bootstrap.init`
3. Review generated `.specify/` configuration
4. Use standard SDD workflow: `/speckit.specify` → `/speckit.plan` → `/speckit.tasks`

## Skills Installation

For AI development expertise skills, see the separate skills directory:
- `skills/AI-INSTALL-GUIDE.md`

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Command not found | Ensure files are in `.claude/commands/` |
| Permission denied | Run with appropriate permissions |
| spec-kit not found | Install spec-kit first |

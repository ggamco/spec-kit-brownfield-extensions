# Brownfield Bootstrap Extension

> **spec-kit Extension** for bootstrapping existing projects into SDD workflow.

## Overview

This extension provides commands to bring **existing (brownfield) projects** into spec-kit's Specification-Driven Development (SDD) workflow with automatic project analysis and customized template generation.

## Installation

### Using spec-kit Extension System (Recommended)

```bash
# Install from GitHub
specify extension add brownfield-bootstrap

# Or install from source
specify extension add --dev /path/to/extension
```

### Manual Installation

Copy command files to your project:

```bash
mkdir -p .claude/commands
cp extension/commands/init.md .claude/commands/speckit.brownfield-bootstrap.init.md
cp extension/commands/init-cn.md .claude/commands/speckit.brownfield-bootstrap.init-cn.md
```

## Commands

| Command | Description |
|---------|-------------|
| `/speckit.brownfield-bootstrap.init` | Initialize SDD for existing brownfield projects (English) |
| `/speckit.brownfield-bootstrap.init-cn` | 初始化棕地项目的SDD工作流 (Chinese) |

### Aliases (Backward Compatibility)

- `speckit.brownfield.bootstrap` → `speckit.brownfield-bootstrap.init`
- `speckit.brownfield.bootstrap-cn` → `speckit.brownfield-bootstrap.init-cn`

## Usage

```bash
# Run the init command in your existing project
/speckit.brownfield-bootstrap.init

# Or with specific focus
/speckit.brownfield-bootstrap.init Focus on the user authentication module
```

## Generated Files

| File | Path | Description |
|------|------|-------------|
| Project Constitution | `.specify/memory/constitution.md` | Core principles and constraints |
| Spec Template | `.specify/templates/spec-template.md` | Feature specification template |
| Plan Template | `.specify/templates/plan-template.md` | Implementation plan template |
| Tasks Template | `.specify/templates/tasks-template.md` | Task breakdown template |

## Requirements

- spec-kit >= 0.1.0
- Required commands: `speckit.specify`, `speckit.plan`, `speckit.tasks`

## Related

- **Skills**: See the separate `skills/` directory for `brownfield-skills` and `brownfield-ears`
- **Main README**: See the repository root for complete documentation

## License

MIT License

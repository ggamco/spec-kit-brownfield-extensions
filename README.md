# spec-kit Brownfield Extensions

> [!IMPORTANT]
> **🌱 For Brownfield (Existing) Projects**
>
> This repository provides tools for **existing projects** to adopt [spec-kit](https://github.com/github/spec-kit)'s Specification-Driven Development (SDD) workflow.
>
> If you're starting a new project from scratch, use the standard `specify init` command instead.

**Bootstrap your existing codebase into spec-kit's SDD workflow with automatic project analysis and customized template generation.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Repository Structure

This repository contains two independent components:

```
spec-kit-brownfield-extensions/
├── extension/                   # spec-kit Extension (独立)
│   ├── extension.yml            # Extension manifest (id: brownfield-bootstrap)
│   ├── README.md                # Extension documentation
│   ├── AI-INSTALL-GUIDE.md      # AI installation instructions
│   ├── config-template.yml      # Configuration template
│   └── commands/
│       ├── init.md              # English bootstrap command
│       └── init-cn.md           # Chinese bootstrap command
│
└── skills/                      # Claude Code Skills (独立)
    ├── README.md                # Skills documentation
    ├── AI-INSTALL-GUIDE.md      # AI installation instructions
    ├── brownfield-skills/       # Developer expertise generator
    │   ├── SKILL.md
    │   └── references/
    │       ├── analysis-guide.md
    │       ├── templates.md
    │       └── templates-cn.md
    └── brownfield-ears/         # EARS requirements converter
        ├── SKILL.md
        └── references/
            ├── conversion-guide.md
            ├── document-template.md
            └── examples.md
```

## Components Overview

| Component | Type | Purpose |
|-----------|------|---------|
| `extension/` | spec-kit Extension | Bootstrap SDD workflow for existing projects |
| `skills/brownfield-skills` | Claude Code Skill | Generate senior developer expertise |
| `skills/brownfield-ears` | Claude Code Skill | Convert requirements to EARS format |

## Quick Start

### Install Extension

```bash
# Using spec-kit extension system
specify extension add --dev /path/to/spec-kit-brownfield-extensions/extension

# Or manually copy commands
cp extension/commands/init.md .claude/commands/speckit.brownfield-bootstrap.init.md
cp extension/commands/init-cn.md .claude/commands/speckit.brownfield-bootstrap.init-cn.md
```

### Install Skills

```bash
mkdir -p .claude/skills
cp -r skills/brownfield-skills .claude/skills/
cp -r skills/brownfield-ears .claude/skills/
```

### For AI Agents

See the AI installation guides:
- **Extension**: [extension/AI-INSTALL-GUIDE.md](extension/AI-INSTALL-GUIDE.md)
- **Skills**: [skills/AI-INSTALL-GUIDE.md](skills/AI-INSTALL-GUIDE.md)

## Usage

### 1. Bootstrap Your Project

```bash
# Run the init command
/speckit.brownfield-bootstrap.init

# Or Chinese version
/speckit.brownfield-bootstrap.init-cn
```

### 2. Review Generated Files

| File | Path | Description |
|------|------|-------------|
| Project Constitution | `.specify/memory/constitution.md` | Core principles and constraints |
| Spec Template | `.specify/templates/spec-template.md` | Feature specification template |
| Plan Template | `.specify/templates/plan-template.md` | Implementation plan template |
| Tasks Template | `.specify/templates/tasks-template.md` | Task breakdown template |

### 3. Start SDD Workflow

```bash
/speckit.specify "Add user profile image upload"
/speckit.plan
/speckit.tasks
/speckit.implement
```

## Command Reference

| Command | Description |
|---------|-------------|
| `/speckit.brownfield-bootstrap.init` | Initialize SDD for existing projects (English) |
| `/speckit.brownfield-bootstrap.init-cn` | 初始化棕地项目的SDD工作流 (Chinese) |

### Aliases (Backward Compatibility)

| Old Name | New Name |
|----------|----------|
| `speckit.brownfield.bootstrap` | `speckit.brownfield-bootstrap.init` |
| `speckit.brownfield.bootstrap-cn` | `speckit.brownfield-bootstrap.init-cn` |

## Key Features

### 🔍 Automatic Project Discovery
- Scans project structure to identify tech stack, frameworks, and patterns
- Recognizes common architectural patterns (MVC, Hexagonal, Microservices, etc.)
- Extracts coding conventions from config files and code samples

### 📋 Multi-Module Project Support
- Full support for Maven/Gradle multi-module projects
- Node.js Monorepo with workspaces support
- Go Workspace, Rust Workspace, Python Monorepo
- Automatic module responsibility mapping and dependency analysis

### 🧪 TDD Enforcement
- Built-in Test-Driven Development discipline
- Red-Green-Refactor cycle embedded in all templates
- Coverage requirements and verification checkpoints

### 📁 Correct Directory Structure
- Ensures all files are generated in spec-kit compatible locations
- Pre-output self-check list to prevent common path mistakes
- Clear path reference standards

## 🧠 Developer Skills Generation

The `brownfield-skills` skill generates **Project Skills** that make Claude Code behave like a senior developer who has been maintaining your project for years.

```
.claude/skills/brownfield-developer-[project-name]/
├── SKILL.md                    # Entry point
└── references/
    ├── architecture.md         # Architecture and layering
    ├── tech-stack.md           # Tech stack and versions
    ├── coding-conventions.md   # Coding standards
    ├── module-structure.md     # Module responsibilities
    └── development-patterns.md # Development patterns
```

## 📝 EARS Requirements Conversion

The `brownfield-ears` skill converts natural language requirements into [EARS (Easy Approach to Requirements Syntax)](https://alistairmavin.com/ears/) format.

| Pattern | Template | Example |
|---------|----------|---------|
| **Ubiquitous** | `The system shall <function>` | The system shall encrypt all user passwords |
| **Event-Driven** | `When <trigger>, the system shall <response>` | When user clicks submit, the system shall validate input |
| **State-Driven** | `If <state>, then the system shall <behavior>` | If user is admin, then the system shall show admin panel |

## Compatibility

### AI Agents
- ✅ **Claude Code** (fully tested)
- ✅ **Cursor** (tested)
- ✅ **GitHub Copilot** (via instructions)
- ✅ **Windsurf** (via project rules)

### spec-kit Versions
- ✅ **spec-kit v0.1.0+**
- ✅ Fully compatible with core spec-kit workflows

### Project Types
- ✅ Single module projects
- ✅ Multi-module Maven/Gradle projects
- ✅ Node.js Monorepo (with workspaces)
- ✅ Go Workspace, Rust Workspace, Python Monorepo

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

MIT License - See [LICENSE](LICENSE) for details.

## Credits

- [GitHub spec-kit team](https://github.com/github/spec-kit) for the foundation
- [spec-kit-cn](https://github.com/Linfee/spec-kit-cn) for the Chinese localization
- [Repomix](https://github.com/yamadashy/repomix) for code understanding and skill generation
- Community contributors

## Support

- **Issues**: [GitHub Issues](https://github.com/wcpaxx/spec-kit-brownfield-extensions/issues)
- **Discussions**: [GitHub Discussions](https://github.com/wcpaxx/spec-kit-brownfield-extensions/discussions)
- **spec-kit**: [Original spec-kit repo](https://github.com/github/spec-kit)

# spec-kit Brownfield Bootstrap Extension

> [!IMPORTANT]
> **🌱 For Brownfield (Existing) Projects**
>
> This extension is specifically designed for **existing projects** that want to adopt [spec-kit](https://github.com/github/spec-kit)'s Specification-Driven Development (SDD) workflow.
>
> If you're starting a new project from scratch, use the standard `specify init` command instead.

**Bootstrap your existing codebase into spec-kit's SDD workflow with automatic project analysis and customized template generation.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## What Is This?

When you have an **existing project (brownfield project)** and want to adopt spec-kit's structured development workflow, you face a challenge: the standard `specify init` creates generic templates that don't reflect your project's actual architecture, tech stack, and coding conventions.

**This extension solves that problem** by:

1. **Reverse-analyzing** your existing codebase to extract architectural DNA
2. **Generating customized** project constitution reflecting actual project principles
3. **Adapting templates** to your specific tech stack and coding style
4. **Validating readiness** to ensure SDD workflow can be immediately enabled

## 📊 Workflow Overview

This extension provides commands that extend the standard spec-kit SDD workflow:

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           Extended SDD Workflow                                  │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│   [Existing Project]                                                             │
│         │                                                                        │
│         ▼                                                                        │
│   ┌─────────────────────────┐                                                   │
│   │ /speckit.brownfield-    │  ← Bootstrap existing project into SDD            │
│   │ bootstrap               │                                                    │
│   └───────────┬─────────────┘                                                   │
│               │                                                                  │
│               ▼                                                                  │
│   ┌─────────────────────────┐     ┌─────────────────────────┐                   │
│   │ User Requirements       │────▶│ /speckit.ears           │  ← Optional       │
│   │ (Natural Language)      │     │ (EARS Format Conversion)│    Pre-step       │
│   └─────────────────────────┘     └───────────┬─────────────┘                   │
│                                               │                                  │
│                                               ▼                                  │
│   ┌─────────────────────────────────────────────────────────────────────────┐   │
│   │                    Standard spec-kit SDD Workflow                        │   │
│   │  ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐              │   │
│   │  │ /speckit │──▶│ /speckit │──▶│ /speckit │──▶│ /speckit │              │   │
│   │  │ .specify │   │ .plan    │   │ .tasks   │   │.implement│              │   │
│   │  └──────────┘   └──────────┘   └──────────┘   └──────────┘              │   │
│   └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### Commands Provided

| Command | Purpose | When to Use |
|---------|---------|-------------|
| `/speckit.brownfield-bootstrap` | Initialize SDD for existing projects | First time adopting spec-kit in a brownfield project |
| `brownfield-skills` | Generate senior developer Skills for project | Enable AI to master project conventions and patterns |
| `/speckit.ears` | Convert requirements to EARS format | Before `/speckit.specify` when requirements are complex or ambiguous |

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

## Quick Start

### Prerequisites

- **spec-kit** installed ([installation guide](https://github.com/github/spec-kit))
- **AI coding agent** (Claude Code, GitHub Copilot, Cursor, Windsurf, etc.)
- **Existing project** with established codebase

### Installation

**Step 1: Copy Command File**

Copy the command file to your AI coding tool's commands directory:

| AI Tool | Target Directory |
|---------|------------------|
| **Claude Code** | `.claude/commands/` |
| **Cursor** | `.cursor/commands/` |
| **Other Tools** | Check tool documentation |

```bash
# Example for Claude Code
mkdir -p .claude/commands/
cp speckit.brownfield-bootstrap.md .claude/commands/

# For Chinese version
cp speckit.brownfield-bootstrap-cn.md .claude/commands/
```

**Step 2: Verify Installation**

In your AI coding tool, try:
```
/speckit.brownfield-bootstrap
```

### Usage

**1. Run the Bootstrap Command**

```
/speckit.brownfield-bootstrap
```

Or with specific focus:
```
/speckit.brownfield-bootstrap Focus on the user authentication module
```

**2. Review Generated Files**

The command will generate:

| File | Path | Description |
|------|------|-------------|
| Project Constitution | `.specify/memory/constitution.md` | Core principles and constraints |
| Spec Template | `.specify/templates/spec-template.md` | Feature specification template |
| Plan Template | `.specify/templates/plan-template.md` | Implementation plan template |
| Tasks Template | `.specify/templates/tasks-template.md` | Task breakdown template |

**3. Confirm Constitution**

Review the generated constitution and confirm or modify:
- Core principles derived from your code
- Tech stack locked versions
- Directory contracts
- Module responsibilities (for multi-module projects)

**4. Start Using SDD Workflow**

Once bootstrap is complete:

```bash
# Create new feature spec
/speckit.specify "Add user profile image upload"

# Generate implementation plan
/speckit.plan

# Generate task list
/speckit.tasks

# Execute implementation
/speckit.implement
```

## Generated Directory Structure

After running the bootstrap command, your project will have:

```
your-project/
├── .specify/                          # SDD configuration directory
│   ├── memory/
│   │   └── constitution.md            # Project constitution (core file)
│   └── templates/
│       ├── spec-template.md           # Feature spec template
│       ├── plan-template.md           # Implementation plan template
│       └── tasks-template.md          # Task list template
└── specs/                             # Feature specs directory
    └── [###-feature-name]/            # Organized by feature
        ├── spec.md
        ├── plan.md
        └── tasks.md
```

## 🧠 Developer Skills Generation (NEW)

The **Brownfield Developer Skills Generator** (`brownfield-skills.md`) generates **Project Skills** that make Claude Code behave like a senior developer who has been maintaining your project for years.

### What It Does

This command analyzes your project and generates structured Skills that:

| Capability | Description |
|------------|-------------|
| **Master Tech Stack** | Deep understanding of languages, frameworks, and tools |
| **Follow Conventions** | Adhere to your project's coding style and patterns |
| **Understand Architecture** | Know where to place new code and how modules interact |
| **Prioritize Reuse** | Always search for existing code before creating new |
| **Maintain Compatibility** | Never break existing functionality |

### Usage

```bash
# Copy the skills generator to your commands directory
cp brownfield-skills.md .claude/commands/

# Generate developer skills for your project
# Use in your AI coding tool
```

### Generated Skills Structure

```
.claude/skills/brownfield-developer-[project-name]/
├── SKILL.md                    # Skill entry point (usage guide)
└── references/
    ├── architecture.md         # Project architecture and layering
    ├── tech-stack.md           # Tech stack details and constraints
    ├── coding-conventions.md   # Coding standards and style
    ├── module-structure.md     # Module structure and responsibilities
    └── development-patterns.md # Development patterns and best practices
```

### Key Features

- **Idempotent**: Run anytime to refresh Skills based on current project state
- **Team Shareable**: Add `.claude/skills/` to version control
- **Complementary**: Works alongside Repomix for complete project understanding

### Recommended Workflow

1. Run the Brownfield Skills Generator to generate developer expertise
2. Run `repomix --skill-generate` to generate code snapshots
3. Together they provide comprehensive project mastery

> **💡 Tip**: Re-run the skills generator after major architectural changes to keep AI understanding current.

## 🚀 Enhance with Repomix (Recommended)

For large brownfield projects, we recommend using [Repomix](https://github.com/yamadashy/repomix) to help AI coding tools better understand your existing codebase. Repomix generates structured "Skills" that serve as long-term memory for Claude Code.

### Why Repomix?

| Challenge | How Repomix Helps |
|-----------|-------------------|
| **Context Window Limits** | Compresses codebase into AI-friendly format via Tree-sitter |
| **Code Reuse** | Enables quick search of existing Utils, DTOs, Services |
| **Accuracy** | Generated constitution precisely reflects module structure |
| **Dynamic Updates** | `repomix --skill-generate` is idempotent - run anytime to sync |

### Setup Guide (Claude Code)

**Step 1: Install Repomix CLI**

```bash
npm install -g repomix
```

**Step 2: Install Repomix MCP for Claude Code**

Configure Claude Code to support Repomix's Model Context Protocol:

```bash
claude mcp add repomix -- npx -y repomix --mcp
```

**Step 3: Install Repomix Plugin (Optional)**

For convenient slash commands like `/repomix-explorer`:

```
# In Claude Code interactive interface
/plugin install repomix-mcp@repomix
```

### Generate Skills for Your Project

Run the following command in your project root:

```bash
repomix --skill-generate
```

This creates a `.claude/skills/` directory with structured references:

```
.claude/skills/repomix-reference-[project-name]/
├── SKILL.md                 # Core skill metadata
└── references/
    ├── summary.md           # Project purpose and statistics
    ├── project-structure.md # Directory tree with line counts
    ├── files.md             # Full file contents (grep-optimized)
    └── tech-stack.md        # Auto-detected tech stack
```

Claude Code automatically loads these Skills as part of its long-term memory.

### Best Practices

| When to Run | Action |
|-------------|--------|
| **First time using brownfield-bootstrap** | Run `repomix --skill-generate` before bootstrap |
| **Before major feature development** | Refresh skills to ensure latest codebase understanding |
| **After significant code changes** | Re-run to sync AI's memory with current code |

> **💡 Tip**: The brownfield-bootstrap command already includes rules for code reuse and understanding existing code. With Repomix Skills loaded, Claude Code will automatically search existing implementations before creating new code.

## 📝 EARS Requirements Conversion (Optional Pre-step)

The `/speckit.ears` command provides an **optional pre-step** to improve requirement quality before entering the standard SDD workflow. It converts natural language requirements into [EARS (Easy Approach to Requirements Syntax)](https://alistairmavin.com/ears/) format.

### Why Use EARS?

| Problem | How EARS Helps |
|---------|----------------|
| **Ambiguous requirements** | Fixed sentence templates force clear trigger conditions and responses |
| **AI misinterpretation** | Structured format reduces ambiguity, improves AI accuracy |
| **Missing requirements** | Categorized templates ensure comprehensive coverage |
| **Unclear acceptance criteria** | Each EARS requirement is inherently testable |

### EARS Five Requirement Patterns

| Pattern | Template | Example |
|---------|----------|---------|
| **Ubiquitous** | `The system shall <function>` | The system shall encrypt all user passwords |
| **Event-Driven** | `When <trigger>, the system shall <response>` | When user clicks submit, the system shall validate input |
| **State-Driven** | `If <state>, then the system shall <behavior>` | If user is admin, then the system shall show admin panel |
| **Optional** | `Where <condition>, the user can <operation>` | Where notifications are enabled, the user can set frequency |
| **Complex** | `When <trigger>, and <state>, the system shall <response>` | When login fails, and attempts exceed 5, the system shall lock account |

### Usage

```bash
# Convert requirement to EARS format
/speckit.ears I need a user login feature supporting phone and email

# Then continue to spec creation
/speckit.specify .docs/EARS/001-user-login.md
```

### Output Location

EARS documents are stored separately from spec-kit core directories:

```
your-project/
├── .docs/                    # Documentation (not SDD core)
│   └── EARS/                 # EARS requirement documents
│       ├── 001-user-login.md
│       └── 002-payment.md
├── .specify/                 # SDD configuration (unchanged)
└── specs/                    # Feature specs (unchanged)
```

> **📍 Why separate location?**
> EARS requirements are optional and outside the standard spec-kit workflow. Keeping them in `.docs/EARS/` avoids interference with core SDD files.

## Language Versions

| File | Language | Description |
|------|----------|-------------|
| `speckit.brownfield-bootstrap.md` | English | Brownfield bootstrap (English) |
| `speckit.brownfield-bootstrap-cn.md` | 中文 | Brownfield bootstrap (Chinese) |
| `brownfield-skills.md` | English | Brownfield Developer Skills Generator (English) |
| `brownfield-skills-cn.md` | 中文 | Brownfield Developer Skills Generator (Chinese) |
| `speckit.ears.md` | English | EARS conversion (English) |
| `speckit.ears-cn.md` | 中文 | EARS conversion (Chinese) |

## Compatibility

### AI Agents

This extension works with any AI agent that supports custom commands:

- ✅ **Claude Code** (fully tested)
- ✅ **Cursor** (tested)
- ✅ **GitHub Copilot** (via instructions)
- ✅ **Windsurf** (via project rules)
- ✅ **Other AI Coding Tools** (copy to commands directory)

### spec-kit Versions

- ✅ **spec-kit v0.0.18+** (uses `/speckit.` prefix)
- ✅ Fully compatible with core spec-kit workflows
- ✅ Non-breaking addition to existing spec-kit setup

### Project Types

- ✅ Single module projects
- ✅ Multi-module Maven/Gradle projects
- ✅ Node.js Monorepo (with workspaces)
- ✅ Go Workspace
- ✅ Rust Workspace
- ✅ Python Monorepo
- ✅ Any language/framework combination

## Brownfield vs Greenfield

| Aspect | Greenfield (`specify init`) | Brownfield (This Extension) |
|--------|---------------------------|----------------------------|
| **Starting Point** | Empty project | Existing codebase |
| **Tech Stack** | You choose | Auto-detected and locked |
| **Architecture** | You design | Reverse-engineered |
| **Templates** | Generic | Project-specific |
| **Constitution** | Minimal | Comprehensive from code analysis |
| **Multi-module** | Basic | Full module mapping |

## FAQ

### When should I use this vs `specify init`?

Use **brownfield-bootstrap** when:
- You have an existing codebase with established patterns
- Your project has specific tech stack constraints
- You want templates that match your existing code style
- You have a multi-module project structure

Use **`specify init`** when:
- Starting a new project from scratch
- You want to establish new conventions
- Project structure is not yet defined

### Will this modify my existing code?

**No!** This command only creates new files in `.specify/` and `specs/` directories. It does not modify any existing source code.

### Can I customize the generated templates?

Yes! After bootstrap, you can freely modify:
- `.specify/memory/constitution.md` - Update principles
- `.specify/templates/*.md` - Customize template formats

### What if my project structure is unusual?

The command will:
1. Do its best to analyze your structure
2. Mark uncertain items with `[NEEDS CLARIFICATION: ...]`
3. Ask you to confirm or provide guidance

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

MIT License - See [LICENSE](LICENSE) for details.

## Credits

- [GitHub spec-kit team](https://github.com/github/spec-kit) for the foundation
- [spec-kit-cn](https://github.com/Linfee/spec-kit-cn) for the Chinese localization of spec-kit
- [spec-kit-extensions](https://github.com/MartyBonacci/spec-kit-extensions) for inspiration
- [Repomix](https://github.com/yamadashy/repomix) for code understanding and skill generation
- Community contributors

## Support

- **Issues**: [GitHub Issues](https://github.com/wcpaxx/spec-kit-brownfield-extensions/issues)
- **Discussions**: [GitHub Discussions](https://github.com/wcpaxx/spec-kit-brownfield-extensions/discussions)
- **spec-kit**: [Original spec-kit repo](https://github.com/github/spec-kit)
- **Repomix**: [Code understanding tool](https://github.com/yamadashy/repomix)

---

**Ready to try it?** Copy the command file to your AI tool's commands directory and run `/speckit.brownfield-bootstrap`!

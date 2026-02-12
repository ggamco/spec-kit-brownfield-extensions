# Skills AI Installation Guide

This document provides executable instructions for AI agents to install the Brownfield Skills.

## Prerequisites

- Claude Code or compatible AI coding agent
- Git available
- Target project directory identified

## Installation Steps

### Step 1: Clone Repository

```bash
git clone https://github.com/wcpaxx/spec-kit-brownfield-extensions.git /tmp/brownfield-ext
```

### Step 2: Install Skills

Copy skills to your project:

```bash
mkdir -p .claude/skills
cp -r /tmp/brownfield-ext/skills/brownfield-skills .claude/skills/
cp -r /tmp/brownfield-ext/skills/brownfield-ears .claude/skills/
```

### Step 3: Verify Installation

```bash
ls .claude/skills/brownfield-*/SKILL.md
```

Expected output:
- `SKILL.md` files in both `brownfield-skills` and `brownfield-ears` directories

### Step 4: Cleanup

```bash
rm -rf /tmp/brownfield-ext
```

## Post-Installation

After installation, the following skills are available:

| Skill | Description |
|-------|-------------|
| `brownfield-skills` | Generate project expertise skills |
| `brownfield-ears` | Convert requirements to EARS format |

## Usage

### Generate Developer Skills

The `brownfield-skills` skill will analyze your project and generate expertise files:

```
.claude/skills/brownfield-developer-[project-name]/
├── SKILL.md
└── references/
    ├── architecture.md
    ├── tech-stack.md
    ├── coding-conventions.md
    ├── module-structure.md
    └── development-patterns.md
```

### Convert Requirements to EARS

Use `brownfield-ears` to convert natural language requirements:

```
Input: "Users should be able to login with email or phone"

Output: 
- When user provides email, the system shall authenticate using email credentials
- When user provides phone number, the system shall authenticate using phone credentials
```

## Extension Installation

For spec-kit commands, see the separate extension directory:
- `extension/AI-INSTALL-GUIDE.md`

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Skills not loading | Check `.claude/skills/` directory structure |
| SKILL.md not found | Ensure directory names match exactly |
| Permission denied | Run with appropriate permissions |

## Directory Structure Reference

```
.claude/skills/
├── brownfield-skills/
│   ├── SKILL.md
│   └── references/
│       ├── analysis-guide.md
│       ├── templates.md
│       └── templates-cn.md
└── brownfield-ears/
    ├── SKILL.md
    └── references/
        ├── conversion-guide.md
        ├── document-template.md
        └── examples.md
```

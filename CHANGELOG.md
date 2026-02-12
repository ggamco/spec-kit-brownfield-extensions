# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.2.0] - 2026-02-12

### Breaking Changes

- **Repository restructured**: Extension and Skills are now in separate directories
- **Extension ID finalized**: `brownfield-bootstrap`
- **Commands renamed**: `bootstrap` → `init` (to avoid semantic redundancy)

### Added

- `extension/` directory - Extension now isolated in its own directory
- `skills/` directory - Skills now isolated in their own directory
- `extension/AI-INSTALL-GUIDE.md` - AI installation guide for extension
- `skills/AI-INSTALL-GUIDE.md` - AI installation guide for skills
- `extension/config-template.yml` - Configuration template
- `skills/brownfield-skills/references/templates-cn.md` - Chinese templates (was missing)

### Changed

- Extension location: root `extension.yml` → `extension/extension.yml`
- Commands location: root `commands/` → `extension/commands/`
- Command names: `bootstrap`/`bootstrap-cn` → `init`/`init-cn`
- Full command pattern: `speckit.brownfield-bootstrap.init`
- Both README.md and README-CN.md updated for new structure

### Removed

- Root-level `extension.yml` (moved to `extension/`)
- Root-level `commands/` directory (moved to `extension/commands/`)
- Root-level `AI-INSTALL-GUIDE.md` (split into extension/ and skills/)

### Migration from v2.1.0

| v2.1.0 | v2.2.0 | Notes |
|--------|--------|-------|
| `/speckit.brownfield.bootstrap` | `/speckit.brownfield-bootstrap.init` | Command renamed |
| `/speckit.brownfield.bootstrap-cn` | `/speckit.brownfield-bootstrap.init-cn` | Command renamed |
| `extension.yml` (root) | `extension/extension.yml` | Moved to extension/ |
| `commands/` (root) | `extension/commands/` | Moved to extension/ |

Old command aliases preserved for backward compatibility.

## [2.1.0] - 2026-02-12

### Breaking Changes

- **Skills/EARS converted to Skills**: Now standalone Skills instead of extension commands

### Added

- `skills/brownfield-skills/` - Project expertise generator (now a Skill)
- `skills/brownfield-ears/` - EARS requirements converter (now a Skill)
- `AI-INSTALL-GUIDE.md` - Executable installation instructions for AI agents
- References directory structure following Skill best practices

### Changed

- Skills and EARS moved from `commands/` to `skills/` directory
- README updated with human/AI installation sections

### Removed

- `commands/skills.md` - Now `skills/brownfield-skills/SKILL.md`
- `commands/skills-cn.md` - Merged into brownfield-skills references
- `commands/ears.md` - Now `skills/brownfield-ears/SKILL.md`
- `commands/ears-cn.md` - Merged into brownfield-ears references
- `hooks.after_tasks` - Removed (skills are now standalone)

## [2.0.0] - 2026-02-12

### Breaking Changes

- **Extension System Migration**: Project now follows spec-kit official extension format
  - Requires spec-kit v0.1.0 or higher with extension support
  - Commands moved from root to `commands/` directory
  - Command names follow new pattern: `speckit.brownfield-bootstrap.{command}`
  - Old command names still work as aliases for backward compatibility

### Added

- `extension.yml` manifest file for spec-kit extension system
- `commands/` directory structure following extension conventions
- Backward compatibility aliases for all commands
- `after_tasks` hook to suggest generating developer skills
- Migration guide in README for existing users

### Changed

- Installation method: now uses `specify extension add` command
- File structure: command files moved to `commands/` directory
- Command naming: follows `speckit.{extension-id}.{command}` pattern

### Command Name Mapping

| Old Name | New Name | Alias |
|----------|----------|-------|
| `speckit.brownfield-bootstrap` | `speckit.brownfield-bootstrap.bootstrap` | Yes |
| `speckit.brownfield-bootstrap-cn` | `speckit.brownfield-bootstrap.bootstrap-cn` | Yes |
| `brownfield-skills` | `speckit.brownfield-bootstrap.skills` | Yes |
| `brownfield-skills-cn` | `speckit.brownfield-bootstrap.skills-cn` | Yes |
| `speckit.ears` | `speckit.brownfield-bootstrap.ears` | Yes |
| `speckit.ears-cn` | `speckit.brownfield-bootstrap.ears-cn` | Yes |

## [1.1.0] - 2025-01-08

### Added

- **New Command: `/speckit.skills`** - Generate senior developer Skills for brownfield projects
  - `speckit.skills.md` - English version
  - `speckit.skills-cn.md` - Chinese version
- Deep project analysis capabilities
  - Tech stack identification (languages, frameworks, testing, data storage, infrastructure)
  - Architecture pattern recognition (layered, onion, hexagonal, microservices, etc.)
  - Coding conventions extraction (naming, formatting, comments, Git conventions)
  - Module structure analysis (responsibilities, dependencies, code placement)
  - Development patterns recognition (design patterns, error handling, logging, testing)
- Generated Skills structure
  - `SKILL.md` - Skill entry point with usage guide
  - `references/architecture.md` - Project architecture and layering
  - `references/tech-stack.md` - Tech stack details and constraints
  - `references/coding-conventions.md` - Coding standards and style
  - `references/module-structure.md` - Module structure and responsibilities
  - `references/development-patterns.md` - Development patterns and best practices
- Five brownfield development principles
  - Respect existing architecture
  - Code reuse first
  - Forward compatibility
  - Refactor on-demand
  - Compatibility first
- Idempotent execution support (re-run anytime to refresh Skills)
- Complementary workflow with Repomix

### Changed

- Updated README.md with new command documentation
- Updated command table to include `/speckit.skills`
- Updated language versions table

## [1.0.0] - 2025-01-06

### Added

- Initial release of spec-kit Brownfield Bootstrap Extension
- `speckit.brownfield-bootstrap.md` - English version of the command
- `speckit.brownfield-bootstrap-cn.md` - Chinese version of the command
- Automatic project discovery and analysis
  - Tech stack detection
  - Architecture pattern recognition
  - Coding convention extraction
- Multi-module project support
  - Maven/Gradle multi-module
  - Node.js Monorepo
  - Go Workspace
  - Rust Workspace
  - Python Monorepo
- TDD (Test-Driven Development) enforcement
- Project constitution generation
- Customized template generation
  - Spec template
  - Plan template
  - Tasks template
- Pre-output self-check list for path validation
- Comprehensive documentation
  - README.md
  - CONTRIBUTING.md
  - LICENSE (MIT)

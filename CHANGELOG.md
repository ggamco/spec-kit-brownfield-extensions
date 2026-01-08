# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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

# spec-kit 棕地项目扩展

> [!IMPORTANT]
> **适用于棕地（现有）项目**
>
> 此仓库提供工具，帮助**现有项目**采用 [spec-kit](https://github.com/github/spec-kit) 规范驱动开发（SDD）工作流。
>
> 如果您正在从零开始创建新项目，请使用标准的 `specify init` 命令。

**通过自动项目分析和定制模板生成，将现有代码库引导至 spec-kit 的 SDD 工作流。**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 仓库结构

此仓库包含两个独立组件：

```
spec-kit-brownfield-extensions/
├── extension/                   # spec-kit 扩展（独立）
│   ├── extension.yml            # 扩展清单 (id: brownfield-bootstrap)
│   ├── README.md                # 扩展文档
│   ├── AI-INSTALL-GUIDE.md      # AI 安装说明
│   ├── config-template.yml      # 配置模板
│   └── commands/
│       ├── init.md              # 英文引导命令
│       └── init-cn.md           # 中文引导命令
│
└── skills/                      # Claude Code Skills（独立）
    ├── README.md                # Skills 文档
    ├── AI-INSTALL-GUIDE.md      # AI 安装说明
    ├── brownfield-skills/       # 开发者专业知识生成器
    │   ├── SKILL.md
    │   └── references/
    │       ├── analysis-guide.md
    │       ├── templates.md
    │       └── templates-cn.md
    └── brownfield-ears/         # EARS 需求转换器
        ├── SKILL.md
        └── references/
            ├── conversion-guide.md
            ├── document-template.md
            └── examples.md
```

## 组件概览

| 组件 | 类型 | 用途 |
|------|------|------|
| `extension/` | spec-kit 扩展 | 为现有项目引导 SDD 工作流 |
| `skills/brownfield-skills` | Claude Code Skill | 生成高级开发者专业知识 |
| `skills/brownfield-ears` | Claude Code Skill | 将需求转换为 EARS 格式 |

## 核心功能

### 自动项目发现
- 扫描项目结构以识别技术栈、框架和模式
- 识别常见架构模式（MVC、六边形架构、微服务等）
- 从配置文件和代码示例中提取编码规范

### 多模块项目支持
- 完全支持 Maven/Gradle 多模块项目
- 支持带 workspaces 的 Node.js Monorepo
- Go Workspace、Rust Workspace、Python Monorepo
- 自动模块职责映射和依赖分析

### TDD 强制执行
- 内置测试驱动开发规范
- 红-绿-重构循环嵌入所有模板
- 覆盖率要求和验证检查点

### 正确的目录结构
- 确保所有文件生成在 spec-kit 兼容的位置
- 输出前自检列表以防止常见路径错误
- 清晰的路径引用标准

## 快速开始

### 安装扩展

```bash
# 使用 spec-kit 扩展系统
specify extension add --dev /path/to/spec-kit-brownfield-extensions/extension

# 或手动复制命令
cp extension/commands/init.md .claude/commands/speckit.brownfield-bootstrap.init.md
cp extension/commands/init-cn.md .claude/commands/speckit.brownfield-bootstrap.init-cn.md
```

### 安装 Skills

```bash
mkdir -p .claude/skills
cp -r skills/brownfield-skills .claude/skills/
cp -r skills/brownfield-ears .claude/skills/
```

### AI 代理安装

查看 AI 安装指南：
- **扩展**: [extension/AI-INSTALL-GUIDE.md](extension/AI-INSTALL-GUIDE.md)
- **Skills**: [skills/AI-INSTALL-GUIDE.md](skills/AI-INSTALL-GUIDE.md)

## 使用方法

### 1. 引导您的项目

```bash
# 运行 init 命令
/speckit.brownfield-bootstrap.init

# 或中文版本
/speckit.brownfield-bootstrap.init-cn
```

### 2. 查看生成的文件

| 文件 | 路径 | 描述 |
|------|------|------|
| 项目宪章 | `.specify/memory/constitution.md` | 核心原则和约束 |
| 规范模板 | `.specify/templates/spec-template.md` | 功能规范模板 |
| 计划模板 | `.specify/templates/plan-template.md` | 实施计划模板 |
| 任务模板 | `.specify/templates/tasks-template.md` | 任务分解模板 |

### 3. 开始 SDD 工作流

```bash
/speckit.specify "添加用户头像上传功能"
/speckit.plan
/speckit.tasks
/speckit.implement
```

## 命令参考

| 命令 | 描述 |
|------|------|
| `/speckit.brownfield-bootstrap.init` | 为现有项目初始化 SDD（英文） |
| `/speckit.brownfield-bootstrap.init-cn` | 初始化棕地项目的SDD工作流（中文） |

### 别名（向后兼容）

| 旧名称 | 新名称 |
|--------|--------|
| `speckit.brownfield.bootstrap` | `speckit.brownfield-bootstrap.init` |
| `speckit.brownfield.bootstrap-cn` | `speckit.brownfield-bootstrap.init-cn` |

## 开发者技能生成

`brownfield-skills` 技能生成**项目技能**，使 Claude Code 表现得像一位维护您项目多年的高级开发者。

```
.claude/skills/brownfield-developer-[project-name]/
├── SKILL.md                    # 技能入口点
└── references/
    ├── architecture.md         # 项目架构和分层
    ├── tech-stack.md           # 技术栈详情和约束
    ├── coding-conventions.md   # 编码标准和风格
    ├── module-structure.md     # 模块结构和职责
    └── development-patterns.md # 开发模式和最佳实践
```

## EARS 需求转换

`brownfield-ears` 技能将自然语言需求转换为 [EARS（Easy Approach to Requirements Syntax）](https://alistairmavin.com/ears/) 格式。

| 模式 | 模板 | 示例 |
|---------|----------|---------|
| **普遍型** | `系统应 <功能>` | 系统应加密所有用户密码 |
| **事件驱动型** | `当 <触发条件> 时，系统应 <响应>` | 当用户点击提交时，系统应验证输入 |
| **状态驱动型** | `如果 <状态>，则系统应 <行为>` | 如果用户是管理员，则系统应显示管理面板 |

## 兼容性

### AI 代理
- ✅ **Claude Code**（完整测试）
- ✅ **Cursor**（已测试）
- ✅ **GitHub Copilot**（通过 instructions）
- ✅ **Windsurf**（通过 project rules）

### spec-kit 版本
- ✅ **spec-kit v0.1.0+**
- ✅ 与核心 spec-kit 工作流完全兼容

### 项目类型
- ✅ 单模块项目
- ✅ Maven/Gradle 多模块项目
- ✅ Node.js Monorepo（带 workspaces）
- ✅ Go Workspace、Rust Workspace、Python Monorepo

## 贡献

欢迎贡献！请参阅 [CONTRIBUTING.md](CONTRIBUTING.md) 了解指南。

## 许可证

MIT 许可证 - 详见 [LICENSE](LICENSE)。

## 致谢

- [GitHub spec-kit 团队](https://github.com/github/spec-kit) 提供基础
- [spec-kit-cn](https://github.com/Linfee/spec-kit-cn) 提供 spec-kit 中文本地化
- [Repomix](https://github.com/yamadashy/repomix) 提供代码理解和技能生成
- 社区贡献者

## 支持

- **问题反馈**: [GitHub Issues](https://github.com/wcpaxx/spec-kit-brownfield-extensions/issues)
- **讨论**: [GitHub Discussions](https://github.com/wcpaxx/spec-kit-brownfield-extensions/discussions)
- **spec-kit**: [原始 spec-kit 仓库](https://github.com/github/spec-kit)

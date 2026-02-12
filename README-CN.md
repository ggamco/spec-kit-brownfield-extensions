# spec-kit 棕地项目引导扩展

> [!IMPORTANT]
> **适用于棕地（现有）项目**
>
> 此扩展专为希望采用 [spec-kit](https://github.com/github/spec-kit) 规范驱动开发（SDD）工作流的**现有项目**而设计。
>
> 如果您正在从零开始创建新项目，请使用标准的 `specify init` 命令。

**通过自动项目分析和定制模板生成，将现有代码库引导至 spec-kit 的 SDD 工作流。**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 这是什么？

当您有一个**现有项目（棕地项目）**并希望采用 spec-kit 的结构化开发工作流时，会面临一个挑战：标准的 `specify init` 会创建通用模板，无法反映项目的实际架构、技术栈和编码规范。

**此扩展解决了这个问题**，通过：

1. **逆向分析**现有代码库以提取架构 DNA
2. **生成定制化**的项目宪章，反映实际项目原则
3. **适配模板**到您特定的技术栈和编码风格
4. **验证就绪状态**以确保 SDD 工作流可以立即启用

## 工作流概览

此扩展提供的命令扩展了标准 spec-kit SDD 工作流：

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           扩展 SDD 工作流                                        │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│   [现有项目]                                                                      │
│         │                                                                        │
│         ▼                                                                        │
│   ┌─────────────────────────┐                                                   │
│   │ /speckit.brownfield-    │  ← 将现有项目引导至 SDD                             │
│   │ bootstrap               │                                                    │
│   └───────────┬─────────────┘                                                   │
│               │                                                                  │
│               ▼                                                                  │
│   ┌─────────────────────────┐     ┌─────────────────────────┐                   │
│   │ 用户需求                 │────▶│ /speckit.ears           │  ← 可选            │
│   │ （自然语言）              │     │ （EARS 格式转换）         │    前置步骤        │
│   └─────────────────────────┘     └───────────┬─────────────┘                   │
│                                               │                                  │
│                                               ▼                                  │
│   ┌─────────────────────────────────────────────────────────────────────────┐   │
│   │                    标准 spec-kit SDD 工作流                              │   │
│   │  ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐              │   │
│   │  │ /speckit │──▶│ /speckit │──▶│ /speckit │──▶│ /speckit │              │   │
│   │  │ .specify │   │ .plan    │   │ .tasks   │   │.implement│              │   │
│   │  └──────────┘   └──────────┘   └──────────┘   └──────────┘              │   │
│   └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### 提供的命令

| 命令 | 用途 | 使用时机 |
|---------|---------|-------------|
| `/speckit.brownfield-bootstrap` | 为现有项目初始化 SDD | 首次在棕地项目中采用 spec-kit |
| `brownfield-skills` | 为项目生成高级开发者技能 | 使 AI 掌握项目规范和模式 |
| `/speckit.ears` | 将需求转换为 EARS 格式 | 在 `/speckit.specify` 之前，当需求复杂或模糊时 |

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

### 前置条件

- 已安装 **spec-kit**（[安装指南](https://github.com/github/spec-kit)）
- **AI 编码代理**（Claude Code、GitHub Copilot、Cursor、Windsurf 等）
- 具有已建立代码库的**现有项目**

### 安装

**方式一：使用 spec-kit 扩展系统（推荐）**

```bash
# 从 GitHub 安装（发布到目录后）
specify extension add brownfield-bootstrap

# 或从源码安装（开发模式）
specify extension add --dev /path/to/spec-kit-brownfield-extensions
```

**方式二：手动安装（旧方式）**

> **注意**：此方法已弃用，请使用上述扩展系统。

将命令文件复制到 AI 编码工具的命令目录：

| AI 工具 | 目标目录 |
|---------|----------|
| **Claude Code** | `.claude/commands/` |
| **Cursor** | `.cursor/commands/` |

```bash
# 克隆仓库
git clone https://github.com/wcpaxx/spec-kit-brownfield-extensions.git

# 复制命令（以 Claude Code 为例）
cp spec-kit-brownfield-extensions/commands/*.md .claude/commands/
```

### 从手动安装迁移

如果你之前手动安装了命令：

1. 从 `.claude/commands/` 或 `.cursor/commands/` 删除旧命令文件
2. 使用扩展系统安装：`specify extension add --dev /path/to/repo`
3. 验证安装：`specify extension list`

**命令名称变更**（提供别名以保持向后兼容）：

| 旧命令 | 新命令 |
|--------|--------|
| `/speckit.brownfield-bootstrap` | `/speckit.brownfield-bootstrap.bootstrap` |
| `/brownfield-skills` | `/speckit.brownfield-bootstrap.skills` |
| `/speckit.ears` | `/speckit.brownfield-bootstrap.ears` |

> 旧命令名称仍可作为别名使用，保持向后兼容。

**步骤 2：验证安装**

在您的 AI 编码工具中尝试：
```
/speckit.brownfield-bootstrap
```

### 使用方法

**1. 运行引导命令**

```
/speckit.brownfield-bootstrap
```

或指定特定焦点：
```
/speckit.brownfield-bootstrap 聚焦于用户认证模块
```

**2. 查看生成的文件**

命令将生成：

| 文件 | 路径 | 描述 |
|------|------|-------------|
| 项目宪章 | `.specify/memory/constitution.md` | 核心原则和约束 |
| 规范模板 | `.specify/templates/spec-template.md` | 功能规范模板 |
| 计划模板 | `.specify/templates/plan-template.md` | 实施计划模板 |
| 任务模板 | `.specify/templates/tasks-template.md` | 任务分解模板 |

**3. 确认宪章**

审查生成的宪章并确认或修改：
- 从代码中派生的核心原则
- 技术栈锁定版本
- 目录契约
- 模块职责（适用于多模块项目）

**4. 开始使用 SDD 工作流**

引导完成后：

```bash
# 创建新功能规范
/speckit.specify "添加用户头像上传功能"

# 生成实施计划
/speckit.plan

# 生成任务列表
/speckit.tasks

# 执行实施
/speckit.implement
```

## 生成的目录结构

运行引导命令后，您的项目将包含：

```
your-project/
├── .specify/                          # SDD 配置目录
│   ├── memory/
│   │   └── constitution.md            # 项目宪章（核心文件）
│   └── templates/
│       ├── spec-template.md           # 功能规范模板
│       ├── plan-template.md           # 实施计划模板
│       └── tasks-template.md          # 任务列表模板
└── specs/                             # 功能规范目录
    └── [###-feature-name]/            # 按功能组织
        ├── spec.md
        ├── plan.md
        └── tasks.md
```

## 开发者技能生成（新功能）

**棕地项目开发Skills生成工具**（`brownfield-skills.md` / `brownfield-skills-cn.md`）生成**项目技能**，使 Claude Code 表现得像一位维护您项目多年的高级开发者。

### 功能说明

此命令分析您的项目并生成结构化技能：

| 能力 | 描述 |
|------------|-------------|
| **精通技术栈** | 深入理解语言、框架和工具 |
| **遵循规范** | 遵守项目的编码风格和模式 |
| **理解架构** | 知道在哪里放置新代码以及模块如何交互 |
| **优先复用** | 创建新代码前总是搜索现有代码 |
| **保持兼容** | 永不破坏现有功能 |

### 使用方法

```bash
# 将技能生成工具复制到命令目录
cp brownfield-skills-cn.md .claude/commands/

# 在 AI 编码工具中生成开发者技能
```

### 生成的技能结构

```
.claude/skills/brownfield-developer-[project-name]/
├── SKILL.md                    # 技能入口点（使用指南）
└── references/
    ├── architecture.md         # 项目架构和分层
    ├── tech-stack.md           # 技术栈详情和约束
    ├── coding-conventions.md   # 编码标准和风格
    ├── module-structure.md     # 模块结构和职责
    └── development-patterns.md # 开发模式和最佳实践
```

### 主要特性

- **幂等性**：随时运行以根据当前项目状态刷新技能
- **团队共享**：将 `.claude/skills/` 添加到版本控制
- **互补性**：与 Repomix 配合使用以实现完整的项目理解

### 推荐工作流

1. 运行棕地项目开发Skills生成工具生成开发者专业知识
2. 运行 `repomix --skill-generate` 生成代码快照
3. 二者结合提供全面的项目掌握

> **提示**：在重大架构变更后重新运行此工具，保持 AI 理解的时效性。

## 使用 Repomix 增强（推荐）

对于大型棕地项目，我们推荐使用 [Repomix](https://github.com/yamadashy/repomix) 帮助 AI 编码工具更好地理解您的现有代码库。Repomix 生成结构化"技能"，作为 Claude Code 的长期记忆。

### 为什么使用 Repomix？

| 挑战 | Repomix 如何帮助 |
|-----------|-------------------|
| **上下文窗口限制** | 通过 Tree-sitter 将代码库压缩为 AI 友好格式 |
| **代码复用** | 快速搜索现有的 Utils、DTOs、Services |
| **准确性** | 生成的宪章精确反映模块结构 |
| **动态更新** | `repomix --skill-generate` 是幂等的 - 随时运行以同步 |

### 设置指南（Claude Code）

**步骤 1：安装 Repomix CLI**

```bash
npm install -g repomix
```

**步骤 2：为 Claude Code 安装 Repomix MCP**

配置 Claude Code 以支持 Repomix 的模型上下文协议：

```bash
claude mcp add repomix -- npx -y repomix --mcp
```

**步骤 3：安装 Repomix 插件（可选）**

获取便捷的斜杠命令如 `/repomix-explorer`：

```
# 在 Claude Code 交互界面中
/plugin install repomix-mcp@repomix
```

### 为项目生成技能

在项目根目录运行以下命令：

```bash
repomix --skill-generate
```

这将创建一个带有结构化引用的 `.claude/skills/` 目录：

```
.claude/skills/repomix-reference-[project-name]/
├── SKILL.md                 # 核心技能元数据
└── references/
    ├── summary.md           # 项目目的和统计
    ├── project-structure.md # 目录树及行数统计
    ├── files.md             # 完整文件内容（grep 优化）
    └── tech-stack.md        # 自动检测的技术栈
```

Claude Code 会自动加载这些技能作为其长期记忆的一部分。

### 最佳实践

| 运行时机 | 操作 |
|-------------|--------|
| **首次使用 brownfield-bootstrap** | 在引导前运行 `repomix --skill-generate` |
| **重大功能开发前** | 刷新技能以确保最新的代码库理解 |
| **重大代码变更后** | 重新运行以同步 AI 的记忆与当前代码 |

> **提示**：brownfield-bootstrap 命令已包含代码复用和理解现有代码的规则。加载 Repomix 技能后，Claude Code 将在创建新代码之前自动搜索现有实现。

## EARS 需求转换（可选前置步骤）

`/speckit.ears` 命令提供一个**可选的前置步骤**，在进入标准 SDD 工作流之前提高需求质量。它将自然语言需求转换为 [EARS（Easy Approach to Requirements Syntax）](https://alistairmavin.com/ears/) 格式。

### 为什么使用 EARS？

| 问题 | EARS 如何帮助 |
|---------|----------------|
| **需求模糊** | 固定句式模板强制明确触发条件和响应 |
| **AI 误解** | 结构化格式减少歧义，提高 AI 准确性 |
| **需求遗漏** | 分类模板确保全面覆盖 |
| **验收标准不清晰** | 每个 EARS 需求天然可测试 |

### EARS 五种需求模式

| 模式 | 模板 | 示例 |
|---------|----------|---------|
| **普遍型** | `系统应 <功能>` | 系统应加密所有用户密码 |
| **事件驱动型** | `当 <触发条件> 时，系统应 <响应>` | 当用户点击提交时，系统应验证输入 |
| **状态驱动型** | `如果 <状态>，则系统应 <行为>` | 如果用户是管理员，则系统应显示管理面板 |
| **可选功能型** | `在 <条件> 下，用户可以 <操作>` | 在启用通知的情况下，用户可以设置频率 |
| **复杂型** | `当 <触发条件>，且 <状态> 时，系统应 <响应>` | 当登录失败，且尝试次数超过5次时，系统应锁定账户 |

### 使用方法

```bash
# 将需求转换为 EARS 格式
/speckit.ears 我需要一个支持手机和邮箱的用户登录功能

# 然后继续创建规范
/speckit.specify .docs/EARS/001-user-login.md
```

### 输出位置

EARS 文档与 spec-kit 核心目录分开存储：

```
your-project/
├── .docs/                    # 文档（非 SDD 核心）
│   └── EARS/                 # EARS 需求文档
│       ├── 001-user-login.md
│       └── 002-payment.md
├── .specify/                 # SDD 配置（不变）
└── specs/                    # 功能规范（不变）
```

> **为什么单独存放？**
> EARS 需求是可选的，位于标准 spec-kit 工作流之外。将其保存在 `.docs/EARS/` 可避免干扰核心 SDD 文件。

## 语言版本

| 文件 | 语言 | 描述 |
|------|----------|-------------|
| `speckit.brownfield-bootstrap.md` | English | 棕地引导（英文） |
| `speckit.brownfield-bootstrap-cn.md` | 中文 | 棕地引导（中文） |
| `brownfield-skills.md` | English | 棕地项目开发Skills生成工具（英文） |
| `brownfield-skills-cn.md` | 中文 | 棕地项目开发Skills生成工具（中文） |
| `speckit.ears.md` | English | EARS 转换（英文） |
| `speckit.ears-cn.md` | 中文 | EARS 转换（中文） |

## 兼容性

### AI 代理

此扩展适用于任何支持自定义命令的 AI 代理：

- ✅ **Claude Code**（完整测试）
- ✅ **Cursor**（已测试）
- ✅ **GitHub Copilot**（通过 instructions）
- ✅ **Windsurf**（通过 project rules）
- ✅ **其他 AI 编码工具**（复制到命令目录）

### spec-kit 版本

- ✅ **spec-kit v0.0.18+**（使用 `/speckit.` 前缀）
- ✅ 与核心 spec-kit 工作流完全兼容
- ✅ 对现有 spec-kit 设置的非破坏性添加

### 项目类型

- ✅ 单模块项目
- ✅ Maven/Gradle 多模块项目
- ✅ Node.js Monorepo（带 workspaces）
- ✅ Go Workspace
- ✅ Rust Workspace
- ✅ Python Monorepo
- ✅ 任何语言/框架组合

## 棕地 vs 绿地

| 方面 | 绿地（`specify init`） | 棕地（此扩展） |
|--------|---------------------------|----------------------------|
| **起点** | 空项目 | 现有代码库 |
| **技术栈** | 您选择 | 自动检测并锁定 |
| **架构** | 您设计 | 逆向工程 |
| **模板** | 通用 | 项目特定 |
| **宪章** | 最小化 | 从代码分析中全面提取 |
| **多模块** | 基础 | 完整模块映射 |

## 常见问题

### 什么时候应该使用此扩展而不是 `specify init`？

使用 **brownfield-bootstrap** 当：
- 您有一个具有已建立模式的现有代码库
- 您的项目有特定的技术栈约束
- 您希望模板与现有代码风格匹配
- 您有多模块项目结构

使用 **`specify init`** 当：
- 从零开始新项目
- 您想建立新的规范
- 项目结构尚未定义

### 这会修改我现有的代码吗？

**不会！** 此命令只在 `.specify/` 和 `specs/` 目录中创建新文件。它不会修改任何现有源代码。

### 我可以自定义生成的模板吗？

可以！引导后，您可以自由修改：
- `.specify/memory/constitution.md` - 更新原则
- `.specify/templates/*.md` - 自定义模板格式

### 如果我的项目结构不寻常怎么办？

命令将：
1. 尽最大努力分析您的结构
2. 用 `[需要澄清: ...]` 标记不确定的项目
3. 询问您确认或提供指导

## 贡献

欢迎贡献！请参阅 [CONTRIBUTING.md](CONTRIBUTING.md) 了解指南。

## 许可证

MIT 许可证 - 详见 [LICENSE](LICENSE)。

## 致谢

- [GitHub spec-kit 团队](https://github.com/github/spec-kit) 提供基础
- [spec-kit-cn](https://github.com/Linfee/spec-kit-cn) 提供 spec-kit 中文本地化
- [spec-kit-extensions](https://github.com/MartyBonacci/spec-kit-extensions) 提供灵感
- [Repomix](https://github.com/yamadashy/repomix) 提供代码理解和技能生成
- 社区贡献者

## 支持

- **问题反馈**: [GitHub Issues](https://github.com/wcpaxx/spec-kit-brownfield-extensions/issues)
- **讨论**: [GitHub Discussions](https://github.com/wcpaxx/spec-kit-brownfield-extensions/discussions)
- **spec-kit**: [原始 spec-kit 仓库](https://github.com/github/spec-kit)
- **Repomix**: [代码理解工具](https://github.com/yamadashy/repomix)

---

**准备好尝试了吗？** 将命令文件复制到您的 AI 工具的命令目录并运行 `/speckit.brownfield-bootstrap`！

---
description: 为棕地项目生成"精通本项目的资深开发工程师"技能(Skills)，使AI编程工具获得持续维护该项目所需的全部专业知识。
handoffs:
  - label: 引导SDD工作流
    agent: /speckit.brownfield-bootstrap
    prompt: 基于项目技能初始化SDD工作流
  - label: 创建功能规范
    agent: /speckit.specify
    prompt: 使用项目技能创建符合项目规范的功能规范
---

## 用户输入

```text
$ARGUMENTS
```

在继续之前，你**必须**考虑用户输入（如果不为空）。

---

# 棕地项目开发技能生成器 (Brownfield Developer Skills Generator)

## 概述

此命令用于为**棕地项目（已有项目）**生成 Claude Code 可使用的 Project Skills。生成的 Skills 将赋予 AI 编程工具以下能力：

1. **精通本项目**：深度理解项目的技术栈、架构、分层和代码风格
2. **遵循开发习惯**：按照项目现有的编码规范和开发模式工作
3. **向前兼容**：在扩展功能时保持与现有代码的兼容性
4. **按需重构**：只在必要时进行重构，避免不必要的变更
5. **代码复用优先**：优先使用现有代码，避免重复造轮子
5. **TDD模式优先**：在测试框架允许的情况下，优先使用TDD模式开发

## 最高目标（不可协商）

> **生成一个熟悉本项目，拥有长期维护该项目经验的，精通项目全部技术栈的资深开发工程师技能的 Project Skills**

## ⚠️ 关键：Skills 安装位置

> **🚨 强制约束 - 必读**
>
> 本命令生成的 Skills **必须且只能**安装到以下位置：
> ```
> [项目根目录]/.claude/skills/brownfield-developer-[project-name]/
> ```
> 这是 Claude Code 自动加载 Project Skills 的标准位置。

**Skills 目录结构**：

```
.claude/skills/brownfield-developer-[project-name]/
├── SKILL.md                    # 技能入口（核心元数据和使用指南）
└── references/
    ├── architecture.md         # 项目架构和分层设计
    ├── tech-stack.md           # 技术栈详情和版本约束
    ├── coding-conventions.md   # 编码规范和代码风格
    ├── module-structure.md     # 模块结构和职责划分
    └── development-patterns.md # 开发模式和最佳实践
```

### 🚨 输出前强制自检清单

**在输出任何文件前，必须逐条确认以下检查项全部通过：**

| # | 检查项 | 正确 ✓ | 错误 ✗ | 验证方法 |
|---|--------|--------|--------|----------|
| 1 | Skills根目录 | `.claude/skills/` | `skills/` | 必须在 .claude 下 |
| 2 | 技能目录命名 | `brownfield-developer-[name]` | 其他命名 | 使用项目名称 |
| 3 | 入口文件 | `SKILL.md` | `skill.md` | 大写 SKILL |
| 4 | 引用目录 | `references/` | `reference/` | 复数形式 |
| 5 | 文件完整性 | 5个引用文件全部生成 | 遗漏任一文件 | 检查清单 |

**❌ 如果任一检查项失败，必须立即修正后再输出**

---

## 执行流程

### 阶段 0: 项目深度分析 (Deep Project Analysis)

**目标**: 像一个接手项目的资深工程师一样，全面理解项目

#### 步骤 0.1: 技术栈识别

**系统性扫描项目技术栈**：

1. **主要编程语言**:
   - 识别文件扩展名分布（.java, .ts, .py, .go, .rs 等）
   - 确定语言版本约束（package.json engines, pom.xml properties 等）
   - 识别是否为多语言项目

2. **框架和运行时**:
   - Web框架: Spring Boot, Express, Django, Gin, Actix 等
   - 前端框架: React, Vue, Angular, Svelte 等
   - 运行时: Node.js, JVM, Python, Go runtime 等

3. **构建工具和包管理**:
   - 构建: Maven, Gradle, npm/yarn/pnpm, cargo, go build 等
   - 依赖管理: 识别依赖配置文件和锁文件

4. **测试框架**:
   - 单元测试: JUnit, Jest, pytest, go test 等
   - 集成测试: Testcontainers, Supertest 等
   - E2E测试: Playwright, Cypress, Selenium 等

5. **数据存储**:
   - 数据库: MySQL, PostgreSQL, MongoDB, Redis 等
   - ORM/ODM: JPA, Prisma, SQLAlchemy, GORM 等

6. **基础设施**:
   - 容器化: Docker, docker-compose
   - CI/CD: GitHub Actions, GitLab CI, Jenkins 等
   - 云服务: AWS, GCP, Azure 等

#### 步骤 0.2: 架构模式识别

**分析项目架构风格**：

| 架构模式 | 识别特征 | 关键目录 |
|----------|----------|----------|
| 分层架构 | controller/service/repository | src/main/java/.../controller |
| 洋葱架构 | domain/application/infrastructure | src/domain, src/infrastructure |
| 六边形架构 | ports/adapters | src/adapters, src/ports |
| 微服务 | 独立服务目录 | services/, apps/ |
| Monorepo | 多包共存 | packages/, apps/, libs/ |
| 模块化单体 | 按功能模块划分 | modules/, features/ |

**分析代码组织方式**：
- 按层组织 (layer-first): controllers/, services/, models/
- 按功能组织 (feature-first): users/, orders/, payments/
- 混合组织: 识别主次组织方式

#### 步骤 0.3: 编码规范提取

**从配置文件和代码样本中提取实际规范**：

1. **命名约定**:
   - 文件命名: kebab-case, PascalCase, snake_case
   - 变量命名: camelCase, snake_case
   - 类/接口命名: PascalCase, I前缀（接口）
   - 常量命名: UPPER_SNAKE_CASE

2. **代码风格**:
   - 缩进: 空格/Tab, 数量
   - 引号: 单引号/双引号
   - 分号: 是否使用
   - 行长度限制
   - 导入组织方式

3. **注释规范**:
   - 文档注释格式: JSDoc, Javadoc, docstring
   - 行内注释风格
   - TODO/FIXME 约定

4. **Git规范**:
   - 提交消息格式: Conventional Commits, 自定义格式
   - 分支命名策略
   - PR/MR 模板

#### 步骤 0.4: 模块结构分析

**对于多模块项目，进行详细分析**：

1. **枚举所有模块**:
   ```markdown
   | 模块名 | 路径 | 类型 | 职责 |
   |--------|------|------|------|
   | [module] | [path] | [api/service/dao/common] | [职责描述] |
   ```

2. **分析模块职责**:
   - API/接口层: 对外暴露的接口定义
   - 服务实现层: 业务逻辑实现
   - 数据访问层: 数据持久化操作
   - 通用工具层: 共享的工具和基础设施

3. **分析依赖关系**:
   - 绘制模块依赖图
   - 识别依赖规则（允许/禁止的依赖方向）
   - 识别跨模块通信方式

#### 步骤 0.5: 开发模式识别

**识别项目中使用的开发模式和最佳实践**：

1. **设计模式**:
   - Repository Pattern
   - Service Layer Pattern
   - Factory Pattern
   - Strategy Pattern
   - 其他常用模式

2. **代码组织模式**:
   - DTO/VO/Entity 分离
   - 接口与实现分离
   - 配置外部化
   - 依赖注入

3. **错误处理模式**:
   - 异常层次结构
   - 统一错误响应格式
   - 错误码规范

4. **日志和可观测性**:
   - 日志框架和格式
   - 链路追踪
   - 指标收集

---

### 阶段 1: 生成 Skills 文件 (Skills Generation)

**目标**: 将分析结果转化为结构化的 Skills 文件

#### 步骤 1.1: 创建目录结构

```bash
mkdir -p .claude/skills/brownfield-developer-[project-name]/references
```

#### 步骤 1.2: 生成 SKILL.md（技能入口）

创建 `.claude/skills/brownfield-developer-[project-name]/SKILL.md`：

```markdown
# [PROJECT_NAME] 项目开发技能

## 技能概述

本技能赋予 Claude Code 作为 **[PROJECT_NAME]** 项目资深开发工程师的能力。拥有此技能后，Claude Code 将：

- 精通本项目的全部技术栈和架构设计
- 遵循本项目的编码规范和开发习惯
- 优先复用现有代码，避免重复造轮子
- 在扩展功能时保持向前兼容
- 按需重构，避免不必要的变更

## 🔑 核心技能清单

### 1. 技术栈精通
- **主要语言**: [语言及版本]
- **核心框架**: [框架列表]
- **详细信息**: 参见 [references/tech-stack.md](references/tech-stack.md)

### 2. 架构理解
- **架构风格**: [架构模式]
- **分层结构**: [分层描述]
- **详细信息**: 参见 [references/architecture.md](references/architecture.md)

### 3. 编码规范
- **命名约定**: [主要约定]
- **代码风格**: [工具/配置]
- **详细信息**: 参见 [references/coding-conventions.md](references/coding-conventions.md)

### 4. 模块结构
- **项目类型**: [单体/多模块/微服务]
- **模块数量**: [N] 个
- **详细信息**: 参见 [references/module-structure.md](references/module-structure.md)

### 5. 开发模式
- **设计模式**: [常用模式]
- **最佳实践**: [关键实践]
- **详细信息**: 参见 [references/development-patterns.md](references/development-patterns.md)

## 🚨 棕地项目开发原则

### 原则一：尊重现有架构
> **不要试图"改进"现有架构，而是准确理解并遵循它**

- 新代码必须与现有架构风格保持一致
- 架构调整需要充分的理由和评估

### 原则二：代码复用优先
> **创建新代码之前，必须先查找现有实现**

执行顺序：
1. 搜索项目中是否已有相似功能
2. 检查 common/utils/shared 等共享模块
3. 确认无可复用代码后，才创建新代码

### 原则三：向前兼容
> **新增功能不能破坏现有功能**

- 添加而非修改（Open/Closed 原则）
- 保持现有 API 的向后兼容性
- 充分的回归测试

### 原则四：按需重构
> **只在必要时进行重构，避免过度工程**

重构触发条件：
- 影响新功能的实现
- 存在明显的代码异味
- 用户明确要求

### 原则五：兼容性优先
> **所有生成的代码必须与现有代码风格一致**

- 使用相同的命名约定
- 使用相同的代码格式
- 使用相同的目录结构

## 📋 使用指南

### 在开发新功能时

1. **首先阅读相关 references 文件**了解项目规范
2. **搜索现有实现**确认是否有可复用代码
3. **遵循模块结构**将代码放在正确的位置
4. **遵循编码规范**保持代码风格一致
5. **编写测试**使用项目的测试框架

### 在理解现有代码时

使用 Repomix 生成或更新 skills：
```bash
repomix --skill-generate
```

### 在修改现有代码时

1. **理解影响范围**：确认修改会影响哪些模块
2. **保持兼容性**：确保不破坏现有功能
3. **充分测试**：运行相关测试确认无回归

## 📂 引用文件

| 文件 | 说明 |
|------|------|
| [architecture.md](references/architecture.md) | 项目架构和分层设计 |
| [tech-stack.md](references/tech-stack.md) | 技术栈详情和版本约束 |
| [coding-conventions.md](references/coding-conventions.md) | 编码规范和代码风格 |
| [module-structure.md](references/module-structure.md) | 模块结构和职责划分 |
| [development-patterns.md](references/development-patterns.md) | 开发模式和最佳实践 |

---

**版本**: 1.0.0 | **生成日期**: [DATE] | **来源**: /speckit.skills
```

#### 步骤 1.3: 生成 architecture.md

创建 `.claude/skills/brownfield-developer-[project-name]/references/architecture.md`：

```markdown
# [PROJECT_NAME] 项目架构

## 架构风格

**主要架构模式**: [分层架构/洋葱架构/六边形架构/微服务/...]

**架构示意图**:
```
[根据实际架构绘制示意图]
```

## 分层结构

### [层1名称]
- **职责**: [职责描述]
- **位置**: [目录路径]
- **典型组件**: [组件类型列表]

### [层2名称]
- **职责**: [职责描述]
- **位置**: [目录路径]
- **典型组件**: [组件类型列表]

[继续列出所有层...]

## 依赖规则

### 允许的依赖方向
- [上层] → [下层]
- 示例: Controller → Service → Repository

### 禁止的依赖方向
- [下层] → [上层]
- 循环依赖

## 关键架构决策

| 决策 | 选择 | 理由 |
|------|------|------|
| [决策1] | [选择] | [理由] |
| [决策2] | [选择] | [理由] |

## 扩展指南

### 添加新功能时
1. [步骤1]
2. [步骤2]
3. [步骤3]

### 添加新模块时
1. [步骤1]
2. [步骤2]
3. [步骤3]
```

#### 步骤 1.4: 生成 tech-stack.md

创建 `.claude/skills/brownfield-developer-[project-name]/references/tech-stack.md`：

```markdown
# [PROJECT_NAME] 技术栈

## 核心技术栈（锁定）

> ⚠️ 以下技术栈由项目确定，新代码必须使用相同的技术

| 类别 | 技术 | 版本 | 说明 |
|------|------|------|------|
| **语言** | [语言] | [版本] | [说明] |
| **运行时** | [运行时] | [版本] | [说明] |
| **框架** | [框架] | [版本] | [说明] |
| **构建工具** | [工具] | [版本] | [说明] |
| **测试框架** | [框架] | [版本] | [说明] |

## 依赖详情

### 生产依赖
| 依赖 | 版本 | 用途 |
|------|------|------|
| [依赖1] | [版本] | [用途] |
| [依赖2] | [版本] | [用途] |

### 开发依赖
| 依赖 | 版本 | 用途 |
|------|------|------|
| [依赖1] | [版本] | [用途] |
| [依赖2] | [版本] | [用途] |

## 数据存储

| 类型 | 技术 | 用途 |
|------|------|------|
| 主数据库 | [数据库] | [用途] |
| 缓存 | [缓存技术] | [用途] |
| 消息队列 | [MQ技术] | [用途] |

## 基础设施

| 类别 | 技术 | 配置文件 |
|------|------|----------|
| 容器化 | [Docker/etc] | [文件路径] |
| CI/CD | [工具] | [配置路径] |
| 部署 | [平台] | [配置路径] |

## 版本约束

### 必须遵守
- [约束1]
- [约束2]

### 升级指南
- 升级前必须[操作]
- 升级后必须[验证]
```

#### 步骤 1.5: 生成 coding-conventions.md

创建 `.claude/skills/brownfield-developer-[project-name]/references/coding-conventions.md`：

```markdown
# [PROJECT_NAME] 编码规范

## 命名约定

### 文件命名
| 类型 | 约定 | 示例 |
|------|------|------|
| 组件文件 | [约定] | [示例] |
| 服务文件 | [约定] | [示例] |
| 测试文件 | [约定] | [示例] |
| 配置文件 | [约定] | [示例] |

### 代码命名
| 类型 | 约定 | 示例 |
|------|------|------|
| 类/接口 | PascalCase | UserService |
| 方法/函数 | camelCase/snake_case | getUserById |
| 变量 | camelCase/snake_case | userId |
| 常量 | UPPER_SNAKE_CASE | MAX_RETRY_COUNT |
| 私有成员 | [约定] | [示例] |

## 代码格式

### 工具配置
- **格式化工具**: [工具名称]
- **配置文件**: [配置路径]
- **运行命令**: [命令]

### 格式规则
- **缩进**: [空格数/Tab]
- **行长度**: [最大字符数]
- **引号**: [单引号/双引号]
- **分号**: [是/否]
- **尾逗号**: [是/否]

### 导入组织
1. [导入组1：如标准库]
2. [导入组2：如第三方库]
3. [导入组3：如项目内部模块]

## 注释规范

### 文档注释
```[语言]
[文档注释示例]
```

### 行内注释
- [规则1]
- [规则2]

### TODO/FIXME
- TODO: [格式]
- FIXME: [格式]

## Git 规范

### 提交消息格式
```
[格式模板]
```

### 提交类型
| 类型 | 说明 |
|------|------|
| feat | 新功能 |
| fix | Bug修复 |
| docs | 文档更新 |
| [其他类型] | [说明] |

### 分支命名
- 功能分支: [格式]
- 修复分支: [格式]
- 发布分支: [格式]

## 代码质量工具

| 工具 | 用途 | 配置文件 | 运行命令 |
|------|------|----------|----------|
| [Linter] | 代码检查 | [配置] | [命令] |
| [Formatter] | 代码格式化 | [配置] | [命令] |
| [TypeChecker] | 类型检查 | [配置] | [命令] |
```

#### 步骤 1.6: 生成 module-structure.md

创建 `.claude/skills/brownfield-developer-[project-name]/references/module-structure.md`：

```markdown
# [PROJECT_NAME] 模块结构

## 项目类型

**结构类型**: [单体应用/多模块项目/Monorepo/微服务]
**模块数量**: [N] 个

## 模块清单

| 模块名 | 路径 | 职责分类 | 核心职责 |
|--------|------|----------|----------|
| [模块1] | [路径] | [分类] | [职责描述] |
| [模块2] | [路径] | [分类] | [职责描述] |

## 模块职责详解

### [模块1名称]
- **路径**: [完整路径]
- **职责**: [详细职责描述]
- **可放置的代码类型**:
  - [代码类型1]
  - [代码类型2]
- **典型目录结构**:
  ```
  [模块内部结构]
  ```

### [模块2名称]
[同上格式...]

## 模块依赖关系

### 依赖图
```
[app/boot]
├── [service-module-1]
│   ├── [api-module-1]
│   └── [common]
├── [service-module-2]
│   ├── [api-module-2]
│   └── [common]
└── [common]
```

### 依赖规则
- **允许**: [规则描述]
- **禁止**: [规则描述]
- **跨模块通信**: [通信方式]

## 代码放置决策树

### 新增功能代码放置指南

```
是否是对外暴露的接口/DTO?
├── 是 → [api模块]
└── 否 → 是否是业务逻辑/服务实现?
    ├── 是 → [service模块]
    └── 否 → 是否是数据库实体/数据访问?
        ├── 是 → [dao模块]
        └── 否 → 是否是跨模块共享的工具?
            ├── 是 → [common模块]
            └── 否 → 咨询架构师或创建新模块
```

### 代码类型速查表

| 代码类型 | 目标模块 | 目标路径 |
|----------|----------|----------|
| REST API 端点 | [模块] | [路径] |
| Service 接口 | [模块] | [路径] |
| Service 实现 | [模块] | [路径] |
| 数据库 Entity | [模块] | [路径] |
| DTO/VO | [模块] | [路径] |
| 工具类 | [模块] | [路径] |
| 配置类 | [模块] | [路径] |
| 测试代码 | [模块] | [路径] |
```

#### 步骤 1.7: 生成 development-patterns.md

创建 `.claude/skills/brownfield-developer-[project-name]/references/development-patterns.md`：

```markdown
# [PROJECT_NAME] 开发模式

## 设计模式

### 常用模式清单

| 模式 | 用途 | 典型示例 |
|------|------|----------|
| Repository Pattern | 数据访问抽象 | [示例类] |
| Service Layer | 业务逻辑封装 | [示例类] |
| Factory Pattern | 对象创建 | [示例类] |
| [其他模式] | [用途] | [示例] |

### 模式使用指南

#### Repository Pattern
```[语言]
[代码示例]
```

#### Service Layer
```[语言]
[代码示例]
```

## 代码组织模式

### DTO/VO/Entity 分离
- **Entity**: [说明和位置]
- **DTO**: [说明和位置]
- **VO**: [说明和位置]

### 接口与实现分离
- 接口定义位置: [路径]
- 实现类位置: [路径]
- 命名约定: [约定]

## 错误处理模式

### 异常层次结构
```
BaseException
├── BusinessException
│   ├── [具体业务异常]
│   └── [具体业务异常]
└── SystemException
    ├── [具体系统异常]
    └── [具体系统异常]
```

### 统一错误响应格式
```[语言]
[错误响应示例]
```

### 错误码规范
| 范围 | 类型 | 示例 |
|------|------|------|
| [范围1] | [类型] | [示例] |
| [范围2] | [类型] | [示例] |

## 日志规范

### 日志框架
- **框架**: [框架名称]
- **配置**: [配置文件路径]

### 日志格式
```
[日志格式示例]
```

### 日志级别使用
| 级别 | 使用场景 |
|------|----------|
| ERROR | [场景] |
| WARN | [场景] |
| INFO | [场景] |
| DEBUG | [场景] |

## 测试模式

### 测试结构
```
[测试目录结构]
```

### 单元测试模式
```[语言]
[单元测试示例]
```

### 集成测试模式
```[语言]
[集成测试示例]
```

### Mock 使用规范
- Mock 框架: [框架名称]
- Mock 范围: [规则]

## 配置管理

### 配置文件结构
```
[配置文件列表]
```

### 环境配置
| 环境 | 配置文件 | 说明 |
|------|----------|------|
| 开发 | [文件] | [说明] |
| 测试 | [文件] | [说明] |
| 生产 | [文件] | [说明] |

### 敏感配置处理
- [规则1]
- [规则2]
```

---

### 阶段 2: Skills 安装与验证 (Installation & Validation)

**目标**: 确保 Skills 正确安装并可被 Claude Code 加载

#### 步骤 2.1: 安装验证

**验证 Skills 目录结构**：

```bash
# 检查目录结构
ls -la .claude/skills/brownfield-developer-[project-name]/
ls -la .claude/skills/brownfield-developer-[project-name]/references/
```

**验证必需文件存在**：

| 文件 | 路径 | 状态 |
|------|------|------|
| 技能入口 | `.claude/skills/brownfield-developer-[name]/SKILL.md` | ✓/✗ |
| 架构文档 | `.../references/architecture.md` | ✓/✗ |
| 技术栈文档 | `.../references/tech-stack.md` | ✓/✗ |
| 编码规范 | `.../references/coding-conventions.md` | ✓/✗ |
| 模块结构 | `.../references/module-structure.md` | ✓/✗ |
| 开发模式 | `.../references/development-patterns.md` | ✓/✗ |

#### 步骤 2.2: 幂等性验证

**确认重复执行的结果一致**：

此命令支持重复执行：
- 每次执行都根据项目**当前状态**重新分析
- 所有 Skills 文件会被**完全覆盖**
- 无需手动删除旧文件

**版本管理**：
- SKILL.md 中的生成日期会更新
- 建议将 `.claude/skills/` 加入版本控制
- 团队成员可共享项目技能

#### 步骤 2.3: 生成完成报告

```markdown
## Skills 生成完成报告

**项目**: [项目名称]
**生成时间**: [日期时间]
**状态**: ✅ 成功

### 生成文件清单

| 文件 | 路径 | 状态 |
|------|------|------|
| SKILL.md | `.claude/skills/brownfield-developer-[name]/SKILL.md` | ✅ |
| architecture.md | `.../references/architecture.md` | ✅ |
| tech-stack.md | `.../references/tech-stack.md` | ✅ |
| coding-conventions.md | `.../references/coding-conventions.md` | ✅ |
| module-structure.md | `.../references/module-structure.md` | ✅ |
| development-patterns.md | `.../references/development-patterns.md` | ✅ |

### Skills 摘要

**技术栈**: [主要技术栈]
**架构**: [架构风格]
**模块数**: [N] 个

### 验证结果

- [x] Skills 目录结构正确
- [x] 所有必需文件已生成
- [x] SKILL.md 入口文件有效
- [x] 引用文件链接正确

### 下一步操作

1. **验证 Skills 加载**: 重启 Claude Code 或刷新会话
2. **测试技能效果**: 尝试询问项目相关问题
3. **保持同步**: 项目重大变更后重新运行 `/speckit.skills`

### 建议命令

```bash
# 验证 Skills 已安装
ls .claude/skills/

# 如果使用 SDD 工作流，继续引导
/speckit.brownfield-bootstrap

# 直接开始开发
# Claude Code 将自动使用项目技能
```
```

---

## 通用指南

### 棕地项目特殊考量

1. **尊重现有架构**: Skills 应准确反映项目现状，而非"改进"它
2. **技术栈锁定**: 项目的技术选型是既定事实，Skills 必须锚定它
3. **兼容性优先**: Skills 指导生成的所有代码必须与现有代码风格一致
4. **禁止代码重复**: Skills 必须强调代码复用原则
5. **理解现有代码**: 推荐配合 Repomix 使用，增强代码理解能力

### 处理不确定性

当无法从代码中确定某些约定时：

1. **优先使用行业标准**: 基于技术栈的最佳实践
2. **标记待确认**: 使用 `[NEEDS CLARIFICATION: 问题描述]` 标记
3. **限制数量**: 最多3个待确认项
4. **提供选项**: 为每个待确认项提供2-3个建议选项

### 与 Repomix 的配合

此命令与 Repomix 互补：

| 工具 | 关注点 | 输出 |
|------|--------|------|
| `/speckit.skills` | 开发技能和规范 | 结构化的开发指南 |
| `repomix --skill-generate` | 代码内容和结构 | 代码快照和索引 |

**推荐工作流**：
1. 先运行 `repomix --skill-generate` 生成代码快照
2. 再运行 `/speckit.skills` 生成开发技能
3. 两者共同提供完整的项目理解

### 错误处理

| 场景 | 处理方式 |
|------|----------|
| 无法识别项目类型 | 询问用户确认主要技术栈 |
| 目录结构异常 | 使用最佳猜测并标记不确定项 |
| 多语言项目 | 识别主要语言，列出所有语言 |
| 极简项目 | 生成基础 Skills，标记可扩展项 |

---

## 上下文

{ARGS}

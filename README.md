# Codex Assistant

> 通过自然语言调用 OpenAI Codex CLI 执行代码任务

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Platform](https://img.shields.io/badge/platform-macOS%2FLinux-lightgrey)
![License](https://img.shields.io/badge/license-MIT-orange)

---

## 为什么需要这个工具？

OpenAI Codex 是一个强大的 AI 编程助手，但直接使用命令行不够直观：

- ❌ 需要记住复杂的命令参数
- ❌ 难以与 Claude Code 等工具集成
- ❌ 缺少最佳场景指引

**这个 Skill 解决了这些痛点**：
- ✅ 自然语言触发，无需记忆命令
- ✅ 内置最佳场景提示词模板
- ✅ 一键执行，返回结果
- ✅ 与 Claude Code 无缝协作

---

## 核心功能

| 场景 | Codex 擅长 | 触发示例 |
|------|-----------|---------|
| **代码重构** | 优化结构、提升可读性 | `/codex-assistant 重构这段代码` |
| **Bug 修复** | 定位问题、给出修复 | `/codex-assistant 找出并修复 bug` |
| **测试生成** | 编写单元测试 | `/codex-assistant 给这个函数写测试` |
| **代码解释** | 逐行解释逻辑 | `/codex-assistant 解释这段代码` |
| **跨语言迁移** | 语言/框架转换 | `/codex-assistant 转成 TypeScript` |
| **代码审查** | 找出问题、改进建议 | `/codex-assistant 审查这段代码` |
| **文档生成** | 添加注释/文档 | `/codex-assistant 给这个函数写文档` |
| **样板代码** | 生成模板/脚手架 | `/codex-assistant 写一个组件模板` |
| **代码清理** | 移除技术债务 | `/codex-assistant 清理这段代码` |

---

## 安装

### 方式一：`npx skills add`（推荐）

使用 Vercel 的 skills 生态系统一键安装：

```bash
npx skills add joeseesun/codex-assistant
```

> 支持 Claude Code、OpenManus 等兼容 `skills` 标准的 AI Agent

### 方式二：Claude Code 一键安装

直接告诉 Claude Code：

```
安装这个 skill：https://github.com/joeseesun/codex-assistant
```

Claude Code 会自动完成所有安装步骤！

### 方式三：手动安装

#### 1. 安装 Codex CLI

**macOS:**

```bash
# 使用 Homebrew 安装
brew install codex-cli/codex/codex

# 或通过 npm
npm install -g @openai/codex
```

**验证安装：**

```bash
codex --version
# 应该显示类似: OpenAI Codex v0.89.0
```

#### 2. 配置 Codex

```bash
# 登录 Codex（需要 OpenAI 账户）
codex login

# 添加信任目录（可选，但推荐）
codex config set projects."$(pwd)" trust_level=trusted
```

#### 3. 克隆 Skill

```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/joeseesun/codex-assistant.git \
  ~/.claude/skills/codex-assistant
```

---

## 使用方法

### 方式一：通过 Claude Code 对话

```
你：/codex-assistant 重构这段代码，让它更简洁
Codex：[自动执行并返回结果]

你：用 Codex 帮我写一个快速排序
Codex：[生成代码]
```

### 方式二：直接使用 Codex CLI

```bash
# 进入信任目录
cd /path/to/your/project

# 执行任务
echo "写一个快速排序算法" | codex exec
```

---

## 使用示例

### 示例 1：代码重构

```
你：/codex-assistant 重构这段代码，消除重复逻辑

Codex：[分析代码并提供重构方案]
```

### 示例 2：Bug 修复

```
你：/codex-assistant 帮我找出并修复这个 bug
[粘贴有问题的代码]

Codex：[定位问题并给出修复]
```

### 示例 3：测试生成

```
你：/codex-assistant 给这个函数写单元测试
[粘贴函数代码]

Codex：[生成测试用例]
```

### 示例 4：跨语言迁移

```
你：/codex-assistant 把这段 Python 转成 TypeScript
[粘贴 Python 代码]

Codex：[生成等价的 TypeScript 代码]
```

---

## 最佳实践

### Codex 适合的场景

- ✅ **小到中型代码任务** - 函数重构、单文件修改
- ✅ **明确的任务描述** - 知道要什么，但不确定怎么实现
- ✅ **快速原型** - 快速生成样板代码
- ✅ **代码解释** - 理解不熟悉的代码

### Codex 不太适合的场景

- ❌ **大型重构** - 跨多文件的复杂改动
- ❌ **模糊需求** - 不确定要什么
- ❌ **生产代码** - 建议 review 后使用

### 提升效果的建议

1. **提供上下文** - 告诉 Codex 你在做什么项目
2. **明确约束** - 说明语言、风格、要求
3. **迭代优化** - 基于结果多次调整

---

## 系统要求

- **平台**: macOS / Linux
- **Codex CLI**: >= 0.89.0
- **工作目录**: 建议在 git 仓库或信任目录中

---

## 常见问题

**Q: Codex 返回空结果怎么办？**

A: 确保工作目录在 Codex 信任列表中：
```bash
codex config set projects."$(pwd)" trust_level=trusted
```

**Q: 如何切换模型？**

A: 使用 `-m` 参数指定模型：
```bash
echo "任务" | codex exec -m gpt-4o
```

**Q: Codex 是免费的吗？**

A: Codex CLI 本身免费，但调用 OpenAI API 消耗配额。

**Q: 支持 Windows 吗？**

A: 支持，但需要在 WSL 或 Git Bash 中运行。

---

## 更新日志

### v1.0.0 (2026-01-24) - 首次发布

- 自然语言触发
- 9 种最佳场景模板
- 与 Claude Code 集成
- 详细文档

---

## 贡献

欢迎贡献！请提交 Issue 或 Pull Request。

---

## 许可证

MIT License

---

## 联系方式

- **作者**: Qiaomu (乔木)
- **GitHub**: [@joeseesun](https://github.com/joeseesun)
- **Email**: vista8@gmail.com
- **个人网站**: [qiaomu.ai](https://qiaomu.ai/)

---

**⭐ 如果这个工具对你有帮助，请给个 Star！**

_让 AI 编程助手触手可及_

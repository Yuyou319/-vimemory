# ViMemory

> 通用记忆系统 for AI Coding Tools — 一次编写，到处同步
> 
> Universal Memory System for AI Coding Tools — Write Once, Sync Everywhere

让你在不同 AI 编程工具（Cursor、Claude Code、Windsurf、CodeBuddy、Cline、Trae 等）间自由切换，记忆永远跟着你走。

Switch between AI coding tools freely — your memory stays with you.

---

## 为什么选择 ViMemory？ / Why ViMemory?

### 1. 极致轻量 / Ultra Lightweight

| 指标 | ViMemory | 其他方案 |
|------|----------|----------|
| 安装包大小 | ~5 MB | 通常 50MB+ |
| 依赖数量 | 2 个 (chalk, commander) | 动辄几十个 |
| 启动速度 | 毫秒级 | 秒级 |
| 内存占用 | 几乎为零 | 常驻后台服务 |

**无后台服务、无数据库、无复杂配置。** 纯文本 + CLI，简单到不会坏。

**No background service, no database, no complex config.** Plain text + CLI, too simple to break.

### 2. 使用极其方便 / Incredibly Easy to Use

```bash
# 三步上手 / Three steps to start
npm install -g .
vimemory init --global
vimemory sync
```

- **一次配置** — 填写你的身份和偏好，永久生效
- **一键同步** — `vimemory sync` 同时更新 8 个工具的规则文件
- **随手记录** — `vimemory add "今天发现..."` 碎片记忆自动归档

- **Configure once** — fill in your identity and preferences, permanent effect
- **One-click sync** — `vimemory sync` updates rules for 8 tools simultaneously
- **Jot anytime** — `vimemory add "found that..."` fragments auto-archived

### 3. 对比其他记忆方案 / Compared to Other Solutions

| 特性 | ViMemory | 手动复制粘贴 | 云端记忆服务 |
|------|----------|-------------|-------------|
| 跨工具同步 | ✅ 一键 8 个工具 | ❌ 每个工具单独配 | ⚠️ 仅支持部分工具 |
| 隐私安全 | ✅ 完全本地，不上传 | ✅ 本地 | ❌ 数据上传云端 |
| 离线可用 | ✅ 随时可用 | ✅ | ❌ 需联网 |
| 版本控制 | ✅ Git 原生支持 | ❌ | ⚠️ 有限 |
| 迁移成本 | ✅ git clone 即用 | ❌ 手动拷贝 | ❌ 锁定平台 |
| 自定义程度 | ✅ 完全开放源码 | ⚠️ 受工具限制 | ❌ 受服务限制 |
| 学习成本 | ⭐ 极低 | ⭐⭐ 中等 | ⭐⭐⭐ 较高 |

**核心优势：你拥有完全的控制权。** 源码在手，随时修改，不受任何平台限制。

**Core advantage: you have full control.** Source code in hand, modify anytime, no platform lock-in.

### 4. 真正通用 / Truly Universal

支持 **8 个主流 AI 编程工具**：

Supports **8 major AI coding tools**:

| 工具 / Tool | 输出文件 / Output |
|------------|------------------|
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursorrules` |
| Windsurf | `.windsurfrules` |
| CodeBuddy | `.codebuddy/rules/project/rule.md` |
| Cline | `.clinerules` |
| Aider | `.aider.conf.yml` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Trae | `.trae/rules/*.md` |

**换工具？git clone 即可，零配置。**

**Switching tools? Just git clone, zero config.**

---

## 快速开始 / Quick Start

```bash
# 安装 / Install
npm install -g .

# 初始化全局记忆（首次使用）/ Init global memory (first time)
vimemory init --global

# 进入项目，初始化项目记忆 / Init project memory
cd your-project
vimemory init --project

# 编辑记忆文件，填写你的信息 / Edit memory files
# ~/.vimemory/IDENTITY.md  → 你的身份 & 习惯 / Your identity & habits
# ~/.vimemory/COGNITION.md → 你的认知 & 偏好 / Your cognition & preferences
# .vimemory/PROJECT.md     → 项目概述 / Project overview
# .vimemory/CONVENTIONS.md → 编码规范 / Coding conventions

# 同步到所有 AI 工具 / Sync to all AI tools
vimemory sync
```

---

## 命令 / Commands

```bash
vimemory init                    # 初始化全局 + 项目记忆 / Init global + project
vimemory init --global           # 只初始化全局 / Init global only
vimemory init --project          # 只初始化项目 / Init project only

vimemory sync                    # 同步到所有工具 / Sync to all tools
vimemory sync --target claude    # 只同步到 Claude / Sync to Claude only
vimemory sync --force            # 强制覆盖已有文件 / Force overwrite
vimemory sync --dry-run          # 预览不写入 / Preview without writing

vimemory add "完成了用户模块"     # 添加碎片记忆 / Add fragment memory
vimemory add --layer daily "xxx" # 添加到今日记忆 / Add to daily memory
vimemory add --layer identity "xxx"  # 追加到身份层 / Append to identity
vimemory add --layer cognition "xxx" # 追加到认知层 / Append to cognition
vimemory add --layer decision "选A不选B|理由"  # 添加决策 / Add decision

vimemory consolidate             # 手动提炼记忆 / Manual consolidation
vimemory status                  # 查看状态 / View status
vimemory guide                   # 使用指南 / Usage guide
```

---

## 记忆架构 / Memory Architecture

### 全局记忆（跟人走）/ Global Memory (Follows You)

| 层 / Layer | 文件 / File | 说明 / Description |
|-----------|------------|-------------------|
| L1 | SOUL.md | AI 行为准则 / AI behavior guidelines |
| L2 | IDENTITY.md | 你的身份 & 习惯 / Your identity & habits |
| L3 | COGNITION.md | 你的认知 & 偏好 / Your cognition & preferences |
| L4 | CONFIG.md | 全局配置 / Global config |
| L5 | MEMORY.md | 永久记忆（自动提炼）/ Permanent memory (auto-consolidated) |
| L6 | daily/ | 临时记忆 / Temporary memory |
| L7 | fragments/ | 碎片记忆 / Fragment memory |

### 项目记忆（跟项目走）/ Project Memory (Follows Project)

| 层 / Layer | 文件 / File | 说明 / Description |
|-----------|------------|-------------------|
| P1 | PROJECT.md | 项目概述 / Project overview |
| P2 | ARCHITECTURE.md | 架构设计 / Architecture design |
| P3 | CONVENTIONS.md | 编码规范 / Coding conventions |
| P4 | API.md | 接口文档 / API documentation |
| P5 | DATABASE.md | 数据库设计 / Database design |
| P6 | DECISIONS.md | 决策记录（自动追加）/ Decision records (auto-appended) |
| P7 | daily/ | 临时记忆 / Temporary memory |

---

## 工作原理 / How It Works

```
你编辑源文件 / You edit source files
    ↓
.vimemory/ 目录 / .vimemory/ directory
    ↓
vimemory sync
    ↓
自动生成 8 个工具的规则文件 / Auto-generate 8 tool rule files
    ↓
各工具自动读取 / Tools auto-read
```

**核心设计：单一数据源。** 你只维护 `.vimemory/` 里的源文件，其余全部自动生成。

**Core design: single source of truth.** You only maintain source files in `.vimemory/`, everything else is auto-generated.

---

## 技术栈 / Tech Stack

- **Runtime**: Node.js (>= 14)
- **Dependencies**: chalk (CLI colors), commander (CLI framework)
- **Storage**: Plain Markdown files (zero database)
- **Sync**: File-based translation engine

---

## License

MIT

---

## 作者 / Author

Yubangwang (Yuyou319)

---

> **ViMemory** — 让 AI 记住你，无论你在哪个工具里。
>
> **ViMemory** — Let AI remember you, no matter which tool you're in.

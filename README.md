# Pi Memory Extension

> 一个面向 Pi Coding Agent 的持久化记忆扩展。
> 通过人工治理、Markdown 存储和可选 Git 管理，为 Pi 提供跨 session 的长期知识能力。
> 第一版专注 Pi，不尝试替代 Codex / Claude Code 自身的 memory 机制。

## Philosophy

1. **Human decides what becomes memory.** 只有人工确认的知识才进入权威文件。
2. **Markdown is the source of truth.** 纯文本，Git 可 diff、可回滚、可审查。
3. **Session history is not memory.** Pi JSONL 是原始记录，memory 是提炼后的知识。

## 安装

```bash
# 从 GitHub 安装
pi install git:github.com:appleface2050/pi-memory-extension

# 重启 Pi 或 /reload
```

## 快速开始

```bash
# 1. 初始化 Global Memory（个人偏好、通用知识）
/memory:init global

# 2. 初始化 Workspace Memory（当前项目知识）
cd your-project
/memory:init workspace

# 3. 查看记忆状态
/memory:status
/memory:list
```

## 命令一览

| 命令 | 描述 |
|------|------|
| `/memory:init global` | 初始化 `~/.pi/memory/`（个人层级） |
| `/memory:init workspace` | 初始化当前项目的 `.pi/memory/`（项目层级） |
| `/memory:status` | 显示当前加载的 Global + Workspace 文件详情 |
| `/memory:list` | 显示 Global 和 Workspace 的文件数 |
| `/memory:refresh` | 重新加载全部记忆文件 |
| `/memory:checkpoint` | 生成 session 摘要到 workspace inbox（需先 init workspace） |
| `/memory:promote <file> <targetDir> <targetFile>` | 将 inbox 内容提炼到权威文件 |
| `/memory:clear-task` | 清空 state/current-task.md（中断恢复后） |

## 存储结构

### Global Memory (`~/.pi/memory/`)

```
~/.pi/memory/
├── user/                       # 个人偏好
│   ├── preferences.md
│   ├── coding-style.md
│   └── tools.md
├── facts/                      # 背景事实
│   ├── environment.md
│   └── references.md
├── knowledge/                  # 跨项目知识
│   ├── decisions.md
│   ├── patterns.md
│   ├── lessons.md
│   └── bugs.md
├── state/                      # 工作状态
│   └── current-task.md
├── inbox/                      # 待确认候选
└── archive/                    # 历史归档
```

### Workspace Memory (`project/.pi/memory/`)

```
project/.pi/memory/
├── decisions.md
├── patterns.md
├── lessons.md
├── experiments.md
├── inbox/
└── archive/
```

## 设计文档

详见 [docs/design.md](docs/design.md)。

## 许可证

MIT

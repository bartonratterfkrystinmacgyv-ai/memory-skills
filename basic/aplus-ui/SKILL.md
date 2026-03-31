---
name: aplus-ui
description: 初始化并维护前端项目的记忆索引（Memory Index System），包含 /init 建树流 与 日常四步消费流。
license: Proprietary
metadata:
  language: zh-CN
  category: frontend
  system: memory-index
---

# Aplus UI Memory Index Skill

## 目标
为前端项目提供一套可持续维护的记忆索引系统：
- `/init` 时执行建树
- 日常任务执行前强制先读 `docs/INDEX.md`
- 代码修改后同步回写对应 `docs/state-*.md`

## Memory Creation Flow
当且仅当用户输入 `/init` 时，必须严格执行：

### 1. 环境握手
暂停代码编写，先询问：
“准备初始化记忆树。请问当前环境是 OpenCode、Trae、Cursor 还是其他 AI 工具？”

### 2. 规则注入
根据工具生成对应规则文件，并强制注入铁律：
- 在执行任何代码修改前，必须利用文件读取能力查阅 `docs/INDEX.md`

约束：
- 如生成工具配置项，严禁使用 `env` 属性
- OpenCode 使用 `environment` 或省略

### 3. 架构嗅探与拓扑生成
扫描根目录关键特征：
- `package.json`
- `vite.config.ts`
- `pnpm-workspace.yaml`
- `apps/`
- `packages/`

识别项目形态后：
- 创建 `docs/INDEX.md`
- 创建对应 `docs/state-*.md`
- 注入基础模板：
  - `## 架构规范`
  - `## 已通链路`
  - `## TODO 遗留`

## Memory Consumption Flow
每次处理代码任务都必须走完：

### Step 1: 路由寻址
第一步永远是静默读取 `docs/INDEX.md`

### Step 2: 上下文切片加载
根据 INDEX 路由映射，只读取对应模块的 `docs/state-*.md`

### Step 3: 业务执行
基于上下文修改代码，遵守现有类型和封装

### Step 4: 记忆归档
修改完成后，必须更新对应 `docs/state-*.md`：
- 划掉已完成 TODO
- 更新已通链路
- 必要时补充架构规范

最终回复：
✅ 代码已修改，且最新状态已同步至文档。

## 安装后建议生成到项目根目录的文件
- `docs/INDEX.md`
- `docs/state-api.md`
- `docs/state-client.md`
- `docs/state-staff.md`
- `.cursor/rules/memory-tree.mdc`
- `AGENTS.md`
- `opencode.jsonc`

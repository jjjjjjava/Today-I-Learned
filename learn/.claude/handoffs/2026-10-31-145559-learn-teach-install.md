# Handoff: learn / teach 安装交接

## Session Metadata

- Created: 2026-10-31 14:55:59 +0800
- Project: /Users/panruiqi/learn
- 安装仓库: /Users/panruiqi/learn/.pi
- 安装版本: 7cfd8942f82ab9476e63572387e1fe9bcea5082c
- 范围: 只记录 learn / teach 安装，不包含其他讨论。

## Current State Summary

learn 基础安装已完成，采用项目级安装，位置为 /Users/panruiqi/learn/.pi。teach 是 learn 仓库中的 skill，不是独立 npm package。已验证 Pi 能加载扩展并发现 teach 命令；尚未进行真实教学会话和交互弹窗验收。没有修改全局 Pi 设置，没有安装可视化依赖，也没有配置 Obsidian。安装任务没有待完成的必需步骤，不要重复克隆或自动扩展集成范围。

## Architecture Overview

上游仓库整体作为学习项目的 .pi 目录。Pi 在该项目启动、信任项目资源后加载 skills 和 extensions。teach 使用 probe → plan → teach 流程：测验定位基础、提出学习计划、用户确认后逐步教学。基础教学不依赖子代理。

## Critical Files

| File | Purpose | Relevance |
|------|---------|-----------|
| /Users/panruiqi/learn/.pi/README.md | 上游说明 | 安装方式与可选能力 |
| /Users/panruiqi/learn/.pi/skills/teach/SKILL.md | 教学流程 | teach 入口 |
| /Users/panruiqi/learn/.pi/extensions/ask-user-question.ts | 交互提问 | 学习偏好与选择 |
| /Users/panruiqi/learn/.pi/extensions/quiz.ts | 测验交互 | 学习基础探测与检验 |
| /Users/panruiqi/learn/.pi/extensions/md-log.ts | 可选 Markdown 日志 | 当前未绑定笔记 |
| /Users/panruiqi/learn/.pi/extensions/visual-tools/index.ts | 可选绘图工具入口 | 当前未接通绘图链路 |

## Work Completed

- [x] 确认上游为 https://github.com/amosblomqvist/learn.git。
- [x] 阅读安装说明、Pi packages/skills 文档及相关扩展代码。
- [x] 执行项目级安装：

```bash
mkdir -p /Users/panruiqi/learn
git clone --depth 1 https://github.com/amosblomqvist/learn.git /Users/panruiqi/learn/.pi
```

以上为已执行操作记录，不是要求恢复会话后重新执行。

- [x] 离线 RPC 启动检查：退出码 0，stderr 为空；get_commands 发现 skill:teach、skill:visualize、md-log、md-unlog；get_state 成功，messageCount 为 0，isStreaming 为 false。
- [x] 2026-10-31 14:55 再查安装仓库：git status --short 无输出，HEAD 为上述版本。

### 验证边界

此前检查在 /Users/panruiqi/learn 运行 Pi，使用 --mode rpc --offline --no-session --no-mcp --approve --no-extensions，并通过 -e 显式加载四个 learn 扩展入口；发送 get_commands 和 get_state 后关闭输入。未发模型请求。

该检查证明扩展初始化与命令发现正常，不等于默认交互启动、实际教学、TUI 弹窗或绘图均已验收。不要把注册成功表述为所有能力完整可用。

## Files Modified

- 新增 /Users/panruiqi/learn/.pi，内容来自上游浅克隆，未编辑上游源码。
- 全局配置 /Users/panruiqi/.pi/agent/settings.json 未修改。
- 新增本交接文件，位于安装仓库之外。
- 未执行 npm install，未创建提交或推送。

## Decisions Made

| Decision | Options Considered | Rationale |
|----------|-------------------|-----------|
| 项目级安装 | 全局安装、独立学习项目 | 避免教学 skill 影响日常编码会话 |
| 保持基础安装 | 接入所有可选能力、先用 teach | 先满足教学入口需求，不替换现有子代理系统 |
| 只缩小交接文档范围 | 删除其他组件、仅省略其他讨论 | 用户未授权卸载 learn 自带组件 |

## Important Context

用户最终只需要 learn / teach 安装交接。不要恢复其他讨论，不要把该范围限制理解成删除 learn 内其他扩展或 skill。基础安装已经完成；恢复时先读取本文件，等待用户选择学习主题或提出新要求。现有 pi-subagents 不等同于上游使用的 pi-interactive-subagents，不要宣称绘图与研究子代理已接通，也不要擅自替换基础设施。

## Immediate Next Steps

没有尚未完成的安装动作。用户准备开始学习时，在终端执行：

```bash
cd /Users/panruiqi/learn
pi
```

如出现项目资源信任提示，由用户确认。进入 Pi 后输入，例如：

```text
/skill:teach 带我学习 Android 架构，从我的现有水平开始。
```

主题只是示例，不是已确定的下一任务。若启动或交互失败，保留完整报错后再排查，不要先重装。

## Assumptions Made

- 继续采用独立学习项目，不启用全局 teach。
- 后续学习主题和可选集成由用户决定。

## Potential Gotchas

- 仓库名是 learn，不是 learn.pi；无需重新寻找或重复安装。
- visual-tools 依赖 globalThis.__pi_interactive_subagents；当前 pi-subagents 不会自动提供同一接口。绘图链路未配置。
- 可视化依赖清单含作者本机路径，不能直接假定 npm install 可用；当前没有安装这些依赖。
- 上游子代理含作者特定模型配置与工具假设，未适配当前环境。
- /md-log 初次绑定会回填并覆盖目标文件。若未来用户明确要求日志，只绑定新建空文件，不能绑定已有重要笔记。当前未配置日志或 Obsidian。

## Pending Work

- 无安装阻塞，无未完成必需步骤。
- 实际教学与 TUI 交互可在用户开始学习时验证，不能声称已经测试。
- 可视化、研究子代理、Obsidian 均不在本次交付范围；未获得继续集成授权。

## Environment State

- Pi 版本: 1.4.0；检查时模型: openai / gpt-6.1-sol。
- 用户已安装 pi-subagents，未替换。
- 本任务未保留后台进程。
- 未新增环境变量，无需在交接中携带凭据。

## Related Resources

- 上游: https://github.com/amosblomqvist/learn
- Pi packages 文档: /opt/homebrew/Cellar/pi-coding-agent/1.4.0/libexec/lib/node_modules/@earendil-works/pi-coding-agent/docs/packages.md
- Pi skills 文档: /opt/homebrew/Cellar/pi-coding-agent/1.4.0/libexec/lib/node_modules/@earendil-works/pi-coding-agent/docs/skills.md

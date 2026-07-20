# Warp 中文界面版

> 一个以官方 [Warp](https://github.com/warpdotdev/warp) 为上游、专注于中文界面体验的轻量维护分支。

[![基于官方 Warp](https://img.shields.io/badge/upstream-warpdotdev%2Fwarp-4b89dc)](https://github.com/warpdotdev/warp)
[![许可证：AGPL--3.0](https://img.shields.io/badge/license-AGPL--3.0-blue.svg)](LICENSE-AGPL)

## 项目定位

Warp 的终端交互、工作区和多智能体体验很出色，但桌面客户端目前没有官方中文界面。本项目只解决这一件事：为 Warp 客户端提供自然、克制、符合中文开发者习惯的界面文案。

它不是一个新的终端产品，也不是第三方 AI 网关。

## 保持不变的内容

为确保能够持续跟随官方更新，本项目坚持最小改动原则：

- 保留 Warp 的账户登录、官方服务、Oz / Warp Agent 和同步能力；
- 保留第三方 CLI Agent 的原有用法，包括 Codex、Claude Code、Gemini CLI 等；
- 不内置任何第三方模型网关，不重定向 API 请求，不要求额外 API Key；
- 不移除登录限制，不修改权限、遥测或安全策略；
- 不修改终端命令输出、代码、文件内容或用户输入。

中文化范围仅限客户端中可见的固定界面文案，例如导航、菜单、设置、对话框、状态提示与 Agent 的操作提示。

## 当前状态

项目处于中文化初始化阶段，暂未提供独立安装包。请继续使用[官方 Warp 下载版](https://www.warp.dev/download)作为日常稳定环境。

首个版本的目标是覆盖以下高频界面：

1. 工作区、标签页与命令面板；
2. 设置与键盘快捷键；
3. Agent 面板、权限确认与任务状态；
4. 常见错误、空状态和引导提示。

## 文案原则

- 优先表达用户要做的事，而不是逐字翻译英文；
- 按钮使用清晰的动作词，例如“保存”“继续”“查看详情”；
- “Agent”统一译为“智能体”，首次必要处保留英文括注；
- 产品名、命令、快捷键、设置键、模型名和代码标识保持原样；
- 陌生术语保留英文或采用中英对照，避免制造新的中文黑话；
- 不翻译终端输出和 CLI Agent 自己产生的内容。

## 与 Codex 一起使用

本项目不会替换或代理 Codex。安装 Codex CLI 并完成其自己的登录后，直接在 Warp 的终端中运行：

```bash
codex
```

Codex 的账户、会话、模型与权限仍由 Codex 自己管理；本项目只负责 Warp 客户端的中文界面。

## 上游更新方式

本仓库把官方 Warp 设为 `upstream`，中文改动只维护在 `cn/main` 分支。每次官方发布后，维护者会把中文补丁 rebase 到最新上游，再构建和验证。

```bash
git fetch upstream --tags
git switch cn/main
git rebase upstream/master
```

如发生冲突，只处理与中文文案相关的文件；若上游已提供对应的本地化机制或中文翻译，则优先采用官方方案并删除重复补丁。

## 本地开发

完整的依赖安装、构建和测试方式请遵循官方仓库说明：

```bash
./script/bootstrap
./script/run
./script/presubmit
```

Windows 安装包由 Windows 环境或 CI 构建，不建议把 WSL 中的 Linux 构建产物当作 Windows 客户端使用。

每次推送到 `cn/main` 的中文化改动，都会通过 GitHub Actions 在 Windows 环境执行 Rust 格式检查与 Warp 客户端库编译检查；该流程不发布安装包，也不需要任何第三方模型密钥。

## 贡献中文文案

欢迎提交文案问题或改进建议。请在提交前说明：

- 原始英文与所在界面；
- 建议中文及使用场景；
- 为什么新文案对中文开发者更自然；
- 是否会影响术语一致性。

任何涉及认证、网络端点、模型路由、权限或业务逻辑的改动，不属于本项目的中文化范围，应单独讨论并默认不合入。

## 与官方 Warp 的关系

本仓库 fork 自 [warpdotdev/warp](https://github.com/warpdotdev/warp)，与 Warp 官方团队无隶属或背书关系。Warp 及相关标识归其各自权利方所有。

Warp 的 UI 框架（`warpui_core` 和 `warpui` crates）采用 [MIT 许可证](LICENSE-MIT)，其余代码及本项目的修改采用 [AGPL v3](LICENSE-AGPL)。

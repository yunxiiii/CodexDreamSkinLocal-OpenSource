# Codex Dream Skin Local

[English](#english) · [简体中文](#简体中文)

---

## English

### Overview

`Codex Dream Skin Local` is a Windows local visual customization for the Microsoft Store edition of Codex. It provides home and task-page wallpaper, right-side plan-panel wallpaper, theme management, and a Chinese/English/Japanese control panel without modifying Codex configuration, `WindowsApps`, authentication, tasks, plugins, or user data.

### Install

Clone or extract this repository to any local writable directory. Start Codex normally once before the first installation, then run this command from the repository root:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\scripts\setup.ps1
```

Setup copies the Node.js runtime bundled with Codex into `runtime\node`, validates the current Codex package, initializes local theme data under `state`, and creates one shortcut:

- `Codex Dream Skin Local`

The shortcut starts without a visible PowerShell window. Its control panel can enable or reapply the skin, pause or resume it, choose full-wallpaper or lightweight-static task pages, switch Chinese/English/Japanese, change and save backgrounds, open the theme folder, and restore normal Codex.

The one-time `Bypass` applies only to setup. Daily shortcuts use `RemoteSigned` and do not change the system execution policy. Generated `runtime` and `state` directories are local machine data and are ignored by Git.

### Commands

```powershell
# Validate the local runtime and Codex package.
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\diagnose.ps1

# Launch with loopback-only CDP and apply the skin.
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\launch.ps1 -PromptRestart

# Open the single control-panel entry.
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\control-center.ps1

# Verify the live injection and write a screenshot.
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\verify.ps1 -ScreenshotPath .\state\verify.png

# Stop the skin and reopen normal Codex.
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\restore.ps1 -PromptRestart
```

### Safety model

- CDP listens only on `127.0.0.1` and selects an available port beginning at `9335`.
- The launcher validates the Microsoft Store Codex package and process identity.
- The injector validates the Browser ID and native renderer markers; visual layers do not intercept pointer events.
- The home route always uses wallpaper; task pages can use full-wallpaper or lightweight-static mode.
- Images must be UI-free PNG, JPEG, or WebP files, up to 16 MB, 16384 px per side, and 50 MP.
- `restore.ps1` stops only the recorded private Node injector and does not edit `config.toml`.

### Tests

After setup, run from the repository root:

```powershell
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\tests\run-local-tests.ps1
```

The suite covers the private Node runtime, Appx-unavailable process-discovery fallback, theme payload, injector, renderer, image metadata, control panel, and Codex configuration protection.

### Publishing and privacy

Publish only source code and redistributable default theme assets. Never commit generated `runtime` or `state` directories because they may contain a private Node runtime, verified application identity, logs, screenshots, saved themes, and personal wallpaper files. Retain `LICENSE` and `NOTICE.md` when redistributing the project.

This is an independent third-party local visual customization. It is not an OpenAI product and does not use an official, supported Codex theming API.

---

## 简体中文

### 简介

`Codex Dream Skin Local` 是面向 Microsoft Store 版 Codex 的 Windows 本地视觉定制工具。它提供主页与任务页壁纸、右侧计划面板壁纸、主题管理和中文/English/日本語控制面板，同时不修改 Codex 配置、`WindowsApps`、登录信息、任务、插件或用户数据。

### 安装

将本仓库克隆或解压到任意本地可写目录。首次安装前，请先正常启动一次 Codex；然后在仓库根目录运行：

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\scripts\setup.ps1
```

安装程序会将 Codex 自带的 Node.js 运行时复制到 `runtime\node`、验证当前 Codex 包、初始化 `state` 下的本地主题数据，并创建唯一快捷方式：

- `Codex Dream Skin Local`

该快捷方式不会显示黑色 PowerShell 窗口。控制面板可启用或重应用主题、暂停或恢复主题、选择任务页“全壁纸”或“轻量静态”、切换中英日语言、更换和保存背景、打开主题目录，以及恢复普通 Codex。

首次命令中的 `Bypass` 仅作用于本次安装。日常快捷方式使用 `RemoteSigned`，不会修改系统 PowerShell 执行策略。自动生成的 `runtime` 与 `state` 属于本机数据，已被 Git 忽略。

### 常用命令

```powershell
# 验证本地运行时和当前 Codex 包。
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\diagnose.ps1

# 通过仅回环的 CDP 启动并注入主题。
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\launch.ps1 -PromptRestart

# 打开唯一控制面板。
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\control-center.ps1

# 验证实时注入并输出截图。
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\verify.ps1 -ScreenshotPath .\state\verify.png

# 停止主题并恢复普通 Codex。
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\scripts\restore.ps1 -PromptRestart
```

### 安全设计

- CDP 只监听 `127.0.0.1`，从 `9335` 起自动选择可用端口。
- 启动器会验证 Microsoft Store Codex 包及其运行进程身份。
- 注入器会验证 Browser ID 与原生 Codex 渲染标记；视觉层不拦截鼠标事件。
- 主页始终使用壁纸；任务页可在控制面板选择全壁纸或轻量静态模式。
- 图片仅接受无 UI 的 PNG、JPEG 或 WebP，最大 16 MB、单边 16384 px、总像素 5000 万。
- `restore.ps1` 只停止本项目记录的私有 Node 注入器，不编辑 `config.toml`。

### 测试

完成安装后，在仓库根目录运行：

```powershell
powershell -NoProfile -ExecutionPolicy RemoteSigned -File .\tests\run-local-tests.ps1
```

测试覆盖私有 Node 运行时、Appx 查询不可用时的进程发现回退、主题载荷、注入器、渲染器、图片元数据、控制面板与 Codex 配置保护。

### 发布与隐私

仓库只应包含源码和可再分发的默认主题素材。不要提交自动生成的 `runtime` 或 `state`：其中可能包含私有 Node 运行时、已验证的应用身份、日志、截图、已保存主题和个人壁纸。再次分发时请保留 `LICENSE` 与 `NOTICE.md`。

本项目是第三方本地视觉定制工具，不是 OpenAI 产品，也不使用受支持的 Codex 官方主题 API。

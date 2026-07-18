# GitHub Publishing Checklist / GitHub 发布检查清单

## English

- [ ] Review `git status` and confirm that `runtime/` and `state/` are absent.
- [ ] Do not add personal wallpaper images, screenshots, logs, session files, or trusted Codex identity files.
- [ ] Confirm that `assets/dream-reference.jpg` is suitable for redistribution under the retained MIT notice. Replace it with your own licensed image if needed.
- [ ] Keep `LICENSE` and `NOTICE.md` in the repository.
- [ ] Run `powershell.exe -NoProfile -ExecutionPolicy RemoteSigned -File .\tests\run-local-tests.ps1` after setup on a test machine.
- [ ] Create the GitHub repository as Public only after completing the above checks.

The project is an independent local visual customization. It is not an OpenAI product and does not use an official Codex theming API.

## 简体中文

- [ ] 检查 `git status`，确认不包含 `runtime/` 和 `state/`。
- [ ] 不要添加个人壁纸、截图、日志、会话文件或已验证 Codex 身份文件。
- [ ] 确认 `assets/dream-reference.jpg` 可依照保留的 MIT 声明再分发；如有需要，请替换成你拥有授权的图片。
- [ ] 在仓库中保留 `LICENSE` 和 `NOTICE.md`。
- [ ] 在测试机完成安装后，运行 `powershell.exe -NoProfile -ExecutionPolicy RemoteSigned -File .\tests\run-local-tests.ps1`。
- [ ] 完成以上检查后，再将 GitHub 仓库设为 Public。

本项目是独立的本地视觉定制工具，不是 OpenAI 产品，也不使用官方支持的 Codex 主题 API。

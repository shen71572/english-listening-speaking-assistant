# 英语听说助手（静态版）

> 仓库：https://github.com/shen71572/english-listening-speaking-assistant（公开，main 分支）

第三届大学生人工智能通识应用大赛参赛作品「英语听说助手」的静态版本：把原型里的全部内容数据逐字嵌入一个 HTML 文件，在任何浏览器里离线打开都能用，学习记录只保存在浏览器本地（localStorage）。

- 原型：Muse 英语听说助手（fullstack 原型，另见大赛百度搭子版）
- 静态版内容：词书 A 1200 词（词达人版）+ 词书 B 800 词、单词考察（含题型自选）、精听 9 篇、口语 8 单元对话、12 校园场景 + 9 位 NPC、美句/名言各 50、模拟测试 30 题、四级真题 35 套（2021.06–2026.06，文本版，无语音）、艾宾浩斯复习、学习报告
- 语音：静态版不带 Lily 预录音，全部发音走浏览器英文 TTS；固定人声 Lily 是原型版专属
- 学习记录：只存在浏览器本地，换设备/换浏览器会丢失

## 直接打开

用浏览器打开 `www/index.html` 即可（手机优先）。

## 打 APK

仓库里已配好 Capacitor + GitHub Action：每次 push 到 `main` 分支，`.github/workflows/build-apk.yml` 会在云端自动构建，产物是 debug 版 `.apk`（在 Action 运行页的 Artifacts 里下载）。

- 改编自 [Narottam04/action-capacitor-android](https://github.com/Narottam04/action-capacitor-android)（MIT），按本仓库的 `main` 分支、预构建静态站、debug 优先做了调整。
- 如需签名的发布版 `.aab`：在仓库 Settings → Secrets 里配好 `RELEASE_KEYSTORE`（base64 的 keystore）、`RELEASE_KEYSTORE_PASSWORD`、`ACCESS_TOKEN`，工作流会自动签名并创建 Release。

## skills/

本项目用到的三个自定义 skill（Muse skill 格式），和原型一起打包：

- `skills/dynamic_design_studio/` — 动态设计工具箱（原型设计方向）
- `skills/voice_studio/` — VoiceStudio（Lily 固定人声）
- `skills/research_skills/` — 研究技能工具箱（内容核验）

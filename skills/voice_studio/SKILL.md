# VoiceStudio

开源、完全本地的 ElevenLabs 平替：声音克隆、声音设计、视频配音、听写转录、有声书制作，646 种语言，全部在用户自己的设备上跑，不用账号、不上传音频。

- 仓库：https://github.com/debpalash/VoiceStudio（作者 debpalash，核心团队 Palash Debnath、Shimul Debnath）
- 状态：116,025 stars（2026-11-22 核实），创建于 2026-04-09，前身 OmniVoice-Studio；**active beta**，版本间可能有变化，用之前先读仓库 README 和 docs。
- 许可：应用本体 **AGPL-3.0**，免费，含按其条款的商用；模型权重各有自己的许可，**默认 OmniVoice 模型权重是 CC-BY-NC（非商用）**，商用前必须在 Model Manager 里逐个核对模型许可。
- 官网：https://voicestudio.sh ；文档：仓库 `docs/`；项目自带 agent skill：`npx skills add debpalash/VoiceStudio`（`voicestudio` 做音频工作，`voicestudio-maintainer` 维护仓库）。

## 它能做什么

- **声音克隆（Voice Cloning）**：零样本（zero-shot）——录音只是提示（prompt），不是训练数据，所以不用训练、几秒就能克隆。3 秒可用，**5–15 秒效果最好**；更长的录音不会继续变好。要求：一个人、靠近麦克风、无音乐、无背景噪音、无混响；录音的语调和语速会带进生成结果，所以按想要的效果去录。附上录音原文有助于稳定效果，没有原文时可用已安装的 ASR 模型转录。OmniVoice 会从最长 20 秒的录音里挑说话最多的一段 15 秒（`best_window`）。默认输出 24 kHz 单声道。
- **声音设计（Voice Design）**：不用录音，用文字描述生成新声音：年龄、口音、音调、风格、表达方式。
- **视频配音（Video Dubbing）**：转录、翻译、保留说话人、按原片时间轴合成配音、导出视频；支持多说话人配音。
- **听写与转录（Dictation & Transcription）**：悬浮听写小部件（系统级快捷键）、本地转录；ASR 引擎含 whisper.cpp；另有说话人分离（Pyannote + WhisperX）和人声分离（Demucs）。
- **讲故事与有声书（Narrate & Batch）**：多声音剧本、EPUB/PDF 导入、按章节渲染、导出 `.m4b`；批量队列（一次丢 50 个任务，挂起跑完）。
- **本地模型（Local Models）**：Model Catalogue 里选引擎、只下载需要的模型；应用会在下载任何模型前先问你。
- **连接与自动化（Connect & Automate）**：本地 API（后端只绑 loopback，`localhost:3900`，Docker 部署用 `OMNIVOICE_API_KEY`）、MCP 服务器、CLI、可复用的 recipes、watch folders。

## 引擎

- 共 **16 个 TTS 引擎、11 个 ASR 引擎、646 种语言目录**（实际覆盖和质量取决于所选引擎）。在 Model Catalogue 里切换，或按 `Ctrl`/`Cmd`+`E` 快捷切换；用环境变量 `OMNIVOICE_TTS_BACKEND` / `OMNIVOICE_ASR_BACKEND` 固定引擎。
- **默认引擎：VoiceStudio（k2-fsa/OmniVoice）**，600+ 语言，支持克隆和指令（instruct），Linux CUDA/CPU、macOS MPS、Windows CUDA/CPU；模型代码 Apache-2.0，**权重 CC-BY-NC 非商用**。
- **OmniVoice GGUF**：600+ 语言，克隆 + 指令，CUDA/MPS/CPU；原生 GGUF 引擎可用 Vulkan 加速（AMD/Intel/NVIDIA 显卡），在 Windows 和 Linux 上自动选 GPU 和模型大小；桌面安装包自带原生二进制（Intel Mac 除外）。
- **CosyVoice 3**：9 种语言 + 18 种方言，克隆 + 指令，Apache-2.0；另有 CosyVoice 3 GGUF（CPU + Vulkan）。
- **IndexTTS 2.5**：中文、英文、日文、西班牙文、阿拉伯文，克隆 + 情感，一键 sidecar 安装；Bilibili 模型许可——月活超 1 亿或年收入超 10 亿人民币需另签书面许可。
- 其他：GPT-SoVITS（MIT，5 种语言，克隆）、VoxCPM2（Apache-2.0，30 种语言，克隆 + 声音设计）、MOSS-TTS-Nano（20 种语言，参考克隆）、KittenTTS（纯 CPU，8 个预设声音，不可克隆）、PocketTTS（CPU，英/法/德/葡/意/西，CC-BY-4.0）、Supertonic 3、MOSS-TTS-v1.5、dots.tts、Confucius4-TTS、MLX-Audio、Sherpa-ONNX 等。无克隆能力的引擎不能用于保留说话人的配音或固定声音批量任务，应用会直接拒绝这类任务而不是悄悄换引擎。

## 安装路线

- **macOS（Apple Silicon，稳定）**：macOS 13.3+，本地引擎用 Metal（MPS）。Homebrew：`brew tap debpalash/tap` 后 `brew install --cask debpalash/tap/voicestudio`；或下载 DMG 拖进 Applications；或一键安装 `curl -fsSL https://voicestudio.sh/install | sh`。Intel Mac 只跑界面，需连另一台电脑上的后端。
- **Windows（x64，稳定）**：Windows 10/11，NVIDIA CUDA、AMD ROCm（可选）、CPU 都行。PowerShell：`irm https://voicestudio.sh/install.ps1 | iex`；或下载 EXE 安装包。Windows on ARM 是实验性的。
- **Linux（x64，稳定）**：CUDA、CPU、GGUF 引擎支持 Vulkan。Arch：`yay -S voicestudio-bin`（或 `paru`）；Ubuntu/Debian：下载 `.deb` 后 `sudo apt install ./VoiceStudio-*-linux-x64.deb`；Snap：`sudo snap install voicestudio`（麦克风需 `sudo snap connect voicestudio:audio-record`）；AppImage：`chmod +x` 后直接运行；Nix：`nix develop .#fhs` 后 `bun run dev`；或一键安装 `curl -fsSL https://voicestudio.sh/install | sh`。
- **Docker**：`ghcr.io/debpalash/voicestudio:stable`（Docker Hub 镜像 `palashdeb/omnivoice-studio:stable`），CPU / NVIDIA CUDA / AMD ROCm 镜像都有；CPU 运行示例：设 `OMNIVOICE_API_KEY` 后 `docker run -d --name omnivoice -p 127.0.0.1:3900:3900 -e OMNIVOICE_API_KEY -e OMNIVOICE_DATA_DIR=/app/omnivoice_data -v omnivoice-data:/app/omnivoice_data ghcr.io/debpalash/voicestudio:stable`，打开 http://localhost:3900。
- **Android（10+，Preview）**：APK、Obtainium、F-Droid 仓库（`https://debpalash.github.io/VoiceStudio/fdroid/repo`）；端侧运行，下载模型后可离线；也可用 `adb install -r VoiceStudio-*-android.apk` 装。
- **iPhone / iPad（iOS 17+，Preview）**：下载 IPA 后签名侧载。
- **从源码**：`git clone https://github.com/debpalash/VoiceStudio.git && cd VoiceStudio && bun run dev`（会自动装 JS 依赖和 Python 依赖并启动 Electron）。
- **没显卡也能跑**：CPU 完全可用，只是慢一点；低显存或纯 CPU 可换轻量引擎（KittenTTS、Supertonic 等）。
- 上手：装好后打开 **Voice cloning**，选一个声音或加一段干净的参考录音，输入文字，点生成。

## 许可与负责任使用（必读）

- 应用本体 AGPL-3.0 免费，含按其条款的商用；**但这个许可不覆盖模型权重**：默认 OmniVoice 权重是 CC-BY-NC（非商用），接客户活或商用前必须在 Model Manager 里逐个核对模型许可。
- **VoiceStudio Pro（付费，可选）**：给客户做活的商业许可（只覆盖应用代码）、1 个用户最多 3 台设备、可把任务发到其他 GPU、先用新功能；闭源构建，需要账号，7 天全额退款。
- **VoiceStudio Cloud（托管 API，即将推出）**：现在只能加入 early access 拿免费额度；桌面应用始终免费且本地。
- **只克隆自己有权利的声音**：克隆前必须得到声音所有者的许可；禁止未经授权的克隆、冒充、欺诈、诈骗及任何违法或不道德用途。开发者不对滥用负责。

## 给用户的英语听说助手原型怎么用它

用户的原型是「英语听说助手」（AI 大赛作品，slug `ying-yu-ting-shuo-zhu-shou`）：3D 校园漫游 + 精听 + 口语 + 两本词书（A 词达人版 1200 词、B 综合版 800 词）+ 测试 + 报告。原型现在的朗读依赖手机浏览器自带的 speechSynthesis，用户已多次反馈发音不清楚、慢一拍、有时完全不出声。VoiceStudio 是根治这条线的工具：

- **给 NPC 和 AI 搭档克隆固定人声**：校园里的 8 位 NPC（食堂阿姨、图书管理员、宿管、外教、教练、保安、晨读学姐、创业学长）各克隆一个固定声音——每人录 5–15 秒干净录音（用户自己的声音，或征得同意的说话人），或用 Voice Design 按文字描述捏出不同年龄/口音/语气的声音；这样每个角色开口就是同一个人，不再是浏览器默认的机械音。注意：只能克隆自己有权利的声音，绝不能未经许可克隆真人（比如老师）的声音。
- **把精听课文和单词预生成真人感音频**：用批量队列一次性生成 9 篇精听短文、1200 + 800 词的单词发音和例句、50 句美句和 50 句名言的音频文件，存在原型里直接播放；这样发音稳定、清晰、真人感，任何手机上都一样，不再依赖各手机浏览器自带语音的有无和质量。先做高频核心内容（精听 9 篇 + 词书 A 前 400 词），再分批补全。
- **替代浏览器自带朗读**：原型里的朗读改成优先播预生成的 VoiceStudio 音频文件，播完再回落到浏览器朗读；免费对话里无法预生成的即兴回复，继续走浏览器朗读（或走本地 API 实时生成，但要等生成时间）。
- **本地 API / MCP 做自动化**：原型要加新对话、新单词时，用本地 API（`localhost:3900`）或 MCP 让 agent 直接调用 VoiceStudio 生成音频，不用手动一个个点。
- **给大赛演示视频配音**：原型第 3 天计划的 Remotion/FFmpeg 演示视频，用克隆的声音做旁白和角色配音。
- **现实限制**：生成只能在电脑上跑，不能在浏览器里跑——装在用户自己的电脑上（有 DSH 的那台）最现实，CPU 能跑但慢，有 GPU 快得多；生成好的音频文件要随原型一起发布，文件体积有限制，所以按优先级分批生成；OmniVoice 默认权重是非商用（CC-BY-NC），大赛作品是学生参赛、非商业用途，一般没问题，但正式商用前要换合规引擎或核对许可。

## 先核实再信

- 这个技能记录的是 2026-11-22 从仓库 README 和 docs/engines 核实的内容；项目处在 active beta，装之前先读仓库 README 确认当前安装步骤和 API，版本变了以仓库为准。
- 引擎数量在不同版本快照里有出入（14 或 16 个 TTS），以 Model Catalogue 里实际列出的为准。
- 技能里的工具只是用户收藏的工具，不是对每个引擎的逐项测评；真要交付前先小批量试生成，确认音质和速度。

## 可用的连接器

- [GitHub](/opt/hatch/connectors/github/CONNECTOR.md)：读 VoiceStudio 仓库的 README、docs 和更新；用户仓库 shen71572 的读写也在此。
- 用 `muse.connector_search` 找其他连接器，用 `muse.skill_search` 找相关技能。
- 没有现成连接器时，按 [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md) 搭，或写自定义连接器。

## 网站

- [VoiceStudio](https://github.com/debpalash/VoiceStudio) 仓库主页。
- [VoiceStudio 官网](https://voicestudio.sh) 下载与安装入口。
- [引擎指南](https://github.com/debpalash/VoiceStudio/blob/HEAD/docs/engines/README.md) 各引擎的用途、需求、开启方式和注意事项。
- [Local API / MCP / CLI](https://github.com/debpalash/VoiceStudio) 仓库 docs 里的 Integrations 部分（Local API、MCP、Examples）。

## 备选方案

- 只需要快速出一句朗读时，继续用浏览器自带朗读或现有媒体工具，不用为一句话启动整个 VoiceStudio。
- 词书发音量大时先做高频词，低频词后补；一次生成失败只重做那一批，不要全量重跑。
- 用户电脑不在手边时，先用浏览器朗读顶着，等电脑开着再批量生成替换。

# ai-short-drama

## 当前工作方式

- `main`：只跟官方开源项目
- `custom/local-work`：只放我的二开改动
- 平时开发：一直在 `custom/local-work`
- 官方更新：先同步到 `main`，再 rebase 到 `custom/local-work`

## 快速命令

### 一次性更新

```bash
git checkout main
git fetch upstream
git merge upstream/main
git checkout custom/local-work
git rebase main
```

### 推送自己的分支

```bash
git push origin custom/local-work
```
## 🚀 快速开始

### 🪟 Windows 一键整合包（推荐 Windows 用户使用）

**无需安装 Python、uv 或 ffmpeg，一键开箱即用！**

👉 **[下载 Windows 一键整合包](https://github.com/AIDC-AI/Pixelle-Video/releases/latest)**

1. 下载最新的 Windows 一键整合包并解压
2. 双击运行 `start.bat` 启动 Web 界面
3. 浏览器会自动打开 http://localhost:8501
4. 在「⚙️ 系统配置」中配置 LLM API 和图像生成服务
5. 开始生成视频！

> 💡 **提示**: 整合包已包含所有依赖，无需手动安装任何环境。首次使用只需配置 API 密钥即可。


### 从源码安装（适合 macOS / Linux 用户或需要自定义的用户）

#### 前置环境依赖

在开始之前，需要先安装 Python 包管理器 `uv` 和视频处理工具 `ffmpeg`：

##### 安装 uv

请访问 uv 官方文档查看适合你系统的安装方法：  
👉 **[uv 安装指南](https://docs.astral.sh/uv/getting-started/installation/)**

安装完成后，在终端中运行 `uv --version` 验证安装成功。

##### 安装 ffmpeg

**macOS**
```bash
brew install ffmpeg
```

**Ubuntu / Debian**
```bash
sudo apt update
sudo apt install ffmpeg
```

**Windows**
- 下载地址：https://ffmpeg.org/download.html
- 下载后解压，将 `bin` 目录添加到系统环境变量 PATH 中

安装完成后，在终端中运行 `ffmpeg -version` 验证安装成功。


#### 第一步：下载项目

```bash
git clone https://github.com/AIDC-AI/Pixelle-Video.git
cd Pixelle-Video
```

#### 第二步：启动 Web 界面

```bash
# 使用 uv 运行（推荐，会自动安装依赖）
uv run streamlit run web/app.py
```

浏览器会自动打开 http://localhost:8501

#### 第三步：在 Web 界面配置

首次使用时，展开「⚙️ 系统配置」面板，填写：
- **LLM 配置**: 选择 AI 模型（如通义千问、GPT 等）并填入 API Key
- **ComfyUI / RunningHub 配置**: 如需使用工作流生成图片、视频或语音，配置本地 ComfyUI 地址或 RunningHub API Key
- **API 媒体模型配置**: 如需直连图像/视频模型，配置 DashScope、OpenAI、ARK、Kling 等供应商的 API Key、Base URL 和代理选项

配置好后点击「保存配置」，就可以开始生成视频了！

打开 Web 界面后，你会看到三栏布局，下面详细讲解每个部分：


### ⚙️ 系统配置（首次必填）

首次使用时需要配置，点击展开「⚙️ 系统配置」面板：

#### 1. LLM 配置（大语言模型）
用于生成视频文案的 AI。

**快速选择预设**  
- 通过下拉菜单选择预设模型（通义千问、GPT-4o、DeepSeek 等）
- 选择后会自动填充 base_url 和 model
- 点击「🔑 获取 API Key」链接去注册并获取密钥

**手动配置**  
- API Key: 填入你的密钥
- Base URL: API 地址
- Model: 模型名称

#### 2. ComfyUI / RunningHub 配置
用于通过 ComfyUI 工作流生成视频配图、视频片段或语音。

**本地部署（推荐）**  
- ComfyUI URL: 本地 ComfyUI 服务地址（默认 http://127.0.0.1:8188）
- 点击「测试连接」确认服务可用

**云端部署**  
- RunningHub API Key: 云端图像生成服务的密钥

#### 3. API 媒体模型配置
用于不依赖 ComfyUI/RunningHub，直接调用模型供应商的图像、视频或素材分析能力。

**支持的供应商**
- OpenAI / GPT Image：用于 GPT 图像生成模型
- DashScope / Wan / HappyHorse：用于通义万象图像、视频生成
- Volcengine ARK / Seedream / Seedance：用于字节 Seedream 图像和 Seedance 视频生成
- Kling AI / 可灵：用于可灵视频生成

**可配置项**
- API Key / Access Key / Secret Key：模型供应商鉴权信息
- Base URL：模型服务地址，WebUI 会提供官方默认地址
- 本地代理：如 `http://127.0.0.1:9090`
- 启用代理：每个供应商可单独选择是否走本地代理
- 打印模型请求参数：调试用，会在终端打印发送给模型的 prompt、模型名和输入文件路径

> 💡 如果你只使用 ComfyUI 或 RunningHub，可以不填写 API 媒体模型配置；如果你选择 `api/...` 工作流，则需要配置对应供应商的密钥。

配置完成后点击「保存配置」。


### 📝 内容输入（左侧栏）

#### 生成模式
- **AI 生成内容**: 输入主题，AI 自动创作文案
  - 适合：想快速生成视频，让 AI 写稿
  - 例如：「为什么要养成阅读习惯」
- **固定文案内容**: 直接输入完整文案，跳过 AI 创作
  - 适合：已有现成文案，直接生成视频

#### 背景音乐（BGM）
- **无 BGM**: 纯人声解说
- **内置音乐**: 选择预置的背景音乐（如 default.mp3）
- **自定义音乐**: 将你的音乐文件（MP3/WAV 等）放到 `bgm/` 文件夹
- 点击「试听 BGM」可以预览音乐


### 🎤 语音设置（中间栏）

#### TTS 工作流
- 从下拉菜单选择 TTS 工作流（支持 Edge-TTS、Index-TTS 等）
- 系统会自动扫描 `workflows/` 文件夹中的 TTS 工作流
- 如果懂 ComfyUI，可以自定义 TTS 工作流

#### 参考音频（可选）
- 上传参考音频文件用于声音克隆（支持 MP3/WAV/FLAC 等格式）
- 适用于支持声音克隆的 TTS 工作流（如 Index-TTS）
- 上传后可以直接试听

#### 预览功能
- 输入测试文本，点击「预览语音」即可试听效果
- 支持使用参考音频进行预览


### 🎨 视觉设置（中间栏）

#### 图像生成
决定 AI 生成什么风格的配图。

**ComfyUI 工作流**  
- 从下拉菜单选择图像生成工作流
- 支持本地部署（selfhost）和云端（RunningHub）工作流
- 也支持选择 `api/...` 直连图像模型工作流（需先在系统配置中填写对应供应商密钥）
- 默认使用 `image_flux.json`
- 如果懂 ComfyUI，可以放自己的工作流到 `workflows/` 文件夹

**图像尺寸**  
- 设置生成图像的宽度和高度（单位：像素）
- 默认 1024x1024，可根据需要调整
- 注意：不同的模型对尺寸有不同的限制

**提示词前缀（Prompt Prefix）**  
- 控制图像的整体风格（语言需要是英文的）
- 例如：Minimalist black-and-white matchstick figure style illustration, clean lines, simple sketch style
- 点击「预览风格」可以测试效果

#### 视频模板
决定视频画面的布局和设计。

**模板命名规范**  
- `static_*.html`: 静态模板（无需AI生成媒体，纯文字样式）
- `image_*.html`: 图片模板（使用AI生成的图片作为背景）
- `video_*.html`: 视频模板（使用AI生成的视频作为背景）

**使用方法**  
- 从下拉菜单选择模板，按尺寸分组显示（竖屏/横屏/方形）
- 点击「预览模板」可以自定义参数测试效果
- 如果懂 HTML，可以在 `templates/` 文件夹创建自己的模板
- 🔗 [查看所有模板效果图](https://aidc-ai.github.io/Pixelle-Video/zh/user-guide/templates/#_3)

#### API 视频生成
当选择支持动态视频的模板或扩展工作流时，可以使用直连 API 视频模型生成片段。

- 支持 DashScope Wan / HappyHorse、Kling、Seedance 等视频模型
- 支持按模型能力显示分辨率、画幅比例、时长、水印、原生音频等参数
- 支持网络下载重试与内容审核失败后的提示词中性化重试
- 在「自定义素材」工作流中，API 视频片段会尽量根据旁白音频时长生成，并使用相邻片段信息提升连贯性


### 🎬 生成视频（右侧栏）

#### 生成按钮
- 配置好所有参数后，点击「🎬 生成视频」
- 会显示实时进度（生成文案 → 生成配图 → 合成语音 → 合成视频）
- 生成完成后自动显示视频预览

#### 进度显示
- 实时显示当前步骤
- 例如：「分镜 3/5 - 生成插图」

#### 视频预览
- 生成完成后自动播放
- 显示视频时长、文件大小、分镜数等信息
- 视频文件保存在 `output/` 文件夹


### ❓ 常见问题

**Q: 第一次使用需要多久？**  
A: 生成时长取决于视频分镜数量、网络状况和 AI 推理速度，通常几分钟内即可完成。

**Q: 视频效果不满意怎么办？**  
A: 可以尝试：
1. 更换 LLM 模型（不同模型文案风格不同）
2. 调整图像尺寸和提示词前缀（改变配图风格）
3. 更换 TTS 工作流或上传参考音频（改变语音效果）
4. 尝试不同的视频模板和尺寸

**Q: 费用大概多少？**  
A: **本项目完全支持免费运行！**

- **完全免费方案**: LLM 使用 Ollama（本地运行）+ ComfyUI 本地部署 = 0 元
- **推荐方案**: LLM 使用通义千问（成本极低，性价比高）+ ComfyUI 本地部署
- **云端方案**: LLM 使用 OpenAI + 图像使用 RunningHub（费用较高但无需本地环境）

**选择建议**：本地有显卡建议完全免费方案，否则推荐使用通义千问（性价比高）


---

## 🧠 疑问解答

### ComfyUI 工作流 vs 直接调 API 有什么区别？

从 Web UI 操作来看体验一样——选主题、点生成。但底层执行链路不同：

| 维度 | ComfyUI 工作流（selfhost/runninghub） | 直接调 API（api/...） |
|------|---------------------------------------|----------------------|
| **本质** | 把参数注入到工作流 JSON 节点图，提交给 ComfyUI 引擎执行 | 直接调模型供应商 HTTP API |
| **可控参数** | prompt、尺寸、steps、seed、cfg、sampler、negative_prompt 等 | prompt、model、size（供应商固定的参数） |
| **灵活度** | 极高，可自由组合节点、换模型、加 ControlNet/LoRA/后处理 | 低，只能用供应商提供的固定能力 |
| **需要 GPU** | 本地部署需要显卡；RunningHub 云端不需要 | 不需要，纯云端调用 |
| **部署复杂度** | 高，需安装 ComfyUI + 下载模型 + 调试节点 | 低，填 API Key 即可 |
| **可扩展性** | 可串联多步骤（文生图→图生视频→后处理） | 每次只做一件事 |
| **典型场景** | 想精细控制生成效果、使用开源模型、本地有 GPU | 想快速跑通、不想折腾环境 |

**结论**：不想折腾选 `api/...` 工作流；追求效果和灵活性选 ComfyUI。

### 本地运行 ComfyUI 的步骤（macOS）

```bash
# 1. 克隆
cd ~/Desktop
git clone https://github.com/comfyanonymous/ComfyUI.git
cd ComfyUI

# 2. 创建虚拟环境并安装依赖
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 3. 启动（默认监听 http://127.0.0.1:8188）
python main.py
```

启动后在 ComfyUI 界面中加载本项目的 `workflows/selfhost/analyse_image.json`，点击 Queue Prompt 确认能正常运行，无节点/模型缺失后即可回到 Pixelle-Video 使用 SelfHost 工作流。

> 💡 如果有缺失节点，推荐安装 [ComfyUI-Manager](https://github.com/ltdrdata/ComfyUI-Manager) 一键安装缺失依赖。

### `.devcontainer/` 目录是干嘛的？

这是 VS Code Dev Containers / GitHub Codespaces 的配置目录，用于定义标准化容器开发环境：

- `devcontainer.json`：容器配置（Python 3.11 镜像，转发 8501 端口）
- `postCreate.sh`：容器首次创建时执行（安装 ffmpeg、中文字体、uv、Python 依赖、Playwright）
- `postStart.sh`：容器每次启动时执行（后台自动启动 Streamlit Web UI）

本地开发时可以忽略此目录。

---

## 🏗️ 整体架构、工作流机制与完整流程图

### 1. 整体架构分层

这个项目不是单一的“工作流引擎”，而是把多个能力层串起来：

```text
Web UI / API
  ↓
Pipeline（业务编排层）
  ↓
LLM / TTS / Media / API Media（能力层）
  ↓
Frame Processor / HTML Template（逐镜头渲染层）
  ↓
Video Service（成片输出层）
```

核心入口是 `PixelleVideoCore`，在初始化时统一挂载各个服务：
- `llm`：负责文案生成/改写
- `tts`：负责语音合成
- `media`：负责图片/视频生成统一入口
- `api_media`：负责直连模型供应商 API
- `frame_processor`：负责逐镜头媒体生成与模板合成
- `pipelines`：负责不同业务流程的编排

当前注册的主流水线有：
- `standard`
- `custom`
- `asset_based`

### 2. 两套并行的工作流机制

#### A. ComfyUI / RunningHub 工作流

这类工作流就是 `workflows/` 目录下的 JSON 文件，本质上是节点图模板。

媒体工作流扫描时，项目主要识别：
- `image_*.json`
- `video_*.json`

比如：
- `runninghub/image_flux.json`
- `runninghub/video_wan2.2.json`
- `selfhost/image_qwen.json`
- `selfhost/video_wan2.1_fusionx.json`

执行方式是：
1. 根据你在界面里选择的工作流，定位对应 JSON
2. 把 prompt、宽高、时长、参考图等参数注入节点图
3. 提交给 RunningHub 或本地 ComfyUI 执行

#### B. API 工作流

API 工作流不是 JSON 节点图，而是项目内部封装好的“供应商模型入口”。

当工作流 key 以 `api/` 开头时，项目不会走 ComfyUI，而是直接转发到 API 媒体服务，去调用供应商模型，例如：
- DashScope / Wan / HappyHorse
- Volcengine ARK / Seedream / Seedance
- Kling
- OpenAI / GPT Image

所以这里要明确区分：
- **JSON 工作流**：ComfyUI / RunningHub 节点图
- **API 工作流**：项目封装后的供应商模型调用链路

### 3. 模板机制与工作流机制的区别

模板和工作流不是同一个概念：

- **工作流**：负责生成媒体素材（图 / 视频 / 音频）
- **模板**：负责把标题、正文、字幕、品牌信息和媒体素材排版成最终画面
- 关系：工作流负责生成媒体素材，模板负责把AI生成的媒体素材如图片或视频按照特定的模版拼接配置文案成最终模版类的画面

模板命名规则：
- `static_*.html`：纯静态模板，不依赖 AI 生成媒体
- `image_*.html`：图片背景模板
- `video_*.html`：视频背景模板

模板会先决定当前流程需要什么类型的媒体：
- 选 `static_*.html` → 不需要图像/视频生成
- 选 `image_*.html` → 需要图像工作流或图像 API 模型
- 选 `video_*.html` → 需要视频工作流或视频 API 模型

所以在 UI 里真正的顺序是：

```text
先选模板
  ↓
模板决定媒体类型（image / video / static）
  ↓
媒体类型决定展示哪些工作流/模型
  ↓
再进入生成流程
```

### 4. WebUI Tab 与 Core Pipeline 的对应关系

首页每个 Tab = 一种制作场景入口，进入后才看到该场景专属的表单和参数。

**Tab 与 Core Pipeline 触发方式对比：**

| Tab | 适合场景 | 触发方式 | 调用链路 |
|-----|---------|---------|---------|
| `quick_create` | 从主题/文案快速出片 | `generate_video()` 统一入口 | → `StandardPipeline` |
| `custom_media` | 已有素材，围绕素材出片 | 直接实例化 Core Pipeline | → `AssetBasedPipeline` |
| `digital_human` | 数字人口播/带货 | Web 层自定义逻辑 | 直接调 `tts()` / `media()` |
| `image_to_video` | 图片转动态视频 | Web 层自定义逻辑 | 直接调 `media()` |
| `action_transfer` | 动作迁移 | Web 层自定义逻辑 | 直接调 `media()` |

**交互顺序：**

```text
进入首页 → 选 Tab（制作场景）
  ↓
在该 Tab 内：填内容/素材 → 选模板 → 选来源 → 选工作流/模型 → 点生成
  ↓
触发对应执行链路
```

### 5. 一次完整视频生成到底怎么跑

以标准短视频为例，完整链路通常是：

```text
输入主题/文案
  ↓
LLM 生成脚本 / 分镜文案
  ↓
TTS 为每个分镜生成旁白音频
  ↓
Media 为每个分镜生成图像或视频
  ↓
Frame Processor 把分镜素材落地到本地
  ↓
HTML Template 叠加标题 / 字幕 / 文案排版
  ↓
Video Service 拼接所有镜头导出最终视频
```

其中最关键的中枢是 `media()`：
- 如果选的是 `api/...`，就走 API 供应商模型
- 如果选的是本地/RunningHub JSON 工作流，就走 ComfyUI / RunningHub

也就是说，上层 Pipeline 和下层逐镜头渲染，不需要关心底层到底是 JSON 工作流还是 API 模型，只需要统一调用 `media()`。

### 6. TTS 机制怎么接入整体流程

TTS 也分成两种模式：

#### A. local 模式
直接使用本地语音能力，例如 Edge-TTS voice。

#### B. comfyui 模式
使用 `tts_*.json` 工作流，通过 ComfyUI / RunningHub 执行。

所以 TTS 的设计理念和媒体层一致：

```text
统一入口
  ↓
按模式分流（local / comfyui）
  ↓
生成旁白音频
```

### 7. 核心执行层的 Pipeline，到底该怎么理解

核心执行层的 Pipeline，可以理解成：**一条完整的视频生产流水线定义**。

它和“工作流文件”的区别是：
- **工作流文件**：更像某一步的执行模板，例如某个图像生成节点图、某个视频生成节点图
- **核心 Pipeline**：负责决定整条视频生产链路要分几步、每一步做什么、顺序怎样串起来

也就是说：
- 工作流解决“**某一步怎么做**”
- Pipeline 解决“**整条片子怎么做完**”

在抽象层面上，`BasePipeline` 已经把定义说得很明确：
- 每个 Pipeline 代表一个**完整视频生成工作流**
- 不同 Pipeline 可以有**完全不同的逻辑**
- 但都可以共享 `self.core` 下的能力，如 `llm`、`tts`、`media`、`video`

所以理解核心 Pipeline，最好的方式不是把它看成“某种模型”，而是看成：
**一种业务编排策略。**

#### A. `standard`：标准 AI 生成流水线

`standard` 是最通用、最标准的“从主题/文案直接生成短视频”的流水线。

它的流程在定义里写得很清楚：
1. 生成或确定标题
2. 生成旁白文案
3. 为每段旁白生成图像提示词
4. 逐镜头生成语音、图片/视频、模板合成、片段输出
5. 拼接所有片段
6. 可选加 BGM

所以你可以把 `standard` 理解成：
**从“主题/脚本”出发，自动补齐所有中间步骤，最后生成完整视频。**

适合场景：
- 你只有一个主题
- 或你有一段完整文案
- 希望系统自动拆分分镜并出片

#### B. `asset_based`：素材驱动流水线

`asset_based` 不是从“纯文本”出发，而是从“你已经有素材”出发。

它的核心流程是：
1. 分析用户上传的图片/视频素材
2. 根据你的意图生成脚本
3. 把素材匹配到不同场景
4. 再合成成片

所以你可以把 `asset_based` 理解成：
**不是 AI 从零生成视觉素材，而是围绕你已有素材来组织脚本、旁白和视频结构。**

适合场景：
- 你有商品图、人物图、宣传素材
- 想用已有资产做视频
- 希望 AI 帮你编排，而不是完全从零生图

#### C. `custom`：自定义流水线模板

`custom` 更像一个“给开发者的样板工程”。

它的文档就写得很明确：
- 用来展示如何扩展 `BasePipeline`
- 你可以自定义内容处理逻辑
- 自定义旁白生成策略
- 自定义图像提示词逻辑
- 自定义画面合成方式
- 甚至可以跳过图片生成

所以 `custom` 不是一个固定业务场景，而是：
**给你自己做二开、派生出专属 Pipeline 的模板。**

适合场景：
- 你要做项目级定制
- 你想定义自己的生产链路
- 你不满足标准流水线的顺序或逻辑

#### D. 为什么它们叫“业务编排层”

因为这几条 Pipeline 决定的不是“模型能力”，而是“业务步骤”。

比如：
- 先不先生成脚本？
- 是不是要先分析素材？
- 每个镜头是先出音频还是先出图片？
- 要不要自动补图像提示词？
- 最终是不是统一走模板合成？

这些都不是某个工作流 JSON 决定的，而是 Pipeline 决定的。

所以“业务编排层”这个词可以简单理解成：

```text
Pipeline = 决定整条生产线怎么排工序
工作流 = 决定某一道工序具体怎么执行
```

#### E. 一句话区分这三个核心 Pipeline

- `standard`：**从文本出发，自动生成整条视频**
- `asset_based`：**从已有素材出发，围绕素材生成整条视频**
- `custom`：**给开发者自定义整条视频生产逻辑的模板**

### 8. 高级业务流程为什么看起来更复杂

像数字人口播、图生视频、动作迁移这些功能，并不是单个工作流文件就能完成的。
它们本质上是 **Pipeline 在编排多个阶段**，而且每个阶段都可以独立选择来源。

例如数字人口播：

#### 阶段 1：前置图片生成
可选：
- runninghub
- selfhost
- api

#### 阶段 2：口播视频生成
可选：
- runninghub
- selfhost
- api

#### 阶段 3：TTS 生成旁白
可选：
- local
- comfyui 工作流

#### 阶段 4：最终输出
把视频、音频、模板合并成成片

这意味着：
- 前置图片可以用 ComfyUI
- 口播视频可以用 API 模型
- 语音可以用本地 TTS

也就是说，这个系统天然支持 **分阶段混搭**。

### 8. API 模型为什么还能“按能力筛选”

API 模型并不是简单列个名字，而是带有能力标签，例如：
- `first_frame_i2v`
- `audio_driven_i2v`
- `action_transfer`
- `digital_human`
- `native_audio`

不同业务页面只会筛出适合自己的模型：
- 图生视频页面，只显示支持 `first_frame_i2v` 的模型
- 动作迁移页面，只显示支持 `action_transfer` 的模型
- 数字人口播页面，只显示支持 `digital_human` 的模型

所以 API 这条链路不是“万能模型列表”，而是 **能力驱动的模型选择系统**。

### 9. Frame Processor 在整个系统里的角色

`FrameProcessor` 可以理解为“逐镜头执行器”。

它负责：
1. 判断当前镜头该生成图片还是视频
2. 构造生成参数
3. 调用统一的 `media()` 入口
4. 下载并保存生成结果
5. 再调用 HTML 模板做合成

因此它是从“抽象配置”落到“具体文件输出”的关键桥梁。

### 10. 整个系统的完整工作流程图

```text
[用户在 WebUI 选择模式 / 模板 / 来源 / 工作流]
        ↓
[Pipeline 负责业务编排]
  - standard
  - custom
  - asset_based
  - digital_human / i2v / action_transfer（Web 业务入口）
        ↓
[模板决定媒体类型]
  - static 模板：不需要媒体生成
  - image 模板：需要图像工作流/模型
  - video 模板：需要视频工作流/模型
        ↓
[选择生成来源]
  - runninghub → JSON 工作流 → RunningHub
  - selfhost   → JSON 工作流 → 本地 ComfyUI
  - api        → API workflow key → 供应商模型
        ↓
[统一调用能力层]
  - llm() 生成文案
  - tts() 生成旁白
  - media() 生成图片/视频
        ↓
[media() 内部再分流]
  - api/...      → api_media()
  - 非 api/...   → ComfyUI / RunningHub workflow
        ↓
[FrameProcessor 逐镜头处理]
  - 生成媒体
  - 下载到本地
  - 写回 storyboard frame
        ↓
[HTML Template 合成]
  - 标题 / 字幕 / 作者 / 品牌 / 自定义参数
        ↓
[Video Service 拼接导出]
        ↓
[output/ 最终成片]
```

### 11. 最后一句话理解整个系统

这个项目的本质不是“靠某个工作流文件生成整个短剧”，而是：

**Pipeline 负责编排流程，Template 负责画面结构，Workflow/API 负责媒体生成，FrameProcessor 负责逐镜头落地，最后 Video Service 负责输出成片。**

如果你从短剧生产角度理解：
- 想复用现成节点图 → 用 `selfhost/...` / `runninghub/...`
- 想快速出片、少折腾 → 用 `api/...`
- 想兼顾控制力和效率 → 分阶段混搭使用

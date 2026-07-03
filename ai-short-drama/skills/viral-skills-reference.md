# 短视频短剧爆款 Skill 参考资料

本文档整理了当前适合“短视频 / 短剧生成爆款”方向的第一梯队 skill，作为后续设计、拆解、仿写和产品能力沉淀的参考。

## 参考目标

围绕以下几个核心问题建立参考体系：
- 先拍什么：高传播选题从哪里来
- 怎么开头：前 1~3 秒如何抓停留
- 怎么写顺：短视频 / 短剧脚本结构如何保证留存
- 怎么适配平台：同一内容如何更适合 TikTok 等平台分发

## 第一梯队 Skill 列表

### 1. [`viral-hooks`](https://skills.sh/vyralcontent/content-skills/viral-hooks)

- 来源：[`vyralcontent/content-skills`](https://skills.sh/vyralcontent/content-skills)
- 定位：爆款开头优化 skill
- 主要功能：
  - 专门处理短视频前 1~3 秒 hook
  - 拆解视觉钩子、口播钩子、字幕钩子三层结构
  - 提供常见 hook archetypes 与低留存反模式
- 适用用途：
  - 优化短剧第一句台词
  - 优化第一镜头和第一屏字幕
  - 把平淡开场改成高停留开场
- 对本项目的价值：
  - 短剧是否能留下用户，往往取决于开头几秒
  - 适合沉淀为“爆款开场生成器”“首屏重写器”“3 秒留存优化器”
- 后续可借鉴点：
  - hook 模板库
  - 开场失败案例库
  - 三层 hook 联动生成

### 2. [`viral-short-form-ideas`](https://skills.sh/vyralcontent/content-skills/viral-short-form-ideas)

- 来源：[`vyralcontent/content-skills`](https://skills.sh/vyralcontent/content-skills)
- 定位：爆款选题生成 skill
- 主要功能：
  - 帮助用户批量生成短视频 / 短剧选题
  - 提供切入口、角度、系列化方向
  - 更适合从“内容母题”出发生成可连续更新的题材
- 适用用途：
  - 建立短剧选题池
  - 生成系列账号内容方向
  - 从热点、情绪、冲突、身份反差中提炼可拍题材
- 对本项目的价值：
  - 适合沉淀为“短剧题材生成器”“账号选题引擎”“系列内容规划器”
  - 可用于构建高频爽点母题，如逆袭、误会、背叛、复仇、打脸、身份揭露等
- 后续可借鉴点：
  - 母题库 / 爽点库
  - 角色关系模板
  - 选题 → 冲突 → 场景 → 爆点的自动映射

### 3. [`viral-short-form`](https://skills.sh/vyralcontent/content-skills/viral-short-form)

- 来源：[`vyralcontent/content-skills`](https://skills.sh/vyralcontent/content-skills)
- 定位：短内容总控 skill
- 主要功能：
  - 从空白开始帮助用户搭建短内容整体结构
  - 覆盖 hook、留存、内容格式、平台适配等关键环节
  - 给出经过验证的短内容结构，而不是只写一段文案
- 适用用途：
  - 从 0 到 1 生成短视频脚本
  - 设计短剧的开头、中段、反转、结尾钩子
  - 把碎片化想法整理成完整成片结构
- 对本项目的价值：
  - 可视为“总编剧 + 总导演”的参考框架
  - 适合沉淀为“短剧结构生成器”“留存节奏规划器”“爆款脚本骨架生成器”
- 后续可借鉴点：
  - 15 秒 / 30 秒 / 60 秒脚本模板
  - 冲突升级节奏模板
  - 结尾追更钩子模板

### 4. [`viral-tiktok-content`](https://skills.sh/vyralcontent/content-skills/viral-tiktok-content)

- 来源：[`vyralcontent/content-skills`](https://skills.sh/vyralcontent/content-skills)
- 定位：TikTok 平台适配 skill
- 主要功能：
  - 处理 TikTok For You Page 分发逻辑相关的内容优化
  - 关注不同长度内容对应的完播要求
  - 关注声音使用、节奏控制和平台惩罚点
- 适用用途：
  - 将短剧脚本改写为更适合 TikTok 分发的版本
  - 优化节奏、字幕、声音、桥段密度
  - 适配海外短剧 / 海外短视频内容策略
- 对本项目的价值：
  - 如果后续要做国际化分发，这类平台 skill 非常关键
  - 适合沉淀为“平台改写器”“TikTok 分发优化器”“海外短剧节奏调整器”
- 后续可借鉴点：
  - 按时长给出完播目标
  - 平台不推荐写法清单
  - 平台偏好内容节奏模板

## 推荐使用顺序

建议后续研究和产品化时，按这个顺序吸收：

1. [`viral-hooks`](https://skills.sh/vyralcontent/content-skills/viral-hooks)
2. [`viral-short-form-ideas`](https://skills.sh/vyralcontent/content-skills/viral-short-form-ideas)
3. [`viral-short-form`](https://skills.sh/vyralcontent/content-skills/viral-short-form)
4. [`viral-tiktok-content`](https://skills.sh/vyralcontent/content-skills/viral-tiktok-content)

原因：
- 先解决“留不留人”问题
- 再解决“拍什么”问题
- 然后解决“怎么写完整”问题
- 最后解决“在哪个平台更容易跑起来”问题

## 对应到本项目的能力映射

可以把这 4 个 skill 映射成你后续产品能力模块：

- 爆款开头层：[`viral-hooks`](https://skills.sh/vyralcontent/content-skills/viral-hooks)
- 爆款选题层：[`viral-short-form-ideas`](https://skills.sh/vyralcontent/content-skills/viral-short-form-ideas)
- 爆款脚本结构层：[`viral-short-form`](https://skills.sh/vyralcontent/content-skills/viral-short-form)
- 平台分发适配层：[`viral-tiktok-content`](https://skills.sh/vyralcontent/content-skills/viral-tiktok-content)

## 建议后续沉淀方向

后续可以基于这些参考资料，在项目内逐步整理出你自己的能力文档：

- 爆款钩子模板库
- 爽点母题与冲突库
- 短剧节奏结构模板
- 平台适配改写规范
- 短剧 AI 生成工作流文档

## 备注

以上 skill 更偏“内容增长方法论 + 平台适配策略”，不是通用写作工具。它们的价值不在于预测爆款，而在于把已有的爆款经验结构化，降低从 0 到 1 写出高留存内容的难度。
# Nightwolf Empire — 生产流水线

> 本文件定义本项目从剧本接收到视听单元交付的完整 AIGC 生产流程。
> 每个阶段对应一个技能文件，按顺序执行，前一阶段输出是后一阶段输入。

---

## 流水线总览

| 阶段 | 名称 | 调用技能 | 输入 | 输出 |
|------|------|---------|------|------|
| 阶段 0 | 物资接收与项目诊断 | 内置 | 完整剧本 | 结构性摘要 + 生产参数确认 |
| 第一阶段 | 城市搜索与风格锁定 | `one` | 完整剧本 | 视觉词典（角色/场景/物件/风格/情绪地图） |
| 第二阶段 | 导演版本画面 | `daoyan` | 完整剧本 + 视觉词典（可选） | 导演版本画面剧本 |
| 第三阶段 | 逐镜头分镜拆解 | `director-storyboard-core` + 辅助技能 + `VSS_StoryboardRules` | 导演版本画面剧本 + 视觉词典 | 逐镜头分镜表 |
| 第四阶段 | 镜头画面设计与提示 | `director-visual-design-core` | 分镜表 + 视觉词典 | 可灵/即梦 Prompt 包 |
| 第五阶段 | 视听单元拆卸与交付 | `two` | 完整剧本 + 视觉词典 | 视听单元（可直接喂给 AI 视频工具） |

---

## 技能文件索引

| 技能标识 | 对应文件 | 说明 |
|---------|---------|------|
| `one` | `../one` | 视觉词典生成技能：角色词条、场景词条、物件词条、视觉风格锁定、情绪地图 |
| `daoyan` | `../daoyan` | 导演版本画面剧本改写技能：将原剧本改写为导演脑中画面版本 |
| `director-storyboard-core` | `../director-storyboard-core.md` | 核心分镜拆解技能：Beat 划分 → 逐镜头设计 → AI 提示词 |
| `director-storyboard-advanced` | `../director-storyboard-advanced.md` | 分镜进阶精修模块（角色深度塑造、高级镜头语言等） |
| `AI导演分镜脚本-进阶精修版` | `../AI导演分镜脚本-进阶精修版.md` | 分镜进阶精修版（核心版叠加使用） |
| `VSS_StoryboardRules` | `../VSS_StoryboardRules.md` | 分镜方法论与批量生产规则（从标杆制作中归纳） |
| `director-visual-design-core` | `../director-visual-design-core.md` | 镜头画面设计与 Prompt 工程核心版 |
| `director-visual-design-advanced` | `../director-visual-design-advanced.md` | 镜头画面设计进阶扩展包 |
| `two` | `../two` | 视听单元拆解与交付技能 |

### 辅助技能

| 技能文件 | 说明 |
|---------|------|
| `../Dialogue_Shot_Sequence_Designer.SKILL.md` | 对话镜头序列设计器 |
| `../Emotional_Sequence_Designer.SKILL.md` | 情绪序列设计器 |
| `../Montage_Transition_Designer.SKILL.md` | 蒙太奇/转场设计器 |
| `../Seedance2_Prompt_Avoid_List_GitHub.md` | Seedance 2.0 提示词避坑清单 |
| `../META_StoryboardProcess.md` | 元流程：从剧本到分镜规则的通用方法论 |

---

## 执行顺序与依赖

```
screenplay.md（完整剧本）
       │
       ▼
  ┌──────────────────┐
  │  阶段 0：项目诊断  │ ← 内置（见 stage0-diagnosis.md）
  └────────┬─────────┘
           ▼
  ┌──────────────────────────┐
  │ 第一阶段：视觉词典（one）  │ ← 输入：完整剧本
  └────────┬─────────────────┘
           ▼
  ┌────────────────────────────┐
  │ 第二阶段：导演画面（daoyan） │ ← 输入：完整剧本 + 视觉词典
  └────────┬───────────────────┘
           ▼
  ┌─────────────────────────────────────────────┐
  │ 第三阶段：分镜拆解（storyboard-core + rules） │ ← 输入：导演版剧本 + 视觉词典
  └────────┬────────────────────────────────────┘
           ▼
  ┌─────────────────────────────────────────────────┐
  │ 第四阶段：画面设计与 Prompt（visual-design-core）  │ ← 输入：分镜表 + 视觉词典
  └────────┬────────────────────────────────────────┘
           ▼
  ┌──────────────────────────────┐
  │ 第五阶段：视听单元交付（two）  │ ← 输入：完整剧本 + 视觉词典
  └──────────────────────────────┘
```

---

## 项目信息

- **项目名称**：Nightwolf Empire
- **题材**：狼人 / 豪门 / 契约婚姻 / 权力 / 命定伴侣 (Fated Mate)
- **目标平台**：ReelShort / DramaBox / ShortMax（北美竖屏短剧）
- **集数**：12 集（当前剧本覆盖范围）
- **画面比例**：9:16 竖屏
- **付费墙位置**：Episode 8–9 之间
- **剧本文件**：`screenplay.md`
- **阶段 0 诊断**：`stage0-diagnosis.md`

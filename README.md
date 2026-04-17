# AI导演分镜技能库

本仓库用于统一管理 AI 真人 / AI 导演分镜相关规则、模板与质检标准。

## 文件结构

### 核心技能文件
- `director-storyboard-core.md`：核心分镜拆解规则
- `director-storyboard-advanced.md`：分镜进阶精修版
- `AI导演分镜脚本-进阶精修版.md`：进阶精修规则
- `director-visual-design-core.md`：镜头画面设计与 Prompt 工程核心版
- `director-visual-design-advanced.md`：镜头画面设计进阶扩展包
- `VSS_StoryboardRules.md`：分镜方法论与批量生产规则
- `META_StoryboardProcess.md`：元流程（从剧本到分镜规则的通用方法论）

### 阶段技能文件
- `one`：第一阶段 — 视觉词典生成（城市搜索与风格锁定）
- `daoyan`：第二阶段 — 导演版本画面剧本改写
- `two`：第五阶段 — 视听单元拆解与交付

### 辅助技能
- `Dialogue_Shot_Sequence_Designer.SKILL.md`：对话镜头序列设计器
- `Emotional_Sequence_Designer.SKILL.md`：情绪序列设计器
- `Montage_Transition_Designer.SKILL.md`：蒙太奇/转场设计器
- `Seedance2_Prompt_Avoid_List_GitHub.md`：Seedance 2.0 提示词避坑清单

### 项目文件夹
- `Nightwolf-Empire/`：狼人帝国项目（北美女频短剧，12集）

## 使用方式
1. 先阅读 core 文件
2. 再叠加进阶精修版
3. 根据项目类型调用对应模板
4. 输出分镜后按质检清单复核

## 生产流水线（六阶段）

| 阶段 | 名称 | 调用技能 |
|------|------|---------|
| 阶段 0 | 物资接收与项目诊断 | 内置 |
| 第一阶段 | 城市搜索与风格锁定 | `one` |
| 第二阶段 | 导演版本画面 | `daoyan` |
| 第三阶段 | 逐镜头分镜拆解 | `director-storyboard-core` + 辅助技能 + `VSS_StoryboardRules` |
| 第四阶段 | 镜头画面设计与提示 | `director-visual-design-core` |
| 第五阶段 | 视听单元拆卸与交付 | `two` |

详见各项目文件夹中的 `pipeline.md` 了解具体项目的流水线配置。

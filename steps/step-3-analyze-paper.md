# Step 3: 按数字基因框架精读论文

## 目标

对筛选出的每篇论文进行深度分析。分析目标不是复述论文，而是判断它对用户的 **制造数字基因、DG-VLA、WAM、人机协作和工业数字孪生** 研究有什么价值。

## 核心原则

```text
1. 质量第一，宁可少读，也要读出可迁移的研究启发。
2. 每篇论文独立分析，避免上下文污染。
3. 结论必须回到用户研究主线。
4. 不只总结方法，还要判断它能否转化为模块、实验、约束或论文贡献。
5. 对不确定的内容必须明确标注，不要编造论文细节。
```

## 输入

每篇论文应包含：

- Title
- Authors
- Year / Venue
- Abstract
- PDF / arXiv / Project URL
- Code URL（如有）

## 推荐分析流程

### Phase 1: 论文基本理解

回答：

1. 这篇论文解决什么问题？
2. 它的输入、输出和任务场景是什么？
3. 它的核心方法是什么？
4. 它和已有方法相比解决了什么不足？

### Phase 2: 三层拆解

从感知、认知、动作三层拆解论文：

#### Perception Level

- 使用了哪些视觉、空间、几何或传感信息？
- 是否涉及 3D 场景、对象关系、姿态、拓扑、可供性？
- 是否能为 Digital DNA 提供稳定对象知识？

#### Cognition / Reasoning Level

- 是否使用 VLM、LLM、world model、memory、task graph、planner 或 policy？
- 如何表示任务状态、环境状态、人类意图或动作后果？
- 是否能为 Digital RNA 提供任务激活或动态表达机制？

#### Action Level

- 如何生成或引导机器人动作？
- 输出是轨迹、离散动作、关键帧、策略、约束、计划还是 affordance？
- 是否可以接入 Gene-as-Constraint 或 Gene-as-Policy Interface？

### Phase 3: 数字基因关系分析

必须从以下维度分析：

#### Digital DNA

判断论文是否提供稳定对象级制造知识，例如：

- geometry primitives
- object attributes
- material properties
- part hierarchy
- affordances
- assembly relations
- process constraints
- interface definitions

#### Digital RNA

判断论文是否提供任务级或执行级激活机制，例如：

- task-conditioned activation
- context-specific constraint selection
- action sequence generation
- dynamic topology update
- human intervention response
- adaptive replanning

#### Gene-as-Context

判断数字基因能否作为该方法的结构化上下文输入。

#### Gene-as-Constraint

判断数字基因能否作为该方法的约束层，限制不合理感知、规划或动作。

#### Gene-as-Memory

判断数字基因能否成为对象、工艺、工具、场景和协作历史的长期记忆。

#### Gene-as-Policy Interface

判断数字基因能否转换成策略条件、关键帧、动作参数、子任务或执行约束。

### Phase 4: 与 VLA / WAM / HRC 的关系

#### Relation to DG-VLA

回答：

- 它能增强 VLA 的哪个部分？语言层、视觉 grounding、动作层、策略层还是 memory？
- 数字基因应该以 prompt、retrieval context、constraint layer、memory module 还是 action interface 的方式进入？
- 它是否有助于未见物体泛化或长程任务执行？

#### Relation to WAM / World Model

回答：

- 它是否学习“世界如何因动作而变化”？
- 它是否支持状态转移、未来帧预测、动作后果预测？
- 它是否能与“第三视角连续动态学习 + 第一视角稀疏关键帧对齐”范式结合？
- 数字基因能否作为 world model 的先验、状态描述或约束？

#### Relation to HRC

回答：

- 它是否支持人类意图理解？
- 它是否支持人类干预后的任务重规划？
- 它是否能减少显式人类命令？
- 它是否能提升协作安全、鲁棒性和可解释性？

### Phase 5: 对用户研究的直接启发

必须给出具体可用结论：

- Possible use in DG-VLA:
- Possible use in DG-HRC:
- Possible use in digital twin:
- Possible experiment:
- Possible paper contribution:
- Possible figure / framework update:
- Possible baseline or comparison:

## 输出文档模板

```markdown
# Paper Analysis: [Title]

## 1. Basic Information

- Title:
- Authors:
- Year / Venue:
- URL:
- Code:
- Keywords:

## 2. One-Sentence Summary

用一句话说明这篇论文对用户研究的价值。

## 3. Core Problem

### 3.1 Problem Definition

### 3.2 Why It Matters for Embodied Manufacturing

## 4. Method Summary

### 4.1 Overall Pipeline

### 4.2 Perception Level

### 4.3 Cognition / Reasoning Level

### 4.4 Action Level

## 5. Relation to Manufacturing Digital Gene

### 5.1 Digital DNA

### 5.2 Digital RNA

### 5.3 Gene-as-Context

### 5.4 Gene-as-Constraint

### 5.5 Gene-as-Memory

### 5.6 Gene-as-Policy Interface

## 6. Relation to DG-VLA

## 7. Relation to WAM / World Model

## 8. Relation to Human-Robot Collaboration

## 9. Possible Integration into User's Framework

### 9.1 Module Position

说明它可以放在 DG-VLA / DG-HRC 框架的哪个模块。

### 9.2 Input / Output Interface

说明如果借鉴该方法，输入输出应该是什么。

### 9.3 Required Digital Gene Content

说明需要哪些数字基因内容作为支撑。

## 10. Possible Experiment

- Task:
- Dataset / Environment:
- Method:
- Baselines:
- Metrics:
- Expected Results:

## 11. Paper Contribution Ideas

给出 2-3 个可以转化为用户论文创新点的想法。

## 12. Limitations

说明该论文不适合直接用于制造场景的地方。

## 13. Follow-up Questions

列出后续需要继续查找的文献或问题。
```

## 输出路径

```text
output/papers/YYYY-MM-DD_XX_paper_title.md
```

## 质量检查

一篇论文分析必须包含：

- 至少一个与 Digital DNA / RNA 的判断
- 至少一个 DG-VLA 集成方式
- 至少一个 HRC 或 WAM 相关判断
- 至少一个可执行实验设想
- 至少一个可能论文贡献点

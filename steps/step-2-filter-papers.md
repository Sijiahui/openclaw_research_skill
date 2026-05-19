# Step 2: 筛选最有价值的 3-5 篇论文

## 目标

从候选论文中筛选出 **3-5 篇** 对用户当前研究最有价值的论文。筛选标准不再是泛泛的 Spatial AGI 相关性，而是判断论文是否能够支撑：

- 制造数字基因理论构建
- DG-VLA 框架设计
- WAM / world model 与数字基因结合
- 人机协作中的记忆对齐、任务重规划与主动适应
- 工业数字孪生与动态拓扑建模

## 严格约束

```text
1. 默认筛选 3-5 篇；如果用户明确要求数量，则按用户要求。
2. 必须排除已经分析过的论文。
3. 避免连续多天重复分析同一类论文。
4. 每篇论文必须给出选择理由和与用户研究的关系。
5. 不要因为论文热门就选择，必须说明它对制造数字基因 / DG-VLA / HRC 的具体价值。
```

## 优先选择规则

### 1. 与制造数字基因强相关

高优先级论文通常包含以下内容之一：

- 对象级结构化知识表示
- 几何原语、零件层级、装配关系
- 可供性、工具功能、操作接口
- 工艺流程、任务约束、装配/拆解约束
- 制造知识图谱、数字孪生、动态拓扑
- CAD / STEP / 3D 表示与机器人操作结合

### 2. 可增强 VLA

高优先级论文可能提供：

- 新的 Vision-Language-Action 架构
- 语言层知识注入机制
- 视觉 grounding / object grounding 方法
- action expert / policy interface 设计
- 长程任务分解与执行
- 未见物体泛化或跨对象迁移能力

### 3. 可增强 WAM / World Model

高优先级论文可能涉及：

- action-conditioned world model
- 机器人操作后果预测
- 视频生成 / 未来帧预测
- 状态转移建模
- 第三视角连续动态学习
- 第一视角稀疏关键帧对齐
- latent state 与机器人观测映射

### 4. 可支持 HRC

高优先级论文可能涉及：

- 人类意图理解
- 人机任务状态对齐
- proactive collaboration
- shared autonomy
- human intervention handling
- task replanning
- 安全、鲁棒、可解释协作

## 排除规则

排除以下论文：

1. 只做通用图文理解，没有空间、动作、机器人或制造关联。
2. 只做 benchmark，没有方法或研究启发。
3. 只关注通用 LLM 能力，无法转化为 VLA/WAM/HRC 模块。
4. 只做纯视觉识别，缺少对象关系、动作、任务或约束信息。
5. 与用户当前研究主线距离过远，无法形成实验或论文贡献。

## 评分标准

每篇候选论文按 100 分评分：

| 维度 | 分值 | 说明 |
|---|---:|---|
| Digital Gene 相关性 | 25 | 是否支持 Digital DNA/RNA、Gene-as-Context/Constraint/Memory |
| DG-VLA 价值 | 20 | 是否能增强 VLA 的语言、视觉、动作或策略层 |
| WAM / World Model 价值 | 15 | 是否支持状态转移、动作后果预测或世界模型训练 |
| HRC 价值 | 15 | 是否支持意图理解、任务重规划、主动适应或协作安全 |
| 工业制造可迁移性 | 15 | 是否能落到装配、拆解、检测、工艺规划等制造任务 |
| 新颖性与可写作性 | 10 | 是否能形成论文创新点、实验对比或综述段落 |

## 输出格式

```markdown
# Selected Papers: YYYY-MM-DD

## Selection Summary

- Candidate papers:
- Selected papers:
- Main theme:
- Reason for today's focus:

## Paper 01: Title

- URL:
- Score: xx/100
- Selected because:
- Relation to Digital Gene:
  - Digital DNA:
  - Digital RNA:
  - Gene-as-Context:
  - Gene-as-Constraint:
  - Gene-as-Memory:
- Relation to DG-VLA:
- Relation to WAM:
- Relation to HRC:
- Possible use in user's research:
- Priority: High / Medium / Low

## Paper 02: Title
...
```

## 筛选后的临时文件

保存为：

```text
/tmp/dg_vla_hrc_selected_YYYY-MM-DD.json
```

或手动阶段保存为：

```text
output/selected/YYYY-MM-DD_selected.md
```

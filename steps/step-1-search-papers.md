# Step 1: 搜索最新论文与项目

## 目标

搜索与 **制造数字基因、DG-VLA、WAM、具身智能、人机协作、工业数字孪生** 相关的最新论文、项目页和技术报告，形成候选论文池。

本步骤不追求数量越多越好，而是尽量覆盖用户研究主线中的关键方向。

## 核心搜索方向

### A. Manufacturing Digital Gene / Digital Twin

用于寻找制造数字基因的理论基础、对象表示、工艺知识、几何建模和数字孪生方法。

关键词：

- `manufacturing digital gene`
- `digital twin manufacturing robot`
- `industrial digital twin embodied AI`
- `manufacturing knowledge graph robot`
- `process knowledge representation manufacturing`
- `dynamic topology digital twin`
- `CAD robot learning manufacturing`

### B. VLA / Embodied Manipulation

用于寻找能够被数字基因增强的 VLA、机器人基础模型和长程操作方法。

关键词：

- `vision language action model robot`
- `VLA robot manipulation`
- `generalist robot policy language conditioned manipulation`
- `embodied AI manipulation`
- `robot foundation model manipulation`
- `language conditioned robot policy`
- `affordance robot manipulation VLM`

### C. World Model / WAM

用于寻找动作后果预测、状态转移建模、视频预测和世界模型相关研究。

关键词：

- `world model robot manipulation`
- `world action model robot`
- `video prediction robot manipulation`
- `action conditioned video generation robot`
- `dynamics model robot manipulation`
- `future frame prediction robot action`
- `third person video robot learning egocentric`

### D. HRC / Human-Robot Collaboration

用于寻找人机协作、主动适应、人类意图理解、任务重规划和共享自治研究。

关键词：

- `human robot collaboration task planning`
- `human intention prediction robot collaboration`
- `proactive human robot collaboration`
- `shared autonomy manufacturing robot`
- `collaborative assembly robot`
- `adaptive robot behavior human intervention`
- `human robot task replanning`

### E. Object-Centric / Geometry / Affordance

用于寻找支撑 Digital DNA 的稳定对象知识与可迁移表示。

关键词：

- `object centric representation robot manipulation`
- `geometric primitive robot manipulation`
- `object affordance learning robot`
- `3D scene graph robot manipulation`
- `part level representation robot`
- `semantic constraint robot planning`

## 推荐 arXiv 搜索命令

```bash
cd ~/.openclaw/workspace/skills/dg-vla-hrc-research/scripts

python3 search_arxiv.py "all:vision+all:language+all:action+all:robot" 20
python3 search_arxiv.py "all:world+all:model+all:robot+all:manipulation" 20
python3 search_arxiv.py "all:human+all:robot+all:collaboration" 20
python3 search_arxiv.py "all:digital+all:twin+all:manufacturing" 20
python3 search_arxiv.py "all:affordance+all:robot+all:manipulation" 20
python3 search_arxiv.py "all:object+all:centric+all:robot" 20
```

## 推荐 Web 搜索源

优先搜索：

- arXiv
- OpenReview
- Google Scholar 页面或论文项目页
- GitHub 项目页
- 机器人/VLA/WAM 研究团队主页
- 会议论文页面：CoRL、RSS、ICRA、IROS、NeurIPS、ICLR、CVPR、ICCV、ECCV、ACL、EMNLP、AAAI、IJCAI

## 候选论文记录格式

每篇候选论文至少记录：

```markdown
## Candidate Paper

- Title:
- Authors:
- Year / Date:
- Venue / Source:
- arXiv / PDF / Project URL:
- Keywords:
- Abstract:
- Initial relevance:
  - Digital Gene:
  - VLA / WAM:
  - HRC:
  - Digital Twin:
- Reason for keeping:
```

## 输出

将候选论文保存为：

```text
/tmp/dg_vla_hrc_candidates_YYYY-MM-DD.json
```

或者在手动运行阶段，直接保存为：

```text
output/candidates/YYYY-MM-DD_candidates.md
```

## 注意事项

1. 不要只搜索 `manufacturing digital gene`，因为该术语可能还不是主流关键词。
2. 应重点搜索可以支撑数字基因的相关概念，例如 object-centric representation、affordance、process constraint、world model、VLA、HRC。
3. 每次搜索要覆盖至少 3 个方向：VLA、WAM、HRC 或 Digital Twin。
4. 如果发现与用户当前论文选题高度相关的旧论文，也可以纳入候选池。

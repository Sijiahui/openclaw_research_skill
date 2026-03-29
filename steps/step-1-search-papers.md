# Step 1: 搜索arXiv最新论文

## 目标

使用arXiv API搜索与Spatial AGI相关的最新论文。

## 执行命令

```bash
cd ~/.openclaw/workspace/skills/spatial-agi-research/scripts

# 搜索多个关键词组合
python3 search_arxiv.py "all:spatial+all:intelligence" 20
python3 search_arxiv.py "all:VLM+all:3D" 20
python3 search_arxiv.py "all:Gaussian+Splatting" 20
python3 search_arxiv.py "all:world+all:model" 20
python3 search_arxiv.py "all:embodied+all:AI" 20
```

## 搜索关键词

**核心关键词**:
- `spatial intelligence`
- `VLM (Vision-Language Models)`
- `3D Gaussian Splatting`
- `world model`
- `embodied AI`

**扩展关键词**:
- `spatial reasoning`
- `3D understanding`
- `scene understanding`
- `video generation`
- `robot learning`
- `UAV`
- `drone`
- `aerial`

## 输出

- **JSON文件**: `/tmp/today_papers.json`
- **内容**: 论文列表，包含：
  - 标题
  - 摘要
  - 链接
  - 作者
  - 发布日期

## 搜索结果示例

```json
{
  "papers": [
    {
      "title": "Matryoshka Gaussian Splatting",
      "summary": "...",
      "arxiv_url": "https://arxiv.org/abs/2603.19234v1",
      "pdf_url": "https://arxiv.org/pdf/2603.19234v1",
      "authors": ["Zhilin Guo", "..."],
      "published": "2026-03-19"
    },
    ...
  ]
}
```

## 注意事项

- ✅ 每个关键词搜索20篇（可调整）
- ✅ 总共约100篇候选论文
- ✅ 自动保存到临时文件
- ✅ 支持arXiv API限流

## 预计时间

- 10分钟（5个关键词 × 2分钟/关键词）

---

## 执行状态

**Status**: ✅ Completed (Today's Run)
**Completed At**: 2026-03-30T07:05:00+08:00

### 执行记录

1. **arXiv API 限流问题**: API返回429错误，切换到web_fetch方案
2. **成功获取数据**: 通过arXiv网页搜索获取120篇论文
3. **输出文件**: `data/papers.json` (16,242 bytes)

### 搜索类别 (2026-03-30)

| 类别 | 论文数 | 关键发现 |
|------|--------|----------|
| 3D Gaussian Splatting | 25 | ViewSplat, GaussFusion, MoRGS |
| Spatial Intelligence | 18 | Holi-Spatial, 3DGSNav, OpenMonoGS-SLAM |
| World Model + 4D | 22 | Kinema4D, Phys4D, Omni-WorldBench |
| Embodied AI + VLA | 28 | ST-VLA, StemVLA, ABot-M0 |
| Robot Perception | 18 | PAWS, HyReach, Dex4D |

### Top 10 优先论文 (2026-03-30)

1. **Kinema4D** - 运动学4D世界建模
2. **Holi-Spatial** - 视频流到整体空间智能
3. **ST-VLA** - 4D感知VLA模型
4. **Thinking in Dynamics** - MLLM在4D物理世界中的推理
5. **3DGSNav** - 3DGS + VLM导航
6. **LagMemo** - 语言3DGS记忆系统
7. **Omni-WorldBench** - 世界模型评估基准
8. **StemVLA** - VLA + 3D几何 + 4D历史
9. **SimWorld** - 物理和社会世界模拟器
10. **Phys4D** - 物理一致的4D建模

### 今日新增论文 (9篇)

- **PAWS** (2026-03-26) - 大规模关节感知
- **ViewSplat** (2026-03-26) - 视角自适应动态3DGS
- **GaussFusion** (2026-03-26) - 几何感知视频生成器
- **MoRGS** (2026-03-26) - 高斯运动推理
- **LiveWorld** (2026-03-24) - 生成式视频世界模型
- **PhotoAgent** (2026-03-24) - 空间美学理解机器人
- **Omni-WorldBench** (2026-03-23) - 世界模型基准
- **HyReach** (2026-03-22) - 视觉引导混合机械臂
- 更多详见 `data/papers.json`

### 下一步

继续执行 `step-2-filter-papers.md` 进行论文筛选和深度分析。

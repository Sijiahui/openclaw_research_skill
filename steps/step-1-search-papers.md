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

**Status**: ✅ Completed (2026-04-07 Run)

### 执行记录 (2026-04-07)

1. **arXiv API 限流**: API返回0篇，降级为web_fetch抓取arXiv list页面
2. **成功获取数据**: 4个类别共419篇新论文，关键词筛选后158篇高相关
3. **输出文件**: `data/papers_2026-04-07.json` (180KB)

### 搜索类别 (2026-04-07)

| 类别 | 新论文数 | 说明 |
|------|---------|------|
| cs.CV | 180 | 计算机视觉 |
| cs.RO | 53 | 机器人学 |
| cs.GR | 4 | 计算机图形学 |
| cs.AI | 248 | 人工智能 |

### Top 15 优先论文 (2026-04-07)

1. **TrackerSplat** (score=8, cs.CV) - 点跟踪加速动态3D高斯重建
2. **Delaunay Canopy** (score=6, cs.CV) - 机载LiDAR点云Delaunay图建筑线框重建
3. **GP-4DGS** (score=6, cs.CV) - 变分高斯过程概率4D高斯泼溅
4. **Rendering Multi-Human and Multi-Object with 3DGS** (score=6, cs.CV) - 多人多物体3DGS渲染
5. **SparseSplat** (score=6, cs.CV) - 像素不对齐前馈3DGS
6. **MedGS** (score=6, cs.CV) - 多模态3D医学影像高斯泼溅
7. **SING3R-SLAM** (score=6, cs.CV) - 子图室内单目高斯SLAM
8. **DePT3R** (score=6, cs.CV) - 联合密集点跟踪与动态场景3D重建
9. **Uncertainty-Aware 4DGS** (score=6, cs.CV) - 不确定性感知4DGS遮挡人体渲染
10. **LiDAR Off-Road Nav Stack** (score=6, cs.RO) - 开源LiDAR+单目越野自主导航
11. **Streaming 3D Gaussians** (score=6, cs.GR) - 实时渲染场景流式3D高斯
12. **PlayGen-MoG** (score=4, cs.CV) - 混合高斯轨迹预测多智能体
13. **Contrastive Language-Colored Pointmap** (score=4, cs.CV) - 统一3D场景理解对比预训练
14. **Rascene** (score=4, cs.CV) - mmWave通信信号高保真3D场景成像
15. **Cross-Vehicle 3D Geometric** (score=4, cs.CV) - 自监督环绕深度估计跨车辆3D一致性

### 趋势观察 (2026-04-07)

1. **3DGS持续爆发**: TrackerSplat(动态)、GP-4DGS(概率4D)、SparseSplat(前馈)、MedGS(医学)、SING3R-SLAM、Streaming
2. **动态场景重建**: TrackerSplat(点跟踪+动态3DGS)、DePT3R(跟踪+重建联合)、Uncertainty-Aware 4DGS
3. **Embodied Navigation**: LiDAR越野导航、ExploreVLA(端到端驾驶)、NavCrafter(单图3D场景探索)
4. **多智能体**: PlayGen-MoG轨迹预测

---

**Status**: ✅ Completed (2026-04-02 Run)
**Completed At**: 2026-04-02T07:05:00+08:00

### 执行记录 (2026-04-02)

1. **arXiv API 限流**: API返回"Rate exceeded"，web_search无Brave API key
2. **降级方案**: 直接抓取arXiv list页面(cs.CV/cs.RO/cs.GR/cs.AI)的HTML，用正则解析标题/作者/摘要
3. **成功获取数据**: 4个类别共219篇新论文(2026-04-01发布)，关键词筛选后42篇高相关
4. **输出文件**: `data/papers_2026-04-02.json` (63,052 bytes)

### 搜索类别 (2026-04-02)

| 类别 | 新论文数 | 说明 |
|------|---------|------|
| cs.CV | 116 | 计算机视觉 |
| cs.RO | 35 | 机器人学 |
| cs.GR | ~30 | 计算机图形学 |
| cs.AI | ~38 | 人工智能 |

### Top 15 优先论文 (2026-04-02)

1. **OccSim** (score=10) - 多公里范围占用世界模型仿真
2. **SceneTeract** (score=10) - VLM在3D场景中的功能可供性智能体
3. **Stepper** (score=9) - 多视图全景逐步沉浸式场景生成
4. **UltraG-Ray** (score=9) - 基于物理的高斯光线投射新视角合成
5. **AutoWorld** (score=8, cs.RO) - 自监督世界模型多智能体交通仿真
6. **PRISM** (score=7) - Embodied VLM零售视频多视角数据集
7. **MotionScale** (score=7) - 可扩展4D高斯动态场景外观/几何/运动重建
8. **AA-Splat** (score=7) - 抗锯齿前馈高斯泼溅
9. **CReF** (score=7, cs.RO) - 跨模态循环融合深度条件人形运动
10. **LightHarmony3D** (score=6) - 3DGS物体插入光照阴影协调
11. **SparseDriveV2** (score=3) - 端到端自动驾驶评分
12. **LatentPilot** (score=3) - 场景感知VLN潜在视觉推理
13. **DIAL** (score=5, cs.RO) - 解耦意图与动作的潜在世界模型VLA
14. **Gleanmer** (score=4, cs.RO) - 6mW实时3D高斯占用映射SoC
15. **Extend3D** (score=4) - 城镇尺度3D生成

### 趋势观察 (2026-04-02)

1. **世界模型实际应用**: OccSim(AV仿真)、AutoWorld(交通)、DIAL(VLA)将世界模型从论文推向系统
2. **3DGS继续演进**: AA-Splat(抗锯齿)、MotionScale(4D动态)、Gleanmer(硬件SoC)、LightHarmony3D(光照)
3. **VLM+3D场景理解**: SceneTeract(VLM可供性)、SeGPruner(3D QA)、PRISM(Embodied VLM)
4. **端到端自动驾驶**: SparseDriveV2、AutoWorld规模化

---

### 执行记录 (2026-04-01)

1. **arXiv API 限流**: API返回空结果（5个查询全部0篇），降级为web_fetch抓取arXiv搜索页
2. **成功获取数据**: 通过5个搜索查询获取78篇论文
3. **输出文件**: `data/papers_2026-04-01.json` (17,306 bytes)

### 搜索类别 (2026-04-01)

| 类别 | 论文数 | 关键发现 |
|------|--------|----------|
| 3D Gaussian Splatting | 25 | GeoHCC, ObjectMorpher, GS3LAM, ViewSplat, AirSplat, GaussFusion |
| Video Generation/World Models | 15 | Video Gen as World Models综述, VGGRPO, LOME, DreamerAD |
| Embodied AI/Robot | 18 | Learning Multi-View Spatial, ROSClaw, Kinema4D, Ego to World |
| Spatial Intelligence/VLM/3D | 12 | HiSpatial, GST-VLA, Holi-Spatial, Thinking with Geometry |
| UAV/Drone | 8 | AeroDaaS, VLN-Pilot, VLA-AN, AeroVerse |

### Top 10 优先论文 (2026-04-01)

1. **Video Generation Models as World Models** - 系统综述，视频生成作为世界模型
2. **VGGRPO** - 4D Latent Reward世界一致性视频生成
3. **Kinema4D** - 运动学4D世界建模
4. **HiSpatial** - VLM层级3D空间理解
5. **GaussFusion** - 3DGS + 几何感知视频生成器
6. **Ego to World** - 多智能体协作空间推理基准
7. **PhotoAgent** - 3DGS世界模型机器人摄影师
8. **Persistent Robot World Models** - 稳定多步rollout
9. **Holi-Spatial** - 视频流→整体3D空间智能
10. **GST-VLA** - 高斯空间token注入VLA

### 趋势观察 (2026-04-01)

1. **4D世界建模**: VGGRPO, Kinema4D, Persistent Robot World Models, LOME
2. **几何感知VLM**: HiSpatial, GST-VLA, Thinking with Geometry将3D几何引入语言模型
3. **3DGS+生成式AI**: GaussFusion, ViewSplat, AirSplat将3DGS与视频生成结合
4. **Embodied AI系统化**: ROSClaw框架、Active Inference理论
5. **UAV领域VLA化**: VLN-Pilot, VLA-AN将VLA应用于无人机导航

---

### 历史记录

#### 2026-03-31

1. **arXiv API 限流**: API返回空结果，使用web_fetch抓取arXiv网页
2. **成功获取数据**: 通过4个搜索查询获取65篇最新论文
3. **输出文件**: `data/papers_2026-03-31.json` (34,850 bytes)

### 搜索类别 (2026-03-31)

| 类别 | 论文数 | 关键发现 |
|------|--------|----------|
| 3D Gaussian Splatting | 20 | ViewSplat, GaussFusion, AirSplat, GLINT, MoRGS |
| Spatial Intelligence/VLM | 15 | HiSpatial, Make Geometry Matter, S3-Bench |
| Embodied AI/VLA | 15 | Ego-to-World, OxyGen, SIMART, GHOST |
| Video Generation/World Models | 15 | VGGRPO, ABot-PhysWorld, DreamerAD, WildWorld |

### Top 10 优先论文 (2026-03-31)

1. **VGGRPO** - 4D Latent Reward世界一致性视频生成
2. **Kinema4D** - 运动学4D世界建模 (已在库)
3. **Make Geometry Matter** - VLM几何token注入
4. **HiSpatial** - VLM层级3D空间理解
5. **Ego to World** - 多智能体协作空间推理基准
6. **GaussFusion** - 3DGS + 几何感知视频生成器
7. **PhotoAgent** - 3DGS世界模型机器人摄影师
8. **ABot-PhysWorld** - 物理对齐世界基础模型
9. **Persistent Robot World Models** - 稳定多步rollout
10. **ViewSplat** - 视角自适应动态3DGS

### 今日关键论文 (2026-03-27)

- **VGGRPO** - 4D Latent Reward视频生成
- **PhysVid** - 物理感知生成视频模型
- **Make Geometry Matter** - VLM空间推理几何token
- **PerceptionComp** - 感知中心推理视频基准
- **Detailed Geometry and Appearance** - 2D GS联合优化
- **Drive-Through 3D Vehicle** - SfM + 失真感知3DGS
- **GLINT** - 场景级透明度高斯辐射传输
- **R-PGA** - 可重光照3DGS对抗攻击

### 趋势观察

1. **4D世界建模**: VGGRPO, Kinema4D, ABot-PhysWorld聚焦4D时空
2. **几何感知VLM**: Make Geometry Matter, HiSpatial将3D几何引入语言模型
3. **3DGS+Embodied**: PhotoAgent, GaussFusion将3DGS作为机器人世界模型
4. **世界一致性**: 视频生成模型开始强调物理和时空一致性

### 历史记录

#### 2026-03-30
- 获取120篇论文
- 关键发现: Kinema4D, Holi-Spatial, ST-VLA

### 下一步

继续执行 `step-2-filter-papers.md` 进行论文筛选和深度分析。

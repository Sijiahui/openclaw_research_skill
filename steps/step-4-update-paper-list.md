# Step 4: 更新论文列表

## 目标

更新`papers_list.md`，添加今天分析的5篇论文信息。

## 执行步骤

### 1. 定位文件

```bash
PAPERS_LIST="/home/cwh/coding/spatial_agi/papers_list.md"
```

### 2. 添加今天的论文条目

在文件末尾添加：

```markdown
## YYYY-MM-DD 研究的论文（精选5篇）

1. **论文1标题** - arXiv:xxxx
   - 相关性: ⭐⭐⭐⭐⭐
   - 关键词: xxx, yyy, zzz
   - 文档: papers/YYYY-MM-DD_01_xxx.md
   - NotebookLM: [notebook_id]

2. **论文2标题** - arXiv:yyyy
   - 相关性: ⭐⭐⭐⭐⭐
   - 关键词: xxx, yyy, zzz
   - 文档: papers/YYYY-MM-DD_02_yyy.md
   - NotebookLM: [notebook_id]

3. **论文3标题** - arXiv:zzzz
   - 相关性: ⭐⭐⭐⭐⭐
   - 关键词: xxx, yyy, zzz
   - 文档: papers/YYYY-MM-DD_03_zzz.md
   - NotebookLM: [notebook_id]

4. **论文4标题** - arXiv:aaaa
   - 相关性: ⭐⭐⭐⭐
   - 关键词: xxx, yyy, zzz
   - 文档: papers/YYYY-MM-DD_04_aaa.md
   - NotebookLM: [notebook_id]

5. **论文5标题** - arXiv:bbbb
   - 相关性: ⭐⭐⭐⭐
   - 关键词: xxx, yyy, zzz
   - 文档: papers/YYYY-MM-DD_05_bbb.md
   - NotebookLM: [notebook_id]
```

### 3. 提取论文信息

从Subagent的输出中提取：
- 论文标题
- arXiv ID
- 相关性评分（⭐评分）
- 关键词
- 文档路径
- NotebookLM笔记本ID

## 示例

```markdown
## 2026-03-22 研究的论文（精选5篇）

1. **Matryoshka Gaussian Splatting** - arXiv:2603.19234v1
   - 相关性: ⭐⭐⭐⭐⭐
   - 关键词: 3D Gaussian Splatting, LoD, Real-time Rendering
   - 文档: papers/2026-03-22_01_Matryoshka_Gaussian_Splatting.md
   - NotebookLM: 9c0f25b5-432d-4103-8210-55eadd1f5d9c

2. **GSMem: 3D Gaussian Splatting as Persistent Spatial Memory** - arXiv:2603.19137v1
   - 相关性: ⭐⭐⭐⭐⭐
   - 关键词: Spatial Memory, Embodied AI, 3D Gaussian Splatting
   - 文档: papers/2026-03-22_02_GSMem.md
   - NotebookLM: [notebook_id]
...
```

## 预计时间

- 5分钟

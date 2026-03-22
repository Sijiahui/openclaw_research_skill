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

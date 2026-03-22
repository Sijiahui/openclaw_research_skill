# Step 3: 使用Subagent精读每篇论文

## 目标

为每篇筛选出的论文启动独立的Subagent进行深度分析。

## 核心原则

```
╔════════════════════════════════════════════════════════════╗
║  🎯 质量第一原则                                           ║
║                                                              ║
║  ✅ 每篇论文15-20分钟是正常的                              ║
║  ✅ 深度分析比快速完成更重要                                ║
║  ✅ 使用Subagent避免token限制                              ║
║  ✅ 每篇论文独立处理，互不干扰                             ║
║                                                              ║
║  ❌ 不要为了省时而创建精简版文档                           ║
║  ❌ 不要因为token不足而降低质量                            ║
║  ❌ 不要跳过NotebookLM问答环节                             ║
╚════════════════════════════════════════════════════════════╝
```

## 执行流程

### 1. 读取筛选后的论文列表

```bash
PAPERS_FILE="/tmp/spatial_agi_papers_$(date +%Y-%m-%d).json"

# 提取论文信息
PAPERS=$(cat "$PAPERS_FILE" | jq -r '.papers[] | "\(.title)|\(.arxiv_url)|\(.pdf_url)"')
```

### 2. 为每篇论文启动Subagent

```bash
for PAPER_INFO in $PAPERS; do
  IFS='|' read -r TITLE ARXIV_URL PDF_URL <<< "$PAPER_INFO"
  
  # 生成paper_id（用于文件命名）
  PAPER_ID=$(echo "$TITLE" | sed 's/[^a-zA-Z0-9]/_/g')
  
  echo "📚 处理论文: $TITLE"
  
  # 启动Subagent
  sessions_spawn \
    --mode run \
    --runtime subagent \
    --task "使用paper-analysis skill精读论文: $TITLE
    
论文信息:
- 标题: $TITLE
- arXiv: $ARXIV_URL
- PDF: $PDF_URL
- Paper ID: $PAPER_ID

要求:
1. 创建NotebookLM笔记本并记录ID
2. 添加arXiv页面和PDF作为来源
3. 询问3个核心问题（核心算法、与Spatial AGI关系、创新点/局限）
4. 生成演示文稿（3-5分钟）
5. 生成中文音频概览（2-3分钟）
6. 创建详细markdown文档（至少500行）
7. 保存到 /home/cwh/coding/auto_blog/spatial_agi/papers/

输出格式:
- 返回笔记本ID
- 返回文档路径
- 返回文档行数
- 返回演示文稿生成状态
- 返回音频生成状态" \
    --timeout 1500 \
    --run-timeout 1500
done

echo "✅ 所有论文精读完成"
```

## Subagent执行流程

### Phase 1: 创建NotebookLM笔记本

```bash
export NOTEBOOKLM_PROXY="socks5://127.0.0.1:1080"

# 创建笔记本
NOTEBOOK_ID=$(~/miniconda3/bin/conda run -n base notebooklm create "$PAPER_TITLE" | grep -oP 'Created notebook: \K[a-f0-9-]+')

# 验证ID
if [ -z "$NOTEBOOK_ID" ]; then
    echo "❌ 错误：笔记本ID未设置"
    exit 1
fi

echo "✅ 笔记本创建成功: $NOTEBOOK_ID"
```

### Phase 2: 添加来源

```bash
# 添加arXiv页面
~/miniconda3/bin/conda run -n base notebooklm source add -n "$NOTEBOOK_ID" --type url "$ARXIV_URL"

# 添加PDF链接（以网站形式）
if timeout 90 ~/miniconda3/bin/conda run -n base notebooklm source add -n "$NOTEBOOK_ID" --type url "$PDF_URL"; then
    echo "✅ PDF链接添加成功"
else
    # Fallback: 使用HTML版本
    HTML_URL=$(echo "$ARXIV_URL" | sed 's|/abs/|/html/|')
    ~/miniconda3/bin/conda run -n base notebooklm source add -n "$NOTEBOOK_ID" --type url "$HTML_URL"
    echo "✅ HTML版本添加成功"
fi

# 等待处理
sleep 30
```

### Phase 3: 询问3个核心问题

```bash
# Q1: 核心算法原理
Q1_ANSWER=$(timeout 90 ~/miniconda3/bin/conda run -n base notebooklm ask \
  -n "$NOTEBOOK_ID" \
  "这篇文章的核心算法原理是什么？请详细描述：1) 核心思想和动机，2) 主要技术方法，3) 算法流程和关键步骤，4) 输入输出。")

# Q2: 与Spatial AGI的关系
Q2_ANSWER=$(timeout 90 ~/miniconda3/bin/conda run -n base notebooklm ask \
  -n "$NOTEBOOK_ID" \
  "这篇文章与通用空间智能（Spatial AGI）有什么关系？请分析：1) 如何理解和表示空间，2) 如何处理空间关系，3) 对Spatial AGI有什么启发，4) 可以应用到哪些Spatial AGI场景。")

# Q3: 创新点和局限性
sleep 30
Q3_ANSWER=$(timeout 90 ~/miniconda3/bin/conda run -n base notebooklm ask \
  -n "$NOTEBOOK_ID" \
  "基于前面的分析，这个方法的主要创新点和局限性是什么？与其他相关工作相比有什么优势和劣势？")
```

### Phase 4: 生成演示文稿（可选）

```bash
echo "📊 生成演示文稿..."
~/miniconda3/bin/conda run -n base notebooklm generate slide-deck -n "$NOTEBOOK_ID"
sleep 180
```

### Phase 5: 生成中文音频（可选）

```bash
echo "🎧 生成中文音频概览..."
~/miniconda3/bin/conda run -n base notebooklm generate audio -n "$NOTEBOOK_ID" --language zh-CN
sleep 150
```

### Phase 6: 创建详细文档

```bash
# 使用收集的信息创建markdown文档
# 至少500行，包含完整的问答记录
# 保存到: /home/cwh/coding/auto_blog/spatial_agi/papers/YYYY-MM-DD_XX_paper_title.md
```

## 质量要求

- ✅ 文档至少500行
- ✅ 包含完整的NotebookLM问答记录（不总结）
- ✅ 包含与Spatial AGI的关系分析
- ✅ 包含个人思考和见解
- ✅ 包含NotebookLM笔记本ID

## 预计时间

- **单篇论文**: 18分钟
- **5篇论文（串行）**: 90分钟
- **5篇论文（并行）**: 20-30分钟

## 注意事项

1. ✅ **必须使用Subagent**：避免主session的token限制
2. ✅ **每篇独立上下文**：互不干扰
3. ✅ **质量优先**：宁可多花时间，也要确保质量
4. ✅ **记录笔记本ID**：用于后续查询

# Step 0: 完成度检查与补充

## 目标

检查昨天任务是否完整完成，如果未完成则先补充缺失内容。**补充完成后（或昨天已完整完成），必须继续执行今天的Step 1-7任务。**

## 执行步骤

### 1. 检查昨天的论文数量

```bash
YESTERDAY=$(date -d yesterday +%Y-%m-%d)
BLOG_DIR="/home/cwh/coding/spatial_agi"

# 检查论文数量
PAPERS_COUNT=$(ls "$BLOG_DIR"/papers/${YESTERDAY}_*.md 2>/dev/null | wc -l)
echo "📄 昨天论文: $PAPERS_COUNT/5"

if [ $PAPERS_COUNT -lt 5 ]; then
    echo "⚠️  论文数量不足，缺少 $((5 - PAPERS_COUNT)) 篇"
fi
```

### 2. 检查每日思考

```bash
THINKING_FILE="$BLOG_DIR/daily_thinking/${YESTERDAY}.md"

if [ -f "$THINKING_FILE" ]; then
    LINES=$(wc -l < "$THINKING_FILE")
    echo "💭 思考: $LINES 行"
    
    if [ $LINES -lt 800 ]; then
        echo "⚠️  思考行数不足（$LINES < 800）"
    fi
else
    echo "❌ 思考未生成"
fi
```

### 3. 检查papers_list.md

```bash
if grep -q "$YESTERDAY" "$BLOG_DIR/papers_list.md" 2>/dev/null; then
    echo "✅ papers_list.md 已更新"
else
    echo "⚠️  papers_list.md 未更新"
fi
```

### 4. 判断是否需要补充

```bash
NEED_SUPPLEMENT="false"

if [ $PAPERS_COUNT -lt 5 ]; then
    NEED_SUPPLEMENT="true"
fi

if [ ! -f "$THINKING_FILE" ] || [ $(wc -l < "$THINKING_FILE" 2>/dev/null || echo 0) -lt 800 ]; then
    NEED_SUPPLEMENT="true"
fi

if [ "$NEED_SUPPLEMENT" = "true" ]; then
    echo "🔄 需要补充昨天的任务"
    
    # 创建补充任务文件
    cat > "/tmp/spatial_agi_supplement_$YESTERDAY.txt" << EOF
补充任务 - $YESTERDAY

论文: $PAPERS_COUNT/5
思考: $(test -f "$THINKING_FILE" && echo "$(wc -l < "$THINKING_FILE") 行" || echo "未生成")
列表: $(grep -q "$YESTERDAY" "$BLOG_DIR/papers_list.md" 2>/dev/null && echo "已更新" || echo "未更新")

优先级:
1. 思考（最高）
2. 论文
3. papers_list.md更新
EOF
    
    echo "📝 补充任务已记录: /tmp/spatial_agi_supplement_$YESTERDAY.txt"
else
    echo "✅ 昨天任务已完整完成"
fi

echo ""
echo "=========================================="
echo "🚀 准备执行今天的任务（Step 1-7）"
echo "=========================================="
echo ""
echo "⚠️  重要：无论昨天是否需要补充，都要继续执行今天的Step 1-7！"
echo ""
```

## 补充流程（如果需要）

### 优先级1: 生成每日思考

即使只有1-2篇论文，也要生成思考（基于已有论文）。

### 优先级2: 补充论文

从昨天的论文列表中选择未分析的论文，使用Subagent独立分析。

### 优先级3: 更新papers_list.md

添加昨天的论文条目。

## 输出

- ✅ 状态文件: `/tmp/spatial_agi_supplement_$YESTERDAY.txt`（如果需要补充）
- ✅ 补充完成后的报告

## ⚠️ 重要提醒：必须继续执行今天的任务

```
╔════════════════════════════════════════════════════════════╗
║  🚨 Step 0完成后，必须继续执行今天的Step 1-7！              ║
║                                                              ║
║  ❌ 错误：Step 0完成后停止                                   ║
║  ✅ 正确：Step 0 → Step 1 → Step 2 → ... → Step 7           ║
║                                                              ║
║  无论昨天是否完成，都要执行今天的任务：                      ║
║  1. Step 1: 搜索今天的论文                                   ║
║  2. Step 2: 筛选5篇论文                                      ║
║  3. Step 3: 精读5篇论文                                      ║
║  4. Step 4: 更新论文列表                                     ║
║  5. Step 5: 生成每日思考                                     ║
║  6. Step 6: 验证质量                                         ║
║  7. Step 7: Git推送                                          ║
╚════════════════════════════════════════════════════════════╝
```

## 预计时间

- 检查: 1分钟
- 补充: 30-60分钟（如果需要）
- **继续执行: Step 1-7（约60-90分钟）**

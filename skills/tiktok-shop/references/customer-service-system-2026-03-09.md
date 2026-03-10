# Customer Service System Reference — TikTok Shop Japan

**Last Updated:** 2026-03-09
**Applicable Region:** JP (can generalize to US/UK with caution)

---

## 1. Entry Points

### Primary URL
```
https://seller.tiktokshopglobalselling.com/chat?shop_region=JP
```

### From Seller Center Home
- Top navigation bar → Headset icon (Customer Service)
- ⚠️ Opens **NEW tab** — must use `browser tabs` to discover and switch

---

## 2. Main Page Layout

### 2.1 Top Bar (Metrics)
| Field | Observed Value |
|-------|---------------|
| Current Agent | Customer Service5741 |
| Shop | JP(KosblingDIY) |
| Unassigned Chats | 暂无未分配的聊天 |
| 24h Response Rate | - (not shown in real-time) |
| Satisfaction Rate | - (not shown in real-time) |
| Today's Sessions | 0 (current agent only) |
| View Details | Link → analytics page |

### 2.2 Filter Panel (Left Side)
| Filter | Options | Default |
|--------|---------|---------|
| 客服消息 (Agent) | 我 / 全选 / Individual agents | 我 |
| 状态 (Status) | 全部, 紧急, 已过期, 即将过期, 未回复, 未读, 已加星标, 已关闭 | 紧急 |
| 按类目筛选 (Category) | 全部, 售后, 物流, 售前 | 全部 |

### 2.3 Conversation List
- Tabs: 已分配 (Assigned) / 未分配 (Unassigned)
- Search: 搜索所有聊天记录
- Per-conversation fields:
  - Buyer username
  - Last message time
  - Message preview
  - Customer tag: 常客 / 近期客户 / 现有粉丝 / 潜在客户
  - Assigned agent

### 2.4 Detail Panel (Right)
- Buyer info
- Order ID
- Status (进行中/已关闭)
- Assigned agent
- Message timeline

---

## 3. Critical: How to View ALL Agent Conversations

### Step-by-Step:
1. Find the dropdown arrow next to "客服消息： 我"
2. Click the dropdown to expand agent list
3. Click "全选" (Select All) button
4. Also change status filter from "紧急" to "全部"

### ⚠️ Common Pitfalls
- **Default shows only YOUR conversations** — must switch to "全部" / "全选"
- **Status defaults to "紧急"** — not "全部", will miss non-urgent chats
- **Both filters need changing** for complete view

---

## 4. Analytics Page (View Details)

### URL
```
https://seller.tiktokshopglobalselling.com/chat/compass/service-analytics/chat-trend?shop_region=JP
```

### Tab: 聊天概览 (Chat Overview)
| Metric | Value | Competitor Benchmark | Change |
|--------|-------|---------------------|--------|
| 满意度 (Satisfaction) | 75% | 84% | -25% |
| 24h Response Rate | 93.75% | 84.23% | -6.25% |
| 转化率 (Conversion) | 97.75% | 33.30% | -0.52% |
| 评价数 (Ratings) | 12 | - | -36.84% |

**Satisfaction Breakdown:**
- 满意: 75% (-25%)
- 不满意: 25%
- 差评原因: 其他(100%)

**Trend Chart Options:**
- 收到的聊天数 48
- 24 小时响应率
- 满意度
- 平均首次响应时长 368.4分钟
- 转化率

### Tab: 全部聊天 (All Chats)
| Metric | Value | Change |
|--------|-------|--------|
| 客户发起的聊天数 | 48 | -11.11% |
| 商家处理的聊天数 | 48 | -11.11% |
| 24 小时响应率 | 93.75% | -6.25% |
| 排队时长 | 62.3分钟 | - |
| 平均处理时长 | 592.7分钟 | - |

**Filters:**
- 聊天分类: 全部 / 超时响应 / 未响应 / 满意度(3星及以下) / 由聊天助手回复
- 聊天标签: 全部 / 售后 / 物流 / 售前
- 客服专员: dropdown select
- 日期范围: start-end
- 客户: username search

**Table Columns:**
- 客服专员
- 客户
- 状态
- 聊天发起人
- 标签
- 首次响应时长
- 时长
- 客户评分
- 评价原因
- 操作（查看）

---

## 5. Quick Reference by Use Case

| What You Need | Where to Find It |
|---------------|-----------------|
| All agent conversations | Main page → 客服消息 → 全选 + 状态 → 全部 |
| My conversations only | Main page → 客服消息 → 我 (default) |
| Response rate | View Details → 聊天概览 |
| Satisfaction rate | View Details → 聊天概览 |
| Backlog (unreplied) | Status filter → 未回复 |
| Urgent chats | Status filter → 紧急 |
| Unassigned chats | Tab → 未分配 |
| Per-agent workload | View Details → 全部聊天 → 客服专员 filter |
| Customer chat history | Main page → search by username |

---

## 6. Read-Only vs. Forbidden Actions

### ✅ Safe (Read-Only)
- Browse conversation list
- View conversation details
- View analytics/statistics
- Use filters and search
- Click "View Details"

### ❌ Forbidden
- Reply to buyer messages
- Send any messages
- Create/modify/close tickets
- Assign conversations
- Modify customer tags
- Use automation tools

---

## 7. Cross-Region Generalization

Based on JP observations, these rules should apply to US/UK:

1. **URL Pattern**: `https://seller.tiktokshopglobalselling.com/chat?shop_region={XX}`
2. **Default Filter Behavior**: Shows only current agent, needs switch to "all"
3. **Status Default**: Not "all", must manually change
4. **Analytics Entry**: "View Details" link from main CS page
5. **Key Metrics Location**: Top nav bar (response rate, satisfaction, today's sessions)

---

## 8. Notes & Limitations

- Real-time metrics (response rate, satisfaction) show as "-" on main page
- Full metrics available in analytics (View Details)
- Timezone shows confusing "法国 / GMT+9 (东京)" — likely a display bug
- "今日会话" shows only current agent's count, not total team
- This doc based on JP store; US/UK UI may vary slightly

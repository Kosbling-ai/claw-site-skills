# Customer Service System — United States (US)

**Last Updated:** 2026-03-09
**Profile:** kosbling
**Store:** KosblingDiyShop
**Status:** ⏳ 需要用 profile="kosbling" 复核

---

## 1. Entry (⏳ 待复核)

### Expected URL
```
https://seller.tiktokshopglobalselling.com/chat?shop_region=US
```

### Expected Navigation
- Seller Center 首页 → 顶部导航栏 → 耳机图标 (Customer Service)
- ⏳ 待确认：是否也是新开 tab

---

## 2. Main Page (⏳ 待复核)

### 2.1 Top Metrics Bar (⏳ 待复核)
| Field | Expected |
|-------|----------|
| 当前账号 | 待确认 |
| 店铺 | KosblingDiyShop |
| 未分配聊天 | 待确认 |
| 时区 | PST/EST (待确认) |
| 24 小时响应率 | 待确认 |
| 满意率 | 待确认 |
| 今日会话 | 待确认 |
| 查看详情 | → 统计页面 |

### 2.2 Left Filter Panel (⏳ 待复核)
| Filter | Expected Options | Expected Default |
|--------|-----------------|------------------|
| Agent filter | Me / All / Select specific | ⏳ 需确认 |
| Status | All, Urgent, Expired, etc. | ⏳ 需确认 |
| Category | All, After-sales, Shipping, Pre-sales | ⏳ 需确认 |

### 2.3 Conversation List (⏳ 待复核)
- Expected tabs: Assigned / Unassigned
- Search: 待确认文案
- Per item: 待确认字段

---

## 3. How to View ALL Agents (⏳ 待复核)

**Expected steps:**
1. Find agent filter dropdown
2. Select "All" / "全选"
3. Change status from default to "All"

**Expected pitfalls:**
- Default may show only own conversations
- Status filter default may not be "All"

---

## 4. Analytics Page (⏳ 待复核)

### Expected URL
```
https://seller.tiktokshopglobalselling.com/chat/compass/service-analytics/chat-trend?shop_region=US
```

### Expected Metrics (⏳ 待复核)
- 满意度 / Satisfaction
- 24h响应率 / 24h Response Rate
- 转化率 / Conversion Rate
- 评价数 / Number of ratings

---

## 5. US vs JP 对比

| Item | JP (Confirmed) | US (To Verify) |
|------|---------------|----------------|
| Entry icon | 耳机/Headset | ⏳ |
| URL pattern | /chat?shop_region=JP | ⏳ |
| Agent filter default | 我 (Me) | ⏳ |
| Status filter default | 紧急 (Urgent) | ⏳ |
| Category options | 全部/售后/物流/售前 | ⏳ |
| Customer tags | 常客/近期客户/现有粉丝/潜在客户 | ⏳ |
| Analytics URL | /chat/compass/... | ⏳ |

---

## 6. 需要美国站复核的事项

请用 profile="kosbling" 执行以下验证：
1. [ ] 入口路径是否相同
2. [ ] 默认筛选器状态
3. [ ] 所有筛选器文案
4. [ ] 统计页面指标
5. [ ] 客户标签类型

---

## 7. Guardrails (US Specific)

### ✅ Safe Operations
- 浏览会话列表
- 查看会话详情
- 查看统计数据
- 使用筛选器搜索

### ❌ Forbidden
- 回复买家消息
- 发送消息
- 创建/修改工单
- 指派会话
- 修改标签
- 使用自动化工具

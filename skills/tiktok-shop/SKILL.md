---
name: tiktok-shop
description: Operate TikTok Shop seller center via browser. Use when user asks to check store dashboard, GMV, orders, analytics, customer service messages, product management, or any TikTok Shop backend operation. Supports multi-region stores (US, JP, UK, etc.) with separate browser profiles per store.
---

# TikTok Shop Seller Center Operations

## Version
- Version: 2026-03-10
- Last verified: 2026-03-10
- Status: active

## Prerequisites

- A browser profile logged into TikTok Shop seller center for each store
- One profile per store (TikTok binds sessions to region; wrong profile → auto-redirect)
- Store credentials if re-login needed (check workspace TOOLS.md or secrets/ for encrypted credentials)

## Entry Points

| Region | URL |
|--------|-----|
| 🇯🇵 Japan | `https://seller-jp.tiktok.com` |
| 🇺🇸 US | `https://seller-us.tiktok.com` |
| 🇬🇧 UK | `https://seller-uk.tiktok.com` |
| Cross-border | `https://seller.tiktokglobalshop.com` |

## Terminology

Treat these as different things:

- **`LIVE & video analytics`** = the analytics module under `Analytics`, reached at `/compass/live-analysis`
- **`Live Dashboard`** = the live-room dashboard for an ongoing session, typically entered from an ongoing-live card or a dedicated `LIVE dashboard` button

Do not collapse these terms.
If a task asks for analytics tables, metric configuration, traffic-source breakdown, historical live-session rows, or summary KPIs, go to **`LIVE & video analytics`** first.
If a task asks for the actual live-room dashboard during an ongoing stream, open **`Live Dashboard`** from the relevant live-session entry point.

## Login Readiness

Before any dashboard/menu/data task, first confirm the profile is already logged in.

If you see login, captcha, SMS, or human verification:
- Treat it as a login blocker, not a normal navigation problem
- Stop early and report the blocker
- Ask for human intervention when needed
- If phone login is used, first confirm whether the country/region code is selected from a dropdown; use the correct code for that site/account instead of guessing
- After human verification is completed, resume the unfinished task from the current logged-in state instead of redoing the whole exploration from scratch

Do not spend the task budget exploring alternate login flows unless the user explicitly asked for a login task.

⚠️ `seller.tiktokglobalselling.com` is **expired/parked** — do NOT use it.

These regional URLs auto-redirect to `seller.tiktokshopglobalselling.com?shop_region=XX` after login.

If not logged in, authenticate with phone + password. May require captcha + SMS code.

Phone region code may be a dropdown/select control instead of a free-text input. For JP/US/other regional seller centers, choose the correct region code shown by the login UI for that account. Do not guess the code.

When the region code control is a selector:
1. Click the region-code area on the left side of the phone field (for example `JP +81`)
2. Wait for the country/region list to open
3. Select the correct country/region code from the list
4. Confirm the phone field now shows the selected code before typing the phone number

**After page loads, verify store name in top-right to confirm correct region.**

## Page Layout

### Top Navigation Bar (right side, left → right)

```
[Help/学習センター] [Customer Service 🎧] [Messages ✉️] [Profile 👤]
```

- **Help**: Learning center, help docs
- **Customer Service**: Buyer-seller live chat system (**opens NEW tab** — see below)
- **Messages**: Platform notifications / announcements (not buyer chat)
- **Profile**: Account settings, store switcher

### Left Sidebar

Many left-sidebar menus expand on **hover**. Do not assume a direct click or guessed URL is enough.

Common top-level areas include Home, Products, Orders, LIVE & video, Analytics, Account Health, Compliance, and Finance, but labels and permissions may vary by region/account.

For concrete menu maps and currently observed submenu structures, read the reference files instead of hard-coding assumptions from this SKILL.md.

## Core Operations

### 1. Dashboard Data Pull

1. Navigate to Home page
2. Capture today's snapshot: GMV, orders, visitors, pending items
3. Switch time range (7d / 30d) for trend data
4. Key metrics:

**`LIVE & video analytics` recognition notes:**
- In `Analytics → LIVE & video analytics`, the traffic-source area may include an **`Impressions`** column. Treat this as an exposure-related metric. If only shares/distribution are visible and not an absolute count, report it as a **partial / substitute exposure metric**, not “missing”.
- In `Analytics → LIVE & video analytics`, trend charts may render as **Canvas**. If the chart is visibly present but text values are not extractable, report **“chart exists but point values were not extracted”** — do not say the trend chart is missing.

| Category | Metrics |
|----------|---------|
| Revenue | GMV (total), GMV by channel (LIVE / Product Card / Videos) |
| Orders | Order count, SKU count, items sold |
| Customers | Customer count, AOV (average order value) |
| Traffic | Visitors, page views |
| Operations | Pending shipment, pending returns, low stock count |
| Health | Store health score, product rating |

### 1A. Live Room Dashboard Monitoring

Use this path only when the task is to monitor a currently ongoing live room from inside the room dashboard.

1. Open `Analytics → LIVE & video analytics`
2. Find `Ongoing LIVE streams`
3. Identify the active account card
4. Click `LIVE dashboard`
5. Monitor the room-level dashboard at a URL like `/workbench/live/overview?room_id=...`

For this monitoring workflow:
- Treat outer Seller Center analytics as **entry discovery only**
- Treat the room-level `Live Dashboard` as the **formal monitoring surface**
- Prefer 1-2 minute polling loops for current viewers, GMV, GMV/hour, items sold, comment rate, follow rate, and warning states
- If the task needs detailed rules, event framing, or output structure, read `references/live-room-dashboard-monitoring-2026-03-10.md`

### 2. Customer Service Center (客服中心)

**⚠️ This is the buyer-seller chat system. NOT the Messages/notification inbox.**

Location: Top nav bar → icon **between Help and Messages** (headphone/chat icon)

**Critical: clicking opens a NEW browser tab.** You must switch to it:

```
1. Click the Customer Service icon
2. browser(action="tabs", profile="<profile>")           → list all tabs
3. Find the new tab (URL contains /chat/)
4. browser(action="focus", profile="<profile>", targetId="<new_tab_id>")
5. browser(action="snapshot", profile="<profile>", targetId="<new_tab_id>")
```

The CS page URL pattern: `https://seller.tiktokshopglobalselling.com/chat?shop_region=XX`

The CS page shows:
- Agent role assignment
- Today's session count (⚠️ shows only YOUR count, not team total)
- 24h response rate & satisfaction rate (⚠️ main page shows "-", check Analytics for actual values)
- Conversation list with last messages

#### 🔴 Critical: Default View Shows Only YOUR Conversations

**⚠️ Default filter shows only YOUR conversations. To see ALL:**

1. Find the "客服消息" (CS Messages) filter — default is "我" (Me)
2. Click the dropdown arrow next to it
3. Click "全选" (Select All) to see conversations from ALL customer service agents
4. Also set status filter to "全部" (All) instead of default "紧急" (Urgent)
5. This is critical — otherwise you'll miss messages handled by other agents

#### 📊 Key Metrics Locations

| Data Needed | Where to Find |
|-------------|----------------|
| Team workload (all agents) | Main CS page → Select All agents |
| Response rate | Click "查看详情" → 聊天概览 tab |
| Satisfaction rate | Click "查看详情" → 聊天概览 tab |
| Backlog (unreplied) | Status filter → 未回复 |
| Urgent chats | Status filter → 紧急 |
| Unassigned chats | Tab → 未分配 |
| Per-agent stats | Click "查看详情" → 全部聊天 → filter by 客服专员 |

#### 📖 Reference Files

For detailed, region-specific CS system documentation, see:
- **JP:** `references/jp-customer-service-system-2026-03-09.md`
- **US:** `references/us-customer-service-system-2026-03-09.md` (needs verification)
- **General:** `references/customer-service-system-2026-03-09.md`

#### ⚠️ Guardrails

- ❌ Never reply to buyer messages — observe only
- ❌ Never send messages or create tickets
- ❌ Never assign conversations or modify tags
- ❌ Never use automation tools
- ✅ Only browse, view, search, and read analytics

### 3. Product Management

Left sidebar → usually enter from Products. Prefer hover first if the sidebar supports flyout submenus. Use the reference files for current submenu names.

### 4. Order Management

Left sidebar → usually enter from Orders. Prefer hover first if the sidebar supports flyout submenus. Use the reference files for current submenu names.

### 5. Analytics Deep Dive

Left sidebar → usually enter from Analytics. Prefer menu entry over guessed URLs; direct URL guessing may return 404.

### 6. Store Health (PEAKS Framework)

Left sidebar → Account Health. TikTok's PEAKS framework:
- **P**remium Products — inventory, listing quality, reviews, brand auth
- **E**ngaging Content — video/live performance metrics
- **A**ctive Selling — listing frequency, promotion participation
- **K**ey Service — response rate, shipment speed, return handling
- **S**atisfaction — ratings, complaints, violations

Each metric shows: your value, benchmark, status (Issue / High-impact / Platform-endorsed / Exceeds)

## Multi-Store Operations

When managing multiple regional stores:
1. Each store MUST use its own dedicated browser profile
2. Never reuse a profile across stores — TikTok cookies bind to one region
3. Verify store name/region after every page load
4. Currency differs by region ($ for US, ¥/円 for JP, £ for UK) — never mix in reports

## Report Output

Write reports to workspace memory: `memory/YYYY-MM-DD-tiktok-{region}-{topic}.md`

Standard format:
```markdown
# TikTok Shop {Region} — {Topic}
**Date:** YYYY-MM-DD
**Store:** {Store Name}

## Today's Snapshot
| Metric | Value | vs Yesterday |
|--------|-------|-------------|
| GMV | ... | ... |
...

## 7-Day Summary
...

## Action Items
### 🔴 Urgent (24h)
### 🟡 This Week
### 🟢 Long-term
```

## Common Pitfalls

| Pitfall | Solution |
|---------|----------|
| Wrong store loaded | Verify store name in top-right after page load |
| Customer Service opens new tab | Use `browser tabs` → `browser focus` to switch |
| Session expired | Check for login redirect; do a login check first |
| Captcha / SMS / human verification | Human intervention required | Stop and report blocker |
| Data shows 0 early in day | TikTok updates data with delay; note the data refresh timestamp |
| Redirected to wrong region | Wrong browser profile; switch to correct one |
| `tiktokglobalselling.com` shows GoDaddy | Domain expired; use `seller-{region}.tiktok.com` instead |
| `seller.tiktokshop.com` connection error | Wrong domain; use `seller-{region}.tiktok.com` |

## References

Use reference files as the changeable layer. Read the smallest relevant one instead of loading everything.

### Reference Guide

| If the task is about... | Read this file first | Role / status |
|---|---|---|
| Store/profile mapping, entry URL, credential file, environment setup | `references/kosbling-config.md` | Core Kosbling environment reference |
| US seller center menu structure and navigation discovery | `references/us-seller-center-menu-map-2026-03-09.md` | US navigation map |
| US "I need metric X, where do I check it?" | `references/us-what-to-check-where-2026-03-09.md` | US task-routing cheat sheet |
| `LIVE & video analytics` metrics, configurable columns, and analytics entry rules | `references/live-dashboard-metrics-2026-03-10.md` | Core LIVE analytics reference |
| Ongoing live-room monitoring from inside the room dashboard | `references/live-room-dashboard-monitoring-2026-03-10.md` | Core room-monitoring reference |
| Customer service system basics that are likely reusable across regions | `references/customer-service-system-2026-03-09.md` | General CS reference, derived from observed flows |
| Japan customer service page structure and filters | `references/jp-customer-service-system-2026-03-09.md` | JP-specific CS reference |
| United States customer service page structure | `references/us-customer-service-system-2026-03-09.md` | US-specific CS draft; verify live before relying on details |

### Selection Rules

- For **environment / profile choice**, start with `kosbling-config.md`.
- For **navigation / menu discovery**, start with the region menu map.
- For **`LIVE & video analytics` tasks**, start with `live-dashboard-metrics-2026-03-10.md`.
- For **ongoing live-room monitoring inside the room dashboard**, start with `live-room-dashboard-monitoring-2026-03-10.md`.
- For **customer service tasks**, read the general CS reference first, then the region-specific file if the task is JP or US.
- Treat files marked **draft / needs verification** as hints, not ground truth.
- Keep task-specific reporting rules in workspace task docs, not in this skill, unless they generalize across TikTok Shop work.

## Human Verification Recovery

When a task is blocked by captcha, SMS, or manual verification:
1. Stop and report the blocker clearly
2. Wait for human completion
3. Then continue the unfinished task from the current state

For one-shot browser sub-tasks, prefer spawning a fresh follow-up task after human completion. Use `sessions_send` only when the original browser worker is intentionally persistent and still active.

## Guardrails

- ❌ Never reply to buyer messages without explicit user permission — observe only
- ❌ Never modify product listings without explicit instruction
- ❌ Never cancel or modify orders
- ❌ Never change store settings or account configuration

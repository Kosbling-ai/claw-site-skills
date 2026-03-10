# LIVE & Video Analytics Metrics Reference (2026-03-10)

Terminology correction:
- This file is about **`Analytics → LIVE & video analytics`** (`/compass/live-analysis`)
- It is **not** the same thing as **`Live Dashboard`** for an ongoing live room

Use this reference when a TikTok Shop task depends on `LIVE & video analytics`, especially when the operator needs to know which metrics can be configured directly in that analytics module and which cannot.

## 1. Correct entry

- Use `Analytics → LIVE & video analytics`
- Canonical path: `/compass/live-analysis`
- Do not guess `/live...` paths; they may show `No Permission` even when the analytics page itself is accessible

## 2. Two useful surfaces

### Performance
Use for account-level summary metrics and ongoing-live overview.

Stable observations:
- Has a `Metrics` control for a small set of core KPIs
- Supports account selection
- Supports date selection
- Has a `Trends` toggle
- Shows traffic-source distribution / ratios, not full raw exposure totals

### Details
Use for per-live-session table analysis.

Stable observations:
- Has a richer `Metrics` control than Performance
- Better place to expose session-level engagement columns needed for reporting
- Suitable for reviewing historical live-session rows

## 3. Metric mapping for common reporting needs

| Reporting need | Dashboard metric / surface | Notes |
|---|---|---|
| Exposure | `Views` on Details | Prefer this over traffic-source ratios when the task wants a count-like exposure metric |
| Viewer level / viewer history by session | `Viewers` on Details | Session-level metric, not a full time-series chart export |
| Current online viewers | `Ongoing LIVE streams` on Performance | Treat as current status, not as “viewer trend/change” |
| Room-entry / click-through style metric | `CTR` | Already available in dashboard metrics |
| Conversion after click | `CTOR` | Already available in dashboard metrics |
| Watch duration / retention proxy | `Avg. viewing duration` on Details | Enable via `Metrics` if not visible |
| Comment interaction | `Comments` on Details | Enable via `Metrics` if not visible |
| GMV | `GMV` | Available on Performance and Details |
| GPM | Not available | Report as unavailable if the task is restricted to `LIVE & video analytics` |

## 4. Important constraints

- `Traffic Source` is useful for distribution analysis, but it shows ratios / percentages rather than a full raw exposure total
- `Current viewers` is a real-time snapshot and must not be mislabeled as viewer trend / viewer change
- Details is richer than Performance for configurable columns, but it is row-based historical live data, not a fully extractable trend workspace
- If a metric is absent from the available `Metrics` selections, do not invent a workaround and present it as first-party dashboard support

## 5. Recommended operating pattern

1. Enter `Analytics → LIVE & video analytics`
2. Decide whether the task needs summary view (`Performance`) or session detail (`Details`)
3. Use the page’s `Metrics` control before concluding a metric is missing
4. Distinguish between:
   - directly available metric
   - substitute / partial metric
   - unavailable metric
5. If the task is constrained to `LIVE & video analytics` only, keep that as a task rule rather than a universal TikTok Shop skill rule

## 6. Stable takeaways worth reusing

- `Details` is the stronger surface for configurable LIVE-session metrics
- `Performance` is the faster surface for account-level summary and current ongoing-live context
- `Views`, `Viewers`, `Avg. viewing duration`, and `Comments` may need to be enabled via `Metrics`
- `GPM` should be treated as unsupported in `LIVE & video analytics` unless TikTok later adds it
- Path choice matters: use `/compass/live-analysis` for analytics, not guessed `/live` routes

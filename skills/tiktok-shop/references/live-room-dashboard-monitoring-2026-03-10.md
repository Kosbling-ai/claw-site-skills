# Live Room Dashboard Monitoring Reference (2026-03-10)

Use this reference when the task is to monitor an ongoing TikTok Shop live room from inside the room’s `Live Dashboard`, rather than to inspect outer Seller Center analytics.

## 1. Terminology

- **`LIVE & video analytics`** = outer analytics module under `Analytics`; use it only to find active live rooms and enter them
- **`Live Dashboard`** = the room-level dashboard for one ongoing live session; this is the actual monitoring surface

Do not collapse these terms.

## 2. Entry path

Typical path:
1. Open `Analytics → LIVE & video analytics`
2. Find `Ongoing LIVE streams`
3. Identify the account card that is currently live
4. Click `LIVE dashboard`
5. Enter a URL like `/workbench/live/overview?room_id=...`

If no account is live, stop and report that there is no room to monitor.

## 3. Monitoring boundary

For this task:
- Use outer Seller Center pages only as entry discovery
- Treat the room-level `Live Dashboard` as the only formal monitoring surface
- Do not substitute outer analytics summaries for room observations

## 4. Primary fields worth polling

Prefer these fields for 1-2 minute monitoring loops:
- `Current viewers`
- `GMV`
- `GMV per hour`
- `Items sold`
- `Impressions`
- `Views`
- `Show GPM`
- `Avg. viewing duration`
- `Comment rate`
- `Follow rate`

Useful supporting modules:
- `Performance trends`
- `Traffic source`
- real-time comment stream
- warning / alert area (for example `Low LIVE traffic`)
- product list

## 5. Monitoring cadence

- Default poll interval: every 1-2 minutes
- The page may not auto-refresh reliably; assume explicit refresh / re-check is needed
- Trend charts may be aggregated on a coarser interval (for example 5 minutes); distinguish snapshot values from aggregated trend values

## 6. Event framing

### Good events
Examples:
- viewers rising
- GMV increasing steadily
- GMV per hour improving
- comment rate rising / staying strong
- follow rate rising
- items sold increasing
- warning disappears / no warning present

### Bad events
Examples:
- viewers drop sharply
- GMV stalls for multiple checks
- GMV per hour declines
- comment rate very low
- follow rate very low
- `Low LIVE traffic` or similar warning appears
- comments show confusion, complaints, or repeated objections

### Abnormal events
Examples:
- live ends suddenly
- key modules disappear
- metrics reset unexpectedly
- stream rhythm changes sharply, suggesting host change or incident

## 7. Output pattern for each polling step

Record at least:
- timestamp
- account / room identifier
- live status
- current key metrics
- changes vs previous polling step
- good / bad / abnormal event flags
- short note

## 8. Audio / ASR boundary

Current observations confirm that the Seller Center `Live Dashboard` has a **right-side video player**, and the observed state was **muted by default**.

However:
- the presence of a player does **not** yet prove reliable audio capture availability
- treat Seller Center audio capture as **unconfirmed** until a live-session check explicitly proves audio can be used

If future work needs recording + speech recognition, still plan a separate TikTok consumer-side capture path as the default assumption.
For now, use visible comments and metric changes as the available event signals.

## 9. Current open questions

- A right-side player exists and was observed muted by default
- A `custom metrics / edit metrics / metrics picker` entry was **not found in the checked run**, but this is not a final exclusion because the live ended and the page jumped away during verification
- Re-check metric customization during a stable ongoing live before concluding the feature does not exist

## 10. Blocking conditions

Stop and report when you hit:
- login expiry
- captcha / human verification
- no permission for room dashboard
- missing `LIVE dashboard` entry button
- blank page / missing modules
- no ongoing live room to enter

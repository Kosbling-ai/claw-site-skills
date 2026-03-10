# claw-site-skills

Community-maintained **OpenClaw site skills** for navigating real websites more reliably.

This repo is for practical, reusable skills that teach OpenClaw how to operate mainstream sites and web apps through browser automation: where to enter, how the UI is structured, what the common blockers are, and what not to touch.

## Goal

Make it easier for contributors to share battle-tested website operation skills so OpenClaw can work better across real-world surfaces like seller centers, dashboards, support inboxes, admin panels, and analytics tools.

## What belongs here

A good site skill usually includes:

- a focused `SKILL.md`
- small reference files for volatile UI details
- navigation rules and entry points
- blocker handling (login, captcha, SMS, redirects, permissions)
- guardrails for risky actions
- region/account differences when relevant

## Current skills

| Skill | Scope |
|---|---|
| `skills/tiktok-shop` | TikTok Shop seller center operations, analytics entry points, customer service center discovery, live dashboard monitoring |

## Suggested layout

```text
skills/
  <site-name>/
    SKILL.md
    references/
      *.md
```

## Contribution rules

- Keep the main `SKILL.md` stable and reusable
- Put fast-changing page details into `references/`
- Prefer concrete observed behavior over guessed URLs
- Clearly mark anything unverified as draft / needs verification
- Include guardrails for destructive or high-risk surfaces
- Keep one skill focused on one site or one closely related product surface

See `CONTRIBUTING.md` for contribution guidance.

## Why this repo exists

Website operation knowledge changes constantly. A shared repo makes it easier for the community to keep improving how OpenClaw reaches and uses mainstream sites without hard-coding brittle behavior into one giant prompt.

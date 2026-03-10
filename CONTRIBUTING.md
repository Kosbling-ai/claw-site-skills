# Contributing to claw-site-skills

Thanks for contributing.

## What to add

Please add reusable knowledge that helps OpenClaw operate a website more reliably, for example:

- entry URLs
- menu paths
- tab-switching behavior
- login readiness checks
- known redirects
- region/store/account differences
- safe read-only workflows
- common blockers and recovery steps

## What not to add

- raw secrets, cookies, tokens, passwords, phone numbers, or API keys
- one-off notes that only make sense in a single private workspace
- destructive automation without explicit safety guardrails
- vague advice like “click around until you find it”

## Structure

```text
skills/<site-name>/SKILL.md
skills/<site-name>/references/*.md
```

## Writing guidance

- Write for future operators, not just today’s task
- Keep `SKILL.md` concise and durable
- Move volatile UI details into `references/`
- State when something is confirmed vs inferred vs draft
- Prefer smallest-necessary references over giant dumps

## Pull requests

A good PR should explain:

1. what site or surface this skill improves
2. what workflows are now supported
3. what was directly observed
4. any safety boundaries contributors should keep

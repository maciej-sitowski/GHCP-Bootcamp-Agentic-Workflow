---
name: Weekly Report Status
description: Publish a concise report of repository activity from the previous seven days.
engine: copilot
on:
  schedule:
    - cron: "0 9 * * 1"
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
strict: true
tools:
  github:
    mode: gh-proxy
    toolsets: [default]
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

# Weekly Report Status

Create one new GitHub issue containing a concise activity report for the last
seven full days ending at the workflow start time in UTC.

Review repository activity in these categories:

- commits
- issues opened or updated
- pull requests opened, merged, or updated

For each category, include a short summary and useful links when available.
State the reporting window explicitly. If there was no activity in any
category, clearly state that no repository activity occurred during the
reporting window; still publish the issue.

Use these report sections:

### Summary

Give a one- or two-sentence overview of the period.

### Commits

Summarize the commits from the reporting window, or state that there were none.

### Issues

Summarize issues opened or updated during the reporting window, or state that
there were none.

### Pull Requests

Summarize pull requests opened, merged, or updated during the reporting window,
or state that there were none.

Do not invent activity or metadata. Keep the report concise and do not create
more than one issue.
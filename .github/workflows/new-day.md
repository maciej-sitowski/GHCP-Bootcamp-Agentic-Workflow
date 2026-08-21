---
name: New Day
description: Add the current UTC date and a confirmation dialog to the Daily Updates navigation.
engine: copilot
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
strict: true
tools:
  edit: true
safe-outputs:
  create-pull-request:
    max: 1
    allowed-files:
      - "index.html"
---

# New Day

Use the workflow run's current UTC date, obtained with `date -u +%Y-%m-%d`.
Update `index.html` to record that daily update.

Follow the existing Daily Updates HTML structure, ID conventions, date wording,
and styling exactly:

- Add one navigation control to the existing Daily Updates navigation.
- Add one matching accessible `<dialog>` for that date.
- The navigation control must use the existing `daily-update-trigger` class,
  `aria-haspopup="dialog"`, `aria-controls`, and `data-dialog-trigger`
  attributes.
- The dialog must use the existing `daily-update-dialog` structure with matching
  date-based IDs for `id`, `aria-labelledby`, and `aria-describedby`.
- The dialog should clearly confirm that the daily update ran for that UTC date.
- Match the existing wording style, including the ordinal date format such as
  `1st of August`, and preserve the existing HTML entities and formatting style.

Before editing, inspect `index.html` for the UTC date. If that date is already
present in a navigation control or dialog, make no change and do not create a
pull request. Never duplicate a date, navigation control, or dialog. Preserve
every existing daily update. Do not modify `styles.css` or any other file.

When a change is needed, edit only `index.html` and create one pull request
describing the added daily update.
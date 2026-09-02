---
name: demo-playwright-python-skill
description: Use when asked to run, explain, or extend the demo-playwright-python locator-strategy walkthrough, or to build a similar Playwright demo against a different site.
---

# Demo Playwright Python Skill

This repo teaches five Playwright locator strategies and four form interactions against the public page https://testingexamples.github.io.

Locator strategies: by id (`#id-example-1`), by name attribute (`[name="name-example-1"]`), by class (`.class-example-1`), by link text (`page.locator('a', has_text='Link Example 1')`), and by XPath (`xpath=//input[@type="submit"]`).

Form interactions: fill a text input (`#text-example-1-id` with `"hello"`), check a checkbox (`#checkbox-example-1-id`), check a radio button (`#radio-example-1-option-1-id`), and select an option in a `<select>` (`#select-example-1-id`, by index 0).

Each step prints the located element's outer HTML (and, for the select, the resulting value) — this is a walkthrough that demonstrates locators, not a test suite with assertions.

## Running it

Install Python and Playwright per README.md (`pip install playwright && playwright install chromium`), then run `python src/demo.py` (or `./src/demo.py`). A visible (non-headless) Chromium window opens, walks the page, and closes. There is also a stubbed-out `demo_async()` for an async-API variant, not currently wired up.

## Adapting it to a different site or selectors

1. Update the target URL passed to `page.goto(...)`.
2. Update each locator string to match the new page's real ids/classes/attributes/link text/XPath.
3. Update the values used in `.fill(...)`, `.check()`, and `.select_option(...)` to match the new form's real inputs.
4. Update `spec/index.md` to describe the new scenario verbatim, in the same change — not after.

This skill summarizes the repo. `AGENTS.md` and `spec/index.md` are the source of truth — if this skill's summary ever disagrees with those, they win.

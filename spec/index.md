# Spec

## Summary

This spec describes the exact browser-automation walkthrough that `src/demo.py` performs: launching Chromium with Playwright, navigating to the public testing-examples site, exercising five locator strategies, and performing four form interactions, logging the result of each step instead of asserting it.

## Scope

This spec covers the scenario implemented in `src/demo.py`: the target URL, every locator/selector it uses, and every form interaction it performs, together with what "this demo still works" means.

This spec does NOT cover: how to install Python/Playwright/mypy or how to invoke the script (see README.md), CI or build tooling, browsers other than Chromium, the commented-out `demo_async()` alternative, or test-framework assertions — this script is a walkthrough, not a test suite.

## Principles and rules

- This is a walkthrough script, not a test suite: it demonstrates locator strategies and form interactions by logging what it finds, and it does not assert expected outcomes with a test framework.
- The code and this spec describe the same scenario. If they ever diverge, that is a defect — fix it before making any other change.

## Detail

Target URL: `https://testingexamples.github.io`

Locator strategies demonstrated, in order:

1. By id — `page.locator('#id-example-1')` — locates an element by its `id` attribute. Prints the element's outer HTML.
2. By name attribute — `page.locator('[name="name-example-1"]')` — locates an element by an attribute selector on `name`. Prints the element's outer HTML.
3. By class name — `page.locator('.class-example-1')` — locates an element by CSS class selector. Prints the element's outer HTML.
4. By link text — `page.locator('a', has_text='Link Example 1')` — locates a link (`<a>`) by its visible text `Link Example 1`. Prints the element's outer HTML.
5. By XPath — `page.locator('xpath=//input[@type="submit"]')` — locates an element with an XPath expression. Prints the element's outer HTML.

Form interactions performed, in order:

1. Text input — `page.locator('#text-example-1-id')` — prints outer HTML, then fills it with the value `"hello"` via `.fill("hello")`.
2. Checkbox — `page.locator('#checkbox-example-1-id')` — prints outer HTML, then checks it via `.check()`.
3. Radio button — `page.locator('#radio-example-1-option-1-id')` — prints outer HTML, then checks it via `.check()`.
4. Select — `page.locator('#select-example-1-id')` — prints outer HTML, then selects the option at index `0` via `.select_option(index=0)`, prints the resulting value from `.input_value()`, and prints the outer HTML of the now-selected option via `select_element.locator('option:checked')`.

## Acceptance criteria

- The script navigates to `https://testingexamples.github.io` without error.
- Each of the five locators above resolves to exactly one element on the live page (no timeout or strict-mode-violation error from Playwright).
- The text input accepts the fill value `"hello"`, the checkbox and radio button end up checked, and the select ends up with the option at index 0 selected.
- The script exits with status code 0 and no unhandled exception.

## Related topics

- [../README.md](../README.md)
- [../AGENTS.md](../AGENTS.md)

## Sources

- [https://testingexamples.github.io](https://testingexamples.github.io)

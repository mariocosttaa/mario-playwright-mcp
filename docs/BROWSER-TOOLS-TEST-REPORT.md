# Browser Tools Test Report

**Date:** 2026-03-05  
**MCP:** mario-playwright-mcp v1.1.0  
**Test flow:** example.com → iana.org (click) → back → httpbin.org/get

---

## Tools tested

| Tool | Status | Notes |
|------|--------|-------|
| `browser_navigate` | ✅ Pass | Navigates correctly, returns snapshot |
| `browser_snapshot` | ✅ Pass | Accessibility tree with refs for actions |
| `browser_take_screenshot` | ✅ Pass | Full-page PNG saved to `.mcp-output/` |
| `browser_click` | ✅ Pass | Click by ref (e6 "Learn more") → iana.org |
| `browser_navigate_back` | ✅ Pass | Returns to example.com |
| `browser_tabs` | ✅ Pass | Lists tabs with URL and current flag |
| `browser_console_messages` | ✅ Pass | Captures errors (e.g. favicon 404) |
| `browser_network_requests` | ✅ Pass | Lists requests; `includeStatic` works |
| `browser_evaluate` | ✅ Pass | Runs JS (e.g. `document.title`) |
| `browser_press_key` | ✅ Pass | Key press (End) |
| `browser_resize` | ✅ Pass | Viewport 1280×720 |
| `browser_wait_for` | ✅ Pass | Waits for text "httpbin" |

---

## Analysis

### Core navigation & interaction
- Navigation, snapshot, click, and back work as expected.
- Snapshots provide stable refs (`e2`, `e3`, `e6`) for `browser_click` and `browser_type`.
- Output includes page URL, title, and console error count.

### Mario enhancements
- **Network requests:** Basic listing works (`[GET] url => [200]`).
- **Output organization:** Screenshots and console logs go to `.mcp-output/` (no repo root pollution).
- **Console logs:** Linked in snapshot events (e.g. `console-*.log#L1`).

### Not exercised in this run
- `browser_type`, `browser_fill_form`, `browser_select_option` (no forms on test pages)
- `browser_drag`, `browser_hover`, `browser_file_upload`, `browser_handle_dialog`
- `browser_network_requests` with `includePayloads: true` + `url` filter (API page) — needs follow-up

### Recommendations
1. Run a test with an API page (e.g. POST to httpbin) to validate `includePayloads` and sensitive redaction.
2. Add a test page with forms to verify `browser_type` and `browser_fill_form`.
3. Keep `.mcp-output/` in `.gitignore` so generated files stay out of the repo.

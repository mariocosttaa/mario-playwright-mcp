# Updating from upstream

To pull changes from Microsoft Playwright MCP:

```bash
cd mario-playwright-mcp
git remote add upstream https://github.com/microsoft/playwright-mcp.git   # if not already added
git fetch upstream
git merge upstream/main   # or rebase, as preferred
npm install
```

If Playwright version changes, the patch may fail. Run:

```bash
# Edit node_modules/playwright/lib/mcp/browser/tools/network.js with our changes, then:
npx patch-package playwright
```

---
description: Run Playwright integration tests for RealmOfAgents via MCP
mode: agent
model: default
tools:
  - run_playwright_test
---

Call MCP tool `run_playwright_test` with:
```
{
  "test_path": "src/QualityMCP/tests_playwright/integration",
  "repo_path": "c:/Development/ASISaga/Website/realmofagents.asisaga.com",
  "subdomain": "realmofagents"
}
```

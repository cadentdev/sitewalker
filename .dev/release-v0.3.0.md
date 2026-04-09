# Release Checklist: v0.3.0

**Started:** 2026-04-09 | **Project:** sitewalker

## Current Step: COMPLETE

| Step | Status | Notes |
|------|--------|-------|
| Pre-flight | [x] | 3 features inventoried, target v0.3.0 |
| 1. Security Audit | [x] | 14 findings (1 CRITICAL, 4 HIGH, 4 MED, 3 LOW, 2 INFO) |
| 2. Triage Findings | [x] | 2 blockers, rest filed as #6-9 |
| 3. Fix Blockers | [x] | Empty title crash + dynamic user-agent |
| --- GATE: Security | [x] | PASS — both blockers resolved |
| 4. Test Coverage | [x] | 51 tests, 96% coverage |
| --- GATE: Quality | [x] | PASS |
| 5. Dependency Audit | [x] | bandit clean, deps current |
| 6. Documentation Final Pass | [x] | README + CLI help verified |
| 7. Version Bump | [x] | 0.2.1 → 0.3.0 |
| 8. Release Notes | [x] | RELEASE-NOTES.md created |
| 9. PR Creation/Update | [x] | PR #5 updated |
| 10. Issue Triage | [x] | #1-4 closeable, #6-9 stay open |
| 11. Merge & Verify | [x] | Merged to main |
| --- GATE: CI | [!] | No CI configured |
| 12. Tag & GitHub Release | [x] | v0.3.0 tagged and released |
| 13. Post-Release | [x] | PyPI published, LinkedIn draft created |
| 14. Branch Cleanup | [x] | feature/csv-output-fixes pruned |
| 15. Retrospective | [x] | See below |

## Features Included

- CSV output fixes (issues #3, #4) — save both files with -e, Unix line endings
- BFS crawl algorithm (issue #1) — replaces DFS, correct depth tracking
- External link status checking (issue #2) — new --check-external flag

## Findings

- CRITICAL: Empty `<title>` tag crash → fixed
- HIGH: Dynamic user-agent version → fixed
- Should-fix: Filed as issues #6-9 (external link limits, queue bounds, rate limiting, filename safety)

## Retrospective

### What went well
- Stacking 3 FeatureDev cycles on one branch was the right call — avoided cherry-pick complexity
- Security audit caught a real crash (empty title) that would have hit in production
- TDD caught the BFS test design challenge early — first test didn't expose the DFS bug, rethinking the test scenario led to a proper regression test
- Dynamic user-agent version via importlib.metadata is cleaner than hardcoding

### What could improve
- **pip-audit not installed** — should be in dev dependencies for the dependency audit step
- **No CI** — quality gate had to be manual. Adding GitHub Actions would automate this
- **PR edit via `gh pr edit` broken** — GraphQL Projects Classic deprecation error. Had to use `gh api` directly

### Lessons for next time
- The DFS→BFS test design insight: flat nav structures don't expose the DFS bug. You need **cross-links** where DFS visits a page via a deep path, preventing its children from being explored at the correct depth
- `csv.writer` `lineterminator='\n'` is the correct fix for Unix line endings, not `newline='\n'` on the file open

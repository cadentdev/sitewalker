# Release Checklist: v0.3.1

**Started:** 2026-04-09 | **Project:** sitewalker

## Current Step: COMPLETE

| Step | Status | Notes |
|------|--------|-------|
| Pre-flight | [x] | 2 features, target v0.3.1 |
| 1. Security Audit | [x] | 0 findings — minimal code changes |
| 2. Triage Findings | [x] | Nothing to triage |
| 3. Fix Blockers | [x] | None needed |
| --- GATE: Security | [x] | PASS |
| 4. Test Coverage | [x] | 51 tests, 96% coverage |
| --- GATE: Quality | [x] | PASS |
| 5. Dependency Audit | [x] | bandit clean, only new dep is bandit itself (dev) |
| 6. Documentation Final Pass | [x] | Added --delay to README options table |
| 7. Version Bump | [x] | 0.3.0 → 0.3.1 |
| 8. Release Notes | [x] | RELEASE-NOTES.md updated |
| 9. PR Creation/Update | [x] | PR #13 |
| 10. Issue Triage | [x] | #6-9 stay open (future work) |
| 11. Merge & Verify | [x] | CI green on 3.9 + 3.12 |
| --- GATE: CI | [x] | PASS |
| 12. Tag & GitHub Release | [x] | v0.3.1 tagged and released |
| 13. Post-Release | [x] | PyPI published, social media skipped (patch) |
| 14. Branch Cleanup | [x] | 3 branches pruned |
| 15. Retrospective | [x] | See below |

## Retrospective

### What went well
- Fastest FeatureRelease yet — small changes, no blockers, CI verified everything
- CI gate worked as intended — first release where CI was a real gate, not skipped
- The --delay flag immediately proved its value: 3305 pages in 10 min vs 83 min

### What could improve
- README was missing the --delay flag after FeatureDev — caught in Step 6. FeatureDev Phase 8 should have updated the README options table.

### Process note
- Patch releases with CI + no blockers can flow through the pipeline very quickly. The FeatureRelease workflow scales well from heavy (v0.3.0, 3 features + security fixes) to light (v0.3.1, 2 small changes).

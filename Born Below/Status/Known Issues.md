---
type: status
domain: project
status: living
tags:
  - status
  - bugs
  - issues
---
# Known Issues

Current bugs, limitations, and technical debt in Born Below.

## Active Bugs

### High Priority

*No critical bugs currently tracked.*

### Medium Priority

| Issue | Area | Notes |
|-------|------|-------|
| Beat spam possible in edge cases | Mission | Grace rules may miss multi-zone jumps |
| Cult meter display sync | UI | Occasional stale values in modal |

### Low Priority

| Issue | Area | Notes |
|-------|------|-------|
| Memory leak in long sessions | Performance | Minor, affects 2+ hour sessions |
| Tooltip positioning edge cases | UI | Near screen edges |

---

## Technical Debt

### Code Quality

| Area | Issue | Priority |
|------|-------|----------|
| Type annotations | Some services lack full typing | Medium |
| Test coverage | Integration tests for cult system | Medium |
| Documentation | Inline comments sparse in some services | Low |

### Architecture

| Area | Issue | Priority |
|------|-------|----------|
| Event pack loading | Could benefit from lazy loading | Low |
| UI state management | Some direct manager access | Low |

---

## Known Limitations

### By Design

| Limitation | Reason |
|------------|--------|
| One activity per demon per week | Core design constraint |
| Single save slot | Demo scope |
| Fixed target roster | Demo scope |

### Technical

| Limitation | Reason |
|------------|--------|
| Web export limitations | Godot 4.x web constraints |
| Large save files | JSON serialization overhead |

---

## Recently Fixed

| Issue | Fixed In | Notes |
|-------|----------|-------|
| Activity log missing entries | Dec 2024 | Added demon commentary |
| Intervention risk logging | Dec 2024 | Mission execution logging |
| Cult leverage bonus | Dec 2024 | Support mission integration |

---

## Reporting Issues

When encountering bugs:

1. Check if it's a known issue above
2. Note reproduction steps
3. Include relevant game state:
   - Week number
   - Active missions
   - Demon assignments
   - Recent actions

## Related

- [[Roadmap]] - Planned fixes
- [[Development/Testing Guide]] - Running tests

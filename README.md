# Contribution 1: Reporting/Bug — Fixtures for 2025 should not include "Apr-Dec production data" field

**Contribution Number:** 1  
**Student:** Sushant Aryal  
**Issue:** [bcgov/cas-registration #4633](https://github.com/bcgov/cas-registration/issues/4633)  
**Status:** Phase I Complete

---

## Why I Chose This Issue

I chose this issue because it is a well-scoped, clearly diagnosed bug that fits comfortably within the program's 3–4 week timeline. The maintainers have already done a lot of the analysis in the comments: a contributor identified that the dev fixtures still seed `production_data_apr_dec` data for the 2025 reporting year, even though that field only applies to the 2024 reporting year (Apr 1 – Dec 31, 2024). Because the field exists in the fixture-seeded submitted report but not in a supplementary draft, the diff on the Review Changes page incorrectly flags it as "DELETED." That kind of self-contained, data/fixture-level fix with a known root cause is exactly the kind of bounded problem the issue selection checklist points toward.

It also matches my skills and learning goals. The fix lives in test/seed fixtures rather than deep application logic, so I can ramp up on the bcgov reporting codebase without needing expertise in every part of the system. The issue is labeled **Good First Issue**, has helpful maintainer context and reproduction steps, and is part of an active, well-maintained government project — so I get a realistic open-source contribution experience while learning how reporting fixtures, supplementary reports, and the Review Changes diff fit together.

---

## Understanding the Issue

### Problem Description

The development fixtures for the 2025 reporting year incorrectly include `production_data_apr_dec` ("Apr-Dec production data") values. This field is only meaningful for the 2024 reporting year (covering Apr 1 – Dec 31, 2024) and should not exist on 2025 reports at all.

### Expected Behavior

When a user creates a supplementary report for a 2025 report and reviews changes, the Review Changes page should only show deltas for fields the user actually modified. Production data fields that were never touched should not appear as changed.

### Current Behavior

The Review Changes page displays an unexpected "DELETED" delta for `production_data_apr_dec` even when the user only modified an unrelated field (e.g., Cement equivalent annual production). The fixture-seeded submitted report contains `production_data_apr_dec` data, but the supplementary draft does not, so the diff correctly flags it as deleted — surfacing a difference the user never made.

### Affected Components

- The 2025 reporting-year **dev/seed fixtures** that populate production data (these incorrectly include `production_data_apr_dec`).
- Indirectly, the **Review Changes / supplementary report diff** view, where the bad fixture data manifests as a spurious delta. Note: per maintainer comments, this does **not** affect real users — a genuine 2025 submitted report will never contain `production_data_apr_dec` data; the problem is isolated to the seeded fixtures.

---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]

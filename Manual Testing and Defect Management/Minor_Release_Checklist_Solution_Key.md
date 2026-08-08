# Minor Release Checklist — Solution Key

**MindBridge Education Portal | Regression - Minor Release v2.5.1**

**Audience:** Self-assessment reference for learners who curated a 10-case minor-release regression cycle in Zephyr. Compare your selected Test IDs and rationale against this key.

---

## About This Solution Key

This document provides the rationalized set of 10 test cases recommended for the Minor Release v2.5.1 regression cycle. It is intended for learner self-assessment only and should not be used as a substitute for independent risk-based analysis.

If your selections differ, review the Rationale column to understand the risk-based reasoning behind each recommended case.

---

## Release Notes Summary — v2.5.1

| Changed Area | Nature of Change |
| ----- | ----- |
| Authentication Module | Password validation logic updated: minimum 12 characters, at least one special character required |
| Course Search Module | Search indexing service refactored to improve response time for queries with more than three keywords |
| No changes | Enrollment, Payment, Dashboard, Reporting |

---

## Recommended Test Case Selections

| # | Test ID | Area | Title | Rationale |
| ----- | ----- | ----- | ----- | ----- |
| 1 | TC-001 | Authentication | Valid Login (standard) | Core smoke path; login must always be verified regardless of what changed. The authentication module was directly modified (login validation consistency fix). |
| 2 | TC-002 | Authentication | Login - New Password Validation (12+ chars, special char) | Directly tests the updated password validation rule from the v2.5.1 release notes. Highest-risk authentication case in this release. |
| 3 | TC-003 | Authentication | Login - Rejection of Password Below 12 Characters | Validates that the new minimum character rule correctly rejects non-compliant passwords. |
| 4 | TC-004 | Authentication | Login - Rejection of Password Without Special Character | Validates that the special character enforcement rule works as expected. |
| 5 | TC-005 | Authentication | Logout - Session Termination | Session management is connected to authentication logic; password validation changes can affect session state behavior. |
| 6 | TC-006 | Course Catalogue & Search | Basic Search - Single Keyword Query | Establishes a baseline for search functionality after the indexing refactor. |
| 7 | TC-007 | Course Catalogue & Search | Advanced Search - Query With More Than Three Keywords | Directly targets the refactored indexing service optimized for multi-keyword queries (multi-keyword timeout fix and performance enhancement). |
| 8 | TC-008 | Course Catalogue & Search | Search - No Results for Unrecognized Query | Validates that the refactored indexing service handles edge cases and empty result sets correctly. |
| 9 | TC-009 | Course Catalogue & Search | Search Results - Correct Course for Exact Title Match | Confirms that result accuracy was not degraded by the indexing refactor. |
| 10 | TC-010 | Authentication | Password Reset Flow - End to End | Password reset depends on the same validation logic updated in v2.5.1; a regression here could block users from recovering access. |

---

## Selection Summary

| Area | Cases Selected | Reason |
| ----- | ----- | ----- |
| Authentication | 6 | Directly modified module—highest risk area in this release |
| Course Catalogue & Search | 4 | Directly modified module—refactor introduces regression risk |
| Core critical path (login/logout) | Included within Authentication selections above | Always verify core paths regardless of scope |
| Enrollment & Cart | 0 | No changes made; no indirect dependency identified |
| Checkout & Payment | 0 | No changes made; no indirect dependency identified |
| Dashboard | 0 | No changes made; no indirect dependency identified |
| Profile & Account | 0 | No changes made; no indirect dependency identified |
| Admin | 0 | No changes made; no indirect dependency identified |

---

## Acceptable Variation

Learner selections do not need to match this key exactly. An acceptable submission meets these criteria:

- At least 5 of the 6 Authentication test cases selected match the recommended cases.
- At least 3 of the 4 Course Catalogue & Search test cases selected match the recommended cases.
- No more than 1 test case was selected from Enrollment, Checkout, Dashboard, Profile, or Admin without a documented rationale tied to release risk.
- Written rationale demonstrates risk-based reasoning rather than random or alphabetical selection.

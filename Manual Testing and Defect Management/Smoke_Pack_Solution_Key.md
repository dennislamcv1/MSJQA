# Smoke Pack Solution Key

**MindBridge Education Portal | Build Smoke Test—MindBridge Portal**

**Build:** sc5_smoke_pack | **Application URL:** http://localhost:3000

**Audience:** Self-assessment reference for learners who completed the 10-case smoke pack in Zephyr. Compare your logged Pass/Fail results and notes against this key.

---

## Execution Results

| Test ID | Title | Brief Steps | Expected Result | Status |
| ----- | ----- | ----- | ----- | ----- |
| TC-001 | Application Load: Portal Home Page | Open the browser. Navigate to the MindBridge Portal home URL. Observe the landing page. | Portal home page loads without error; primary navigation and main content are visible. | Pass |
| TC-002 | User Login: Valid Credentials | Navigate to the login page. Enter a valid registered email and password. Select Sign in. | User is authenticated and redirected to the user dashboard. | Pass |
| TC-003 | User Login: Invalid Password Rejection | Navigate to the login page. Enter a valid email and an incorrect password. Select Sign in. | Login is rejected; an error message is displayed and the user is not granted access to the dashboard. | Pass |
| TC-004 | Navigation: Home to Course Catalog | From the portal home page, select the navigation link to the course catalog. | Course catalog page loads and displays available courses. | Pass |
| TC-005 | Course Search: Single Keyword Query Returns Results | Open course search. Enter a single keyword (for example, "Testing"). Execute the search. | Search results page loads and displays at least one matching course. | Pass |
| TC-006 | Course Detail Page: Page Loads Without Error | From the catalog or search results, select a course to open its detail page. | Course detail page loads without error; course title, description, and enrollment action are visible. | Pass |
| TC-007 | Add Course to List: Confirmation Message Displays | From a course detail page, select the control to add the course to the enrollment list or cart. | A confirmation message displays indicating the course was added successfully. | Pass |
| TC-008 | User Dashboard: Loads With Correct User Data | Sign in with a user who has enrollments and payment history. Navigate to the user dashboard. Review the greeting, Recent activity section, and Grades (enrolled-courses) section. | Dashboard displays the correct user greeting, Recent activity entries (enrolment and payment records), and a populated enrolled-courses list in the Grades section. | Fail |
| TC-009 | Navigation: Return to Home From Dashboard | From the user dashboard, select navigation to return to the portal home page. | Home page loads successfully without error. | Pass |
| TC-010 | User Logout: Session Ends | Select Log out in the page header. Observe the result. Attach screenshot evidence in Zephyr. | Session ends and the user returns to an unauthenticated state; the header again shows Log in and Register. | Pass |

---

## TC-008 Failure Detail (Actual Result)

Dashboard greeting and Recent activity (enrolment and payment entries) rendered correctly. The Grades section (enrolled-courses list) rendered blank, showed "0 courses," and displayed the empty-state text "You have not received any grades yet."

---

## Summary

**9 passed, 1 failed.** TC-008 (User Dashboard: Loads With Correct User Data) is the only failure. All other smoke cases passed. The build is not stable enough for deeper quality assurance (QA) work until the dashboard course-list defect is resolved.

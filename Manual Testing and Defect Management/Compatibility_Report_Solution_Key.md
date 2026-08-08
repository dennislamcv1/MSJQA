# Compatibility Report — Solution Key (Gold Standard)

**Audience:** Self-assessment reference for learners who ran the cross-browser / device emulation lab on MindBridge. Compare your report against this model. Your wording will differ — what matters is that the **conditions, control result, and technical observation** are accurate.

---

## 1. Environments tested

| # | Browser (version) | Emulated device | Viewport (W × H) | Auth state | Result |
|---|---|---|---|---|---|
| 1 | Microsoft Edge (Chromium) | None (desktop) | ~1280 × 800 | Logged in (admin) | **Pass** |
| 2 | Microsoft Edge (Chromium) | iPhone SE | 375 × 667 | Logged in (admin) | **Fail** |
| 3 | Microsoft Edge (Chromium) | iPhone SE | 375 × 667 | Logged out | **Pass** |

The matrix isolates two variables — **viewport width** and **auth state**. The only failing combination is **small viewport + logged in**, which pinpoints the defect.

---

## 2. Defect detail

| Field | Entry |
|---|---|
| **Defect title** | Primary navigation menu is unclickable on logged-in screens below 400px |
| **Area / component** | Primary navigation (global header) |
| **Browser + emulation** | Microsoft Edge (Chromium), DevTools device emulation, iPhone SE preset (375 × 667) |
| **Trigger conditions** | Viewer is **logged in** AND viewport width is **below 400px** |
| **Steps to reproduce** | 1. Log in as `admin@mindbridge.local` / `admin12345`. 2. Open DevTools (F12) and toggle device emulation (Ctrl+Shift+M). 3. Select iPhone SE (375 × 667). 4. Attempt to select any header nav item (Dashboard, Practice, Catalogue, My learning, Account, cart, Log out). |
| **Expected result** | Each navigation item is tappable and navigates to its page, as it does at desktop width. |
| **Actual result** | The navigation menu is dimmed (faded) and no item responds to a tap/click. The page does not navigate. |
| **Works at desktop width?** | **Yes** — at ~1280px the same menu items are fully clickable. |
| **Severity** | **High** — logged-in mobile users cannot navigate anywhere from the header; the core menu is completely blocked on phone-class screens. |
| **Evidence** | Screenshot of the faded, unresponsive nav at 375px while logged in; DevTools Computed panel showing `pointer-events: none` on the nav. |

---

## 3. Technical observation (DevTools)

With the `<nav data-testid="primary-nav">` element selected in **Elements**, the **Computed** panel shows:

- **`pointer-events: none`** at the 375px viewport — this is what makes every menu item ignore clicks and taps.
- The menu is also rendered at reduced **opacity** (~30%), which is why it looks greyed out.

Both styles are applied through a width breakpoint that only activates **below 400px**. When the viewport is widened back to desktop size, `pointer-events` returns to **`auto`** and the menu works again. The styles are applied only while the viewer is authenticated, which is why the logged-out check at 375px passes.

Crucially, the **MindBridge** title link sits **outside** the `<nav>` element, so it keeps working at 375px — proving the page is responsive and only the navigation menu is affected.

---

## 4. Summary and recommendation

On phone-class viewports (below 400px), logged-in MindBridge users cannot use the primary navigation: its pointer events are suppressed and the menu is dimmed. Desktop and logged-out states are unaffected. This is a **High-severity** mobile blocker.

**Recommendation:** remove the rule that drops `pointer-events` (and opacity) on the authenticated navigation below 400px, then add a small-viewport regression check (manual or automated) that confirms the menu is interactive at 375px while logged in.

---

## What makes this report strong

| Element | Why it matters |
|---|---|
| **Control result** (desktop pass) | Shows the menu is not broken everywhere, narrowing the cause to a breakpoint. |
| **Two isolated variables** | The matrix proves the failure needs *both* small width *and* logged-in state. |
| **Exact reproduction conditions** | A developer can recreate the bug immediately at 375px while logged in. |
| **Technical observation** | Names the actual cause (`pointer-events: none`), not just the symptom. |
| **Emulation stated honestly** | Documents DevTools emulation rather than implying a physical-device or cloud result. |

## Acceptable variation

Your report does not need to match this wording. An acceptable submission:

- Reproduces the defect at a viewport **below 400px** (iPhone SE class) while **logged in**.
- Records a **desktop control** that passes.
- Notes that the **logged-out** state at the same small width is unaffected (or, at minimum, ties the defect to the logged-in state).
- Identifies the cause as the navigation's **suppressed pointer events** (menu also dimmed).
- States the method as **browser DevTools emulation**, not a cloud device farm.

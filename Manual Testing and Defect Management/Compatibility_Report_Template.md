# Cross-Browser / Device Compatibility Report — MindBridge

Fill in each section from your own DevTools device-emulation session. Use this report to communicate exactly how, where, and under what conditions the defect appears.

**Tester name / role:** ___________________________
**Date:** ___________________________
**Application URL:** `http://localhost:3000`
**Test method:** Browser DevTools device emulation (no physical device, no cloud device farm)

---

## 1. Environments tested

Record every environment you checked, including the desktop control.

| # | Browser (version) | Emulated device | Viewport (W × H) | Auth state | Result (Pass / Fail) |
|---|---|---|---|---|---|
| 1 | Edge (Chromium) ______ | None (desktop) | ~1280 × ______ | Logged in (admin) | |
| 2 | Edge (Chromium) ______ | iPhone SE | 375 × 667 | Logged in (admin) | |
| 3 | (optional) ______ | iPhone SE | 375 × 667 | Logged out | |

---

## 2. Defect detail

| Field | Your entry |
|---|---|
| **Defect title** | |
| **Area / component** | |
| **Browser + emulation** | |
| **Trigger conditions** (auth state + viewport) | |
| **Steps to reproduce** | |
| **Expected result** | |
| **Actual result** | |
| **Works at desktop width?** (Yes / No) | |
| **Severity** (High / Medium / Low) | |
| **Evidence** (screenshot / file reference) | |

---

## 3. Technical observation (DevTools)

What did the **Elements > Computed** (or **Styles**) panel show for the navigation element at 375px? Name the property and value, and what changed when you returned to desktop width.

_Your notes:_

---

## 4. Summary and recommendation

One or two sentences: who is affected, how badly, and what you recommend the team do.

_Your notes:_

---

## Self-check before you submit

- [ ] I recorded a **desktop control** result, not just the failing case.
- [ ] My trigger conditions name both the **viewport width** and the **logged-in** state.
- [ ] My steps let someone else reproduce the defect without asking me questions.
- [ ] I named the technical observation (the `pointer-events` value at 375px).
- [ ] My environment says **DevTools emulation**, not a cloud device farm.
- [ ] I attached or referenced a screenshot of the defect at 375px.

# Accessibility Solution Key — Lab 2: Accessibility and Usability Summary

**Application:** MindBridge (`http://localhost:3000`)  
**Audit tool:** Microsoft Edge DevTools  
**Lab build:** Two seeded Web Content Accessibility Guidelines (WCAG) violations (`D-WCAG-ALT`, `D-WCAG-CONTRAST`)

Use this key after your audit to compare your documented findings against the confirmed violations and example usability improvements.

---

## Violation 1: D-WCAG-ALT — Missing alternative text on course thumbnails

| Field | Detail |
|---|---|
| **Defect ID** | D-WCAG-ALT |
| **Element** | The primary course image — the Course Detail hero image (data-testid: `course-hero`) — and the course thumbnails on the Home and Catalogue pages (data-testid: `course-thumb`) |
| **WCAG Success Criterion** | 1.1.1 Non-text Content — Level A |
| **Inspection method** | Microsoft Edge DevTools → Elements panel → select the course thumbnail image and review attributes; optionally review the Accessibility tree |

### Expected behavior

Every meaningful course thumbnail image includes a descriptive `alt` attribute (for example, `Cover image for [course title]`) so assistive technologies can convey the image purpose to users who cannot see it.

### Actual (buggy) behavior

Course thumbnail images on Home, Catalogue, and CourseDetail render without an `alt` attribute, failing WCAG image-alternative requirements.

### Impact

Screen reader users hear the image announced as unlabeled or generic content. They cannot determine which course the thumbnail represents, creating a barrier to browsing and selecting courses independently.

---

## Violation 2: D-WCAG-CONTRAST — Low contrast on the main call-to-action button

| Field | Detail |
|---|---|
| **Defect ID** | D-WCAG-CONTRAST |
| **Element** | The main call-to-action button **"Browse courses"** in the Home page hero (data-testid: `hero-cta`). The same low-contrast tone also affects the featured course card metadata on Home (data-testid: `featured-meta`, with `featured-instructor` and `featured-price`) — a secondary instance. |
| **WCAG Success Criterion** | 1.4.3 Contrast (Minimum) — Level AA |
| **Inspection method** | Microsoft Edge DevTools → Issues panel (contrast failure flag) or Elements panel → Styles panel → select the button label's text color swatch to view the measured contrast ratio |

### Expected behavior

The button label text renders in a colour that meets WCAG 2.1 Level AA contrast requirements — a minimum contrast ratio of **4.5:1** against the button background for normal text (3:1 for large text).

### Actual (buggy) behavior

The "Browse courses" button label renders in a low-contrast tone (indigo text on the indigo button) that fails WCAG AA. The featured course card metadata (instructor name and price) renders in the same failing low-contrast tone.

### Measured vs required contrast

| Measurement | Value |
|---|---|
| **Measured ratio (Microsoft Edge DevTools)** | Below 2:1 |
| **Required minimum (normal text, Level AA)** | 4.5:1 |
| **Result** | Fails — measured ratio is well below the 4.5:1 threshold for normal-sized text |

### Impact

Users with low vision, colour perception differences, or anyone viewing the page in bright ambient light may be unable to read the primary call-to-action, blocking the main path into the catalogue. The same failure hides the featured course's instructor and price.

---

## Violation summary table

| Defect ID | Element | WCAG criterion | Level | Key evidence |
|---|---|---|---|---|
| D-WCAG-ALT | Primary course image — Course Detail hero (`course-hero`) — and Home/Catalogue thumbnails (`course-thumb`) | 1.1.1 Non-text Content | A | `alt` attribute absent on these images |
| D-WCAG-CONTRAST | Main call-to-action button "Browse courses" on Home (`hero-cta`); featured card metadata (`featured-meta`) as a secondary instance | 1.4.3 Contrast (Minimum) | AA | Measured ratio below 2:1; required 4.5:1 for normal text |

---

## Example usability improvements (not WCAG violations)

These are friction points a tester might observe during inspection. They are distinct from the two WCAG failures above and illustrate the kind of actionable usability feedback expected in the lab summary.

### Example 1: Registration wizard step indicator clarity

**Issue:** The three-step registration wizard (Email → Password → Profile) shows step numbers but does not indicate which fields are required versus optional until the user reaches Step 3.

**Recommendation:** Add a brief note on Step 1 stating that all three steps are required to create an account, and mark optional fields consistently on Step 3 so users know what they can skip.

### Example 2: Registration error messaging on server failure

**Issue:** When registration fails due to a server error, the message displayed on Step 3 is generic and does not guide the user toward a recovery action (for example, whether to retry, use a different email, or contact support).

**Recommendation:** Replace the generic failure message with context-specific guidance. For duplicate-email conflicts, display "This email is already registered — sign in instead." For unexpected server errors, display "Something went wrong — please wait a moment and try again."

---

## Example accessibility and usability summary (within the 150–200 word target)

Use this as a model for the summary deliverable. Yours may differ in wording, but
it should cover the same header, both violations (with criterion, level, and
impact), and one usability proposal.

> This audit of the MindBridge Home page (`http://localhost:3000`), performed with
> Microsoft Edge DevTools, found two WCAG violations and one usability improvement.
> **Violation 1:** the course thumbnail images render with no `alt` attribute,
> failing **WCAG 1.1.1 Non-text Content (Level A)**. Screen reader users hear the
> images announced as unlabeled content and cannot tell which course each thumbnail
> represents, so they cannot browse independently. **Violation 2:** the main
> "Browse courses" call-to-action in the hero uses indigo label text on an indigo
> background, measuring a contrast ratio below 2:1 against the required 4.5:1 for
> normal text — failing **WCAG 1.4.3 Contrast (Minimum) (Level AA)**. Low-vision
> users, or anyone reading in bright light, may be unable to read the primary path
> into the catalogue; the same tone also hides the featured card's instructor and
> price. **Usability improvement:** the three-step registration wizard never states
> upfront that all three steps are required or which Step 3 fields are optional;
> adding that note on Step 1 would reduce confusion and drop-off.

---

## Self-evaluation checklist

After comparing your audit summary against this key, confirm:

- [ ] Violation 1 identifies the primary course image (and thumbnails) and cites WCAG Success Criterion 1.1.1 (Level A).
- [ ] Violation 2 identifies the main call-to-action button and cites WCAG Success Criterion 1.4.3 (Level AA).
- [ ] Violation 2 includes the measured contrast ratio and the required 4.5:1 minimum for normal text.
- [ ] Your usability improvement proposal is specific, actionable, and not a restatement of the two WCAG violations.
- [ ] Your written summary is **150–200 words** and includes a header, both WCAG violations (criterion, level, impact), and one usability proposal.
- [ ] All inspection steps reference Microsoft Edge DevTools panels only.

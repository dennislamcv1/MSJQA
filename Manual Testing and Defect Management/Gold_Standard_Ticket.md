# Gold Standard Ticket

**MindBridge Education | Model completed defect ticket**

This is a model of the bug ticket you should produce from `Defect_Brief.md`. Use it to self-compare **after** you file your own ticket in Jira. Your wording does not need to match word-for-word — what matters is that every section is present, specific, and unambiguous.

---

## Issue Type

Bug

## Summary

Checkout — "Place order" returns a 404 Not Found on Microsoft Edge instead of the order confirmation page

> A good summary names the **action** (selecting Place order), the **location** (checkout), and the **outcome** (404 instead of confirmation). It is specific enough to search for later.

## Description

**Environment**

- **Browser:** Microsoft Edge 124
- **Operating System:** Windows 11
- **URL:** `http://localhost:3000/checkout`
- **Account:** Standard learner account with one course in the cart
- **Payment:** Mock card `4242 4242 4242 4242` (pre-filled on the checkout page)

**Steps to reproduce**

1. Sign in as a learner and add any course to the cart.
2. Open the cart and select **Checkout**.
3. On the checkout page, confirm the payment fields (Card number, Expiry, CVV) are populated with the pre-filled mock card.
4. Select **Place order**.

**Expected result**

The order confirmation page loads, the payment is recorded, and the course appears in **My Learning**.

**Actual result**

The page fails and displays a **"404 Not Found"** error. No confirmation page is shown, no enrolment is created, and the course does not appear in My Learning.

**Notes**

- Reproduced **3 times in a row** on Edge 124 / Windows 11 (consistent, not intermittent).
- A teammate ran the identical steps on **Google Chrome** and the confirmation page loaded normally, so the failure appears **Edge-specific**. Using a different browser is a temporary workaround.

## Severity

**Critical (S2)** — the checkout failure blocks the core purchase-and-enrol workflow, but a workaround exists (complete the purchase on another browser), so it is not a Blocker that stops every user.

## Priority

**High** — checkout directly affects enrolment and revenue, so the fix should be scheduled for the current or very next release.

## Attachment

`checkout_404_edge.png` *(placeholder)* — an annotated screenshot of the 404 page captured during the session, with the error and the browser version highlighted.

---

## Self-check: does your ticket do all of this?

- [ ] Summary names the action, the location, and the outcome.
- [ ] Environment lists browser, OS, and the page URL.
- [ ] Steps to reproduce are numbered and specific enough for anyone to follow.
- [ ] Expected and Actual results are stated separately so the conflict is obvious.
- [ ] Severity and Priority are both set, with a one-line reason for each.
- [ ] An evidence file is attached (a dummy screenshot is fine for this lab).

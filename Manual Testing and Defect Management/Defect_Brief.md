# Defect Brief — Raw Tester Notes

**MindBridge Education | Course checkout issue**

These are the unedited notes you jotted down during a test session. They contain everything you observed, but they are **not** yet organised into a bug ticket. Your job in this lab is to turn these raw notes into one clean, complete Jira Bug. Do not file the notes as-is — a developer should never have to dig through scratch notes.

---

## What I was doing

Smoke-testing the new MindBridge build before release. Working through the course-purchase flow — picking a course, adding it to the cart, and paying to enrol. I was using **Microsoft Edge** (version 124) on a **Windows 11** laptop.

## What happened

Got to the checkout page fine. The payment fields were all there — card number, expiry, CVV. The mock card `4242 4242 4242 4242` was pre-filled. I clicked the **Place order** button at the bottom expecting to land on the order confirmation / "You're enrolled" page.

Instead the whole page died — it showed a **"404 Not Found"** error page. No confirmation, no enrolment created, and the course did not show up in My Learning afterward. So the learner basically can't complete the purchase.

The checkout page I was on was `http://localhost:3000/checkout`.

## Extra details I remember

- Tried it **three times in a row** — same 404 every time, so it is not a one-off glitch.
- A teammate tried the exact same steps on **Google Chrome** and it worked fine for them — confirmation page loaded, enrolment created. So it looks **Edge-specific**.
- I grabbed a screenshot of the 404 page but have not attached it anywhere yet.
- This feels serious because it stops people from paying / enrolling, but there is a workaround (use a different browser), so it is probably not the absolute top "nothing works for anyone" level.

## My rough guess at impact

Blocks the core purchase path for anyone on Edge. Revenue / enrolment impact. Needs to be looked at soon. Not sure exactly what label MindBridge uses for severity vs priority — need to set those properly in the ticket.

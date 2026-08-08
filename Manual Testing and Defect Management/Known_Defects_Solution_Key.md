# Known Defects Solution Key — Lab 1: Exploratory Charter (Registration Flow)

**Application:** MindBridge (`http://localhost:3000`)  
**Charter:** "Spend 15 minutes exploring the new MindBridge Registration Flow with a focus on input validation and state changes."  
**Lab build:** Three seeded registration defects (`D-REG-DUPLICATE`, `D-REG-BACK-LOSS`, `D-REG-WHITESPACE`)

Use this key after your 15-minute session to compare your findings against the confirmed defects.

---

## Defect 1: D-REG-DUPLICATE

| Field | Detail |
|---|---|
| **Defect name** | D-REG-DUPLICATE — Duplicate registration submission |
| **Heuristic** | Rapid Input |
| **Severity** | High |

### Reproduction steps

1. Open MindBridge at `http://localhost:3000` and navigate to the Registration flow (`/register`).
2. Complete Step 1 (Email) and Step 2 (Password) with valid values.
3. On Step 3 (Profile), enter a valid name and select **Create account** to finish the first registration.
4. Sign out if you are redirected while still authenticated, then start a new registration with the **same email address** used in step 3.
5. Complete all three steps again and select **Create account** on Step 3.

**Alternate Rapid Input path:** On Step 3, select **Create account** multiple times in rapid succession before the first request completes. Observe whether duplicate submissions are prevented or allowed through.

### Expected behavior

Before a new account is inserted, the server runs a duplicate-email pre-check. If the email is already registered, the application returns a clean conflict response (HTTP 409 with an `email_taken` error code) so the user understands the address is unavailable.

### Actual (buggy) behavior

Registration accepts duplicate submissions: the duplicate-email pre-check is skipped, so a second submit with the same address surfaces a 500 internal server error instead of a clean conflict response.

---

## Defect 2: D-REG-BACK-LOSS

| Field | Detail |
|---|---|
| **Defect name** | D-REG-BACK-LOSS — Password lost on browser history navigation |
| **Heuristic** | Interruption |
| **Severity** | Medium |

### Reproduction steps

1. Open MindBridge at `http://localhost:3000` and navigate to `/register/step/1`.
2. Enter a valid email on Step 1 (Email) and select **Continue**.
3. Enter a valid password on Step 2 (Password) and select **Continue** to reach Step 3 (Profile).
4. Use the browser **Back** button to return to an earlier step in the wizard.
5. Use the browser **Forward** button (or select **Continue** again) to return to Step 2 (Password).
6. Observe whether the password field still contains the value you entered.

### Expected behavior

The registration wizard mirrors entered data (including the password) to session storage and in-memory state. When the user navigates backward and then forward through browser history, previously entered fields—including the password—are retained and re-hydrated.

### Actual (buggy) behavior

The registration wizard drops the password from sessionStorage and from in-memory state on history navigation, so a user who selects Back then Forward finds the password field empty.

---

## Defect 3: D-REG-WHITESPACE

| Field | Detail |
|---|---|
| **Defect name** | D-REG-WHITESPACE — Whitespace-only name accepted |
| **Heuristic** | Boundary/Goldilocks |
| **Severity** | Medium |

### Reproduction steps

1. Open MindBridge at `http://localhost:3000` and navigate to `/register/step/1`.
2. Enter a new, unused email address on Step 1 and select **Continue**.
3. Enter a valid password (at least 8 characters) on Step 2 and select **Continue**.
4. On Step 3 (Profile), enter only spaces in the **Name** field (for example, three spaces: `   `).
5. Select **Create account** and complete registration.
6. Navigate to the Dashboard and observe the welcome greeting.

### Expected behavior

The application trims whitespace from the name field before validation and persistence. A name composed entirely of whitespace fails validation and is rejected with a clear error message; it is not stored or displayed to the user.

### Actual (buggy) behavior

Registration accepts a whitespace-only name: the service-side trim is skipped, so a name like `   ` is treated as valid and persisted verbatim. The dashboard greeting then renders an empty space where the user's name should appear.

---

## Heuristic quick reference

| Heuristic | Defect surfaced |
|---|---|
| Rapid Input | D-REG-DUPLICATE |
| Interruption | D-REG-BACK-LOSS |
| Boundary/Goldilocks | D-REG-WHITESPACE |

---

## Severity framework (reference)

| Level | Definition |
|---|---|
| **High** | Could cause data loss, duplicate records, or a broken user flow |
| **Medium** | Causes unexpected behavior but does not prevent task completion |
| **Low** | Cosmetic or causes minor confusion |

# Release Notes — MindBridge Education Portal v2.5.1

**Release type:** Minor release  
**Target environment:** Staging

---

## Overview

Version 2.5.1 is a focused maintenance release. Changes are limited to the Authentication and Course Search modules. Enrollment, payment, dashboard, profile, and reporting modules were not modified.

---

## Authentication Module

### Bug fix: Login validation consistency

- Corrected inconsistent password validation on the login form so rules match the registration and password-reset flows.
- Updated password validation logic to enforce a minimum of 12 characters and require at least one special character.

### Enhancement: Clearer validation feedback

- Login and registration forms now display specific inline messages when a password fails the updated rules.

---

## Course Search Module

### Bug fix: Multi-keyword search timeout

- Resolved intermittent timeouts when users entered queries with more than three keywords.

### Enhancement: Search indexing performance

- Refactored the search indexing service to improve response time for queries with more than three keywords.

---

## No Changes in This Release

The following areas were not modified in v2.5.1:

- Enrollment and cart
- Checkout and payment
- User dashboard and grades
- Profile and account settings
- Admin and reporting

---

## Regression Guidance

Target regression testing on Authentication and Course Search cases that exercise the updated password rules and the refactored search indexer. Include core login and logout paths to confirm session behavior remains stable after the authentication changes.

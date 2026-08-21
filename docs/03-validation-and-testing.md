# 03 — Validation and Testing

## Overview

The XLSForm was tested throughout development to verify that the form structure, question types, required fields, conditional logic, constraints, calculations, and media references were working as intended.

Testing was performed using the ODK XLSForm validation/preview process.

---

## XLSForm Validation

The completed XLSForm was submitted for ODK validation.

The validation process was used to identify structural and logic errors in the form before finalizing the submission.

### Validation Status

**Final validation result:** `Form is valid`

> Add the final validation screenshot to the `validation/` folder as evidence.

---

## Validation and Functional Tests

### 1. Required Fields

Fields marked with `*` in the original PDF were implemented as required fields.

**Test:**
Leave a required field empty.

**Expected result:**
The form should not allow the user to proceed without completing the required field.

**Result:**
Passed.

---

### 2. Consent Date

The consent section contains a date field.

**Test:**
Enter a date later than the current date.

**Expected result:**
The form should reject the date.

**Constraint:**

```text
. <= today()

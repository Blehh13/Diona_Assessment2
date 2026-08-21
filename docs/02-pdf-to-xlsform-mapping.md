# 02 — PDF to XLSForm Mapping

## Purpose

This document records how the fields and sections in the Criminal Risk Assessment Request PDF were translated into XLSForm questions and form logic.

The PDF was treated as the source for the form's content and structure.

---

## 1. Consent Section

### Consent Information

**PDF element:** Consent for Criminal Risk Assessment and Release of Information

**XLSForm type:** `note`

**Reason:** The consent text is information that needs to be displayed to the user rather than entered as a response.

**Read-only:** Yes

---

### Consent Date

**PDF field:** Date

**XLSForm type:** `date`

**Required:** No

**Constraint:** Date cannot be later than today.

**Reason:** A consent date should not be entered as a future date.

---

### Signature

**PDF field:** Signature of person being assessed

**XLSForm type:** `image`

**Purpose:** Capture the person's signature.

---

### Unconsented / Witness

The consent section contains the unconsented/witness portion of the original form.

This was represented using appropriate selectable/text input fields while maintaining the intent of the original section.

---

# 2. Personal Information

The PDF contains the following personal-information fields.

| PDF Field | XLSForm Type | Reason |
|---|---|---|
| First Name | `text` | Text input |
| Second Name | `text` | Text input |
| Last Name | `text` | Text input |
| Date of Birth | `date` | Date input |
| Sex | `select_one` | One option can be selected |
| Other Last Names Used | `text` | Text input |
| Other First Names Used / Also Goes By | `text` | Text input |
| Current Address | `text` | Address input |
| Current Ph#s | `text` | Phone number input |
| City/Province or Country of Birth | `text` | Text input |

### Date of Birth Validation

The date of birth uses a constraint preventing a future date.

The purpose is to prevent an invalid future DOB without introducing an age restriction that is not specified in the PDF.

### Phone Validation

The current phone field uses phone-format validation appropriate to the implementation.

---

# 3. Identification

The PDF explicitly states that the subject's name must be identified using:

**TWO PIECES OF IDENTIFICATION**

The identification options are represented using a `select_multiple` question because more than one identification document must be selected.

### Identification Options

The choices include:

- Birth Certificate
- Social Insurance Card
- Manitoba Health Card
- Treaty Card
- Other
- MB Driver's License with Photo

### Two-Piece Requirement

A validation constraint requires at least two identification selections.

This directly reflects the two-piece identification requirement in the PDF.

---

## Conditional Identification Fields

### Other ID

The `Other ID` field is conditionally displayed when the user selects `Other`.

**Relevant condition:**

```text
selected(${identification_documents}, 'other')

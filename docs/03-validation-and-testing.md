# 03 — Validation and Testing

## Overview
The XLSForm was tested throughout development to verify the form structure, question types, required fields, conditional logic, constraints, calculations, and media references. Testing was performed using the ODK XLSForm validation and preview process.

## XLSForm Validation
The completed XLSForm was submitted for ODK validation. The validation process was used to identify structural and logic errors in the form before finalizing the submission.

**Validation Status**: 
- Final validation result: **Form is valid**
- A screenshot of the validation result is stored in `validation/xlsform-validation.png`

---

## Functional Testing

### 1. Required Fields
Fields marked with `*` in the original PDF were implemented as required fields.
- **Test**: Leave a required field empty.
- **Expected**: The form should require the field to be completed.
- **Result**: ✅ Passed.

### 2. Consent Date
The consent section contains a date field. A constraint was added to prevent future dates.
- **Constraint logic**: `. <= today()`
- **Test**: Enter a date later than the current date.
- **Expected**: The form should reject the date.
- **Result**: ✅ Passed.

### 3. Date of Birth
The Personal Information section contains a Date of Birth field. A constraint was added to prevent future dates.
- **Constraint logic**: `. <= today()`
- **Test**: Enter a future date.
- **Expected**: The form should reject the date.
- **Result**: ✅ Passed. *(Note: No age restriction was added because the PDF does not specify an age requirement.)*

### 4. Two-Piece Identification
The PDF specifies that the subject's name must be identified using two pieces of identification.
- **Test 1**: Select only one identification document.
- **Expected 1**: The form should reject the response because two pieces are required.
- **Test 2**: Select two or more identification documents.
- **Expected 2**: The identification requirement should be satisfied.
- **Result**: ✅ Passed.

### 5. Other Identification
The Other ID field is conditionally displayed using `relevant` logic.
- **Test 1**: Select *Other* from the identification choices.
- **Expected 1**: The Other ID field should appear.
- **Test 2**: Do not select *Other*.
- **Expected 2**: The Other ID field should remain hidden.
- **Result**: ✅ Passed.

### 6. Driver's Licence
The driver's licence fields are conditionally displayed.
- **Test 1**: Select *MB Driver's License with Photo*.
- **Expected 1**: Driver's licence number field appears, and optional driver's licence photo field appears.
- **Test 2**: Do not select the driver's licence option.
- **Expected 2**: The driver's licence fields remain hidden.
- **Result**: ✅ Passed.

### 7. Last Criminal Risk Assessment Date
The PDF describes this field as *(if known)*, so the field remains optional. A future-date constraint was added.
- **Constraint logic**: `. <= today()`
- **Test 1**: Leave the field blank.
- **Expected 1**: The field can remain blank.
- **Test 2**: Enter a future date.
- **Expected 2**: The form should reject the date.
- **Result**: ✅ Passed.

### 8. Phone Number Validation
Phone-number regex validation was added to the relevant phone fields.
- **Test 1**: Enter an invalid phone number.
- **Expected 1**: The form should reject the value.
- **Test 2**: Enter a valid phone number according to the implemented format.
- **Expected 2**: The form should accept the value.
- **Result**: ✅ Passed.

### 9. Email Validation
Email-format regex validation was added to the required designate email field.
- **Test 1**: Enter an invalid email address.
- **Expected 1**: The form should reject the value.
- **Test 2**: Enter a valid email address.
- **Expected 2**: The form should accept the value.
- **Result**: ✅ Passed.

### 10. Signature
The consent section contains a signature input (`appearance=signature`).
- **Test**: Enter a signature.
- **Expected**: The signature should be captured successfully.
- **Result**: ✅ Passed.

---

## Issues Encountered During Development
Several issues were encountered during the development and validation process, including:
- Missing calculation errors
- Incorrect image parameter placement
- Invalid constraint expressions
- Circular dependencies in calculation/relevance logic
- Image-rendering issues in the preview environment

These issues were investigated and corrected where possible. The specific image-rendering issue is documented separately in `04-image-rendering-issue.md`.

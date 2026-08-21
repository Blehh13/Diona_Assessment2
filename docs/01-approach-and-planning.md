# 01 — Approach and Planning

## Objective

The objective of this assignment was to develop an ODK XLSForm based on the provided Criminal Risk Assessment Request PDF while maintaining the structure and requirements represented in the original form.

## Initial Approach

I first studied the provided PDF and divided it into its major sections rather than attempting to directly reproduce it question by question.

The main sections identified were:

1. Consent for Criminal Risk Assessment and Release of Information
2. Personal Information
3. Identification
4. Name of Person Being Assessed
5. CFS Agency Designate Instructions
6. Agency Request Details
7. Final Disclaimer

The provided `BBCI.xlsx` file was used only as a reference to understand how an XLSForm is structured. In particular, it helped in understanding the purpose of the `survey`, `choices`, and `settings` sheets and the way XLSForm columns are used.

The actual questions and requirements in this implementation were taken from the Criminal Risk Assessment Request PDF.

## Planning the XLSForm

Before entering the questions into the XLSForm, I mapped the different elements of the PDF to appropriate XLSForm types.

The general decision process was:

- Information that only needs to be displayed → `note`
- Text entered by the user → `text`
- Dates → `date`
- A single choice → `select_one`
- Multiple choices → `select_multiple`
- Signature capture → `image` with signature handling
- Automatically generated values → `calculate`
- Related sections → `begin group` / `end group`

I also identified fields that required:

- `required`
- `relevant`
- `constraint`
- `constraint_message`
- `calculation`
- `readonly`
- `appearance`

## Validation Planning

In addition to reproducing the fields from the PDF, I identified logical validations that could be implemented without changing the intended purpose of the form.

These included:

- Preventing future consent dates
- Preventing future dates of birth
- Preventing future previous-assessment dates
- Validating phone numbers
- Validating email addresses
- Requiring two pieces of identification
- Showing identification-specific fields conditionally

The distinction between a field being required and a field having a validation constraint was also considered.

For example, the previous criminal risk assessment date remains optional because the PDF states "(if known)", while a future date is still prevented if a value is entered.

## Development Process

The form was developed incrementally.

The general workflow was:

1. Study the PDF
2. Identify sections and fields
3. Decide the appropriate XLSForm type for each field
4. Define choice lists in the `choices` sheet
5. Organize related questions into groups
6. Add required fields
7. Add conditional logic
8. Add constraints and calculations
9. Add media resources
10. Test and validate the form
11. Document issues encountered during implementation

Detailed field-level mapping is documented in `02-pdf-to-xlsform-mapping.md`.

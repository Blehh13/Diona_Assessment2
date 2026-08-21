# Criminal Risk Assessment Request — ODK XLSForm

## Overview

This repository contains my implementation of an **ODK XLSForm** based on the provided **Criminal Risk Assessment Request** PDF.

The form was developed by mapping the structure, fields, choices, requirements, and conditional behaviour from the source PDF into an ODK-compatible XLSForm.

The provided `BBCI.xlsx` file was used only as a reference for understanding the structure of an XLSForm. The Criminal Risk Assessment Request PDF was used as the source for the actual form content.

---

## Assignment

The assignment required:

> Develop an ODK XLSForm for the attached PDF and ensure the form is developed according to the requirements and structure provided in the PDF.

---

## XLSForm Structure

The main XLSForm is:

`Criminal_Risk_Assessment_Request_XLSForm.xlsx`

It contains the standard XLSForm sheets:

- **survey** — Contains the form questions, groups, conditions, constraints, calculations, and other form logic.
- **choices** — Contains the choice lists used by select-one and select-multiple questions.
- **settings** — Contains the form metadata and configuration.

---

## Main Sections

The form follows the structure of the original PDF:

1. Consent for Criminal Risk Assessment and Release of Information
2. Personal Information
3. Identification
4. Name of Person Being Assessed
5. CFS Agency Designate Instructions
6. Agency Request Details
7. Final Disclaimer

---

## Key XLSForm Features

### Consent

- Consent information displayed as read-only content
- Date field
- Signature capture
- Unconsented/Witness section

### Personal Information

- First name
- Second name
- Last name
- Date of birth
- Sex
- Other names used
- Current address
- Current phone number
- City/Province or Country of birth

### Identification

The PDF specifies that the subject's name must be identified using **two pieces of identification**.

The form therefore uses a `select_multiple` question with a validation requirement for at least two selections.

Available identification options include:

- Birth Certificate
- Social Insurance Card
- Manitoba Health Card
- Treaty Card
- Other
- MB Driver's License with Photo

Conditional fields are used for:

- Other identification details
- Driver's licence number
- Optional driver's licence photo

### Agency Request Details

Includes:

- Agency name
- Reason for risk assessment
- Assigned worker
- Date of last criminal risk assessment
- Submitting designate
- Designate phone number
- Designate email
- Designate fax number
- Request date

---

## Validation and Logic

Additional validation was implemented where appropriate, including:

- Future-date prevention for consent date
- Future-date prevention for date of birth
- Future-date prevention for the last criminal risk assessment date
- Phone-number validation
- Email-format validation
- Required-field validation based on the fields marked with `*` in the PDF
- Minimum two-piece identification requirement
- Conditional display of identification-related fields

The form was tested using ODK XLSForm validation and preview tools.

---

## Media

The `media/` directory contains the image resources used by the form:

```text
media/
├── logo.png
└── drivers_license_reference.jpg

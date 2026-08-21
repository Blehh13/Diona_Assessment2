# Criminal Risk Assessment Request — ODK XLSForm

## Overview

This repository contains my implementation of an **ODK XLSForm** based on the provided **Criminal Risk Assessment Request** PDF.

The form was developed by mapping the structure, fields, choices, requirements, and conditional behaviour from the source PDF into an ODK-compatible XLSForm.

The provided `BBCI.xlsx` file was used only as a reference for understanding the general structure of an XLSForm. The Criminal Risk Assessment Request PDF was used as the source for the actual form content.

---

## Assignment

The assignment required:

> Develop an ODK XLSForm for the attached PDF and ensure the form is developed according to the requirements and structure provided in the PDF.

---

## Repository Structure

```text
Diona_Assessment2/
│
├── README.md
│
├── Criminal Risk Assessment Request.pdf
├── Criminal_Risk_Assessment_Request_XLSForm.xlsx
│
├── xforms/
│   ├── Criminal_Risk_Assessment_Request_XLSForm.xml
│   └── Criminal_Risk_Assessment_Request_XLSForm_PREVIEW_ONLY.xml
│
├── media/
│   ├── logo.png
│   └── drivers_license_reference.jpg
│
├── validation/
│   └── xlsform-validation.png
│
├── docs/
│   ├── 01-approach-and-planning.md
│   ├── 02-pdf-to-xlsform-mapping.md
│   ├── 03-validation-and-testing.md
│   ├── 04-image-rendering-issue.md
│   └── notebook/
│       ├── page-01.jpeg
│       ├── page-02.jpeg
│       ├── page-03.jpeg
│       └── page-04.jpeg
│
└── video/
    └── assignment-demonstration.md
```

---

## XLSForm Structure

The main XLSForm is:

`Criminal_Risk_Assessment_Request_XLSForm.xlsx`

It contains the standard XLSForm sheets:

* **survey** — Contains the form questions, groups, conditions, constraints, calculations, and other form logic.
* **choices** — Contains the choice lists used by `select_one` and `select_multiple` questions.
* **settings** — Contains the form metadata and configuration.

The generated XForm XML files are provided in the `xforms/` directory.

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

* Consent information displayed as read-only content
* Consent date field
* Signature capture
* Unconsented/Witness section
* Future-date validation for the consent date

### Personal Information

* First name
* Second name
* Last name
* Date of birth
* Sex
* Other names used
* Current address
* Current phone number
* City/Province or Country of birth
* Future-date validation for date of birth
* Phone-number validation

### Identification

The PDF specifies that the subject's name must be identified using **two pieces of identification**.

The form therefore uses a `select_multiple` question with a validation requirement for at least two selections.

Available identification options include:

* Birth Certificate
* Social Insurance Card
* Manitoba Health Card
* Treaty Card
* Other
* MB Driver's License with Photo

Conditional fields are used for:

* Other identification details
* Driver's licence number
* Optional driver's licence photo

### Name of Person Being Assessed

The person's name is associated with the information entered in the Personal Information section using calculated/read-only information where appropriate.

### CFS Agency Designate Instructions

The instructional content is presented as read-only information.

### Agency Request Details

Includes:

* Agency name
* Reason for risk assessment
* Assigned worker
* Date of last criminal risk assessment
* Submitting designate
* Designate phone number
* Designate email
* Designate fax number
* Request date

The date of the last criminal risk assessment is optional because the PDF specifies `(if known)`.

### Final Disclaimer

The final disclaimer and instructions are presented as read-only information.

---

## Validation and Logic

Additional validation was implemented where appropriate, including:

* Future-date prevention for consent date
* Future-date prevention for date of birth
* Future-date prevention for the last criminal risk assessment date
* Phone-number validation
* Email-format validation
* Required-field validation based on the fields marked with `*` in the PDF
* Minimum two-piece identification requirement
* Conditional display of identification-related fields
* Conditional display of driver's licence fields
* Conditional display of the `Other ID` field

The form was tested using ODK XLSForm validation and preview tools.

The final validation evidence is available at:

`validation/xlsform-validation.png`

Detailed testing information is documented in:

`docs/03-validation-and-testing.md`

---

## Media

The `media/` directory contains the image resources used by the form:

```text
media/
├── logo.png
└── drivers_license_reference.jpg
```

During development, the images were also tested using externally hosted image resources through FreeImage while troubleshooting the image-rendering behaviour.

The image-rendering issue encountered during preview and the troubleshooting process are documented in:

`docs/04-image-rendering-issue.md`

---

## Documentation

The `docs/` directory contains documentation of the development and troubleshooting process.

### Approach and Planning

`docs/01-approach-and-planning.md`

Documents the initial approach, section identification, XLSForm type selection, validation planning, and development workflow.

### PDF to XLSForm Mapping

`docs/02-pdf-to-xlsform-mapping.md`

Documents how the fields and sections from the PDF were mapped to XLSForm question types, groups, choices, and logic.

### Validation and Testing

`docs/03-validation-and-testing.md`

Documents the validation process, functional testing, constraints, conditional logic, and issues encountered during development.

### Image Rendering Issue

`docs/04-image-rendering-issue.md`

Documents the image-rendering issue encountered during preview, the troubleshooting process, and the resulting behaviour.

### Notebook Documentation

The `docs/notebook/` directory contains photographs of my handwritten planning and reasoning process while converting the PDF into an XLSForm.

---

## Video Demonstration

A link to the assignment demonstration video and an important note regarding its length is included in:

`video/assignment-demonstration.md`

The video demonstrates the completed XLSForm and explains the implementation, decisions, and issues encountered during the assignment.

---

## Files Included

| File / Directory                                | Purpose                                      |
| ----------------------------------------------- | -------------------------------------------- |
| `Criminal_Risk_Assessment_Request_XLSForm.xlsx` | Main XLSForm submission                      |
| `Criminal Risk Assessment Request.pdf`          | Original assignment PDF                      |
| `xforms/`                                       | Generated XForm XML files                    |
| `media/`                                        | Form image resources                         |
| `validation/`                                   | Final validation evidence                    |
| `docs/`                                         | Development and implementation documentation |
| `docs/notebook/`                                | Handwritten planning notes                   |
| `video/`                                        | Assignment demonstration video               |

---

## Final Status

The XLSForm has been developed, validated, and documented based on the provided Criminal Risk Assessment Request PDF.

The repository contains the source XLSForm, generated XForms, media resources, validation evidence, development documentation, notebook planning notes, and the assignment demonstration video.

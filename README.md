# Criminal Risk Assessment Request: Digital XLSForm Transformation

**Client Context:** Manitoba Families | **Project:** Diona Technologies Assignment 2

> A comprehensive digital transcription and logic-enforced implementation of the Manitoba Families *Criminal Risk Assessment Request* using the ODK XLSForm standard.

---

## Project Overview

The objective of this assignment was to transition a static, two-page paper PDF form into an intelligent, validation-driven digital form. Rather than merely mimicking the layout, this implementation engineers the **implicit rules** of the paper form into **explicit, unbreakable constraints** within the XLSForm ecosystem. 

The resulting digital form ensures pristine data collection by blocking invalid entries, enforcing required fields dynamically, and adapting the user interface based on real-time inputs.

## Architecture & Logic Design

This project heavily leverages the advanced capabilities of the ODK standard to ensure data integrity at the point of entry. 

### Core Engineering Principles Applied:
- **Intelligent Routing & Relevance**: Conditional fields (e.g., Driver's License specifics or "Other ID" explanations) remain completely hidden unless actively triggered, eliminating visual clutter.
- **Strict Data Governance**: Unlike standard form templates, required fields strictly mirror the asterisk (`*`) notation from the source PDF. Identity-critical inputs enforce rigid formatting (e.g., future-date prevention, email/phone regex).
- **Cross-Form Consistency**: The subject's identity on Page 2 is dynamically calculated and pulled from Page 1 to eliminate human error and data mismatch across the form.
- **Compound Constraints**: Hard constraints are applied to complex requirements, such as the strict mandate to provide *at least two* distinct forms of identification before the form can be finalized.
- **Adaptive Consent Workflows**: Signatures and witness attestations utilize dedicated capture fields and dynamically adapt based on the applicant's consent status.

## XLSForm Structure & Implementation

The core logic of this project is driven entirely by the `Criminal_Risk_Assessment_Request_XLSForm.xlsx` spreadsheet, strictly adhering to the ODK XLSForm standard. The architecture of the document is divided into three foundational sheets:

- **The `survey` Sheet**: The primary engine of the form. It contains the complete translation of the paper PDF into sequential digital prompts. This sheet houses the advanced `relevant` logic columns to handle dynamic field rendering (e.g., hiding driver's license inputs unless specifically requested) and `constraint` columns enforcing regex rules on emails, phone numbers, and date boundaries (preventing future dates).
- **The `choices` Sheet**: Acts as the internal database for all cascading and static dropdown options. It holds the standardized ID types, gender selection options, and assessment reasons, keeping the main survey sheet modular and easily maintainable.
- **The `settings` Sheet**: Configures the high-level form metadata, establishing the form ID, versioning control, and the unique form title that appears on the user's data collection device.

This spreadsheet-driven approach ensures that complex validation rules—such as requiring *at least two* distinct forms of identification—are permanently embedded in the form's logic prior to XML compilation.

## Challenges and Troubleshooting

During the development and testing phase, an issue was encountered where images (e.g., reference logos) failed to render correctly in the interactive preview environment. 

A detailed breakdown of this problem and the troubleshooting process can be found in [docs/04-image-rendering-issue.md](docs/04-image-rendering-issue.md).

* **XLSForm with local media preview error:**
  `Criminal_Risk_Assessment_Request_XLSForm.xlsx`
  👉 [Live Interactive Preview (Error Version)](https://staging.enketo.getodk.org/preview?form=https%3A//staging.xlsform.getodk.org/downloads/ff8877d4732c4402986678ac6eb97b1dnfkvtxlx/Criminal_Risk_Assessment_Request_XLSForm.xml)
* **Final fixed version with image redirection:**
  `Criminal_Risk_Assessment_Request_XLSForm_PREVIEW_ONLY.xlsx`
  👉 [Live Interactive Preview (Final Version)](https://staging.enketo.getodk.org/preview?form=https%3A//staging.xlsform.getodk.org/downloads/0816e1385eac42b6beac7445e334494a0ha257rb/Criminal_Risk_Assessment_Request_XLSForm_PREVIEW_ONLY.xml)

*(Note: The live preview links above are temporary staging links generated via the ODK validation server. If they have expired, please compile the source `.xlsx` files provided.)*

## Repository Blueprint

```text
Diona_Assessment2/
├── README.md
├── Criminal Risk Assessment Request.pdf                      # The original source material
├── Criminal_Risk_Assessment_Request_XLSForm.xlsx             # XLSForm with local media preview error
├── Criminal_Risk_Assessment_Request_XLSForm_PREVIEW_ONLY.xlsx# The engineered XLSForm (Fixed image redirection)
├── docs/                                                     # Deep-dive development documentation
│   ├── 01-approach-and-planning.md
│   ├── 02-pdf-to-xlsform-mapping.md
│   ├── 03-validation-and-testing.md
│   ├── 04-image-rendering-issue.md
│   └── notebook/                                             # Raw handwritten planning logic
├── xforms/                                                   # Compiled, deployment-ready XML (Note: Do not open in web browser)
├── media/                                                    # Assets (logos, reference images)
├── validation/                                               # Audit trails and test passes
└── video/
    ├── assignment-demonstration.mp4                          # Local video file backup
    └── assignment-demonstration.md                           # Loom demonstration link & commentary
```

## Technical Stack & Tooling

| Infrastructure | Application |
| :--- | :--- |
| **XLSForm / Excel** | Core development environment for structuring `survey`, `choices`, and `settings` logic mapping. |
| **ODK Ecosystem** | Validated via *getodk.org/xlsform* to guarantee 100% compliance with XForm compilation standards. |
| **FreeImage & Media** | External hosting and asset handling for image rendering and troubleshooting. |

## Verification & Testing

Every branch of logic was manually stress-tested against the original PDF ruleset to ensure compliance with the initial project constraints. The form compiles flawlessly into standard XForm XML.

> **Validation Status**: Passed.  
> See the photographic compilation evidence in `validation/xlsform-validation.png`.

## Comprehensive Walkthrough

To review the logic, testing methodologies, and architectural decisions made during this build in real-time, please refer to the video demonstration. 

*Both a Loom link and a local MP4 file are provided. They contain the exact same video, giving you two identical options for viewing.*

**[View the Assignment Demonstration](video/assignment-demonstration.md)** 

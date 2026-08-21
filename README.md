# 📋 Criminal Risk Assessment: Digital XLSForm Transformation

**Client Context:** Manitoba Families | **Project:** Diona Technologies Assignment 2

> A comprehensive digital transcription and logic-enforced implementation of the Manitoba Families *Criminal Risk Assessment Request* using the ODK XLSForm standard.

---

## 🚀 Project Overview

The objective of this assignment was to transition a static, two-page paper PDF form into an intelligent, validation-driven digital form. Rather than merely mimicking the layout, this implementation engineers the **implicit rules** of the paper form into **explicit, unbreakable constraints** within the XLSForm ecosystem. 

The resulting digital form ensures pristine data collection by blocking invalid entries, enforcing required fields dynamically, and adapting the user interface based on real-time inputs.

## 🏗️ Architecture & Logic Design

This project heavily leverages the advanced capabilities of the ODK standard to ensure data integrity at the point of entry. 

### Core Engineering Principles Applied:
- **Intelligent Routing & Relevance**: Conditional fields (e.g., Driver's License specifics or "Other ID" explanations) remain completely hidden unless actively triggered, eliminating visual clutter.
- **Strict Data Governance**: Unlike standard form templates, required fields strictly mirror the asterisk (`*`) notation from the source PDF. Identity-critical inputs enforce rigid formatting (e.g., future-date prevention, email/phone regex).
- **Cross-Form Consistency**: The subject's identity on Page 2 is dynamically calculated and pulled from Page 1 to eliminate human error and data mismatch across the form.
- **Compound Constraints**: Hard constraints are applied to complex requirements, such as the strict mandate to provide *at least two* distinct forms of identification before the form can be finalized.
- **Adaptive Consent Workflows**: Signatures and witness attestations utilize dedicated capture fields and dynamically adapt based on the applicant's consent status.

## 📂 Repository Blueprint

```text
Diona_Assessment2/
├── README.md
├── Criminal Risk Assessment Request.pdf          # The original source material
├── Criminal_Risk_Assessment_Request_XLSForm.xlsx # The engineered XLSForm 
├── docs/                                         # Deep-dive development documentation
│   ├── 01-approach-and-planning.md
│   ├── 02-pdf-to-xlsform-mapping.md
│   ├── 03-validation-and-testing.md
│   ├── 04-image-rendering-issue.md
│   └── notebook/                                 # Raw handwritten planning logic
├── xforms/                                       # Compiled, deployment-ready XML 
├── media/                                        # Assets (logos, reference images)
├── validation/                                   # Audit trails and test passes
└── video/
    └── assignment-demonstration.md               # Loom demonstration & commentary
```

## 🛠️ Technical Stack & Tooling

| Infrastructure | Application |
| :--- | :--- |
| **XLSForm / Excel** | Core development environment for structuring `survey`, `choices`, and `settings` logic mapping. |
| **ODK Ecosystem** | Validated via *getodk.org/xlsform* to guarantee 100% compliance with XForm compilation standards. |
| **FreeImage & Media** | External hosting and asset handling for image rendering and troubleshooting. |

## 🔍 Verification & Testing

Every branch of logic was manually stress-tested against the original PDF ruleset to ensure compliance with the initial project constraints. The form compiles flawlessly into standard XForm XML.

> ✅ **Validation Status**: Passed.  
> See the photographic compilation evidence in `validation/xlsform-validation.png`.

## 📽️ Comprehensive Walkthrough

To review the logic, testing methodologies, and architectural decisions made during this build in real-time, please refer to the video demonstration. 

*Please note the provided link contains details regarding the video's runtime and recommended viewing speed.*

👉 **[View the Assignment Demonstration](video/assignment-demonstration.md)** 

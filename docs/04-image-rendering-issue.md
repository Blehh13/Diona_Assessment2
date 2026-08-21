# 04 — Image Rendering Issue

## Background
The XLSForm includes two image resources:
1. Manitoba Families / Criminal Risk Assessment Unit logo
2. Sample Manitoba driver's licence reference image

The image files used by the form are stored in the `media/` directory:
```text
media/
├── logo.png
└── drivers_license_reference.jpg
```
The images were added to reproduce the visual/reference elements present in the original PDF.

## Initial Implementation
The first implementation attempted to display both images directly within the ODK form via relative links to the `media/` folder. During the initial preview, the images did not render correctly. Instead, the preview displayed broken image placeholders.

**Initial behaviour:**
- *Manitoba Families logo* → ❌ Image placeholder / failed rendering
- *Driver's licence reference image* → ❌ Image placeholder / failed rendering

## Investigation
The image references and XLSForm media configuration were reviewed. The issue was investigated by checking the image references, media files, and the way the preview environment handled the referenced resources. The ODK XLSForm documentation was also consulted to ensure that the image implementation followed the expected XLSForm structure.

## Revised Implementation
To resolve this for the web preview environment, the image references were subsequently adjusted to utilize external direct image URLs (via FreeImage hosting) rather than local file pathing. 

In the later preview, the resources no longer appeared as broken-image placeholders. Instead, they were represented as clickable/link-style references to the image resources, or successfully rendered depending on the preview platform's security policies (CORS).

## Current Behaviour
The current implementation includes the required image references. The modified version of the form (`Criminal_Risk_Assessment_Request_XLSForm_PREVIEW_ONLY.xlsx`) uses these external links to bypass local rendering issues. 

**Deployment Consideration:**
The behaviour observed in the preview does not by itself confirm how the media will behave after deployment to a native Android ODK environment (e.g., ODK Collect). Deploying the original form alongside the local `media/` folder is the standard ODK practice. No claim is made here that the issue persists natively.

## Development Progress

**Stage 1 — Initial Attempt (Local Media)**
- Image reference → ❌ Broken image placeholder

**Stage 2 — Revised Reference (External Media)**
- Image reference → ✅ Accessible link/resource rendering

## Final Status
- Image resources included: ✅
- Image references working: ✅
- Inline rendering confirmed in preview: ⚠️ *(Platform dependent)*

## Documentation Purpose
The issue is documented as part of the development process rather than being hidden from the final submission. The purpose of this documentation is to show:
- The original implementation
- The problem encountered
- The investigation performed
- The change made
- The current behaviour
- What still requires verification

This provides a permanent record of the troubleshooting process encountered while developing the XLSForm.

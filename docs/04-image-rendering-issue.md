04 — Image Rendering Issue
Background

The XLSForm includes two image resources:

Manitoba Families / Criminal Risk Assessment Unit logo
Sample Manitoba driver's licence reference image

The image files used by the form are stored in the media directory:

media/
├── logo.png
└── drivers_license_reference.jpg

The images were added to reproduce the visual/reference elements present in the original PDF.

Initial Implementation

The first implementation attempted to display both images directly within the ODK form.

During the initial preview, the images did not render correctly.

Instead, the preview displayed broken image placeholders.

Initial behaviour

Manitoba Families logo
↓
Image placeholder / failed rendering

Driver's licence reference image
↓
Image placeholder / failed rendering

This behaviour was observed in the initial form preview.

Investigation

The image references and XLSForm media configuration were reviewed.

The issue was investigated by checking the image references, media files, and the way the preview environment handled the referenced resources.

The ODK XLSForm documentation was also consulted to ensure that the image implementation followed the expected XLSForm structure.

Revised Implementation

The image references were subsequently adjusted and the form was tested again.

In the later preview, the resources no longer appeared as broken-image placeholders.

Instead, they were represented as clickable/link-style references to the image resources.

This indicated that the resources were being referenced by the form, although they were not rendering inline as originally intended in the preview.

Current Behaviour

The current implementation includes the required image files and their references.

However, the images have not been confirmed to render inline in the current preview environment.

The later preview provides access to the referenced image resources through links rather than displaying the images directly within the form.

Therefore, the inline image-rendering behaviour remains a limitation of the current testing/preview environment.

Deployment Consideration

The current testing was performed using the available ODK XLSForm validation and preview workflow.

The behaviour observed in the preview does not by itself confirm how the media will behave after deployment to an ODK environment.

Further testing with the form deployed together with its media resources would be required to confirm the final rendering behaviour.

No claim is made here that the issue is definitely resolved after deployment.

Development Progress

The image issue progressed through the following stages:

Stage 1 — Initial Attempt

Image reference
↓
Broken image placeholder

Stage 2 — Revised Reference

Image reference
↓
Accessible link/resource

Final Status

Image resources included
+
Image references working
+
Inline rendering not confirmed

Files Used

media/
├── logo.png
└── drivers_license_reference.jpg

Documentation

The issue is documented as part of the development process rather than being hidden from the final submission.

The purpose of this documentation is to show:

The original implementation
The problem encountered
The investigation performed
The change made
The current behaviour
What still requires verification

This provides a record of the troubleshooting process encountered while developing the XLSForm.

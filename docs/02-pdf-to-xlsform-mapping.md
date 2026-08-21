02 — PDF to XLSForm Mapping
Purpose

This document records how the fields and sections in the Criminal Risk Assessment Request PDF were translated into the ODK XLSForm.

The provided PDF was used as the source for the form's content, structure, field requirements, and wording.

The provided BBCI.xlsx file was used only as a reference for understanding the general structure of an XLSForm.

1. Consent for Criminal Risk Assessment and Release of Information
Consent Information

PDF element: Consent for Criminal Risk Assessment and Release of Information

XLSForm type: note

Reason: The consent text is informational content that needs to be displayed to the user rather than entered as a response.

Read-only: Yes

Consent Date

PDF field: Date

XLSForm type: date

Purpose: Allows the user to enter the date associated with the consent section.

Validation: A constraint prevents the user from entering a future date.

Constraint:

. <= today()

Signature

PDF field: Signature

XLSForm type: image

Purpose: Captures the person's signature.

Unconsented / Witness

The consent section contains the unconsented and witness portions of the original form.

These were represented using appropriate input fields while maintaining the purpose and structure of the original section.

2. Personal Information

The following fields from the PDF were mapped to XLSForm questions:

PDF Field	XLSForm Type	Reason
First Name	text	Text input
Second Name	text	Text input
Last Name	text	Text input
Date of Birth	date	Date input
Sex	select_one	One option can be selected
Other Last Names Used	text	Text input
Other First Names Used / Also Goes By	text	Text input
Current Address	text	Address input
Current Ph#s	text	Phone number input
City/Province or Country of Birth	text	Text input
Date of Birth Validation

The Date of Birth field uses a constraint preventing a future date.

Constraint:

. <= today()

No age restriction was added because the source PDF does not specify an age requirement.

Phone Number Validation

The Current Ph#s field includes phone-number validation to reduce invalid entries.

3. Identification

The PDF states that the subject's name must be identified using:

TWO PIECES OF IDENTIFICATION

The identification field was therefore implemented using select_multiple, allowing more than one identification document to be selected.

Identification Options

The identification choices include:

Birth Certificate
Social Insurance Card
Manitoba Health Card
Treaty Card
Other
MB Driver's License with Photo
Two-Piece Requirement

A validation constraint requires at least two identification documents to be selected.

This directly represents the two-piece identification requirement in the PDF.

Conditional Identification Fields
Other ID

The Other ID field is displayed only when Other is selected.

Relevant logic:

selected(${identification_documents}, 'other')

Driver's Licence Number

The driver's licence number field is displayed only when the driver's licence option is selected.

Relevant logic:

selected(${identification_documents}, 'drivers_license')

Driver's Licence Photo

An optional driver's licence photo upload was added as a technical enhancement.

The photo field is displayed when MB Driver's License with Photo is selected.

The upload was kept optional because the PDF refers to a driver's licence with a photo but does not explicitly require the user to upload a photograph.

4. Name of Person Being Assessed

The PDF contains a section for:

NAME OF PERSON BEING ASSESSED

The implementation uses calculated/read-only information where appropriate so that the person's name can be associated with information already entered in the Personal Information section.

The purpose is to avoid unnecessary duplicate manual entry.

5. CFS Agency Designate Instructions

The instructional text provided in the PDF was implemented as read-only note content.

The user does not enter information into this section.

6. Agency Request Details

The following fields were mapped from the PDF:

PDF Field	XLSForm Type	Required
Name of Agency Submitting Request	text	Yes
Reason for Risk Assessment	select_one	Yes
Assigned Worker	text	Yes
Date of Last Criminal Risk Assessment	date	No
Submitting Designate	text	Yes
Designate Ph#	text	Yes
Designate Email#	text	Yes
Designate Fax#	text	No
Request Date	date	Yes

Fields marked with an asterisk in the PDF were treated as required.

The Date of Last Criminal Risk Assessment field remains optional because the PDF specifies (if known).

Previous Criminal Risk Assessment Date

The date field has a constraint preventing future dates.

Constraint:

. <= today()

The field can still be left blank.

Designate Phone Number

The Designate Ph# field is required and includes phone-number validation.

Designate Email

The Designate Email# field is required and includes email-format validation.

7. Final Disclaimer

The final disclaimer and instructions from the PDF were represented as read-only note content.

No user input is required for this section.

Summary

The overall PDF-to-XLSForm mapping followed this process:

PDF field or section

↓

Determine whether it requires user input or is display-only

↓

Select the appropriate XLSForm question type

↓

Determine whether the field is required

↓

Add conditional logic where required

↓

Add constraints and validation where appropriate

↓

Test and validate the form

The resulting XLSForm preserves the main structure and requirements of the original Criminal Risk Assessment Request PDF while adding appropriate ODK form logic and validation.

# AEO Management System - User Stories
## Phase 3: Validation & Risk Assessment

**Document Version:** 1.0  
**Date:** November 07, 2025  
**Project:** Authorized Economic Operator (AEO) Management System  
**Source Documents:**  
- Business Requirements Document (BRD) V1.11  
- System Requirements Document (SRD) V1.2.5

---

## Document Overview

### Purpose
This document contains detailed user stories for **Phase 3: Validation & Risk Assessment** of the AEO Management System. All user stories are directly derived from the Business Requirements Document (BRD V1.11) and System Requirements Document (SRD V1.2.5) without assumptions.

### Scope
Phase 3 covers the complete validation and risk assessment lifecycle including:
- **Initial Risk Assessment** (Local Customs)
- **Assessment Plan Preparation** (Local Customs)
- **Validation Meetings Management** (Local Customs & Commercial Establishment)
- **On-Site Validation** (Local Customs)
- **Assessment File Creation** (Local Customs)
- **Assessment Report Generation and Approval** (Local Customs & Commercial Establishment)
- **Control Plan Development** (Local Customs)

### User Roles

#### Local Customs Portal
- **Validation Team Member:** Conducts initial risk assessment, prepares assessment plan, schedules meetings, performs on-site validation, prepares assessment file and report, develops control plan
- **Validation Team Lead:** Reviews and approves initial risk assessment, assessment plan, assessment file, and assessment report; shares reports with establishment
- **AEO Program Manager:** Makes final decision on AEO status, assigns Key Account Managers Team
- **Key Account Managers Team Member:** Manages control plan post-certification, monitors AEO performance

#### AEO Portal (Commercial Establishment)
- **Commercial Establishment Account Manager:** Confirms meeting dates, reviews assessment reports, manages compliance improvement plan
- **Assessment Report Editor:** Reviews assessment reports, provides comments, uploads compliance improvement plan

---

## Table of Contents
1. [Local Customs Portal - Initial Risk Assessment](#local-customs-initial-risk-assessment)
2. [Local Customs Portal - Assessment Plan Preparation](#local-customs-assessment-plan)
3. [Local Customs Portal - Validation Meetings Management](#local-customs-validation-meetings)
4. [AEO Portal - Meeting Coordination](#aeo-portal-meeting-coordination)
5. [Local Customs Portal - On-Site Validation and Assessment File](#local-customs-assessment-file)
6. [Local Customs Portal - Assessment Report Generation](#local-customs-assessment-report)
7. [AEO Portal - Assessment Report Review](#aeo-portal-assessment-report-review)
8. [Local Customs Portal - Final Decision and Control Plan](#local-customs-final-decision)

---

<a name="local-customs-initial-risk-assessment"></a>
## 1. Local Customs Portal - Initial Risk Assessment

### Epic: Initial Risk Assessment
Enable the Validation Team to conduct initial risk assessment by reviewing the approved SAQ and identifying risks for each leaf section.

---

### US-VAL-001: Initiate Initial Risk Assessment Process

**As a** Validation Team Member  
**I want to** access the approved SAQ to begin the initial risk assessment process  
**So that** I can systematically review each section and identify potential risks

**Acceptance Criteria:**
1. System automatically sends notification to assigned Validation Team when SAQ is approved by Validation Team Lead `[SRD Section 6.3.4.2]`
2. Validation Team Member can access the approved SAQ with all sections, subsections, leaf sections, and related questions and answers visible `[SRD Section 6.3.4.2]`
3. System displays all SAQ sections to all validators assigned to the SAQ `[SRD Section 6.3.4.2]`
4. System restricts editing capability so only the owner of each section can amend it `[SRD Section 6.3.4.2]`
5. System creates "Initial Risk Assessment and Assessment Plan" with initial status "Draft" `[SRD Section 6.3.4.2.6]`
6. For each leaf section of the SAQ, assigned Validation Team Member can:
   - Add initial risks assessment
   - Add assessment plan
   - Upload reference documents
   - Confirm completion of "initial risks and assessment plan" for the section
   - Add comments to any section (including unassigned sections)
   - View internal comments from other Validation Team members
7. System allows users to identify the phase in which comments were added (SAQ review, initial risk assessment and assessment plan, on-site validation) `[SRD Section 6.3.4.2]`
8. Users can reply to comments `[SRD Section 6.3.4.2]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Initial risk assessment process
- **SRD:** Section 6.3.4.2 "Initial Risk Assessment and Assessment Plan Preparation", Pages 246-247

**Dependencies:**
- US-SAQ-026 (SAQ must be approved)

**Priority:** Must Have

---

### US-VAL-002: Identify and Analyze Initial Risks

**As a** Validation Team Member  
**I want to** identify and analyze risks for each leaf section of the SAQ  
**So that** potential compliance issues can be assessed and prioritized

**Acceptance Criteria:**
1. For each assigned leaf section, Validation Team Member can select one or more risks from predefined drop-down list `[SRD Section 6.3.4.2.1]`
2. If relevant risk is not listed in the predefined list, user can add a new risk manually `[SRD Section 6.3.4.2.1]`
3. System provides text field for user to enter brief analysis of the identified risks (Initial risks analysis) `[SRD Section 6.3.4.2.1]`
4. System provides "Consequences" field with predefined single choice list: `[SRD Section 6.3.4.2.1]`
   - Critical
   - Major
   - Moderate
   - Minor
   - Insignificant
5. System provides "Likelihood" field with predefined single choice list: `[SRD Section 6.3.4.2.1]`
   - Almost Certain
   - Likely
   - Possible
   - Unlikely
   - Rare
6. After user selects both Consequences and Likelihood, system automatically calculates Risk Rate based on risk matrix `[SRD Section 6.3.4.2.1, 5.6]`
7. Risk Rate is displayed using one of the following values:
   - Extreme
   - High
   - Medium
   - Low
8. System provides "Assessment Tool" field as drop-down list `[SRD Section 6.3.4.2.1]`
9. If required assessment tool is not listed, user can enter it manually in "Another Tool" text field `[SRD Section 6.3.4.2.1]`
10. System provides "Response to the Risks" field with following predefined single choice options: `[SRD Section 6.3.4.2.1]`
    - Take = within the acceptable materiality
    - Treat = remedial plan or included in the control plan
    - Transfer = set up a mechanism whereby an identified risk, for example related to classification or valuation, can be mitigated through a guarantee
    - Terminate = rejecting the risk as unacceptable, which means rejecting the applicant for AEO status, in that case the decision is up to the local customs to reject the application
11. All risk assessment data is saved with status "Draft" `[SRD Section 6.3.4.2.6]`
12. System provides "Save as Draft" option to continue work later `[SRD Section 6.3.4.2.6]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Risk assessment methodology
- **SRD:** Section 6.3.4.2.1 "Initial Risk Assessment", Section 5.6 "Initial Risk Assessment and Prepare Assessment Plan Data", Pages 71-75, 247-249

**Dependencies:**
- US-VAL-001

**Priority:** Must Have

---

### US-VAL-003: Prepare Assessment Plan for Each Leaf Section

**As a** Validation Team Member  
**I want to** prepare an assessment plan for each leaf section of the SAQ  
**So that** the validation approach and required activities are clearly defined

**Acceptance Criteria:**
1. For each assigned leaf section, Validation Team Member can add assessment plan details `[SRD Section 6.3.4.2.2]`
2. System provides "Assessment Method" field as multiple choice drop-down list (user can select one or more methods) `[SRD Section 6.3.4.2.2]`
3. For each added assessment method, user can optionally enter: `[SRD Section 6.3.4.2.2]`
   - Expected start date
   - Expected duration (in days or hours)
4. System automatically calculates and displays corresponding end date based on provided start date and duration `[SRD Section 6.3.4.2.2]`
5. System provides "Description" text box for entering all relevant details about actions that need to be performed during validation phase `[SRD Section 6.3.4.2.2]`
6. Assessment plan data is saved with status "Draft" `[SRD Section 6.3.4.2.6]`
7. System provides "Save as Draft" option to continue work later

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment plan preparation
- **SRD:** Section 6.3.4.2.2 "Preparing the Assessment Plan", Section 5.6 "Initial Risk Assessment and Prepare Assessment Plan Data", Pages 71-75, 249-250

**Dependencies:**
- US-VAL-001

**Priority:** Must Have

---

### US-VAL-004: Attach Reference Documents to Support Risk Assessment

**As a** Validation Team Member  
**I want to** attach reference documents to support the risk assessment and assessment plan  
**So that** the assessment is backed by relevant documentation

**Acceptance Criteria:**
1. For each leaf section, user can attach one or more reference documents to support risk assessment and assessment plan `[SRD Section 6.3.4.2.3]`
2. For each reference document, system requires the following details: `[SRD Section 6.3.4.2.3, 5.6]`
   - Document Type (mandatory)
   - Document Name (mandatory)
   - Document Version (optional)
   - Release Date (optional)
   - File Upload - the actual document file (mandatory, PDF, 5MB max)
3. User can add multiple reference documents for each leaf section
4. All required metadata must be provided for each document
5. System saves reference documents with the assessment plan in "Draft" status

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Reference documentation for risk assessment
- **SRD:** Section 6.3.4.2.3 "Adding Reference Documents", Section 5.6 "Initial Risk Assessment and Prepare Assessment Plan Data", Pages 71-75, 250

**Dependencies:**
- US-VAL-001, US-VAL-002, US-VAL-003

**Priority:** Must Have

---

### US-VAL-005: Confirm Completion of Initial Risk Assessment for Leaf Section

**As a** Validation Team Member  
**I want to** confirm completion of initial risk assessment and assessment plan for each leaf section  
**So that** progress can be tracked and the Validation Team Lead knows when to review

**Acceptance Criteria:**
1. Validation Team Member/Lead can confirm completion of their work on each leaf section `[SRD Section 6.3.4.2.4]`
2. Confirmation action indicates that the risks, assessment plan, and reference documents have been successfully identified for that specific leaf section `[SRD Section 6.3.4.2.4]`
3. System marks the leaf section as "Complete" when user confirms completion
4. System tracks which leaf sections are completed and which are pending
5. System sends notification to Validation Team Lead when a leaf section is marked as complete `[SRD Section 6.3.4.2.7]`
6. When all leaf sections are marked as complete by assigned Validation Team Members, system changes status to "Initial Risk Assessment and Assessment Plan Ready for Approval" `[SRD Section 6.3.4.2.6]`
7. System sends notification to Validation Team Lead when all sections are complete and ready for approval `[SRD Section 6.3.4.2.7]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Completion tracking for initial risk assessment
- **SRD:** Section 6.3.4.2.4 "Confirm the Completion of the 'Initial Risks and Assessment Plan'", Section 6.3.4.2.6 "Statuses of Assessment Plan", Section 6.3.4.2.7 "Notifications", Pages 250-252

**Dependencies:**
- US-VAL-001, US-VAL-002, US-VAL-003, US-VAL-004

**Priority:** Must Have

---

### US-VAL-006: Review and Approve Initial Risk Assessment and Assessment Plan

**As a** Validation Team Lead  
**I want to** review and approve the completed initial risk assessment and assessment plan  
**So that** the validation process can proceed to the on-site validation phase

**Acceptance Criteria:**
1. System sends notification to Validation Team Lead when initial risk assessment and assessment plan is complete for all leaf sections `[SRD Section 6.3.4.2.5, 6.3.4.2.7]`
2. Validation Team Lead can access and review the complete initial risk assessment and assessment plan
3. Validation Team Lead can view all leaf sections with their associated:
   - Initial risks identified
   - Risk analysis
   - Risk classification (consequences, likelihood, risk rate)
   - Assessment tools
   - Response to risks
   - Assessment plan details
   - Reference documents
4. Validation Team Lead can make needed amendments before approving the plan `[SRD Section 6.3.4.2.5]`
5. Validation Team Lead can edit any section of the initial risk assessment and assessment plan
6. Once approved, system changes status from "Initial Risk Assessment and Assessment Plan Ready for Approval" to "Initial Risk Assessment and Assessment Plan Approved" `[SRD Section 6.3.4.2.6]`
7. System sends notification to Validation Team that the initial risk assessment and assessment plan has been approved `[SRD Section 6.3.4.2.7]`
8. Notification instructs Validation Team to begin the validation process (scheduling meetings and on-site validation) `[SRD Section 6.3.4.2.7]`
9. System records status change in audit trail `[SRD Section 6.3.4.2.6]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Initial risk assessment approval process
- **SRD:** Section 6.3.4.2.5 "Approving the Initial Risk Assessment and Assessment Plan", Section 6.3.4.2.6 "Statuses of Assessment Plan", Section 6.3.4.2.7 "Notifications", Pages 251-252

**Dependencies:**
- US-VAL-005

**Priority:** Must Have

---

<a name="local-customs-assessment-plan"></a>
## 2. Local Customs Portal - Assessment Plan Preparation

(Note: Assessment plan preparation user stories are covered in US-VAL-003 and US-VAL-004 as they are part of the same workflow with initial risk assessment)

<a name="local-customs-validation-meetings"></a>
## 3. Local Customs Portal - Validation Meetings Management

### Epic: Validation Meetings Management
Enable the Validation Team to schedule, manage, and document validation meetings with commercial establishments.

---

### US-VAL-007: Schedule Validation Meetings

**As a** Validation Team Member  
**I want to** schedule validation meetings with the commercial establishment  
**So that** on-site visits and remote meetings can be organized to verify compliance

**Acceptance Criteria:**
1. After approval of initial risk assessment and assessment plan, Validation Team Member/Lead can begin scheduling meetings `[SRD Section 6.3.4.3.1]`
2. System provides meeting template dropdown for user to select appropriate template `[SRD Section 5.7]`
3. When template is selected, system auto-populates following fields (which user can modify): `[SRD Section 5.7]`
   - Meeting title
   - Meeting purpose
   - Agenda
   - Documents/information to be reviewed
4. System provides following mandatory fields for meeting scheduling: `[SRD Section 5.7]`
   - Meeting Title (text)
   - Meeting Purpose (multiple choice list)
   - Site Visit? (Yes/No, default: Yes) - if "No" selected, meeting is remote
   - Meeting Date (date)
   - Start Time (time)
   - Meeting Duration (multiple choice list)
   - List of Validators (multiple choice list, mandatory)
5. System provides optional fields: `[SRD Section 5.7]`
   - Agenda (text)
6. If Site Visit = Yes (field visit): `[SRD Section 5.7]`
   - System displays "Address" field (single choice list, mandatory)
   - Address list includes: main commercial establishment address, branch addresses from AEO authorization request, and additional facility addresses from establishment profile
   - Address consists of: Address Type, Emirate, Area, Detailed Address
   - System auto-generates and displays: Address Type, Emirate, Area, Detailed Address based on selected address
   - System displays "Documents to be Prepared" field (text, optional)
7. If Site Visit = No (remote meeting): `[SRD Section 5.7]`
   - System displays "Meeting Details" field (text, mandatory) - information needed to join the meeting including meeting link
8. System provides "Should Commercial Establishment Be Notified of This Meeting?" field (Yes/No, default: Yes, mandatory) `[SRD Section 5.7]`
9. Validation Team Member/Lead selects up to three proposed dates for each meeting `[SRD Section 6.3.4.3.1]`
10. When multiple dates are proposed, those dates cannot be reused for other commercial establishments until one is selected `[SRD Section 6.3.4.3.1]`
11. Once a date is selected by commercial establishment, remaining unselected dates become available for reuse `[SRD Section 6.3.4.3.1]`
12. Commercial establishment must be notified specific period before meeting date according to system settings (notification period) `[SRD Section 6.3.4.3.1, BR.26]`
13. System does not allow scheduling any meeting with date earlier than the defined notification period `[SRD Section 6.3.4.3.1, BR.26]`
14. If user chooses to notify commercial establishment, system sends notification with meeting details `[SRD Section 6.3.4.3.1]`
15. Meeting remains in "Proposed" status until commercial establishment confirms a date

**Business Rules:**
- **BR.26:** When scheduling meetings whether field visits, remote meetings, or a hearing session for an appeal request, the commercial establishment shall be notified of a specific period in advance, as defined in the system settings. The system will not allow scheduling any meeting with a date earlier than the defined notification period.

**Traceability:**
- **BRD:** Validation meeting scheduling
- **SRD:** Section 6.3.4.3.1 "Scheduling Meetings", Section 5.7 "Validation Meeting's Data", Pages 75-78, 252-254

**Dependencies:**
- US-VAL-006 (Initial risk assessment and assessment plan must be approved)

**Priority:** Must Have

---

### US-VAL-008: Manage Validation Team Shared Calendar

**As a** Validation Team Member  
**I want to** view and manage appointments in a shared team calendar  
**So that** all team members can see scheduled meetings and avoid conflicts

**Acceptance Criteria:**
1. Once commercial establishment confirms meeting date, appointment is automatically recorded in visit scheduling calendar of validators team `[SRD Section 6.3.4.3.1]`
2. Validators within same team have access to shared calendar showing all appointments scheduled by their team members `[SRD Section 6.3.4.3.1]`
3. Shared calendar displays:
   - Meeting date and time
   - Meeting type (site visit or remote)
   - Commercial establishment name
   - Meeting purpose
   - Assigned validators
   - Meeting status (proposed/confirmed/completed/cancelled)
4. Validators in same validation team are authorized to reschedule or cancel appointments assigned to any member of their team `[SRD Section 6.3.4.3.1]`
5. Calendar provides day, week, and month views
6. System highlights conflicts or overlapping meetings for same validator

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Team coordination and calendar management
- **SRD:** Section 6.3.4.3.1 "Scheduling Meetings", Pages 252-254

**Dependencies:**
- US-VAL-007

**Priority:** Must Have

---

### US-VAL-009: Cancel or Reschedule Validation Meetings

**As a** Validation Team Member  
**I want to** cancel or reschedule validation meetings  
**So that** meetings can be adjusted when circumstances change

**Acceptance Criteria:**
1. System allows relevant customs department to cancel or reschedule any meeting `[SRD Section 6.3.4.3.1]`
2. If meeting is cancelled, system requires user to specify reason for cancellation (mandatory) `[SRD Section 5.7, 6.3.4.3.1]`
3. System provides "Reason for Meeting Cancellation" text field (mandatory when cancelling)
4. If meeting is rescheduled:
   - User can modify meeting date, time, duration, and other details
   - System sends notification to commercial establishment if meeting notification was enabled
   - System applies same notification period rules as initial scheduling (BR.26)
5. System sends notification to commercial establishment when meeting is cancelled `[SRD Section 6.2.5.6]`
6. System sends notification to commercial establishment when meeting is rescheduled `[SRD Section 6.2.5.6]`
7. Commercial establishment can view meeting status (cancelled/rescheduled) in their portal
8. System updates shared team calendar with cancellation or new meeting details
9. If meeting was cancelled, the proposed dates become available for reuse with other establishments

**Business Rules:**
- **BR.26:** System will not allow scheduling any meeting with a date earlier than the defined notification period

**Traceability:**
- **BRD:** Meeting cancellation and rescheduling
- **SRD:** Section 6.3.4.3.1 "Scheduling Meetings", Section 5.7 "Validation Meeting's Data", Section 6.2.5.6 "Notifications", Pages 75-78, 201-202, 252-254

**Dependencies:**
- US-VAL-007

**Priority:** Must Have

---

### US-VAL-010: Record Meeting Minutes and Observations

**As a** Validation Team Member  
**I want to** record meeting minutes and observations after validation meetings  
**So that** findings from meetings are documented for the assessment file

**Acceptance Criteria:**
1. After meeting is held, Validation Team Member/Lead can record observations and meeting outcomes in meeting minutes `[SRD Section 6.3.4.3.1]`
2. System provides "Minutes of Meeting" text field (mandatory) `[SRD Section 5.7]`
3. Meeting minutes field allows entry of:
   - Meeting details
   - Observations made during the visit
   - Findings discovered
   - Documents reviewed
   - Attendees
   - Any issues or non-conformances identified
4. System allows user to upload supporting documents or photos from the visit (optional)
5. Once meeting minutes are recorded, meeting status changes to "Completed"
6. Completed meeting minutes are accessible to all validation team members
7. Meeting minutes feed into the assessment file for the relevant leaf sections
8. System records completion in audit trail
9. All validation team members can view meeting minutes for meetings conducted by their team

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Meeting documentation
- **SRD:** Section 6.3.4.3.1 "Scheduling Meetings", Section 5.7 "Validation Meeting's Data", Pages 75-78, 252-254

**Dependencies:**
- US-VAL-007

**Priority:** Must Have

---

### US-VAL-011: Generate Official Meeting Letter

**As a** Validation Team Lead  
**I want to** generate an official letter with meeting details to send to the commercial establishment  
**So that** formal communication about validation meetings is provided

**Acceptance Criteria:**
1. After commercial establishment confirms meeting dates, system issues official letter addressed to the commercial establishment `[SRD Section 6.3.4.3.1]`
2. Official letter includes following meeting details: `[SRD Section 6.3.4.3.1]`
   - Meeting date
   - Meeting time
   - Purpose of each meeting
   - Required documents to be prepared
   - Meeting location (if site visit) or meeting link (if remote)
   - List of validators who will attend
3. System auto-generates letter using predefined template
4. Letter is formatted professionally with official customs department letterhead
5. Validation Team Lead can review letter before it is sent
6. System sends letter via email to commercial establishment account manager and assessment report editors
7. Letter is also available for download in the commercial establishment's portal
8. System records letter generation in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Official meeting communication
- **SRD:** Section 6.3.4.3.1 "Scheduling Meetings", Pages 252-254

**Dependencies:**
- US-VAL-007

**Priority:** Must Have

---

<a name="aeo-portal-meeting-coordination"></a>
## 4. AEO Portal - Meeting Coordination

### Epic: Meeting Coordination (Commercial Establishment)
Enable the commercial establishment to respond to meeting invitations and coordinate validation meetings.

---

### US-VAL-012: Respond to Validation Meeting Invitations

**As a** Commercial Establishment Account Manager  
**I want to** select preferred dates from proposed meeting time slots  
**So that** validation meetings can be scheduled at convenient times

**Acceptance Criteria:**
1. When relevant customs department schedules meetings and chooses to notify commercial establishment, system sends notification `[SRD Section 6.2.5.1]`
2. Notification is sent via email and displayed in AEO Portal `[SRD Section 6.2.5.6]`
3. Notification recipients include: Commercial Establishment Account Manager and Assessment Report Editors `[SRD Section 6.2.5.6]`
4. System displays meeting invitation with up to three proposed date/time slots for each meeting `[SRD Section 6.2.5.1]`
5. Commercial Establishment Account Manager or Assessment Report Editor can select one preferred date from proposed options `[SRD Section 6.2.5.1]`
6. User can reject all proposed options `[SRD Section 6.2.5.1]`
7. If user rejects proposed meetings, customs authority can provide new set of proposed timings `[SRD Section 6.2.5.1]`
8. If commercial establishment rejects suggested meetings two times, escalation notification is sent to program manager `[SRD Section 6.3.4.3.1, 6.3.4.4.5]`
9. System provides allowed response period for commercial establishment to respond to meeting invitation
10. If commercial establishment does not respond within allowed response period, meetings are rejected automatically `[SRD Section 6.2.5.1]`
11. System sends notification to both validation team and commercial establishment when meetings are automatically rejected `[SRD Section 6.2.5.1]`
12. Once user confirms selected date, system sends confirmation notification via email and AEO Portal `[SRD Section 6.2.5.6]`
13. Confirmed meetings are reflected in validators calendar with all relevant meeting details `[SRD Section 6.2.5.1]`
14. Commercial establishment can view all scheduled, confirmed, and completed meetings in their portal

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Commercial establishment meeting coordination
- **SRD:** Section 6.2.5.1 "Confirming meeting dates", Section 6.3.4.3.1 "Scheduling Meetings", Section 6.3.4.4.5 "Notifications", Section 6.2.5.6 "Notifications", Pages 192-193, 201-202, 252-254, 268-269

**Dependencies:**
- US-VAL-007

**Priority:** Must Have

---

### US-VAL-013: View Meeting Schedule and Details

**As a** Commercial Establishment Account Manager  
**I want to** view the complete meeting schedule and details  
**So that** I can prepare appropriately for validation meetings

**Acceptance Criteria:**
1. Commercial Establishment Account Manager and Assessment Report Editors can view meeting schedule in AEO Portal
2. Meeting schedule displays:
   - Meeting date and time
   - Meeting type (site visit or remote)
   - Meeting purpose
   - Meeting agenda
   - Required documents to prepare
   - Meeting location (if site visit) or meeting link (if remote)
   - List of validators who will attend
   - Meeting status (proposed/confirmed/completed/cancelled)
3. System provides calendar view showing all upcoming meetings
4. User can download official meeting letter sent by customs department
5. System highlights upcoming meetings that require preparation
6. User can set reminders for upcoming meetings
7. For remote meetings, meeting link is accessible directly from the meeting details page
8. System displays notifications for meeting cancellations or rescheduling

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Meeting schedule visibility for commercial establishment
- **SRD:** Section 6.2.5.1 "Confirming meeting dates", Section 6.3.4.3.1 "Scheduling Meetings", Pages 192-193, 252-254

**Dependencies:**
- US-VAL-007, US-VAL-012

**Priority:** Must Have

---

<a name="local-customs-assessment-file"></a>
## 5. Local Customs Portal - On-Site Validation and Assessment File

### Epic: On-Site Validation and Assessment File Creation
Enable the Validation Team to conduct on-site validation and develop a comprehensive assessment file documenting findings, recommendations, and remaining risks.

---

### US-VAL-014: Conduct On-Site Validation

**As a** Validation Team Member  
**I want to** conduct on-site validation according to the approved assessment plan  
**So that** the commercial establishment's compliance can be verified through direct observation

**Acceptance Criteria:**
1. After approval of initial risk assessment and assessment plan, system changes status to "Commercial Establishment On-Site Validation" `[SRD Section 6.3.4.4.4]`
2. Validation Team Member/Lead can execute assessment plan by conducting scheduled meetings
3. During on-site validation, Validation Team Member/Lead can:
   - Visit commercial establishment facilities
   - Review documents and records
   - Interview personnel
   - Observe operational procedures
   - Verify information provided in SAQ
   - Identify any discrepancies or non-conformances
4. System provides access to:
   - Complete SAQ with all responses
   - Initial risk assessment for each leaf section
   - Assessment plan details
   - Meeting minutes from previous meetings
5. System records status "Commercial Establishment On-Site Validation" in audit trail `[SRD Section 6.3.4.4.4]`
6. Status remains "Commercial Establishment On-Site Validation" until validation team confirms adding all findings, recommendations, and remaining risks to assessment file `[SRD Section 6.3.4.4.4]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** On-site validation execution
- **SRD:** Section 6.3.4.3 "Detailed Validation and Risk Assessment", Section 6.3.4.4.4 "Statuses of Validation Process", Pages 252-256, 263-264

**Dependencies:**
- US-VAL-006, US-VAL-007, US-VAL-010

**Priority:** Must Have

---

### US-VAL-015: Develop Assessment File with Remaining Risks

**As a** Validation Team Member  
**I want to** prepare the assessment file by reviewing and updating risks based on on-site observations  
**So that** the final risk profile accurately reflects the validation findings

**Acceptance Criteria:**
1. During validation process, Validation Team Member/Lead prepares assessment file by reviewing initial risks and verifying relevance based on on-site observations `[SRD Section 6.3.4.3.2]`
2. System displays all SAQ sections to all validators assigned to SAQ `[SRD Section 6.3.4.3.2]`
3. System restricts editing so only owner of each section can amend it `[SRD Section 6.3.4.3.2]`
4. For each assigned leaf section, Validation Team Member can define list of remaining risks by: `[SRD Section 6.3.4.3.2]`
   - Removing risks that are no longer applicable
   - Adding newly observed risks
   - Modifying existing risks, including updates to risk analysis, likelihood, consequences, or mitigation measures
5. When risk likelihood or consequences are changed, system automatically re-calculates risk rate `[SRD Section 6.3.4.3.2]`
6. System preserves original list of risks from initial assessment unchanged and generates separate list for remaining risks `[SRD Section 6.3.4.3.2]`
7. For remaining risks, system provides following fields: `[SRD Section 5.8]`
   - Remaining Risks (multiple choice list from predefined risks, optional)
   - Remaining Risks Analysis (text, description of remaining risks analysis, optional)
   - Consequences (single choice list: Critical/Major/Moderate/Minor/Insignificant, mandatory if remaining risks are selected)
   - Likelihood (single choice list: Almost Certain/Likely/Possible/Unlikely/Rare, mandatory if remaining risks are selected)
   - Remaining Risk Rate (automatically generated: Extreme/High/Medium/Low based on consequences and likelihood)
   - Respond to Remaining Risks (single choice list: Tolerate/Treat/Transfer/Terminate, mandatory if risks are selected)
8. Assessment file data follows structure defined in data dictionary "Assessment File Data" `[SRD Section 6.3.4.3.2, 5.8]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment file development with risk updates
- **SRD:** Section 6.3.4.3.2 "The Development of the Assessment File", Section 5.8 "Assessment's File Data", Pages 78-81, 254-256

**Dependencies:**
- US-VAL-014

**Priority:** Must Have

---

### US-VAL-016: Record Findings in Assessment File

**As a** Validation Team Member  
**I want to** record findings for each leaf section based on validation observations  
**So that** specific issues and observations are documented in the assessment file

**Acceptance Criteria:**
1. System allows user to enter multiple findings under each leaf section `[SRD Section 6.3.4.3.2]`
2. For each finding, system provides following fields: `[SRD Section 5.8]`
   - Title (text, short title summarizing the observation, mandatory)
   - Content (text, detailed description of the risk assessment findings based on validation process, clarifying extent to which information provided in SAQ aligns with actual situation, mandatory)
   - Finding Evidence (document, uploaded by validation team if there is supporting document for findings, optional)
3. User can add multiple findings per leaf section
4. Each finding is associated with the specific leaf section where it was identified
5. Findings capture:
   - Non-conformances with AEO requirements
   - Discrepancies between SAQ responses and actual observations
   - Areas requiring improvement
   - Positive observations of good practices
6. System maintains chronological record of when each finding was added
7. Validation Team Member can edit or delete findings they have added
8. All findings are visible to all validation team members assigned to the SAQ

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Findings documentation
- **SRD:** Section 6.3.4.3.2 "The Development of the Assessment File", Section 5.8 "Assessment's File Data", Pages 78-81, 254-256

**Dependencies:**
- US-VAL-014, US-VAL-015

**Priority:** Must Have

---

### US-VAL-017: Enter Recommendations in Assessment File

**As a** Validation Team Member  
**I want to** enter recommendations for each leaf section  
**So that** specific actions or changes needed for AEO compliance are documented

**Acceptance Criteria:**
1. System supports entering multiple recommendations per leaf section `[SRD Section 6.3.4.3.2]`
2. For each recommendation, system provides following fields: `[SRD Section 5.8]`
   - Title (text, short title summarizing the recommendation based on validation process, mandatory)
   - Content (text, detailed description of any changes, actions, or requirements needed for applicant to meet AEO criteria in UAE, mandatory)
3. User can add multiple recommendations per leaf section
4. Each recommendation is associated with the specific leaf section where improvement is needed
5. Recommendations include:
   - Corrective actions for non-conformances
   - Improvement suggestions for areas that don't fully meet standards
   - Enhancement opportunities for better compliance
   - Implementation guidance
6. System maintains record of when each recommendation was added
7. Validation Team Member can edit or delete recommendations they have added
8. All recommendations are visible to all validation team members assigned to the SAQ
9. If there are remarks that do not affect decision-making process (i.e., improvement actions), they are included under recommendations `[SRD Section 6.3.4.3.4]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Recommendations documentation
- **SRD:** Section 6.3.4.3.2 "The Development of the Assessment File", Section 5.8 "Assessment's File Data", Section 6.3.4.3.4 "The Development of the Assessment Report", Pages 78-81, 254-257

**Dependencies:**
- US-VAL-014, US-VAL-015, US-VAL-016

**Priority:** Must Have

---

### US-VAL-018: Add Comments During On-Site Validation

**As a** Validation Team Member  
**I want to** add internal comments to any section during on-site validation  
**So that** team communication and collaboration is facilitated

**Acceptance Criteria:**
1. Validation Team Member can add comments to any section, including sections not assigned to them `[SRD Section 6.3.4.3.2]`
2. System allows user to identify phase in which comments were added: `[SRD Section 6.3.4.3.2]`
   - SAQ review phase
   - Initial risk assessment and assessment plan phase
   - On-site validation phase
3. User can reply to comments added by other Validation Team members `[SRD Section 6.3.4.3.2]`
4. Comments are visible only to validation team members (not visible to commercial establishment)
5. Each comment includes:
   - Comment text
   - Author name and role
   - Timestamp
   - Phase/context identifier
   - Parent comment (if it's a reply)
6. System displays comments in chronological order
7. Users receive notification when comments are added to their assigned sections
8. System maintains comment history in audit trail
9. Comments facilitate internal team discussions about findings, recommendations, and assessment approach

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Internal team collaboration
- **SRD:** Section 6.3.4.3.2 "The Development of the Assessment File", Pages 254-256

**Dependencies:**
- US-VAL-014

**Priority:** Must Have

---

### US-VAL-019: Confirm Completion of Assessment File for Leaf Section

**As a** Validation Team Member  
**I want to** confirm completion of the assessment file for each leaf section  
**So that** progress can be tracked and the Validation Team Lead knows when all sections are ready for approval

**Acceptance Criteria:**
1. Validation Team Member/Lead can confirm completion of their work on each leaf section `[SRD Section 6.3.4.3.2]`
2. Confirmation action indicates that remaining risks, findings, and recommendations have been successfully identified for that specific leaf section `[SRD Section 6.3.4.3.2]`
3. System marks the leaf section as "Complete" in the assessment file
4. System tracks which leaf sections are completed and which are pending
5. When validation team confirms adding all findings, recommendations, and remaining risks to assessment file for all leaf sections, system changes status to "Assessment File Ready for Approval" `[SRD Section 6.3.4.4.4]`
6. System sends notification to Validation Team Lead that assessment file is ready for approval `[SRD Section 6.3.4.4.5]`
7. System records status change in audit trail `[SRD Section 6.3.4.4.4]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment file completion tracking
- **SRD:** Section 6.3.4.3.2 "The Development of the Assessment File", Section 6.3.4.4.4 "Statuses of Validation Process", Section 6.3.4.4.5 "Notifications", Pages 254-256, 263-264, 268-269

**Dependencies:**
- US-VAL-015, US-VAL-016, US-VAL-017

**Priority:** Must Have

---

### US-VAL-020: Review and Approve Assessment File

**As a** Validation Team Lead  
**I want to** review and approve the completed assessment file  
**So that** the assessment report can be generated

**Acceptance Criteria:**
1. Once all leaf sections are marked as complete, system sends notification to Validation Team Lead to approve assessment file `[SRD Section 6.3.4.3.3]`
2. Validation Team Lead can access and review complete assessment file including:
   - All remaining risks for each leaf section
   - All findings documented
   - All recommendations provided
   - Internal comments from validation team
3. Validation Team Lead can edit the file and make needed changes before approving it `[SRD Section 6.3.4.3.3]`
4. Validation Team Lead can:
   - Modify remaining risks, findings, or recommendations
   - Add additional findings or recommendations
   - Request changes from validation team members
5. Once Validation Team Lead approves assessment file, system changes status from "Assessment File Ready for Approval" to "Assessment File Approved" `[SRD Section 6.3.4.4.4]`
6. System records approval in audit trail `[SRD Section 6.3.4.4.4]`
7. Once assessment file is approved, system automatically generates "Assessment Report" in "Draft" status `[SRD Section 6.3.4.3.3]`
8. Assessment Report becomes accessible by validation team `[SRD Section 6.3.4.3.3]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment file approval
- **SRD:** Section 6.3.4.3.3 "Approve the Assessment File", Section 6.3.4.4.4 "Statuses of Validation Process", Pages 255-256, 263-264

**Dependencies:**
- US-VAL-019

**Priority:** Must Have

---

<a name="local-customs-assessment-report"></a>
## 6. Local Customs Portal - Assessment Report Generation

### Epic: Assessment Report Generation and Approval
Enable the Validation Team to generate, review, and share the assessment report with the commercial establishment.

---

### US-VAL-021: Generate Draft Assessment Report

**As a** Validation Team Member  
**I want to** generate a draft assessment report from the approved assessment file  
**So that** findings, recommendations, and risks can be compiled into a formal report

**Acceptance Criteria:**
1. Once assessment file is approved by Validation Team Lead, system automatically generates "Assessment Report" in "Draft" status `[SRD Section 6.3.4.3.4]`
2. Assessment Report becomes accessible by validation team `[SRD Section 6.3.4.3.4]`
3. System auto-populates assessment report with following sections: `[SRD Section 6.3.4.3.4, 5.9]`
   - Details of headquarter and all branches included in validation process (auto-populated from commercial establishment profile)
   - Report scope (to be added by validation team)
   - Findings (auto-populated from assessment file using same structure as SAQ)
   - Recommendations (auto-populated from assessment file using same structure as SAQ)
   - Risks (auto-populated from assessment file using same structure as SAQ)
   - Summary of observations (to be added by validation team)
4. Assessment report includes complete commercial establishment details: `[SRD Section 5.9]`
   - Commercial establishment name (Arabic and English, read-only)
   - Emirate (read-only)
   - Legal form (read-only)
   - License issuer (read-only)
   - And other establishment data as per data dictionary
5. If there are remarks that do not affect decision-making process (improvement actions), they are included under recommendations `[SRD Section 6.3.4.3.4]`
6. Detailed data of assessment report is described in data dictionary "Assessment Report Data" `[SRD Section 6.3.4.3.4, 5.9]`
7. System organizes findings, recommendations, and risks by SAQ structure (sections, subsections, leaf sections)
8. Validation team can save assessment report as draft to continue working on it later `[SRD Section 6.3.4.3.4]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment report generation
- **SRD:** Section 6.3.4.3.4 "The Development of the Assessment Report", Section 5.9 "Assessment Report Data", Pages 81-88, 256-257

**Dependencies:**
- US-VAL-020

**Priority:** Must Have

---

### US-VAL-022: Complete Assessment Report Content

**As a** Validation Team Member  
**I want to** add report scope and summary of observations to the draft assessment report  
**So that** the report provides complete context and conclusions

**Acceptance Criteria:**
1. Validation Team Member can add "Report Scope" to assessment report `[SRD Section 6.3.4.3.4]`
2. Report scope describes:
   - Validation objectives
   - Scope of assessment (which areas/activities were assessed)
   - Assessment period
   - Methodology used
   - Limitations or constraints
3. Validation Team Member can add "Summary of Observations" to assessment report `[SRD Section 6.3.4.3.4]`
4. Summary of observations includes:
   - Overall assessment conclusion
   - Key findings and their significance
   - Major risks identified
   - Critical recommendations
   - Overall compliance level
5. System allows multiple team members to collaborate on report content
6. Validation Team can save report as draft at any time `[SRD Section 6.3.4.3.4]`
7. Once all mandatory fields are filled in, validation team can submit assessment report to Validation Team Lead to share with commercial establishment `[SRD Section 6.3.4.3.4]`
8. System validates that all required sections are completed before allowing submission

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment report content completion
- **SRD:** Section 6.3.4.3.4 "The Development of the Assessment Report", Pages 256-257

**Dependencies:**
- US-VAL-021

**Priority:** Must Have

---

### US-VAL-023: Determine Content to Share with Commercial Establishment

**As a** Validation Team Lead  
**I want to** determine which contents of the draft assessment report should be shared with the commercial establishment  
**So that** sensitive or confidential information can be excluded from the shared version

**Acceptance Criteria:**
1. Once assessment report is submitted to Validation Team Lead for sharing, system allows Validation Team Lead to review report before sharing `[SRD Section 6.3.4.3.5]`
2. Validation Team Lead can determine certain contents that are not to be shared with establishment: `[SRD Section 6.3.4.3.5]`
   - Findings: possibility to remove some or all
   - Recommendations: possibility of removing some or all
   - Risks: possibility of removing some or all
3. System provides interface for Validation Team Lead to select which findings, recommendations, and risks to include or exclude
4. System creates two versions of report:
   - Internal version (complete report with all findings, recommendations, and risks)
   - Shared version (report with selected content for commercial establishment)
5. For each trade license included in report, Validation Team Lead assesses whether commercial establishment is required to undertake corrective actions `[SRD Section 6.3.4.3.5]`
6. Validation Team Lead can provide specific remarks for any trade license identified as requiring submission of Compliance Improvement Plan `[SRD Section 6.3.4.3.5]`
7. System allows Validation Team Lead to indicate for each trade license:
   - Whether Compliance Improvement Plan is required (Yes/No)
   - Specific remarks about required corrective actions
8. System preserves complete internal version for customs department records

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment report content control
- **SRD:** Section 6.3.4.3.5 "Sharing the Assessment Report with the Commercial Establishment", Pages 257-258

**Dependencies:**
- US-VAL-022

**Priority:** Must Have

---

### US-VAL-024: Share Draft Assessment Report with Commercial Establishment

**As a** Validation Team Lead  
**I want to** share the draft assessment report with the commercial establishment  
**So that** they can review findings and provide feedback or corrective action plans

**Acceptance Criteria:**
1. After Validation Team Lead determines content to share, system allows sharing of draft assessment report with commercial establishment `[SRD Section 6.3.4.3.5, 6.3.4.3.6]`
2. System changes status from "Assessment File Approved" to "Draft Assessment Report Shared" `[SRD Section 6.3.4.4.4]`
3. System sends notification to commercial establishment via email and AEO Portal `[SRD Section 6.2.5.2, 6.2.5.6]`
4. Notification recipients include: Commercial Establishment Account Manager and all Assessment Report Editors `[SRD Section 6.2.5.2, 6.2.5.6]`
5. Draft assessment report contains findings and recommendations related to observations made during validation process `[SRD Section 6.2.5.2]`
6. Report clearly indicates for each trade license whether Compliance Improvement Plan is required
7. If Compliance Improvement Plan is required, report includes specific remarks about required corrective actions
8. System records sharing action in audit trail `[SRD Section 6.3.4.4.4]`
9. Commercial establishment can access shared draft assessment report in their portal
10. Report is provided in read-only format for commercial establishment
11. System provides deadline for commercial establishment to respond to draft assessment report

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment report sharing
- **SRD:** Section 6.3.4.3.5 "Sharing the Assessment Report with the Commercial Establishment", Section 6.3.4.3.6 "Approving the Assessment Report", Section 6.3.4.4.4 "Statuses of Validation Process", Section 6.2.5.2 "Reviewing of Draft Assessment Report", Section 6.2.5.6 "Notifications", Pages 193-194, 201-202, 257-258, 263-264

**Dependencies:**
- US-VAL-023

**Priority:** Must Have

---

<a name="aeo-portal-assessment-report-review"></a>
## 7. AEO Portal - Assessment Report Review

### Epic: Assessment Report Review and Response (Commercial Establishment)
Enable the commercial establishment to review the draft assessment report, provide feedback, and submit compliance improvement plans if required.

---

### US-VAL-025: Review Draft Assessment Report

**As a** Commercial Establishment Account Manager  
**I want to** review the draft assessment report shared by customs  
**So that** I can understand the validation findings and determine necessary actions

**Acceptance Criteria:**
1. When customs department shares draft assessment report, notification is sent to Commercial Establishment Account Manager and all Assessment Report Editors `[SRD Section 6.2.5.2]`
2. Notification is sent via email and displayed in AEO Portal `[SRD Section 6.2.5.6]`
3. Draft assessment report is accessible in AEO Portal
4. Users can view following sections of report: `[SRD Section 6.2.5.2]`
   - Commercial establishment details
   - Report scope
   - Findings related to observations during validation
   - Recommendations
   - Risks
   - Summary of observations
   - Indication of whether Compliance Improvement Plan is required for each trade license
   - Specific remarks about required corrective actions (if applicable)
5. Report is organized by SAQ structure (sections, subsections, leaf sections)
6. Users can navigate through different sections of the report
7. System highlights findings and recommendations that require attention
8. Users can download copy of draft assessment report
9. System displays deadline for responding to draft assessment report

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment report review by commercial establishment
- **SRD:** Section 6.2.5.2 "Reviewing of Draft Assessment Report", Section 6.2.5.6 "Notifications", Pages 193-194, 201-202

**Dependencies:**
- US-VAL-024

**Priority:** Must Have

---

### US-VAL-026: Provide Comments on Draft Assessment Report

**As a** Commercial Establishment Account Manager  
**I want to** add comments on the draft assessment report  
**So that** I can provide feedback or clarifications to customs department

**Acceptance Criteria:**
1. If user has comments on draft report, system allows adding comments `[SRD Section 6.2.5.2]`
2. Users can add comments on each section (leaf) of draft report `[SRD Section 6.2.5.2]`
3. Users can provide general feedback on overall report `[SRD Section 6.2.5.2]`
4. Comment functionality includes:
   - Comment text field
   - Section/finding reference
   - Supporting documents upload (optional)
5. Multiple users (Commercial Establishment Account Manager and Assessment Report Editors) can add comments
6. Comments can address:
   - Disagreements with findings
   - Additional context or explanations
   - Clarifications about establishment practices
   - Questions about recommendations
7. After adding comments, user can return draft assessment report to customs department `[SRD Section 6.2.5.2]`
8. System sends notification to Validation Team when report is returned with comments `[SRD Section 6.2.5.6, 6.3.4.4.5]`
9. System records return action in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Commercial establishment feedback on assessment report
- **SRD:** Section 6.2.5.2 "Reviewing of Draft Assessment Report", Section 6.2.5.6 "Notifications", Section 6.3.4.4.5 "Notifications", Pages 193-194, 201-202, 268-269

**Dependencies:**
- US-VAL-025

**Priority:** Must Have

---

### US-VAL-027: Upload Compliance Improvement Plan

**As a** Commercial Establishment Account Manager  
**I want to** upload a Compliance Improvement Plan for corrective actions  
**So that** required improvements can be implemented and verified

**Acceptance Criteria:**
1. If Compliance Improvement Plan is required (indicated in draft assessment report), eligible user can upload plan `[SRD Section 6.2.5.2, 5.9]`
2. System displays indication that Compliance Improvement Plan is required for specific trade license(s)
3. Commercial establishment needs to upload separate Compliance Improvement Plan for each trade license that requires corrective actions `[SRD Section 5.9]`
4. For uploading Compliance Improvement Plan, system provides: `[SRD Section 5.9]`
   - File upload field (PDF, 5MB max, mandatory)
   - Implementation Deadline field (number of days required to implement corrective actions, mandatory)
5. System automatically calculates and displays expected date for completion based on implementation deadline `[SRD Section 5.9]`
6. Compliance Improvement Plan should address:
   - Specific findings requiring corrective action
   - Detailed action plan for each issue
   - Responsible parties
   - Resources required
   - Timeline for implementation
7. System allows uploading plan whether user agrees or has comments on draft report `[SRD Section 6.2.5.2]`
8. If user agrees on draft report and Compliance Improvement Plan is required: `[SRD Section 6.2.5.2]`
   - User uploads Compliance Improvement Plan along with implementation period
   - User approves the report
   - Compliance Improvement Plan is sent to customs department for review
9. If user has comments on draft report and Compliance Improvement Plan is required: `[SRD Section 6.2.5.2]`
   - User can optionally upload Compliance Improvement Plan along with implementation period
   - User can add comments and return report to customs
10. System validates file format and size before accepting upload

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Compliance Improvement Plan submission
- **SRD:** Section 6.2.5.2 "Reviewing of Draft Assessment Report", Section 5.9 "Assessment Report Data", Pages 86-87, 193-194

**Dependencies:**
- US-VAL-025

**Priority:** Must Have

---

### US-VAL-028: Approve Draft Assessment Report

**As a** Commercial Establishment Account Manager  
**I want to** approve the draft assessment report  
**So that** the validation process can proceed to final decision phase

**Acceptance Criteria:**
1. If user agrees on draft report, system allows approval `[SRD Section 6.2.5.2]`
2. Two approval scenarios:
   
   **Scenario A - Compliance Improvement Plan Not Required:** `[SRD Section 6.2.5.2]`
   - Eligible users approve the report
   - Status changes to status reflecting approval and readiness for final decision
   
   **Scenario B - Compliance Improvement Plan Required:** `[SRD Section 6.2.5.2]`
   - Eligible user uploads Compliance Improvement Plan along with implementation period
   - Eligible users approve the report
   - Compliance Improvement Plan is sent to customs department for review
3. System sends notification to customs department when report is approved `[SRD Section 6.2.5.6, 6.3.4.4.5]`
4. Notification recipients include Validation Team and AEO Program Manager
5. Only authorized users (Commercial Establishment Account Manager) can approve report
6. System validates that Compliance Improvement Plan is uploaded (if required) before allowing approval
7. System records approval in audit trail
8. After approval, report becomes read-only for commercial establishment
9. System updates status to reflect commercial establishment's approval

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment report approval by commercial establishment
- **SRD:** Section 6.2.5.2 "Reviewing of Draft Assessment Report", Section 6.2.5.6 "Notifications", Section 6.3.4.4.5 "Notifications", Pages 193-194, 201-202, 268-269

**Dependencies:**
- US-VAL-025

**Priority:** Must Have

---

### US-VAL-029: Submit Request to Extend Compliance Improvement Plan Deadline

**As a** Commercial Establishment Account Manager  
**I want to** submit a justified extension request for the Compliance Improvement Plan implementation deadline  
**So that** additional time can be granted if needed for completing corrective actions

**Acceptance Criteria:**
1. If commercial establishment cannot complete implementation of Compliance Improvement Plan within period, system allows submitting extension request `[SRD Section 6.3.4.4, 5.9]`
2. Extension request must be submitted to relevant customs department before deadline `[SRD Section 6.3.4.4]`
3. System provides following fields for extension request: `[SRD Section 5.9]`
   - Justification for Extension Request (text, description of justifications, mandatory)
   - Document Name (text, identification name of supporting documents, optional)
   - Document (file upload, supporting documents for extension request, PDF, 5MB, optional)
4. System validates that request is submitted before current deadline expires
5. System sends notification to Validation Team Lead when extension request is submitted
6. System tracks extension request status:
   - Submitted
   - Under Review
   - Approved (with new deadline)
   - Rejected
7. If extension is approved:
   - Validation Team Lead sets extension period within maximum allowed period defined in system settings `[SRD Section 6.3.4.4]`
   - System updates implementation deadline
   - System notifies commercial establishment of approved extension
8. If extension is rejected:
   - Validation Team Lead adds recommendation about granting AEO status `[SRD Section 6.3.4.4]`
   - Full case is forwarded to AEO Program Manager for final decision
   - System notifies commercial establishment of rejection
9. System records all extension requests and decisions in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Compliance Improvement Plan extension process
- **SRD:** Section 6.3.4.4 "Assessment of Compliance Improvement Plan Extension Request", Section 5.9 "Assessment Report Data", Pages 87, 259

**Dependencies:**
- US-VAL-027, US-VAL-028

**Priority:** Must Have

---

### US-VAL-030: Confirm Completion of Compliance Improvement Plan Implementation

**As a** Commercial Establishment Account Manager  
**I want to** confirm that the Compliance Improvement Plan has been implemented  
**So that** customs can verify the completion and proceed with final AEO status decision

**Acceptance Criteria:**
1. If commercial establishment successfully implements Compliance Improvement Plan within deadline, system allows entering completion data `[SRD Section 6.3.4.4.1, 5.9]`
2. System provides following fields for confirming implementation: `[SRD Section 5.9]`
   - Detailed Description (text, entering detailed description of actions implemented based on corrective actions stated in assessment report, mandatory)
   - Supporting Document Name (text, necessary document name that proves implementation of corrective actions, mandatory)
   - Supporting Document (file upload, attaching necessary documents proving implementation of corrective actions, mandatory)
3. Supporting documents can be in following formats: `[SRD Section 5.9]`
   - docx
   - xlsx
   - pdf
   - png / jpeg / jpg
4. System validates file size and format before accepting upload `[SRD Section 6.3.4.4.1]`
5. Commercial establishment can provide evidence for each corrective action implemented
6. System sends notification to Validation Team Lead upon receiving completion confirmation `[SRD Section 6.3.4.4.1]`
7. Status changes to indicate that implementation is confirmed and awaiting verification
8. System records completion confirmation in audit trail
9. Completion data and supporting documents become accessible to Validation Team for verification

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Compliance Improvement Plan completion confirmation
- **SRD:** Section 6.3.4.4.1 "Confirm the Completion of the Compliance Improvement Plan", Section 5.9 "Assessment Report Data", Pages 87-88, 259-260

**Dependencies:**
- US-VAL-027, US-VAL-028

**Priority:** Must Have

---

<a name="local-customs-final-decision"></a>
## 8. Local Customs Portal - Final Decision and Control Plan

### Epic: Final AEO Status Decision and Control Plan Development
Enable the Validation Team Lead and AEO Program Manager to make final decisions on AEO status and develop control plans for approved establishments.

---

### US-VAL-031: Review Returned Assessment Report with Comments

**As a** Validation Team Member  
**I want to** review the assessment report returned by the commercial establishment with comments  
**So that** feedback can be addressed and the report can be finalized

**Acceptance Criteria:**
1. When commercial establishment returns draft report with comments, system sends notification to Validation Team `[SRD Section 6.3.4.4.5]`
2. Notification is sent via email and displayed in Local Customs AEO Management Portal `[SRD Section 6.3.4.4.5]`
3. Validation Team can view all comments provided by commercial establishment
4. Comments are displayed alongside the relevant sections/findings they reference
5. Validation Team can:
   - Review each comment
   - Discuss comments internally using internal comment system
   - Modify findings or recommendations based on valid comments
   - Reject comments with justification
   - Request additional clarification from commercial establishment
6. Validation Team can update draft assessment report based on feedback
7. After addressing comments, Validation Team can re-share updated draft with commercial establishment
8. System tracks all iterations of draft assessment report
9. System records all review activities in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Assessment report review and revision
- **SRD:** Section 6.3.4.3.6 "Approving the Assessment Report", Section 6.3.4.4.5 "Notifications", Pages 258, 268-269

**Dependencies:**
- US-VAL-026

**Priority:** Must Have

---

### US-VAL-032: Review and Evaluate Compliance Improvement Plan

**As a** Validation Team Lead  
**I want to** review the Compliance Improvement Plan submitted by the commercial establishment  
**So that** I can determine if the proposed corrective actions are adequate

**Acceptance Criteria:**
1. When commercial establishment submits Compliance Improvement Plan, system makes it accessible to Validation Team Lead `[SRD Section 6.2.5.2, 6.3.4.4.1]`
2. Validation Team Lead can review:
   - Compliance Improvement Plan document
   - Proposed implementation deadline
   - Alignment with findings and recommendations in assessment report
3. Validation Team Lead can evaluate if plan adequately addresses all required corrective actions
4. Validation Team Lead has following options: `[SRD Section 6.3.4.4.1]`
   
   **Option A - Accept Plan:**
   - Approve Compliance Improvement Plan
   - Status changes to indicate plan is approved and under execution
   - System sends notification to commercial establishment `[SRD Section 6.2.5.6]`
   
   **Option B - Return Plan:**
   - Return plan to commercial establishment with comments requesting modifications `[SRD Section 6.3.4.4.1]`
   - Add multiple comments, for each comment specify:
     * Section of plan related to comment
     * Details of comment
   - Status changes to indicate plan is returned
   - System sends notification to commercial establishment `[SRD Section 6.2.5.6]`
5. If plan is returned, commercial establishment can revise and resubmit (can happen recursively multiple times)
6. System tracks all versions of Compliance Improvement Plan submitted
7. System records all review decisions in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Compliance Improvement Plan review
- **SRD:** Section 6.3.4.4.1 "Confirm the Completion of the Compliance Improvement Plan", Section 6.2.5.2 "Reviewing of Draft Assessment Report", Section 6.2.5.6 "Notifications", Pages 193-194, 201-202, 259-260

**Dependencies:**
- US-VAL-027

**Priority:** Must Have

---

### US-VAL-033: Verify Compliance Improvement Plan Implementation

**As a** Validation Team Lead  
**I want to** verify that the Compliance Improvement Plan has been properly implemented  
**So that** I can confirm corrective actions before making final recommendation

**Acceptance Criteria:**
1. Upon receiving notification of Compliance Improvement Plan completion from commercial establishment, Validation Team Lead reviews implementation `[SRD Section 6.3.4.4.1]`
2. Validation Team Lead can access:
   - Original Compliance Improvement Plan
   - Detailed description of actions implemented
   - Supporting documents proving implementation
3. Validation Team Lead can conduct verification activities:
   - Review submitted evidence
   - Schedule follow-up meetings if needed
   - Conduct site visits to verify implementation (optional)
4. Validation Team Lead has following options: `[SRD Section 6.3.4.4.1]`
   
   **Option A - Confirm Implementation:**
   - Confirms successful completion of Compliance Improvement Plan for specific trade license
   - If assessment report includes multiple trade licenses, system prompts for recommendation on whether to grant AEO status for that license
   - Status changes to indicate implementation is confirmed
   - Process proceeds to final recommendation
   
   **Option B - Return for Further Action:**
   - Returns report to commercial establishment requesting further clarification or additional information `[SRD Section 6.3.4.4.1]`
   - Can add multiple comments specifying required actions
   - Status changes to indicate further implementation required
   
   **Option C - Reject Implementation:**
   - Rejects completion of Compliance Improvement Plan `[SRD Section 6.3.4.4.1]`
   - Indicates recommendation NOT to grant AEO status for specific trade license
   - Decision applies to concerned license and does not affect other trade licenses in same assessment report
   - Final decision will be made by AEO Program Manager
5. System records verification decision in audit trail
6. System sends notifications to relevant parties based on decision

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Compliance Improvement Plan verification
- **SRD:** Section 6.3.4.4.1 "Confirm the Completion of the Compliance Improvement Plan", Pages 259-260

**Dependencies:**
- US-VAL-030, US-VAL-032

**Priority:** Must Have

---

### US-VAL-034: Submit Final Recommendation on AEO Status

**As a** Validation Team Lead  
**I want to** submit my final recommendation on granting AEO status  
**So that** the AEO Program Manager can make the final decision

**Acceptance Criteria:**
1. Once assessment report is approved by commercial establishment (with or without Compliance Improvement Plan implementation confirmed), Validation Team Lead can submit recommendation `[SRD Section 6.3.4.4.1, 6.3.4.4.2]`
2. For each trade license in assessment report, Validation Team Lead provides recommendation:
   - Grant AEO status
   - Do not grant AEO status (with justification)
3. System compiles assessment file for forwarding to AEO Program Manager with following information: `[SRD Section 6.3.4.4.2]`
   - Assessment File (complete with all findings, recommendations, remaining risks)
   - Assessment Report (complete internal version)
   - Compliance Improvement Plan (if applicable)
   - Validation Team Lead's recommendation for each trade license
4. System changes status to indicate recommendation is submitted and awaiting final decision
5. System sends notification to AEO Program Manager that assessment file is ready for final decision `[SRD Section 6.3.4.4.5]`
6. Notification includes summary of validation findings and recommendations
7. System records recommendation submission in audit trail
8. Assessment file becomes accessible to AEO Program Manager for review

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Final recommendation submission
- **SRD:** Section 6.3.4.4.1 "Confirm the Completion of the Compliance Improvement Plan", Section 6.3.4.4.2 "AEO Decision", Section 6.3.4.4.5 "Notifications", Pages 259-261, 268-269

**Dependencies:**
- US-VAL-028, US-VAL-033 (if Compliance Improvement Plan was required)

**Priority:** Must Have

---

### US-VAL-035: Make Final Decision on AEO Status

**As an** AEO Program Manager  
**I want to** review the complete assessment file and make final decision on granting AEO status  
**So that** the commercial establishment can receive final determination

**Acceptance Criteria:**
1. Once Validation Team Lead submits recommendation, AEO Program Manager receives assessment file with: `[SRD Section 6.3.4.4.2]`
   - Assessment File
   - Assessment Report
   - Compliance Improvement Plan (if applicable)
   - Validation Team Lead's recommendation for each trade license
2. AEO Program Manager reviews complete assessment documentation
3. AEO Program Manager has following decision options: `[SRD Section 6.3.4.4.2]`
   
   **Option A - Request Further Clarifications:**
   - Returns file to Validation Team for additional information
   - Specifies what clarifications are needed
   - System sends notification to Validation Team
   
   **Option B - Reject Granting AEO Status:**
   - Rejects granting AEO status with justification
   - System changes status to "AEO Status Rejected"
   - Commercial establishment and Validation Team are notified `[SRD Section 6.3.4.4.2]`
   - Status becomes final
   
   **Option C - Approve Granting AEO Status:**
   - Approves granting AEO status to commercial establishment
   - System changes status to "AEO Status Granted"
   - Following occurs simultaneously: `[SRD Section 6.3.4.4.2]`
     * Commercial establishment is notified of approval
     * Validation Team is notified to start preparing Control Plan
     * AEO Program Manager must assign Key Account Managers Team
4. If status is approved, system provides interface for AEO Program Manager to assign Key Account Managers Team
5. Key Account Managers Team becomes responsible for:
   - Serving as only contact point with commercial establishment after granting AEO status `[SRD Section 6.3.4.4.2]`
   - Confirming branches for which certificate will be issued
   - Specifying benefits group
   - Identifying authorized contact person to communicate on behalf of commercial establishment
6. System records decision in audit trail `[SRD Section 6.3.4.4.4]`
7. System sends notifications to all relevant parties `[SRD Section 6.3.4.4.5]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Final AEO status decision
- **SRD:** Section 6.3.4.4.2 "AEO Decision", Section 6.3.4.4.4 "Statuses of Validation Process", Section 6.3.4.4.5 "Notifications", Pages 260-261, 263-268, 268-269

**Dependencies:**
- US-VAL-034

**Priority:** Must Have

---

### US-VAL-036: Develop Control Plan for Approved AEO

**As a** Validation Team Member  
**I want to** develop a control plan for the approved AEO  
**So that** ongoing monitoring of the establishment's performance can be managed

**Acceptance Criteria:**
1. Validation Team begins preparing Control Plan once AEO Program Manager approves granting AEO status `[SRD Section 6.3.4.4.3]`
2. System sends notification to Validation Team to start preparing Control Plan `[SRD Section 6.3.4.4.2]`
3. Validation Team Member/Lead enters plan data in accordance with data dictionary "Control Plan Data" `[SRD Section 6.3.4.4.3, 5.10]`
4. System enables user to either: `[SRD Section 6.3.4.4.3]`
   - Create single control plan that covers all approved trade licenses under same AEO Authorization Request, OR
   - Develop individual control plans for each trade license separately
5. System does not allow single branch to be associated with multiple Control Plans `[SRD Section 6.3.4.4.3]`
6. If branch exists in a plan, it cannot be selected for new plan `[SRD Section 6.3.4.4.3]`
7. Control plan has same structure as SAQ so that Validation Team adds monitoring actions and all related details for each action under every leaf section of SAQ `[SRD Section 6.3.4.4.3]`
8. For each control action (assigned to leaf section in SAQ), system provides following fields: `[SRD Section 5.10]`
   - AEO Certificate No (multiple choice list, one at least mandatory) - identifier of AEO(s) related to this control plan
   - Action (multiple choices list, description of control action, mandatory)
   - The Address Related to the Action (single choice list from commercial establishment addresses, optional)
   - Address Type (text, auto-populated, mandatory)
   - Emirate (text, auto-populated, mandatory)
   - And other fields as specified in Control Plan Data dictionary
9. System does not support single control plan for head office and branches located in different emirates `[SRD Section 6.3.4.4.3]`
10. Branches in different emirates are always treated as separate entities `[SRD Section 6.3.4.4.3]`
11. Validation Team can save Control Plan as draft to continue work later
12. System tracks completion status of Control Plan for each leaf section

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Control plan development
- **SRD:** Section 6.3.4.4.3 "The Development of the Control Plan", Section 5.10 "Control Plan Data", Pages 88-91, 261-263

**Dependencies:**
- US-VAL-035 (AEO status must be approved)

**Priority:** Must Have

---

### US-VAL-037: Review and Approve Control Plan

**As a** Validation Team Lead  
**I want to** review and approve the control plan  
**So that** it can be used for ongoing monitoring of the AEO

**Acceptance Criteria:**
1. After Control Plan is prepared, Validation Team Lead reviews the plan `[SRD Section 6.3.4.4.3]`
2. Validation Team Lead can review:
   - All monitoring actions defined for each leaf section
   - Action details including responsible parties, frequencies, methods
   - Completeness of plan across all relevant SAQ sections
3. Validation Team Lead can make modifications before approving plan
4. Validation Team Lead can:
   - Edit any control action
   - Add additional monitoring actions
   - Remove or modify existing actions
   - Request changes from Validation Team members
5. Once satisfied with Control Plan, Validation Team Lead approves it `[SRD Section 6.3.4.4.3]`
6. Following issuance of certificate, responsibility for ongoing monitoring of AEO's performance is transferred to Key Account Managers Team Member `[SRD Section 6.3.4.4.3]`
7. During monitoring phase (post-certification), Control Plan remains editable by Key Account Managers Team—allowing modifications as necessary `[SRD Section 6.3.4.4.3]`
8. Validation Team retains read-only access for supervision purposes `[SRD Section 6.3.4.4.3]`
9. In event of re-validation of commercial establishment:
   - Responsibility of modifying Control Plan is transferred again to Validation Team `[SRD Section 6.3.4.4.3]`
   - Key Account Managers Team Member has read-only access till decision about AEO status is made
   - If decision is to continue AEO status: responsibility goes back to Key Account Managers Team Member
   - If decision is to suspend/revoke AEO status: responsibility remains with Validation Team
10. System records Control Plan approval in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Control plan approval and handover
- **SRD:** Section 6.3.4.4.3 "The Development of the Control Plan", Pages 261-263

**Dependencies:**
- US-VAL-036

**Priority:** Must Have

---

## Summary Tables

### Phase 3 User Stories Summary by Portal

| Portal | Epic | User Stories Count |
|--------|------|-------------------|
| **Local Customs Portal** | Initial Risk Assessment | 6 (US-VAL-001 to US-VAL-006) |
| **Local Customs Portal** | Validation Meetings Management | 5 (US-VAL-007 to US-VAL-011) |
| **AEO Portal** | Meeting Coordination | 2 (US-VAL-012 to US-VAL-013) |
| **Local Customs Portal** | On-Site Validation and Assessment File | 7 (US-VAL-014 to US-VAL-020) |
| **Local Customs Portal** | Assessment Report Generation | 4 (US-VAL-021 to US-VAL-024) |
| **AEO Portal** | Assessment Report Review and Response | 6 (US-VAL-025 to US-VAL-030) |
| **Local Customs Portal** | Final Decision and Control Plan | 7 (US-VAL-031 to US-VAL-037) |
| **TOTAL** | **7 Epics** | **37 User Stories** |

---

### Priority Distribution

| Priority | Count | Percentage |
|----------|-------|------------|
| Must Have | 37 | 100% |
| Should Have | 0 | 0% |
| Could Have | 0 | 0% |
| Won't Have | 0 | 0% |

---

### Business Rules Referenced

| Business Rule | Description | Referenced in User Stories |
|--------------|-------------|---------------------------|
| BR.26 | When scheduling meetings whether field visits, remote meetings, or a hearing session for an appeal request, the commercial establishment shall be notified of a specific period in advance, as defined in the system settings. The system will not allow scheduling any meeting with a date earlier than the defined notification period. | US-VAL-007, US-VAL-009 |

---

### Key Validation Process Statuses

| Status | Description | Portal |
|--------|-------------|--------|
| Initial Risk Assessment and Assessment Plan is Draft | Validation team reviewing SAQ to prepare initial risk assessment and assessment plan | Local Customs |
| Initial Risk Assessment and Assessment Plan Ready for Approval | All leaf sections completed for risk assessment | Local Customs |
| Initial Risk Assessment and Assessment Plan Approved | Validation team lead approved, ready to begin on-site validation | Local Customs |
| Commercial Establishment On-Site Validation | Meetings scheduled to verify compliance with AEO standards | Local Customs |
| Assessment File Ready for Approval | All findings, recommendations and remaining risks added for all sections | Local Customs |
| Assessment File Approved | Assessment file approved by validation team lead | Local Customs |
| Draft Assessment Report Shared | Draft assessment report shared with commercial establishment | Local/AEO |
| Compliance Improvement Plan Submitted | Commercial establishment submitted improvement plan | AEO/Local |
| Compliance Improvement Plan Returned | Plan returned to establishment for modifications | Local/AEO |
| Compliance Improvement Plan in Progress | Approved plan being executed by establishment | AEO |
| Verifying Compliance Plan Implementation | Establishment confirmed completion, awaiting customs verification | Local/AEO |
| AEO Status Under Review | AEO Program Manager reviewing for final decision | Local Customs |
| AEO Status Granted | Decision to grant AEO status confirmed | Local/AEO |
| AEO Status Rejected | Decision to reject AEO status | Local/AEO |

---

### Validation Process Workflow Diagram

```
Initial Risk Assessment Phase:
SAQ Approved → Initial Risk Assessment Draft → Ready for Approval → Approved
          ↓
Validation Meetings Phase:
Schedule Meetings → Commercial Establishment Confirms Dates → Conduct Meetings → Record Minutes
          ↓
On-Site Validation Phase:
Commercial Establishment On-Site Validation → Develop Assessment File
          ↓
Assessment File Development:
Add Remaining Risks → Add Findings → Add Recommendations → Assessment File Ready for Approval → Assessment File Approved
          ↓
Assessment Report Phase:
Generate Draft Assessment Report → Complete Report Content → Validation Team Lead Reviews → Share Draft with Establishment
          ↓
Commercial Establishment Review:
(Option A) Provide Comments → Return to Customs (back to Validation Team)
(Option B) Upload Compliance Improvement Plan (if required) → Approve Report
          ↓
Compliance Improvement Plan Phase (if required):
Validation Team Reviews Plan → Approve/Return Plan → Establishment Implements Plan → 
Confirms Implementation → Validation Team Verifies Implementation
          ↓
Final Decision Phase:
Validation Team Lead Submits Recommendation → AEO Program Manager Reviews → 
Final Decision: Approve/Reject/Request Clarifications
          ↓
(If Approved)
Control Plan Development:
Validation Team Develops Control Plan → Validation Team Lead Approves → 
Transfer to Key Account Managers Team → Certificate Issuance Process
```

---

## Traceability Matrix

### Source Document References

| User Story | BRD Reference | SRD Reference | Page Numbers |
|------------|---------------|---------------|--------------|
| US-VAL-001 | Initial risk assessment process | Section 6.3.4.2 | 246-247 |
| US-VAL-002 | Risk assessment methodology | Section 6.3.4.2.1, 5.6 | 71-75, 247-249 |
| US-VAL-003 | Assessment plan preparation | Section 6.3.4.2.2, 5.6 | 71-75, 249-250 |
| US-VAL-004 | Reference documentation | Section 6.3.4.2.3, 5.6 | 71-75, 250 |
| US-VAL-005 | Completion tracking | Section 6.3.4.2.4, 6.3.4.2.6, 6.3.4.2.7 | 250-252 |
| US-VAL-006 | Initial risk assessment approval | Section 6.3.4.2.5, 6.3.4.2.6, 6.3.4.2.7 | 251-252 |
| US-VAL-007 | Meeting scheduling | Section 6.3.4.3.1, 5.7, BR.26 | 75-78, 252-254 |
| US-VAL-008 | Shared calendar management | Section 6.3.4.3.1 | 252-254 |
| US-VAL-009 | Meeting cancellation/rescheduling | Section 6.3.4.3.1, 5.7, 6.2.5.6 | 75-78, 201-202, 252-254 |
| US-VAL-010 | Meeting minutes | Section 6.3.4.3.1, 5.7 | 75-78, 252-254 |
| US-VAL-011 | Official meeting letter | Section 6.3.4.3.1 | 252-254 |
| US-VAL-012 | Meeting invitation response | Section 6.2.5.1, 6.3.4.3.1, 6.3.4.4.5, 6.2.5.6 | 192-193, 201-202, 252-254, 268-269 |
| US-VAL-013 | Meeting schedule visibility | Section 6.2.5.1, 6.3.4.3.1 | 192-193, 252-254 |
| US-VAL-014 | On-site validation execution | Section 6.3.4.3, 6.3.4.4.4 | 252-256, 263-264 |
| US-VAL-015 | Assessment file with remaining risks | Section 6.3.4.3.2, 5.8 | 78-81, 254-256 |
| US-VAL-016 | Findings documentation | Section 6.3.4.3.2, 5.8 | 78-81, 254-256 |
| US-VAL-017 | Recommendations documentation | Section 6.3.4.3.2, 5.8, 6.3.4.3.4 | 78-81, 254-257 |
| US-VAL-018 | Internal comments during validation | Section 6.3.4.3.2 | 254-256 |
| US-VAL-019 | Assessment file completion | Section 6.3.4.3.2, 6.3.4.4.4, 6.3.4.4.5 | 254-256, 263-264, 268-269 |
| US-VAL-020 | Assessment file approval | Section 6.3.4.3.3, 6.3.4.4.4 | 255-256, 263-264 |
| US-VAL-021 | Assessment report generation | Section 6.3.4.3.4, 5.9 | 81-88, 256-257 |
| US-VAL-022 | Assessment report content | Section 6.3.4.3.4 | 256-257 |
| US-VAL-023 | Content selection for sharing | Section 6.3.4.3.5 | 257-258 |
| US-VAL-024 | Assessment report sharing | Section 6.3.4.3.5, 6.3.4.3.6, 6.3.4.4.4, 6.2.5.2, 6.2.5.6 | 193-194, 201-202, 257-258, 263-264 |
| US-VAL-025 | Assessment report review | Section 6.2.5.2, 6.2.5.6 | 193-194, 201-202 |
| US-VAL-026 | Comments on assessment report | Section 6.2.5.2, 6.2.5.6, 6.3.4.4.5 | 193-194, 201-202, 268-269 |
| US-VAL-027 | Compliance Improvement Plan upload | Section 6.2.5.2, 5.9 | 86-87, 193-194 |
| US-VAL-028 | Assessment report approval | Section 6.2.5.2, 6.2.5.6, 6.3.4.4.5 | 193-194, 201-202, 268-269 |
| US-VAL-029 | Plan extension request | Section 6.3.4.4, 5.9 | 87, 259 |
| US-VAL-030 | Plan implementation confirmation | Section 6.3.4.4.1, 5.9 | 87-88, 259-260 |
| US-VAL-031 | Returned report review | Section 6.3.4.3.6, 6.3.4.4.5 | 258, 268-269 |
| US-VAL-032 | Compliance plan review | Section 6.3.4.4.1, 6.2.5.2, 6.2.5.6 | 193-194, 201-202, 259-260 |
| US-VAL-033 | Plan implementation verification | Section 6.3.4.4.1 | 259-260 |
| US-VAL-034 | Final recommendation submission | Section 6.3.4.4.1, 6.3.4.4.2, 6.3.4.4.5 | 259-261, 268-269 |
| US-VAL-035 | Final AEO status decision | Section 6.3.4.4.2, 6.3.4.4.4, 6.3.4.4.5 | 260-261, 263-268, 268-269 |
| US-VAL-036 | Control plan development | Section 6.3.4.4.3, 5.10 | 88-91, 261-263 |
| US-VAL-037 | Control plan approval | Section 6.3.4.4.3 | 261-263 |

---

## Next Steps

**Phase 3 is now complete.** The next phase will be:

**Phase 4: AEO Certification & Post-Certification Management**
- Estimated 20-25 user stories covering:
  - Certificate Issuance Process
  - Benefits Management
  - Key Account Management
  - Control Plan Execution and Monitoring
  - Performance Monitoring
  - Re-validation Process
  - Certificate Suspension and Revocation
  - Appeals Management

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 07, 2025 | AEO Project Team | Initial version - Phase 3 Validation & Risk Assessment User Stories |

---

**End of Phase 3 User Stories Document**
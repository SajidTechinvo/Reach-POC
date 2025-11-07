# AEO Management System - User Stories
## Phase 4: AEO Certification & Post-Certification Management

**Document Version:** 1.0  
**Date:** November 07, 2025  
**Project:** Authorized Economic Operator (AEO) Management System  
**Source Documents:**  
- Business Requirements Document (BRD) V1.11  
- System Requirements Document (SRD) V1.2.5

---

## Document Overview

### Purpose
This document contains detailed user stories for **Phase 4: AEO Certification & Post-Certification Management** of the AEO Management System. All user stories are directly derived from the Business Requirements Document (BRD V1.11) and System Requirements Document (SRD V1.2.5) without assumptions.

### Scope
Phase 4 covers the complete certification and post-certification lifecycle including:
- **Certificate Issuance Process** (Federal and Local Customs)
- **Benefits Management** (Federal and Local Customs)
- **Key Account Management** (Local Customs)
- **Control Plan Execution and Monitoring** (Local Customs)
- **Performance Monitoring** (Local Customs)
- **Re-validation Process** (Local Customs)
- **Certificate Suspension and Revocation** (Local Customs)
- **Appeals Management** (Local Customs, Federal Customs, and AEO Portal)

### User Roles

#### Federal Customs Portal
- **Senior Federal Administrator:** Issues AEO certificates, manages federal-level operations
- **Federal Administrator:** Reviews and processes escalated appeal requests

#### Local Customs Portal
- **AEO Program Manager:** Assigns Key Account Managers Team, makes decisions on suspension/revocation/continuation, approves revalidation requests, decides on appeal requests
- **Key Account Manager:** Monitors AEO performance, manages control plan, logs violations, schedules monitoring meetings, raises revalidation requests
- **Validation Team Member/Lead:** Conducts re-assessment and re-validation processes
- **Appeals Officer:** Reviews appeal requests, schedules hearing sessions, provides recommendations

#### AEO Portal (Commercial Establishment)
- **Commercial Establishment Account Manager:** Views and downloads certificates, submits appeal requests, confirms monitoring meeting dates
- **Assessment Report Editor:** Participates in revalidation process when required

---

## Table of Contents
1. [Federal Customs Portal - Key Account Team Assignment and Benefits](#federal-customs-key-account-assignment)
2. [Federal Customs Portal - Certificate Issuance](#federal-customs-certificate-issuance)
3. [AEO Portal - Certificate Viewing and Management](#aeo-portal-certificate-viewing)
4. [Local Customs Portal - Key Account Management](#local-customs-key-account-management)
5. [Local Customs Portal - Control Plan Monitoring](#local-customs-control-plan-monitoring)
6. [Local Customs Portal - Re-validation Process](#local-customs-revalidation)
7. [Local Customs Portal - Suspension and Revocation](#local-customs-suspension-revocation)
8. [AEO Portal - Appeals Submission](#aeo-portal-appeals-submission)
9. [Local Customs Portal - Appeals Management](#local-customs-appeals-management)
10. [Federal Customs Portal - Appeals Escalation](#federal-customs-appeals-escalation)

---

<a name="federal-customs-key-account-assignment"></a>
## 1. Federal Customs Portal - Key Account Team Assignment and Benefits

### Epic: AEO Certification Process
**Goal:** Enable AEO Program Manager to assign Key Account Managers Team and manage benefits for certified AEOs

---

### US-CERT-001: Assign Key Account Managers Team

**As an** AEO Program Manager  
**I want to** assign the Key Account Managers Team to certified commercial establishments  
**So that** ongoing monitoring and support can be provided to AEOs

**Acceptance Criteria:**
1. After AEO Program Manager approves granting AEO status to commercial establishment, system allows assignment of Key Account Managers Team `[SRD Section 6.3.5]`
2. System provides interface to select and assign one or more Key Account Managers to the commercial establishment `[SRD Section 6.3.5]`
3. When Key Account Managers Team is assigned, system automatically triggers following actions: `[SRD Section 6.3.5]`
   - System automatically assigns default benefits group to commercial establishment(s)
   - Request to issue certificate(s) is sent to general department of customs at federal authority
4. System allows viewing list of available Key Account Managers with their current workload
5. System allows assigning multiple Key Account Managers to same commercial establishment
6. If more than one Key Account Manager is assigned to commercial establishment, all have same privileges on this establishment `[SRD Section 6.3.6.1]`
7. If "AEO Authorization Request" contains headquarter and other branches, system allows assigning different Key Account Managers to different trade licenses
8. System records Key Account Managers Team assignment in audit trail
9. System sends notification to assigned Key Account Managers about their new assignment
10. System changes status to "Certificate Under Issuance" after Key Account Managers Team assignment

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Key Account Manager assignment process
- **SRD:** Section 6.3.5 "AEO Certification Process", Section 6.3.6.1 "Key Account Management", Pages 269-272

**Dependencies:**
- US-VAL-035 (Final AEO status decision)

**Priority:** Must Have

---

### US-CERT-002: Manage Benefits Assignment

**As a** Key Account Manager  
**I want to** manage benefits packages assigned to certified AEOs  
**So that** appropriate benefits are granted based on commercial establishment's profile

**Acceptance Criteria:**
1. When Key Account Managers Team is assigned, system automatically assigns default benefits group to commercial establishment(s) `[SRD Section 6.3.5]`
2. Key Account Manager can view currently assigned benefits package for commercial establishment
3. Key Account Manager can change benefits package that will be assigned to commercial establishment(s) `[SRD Section 6.3.5]`
4. If "AEO Authorization Request" contains headquarter and other branches, system allows assigning different groups of benefits to approved trade licenses `[SRD Section 6.3.5]`
5. System provides list of available benefits groups to select from
6. Key Account Manager can view details of each benefits group before assignment
7. System validates that selected benefits group is appropriate for commercial establishment's type
8. System allows Key Account Manager to modify benefits assignment before certificate issuance
9. System records all benefits assignment changes in audit trail
10. Benefits become active once certificate is issued

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Benefits management
- **SRD:** Section 6.3.5 "AEO Certification Process", Pages 269-270

**Dependencies:**
- US-CERT-001

**Priority:** Must Have

---

<a name="federal-customs-certificate-issuance"></a>
## 2. Federal Customs Portal - Certificate Issuance

### Epic: Certificate Issuance
**Goal:** Enable Federal Administrator to issue AEO certificates to approved commercial establishments

---

### US-CERT-003: Process Certificate Issuance Request

**As a** Senior Federal Administrator  
**I want to** process certificate issuance requests  
**So that** AEO certificates can be officially issued to approved commercial establishments

**Acceptance Criteria:**
1. After Key Account Managers Team is assigned, request to issue certificate(s) is sent to general department of customs at federal authority `[SRD Section 6.3.5]`
2. Senior Federal Administrator receives notification about certificate issuance request
3. System displays list of pending certificate issuance requests in Federal Customs Portal
4. Senior Federal Administrator can view complete details of each request including:
   - Commercial establishment information
   - Approved trade licenses
   - AEO authorization request details
   - Assessment report summary
   - Assigned benefits package
5. If "AEO Authorization Request" includes multiple branches, system allows issuing AEO certificate for each approved branch separately `[SRD Section 6.2.6.1]`
6. System allows issuing AEO certificate for each approved trade license separately `[SRD Section 6.2.6.1]`
7. For each certificate to be issued, Senior Federal Administrator can:
   - Review all required information
   - Verify accuracy of data
   - Generate certificate document
8. System provides certificate template with all required fields automatically populated
9. Senior Federal Administrator can preview certificate before final issuance

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Certificate issuance process
- **SRD:** Section 6.3.5 "AEO Certification Process", Section 6.2.6.1 "Issuance of Certificate(s)", Pages 203, 269-270

**Dependencies:**
- US-CERT-001

**Priority:** Must Have

---

### US-CERT-004: Issue AEO Certificate

**As a** Senior Federal Administrator  
**I want to** officially issue AEO certificates  
**So that** commercial establishments receive their certification

**Acceptance Criteria:**
1. Senior Federal Administrator can issue certificate(s) for approved commercial establishment `[SRD Section 6.3.5]`
2. When certificate is issued, system changes status from "Certificate Under Issuance" to "AEO Certified" `[SRD Section 6.2.6.2, 6.3.5.1]`
3. System generates unique certificate number for each certificate
4. Certificate includes following information:
   - Commercial establishment name
   - Trade license number
   - Certificate number
   - Issuance date
   - Expiration date (calculated as two years from issuance date) `[BR.17]`
   - Assigned benefits
   - Federal authority seal and signature
5. If multiple trade licenses are approved, system issues separate certificate for each trade license
6. System stores issued certificate(s) in secure document repository
7. System sends notification to following parties when certificate is issued: `[SRD Section 6.2.6.3, 6.3.5.2]`
   - Commercial establishment account manager (via email and AEO Portal)
   - Key Account Managers Team (via email and Local Customs AEO management portal)
   - Local customs departments (via email and Local customs AEO management portal)
8. System records certificate issuance in audit trail `[SRD Section 6.2.6.2, 6.3.5.1]`
9. Certificate becomes available for viewing and download in AEO Portal `[SRD Section 6.2.6.1]`
10. System updates commercial establishment status to "AEO Certified"

**Business Rules:**
- BR.17: The license expiration date is calculated automatically as two years from the issuance date, with the ability to modify the expiration date through the system

**Traceability:**
- **BRD:** Certificate issuance
- **SRD:** Section 6.3.5 "AEO Certification Process", Section 6.2.6.1 "Issuance of Certificate(s)", Section 6.2.6.2 "Statuses of AEO Certificate", Section 6.2.6.3 "Notifications", Section 6.3.5.1 "Statuses of AEO", Section 6.3.5.2 "Notifications", Pages 203-205, 270-271

**Dependencies:**
- US-CERT-003

**Priority:** Must Have

---

<a name="aeo-portal-certificate-viewing"></a>
## 3. AEO Portal - Certificate Viewing and Management

### Epic: Certificate Management
**Goal:** Enable commercial establishments to view and manage their AEO certificates

---

### US-CERT-005: View Certificate Status

**As a** Commercial Establishment Account Manager  
**I want to** view the status of my AEO certificate  
**So that** I can track the issuance process and know when certificate is ready

**Acceptance Criteria:**
1. Commercial establishment can view certificate status in AEO Portal
2. System displays following statuses as applicable: `[SRD Section 6.2.6.2]`
   - **AEO Certificate Under Issuance:** When senior federal administrator receives AEO request to issue certificate but certificate is not issued yet
   - **AEO Certified:** When certificate has been issued
   - **AEO Status Suspended:** When AEO certificate has been suspended temporarily
   - **AEO Status Revoked:** When AEO certificate has been revoked permanently
   - **AEO Status Cancelled:** When commercial establishment cancels the certificate
3. Commercial establishment receives notification when status changes:
   - Certificate Under Issuance: When senior federal administrator receives AEO request `[SRD Section 6.2.6.3]`
   - AEO Certified: When certificate is issued `[SRD Section 6.2.6.3]`
   - AEO Status Suspended: When AEO status is suspended `[SRD Section 6.2.6.3]`
   - AEO Status Revoked: When AEO status is revoked `[SRD Section 6.2.6.3]`
   - AEO Status Under Review: When AEO program manager starts reviewing AEO status `[SRD Section 6.2.5.6]`
4. Notifications are sent via email and AEO Portal `[SRD Section 6.2.6.3]`
5. System displays status history showing all status changes with timestamps
6. Commercial establishment account manager receives all notifications

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Certificate status tracking
- **SRD:** Section 6.2.6.2 "Statuses of AEO Certificate", Section 6.2.6.3 "Notifications", Pages 203-205

**Dependencies:**
- US-CERT-004

**Priority:** Must Have

---

### US-CERT-006: View and Download AEO Certificate

**As a** Commercial Establishment Account Manager  
**I want to** view and download my AEO certificate  
**So that** I can use it for business purposes and keep records

**Acceptance Criteria:**
1. After commercial establishment is approved for granting AEO status and certificate is issued, commercial establishment is notified that certificate is available `[SRD Section 6.2.6.1]`
2. Certificate(s) become available for viewing and download through AEO Portal once issued `[SRD Section 6.2.6.1]`
3. Commercial establishment can view list of all issued certificates (if multiple trade licenses)
4. For each certificate, system displays:
   - Certificate number
   - Trade license number
   - Issuance date
   - Expiration date
   - Current status (Active, Suspended, Revoked, Cancelled)
5. Commercial establishment can view full certificate in PDF format
6. System provides "Download" button to download certificate(s)
7. Downloaded certificate is in official PDF format with all security features
8. System maintains access log of certificate views and downloads
9. If multiple certificates were issued (for different trade licenses), each certificate is available separately
10. System allows printing of certificate directly from portal

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Certificate access and download
- **SRD:** Section 6.2.6.1 "Issuance of Certificate(s)", Page 203

**Dependencies:**
- US-CERT-004

**Priority:** Must Have

---

### US-CERT-007: Request Certificate Cancellation

**As a** Commercial Establishment Account Manager  
**I want to** request cancellation of my AEO certificate  
**So that** I can voluntarily withdraw from the AEO program if needed

**Acceptance Criteria:**
1. Commercial establishment can submit request to cancel AEO certificate through AEO Portal
2. System provides cancellation request form with following fields:
   - Trade license(s) for which cancellation is requested
   - Reason for cancellation
   - Supporting documents (optional)
   - Effective date requested
3. System validates that certificate is in "AEO Certified" or "AEO Status Suspended" status before allowing cancellation request
4. Commercial establishment must confirm cancellation request before submission
5. Once submitted, system sends notification to Key Account Manager and AEO Program Manager
6. System changes status to "Cancellation Requested" pending approval
7. After approval by AEO Program Manager, system changes status to "AEO Status Cancelled" `[SRD Section 6.2.6.2]`
8. Status "AEO Status Cancelled" is final status `[SRD Section 6.2.6.2]`
9. System sends notification to commercial establishment when cancellation is processed
10. System records cancellation request and approval in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Certificate cancellation
- **SRD:** Section 6.2.6.2 "Statuses of AEO Certificate", Pages 203-205

**Dependencies:**
- US-CERT-006

**Priority:** Must Have

---

<a name="local-customs-key-account-management"></a>
## 4. Local Customs Portal - Key Account Management

### Epic: Key Account Management
**Goal:** Enable Key Account Managers to monitor and manage certified AEOs

---

### US-CERT-008: View AEO Summary and Dashboard

**As a** Key Account Manager  
**I want to** view summary dashboard of AEOs assigned to me  
**So that** I can effectively monitor their performance and compliance

**Acceptance Criteria:**
1. Key Account Manager can access dashboard showing all AEOs assigned to them `[SRD Section 6.3.6.1]`
2. For each AEO, system displays summary information including: `[SRD Section 6.3.6.1]`
   - Last monitoring actions that were conducted
   - Upcoming monitoring actions, including responsible team member assigned to each action
   - Date of last validation/revalidation conducted for the AEO
   - Date of upcoming revalidation that will be conducted by Validation Team
3. Dashboard provides at-a-glance view of:
   - Total number of AEOs assigned
   - AEOs with overdue monitoring actions
   - AEOs with upcoming monitoring actions in next 30 days
   - AEOs requiring revalidation
   - AEOs with logged violations
4. System provides filtering and sorting options for AEO list:
   - By AEO status
   - By last monitoring date
   - By upcoming actions
   - By trade license type
5. Key Account Manager can click on any AEO to view detailed profile
6. System sends reminders to Key Account Manager when date of monitoring action is approaching `[SRD Section 6.3.6.1]`
7. Reminder timing is configured through system settings `[SRD Section 6.3.6.1]`
8. Dashboard updates in real-time as actions are completed

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Key Account Manager dashboard
- **SRD:** Section 6.3.6.1 "Key Account Management", Pages 271-272

**Dependencies:**
- US-CERT-001

**Priority:** Must Have

---

### US-CERT-009: View Commercial Establishment Profile

**As a** Key Account Manager  
**I want to** view complete profile of commercial establishment  
**So that** I have all necessary information to perform my monitoring duties

**Acceptance Criteria:**
1. Key Account Manager can view complete commercial establishment profile and all related information `[SRD Section 6.3.6.1]`
2. Profile includes following information: `[SRD Section 6.3.6.1]`
   - AEO Authorization Request details
   - Self-Assessment Questionnaire (SAQ)
   - Assessment file
   - Assessment report
   - AEO certificate(s)
   - Assigned benefits
   - Control plan
   - Monitoring history
   - Violation history
   - Communication history
3. Key Account Manager can access and download all documents associated with commercial establishment
4. System provides tabbed interface or sections to organize information logically
5. Profile shows current AEO status and status history
6. Key Account Manager can view authorized contact persons information
7. System displays trade license details including:
   - Trade license number
   - Expiration date
   - Activities covered
   - Branch information (if applicable)
8. Profile includes timeline view showing key events in AEO lifecycle
9. Key Account Manager can add internal notes to profile (visible only to customs)

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Commercial establishment profile access
- **SRD:** Section 6.3.6.1 "Key Account Management", Pages 271-272

**Dependencies:**
- US-CERT-008

**Priority:** Must Have

---

### US-CERT-010: Manage Authorized Contact Persons

**As a** Key Account Manager  
**I want to** manage authorized contact persons information for AEO  
**So that** contact information remains current for effective communication

**Acceptance Criteria:**
1. Key Account Manager can view list of authorized contact persons for commercial establishment `[SRD Section 6.3.6.1]`
2. For each contact person, system displays: `[SRD Section 5.11]`
   - Name (Arabic and English)
   - Email
   - Phone number
   - Alternative mobile number (if provided)
   - Fixed landline number (if provided)
   - Job title
3. Key Account Manager can update contact person information to keep data current `[SRD Section 6.3.6.1]`
4. System validates email format and phone number format
5. System requires mandatory fields to be completed:
   - Name (Arabic) - Arabic letters only
   - Name (English) - English letters only
   - Email
   - Phone number
   - Job title
6. Key Account Manager can add new authorized contact persons
7. Key Account Manager can deactivate contact persons who are no longer authorized
8. System maintains history of all changes to contact persons
9. Changes to contact persons are recorded in audit trail
10. System validates that at least one active authorized contact person exists at all times

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Contact person management
- **SRD:** Section 6.3.6.1 "Key Account Management", Section 5.11 "Designated Contact Person Representing the Commercial Establishment Data", Pages 78-79, 271-273

**Dependencies:**
- US-CERT-009

**Priority:** Must Have

---

### US-CERT-011: Communicate with Commercial Establishment

**As a** Key Account Manager  
**I want to** communicate with commercial establishment through the system  
**So that** all communications are documented and accessible

**Acceptance Criteria:**
1. Key Account Manager can initiate conversations with commercial establishment through system `[SRD Section 6.3.6.1, 6.3.8]`
2. During certificate issuance phase and after, messages from commercial establishment are directed to Key Account Manager `[SRD Section 6.3.8]`
3. After certificate issuance phase, communication is limited to Key Account Manager only `[SRD Section 6.3.8]`
4. System provides messaging interface within commercial establishment profile
5. Key Account Manager can: `[SRD Section 6.3.8]`
   - View all conversations with commercial establishment
   - Open existing conversation
   - Write reply
   - Attach documents to messages (if necessary)
6. Each conversation is assigned status indicating which party is expected to take next action: `[SRD Section 6.3.8]`
   - "Waiting for Customs Response" - when commercial establishment sends message
   - "Establishment Action Required" - when customs sends message
7. Key Account Manager manages conversation status and can close conversation once matter is resolved `[SRD Section 6.3.8]`
8. All correspondence between commercial establishment and customs is saved in system `[SRD Section 6.3.8]`
9. Key Account Manager can view messages that were previously exchanged during earlier phases (e.g., with administrator or validation team) `[SRD Section 6.3.8]`
10. Upon entering "Conversations" section, all conversations appear with most recent messages displayed at top `[SRD Section 6.3.8]`
11. Key Account Manager receives notification via email and Local Customs AEO management portal when receiving new reply from commercial establishment `[SRD Section 6.3.8, 6.3.8.1]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Communication management
- **SRD:** Section 6.3.6.1 "Key Account Management", Section 6.3.8 "Communication with the Commercial Establishment", Section 6.3.8.1 "Notifications", Pages 271-273, 292-294

**Dependencies:**
- US-CERT-009

**Priority:** Must Have

---

### US-CERT-012: Log Violations

**As a** Key Account Manager  
**I want to** log violations against commercial establishment  
**So that** compliance issues are documented and can be addressed

**Acceptance Criteria:**
1. Key Account Manager can log reported violation against commercial establishment `[SRD Section 6.3.6.1]`
2. System provides violation logging form with following fields:
   - Violation type (from system lookup)
   - Violation date
   - Detailed description
   - Severity level
   - Source of violation report (monitoring action, complaint, customs operation, etc.)
   - Supporting documents (optional)
   - Recommended action
3. System allows selecting violation type from predefined violations lookup managed by Federal Administrator
4. Key Account Manager can attach evidence documents to violation record
5. System automatically links violation to relevant monitoring action if violation was discovered during monitoring
6. Once violation is logged, system sends notification to:
   - AEO Program Manager
   - Other Key Account Managers assigned to same AEO
   - Commercial establishment (if required based on violation severity)
7. Logged violations appear in commercial establishment profile
8. System maintains violation history showing all logged violations with current status
9. Key Account Manager can update violation status:
   - Open
   - Under Review
   - Resolved
   - Escalated
10. System records all violation logging and updates in audit trail
11. Violations are considered in revalidation decisions

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Violation logging
- **SRD:** Section 6.3.6.1 "Key Account Management", Pages 271-273

**Dependencies:**
- US-CERT-009

**Priority:** Must Have

---

<a name="local-customs-control-plan-monitoring"></a>
## 5. Local Customs Portal - Control Plan Monitoring

### Epic: Control Plan Execution and Monitoring
**Goal:** Enable Key Account Managers to execute and manage control plans for certified AEOs

---

### US-CERT-013: View and Manage Control Plan

**As a** Key Account Manager  
**I want to** view and manage control plan for AEO  
**So that** monitoring activities are properly planned and executed

**Acceptance Criteria:**
1. Following issuance of certificate, responsibility for ongoing monitoring of AEO's performance is transferred to Key Account Manager `[US-VAL-037, SRD Section 6.3.4.4.3]`
2. Key Account Manager can access control plan for assigned AEO
3. Control plan displays all monitoring actions organized by SAQ sections/leaf sections
4. For each monitoring action, system displays: `[SRD Section 5.10]`
   - Action description
   - Monitoring method (document review, on-site inspection, remote meeting, etc.)
   - Frequency (daily, weekly, monthly, quarterly, annually, etc.)
   - Responsible Key Account Manager
   - Last execution date
   - Next scheduled date
   - Status (Pending, Completed, Overdue)
5. During monitoring phase (post-certification), control plan remains editable by Key Account Manager `[US-VAL-037, SRD Section 6.3.4.4.3]`
6. Key Account Manager can modify control plan once needed: `[SRD Section 6.3.6.1]`
   - Add new control actions
   - Edit existing control actions
   - Remove control actions
   - Re-assign control action to different Key Account Manager (along with justification)
7. System validates that control plan covers all critical areas from assessment
8. All modifications to control plan are recorded in audit trail with justification
9. System sends notification to affected Key Account Manager when actions are re-assigned
10. Validation Team retains read-only access to control plan for supervision purposes `[US-VAL-037, SRD Section 6.3.4.4.3]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Control plan management
- **SRD:** Section 6.3.4.4.3 "Control Plan Development, Approval and Modification", Section 6.3.6.1 "Key Account Management", Section 5.10 "Control Plan Data", Pages 88-91, 261-263, 271-273

**Dependencies:**
- US-VAL-037 (Control plan approval)

**Priority:** Must Have

---

### US-CERT-014: Execute Monitoring Actions

**As a** Key Account Manager  
**I want to** execute monitoring actions from control plan  
**So that** AEO compliance is continuously verified

**Acceptance Criteria:**
1. Key Account Manager can view list of monitoring actions assigned to them
2. System displays upcoming monitoring actions with due dates
3. System sends reminders when date of monitoring action is approaching `[SRD Section 6.3.6.1]`
4. Reminder timing is configured through system settings
5. For each monitoring action, Key Account Manager can:
   - View action details
   - Access relevant documents and history
   - Conduct monitoring activity (document review, schedule meeting, etc.)
   - Record findings and observations
   - Upload evidence/documents
6. After conducting monitoring action, Key Account Manager confirms completion and adds remarks `[SRD Section 6.3.6.1]`
7. System requires following information upon completion:
   - Completion date
   - Findings/observations
   - Compliance status (Compliant, Minor issue, Major issue, Non-compliant)
   - Remarks
   - Supporting documents (if applicable)
8. System automatically calculates next scheduled date based on action frequency
9. If issues are identified during monitoring, Key Account Manager can:
   - Log violation (if severe)
   - Request corrective action from AEO
   - Escalate to AEO Program Manager
   - Initiate revalidation (if necessary)
10. System records all monitoring action executions in audit trail
11. Completed monitoring actions appear in AEO's monitoring history

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Monitoring action execution
- **SRD:** Section 6.3.6.1 "Key Account Management", Pages 271-273

**Dependencies:**
- US-CERT-013

**Priority:** Must Have

---

### US-CERT-015: Schedule Monitoring Meetings

**As a** Key Account Manager  
**I want to** schedule meetings to perform monitoring actions  
**So that** on-site or remote monitoring can be conducted effectively

**Acceptance Criteria:**
1. Key Account Manager can schedule meetings to perform monitoring actions `[SRD Section 6.3.6.1]`
2. Monitoring meetings follow same process as validation meetings `[SRD Section 6.3.6.1]`
3. System provides meeting scheduling interface with following fields:
   - Meeting title
   - Purpose of meeting
   - Meeting type (on-site, remote, hybrid)
   - Date and time
   - Duration
   - Location (if on-site)
   - Meeting link (if remote)
   - Attendees from Key Account Manager side
   - Required attendees from commercial establishment
4. System validates that meeting is scheduled with adequate advance notice as defined in system settings `[BR.26]`
5. System will not allow scheduling any meeting with date earlier than defined notification period `[BR.26]`
6. Once meeting is scheduled, system sends invitation to:
   - Commercial establishment authorized contact persons (via email and AEO Portal)
   - Key Account Managers team members involved
7. Commercial establishment must confirm or request rescheduling of meeting
8. Once commercial establishment confirms meeting date, it is reflected in calendar of Key Account Managers Team `[SRD Section 6.3.6.1]`
9. System sends reminders before meeting based on configured schedule
10. Key Account Manager can add agenda and attach documents to meeting invitation
11. After meeting, Key Account Manager can record meeting minutes and outcomes
12. Meeting scheduling and attendance are recorded in audit trail

**Business Rules:**
- BR.26: When scheduling meetings whether field visits, remote meetings, or a hearing session for an appeal request, the commercial establishment shall be notified of a specific period in advance, as defined in the system settings. The system will not allow scheduling any meeting with a date earlier than the defined notification period.

**Traceability:**
- **BRD:** Monitoring meeting scheduling
- **SRD:** Section 6.3.6.1 "Key Account Management", Pages 271-273

**Dependencies:**
- US-CERT-013

**Priority:** Must Have

---

### US-CERT-016: Amend Commercial Establishment Profile

**As a** Key Account Manager  
**I want to** amend commercial establishment profile to reflect critical events  
**So that** profile information remains accurate and current

**Acceptance Criteria:**
1. Key Account Manager can amend commercial establishment profile to reflect critical events `[SRD Section 6.3.6.1]`
2. Critical events that can be recorded include:
   - Trade license renewal
   - Trade license cancellation
   - Trade license suspension
   - Changes in activities in supply chain
   - Changes in business operations
   - Changes in ownership/management
   - Mergers or acquisitions
3. System provides interface to record each type of critical event
4. For trade license changes, Key Account Manager can:
   - Update license status
   - Update expiration date
   - Add new licenses
   - Mark licenses as inactive
5. For supply chain activity changes, Key Account Manager can:
   - Add new activities
   - Remove discontinued activities
   - Modify scope of existing activities
6. System validates that all changes are properly documented
7. Key Account Manager must provide justification for significant changes
8. System sends notification to AEO Program Manager when critical changes are recorded
9. Critical changes may trigger need for revalidation
10. All profile amendments are recorded in audit trail with timestamp and justification
11. Commercial establishment is notified when profile changes affect their AEO status or benefits

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Profile amendment
- **SRD:** Section 6.3.6.1 "Key Account Management", Pages 271-273

**Dependencies:**
- US-CERT-009

**Priority:** Must Have

---

<a name="local-customs-revalidation"></a>
## 6. Local Customs Portal - Re-validation Process

### Epic: Re-validation Process
**Goal:** Enable periodic re-validation of AEOs to ensure continued compliance

---

### US-CERT-017: Raise Revalidation Request

**As a** Key Account Manager  
**I want to** raise revalidation request to AEO Program Manager  
**So that** AEO's continued compliance can be verified

**Acceptance Criteria:**
1. Key Account Manager can raise revalidation request to AEO Program Manager along with justification `[SRD Section 6.3.6.1, 6.3.6.2]`
2. Revalidation process begins for one of following reasons: `[SRD Section 6.3.6.2]`
   - Key Account Manager submits request to AEO program manager for revalidation of commercial establishment, including reasons for request
   - Periodic revalidation is triggered based on system settings calculated from date of last validation process
3. Periodic revalidation must be conducted within maximum of five (5) years from last validation `[BR.23]`
4. When periodic revalidation is due, system notifies Key Account Manager to initiate revalidation `[SRD Section 6.3.6.2]`
5. System provides revalidation request form with following fields:
   - Reason for revalidation (from dropdown)
   - Detailed justification
   - Scope of revalidation (full or partial)
   - Areas of concern (if partial revalidation)
   - Priority level
   - Supporting documents
6. Common reasons for revalidation include:
   - Periodic review (5-year cycle)
   - Significant violations logged
   - Major changes in business operations
   - Changes in supply chain activities
   - Complaints received
   - Risk indicators identified
7. Once request is submitted, system sends notification to AEO Program Manager
8. System changes status to "Revalidation Request Submitted" pending approval
9. Request includes link to commercial establishment profile and monitoring history
10. System records revalidation request in audit trail

**Business Rules:**
- BR.23: The periodic revalidation process must be conducted within a maximum of five (5) years from the last validation to ensure the commercial establishment continues to meet the AEO program standards.

**Traceability:**
- **BRD:** Revalidation request
- **SRD:** Section 6.3.6.1 "Key Account Management", Section 6.3.6.2 "The Re-Validation Process", Pages 271-274

**Dependencies:**
- US-CERT-008

**Priority:** Must Have

---

### US-CERT-018: Review and Approve Revalidation Request

**As an** AEO Program Manager  
**I want to** review and approve revalidation requests  
**So that** appropriate revalidation activities are initiated

**Acceptance Criteria:**
1. AEO Program Manager receives notification when revalidation request is submitted
2. AEO Program Manager can view revalidation request with all details including:
   - Commercial establishment information
   - Reason for revalidation
   - Detailed justification
   - Current AEO status
   - Monitoring history
   - Violation history
   - Last validation/revalidation date
3. Upon receiving request from Key Account Manager, AEO Program Manager can take one of following actions: `[SRD Section 6.3.6.2]`
   - **Approve:** Assigns re-validation team to commercial establishment
   - **Return:** Returns request for further clarifications (with remarks)
   - **Reject:** Rejects request along with justification
4. If approved, AEO Program Manager selects validation team members to form revalidation team
5. System validates that selected team members are available
6. Revalidation team must consist of at least two members: team lead and team member `[BR.25]`
7. Once revalidation team is assigned, system sends notification to:
   - Assigned validation team members
   - Key Account Manager who raised request
   - Commercial establishment (if necessary)
8. System changes status to "Revalidation Team Assigned"
9. If returned or rejected, system sends notification to Key Account Manager with remarks
10. System records all actions and decisions in audit trail

**Business Rules:**
- BR.25: The validation team consists of at least two members: a team lead and a team member.

**Traceability:**
- **BRD:** Revalidation approval
- **SRD:** Section 6.3.6.2 "The Re-Validation Process", Pages 273-274

**Dependencies:**
- US-CERT-017

**Priority:** Must Have

---

### US-CERT-019: Prepare Re-assessment Plan

**As a** Validation Team Member  
**I want to** prepare re-assessment plan for revalidation  
**So that** revalidation activities are properly planned and structured

**Acceptance Criteria:**
1. Once re-validation team is assigned, they receive notification to prepare Self-Assessment Questionnaire (SAQ) `[SRD Section 6.3.6.2.1]`
2. Validation Team can use one of following options to create SAQ for revalidation: `[SRD Section 6.3.6.2.1]`
   
   **Option A - Create New SAQ:**
   - Validation Team selects SAQ template to generate SAQ following same steps as validation process
   - System generates new SAQ based on selected template
   
   **Option B - Reuse Previous SAQ:**
   - Validation Team reuses SAQ from previous validation/revalidation
   - Validation Team can edit reused SAQ by removing questions or entire sections
   - System preserves original SAQ and creates modified copy for revalidation
3. Validation team can define scope of revalidation by removing sections/questions from SAQ `[SRD Section 6.3.6.2]`
4. Validation Team can decide not to share SAQ with commercial establishment `[SRD Section 6.3.6.2]`
5. Revalidation process is similar to validation process with noted differences in scope and flexibility
6. Validation Team prepares initial risk assessment and assessment plan following similar process as Phase 3
7. Validation Team Lead reviews and approves re-assessment plan
8. System follows same workflow as initial assessment plan preparation (US-VAL-003, US-VAL-004)
9. System records all re-assessment plan activities in audit trail
10. Once re-assessment plan is approved, revalidation process proceeds to execution phase

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Re-assessment plan preparation
- **SRD:** Section 6.3.6.2 "The Re-Validation Process", Section 6.3.6.2.1 "The Development of the SAQ", Pages 273-274

**Dependencies:**
- US-CERT-018

**Priority:** Must Have

---

### US-CERT-020: Conduct Revalidation Activities

**As a** Validation Team Member  
**I want to** conduct revalidation activities  
**So that** commercial establishment's continued compliance can be verified

**Acceptance Criteria:**
1. Validation Team conducts revalidation following approved re-assessment plan
2. Revalidation process follows similar workflow as validation process from Phase 3
3. Validation Team may not require any meetings with commercial establishment `[SRD Section 6.3.6.2]`
4. If SAQ was shared with commercial establishment, validation team reviews responses
5. Validation Team can schedule meetings if needed following standard meeting process
6. Validation Team performs on-site validation activities if required by re-assessment plan
7. Validation Team identifies findings, remaining risks, and recommendations
8. Validation Team creates assessment file for revalidation
9. Validation Team prepares assessment report
10. Validation Team can decide not to share assessment report with commercial establishment `[SRD Section 6.3.6.2]`
11. All revalidation activities follow same standards and procedures as initial validation
12. System maintains separation between revalidation records and initial validation records
13. During revalidation, responsibility of modifying Control Plan is transferred to Validation Team `[US-VAL-037, SRD Section 6.3.4.4.3]`
14. Key Account Manager has read-only access to control plan until decision about AEO status is made `[US-VAL-037]`
15. System records all revalidation activities in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Revalidation execution
- **SRD:** Section 6.3.6.2 "The Re-Validation Process", Section 6.3.6.2.2 "Re-validation", Pages 273-275

**Dependencies:**
- US-CERT-019

**Priority:** Must Have

---

### US-CERT-021: Make Post-Revalidation Decision

**As an** AEO Program Manager  
**I want to** make final decision on AEO status after revalidation  
**So that** appropriate action is taken based on revalidation findings

**Acceptance Criteria:**
1. After revalidation activities are completed, Validation Team Lead submits final recommendation to AEO Program Manager
2. AEO Program Manager reviews:
   - Revalidation assessment report
   - Assessment file
   - Findings and recommendations
   - Violation history
   - Monitoring history
   - Previous validation results
3. AEO Program Manager can make one of following decisions: `[SRD Section 6.3.6.2.3, 6.3.6.2.4]`
   
   **Decision A - Continue AEO Status:**
   - AEO status continues
   - System changes status to "AEO Certified"
   - Benefits remain active
   - Responsibility of control plan returns to Key Account Manager
   
   **Decision B - Suspend AEO Status:**
   - AEO status is suspended temporarily
   - System changes status to "AEO Status Suspended"
   - Benefits can be disabled
   - Suspension period is defined
   
   **Decision C - Revoke AEO Status:**
   - AEO status is revoked permanently
   - System changes status to "AEO Status Revoked"
   - All benefits are terminated
   - Certificate is cancelled
4. System validates decision and requires justification for suspension or revocation
5. System sends notification to:
   - Commercial establishment (via email and AEO Portal)
   - Key Account Manager
   - Validation Team
   - Local customs departments
6. If decision is to continue AEO status: `[SRD Section 6.3.5.1, 6.3.6.2.4]`
   - Responsibility of control plan goes back to Key Account Manager
   - System records date of revalidation for next periodic cycle
7. If decision is to suspend/revoke AEO status: `[US-VAL-037]`
   - Responsibility of control plan remains with Validation Team
   - Commercial establishment can submit appeal
8. System records decision in audit trail `[SRD Section 6.3.6.2.5]`
9. Commercial establishment status is updated accordingly

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Post-revalidation decision
- **SRD:** Section 6.3.5.1 "Statuses of AEO", Section 6.3.6.2.3 "Post-Revalidation AEO Decision", Section 6.3.6.2.4 "Commercial Establishment Status After the Revalidation Process", Section 6.3.6.2.5 "Statuses of the Revalidation Process", Pages 270, 276-285

**Dependencies:**
- US-CERT-020

**Priority:** Must Have

---

<a name="local-customs-suspension-revocation"></a>
## 7. Local Customs Portal - Suspension and Revocation

### Epic: Certificate Suspension and Revocation
**Goal:** Enable AEO Program Manager to suspend or revoke AEO certificates when necessary

---

### US-CERT-022: Suspend AEO Certificate

**As an** AEO Program Manager  
**I want to** suspend AEO certificate  
**So that** temporary non-compliance can be addressed without permanent revocation

**Acceptance Criteria:**
1. AEO Program Manager can suspend AEO status for period of time `[SRD Section 6.2.6.2, 6.3.5.1]`
2. Suspension can be initiated for reasons such as:
   - Major violations identified
   - Non-compliance with AEO standards
   - Failure to implement corrective actions
   - Significant changes in business operations requiring review
   - Pending investigation
3. System provides suspension form with following fields:
   - Reason for suspension
   - Detailed justification
   - Suspension period (start and end dates)
   - Conditions for lifting suspension
   - Supporting documents
4. When AEO status is suspended, system changes status to "AEO Status Suspended" `[SRD Section 6.2.6.2, 6.3.5.1]`
5. Status "AEO Status Suspended" is recorded in audit trail `[SRD Section 6.2.6.2, 6.3.5.1]`
6. AEO Program Manager can disable or reactivate benefits granted to AEO during suspension
7. System sends notification when AEO status is suspended to: `[SRD Section 6.2.6.3, 6.3.5.2]`
   - Commercial establishment (via email and AEO Portal)
   - Key Account Manager
   - Local customs departments (via email and Local customs AEO management portal)
   - Federal administrator
8. During suspension, commercial establishment can:
   - Submit corrective action plan
   - Request review of suspension
   - Submit appeal against suspension
9. Suspended AEO can transition to following statuses: `[SRD Section 6.2.6.2]`
   - **AEO Certified** - if AEO Program Manager removes suspension and continues AEO status
   - **AEO Status Revoked** - if AEO Program Manager decides to revoke AEO status
   - **AEO Status Cancelled** - if commercial establishment decides to cancel status
10. System tracks suspension duration and sends reminders for review

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Certificate suspension
- **SRD:** Section 6.2.6.2 "Statuses of AEO Certificate", Section 6.2.6.3 "Notifications", Section 6.3.5.1 "Statuses of AEO", Section 6.3.5.2 "Notifications", Pages 203-205, 270-271

**Dependencies:**
- US-CERT-004

**Priority:** Must Have

---

### US-CERT-023: Revoke AEO Certificate

**As an** AEO Program Manager  
**I want to** revoke AEO certificate permanently  
**So that** commercial establishments that no longer meet standards lose AEO status

**Acceptance Criteria:**
1. AEO Program Manager can revoke AEO certificate permanently `[SRD Section 6.2.6.2, 6.3.5.1]`
2. Revocation can be initiated for reasons such as:
   - Severe or repeated violations
   - Fraud or misrepresentation
   - Failure to maintain AEO standards
   - Failure to address issues during suspension period
   - Loss of business license
   - Request from federal authorities
3. System provides revocation form with following fields:
   - Reason for revocation
   - Detailed justification
   - Effective date
   - Supporting documents and evidence
4. System requires confirmation before processing revocation due to permanence
5. When AEO status is revoked, system changes status to "AEO Status Revoked" `[SRD Section 6.2.6.2, 6.3.5.1]`
6. Status "AEO Status Revoked" is final status `[SRD Section 6.2.6.2, 6.3.5.1]`
7. Status is recorded in audit trail `[SRD Section 6.2.6.2, 6.3.5.1]`
8. Upon revocation:
   - All benefits are immediately terminated
   - Certificate becomes invalid
   - AEO status is removed
   - Control plan monitoring ceases
9. System sends notification when AEO status is revoked to: `[SRD Section 6.2.6.3, 6.3.5.2]`
   - Commercial establishment (via email and AEO Portal)
   - Key Account Manager
   - Local customs departments (via email and Local customs AEO management portal)
   - Federal administrator
10. Commercial establishment can submit appeal against revocation within 30 days `[BR.20]`
11. If no appeal is submitted or appeal is rejected, revocation becomes permanent
12. Revoked commercial establishments cannot reapply for AEO status for defined period (as per policy)

**Business Rules:**
- BR.20: The commercial establishment has the right to submit an appeal against the decision of the relevant customs administration within a maximum of 30 days from the date of notification.

**Traceability:**
- **BRD:** Certificate revocation
- **SRD:** Section 6.2.6.2 "Statuses of AEO Certificate", Section 6.2.6.3 "Notifications", Section 6.3.5.1 "Statuses of AEO", Section 6.3.5.2 "Notifications", Pages 203-205, 270-271

**Dependencies:**
- US-CERT-004

**Priority:** Must Have

---

### US-CERT-024: Continue AEO Status After Suspension

**As an** AEO Program Manager  
**I want to** continue AEO status after suspension  
**So that** commercial establishments that address issues can resume normal AEO status

**Acceptance Criteria:**
1. AEO Program Manager can update AEO status to continued after suspension `[SRD Section 6.3.5.1]`
2. Continuation can occur when:
   - Suspension period expires
   - Commercial establishment addresses all issues
   - Corrective actions are successfully implemented
   - Conditions for lifting suspension are met
   - AEO Program Manager reviews and approves continuation
3. System provides continuation review form with:
   - Reason for continuing status
   - Review of corrective actions taken
   - Assessment of current compliance
   - Any new conditions or requirements
4. AEO Program Manager reviews:
   - Original suspension reason
   - Corrective action plan and implementation
   - Monitoring results during suspension
   - Current compliance status
5. When AEO status is continued, system changes status from "AEO Status Suspended" to "AEO Certified" `[SRD Section 6.2.6.2, 6.3.5.1]`
6. Status change is recorded in audit trail `[SRD Section 6.3.5.1]`
7. Upon continuation:
   - All benefits are reactivated (unless modified)
   - Certificate becomes valid again
   - Normal monitoring resumes
   - Responsibility of control plan returns to Key Account Manager (if was suspended due to revalidation)
8. System sends notification when AEO status is continued to: `[SRD Section 6.2.6.3, 6.3.5.2]`
   - Commercial establishment (via email and AEO Portal)
   - Key Account Manager
   - Local customs departments (via email and Local customs AEO management portal)
9. Notification specifies:
   - Continuation of AEO status after suspension
   - Effective date
   - Any new conditions or requirements
   - Next review date (if applicable)
10. System updates certificate status and makes it available for download again

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Status continuation
- **SRD:** Section 6.2.6.2 "Statuses of AEO Certificate", Section 6.2.6.3 "Notifications", Section 6.3.5.1 "Statuses of AEO", Section 6.3.5.2 "Notifications", Pages 203-205, 270-271

**Dependencies:**
- US-CERT-022

**Priority:** Must Have

---

<a name="aeo-portal-appeals-submission"></a>
## 8. AEO Portal - Appeals Submission

### Epic: Appeals Management
**Goal:** Enable commercial establishments to submit and manage appeals against customs decisions

---

### US-CERT-025: Submit Appeal Request

**As a** Commercial Establishment Account Manager  
**I want to** submit appeal against decision issued by customs department  
**So that** I can challenge decisions I believe are unfair or incorrect

**Acceptance Criteria:**
1. Commercial establishment can submit appeal against decision of customs administration within maximum of 30 days from date of notification `[BR.20]`
2. System validates that appeal is submitted within allowed timeframe (30 days)
3. Appeal can be submitted for following reasons: `[SRD Section 5.12]`
   - Rejection of membership request (AEO Authorization Request)
   - Rejection of membership granting (AEO status)
   - Suspension of membership
   - Revocation of membership
4. System provides appeal request form with following fields: `[SRD Section 5.12]`
   - Reason for appeal (single choice from list above) - Mandatory
   - Appeal details (text) - Mandatory
   - Supporting document(s) - Optional
   - Submission date - Auto-filled
   - Appeal request reference number - Auto-generated
5. Appeal request reference number follows format: AEO-APL-[Year]-[Sequential Number] `[SRD Section 5.12]`
   - Example: AEO-APL-2025-0045
   - Sequential number is four-digit running number starting from 0001 each year
6. Commercial establishment must provide detailed justification for appeal
7. Commercial establishment can attach supporting documents (evidence, correspondence, etc.)
8. System validates that all mandatory fields are completed before submission
9. Once submitted, system sends notification to: `[SRD Section 6.3.7.3]`
   - Appeal officer (via email and Local customs AEO management portal)
   - AEO program manager (via email and Local customs AEO management portal)
10. System changes status to "Appeal Request Submitted"
11. Commercial establishment receives confirmation with appeal reference number
12. System records appeal submission in audit trail

**Business Rules:**
- BR.20: The commercial establishment has the right to submit an appeal against the decision of the relevant customs administration within a maximum of 30 days from the date of notification.

**Traceability:**
- **BRD:** Appeal submission process
- **SRD:** Section 5.12 "Appeal Process Data", Section 6.3.7.3 "Notifications", Pages 92-94, 291-292

**Dependencies:**
- US-CERT-023 (or any decision that can be appealed)

**Priority:** Must Have

---

### US-CERT-026: Track Appeal Status

**As a** Commercial Establishment Account Manager  
**I want to** track status of my appeal request  
**So that** I know progress and can take necessary actions

**Acceptance Criteria:**
1. Commercial establishment can view appeal status in AEO Portal
2. System displays following possible statuses: `[SRD Section 6.3.7.2]`
   - **Appeal Request Submitted** - When commercial establishment submits appeal request
   - **Appeal Request Under Review** - When appeal officer starts reviewing request
   - **Appeal Request Returned** - When appeal request is incomplete and returned for more information
   - **Appeal Assigned for Decision** - When appeal is assigned to AEO program manager for decision
   - **Hearing Session Scheduled** - When hearing session date is set
   - **Hearing Session Conducted** - When hearing has taken place
   - **Appeal Approved** - When appeal is accepted
   - **Appeal Rejected** - When appeal is rejected
   - **Appeal Escalated** - When appeal is escalated to federal level
   - **Appeal Closed** - When appeal process is complete
3. For each status, system displays:
   - Status name
   - Date/time of status change
   - Remarks (if any)
   - Required actions (if any)
4. System sends notifications at key status changes: `[SRD Section 6.3.7.3]`
   - When hearing session is requested
   - When additional arguments are needed
   - When decision is made
   - When escalated to general department
   - When appeal is closed automatically
   - When appeal is rejected automatically
5. Commercial establishment can view complete history of appeal with all status changes
6. If appeal is returned, commercial establishment can see what information is required
7. System displays deadline for responding to returned appeal (based on SLA)
8. System alerts commercial establishment if response deadline is approaching

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Appeal status tracking
- **SRD:** Section 6.3.7.2 "Statuses of the Appeal Request", Section 6.3.7.3 "Notifications", Pages 287-292

**Dependencies:**
- US-CERT-025

**Priority:** Must Have

---

### US-CERT-027: Respond to Returned Appeal

**As a** Commercial Establishment Account Manager  
**I want to** respond to returned appeal request  
**So that** I can provide additional information requested by customs

**Acceptance Criteria:**
1. If appeal request is incomplete, appeals officer returns it to commercial establishment with remarks `[SRD Section 6.3.7.1]`
2. System changes status to "Appeal Request Returned" `[SRD Section 6.3.7.2]`
3. Commercial establishment receives notification that appeal was returned `[SRD Section 6.3.7.3]`
4. System displays remarks from appeals officer explaining what is required
5. Commercial establishment can view original appeal request and submitted documents
6. System provides interface to:
   - Update appeal details
   - Add or replace supporting documents
   - Address specific concerns raised by appeals officer
   - Resubmit appeal
7. System displays SLA deadline for responding to returned appeal
8. If commercial establishment exceeds agreed SLA to reply, system automatically closes appeal `[SRD Section 6.3.7.2, 6.3.7.3]`
9. When appeal is automatically closed, notification is sent to: `[SRD Section 6.3.7.3]`
   - Commercial establishment (via email and AEO Portal)
   - Appeal officer (via email and Local customs AEO management portal)
   - AEO program manager (via email and Local customs AEO management portal)
10. Once commercial establishment resubmits appeal with additional information, system changes status back to "Appeal Request Under Review"
11. Resubmission is recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Appeal response
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.2 "Statuses of the Appeal Request", Section 6.3.7.3 "Notifications", Pages 285-292

**Dependencies:**
- US-CERT-026

**Priority:** Must Have

---

### US-CERT-028: Request Hearing Session

**As a** Commercial Establishment Account Manager  
**I want to** request hearing session after appeal rejection  
**So that** I can present my case in person

**Acceptance Criteria:**
1. If appeal request is rejected, commercial establishment has option to object to rejection and request hearing `[SRD Section 6.3.7.1]`
2. System provides "Request Hearing" button when appeal is rejected
3. Commercial establishment must request hearing within defined timeframe
4. System provides hearing request form
5. Once hearing is requested, system sends notification to: `[SRD Section 6.3.7.3]`
   - Appeal officer (via email and Local customs AEO management portal)
   - AEO program manager (via email and Local customs AEO management portal)
6. System changes status to "Hearing Session Requested"
7. Relevant customs administration must coordinate hearing session date within 15 days from request date `[BR.21]`
8. Appeals officer schedules hearing session with following details: `[SRD Section 5.12]`
   - Hearing title - Mandatory
   - Purpose of hearing - Optional
   - Hearing date - Mandatory
   - Start time - Mandatory
   - Duration (from dropdown) - Mandatory
9. System validates that hearing is scheduled within 15-day requirement
10. Once hearing is scheduled, notification is sent to commercial establishment
11. System provides hearing details including date, time, location/meeting link, and agenda

**Business Rules:**
- BR.21: If the commercial establishment requests a hearing session, the relevant customs administration must coordinate a session date within 15 days from the request date.

**Traceability:**
- **BRD:** Hearing request
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.3 "Notifications", Section 5.12 "Appeal Process Data", Pages 92-94, 285-292

**Dependencies:**
- US-CERT-026

**Priority:** Must Have

---

### US-CERT-029: Participate in Hearing Session

**As a** Commercial Establishment Account Manager  
**I want to** participate in hearing session  
**So that** I can present my case and provide additional arguments

**Acceptance Criteria:**
1. Commercial establishment receives notification with hearing session details
2. System provides hearing details including:
   - Hearing title
   - Purpose
   - Date and time
   - Location (if in-person) or meeting link (if virtual)
   - Duration
   - Required attendees
   - Agenda
3. Commercial establishment representative must attend hearing session
4. If commercial establishment representative doesn't show to hearing session, appeal is rejected automatically `[SRD Section 6.3.7.2, 6.3.7.3]`
5. When appeal is automatically rejected due to no-show, notification is sent to: `[SRD Section 6.3.7.3]`
   - Commercial establishment (via email and AEO Portal)
   - Appeal officer (via email and Local customs AEO management portal)
   - AEO program manager (via email and Local customs AEO management portal)
6. Appeals officer records hearing minutes during or after session `[SRD Section 5.12]`
7. After hearing session, minutes are shared with commercial establishment
8. Commercial establishment has 7 days to submit additional arguments after hearing minutes are shared `[BR.22]`
9. If commercial establishment has additional arguments: `[SRD Section 5.12]`
   - System provides form to submit arguments (text) - Mandatory
   - System allows uploading additional documents - Optional
10. When additional arguments are submitted, notification is sent to: `[SRD Section 6.3.7.3]`
    - Appeal officer (via email and Local customs AEO management portal)
    - AEO program manager (via email and Local customs AEO management portal)
11. System tracks 7-day deadline for submitting additional arguments
12. All hearing-related activities are recorded in audit trail

**Business Rules:**
- BR.22: After the hearing session minutes are shared, the commercial establishment has only 7 days to submit any additional arguments, if applicable.

**Traceability:**
- **BRD:** Hearing participation
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.2 "Statuses of the Appeal Request", Section 6.3.7.3 "Notifications", Section 5.12 "Appeal Process Data", Pages 92-94, 285-292

**Dependencies:**
- US-CERT-028

**Priority:** Must Have

---

### US-CERT-030: Object to Hearing Decision

**As a** Commercial Establishment Account Manager  
**I want to** object to hearing decision and escalate to federal level  
**So that** higher authority can review my appeal

**Acceptance Criteria:**
1. After hearing session and final decision, if commercial establishment objects to upheld rejection decision, they can request escalation `[SRD Section 6.3.7.1]`
2. System provides "Object to Decision" option after hearing decision is communicated
3. Commercial establishment can submit objection with:
   - Grounds for objection
   - Additional arguments
   - Supporting evidence
4. When commercial establishment objects to upheld decision following hearing, appeal is escalated to general department of customs `[SRD Section 6.3.7.1, 6.3.7.2]`
5. System changes status to "Appeal Escalated to Federal Level" `[SRD Section 6.3.7.2]`
6. Status is recorded in audit trail `[SRD Section 6.3.7.2]`
7. System sends notification when appeal is escalated to: `[SRD Section 6.3.7.3]`
   - Appeal officer (via email and Local customs AEO management portal)
   - AEO program manager (via email and Local customs AEO management portal)
   - Federal administrator (via email and Federal customs AEO management portal)
8. Complete appeal case file is transferred to federal level including:
   - Original appeal request
   - All supporting documents
   - Review history
   - Hearing minutes
   - Decision history
   - Objection details
9. Federal administrator will review and make final decision on escalated appeal
10. Commercial establishment receives confirmation that appeal has been escalated

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Appeal escalation
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.2 "Statuses of the Appeal Request", Section 6.3.7.3 "Notifications", Pages 285-292

**Dependencies:**
- US-CERT-029

**Priority:** Must Have

---

<a name="local-customs-appeals-management"></a>
## 9. Local Customs Portal - Appeals Management

### Epic: Appeals Review and Decision
**Goal:** Enable appeals officer and AEO Program Manager to review and decide on appeal requests

---

### US-CERT-031: Review Appeal Request for Completeness

**As an** Appeals Officer  
**I want to** review appeal request to ensure it is complete  
**So that** proper review and decision-making can proceed

**Acceptance Criteria:**
1. After commercial establishment submits appeal request, it is forwarded to relevant customs department `[SRD Section 6.3.7.1]`
2. Appeals officer receives notification about new appeal request `[SRD Section 6.3.7.3]`
3. Appeals officer can view appeal request with all details:
   - Appeal reference number
   - Reason for appeal
   - Appeal details/justification
   - Supporting documents
   - Commercial establishment information
   - Original decision being appealed
4. Employee responsible for handling appeal requests reviews and studies appeal request and ensures it is complete `[SRD Section 6.3.7.1]`
5. Appeals officer determines if request is complete:
   
   **If Request is Incomplete:** `[SRD Section 6.3.7.1]`
   - Appeals officer adds remarks to request explaining what is missing
   - Appeals officer returns request to commercial establishment
   - System changes status to "Appeal Request Returned"
   
   **If Request is Complete:** `[SRD Section 6.3.7.1]`
   - Appeals officer adds recommendation to approve or reject appeal
   - System provides recommendation options:
     * Accept
     * Reject
   - Appeals officer provides remarks supporting recommendation - Mandatory `[SRD Section 5.12]`
   - Appeals officer assigns request to AEO Program Manager for decision
   - System changes status to "Appeal Assigned for Decision"
6. System sends notification when appeal is assigned to AEO Program Manager for decision-making `[SRD Section 6.3.7.3]`
7. All review actions are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Appeal review
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.3 "Notifications", Section 5.12 "Appeal Process Data", Pages 92-94, 285-292

**Dependencies:**
- US-CERT-025

**Priority:** Must Have

---

### US-CERT-032: Make Appeal Decision

**As an** AEO Program Manager  
**I want to** make final decision on appeal request  
**So that** appropriate action is taken on the appeal

**Acceptance Criteria:**
1. AEO Program Manager receives notification when appeal is assigned for decision `[SRD Section 6.3.7.3]`
2. AEO Program Manager reviews appeal request including:
   - Original decision being appealed
   - Appeal justification and supporting documents
   - Appeals officer's recommendation
   - Complete case history
3. AEO Program Manager can make one of following decisions: `[SRD Section 6.3.7.1, 5.12]`
   
   **Decision A - Approve Appeal:** `[SRD Section 6.3.7.1]`
   - AEO Program Manager selects "Accept" decision
   - Commercial establishment is notified of approval
   - System automatically updates status of "AEO Authorization Request" or "AEO status" as follows:
     * If "AEO Authorization Request" was rejected: System automatically accepts "AEO Authorization Request", and Senior administrator will need to assign Validation Team
     * If granting AEO status was previously rejected: System automatically approves AEO status for commercial establishment, and AEO Program Manager assigns Key Account Managers Team
     * If appeal was due to suspension or cancellation: System automatically updates commercial establishment's status to continue its status as AEO
   - System changes appeal status to "Appeal Approved"
   
   **Decision B - Return Appeal:** `[SRD Section 6.3.7.1]`
   - AEO Program Manager returns appeal request to appeals officer
   - AEO Program Manager adds remarks explaining what needs to be addressed
   - Appeals officer reviews and resubmits with additional information or clarification
   
   **Decision C - Reject Appeal:** `[SRD Section 6.3.7.1]`
   - AEO Program Manager selects "Reject" decision
   - AEO Program Manager adds reason for rejection - Mandatory in case of rejection `[SRD Section 5.12]`
   - Commercial establishment is notified of rejection
   - Commercial establishment has options:
     * Accept rejection decision
     * Request hearing session (if they object to rejection)
   - System changes appeal status to "Appeal Rejected"
4. System validates that decision includes proper justification
5. System sends notification to commercial establishment and appeals officer about decision
6. Decision is recorded in audit trail
7. If appeal is approved, system triggers appropriate workflow to reverse original decision

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Appeal decision
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.3 "Notifications", Section 5.12 "Appeal Process Data", Pages 92-94, 285-292

**Dependencies:**
- US-CERT-031

**Priority:** Must Have

---

### US-CERT-033: Schedule Hearing Session

**As an** Appeals Officer  
**I want to** schedule hearing session for appeal  
**So that** commercial establishment can present their case in person

**Acceptance Criteria:**
1. When commercial establishment requests hearing session, appeals officer receives notification `[SRD Section 6.3.7.3]`
2. Relevant customs administration must coordinate hearing session date within 15 days from request date `[BR.21]`
3. Appeals officer schedules hearing session with following details: `[SRD Section 5.12]`
   - Hearing title (text) - Mandatory
   - Purpose of hearing (text) - Optional
   - Hearing date - Mandatory
   - Start time - Mandatory
   - Duration (single choice list) - Mandatory
4. System validates that hearing date is within 15-day requirement from request date
5. System validates that meeting is scheduled with adequate advance notice as defined in system settings `[BR.26]`
6. System will not allow scheduling hearing with date earlier than defined notification period `[BR.26]`
7. Appeals officer can specify:
   - Location (if in-person hearing)
   - Meeting link (if virtual hearing)
   - Required attendees from customs side
   - Required attendees from commercial establishment side
   - Agenda items
8. System changes status to "Hearing Session Scheduled"
9. System sends hearing invitation to:
   - Commercial establishment (via email and AEO Portal)
   - AEO Program Manager
   - Other customs officials involved
10. Invitation includes all hearing details and instructions
11. System sends reminders before hearing based on configured schedule
12. Commercial establishment can view hearing details in AEO Portal

**Business Rules:**
- BR.21: If the commercial establishment requests a hearing session, the relevant customs administration must coordinate a session date within 15 days from the request date.
- BR.26: When scheduling meetings whether field visits, remote meetings, or a hearing session for an appeal request, the commercial establishment shall be notified of a specific period in advance, as defined in the system settings. The system will not allow scheduling any meeting with a date earlier than the defined notification period.

**Traceability:**
- **BRD:** Hearing scheduling
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.3 "Notifications", Section 5.12 "Appeal Process Data", Pages 92-94, 285-292

**Dependencies:**
- US-CERT-028

**Priority:** Must Have

---

### US-CERT-034: Conduct Hearing Session and Record Minutes

**As an** Appeals Officer  
**I want to** conduct hearing session and record minutes  
**So that** commercial establishment's case is properly heard and documented

**Acceptance Criteria:**
1. Appeals officer conducts hearing session on scheduled date and time
2. System tracks attendance:
   - Customs officials present
   - Commercial establishment representatives present
3. If commercial establishment representative doesn't attend, system allows marking as no-show
4. If no-show is recorded, appeal is automatically rejected `[SRD Section 6.3.7.2, 6.3.7.3]`
5. During or after hearing, appeals officer records hearing minutes `[SRD Section 5.12]`
6. Hearing minutes include:
   - Date and time of hearing
   - Attendees
   - Commercial establishment's arguments and evidence presented
   - Questions asked and answers provided
   - Customs department's position
   - Key discussion points
   - Preliminary findings (if any)
7. System provides text field for entering hearing minutes - Mandatory `[SRD Section 5.12]`
8. Appeals officer can attach documents or evidence presented during hearing
9. After hearing minutes are recorded, appeals officer shares them with commercial establishment
10. System sends notification to commercial establishment that hearing minutes are available
11. System changes status to "Hearing Session Conducted"
12. Commercial establishment has 7 days to submit additional arguments after hearing minutes are shared `[BR.22]`
13. System tracks 7-day deadline and alerts if deadline is approaching
14. If commercial establishment submits additional arguments within 7 days, system notifies appeals officer and AEO Program Manager
15. All hearing activities are recorded in audit trail

**Business Rules:**
- BR.22: After the hearing session minutes are shared, the commercial establishment has only 7 days to submit any additional arguments, if applicable.

**Traceability:**
- **BRD:** Hearing conduct
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.2 "Statuses of the Appeal Request", Section 6.3.7.3 "Notifications", Section 5.12 "Appeal Process Data", Pages 92-94, 285-292

**Dependencies:**
- US-CERT-033

**Priority:** Must Have

---

### US-CERT-035: Make Post-Hearing Decision

**As an** AEO Program Manager  
**I want to** make final decision after hearing session  
**So that** appeal can be concluded appropriately

**Acceptance Criteria:**
1. After hearing session and any additional arguments are submitted, appeals officer prepares final recommendation
2. Appeals officer forwards case to AEO Program Manager for final decision
3. AEO Program Manager reviews:
   - Hearing minutes
   - Additional arguments submitted by commercial establishment (if any)
   - Appeals officer's recommendation
   - All evidence and documentation
   - Original decision context
4. AEO Program Manager makes final decision:
   - **Uphold Original Decision** (Reject Appeal)
   - **Reverse Original Decision** (Accept Appeal)
5. If decision is to reject appeal after hearing:
   - Commercial establishment has option to object and request escalation to federal level
   - If commercial establishment accepts decision, appeal is closed
   - System changes status to "Appeal Rejected" or "Appeal Closed"
6. If decision is to accept appeal:
   - System triggers reversal of original decision
   - Status of AEO Authorization Request or AEO status is updated accordingly
   - System changes appeal status to "Appeal Approved"
7. System sends notification to commercial establishment about final decision
8. Decision includes detailed explanation of reasoning
9. All post-hearing activities are recorded in audit trail
10. If commercial establishment objects to rejection, case proceeds to escalation (US-CERT-030)

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Post-hearing decision
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.2 "Statuses of the Appeal Request", Pages 285-292

**Dependencies:**
- US-CERT-034

**Priority:** Must Have

---

<a name="federal-customs-appeals-escalation"></a>
## 10. Federal Customs Portal - Appeals Escalation

### Epic: Federal Appeals Review
**Goal:** Enable Federal Administrator to review and decide on escalated appeals

---

### US-CERT-036: Review Escalated Appeal

**As a** Federal Administrator  
**I want to** review appeal that has been escalated to federal level  
**So that** I can make final determination on the appeal

**Acceptance Criteria:**
1. When appeal is escalated to general department of customs, Federal Administrator receives notification `[SRD Section 6.3.7.3]`
2. System changes status to "Appeal Escalated to Federal Level" `[SRD Section 6.3.7.2]`
3. Federal Administrator can access complete appeal case file including:
   - Original appeal request and all supporting documents
   - Local customs review and recommendation
   - Hearing minutes (if hearing was held)
   - Additional arguments submitted by commercial establishment
   - All decision history
   - Objection to local decision
4. Federal Administrator can review:
   - Original decision by local customs that was appealed
   - Local customs handling of appeal
   - Procedural correctness
   - Substantive merits of case
5. System provides interface to:
   - Review all documents
   - Add federal review notes
   - Request additional information if needed
   - Prepare decision
6. Federal Administrator can communicate with:
   - Local customs (for clarification)
   - Commercial establishment (if additional information needed)
7. All review activities are tracked in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Federal appeal review
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.2 "Statuses of the Appeal Request", Section 6.3.7.3 "Notifications", Pages 285-292

**Dependencies:**
- US-CERT-030

**Priority:** Must Have

---

### US-CERT-037: Make Final Federal Decision on Appeal

**As a** Federal Administrator  
**I want to** make final decision on escalated appeal  
**So that** appeal can be concluded at highest level

**Acceptance Criteria:**
1. Federal Administrator makes final decision on escalated appeal
2. Federal Administrator can decide to:
   
   **Decision A - Uphold Local Decision:**
   - Federal Administrator confirms local customs decision
   - Appeal is finally rejected
   - No further recourse available
   - System closes appeal
   
   **Decision B - Reverse Local Decision:**
   - Federal Administrator overturns local customs decision
   - Appeal is approved
   - Original decision is reversed
   - Appropriate action is triggered (accept application, continue status, etc.)
   
   **Decision C - Remand to Local Customs:**
   - Federal Administrator sends case back to local customs for reconsideration
   - Federal Administrator provides specific instructions or areas to address
   - Local customs must review again following federal guidance
3. System requires detailed justification for federal decision
4. Decision must address:
   - Key issues raised in appeal
   - Analysis of local customs handling
   - Legal and procedural considerations
   - Final determination and reasoning
5. System sends notification when federal decision is made to:
   - Commercial establishment (via email and AEO Portal)
   - Local customs departments (via email and Local customs AEO management portal)
   - All involved parties
6. Federal decision is recorded as final in audit trail
7. If appeal is approved at federal level:
   - System triggers reversal of original decision
   - Status updates are propagated throughout system
   - All relevant parties are notified
8. System changes appeal status to appropriate final status:
   - "Appeal Approved" (if reversed)
   - "Appeal Rejected" (if upheld)
   - "Appeal Returned to Local Customs" (if remanded)
9. Federal decision becomes part of permanent record and may be used as precedent

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Federal appeal decision
- **SRD:** Section 6.3.7.1 "Reviewing an Appeal Request", Section 6.3.7.2 "Statuses of the Appeal Request", Pages 285-292

**Dependencies:**
- US-CERT-036

**Priority:** Must Have

---

## Summary Tables

### Phase 4 User Stories Summary by Portal

| Portal | Epic | User Stories Count |
|--------|------|-------------------|
| **Federal Customs Portal** | AEO Certification Process | 2 (US-CERT-001 to US-CERT-002) |
| **Federal Customs Portal** | Certificate Issuance | 2 (US-CERT-003 to US-CERT-004) |
| **AEO Portal** | Certificate Management | 3 (US-CERT-005 to US-CERT-007) |
| **Local Customs Portal** | Key Account Management | 5 (US-CERT-008 to US-CERT-012) |
| **Local Customs Portal** | Control Plan Execution and Monitoring | 4 (US-CERT-013 to US-CERT-016) |
| **Local Customs Portal** | Re-validation Process | 5 (US-CERT-017 to US-CERT-021) |
| **Local Customs Portal** | Certificate Suspension and Revocation | 3 (US-CERT-022 to US-CERT-024) |
| **AEO Portal** | Appeals Management | 6 (US-CERT-025 to US-CERT-030) |
| **Local Customs Portal** | Appeals Review and Decision | 5 (US-CERT-031 to US-CERT-035) |
| **Federal Customs Portal** | Federal Appeals Review | 2 (US-CERT-036 to US-CERT-037) |
| **TOTAL** | **10 Epics** | **37 User Stories** |

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
| BR.17 | License expiration date calculated as two years from issuance | US-CERT-004 |
| BR.20 | Commercial establishment can submit appeal within 30 days | US-CERT-023, US-CERT-025 |
| BR.21 | Hearing session must be coordinated within 15 days | US-CERT-028, US-CERT-033 |
| BR.22 | 7 days to submit additional arguments after hearing | US-CERT-029, US-CERT-034 |
| BR.23 | Periodic revalidation within 5 years | US-CERT-017 |
| BR.25 | Validation team consists of at least two members | US-CERT-018 |
| BR.26 | Meetings scheduled with advance notice per system settings | US-CERT-015, US-CERT-033 |

---

### Phase 4 User Stories Traceability Matrix

| User Story ID | User Story Title | SRD Sections | Page Numbers |
|--------------|------------------|--------------|--------------|
| US-CERT-001 | Key Account Team assignment | Section 6.3.5, 6.3.6.1 | 269-272 |
| US-CERT-002 | Benefits assignment | Section 6.3.5 | 269-270 |
| US-CERT-003 | Certificate issuance request | Section 6.3.5, 6.2.6.1 | 203, 269-270 |
| US-CERT-004 | Issue certificate | Section 6.3.5, 6.2.6.1, 6.2.6.2, 6.2.6.3, 6.3.5.1, 6.3.5.2 | 203-205, 270-271 |
| US-CERT-005 | View certificate status | Section 6.2.6.2, 6.2.6.3, 6.2.5.6 | 193-194, 201-205 |
| US-CERT-006 | View and download certificate | Section 6.2.6.1 | 203 |
| US-CERT-007 | Request cancellation | Section 6.2.6.2 | 203-205 |
| US-CERT-008 | View AEO dashboard | Section 6.3.6.1 | 271-272 |
| US-CERT-009 | View establishment profile | Section 6.3.6.1 | 271-272 |
| US-CERT-010 | Manage contact persons | Section 6.3.6.1, 5.11 | 78-79, 271-273 |
| US-CERT-011 | Communicate with establishment | Section 6.3.6.1, 6.3.8, 6.3.8.1 | 271-273, 292-294 |
| US-CERT-012 | Log violations | Section 6.3.6.1 | 271-273 |
| US-CERT-013 | View and manage control plan | Section 6.3.4.4.3, 6.3.6.1, 5.10 | 88-91, 261-263, 271-273 |
| US-CERT-014 | Execute monitoring actions | Section 6.3.6.1 | 271-273 |
| US-CERT-015 | Schedule monitoring meetings | Section 6.3.6.1 | 271-273 |
| US-CERT-016 | Amend establishment profile | Section 6.3.6.1 | 271-273 |
| US-CERT-017 | Raise revalidation request | Section 6.3.6.1, 6.3.6.2 | 271-274 |
| US-CERT-018 | Approve revalidation request | Section 6.3.6.2 | 273-274 |
| US-CERT-019 | Prepare re-assessment plan | Section 6.3.6.2, 6.3.6.2.1 | 273-274 |
| US-CERT-020 | Conduct revalidation | Section 6.3.6.2, 6.3.6.2.2 | 273-275 |
| US-CERT-021 | Post-revalidation decision | Section 6.3.5.1, 6.3.6.2.3, 6.3.6.2.4, 6.3.6.2.5 | 270, 276-285 |
| US-CERT-022 | Suspend certificate | Section 6.2.6.2, 6.2.6.3, 6.3.5.1, 6.3.5.2 | 203-205, 270-271 |
| US-CERT-023 | Revoke certificate | Section 6.2.6.2, 6.2.6.3, 6.3.5.1, 6.3.5.2 | 203-205, 270-271 |
| US-CERT-024 | Continue status after suspension | Section 6.2.6.2, 6.2.6.3, 6.3.5.1, 6.3.5.2 | 203-205, 270-271 |
| US-CERT-025 | Submit appeal | Section 5.12, 6.3.7.3 | 92-94, 291-292 |
| US-CERT-026 | Track appeal status | Section 6.3.7.2, 6.3.7.3 | 287-292 |
| US-CERT-027 | Respond to returned appeal | Section 6.3.7.1, 6.3.7.2, 6.3.7.3 | 285-292 |
| US-CERT-028 | Request hearing | Section 6.3.7.1, 6.3.7.3, 5.12 | 92-94, 285-292 |
| US-CERT-029 | Participate in hearing | Section 6.3.7.1, 6.3.7.2, 6.3.7.3, 5.12 | 92-94, 285-292 |
| US-CERT-030 | Object and escalate | Section 6.3.7.1, 6.3.7.2, 6.3.7.3 | 285-292 |
| US-CERT-031 | Review appeal completeness | Section 6.3.7.1, 6.3.7.3, 5.12 | 92-94, 285-292 |
| US-CERT-032 | Make appeal decision | Section 6.3.7.1, 6.3.7.3, 5.12 | 92-94, 285-292 |
| US-CERT-033 | Schedule hearing | Section 6.3.7.1, 6.3.7.3, 5.12 | 92-94, 285-292 |
| US-CERT-034 | Conduct hearing | Section 6.3.7.1, 6.3.7.2, 6.3.7.3, 5.12 | 92-94, 285-292 |
| US-CERT-035 | Post-hearing decision | Section 6.3.7.1, 6.3.7.2 | 285-292 |
| US-CERT-036 | Review escalated appeal | Section 6.3.7.1, 6.3.7.2, 6.3.7.3 | 285-292 |
| US-CERT-037 | Federal appeal decision | Section 6.3.7.1, 6.3.7.2 | 285-292 |

---

## Next Steps

**Phase 4 is now complete.** This completes the core AEO lifecycle phases. Additional phases may include:

**Phase 5: System Administration & Configuration** (if required)
- Estimated 15-20 user stories covering:
  - Question Bank Management
  - SAQ Template Management
  - Benefits and Benefits Groups Management
  - Risks Lookup Management
  - Violations Lookup Management
  - Control Plan Actions Lookup Management
  - Mutual Recognition Agreements (MRA) Management
  - User and Role Management
  - System Settings Configuration
  - Notifications and Reminders Configuration

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 07, 2025 | AEO Project Team | Initial version - Phase 4 Certification & Post-Certification Management User Stories |

---

**End of Phase 4 User Stories Document**
# AEO Management System - User Stories
## Phase 5: Certificate Management & Appeals

**Document Version:** 1.0  
**Date:** November 7, 2025  
**Project:** Authorized Economic Operator (AEO) Management System  
**Source Documents:**  
- Business Requirements Document (BRD) V1.11  
- System Requirements Document (SRD) V1.2.5

---

## Document Overview

### Purpose
This document consolidates the user stories for **Phase 5: Certificate Management & Appeals** of the AEO Management System. All stories are sourced strictly from BRD V1.11 and SRD V1.2.5 and maintain direct traceability to the originating requirements.

### Scope
Phase 5 covers:
- Certificate portfolio presentation and download for commercial establishments
- Certificate lifecycle control, suspension, revocation, and continuation by customs authorities
- Appeal submission, review, hearing, escalation, and closure
- Notifications, auditability, and SLA enforcement across certificate and appeal processes

### User Roles

#### AEO Portal (Commercial Establishment)
- **Commercial Establishment Account Manager:** Manages certificates, submits and tracks appeals
- **Authorized Establishment Users:** View certificates and communications aligned with their granted roles

#### Local Customs Portal
- **Appeals Officer:** Validates appeal submissions, manages hearing logistics, documents outcomes
- **AEO Program Manager:** Decides on appeal outcomes and certificate statuses
- **Key Account Manager:** Coordinates ongoing certificate oversight and communicates with establishments

#### Federal Customs Portal
- **Federal Administrator / Senior Federal Administrator:** Issues AEO certificates and ensures metadata integrity
- **Federal Appeals Reviewer:** Handles escalated appeals from local customs

---

## Table of Contents
1. [AEO Portal - Certificate Lifecycle](#aeo-portal-certificate-lifecycle)
2. [AEO Portal - Appeals Management](#aeo-portal-appeals-management)
3. [Local Customs Portal - Certificate Control](#local-customs-portal-certificate-control)
4. [Local Customs Portal - Appeals Operations](#local-customs-portal-appeals-operations)
5. [Federal Customs Portal - Certificate Issuance & Escalations](#federal-customs-portal-certificate-issuance--escalations)

---

<a name="aeo-portal-certificate-lifecycle"></a>
## 1. AEO Portal - Certificate Lifecycle

### Epic: Certificate Portfolio Visibility
**Goal:** Enable certified establishments to view and manage official AEO certificates for all approved trade licenses.

---

#### **US-P5-AEO-001: View Certificate Portfolio**

**User Story:**  
As a **commercial establishment account manager**, I want to **view the official AEO certificates issued to my organization and its branches**, so that **I can confirm certification details and status for each trade license**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.3 - Issuance of the AEO Certificate; Section 4.9 - AEO Certificate Data | SRD: Section 6.2.6.1; Section 6.2.6.2; Section 5.20]

**Business Rules:**  
- Certificate numbers must follow `AE-AEO-<issuing customs code>-<6-digit serial>` and remain unique for each establishment, including branches `[BRD: Section 4.9; SRD: Section 5.20]`

**Acceptance Criteria:**
1. Once the federal administrator issues certificate(s), the portal displays a certificate summary per approved trade license with the trade license number, establishment names (Arabic/English), issuing authority, issue date, certificate number, QR code, and current status. `[SRD: 6.2.6.1; 5.20]`
2. If the AEO authorization request covers a head office and branches, the portfolio lists each certificate record separately and labels the associated trade license. `[SRD: 6.2.6.1]`
3. The certificate summary presents lifecycle statuses strictly from the catalog “AEO Certificate Under Issuance”, “AEO Certified”, “AEO Status Suspended”, “AEO Status Revoked”, and “AEO Status Cancelled”, with status timestamps aligned to the audit trail. `[SRD: 6.2.6.2]`
4. The view surfaces the issuing local customs authority and issue date exactly as they appear on the official certificate template. `[SRD: 5.20]`

**Dependencies:**  
- US-CERT-001 (Phase 4)  
- US-P5-FED-001

---

#### **US-P5-AEO-002: Download Official Certificate**

**User Story:**  
As a **commercial establishment account manager**, I want to **download the official AEO certificate for any approved trade license**, so that **I can furnish proof of certification to partners and regulators**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.3 - Issuance of the AEO Certificate; Section 4.9 - AEO Certificate Data | SRD: Section 6.2.6.1; Section 5.20]

**Business Rules:**  
- Official certificates must display bilingual establishment names, issuing authority, certificate number, issue date, and QR code in accordance with the approved template. `[BRD: Section 4.9; SRD: Section 5.20]`

**Acceptance Criteria:**
1. When a certificate record holds the status “AEO Certified”, the system enables a download action in the AEO portal. `[SRD: 6.2.6.1; 6.2.6.2]`
2. The downloaded certificate reproduces all mandatory data elements defined in the AEO certificate data dictionary, including bilingual establishment names and issuing authority. `[SRD: 5.20]`
3. The embedded QR code in the certificate links to the certificate metadata stored in the system and is rendered in the downloaded copy. `[SRD: 5.20]`
4. The system enforces the certificate number format and prevents alteration of the issued certificate content. `[SRD: 5.20]`

**Dependencies:**  
- US-P5-AEO-001  
- US-P5-FED-002

---

#### **US-P5-AEO-003: Monitor Certificate Status History**

**User Story:**  
As a **commercial establishment account manager**, I want to **review the historical status changes for each certificate**, so that **I can understand suspensions, revocations, or reinstatements applied to my AEO status**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.4 - Continuous Monitoring & Performance Evaluation; Section 4.9 - AEO Certificate Data | SRD: Section 6.2.6.2; Section 6.2.7.1]

**Business Rules:**  
- Status transitions are recorded in the audit trail alongside the triggering authority. `[SRD: 6.2.6.2]`

**Acceptance Criteria:**
1. The certificate detail view displays a chronological history of status transitions using the defined lifecycle statuses, with start and end timestamps recorded. `[SRD: 6.2.6.2]`
2. When revalidation decisions affect the certificate, the history highlights the resulting continuation, suspension, or revocation in line with commercial establishment status outcomes. `[SRD: 6.2.7.1]`
3. Each history entry identifies the authority responsible (senior federal administrator or AEO Program Manager) based on the status definition. `[SRD: 6.2.6.2; 6.3.5.1]`
4. Users can download an audit extract of the certificate status history for compliance evidence. `[SRD: 6.2.6.2]`

**Dependencies:**  
- US-P5-AEO-001  
- US-P5-LC-006  
- US-P5-LC-007

---

#### **US-P5-AEO-004: Receive Certificate Lifecycle Notifications**

**User Story:**  
As a **commercial establishment account manager**, I want to **receive timely notifications whenever my certificate status changes**, so that **I can react to issuance, suspension, revocation, or continuation decisions**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.3 - Issuance of the AEO Certificate; Section 3.4 - Continuous Monitoring & Performance Evaluation | SRD: Section 6.2.6.3]

**Business Rules:**  
- Notifications must be delivered via both email and the AEO portal inbox. `[SRD: 6.2.6.3]`

**Acceptance Criteria:**
1. The system sends separate notifications for “Certificate Under Issuance”, “Certificate(s) Issued”, “Certificate Suspended”, “Certificate Revoked”, and “Certificate Continued” events to the commercial establishment account manager. `[SRD: 6.2.6.3]`
2. Each notification includes the affected trade license, certificate number, status effective date, and a link to the certificate record. `[SRD: 6.2.6.3; 5.20]`
3. Notifications are delivered simultaneously through email and the AEO portal notification center. `[SRD: 6.2.6.3]`
4. Notification history is retained and accessible within the portal for audit purposes. `[SRD: 6.2.6.3]`

**Dependencies:**  
- US-P5-AEO-001  
- US-P5-LC-006  
- US-P5-LC-007  
- US-P5-FED-001

---

<a name="aeo-portal-appeals-management"></a>
## 2. AEO Portal - Appeals Management

### Epic: Appeals Self-Service
**Goal:** Provide commercial establishments with a governed, self-service channel to submit, track, and escalate appeals.

---

#### **US-P5-AEO-005: Initiate Appeal Request**

**User Story:**  
As a **commercial establishment account manager**, I want to **submit an appeal against adverse AEO decisions**, so that **I can formally contest rejections, suspensions, or revocations**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 4.11 - Appeals Data | SRD: Section 6.2.8]

**Business Rules:**  
- Appeals must be submitted within 30 days from the notification date of the decision. `[BRD: Section 6 - Business Rules (BR.20); SRD: 6.2.8]`

**Acceptance Criteria:**
1. The “Submit Appeal Request” action becomes available when the establishment receives a decision for AEO authorization rejection, AEO status rejection, suspension, or revocation. `[SRD: 6.2.8]`
2. The system enforces the 30-day submission window by disabling new appeal requests once the grace period lapses. `[BRD: BR.20; SRD: 6.2.8]`
3. Users must choose the reason for appeal from the controlled list aligned with the four decision types. `[SRD: 6.2.8; 5.12]`
4. Successful submission records the appeal against the relevant application or certificate and sets status to “Appeal Request Submitted”. `[SRD: 6.2.8.1]`

**Dependencies:**  
- US-P5-AEO-004  
- US-P5-LC-001

---

#### **US-P5-AEO-006: Provide Appeal Details and Evidence**

**User Story:**  
As a **commercial establishment account manager**, I want to **document the justification for my appeal and attach supporting evidence**, so that **customs authorities can evaluate the objection comprehensively**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 4.11 - Appeals Data | SRD: Section 6.2.8; Section 5.12]

**Business Rules:**  
- Appeal reference numbers follow `AEO-APL-<Year>-<4-digit sequential>` and are system generated. `[SRD: 5.12]`

**Acceptance Criteria:**
1. The appeal form requires the user to provide narrative details describing the grounds for objection. `[SRD: 5.12]`
2. Users can upload supporting documentation in the allowed formats to substantiate the appeal; attachments are optional but limited per policy. `[SRD: 5.12]`
3. The system auto-populates submission date and generates the appeal reference number using the prescribed format. `[SRD: 5.12]`
4. The appeal record links to the originating decision and is available for local customs review. `[SRD: 6.2.8]`

**Dependencies:**  
- US-P5-AEO-005  
- US-P5-LC-001

---

#### **US-P5-AEO-007: Track Appeal Status and Deadlines**

**User Story:**  
As a **commercial establishment account manager**, I want to **monitor appeal progress and remaining response timeframes**, so that **I meet SLA obligations and know when actions are required**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 6 - Business Rules (BR.20, BR.22) | SRD: Section 6.2.8.1; Section 6.2.8.2]

**Business Rules:**  
- Returned appeals must be actioned before the SLA expires or the system closes the appeal automatically. `[SRD: 6.2.8.1]`

**Acceptance Criteria:**
1. The appeal detail page displays the current workflow status drawn from “Appeal Request Submitted”, “Appeal Request Under Review”, “Appeal Request Returned”, “Appeal Hearing Session Requested”, “Appeal Hearing Session Scheduled”, “Hearing Session MOM Shared”, “Appeal Request Approved”, “Appeal Request Rejected”, “Appeal Rejected Automatically”, and “Escalated to General Department of Customs”. `[SRD: 6.2.8.1]`
2. When an appeal is returned, the portal highlights the remarks from customs and shows the remaining SLA in days before automatic closure. `[SRD: 6.2.8.1]`
3. The portal provides a notification log covering submission, return, approval, rejection, hearing scheduling, minutes sharing, automatic rejection, grace period expiry, and escalation events. `[SRD: 6.2.8.2]`
4. Appeals closed automatically due to SLA breaches are clearly labeled, and users are informed of the closure reason. `[SRD: 6.2.8.1]`

**Dependencies:**  
- US-P5-AEO-005  
- US-P5-LC-001  
- US-P5-LC-003  
- US-P5-LC-004

---

#### **US-P5-AEO-008: Request Hearing Session**

**User Story:**  
As a **commercial establishment account manager**, I want to **request a hearing session when my appeal is initially rejected**, so that **I can present additional arguments to the relevant customs department**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 6 - Business Rules (BR.21, BR.26) | SRD: Section 6.2.8; Section 6.2.8.1]

**Business Rules:**  
- Hearing requests must be submitted within the policy-defined window following rejection, and customs must provide advance notice per system settings. `[BRD: BR.21; BR.26]`

**Acceptance Criteria:**
1. When an appeal transitions to “Appeal Request Rejected”, the portal offers a “Request Hearing Session” action to the establishment. `[SRD: 6.2.8.1]`
2. Submitting the request updates the appeal status to “Appeal Hearing Session Requested” and notifies the relevant customs department. `[SRD: 6.2.8.1; 6.2.8.2]`
3. The request captures a short justification from the establishment explaining the need for a hearing. `[SRD: 5.12]`
4. The system prevents duplicate hearing requests for the same appeal case. `[SRD: 6.2.8.1]`

**Dependencies:**  
- US-P5-AEO-007  
- US-P5-LC-003

---

#### **US-P5-AEO-009: Review Hearing Minutes and Submit Arguments**

**User Story:**  
As a **commercial establishment account manager**, I want to **review the minutes of the hearing session and provide additional arguments if needed**, so that **my appeal reflects the official discussion outcomes**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 6 - Business Rules (BR.22) | SRD: Section 6.2.8; Section 5.12]

**Business Rules:**  
- Additional arguments must be submitted within seven days of the hearing minutes being shared. `[BRD: BR.22; SRD: 6.2.8]`

**Acceptance Criteria:**
1. Once customs shares the hearing minutes, the portal updates the status to “Hearing Session MOM Shared” and exposes the document to the establishment. `[SRD: 6.2.8.1]`
2. The establishment can add supplementary arguments and attach supporting documents while the seven-day window remains open. `[SRD: 5.12; BRD: BR.22]`
3. After seven days elapse or upon confirmation of no further arguments, the system locks additional input and routes the appeal back to the AEO Program Manager for decision. `[SRD: 6.2.8.1; BRD: BR.22]`
4. All responses are date-stamped and retained within the appeal record. `[SRD: 6.2.8]`

**Dependencies:**  
- US-P5-AEO-008  
- US-P5-LC-004

---

#### **US-P5-AEO-010: Escalate Appeal to General Department**

**User Story:**  
As a **commercial establishment account manager**, I want to **escalate my appeal to the General Department of Customs when the rejection is upheld**, so that **a federal-level decision can be obtained**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 4.11 - Appeals Data | SRD: Section 6.2.8]

**Business Rules:**  
- Escalation is permitted only after completion of the local hearing and formal rejection confirmation. `[SRD: 6.2.8]`

**Acceptance Criteria:**
1. Following an upheld rejection, the portal enables an “Escalate to General Department of Customs” action that captures escalation remarks and optional supporting documents. `[SRD: 6.2.8; 5.12]`
2. Submitting the escalation updates the status to “Escalated to General Department of Customs” and notifies both local and federal customs stakeholders. `[SRD: 6.2.8.1; 6.2.8.2]`
3. Escalation records include the appeal history, hearing minutes, and attachments for federal review. `[SRD: 6.2.8]`
4. The system prevents reopening the local appeal workflow after escalation. `[SRD: 6.2.8.1]`

**Dependencies:**  
- US-P5-AEO-009  
- US-P5-FED-003

---

<a name="local-customs-portal-certificate-control"></a>
## 3. Local Customs Portal - Certificate Control

### Epic: Certificate Lifecycle Enforcement
**Goal:** Equip local customs teams with capabilities to control certificate status and notify stakeholders.

---

#### **US-P5-LC-001: Validate Appeal Submissions**

**User Story:**  
As an **appeals officer**, I want to **review newly submitted appeals for completeness**, so that **only valid appeals proceed to decision-making**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 4.11 - Appeals Data | SRD: Section 6.3.7.1; Section 5.12]

**Business Rules:**  
- Appeals exceeding the 30-day submission window must be rejected. `[BRD: BR.20; SRD: 6.2.8]`

**Acceptance Criteria:**
1. Newly received appeals appear in the local customs work queue with full submission details and attachments. `[SRD: 6.3.7.1]`
2. The appeals officer can mark the appeal as complete and assign it to the AEO Program Manager, transitioning the status to “Appeal Under Review”. `[SRD: 6.2.8.1; 6.3.7.1]`
3. If the appeal is incomplete, the officer can add remarks and return it to the establishment, changing the status to “Appeal Request Returned”. `[SRD: 6.2.8.1; 6.3.7.1]`
4. Returning an appeal records the reason and starts the SLA countdown for the establishment response. `[SRD: 6.2.8.1]`

**Dependencies:**  
- US-P5-AEO-005  
- US-P5-AEO-006

---

#### **US-P5-LC-002: Provide Appeal Recommendation**

**User Story:**  
As an **appeals officer**, I want to **add a recommendation to approve or reject an appeal**, so that **the AEO Program Manager can make an informed decision**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 4.11 - Appeals Data | SRD: Section 6.3.7.1; Section 5.12]

**Business Rules:**  
- Recommendations must capture justification remarks. `[SRD: 5.12]`

**Acceptance Criteria:**
1. Once an appeal is deemed complete, the appeals officer can select a recommendation outcome (approve/reject) and record supportive remarks. `[SRD: 6.3.7.1; 5.12]`
2. Submitting the recommendation routes the appeal to the AEO Program Manager with status “Appeal Under Review”. `[SRD: 6.3.7.1; 6.2.8.1]`
3. All recommendations are logged and visible within the appeal history trail. `[SRD: 6.2.8.1]`

**Dependencies:**  
- US-P5-LC-001  
- US-P5-LC-005

---

#### **US-P5-LC-003: Schedule Hearing Sessions**

**User Story:**  
As an **appeals officer**, I want to **schedule hearing sessions within mandated timeframes**, so that **establishments receive fair opportunities to present their case**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 6 - Business Rules (BR.21, BR.26) | SRD: Section 6.3.7.1; Section 5.12]

**Business Rules:**  
- Hearing sessions must be scheduled within 15 days of the request and with sufficient advance notice defined in system settings. `[BRD: BR.21; BR.26]`

**Acceptance Criteria:**
1. When a hearing request is received, the appeals officer can create a hearing schedule capturing title, purpose, date, start time, and expected duration. `[SRD: 5.12; 6.3.7.1]`
2. The system validates the scheduled date against the 15-day policy window and advance-notice requirement, preventing non-compliant entries. `[BRD: BR.21; BR.26; SRD: 6.3.7.1]`
3. Scheduling the hearing updates the appeal status to “Appeal Hearing Session Scheduled” and notifies the establishment with invitation details. `[SRD: 6.2.8.1; 6.2.8.2]`
4. The hearing schedule is visible to the AEO Program Manager and appears in the customs calendar. `[SRD: 6.3.7.1]`

**Dependencies:**  
- US-P5-AEO-008  
- US-P5-AEO-007

---

#### **US-P5-LC-004: Document Hearing Minutes and Follow-up**

**User Story:**  
As an **appeals officer**, I want to **record the minutes of the hearing session and manage follow-up actions**, so that **the appeal case file reflects the official discussion outcomes**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process; Section 4.11 - Appeals Data | SRD: Section 6.3.7.1; Section 5.12]

**Business Rules:**  
- Additional arguments must be accepted within seven days of sharing the minutes. `[BRD: BR.22]`

**Acceptance Criteria:**
1. After a hearing concludes, the appeals officer records the minutes of meeting and shares them with the establishment, setting status to “Hearing Session MOM Shared”. `[SRD: 6.2.8.1; 6.3.7.1]`
2. The system allows the establishment to submit additional arguments within the seven-day window and captures them in the appeal record. `[BRD: BR.22; SRD: 6.2.8.1]`
3. If the establishment fails to attend the hearing, the officer records non-attendance, and the system marks the appeal as “Appeal Rejected Automatically”. `[SRD: 6.2.8.1]`
4. Once follow-up is complete, the appeal is reassigned to the AEO Program Manager for final decision. `[SRD: 6.3.7.1]`

**Dependencies:**  
- US-P5-LC-003  
- US-P5-AEO-009  
- US-P5-AEO-007

---

#### **US-P5-LC-005: Decide Appeals and Update Linked Processes**

**User Story:**  
As an **AEO Program Manager**, I want to **approve or reject appeals and cascade outcomes to related processes**, so that **membership decisions remain synchronized across the system**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process | SRD: Section 6.3.7.1]

**Business Rules:**  
- Decision remarks are mandatory, especially for rejections. `[SRD: 5.12]`

**Acceptance Criteria:**
1. The AEO Program Manager can accept an appeal, triggering automatic acceptance of the underlying AEO authorization request or continuation of the AEO status, and assigning subsequent tasks (validation team assignment or key account team assignment). `[SRD: 6.3.7.1]`
2. Rejected appeals require the program manager to enter justification, set status to “Appeal Request Rejected”, and notify the establishment. `[SRD: 6.3.7.1; 6.2.8.1; 6.2.8.2]`
3. Returning an appeal to the appeals officer for further action captures remarks and maintains audit traceability. `[SRD: 6.3.7.1]`
4. All decisions update the appeal history and related certificate or application statuses accordingly. `[SRD: 6.3.7.1; 6.2.6.2]`

**Dependencies:**  
- US-P5-LC-002  
- US-P5-LC-004  
- US-P5-AEO-007

---

#### **US-P5-LC-006: Manage Certificate Suspension**

**User Story:**  
As an **AEO Program Manager**, I want to **suspend a certificate when compliance issues are detected**, so that **the AEO status reflects temporary restrictions**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.4 - Continuous Monitoring & Performance Evaluation | SRD: Section 6.3.5.1; Section 6.2.6.2]

**Business Rules:**  
- Suspension decisions must be logged with effective dates and reasons for audit. `[SRD: 6.3.5.1]`

**Acceptance Criteria:**
1. The program manager can set the certificate status to “AEO Status Suspended”, recording the effective date and rationale. `[SRD: 6.3.5.1; 6.2.6.2]`
2. Suspending a certificate updates audit records and notifies the establishment and relevant customs teams. `[SRD: 6.2.6.3; 6.3.5.2]`
3. The system displays suspension status in the commercial establishment profile and certificate portfolio. `[SRD: 6.2.6.2; 6.2.10]`
4. Suspension actions are reversible only via continuation or revocation decisions. `[SRD: 6.3.5.1]`

**Dependencies:**  
- US-P5-AEO-003  
- US-P5-AEO-004

---

#### **US-P5-LC-007: Manage Certificate Revocation or Continuation**

**User Story:**  
As an **AEO Program Manager**, I want to **revoke or continue a suspended certificate**, so that **the final status reflects the outcome of monitoring or revalidation**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.4 - Continuous Monitoring & Performance Evaluation | SRD: Section 6.3.5.1; Section 6.2.7.1]

**Business Rules:**  
- Revoked certificates cannot be reused or reassigned to other establishments. `[SRD: 5.20]`

**Acceptance Criteria:**
1. The program manager can reinstate the certificate to “AEO Certified” following successful revalidation or remediation. `[SRD: 6.3.5.1; 6.2.7.1]`
2. The program manager can revoke the certificate permanently, setting status to “AEO Status Revoked” and recording justification. `[SRD: 6.3.5.1; 6.2.6.2]`
3. If the establishment cancels its status, the program manager records “AEO Status Cancelled” as final. `[SRD: 6.2.6.2]`
4. Status changes propagate to the certificate portfolio, notifications, and audit logs. `[SRD: 6.2.6.2; 6.2.6.3; 6.3.5.2]`

**Dependencies:**  
- US-P5-LC-006  
- US-P5-AEO-003  
- US-P5-AEO-004

---

#### **US-P5-LC-008: Notify Stakeholders of Certificate Status Changes**

**User Story:**  
As an **AEO Program Manager**, I want to **ensure all impacted parties are notified of certificate status updates**, so that **federal, local, and commercial stakeholders act on the latest decision**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.3 - Issuance of the AEO Certificate; Section 3.4 - Continuous Monitoring & Performance Evaluation | SRD: Section 6.2.6.3; Section 6.3.5.2]

**Business Rules:**  
- Notifications must list the affected certificate and describe the action taken. `[SRD: 6.3.5.2]`

**Acceptance Criteria:**
1. When certificate status changes, the system notifies local customs departments, federal administrators, and the commercial establishment with action-specific messages. `[SRD: 6.3.5.2; 6.2.6.3]`
2. Notifications include status, effective date, responsible decision-maker, and next steps if applicable. `[SRD: 6.3.5.2]`
3. All notification events are logged in both customs and establishment portals. `[SRD: 6.3.5.2; 6.2.6.3]`

**Dependencies:**  
- US-P5-LC-006  
- US-P5-LC-007  
- US-P5-AEO-004  
- US-P5-FED-001

---

<a name="local-customs-portal-appeals-operations"></a>
## 4. Local Customs Portal - Appeals Operations

### Epic: Appeals Governance
**Goal:** Streamline appeal handling, hearings, and escalations within local customs.

---

*Note: Stories US-P5-LC-001 through US-P5-LC-005 already cover key appeals operations and remain part of this epic.*

---

<a name="federal-customs-portal-certificate-issuance--escalations"></a>
## 5. Federal Customs Portal - Certificate Issuance & Escalations

### Epic: Federal Issuance & Final Review
**Goal:** Enable federal customs to issue certificates, maintain data integrity, and resolve escalated appeals.

---

#### **US-P5-FED-001: Issue AEO Certificates**

**User Story:**  
As a **senior federal administrator**, I want to **issue AEO certificates for approved trade licenses**, so that **commercial establishments receive official certification**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.3 - Issuance of the AEO Certificate; Section 4.9 - AEO Certificate Data | SRD: Section 6.2.6.1; Section 6.3.5]

**Business Rules:**  
- Certificates are issued only after the AEO Program Manager approves granting AEO status. `[SRD: 6.3.5]`

**Acceptance Criteria:**
1. Upon receiving the issuance request, the federal administrator can issue certificates per approved trade license, changing status to “AEO Certificate Under Issuance” and then “AEO Certified”. `[SRD: 6.2.6.1; 6.2.6.2]`
2. The issuance action generates notifications to the establishment and local customs teams. `[SRD: 6.2.6.3; 6.3.5.2]`
3. Issued certificates become visible and downloadable within the AEO portal. `[SRD: 6.2.6.1]`
4. Issuance details populate the certificate data dictionary fields, including issue date and issuing authority. `[SRD: 5.20]`

**Dependencies:**  
- US-CERT-001 (Phase 4)  
- US-P5-AEO-001

---

#### **US-P5-FED-002: Maintain Certificate Metadata Integrity**

**User Story:**  
As a **federal administrator**, I want to **enforce certificate numbering and metadata rules**, so that **each certificate remains unique and compliant with policy**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 4.9 - AEO Certificate Data | SRD: Section 5.20; Section 6.3.5.1]

**Business Rules:**  
- Certificate numbers must remain unique and are never reused after revocation. `[SRD: 5.20]`

**Acceptance Criteria:**
1. The system enforces the certificate numbering format during issuance and blocks duplicate numbers across all establishments. `[SRD: 5.20]`
2. Revoked certificates retain their numbers but cannot be reassigned to other establishments. `[SRD: 5.20]`
3. Metadata updates (e.g., status changes) are synchronized to the certificate data dictionary and audit logs. `[SRD: 6.3.5.1; 5.20]`
4. Administrators can view audit history related to certificate metadata changes. `[SRD: 6.3.5.1]`

**Dependencies:**  
- US-P5-FED-001  
- US-P5-LC-007

---

#### **US-P5-FED-003: Resolve Escalated Appeals**

**User Story:**  
As a **federal appeals reviewer**, I want to **review and decide on escalated appeals**, so that **final decisions are issued at the federal level when required**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.5 - Appeals Process | SRD: Section 6.2.8; Section 6.3.7.1]

**Business Rules:**  
- Federal decisions are final and must be communicated to all stakeholders. `[SRD: 6.2.8]`

**Acceptance Criteria:**
1. Escalated appeals present the full case history, including initial decision, hearing minutes, and additional arguments. `[SRD: 6.2.8]`
2. The federal reviewer can approve or reject the appeal, setting the final status and locking the case. `[SRD: 6.2.8.1]`
3. Approvals update the underlying AEO authorization or status in line with local acceptance logic. `[SRD: 6.2.8; 6.3.7.1]`
4. Rejections remain final, and the system records the decision date, remarks, and notification trail. `[SRD: 6.2.8.1; 6.2.8.2]`

**Dependencies:**  
- US-P5-AEO-010  
- US-P5-LC-005

---

#### **US-P5-FED-004: Communicate Federal Decisions**

**User Story:**  
As a **federal administrator**, I want to **notify local customs and establishments about federal issuance and appeal decisions**, so that **all parties act on the final outcomes**.

**Priority:** Must Have

**Reference:**  
- [BRD: Section 3.3 - Issuance of the AEO Certificate; Section 3.5 - Appeals Process | SRD: Section 6.2.6.3; Section 6.2.8.2]

**Business Rules:**  
- Notifications must specify whether the decision supersedes prior local decisions. `[SRD: 6.2.8.2]`

**Acceptance Criteria:**
1. Federal issuance triggers notifications to local customs and the establishment indicating certificate availability. `[SRD: 6.2.6.3; 6.3.5.2]`
2. Federal appeal decisions generate notifications summarizing the outcome, effective date, and any required follow-up. `[SRD: 6.2.8.2]`
3. Notification history for federal actions is retained alongside local communication logs. `[SRD: 6.2.6.3; 6.2.8.2]`
4. The system highlights when a federal decision overrides a previous local decision to avoid conflicting actions. `[SRD: 6.2.8.2]`

**Dependencies:**  
- US-P5-FED-001  
- US-P5-FED-003  
- US-P5-AEO-004  
- US-P5-AEO-007

---

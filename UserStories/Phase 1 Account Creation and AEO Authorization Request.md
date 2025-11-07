# AEO Management System - User Stories
## Phase 1: Account Creation & AEO Authorization Request

**Document Version:** 1.0  
**Date:** November 7, 2025  
**Project:** Authorized Economic Operator (AEO) Management System  
**Reference Documents:**
- Business Requirements Document (BRD) - V1.11
- System Requirements Document (SRD) - V1.2.5

---

## Table of Contents
1. [Introduction](#introduction)
2. [AEO Portal - User Stories](#aeo-portal---user-stories)
   - 2.1 [Account Creation Process](#21-account-creation-process)
   - 2.2 [AEO Authorization Request Process](#22-aeo-authorization-request-process)
   - 2.3 [User Management](#23-user-management)
3. [Local Customs Portal - User Stories](#local-customs-portal---user-stories)
   - 3.1 [Account Creation Review](#31-account-creation-review)
   - 3.2 [AEO Authorization Request Review](#32-aeo-authorization-request-review)

---

## 1. Introduction

### 1.1 Purpose
This document contains detailed user stories for Phase 1 of the AEO Management System, covering **Account Creation** and **AEO Authorization Request Submission** processes. Each user story is directly traceable to the Business Requirements Document (BRD) and System Requirements Document (SRD) to ensure complete alignment with project requirements.

### 1.2 User Story Format
Each user story follows the enhanced format:
- **User Story ID**: Unique identifier
- **User Story**: As a [role], I want [goal], so that [benefit]
- **Priority**: MoSCoW (Must Have, Should Have, Could Have, Won't Have)
- **Reference**: Traceability to BRD and SRD
- **Business Rules**: Applicable business rules
- **Acceptance Criteria**: Detailed acceptance criteria
- **Dependencies**: Related user stories or external dependencies

### 1.3 Scope
Phase 1 covers the following processes:
- Commercial Establishment Account Creation
- AEO Authorization Request Submission
- User Management within Commercial Establishment Account
- Review and Decision on Account Creation Requests (Local Customs)
- Review and Decision on AEO Authorization Requests (Local Customs)

---

## 2. AEO Portal - User Stories

### 2.1 Account Creation Process

---

#### **US-AEO-001: Access AEO Program Information**

**User Story:**  
As a **prospective commercial establishment representative**, I want to **access general information about the AEO program** on the public portal, so that **I can understand the program objectives, benefits, eligibility requirements, and application process before creating an account**.

**Priority:** Must Have

**Reference:**  
- [BRD: AEO Program Scope | SRD: Section 6.2.1]
- [SRD: Section 1.2 - Scope of the AEO Program, Page 14-15]

**Business Rules:**  
- N/A - This is a public information access feature with no restrictions

**Acceptance Criteria:**
1. The system shall display general information about the AEO program on the public portal without requiring user login
2. The information section shall include:
   - Program objectives and benefits
   - Eligibility requirements for commercial establishments
   - Step-by-step application process overview
   - FAQs and support contact information
   - Official policy documents
   - Educational publications and videos (AEO E-Learning)
   - List of certified national AEOs with filtering capabilities
   - List of MRA countries and their certified AEOs (visible to logged-in users only)
3. The system shall support both Arabic (RTL) and English (LTR) languages
4. The information shall be presented in a user-friendly, accessible format
5. The system shall provide navigation to account creation and login pages
6. The system shall display local and international communication channels

**Dependencies:**
- None (foundational feature)

---

#### **US-AEO-002: Initiate Account Creation with UAE PASS**

**User Story:**  
As an **applicant from a commercial establishment**, I want to **create an account using UAE PASS authentication**, so that **I can leverage my existing UAE PASS credentials for secure and quick account registration without manual data entry**.

**Priority:** Must Have

**Reference:**  
- [BRD: Commercial Establishment Account Creation Process | SRD: Section 4.1.1, Page 33-34]
- [SRD: Section 6.2.2.1 - Submitting Account Creation Request, Page 167-168]
- [SRD: Section 8 - Integration Points (UAE PASS), Page 355]

**Business Rules:**  
- **BR.1**: When submitting a commercial establishment account creation request, the system verifies that no account or pending request is associated with the same email address
- **BR.24**: The system will only allow commercial establishments holding a trade license issued by Abu Dhabi or Dubai to submit account creation requests
- **BR.28**: System must check before submission if the same establishment has a previously submitted request in progress or approved

**Acceptance Criteria:**
1. The system shall provide a "Login with UAE PASS" option on the account creation page
2. Upon selecting UAE PASS authentication, the system shall redirect to UAE PASS login portal
3. The system shall retrieve and auto-populate the following data from UAE PASS:
   - Name in Arabic
   - Name in English
   - Phone Number
   - Email Address (editable by user)
4. The applicant shall manually complete the following mandatory fields:
   - Job Title
   - Role (Owner/Founder OR Authorized Representative)
   - Authorization document (if role is Authorized Representative)
5. The system shall validate that the provided email is not associated with an existing account or pending request
6. The system shall restrict emirate selection to Abu Dhabi and Dubai only in the trade license emirate field
7. Upon successful submission, the system shall:
   - Generate a reference number in format: AEO-REG-YYYY-#### (e.g., AEO-REG-2025-0015)
   - Send email notification to applicant with reference number
   - Allow future login using UAE PASS credentials directly
8. The system shall display appropriate error messages if business rule validations fail

**Dependencies:**
- UAE PASS integration must be operational
- US-AEO-001 (prerequisite: access to program information)

---

#### **US-AEO-003: Initiate Account Creation with Manual Registration**

**User Story:**  
As an **applicant from a commercial establishment**, I want to **create an account by manually entering my information and receiving credentials via email**, so that **I can register for the AEO program without requiring UAE PASS if I prefer traditional registration method**.

**Priority:** Must Have

**Reference:**  
- [BRD: Commercial Establishment Account Creation Process | SRD: Section 4.1.1, Page 33-34]
- [SRD: Section 6.2.2.1 - Submitting Account Creation Request, Page 167-169]
- [SRD: Section 5.1 - Account Creation Request Data, Page 49-55]

**Business Rules:**  
- **BR.1**: System verifies that no account or pending request is associated with the same email address
- **BR.2**: Reference number format must be AEO-REG-[year]-[4-digit sequential number]
- **BR.5**: One-time password (OTP) validity period is 3 minutes
- **BR.24**: Only Abu Dhabi and Dubai trade licenses are permitted
- **BR.28**: System checks for existing in-progress or approved requests

**Acceptance Criteria:**
1. The system shall provide a "Manual Registration" option on the account creation page
2. The applicant shall enter an email address
3. The system shall verify the email is not associated with an existing account or pending request
4. The system shall send a One-Time Password (OTP) to the provided email
5. The OTP shall be valid for 3 minutes
6. Upon successful OTP validation, the system shall display a form requiring:
   
   **Applicant Information:**
   - Name in Arabic (mandatory, Arabic letters only)
   - Name in English (mandatory, English letters only)
   - Job Title (mandatory)
   - Role: Owner/Founder OR Authorized Representative (mandatory)
   - Phone Number with country code (mandatory, default: UAE)
   - Email Address (mandatory, unique)
   - Communication Language (mandatory)
   
   **Commercial Establishment Information:**
   - Commercial Establishment Name in Arabic (mandatory, Arabic letters only)
   - Commercial Establishment Name in English (mandatory, English letters only)
   
   **License Information:**
   - Emirate (mandatory, restricted to Abu Dhabi or Dubai)
   - License Issuer (mandatory, filtered by emirate selection)
   - License Number (mandatory)
   
   **Attachments:**
   - Valid License (mandatory, PDF/PNG/JPG/JPEG, max 5MB)
   - Copy of Applicant's Emirates ID (mandatory, PDF/PNG/JPG/JPEG, max 5MB)
   - Authorization Document (mandatory if role is Authorized Representative, PDF/PNG/JPG/JPEG, max 5MB)

7. The system shall validate all mandatory fields and file formats/sizes before submission
8. Upon successful submission, the system shall:
   - Generate reference number in format: AEO-REG-YYYY-####
   - Record submission date automatically
   - Send email confirmation with reference number to applicant
9. The applicant shall be able to cancel the request before submission, which deletes all entered data
10. Upon approval by customs department, the system shall:
    - Generate username (identical to provided email)
    - Generate secure password (16 characters, alphanumeric with special characters)
    - Send credentials via email
    - Require password change at first login

**Dependencies:**
- Email service integration must be operational
- File upload functionality must support specified formats and size limits
- US-AEO-001 (prerequisite: access to program information)

---

#### **US-AEO-004: Track Account Creation Request Status**

**User Story:**  
As an **applicant**, I want to **track the status of my account creation request using the reference number**, so that **I can monitor the progress and know when my account is approved or if any action is required**.

**Priority:** Must Have

**Reference:**  
- [BRD: Account Creation Process | SRD: Section 4.1.1, Page 33-34]
- [SRD: Section 6.2.2.2 - Tracking Account Creation Request, Page 170]
- [SRD: Section 5.2 - Tracking Data, Page 56]

**Business Rules:**  
- **BR.2**: Reference number format is AEO-REG-[year]-[4-digit sequential number]

**Acceptance Criteria:**
1. The system shall provide a "Track My Request" option accessible from the public portal without login
2. The tracking page shall require:
   - Reference Number (mandatory)
   - Mobile Number used during registration (mandatory)
3. The system shall validate that the mobile number matches the one registered with the reference number
4. If mobile number doesn't match, system shall display error message: "Please enter the correct mobile number"
5. Upon successful validation, the system shall display:
   - Commercial Establishment Name in Arabic (auto-filled)
   - Commercial Establishment Name in English (auto-filled)
   - Trade License Number (auto-filled)
   - Request Submission Date (auto-filled)
   - Current Status of Request (auto-filled from status workflow)
   - Customs Response Date (auto-filled when applicable)
   - Rejection Reason (auto-filled if rejected)
   - Remarks from customs (auto-filled if provided)
6. The system shall display status history showing all status transitions
7. The tracking information shall be available in both Arabic and English based on user language preference

**Dependencies:**
- US-AEO-002 or US-AEO-003 (prerequisite: account creation request must be submitted)

---

#### **US-AEO-005: Receive Account Creation Request Notifications**

**User Story:**  
As an **applicant**, I want to **receive email notifications at key milestones of my account creation request**, so that **I am promptly informed of status changes without needing to constantly check the portal**.

**Priority:** Must Have

**Reference:**  
- [BRD: Communication and Notifications | SRD: Section 4.1.1, Page 33-34]
- [SRD: Section 6.2.2.9 - Notifications, Page 175]

**Business Rules:**  
- N/A - Notification triggers are event-based

**Acceptance Criteria:**
1. The system shall send email notification upon account creation request submission containing:
   - Confirmation of successful submission
   - Reference number for tracking
   - Estimated review timeline
2. The system shall send email notification upon account approval containing:
   - Confirmation of approval
   - Username (if manual registration)
   - Temporary password (if manual registration)
   - Instructions for first login
   - Link to AEO portal
3. The system shall send email notification upon account rejection containing:
   - Confirmation of rejection
   - Reason for rejection
   - Remarks from customs department
   - Instructions for submitting a new request if applicable
4. The system shall send email notification upon user account creation by Account Manager containing:
   - Welcome message
   - Username
   - Temporary password
   - Role(s) assigned
   - Instructions for first login
5. All notifications shall be sent in the applicant's preferred communication language
6. Email notifications shall include official AEO program branding
7. The system shall maintain notification delivery logs for audit purposes

**Dependencies:**
- US-AEO-002 or US-AEO-003 (account creation request submission)
- Email service must be configured and operational

---

#### **US-AEO-006: Login to Commercial Establishment Account with UAE PASS**

**User Story:**  
As a **Commercial Establishment Account Manager or authorized user**, I want to **login to my commercial establishment account using UAE PASS**, so that **I can securely access the AEO portal without managing separate credentials**.

**Priority:** Must Have

**Reference:**  
- [BRD: Account Access | SRD: Section 6.2.2.1, Page 168-169]
- [SRD: Section 8 - Integration Points (UAE PASS), Page 355]

**Business Rules:**  
- N/A - Login process follows UAE PASS authentication standards

**Acceptance Criteria:**
1. The system shall provide "Login with UAE PASS" option on the login page
2. Upon selecting UAE PASS login, system shall redirect to UAE PASS authentication portal
3. Upon successful UAE PASS authentication, system shall:
   - Validate user has approved commercial establishment account
   - Redirect user to commercial establishment dashboard
   - Display user role and permissions
4. The system shall maintain user session securely
5. The system shall log all login attempts for audit purposes
6. If authentication fails, system shall display appropriate error message
7. The system shall support session timeout with configurable duration

**Dependencies:**
- US-AEO-002 (account must be created with UAE PASS and approved)
- UAE PASS integration must be operational

---

#### **US-AEO-007: Login to Commercial Establishment Account with Username and Password**

**User Story:**  
As a **Commercial Establishment Account Manager or authorized user**, I want to **login to my commercial establishment account using username and password**, so that **I can access the AEO portal using traditional credentials-based authentication**.

**Priority:** Must Have

**Reference:**  
- [BRD: Account Access | SRD: Section 6.2.2.1, Page 168-169]
- [SRD: Section 5.3 - User Account Data, Page 56-58]

**Business Rules:**  
- **BR.4**: Username format is identical to the provided email in account creation request

**Acceptance Criteria:**
1. The system shall provide "Login with Username and Password" option on the login page
2. The login form shall require:
   - Username (email address)
   - Password
3. The system shall validate credentials against stored user accounts
4. Upon first login with temporary password, system shall:
   - Force user to change password
   - Require new password different from temporary password
   - Require password confirmation (retype)
   - Validate new password meets security requirements (16 characters, alphanumeric with special characters)
5. Upon successful authentication, system shall:
   - Redirect user to commercial establishment dashboard
   - Display user role(s) and permissions
   - Log successful login event
6. The system shall implement account lockout after specified number of failed login attempts
7. The system shall provide "Forgot Password" link for password recovery
8. The system shall maintain secure session management
9. If authentication fails, system shall display generic error message without revealing whether username or password is incorrect

**Dependencies:**
- US-AEO-003 (account must be created manually and approved)

---

#### **US-AEO-008: Reset Password via Forgot Password Option**

**User Story:**  
As a **Commercial Establishment user who uses username/password authentication**, I want to **reset my password if I forget it**, so that **I can regain access to my account without contacting support**.

**Priority:** Must Have

**Reference:**  
- [BRD: Account Security | SRD: Section 6.2.2.6, Page 173]

**Business Rules:**  
- N/A - Password reset follows secure authentication flow

**Acceptance Criteria:**
1. The system shall provide "Forgot Password" option on the login page
2. This option shall ONLY be available for users who selected "Login with username and password" during registration
3. This option shall NOT be available for users who login with UAE PASS
4. Upon clicking "Forgot Password", system shall display form requiring:
   - Registered email address (mandatory)
5. The system shall verify the provided email is registered in the system
6. If email is registered, system shall:
   - Allow user to create new password
   - Require new password to be different from forgotten password
   - Require password confirmation (retype)
   - Validate password meets security requirements (16 characters, alphanumeric with special characters)
   - Update user password in system
7. If email is not registered, system shall display error message
8. The system shall send confirmation email after successful password reset
9. The system shall invalidate any active sessions for that user account
10. The system shall log password reset events for audit purposes

**Dependencies:**
- US-AEO-007 (user must have username/password authentication method)
- Email service must be operational

---

#### **US-AEO-009: Change Password from User Profile**

**User Story:**  
As a **Commercial Establishment user who uses username/password authentication**, I want to **change my password at any time from my profile**, so that **I can maintain account security by updating credentials periodically**.

**Priority:** Must Have

**Reference:**  
- [BRD: Account Security | SRD: Section 6.2.2.5, Page 172-173]

**Business Rules:**  
- N/A - Password change is security best practice

**Acceptance Criteria:**
1. The system shall provide "Change Password" option in the user profile page
2. This option shall ONLY be available for users who selected "Login with username and password"
3. This option shall NOT be available for users who login with UAE PASS
4. The change password form shall require:
   - Current password (mandatory)
   - New password (mandatory)
   - Confirm new password (mandatory)
5. The system shall validate:
   - Current password is correct
   - New password is different from current password
   - New password meets security requirements (16 characters, alphanumeric with special characters)
   - New password confirmation matches new password
6. Upon successful password change, system shall:
   - Update password in database
   - Send confirmation email to registered email address
   - Log password change event
7. The system shall display appropriate error messages for validation failures
8. The system shall maintain user session after successful password change

**Dependencies:**
- US-AEO-007 (user must be logged in with username/password method)

---

### 2.2 AEO Authorization Request Process

---

#### **US-AEO-010: Submit New AEO Authorization Request**

**User Story:**  
As a **Commercial Establishment Account Manager or AEO Authorization Request Editor**, I want to **submit a new AEO Authorization Request with all required information and documents**, so that **my commercial establishment can begin the process of obtaining AEO status**.

**Priority:** Must Have

**Reference:**  
- [BRD: AEO Authorization Request Submission Process | SRD: Section 4.1.2, Page 34-35]
- [SRD: Section 6.2.3.1 - Submitting AEO Authorization Request, Page 175-177]
- [SRD: Section 5.4 - AEO Authorization Request Form Data, Page 58-68]

**Business Rules:**  
- **BR.6**: System verifies no existing request under review, accepted request in progress, or active/suspended AEO status
- **BR.8**: Request is automatically assigned to customs department relevant to emirate that issued trade license
- **BR.11**: Reference number format is AEO-AUTH-[year]-[4-digit sequential number]
- **BR.12**: Request can be filled by Account Manager or AEO Authorization Request Editor but must be submitted only by Account Manager
- **BR.13**: System can be configured to allow one request for all branches or separate requests per trade license based on emirate settings

**Acceptance Criteria:**
1. The system shall verify no restrictions exist before allowing new request submission:
   - No existing AEO Authorization Request under review
   - No previously accepted request with establishment undergoing remaining program phases
   - Establishment is not already an AEO with active or suspended status
2. If restrictions exist, system shall display appropriate error message explaining the restriction
3. The system shall display AEO Authorization Request form with following sections:

   **A. Commercial Establishment Details (Auto-filled from Account):**
   - Commercial Establishment Name (Arabic) - Read-only
   - Commercial Establishment Name (English) - Read-only
   - Emirate - Read-only
   - License Issuer - Read-only
   - License Number - Read-only
   - Legal Form (mandatory, single choice from Annex 2)
   - License Issue Date (mandatory)
   - License Expiry Date (mandatory)
   - Customs Code (mandatory)
   - Establishment Date (mandatory)
   - Phone Number (mandatory, default UAE)
   - Website (optional)
   - Emirate of Headquarters (mandatory, defaulted from license emirate, editable)
   - Area (mandatory, filtered by emirate)
   - Detailed Address (mandatory)
   - Valid License document (auto-retrieved from account creation)

   **B. Branch Information:**
   - "Do You Have Branches Active in Supply Chain?" (Yes/No, default No)
   - If Yes, allow adding multiple branches with:
     - Branch Name (Arabic) - mandatory
     - Branch Name (English) - mandatory
     - Emirate - mandatory
     - Legal Form - mandatory
     - License Issuer - mandatory
     - License Number - mandatory
     - License Issue Date - mandatory
     - License Expiry Date - mandatory
     - Customs Code - mandatory
     - Branch Establishment Date - mandatory
     - Area - mandatory
     - Detailed Branch Address - mandatory
     - Valid Branch License - mandatory (PDF/PNG/JPG/JPEG, max 5MB)

   **C. Commercial Establishment Activities:**
   - Supply Chain Activities (mandatory, multiple selection from Annex 3):
     - Importer, Exporter, Manufacturer, Customs Broker, Freight Forwarder, Logistic Service Agent, Ports/Airports Operator, Courier Agent, Warehouse Operator, Freight Terminal Operator, Other Supply Chain Services

   **D. Executive Management and Board:**
   - "Do You Have Executive Management?" (Yes/No, default No)
   - If Yes, add multiple members with: Name (AR/EN), Position (AR/EN), ID/Passport Number, Email, Phone

   **E. Shareholders/Owners:**
   - "Do You Have Shareholders/Owners?" (Yes/No, default No)
   - If Yes, add multiple with: Name (AR/EN), Ownership %, ID/Passport Number, Nationality, Address (AR/EN), Email, Phone

   **F. Accountant Information:**
   - Licensed Accountant Name (AR/EN) - mandatory
   - Office Name (AR/EN) - mandatory
   - License Number - mandatory
   - Validity Period - mandatory
   - Phone - mandatory
   - Email - mandatory

   **G. Customs Procedures and Transactions:**
   - Annual Import Value (mandatory)
   - Annual Export Value (mandatory)
   - Annual Customs Transactions Count (mandatory)

   **H. Applicant Information (Auto-filled, Read-only):**
   - Name, Job Title, Role, Phone, Email

   **I. Attachments (All mandatory, PDF/PNG/JPG/JPEG/XLSX/DOCX, max 5MB each):**
   - Organizational Structure
   - List of Executive Management and Board Members
   - List of Main Shareholders/Owners
   
   **J. Agreement:**
   - Information Exchange Consent (mandatory, must select Yes to submit)

4. The system shall validate all mandatory fields and file formats/sizes
5. Upon submission, system shall:
   - Generate reference number: AEO-AUTH-YYYY-####
   - Record submission date and time
   - Assign request to customs department based on license emirate
   - Send email notification to applicant with reference number
   - Update request status to "AEO Authorization Request Submitted"
6. The system shall allow only Commercial Establishment Account Manager to submit the request
7. The system shall save request as draft if user does not complete submission

**Dependencies:**
- US-AEO-002 or US-AEO-003 (account must be approved and active)
- US-AEO-006 or US-AEO-007 (user must be logged in)

---

#### **US-AEO-011: Save AEO Authorization Request as Draft**

**User Story:**  
As a **Commercial Establishment Account Manager or AEO Authorization Request Editor**, I want to **save my AEO Authorization Request as a draft**, so that **I can complete the form progressively over multiple sessions without losing entered data**.

**Priority:** Must Have

**Reference:**  
- [BRD: AEO Authorization Request Process | SRD: Section 6.2.3.3, Page 178]

**Business Rules:**  
- **BR.7**: There is no defined retention period for drafts in the system; reminders may be sent

**Acceptance Criteria:**
1. The system shall provide "Save as Draft" option on the AEO Authorization Request form
2. The system shall allow saving draft at any point during form completion
3. The system shall save all entered data including:
   - Partially completed form fields
   - Uploaded attachments
   - Added branches, management members, shareholders
4. The system shall NOT validate mandatory fields when saving as draft
5. The system shall display confirmation message upon successful draft save
6. The system shall allow user to resume editing draft from dashboard
7. The system shall display "Draft" status indicator on user dashboard
8. The system shall maintain draft until:
   - User submits the request
   - User deletes the draft
   - User creates new request (replacing draft)
9. The system may send reminder notifications about incomplete drafts
10. The system shall allow multiple users with appropriate roles to access and edit the same draft

**Dependencies:**
- US-AEO-010 (prerequisite: AEO Authorization Request form initiated)

---

#### **US-AEO-012: Track AEO Authorization Request Status**

**User Story:**  
As a **Commercial Establishment Account Manager or AEO Authorization Request Editor**, I want to **view the current status of my AEO Authorization Request**, so that **I can monitor progress and know if any action is required from my side**.

**Priority:** Must Have

**Reference:**  
- [BRD: Request Tracking | SRD: Section 6.2.3.2, Page 178]
- [SRD: Section 6.2.3.6 - Statuses of AEO Authorization Request, Page 181-184]

**Business Rules:**  
- **BR.9**: Relevant customs department must verify all requirements within 30 days from submission date

**Acceptance Criteria:**
1. The system shall display AEO Authorization Request status on the user dashboard
2. The system shall show the following status information:
   - Current Status (with status description)
   - Reference Number
   - Submission Date
   - Last Updated Date
   - Assigned Customs Department
   - Timeline of status changes
3. The system shall support the following statuses visible to commercial establishment:
   - **AEO Authorization Request Submitted**: Awaiting customs review
   - **AEO Authorization Request Under Review**: Under preliminary risk assessment
   - **AEO Authorization Request Returned for Completion**: Requires data correction/completion
   - **AEO Authorization Request Approved**: Approved for validation phase
   - **AEO Authorization Request Rejected**: Application rejected
   - **AEO Authorization Request Withdrawn**: Withdrawn by establishment
   - **AEO Authorization Request Canceled**: Canceled by customs
   - **AEO Authorization Request Expired**: SLA exceeded
4. The system shall display expected action required for statuses needing establishment response
5. The system shall show remaining time for time-bound actions (e.g., 30 days to complete returned request)
6. The system shall provide option to view complete request details in read-only mode
7. The system shall display rejection reasons if request is rejected
8. The system shall show timeline with all status transitions and dates

**Dependencies:**
- US-AEO-010 (AEO Authorization Request must be submitted)

---

#### **US-AEO-013: Withdraw AEO Authorization Request**

**User Story:**  
As a **Commercial Establishment Account Manager**, I want to **withdraw my AEO Authorization Request before it is processed**, so that **I can cancel the application if circumstances change or if I need to resubmit with updated information**.

**Priority:** Must Have

**Reference:**  
- [BRD: Request Management | SRD: Section 6.2.3.4, Page 179]

**Business Rules:**  
- N/A - Withdrawal is establishment's right before final decision

**Acceptance Criteria:**
1. The system shall provide "Withdraw Request" option for AEO Authorization Requests with following statuses:
   - AEO Authorization Request Submitted
   - AEO Authorization Request Under Review
   - AEO Authorization Request Returned for Completion
2. The system shall NOT allow withdrawal for requests with statuses:
   - AEO Authorization Request Approved
   - AEO Authorization Request Rejected
   - AEO Authorization Request Withdrawn (already withdrawn)
   - AEO Authorization Request Canceled
3. Upon clicking "Withdraw Request", system shall:
   - Display confirmation dialog explaining withdrawal is irreversible
   - Require confirmation from Commercial Establishment Account Manager
4. Upon confirmed withdrawal, system shall:
   - Update request status to "AEO Authorization Request Withdrawn"
   - Record withdrawal date and time
   - Record user who performed withdrawal
   - Send notification to establishment users
   - Send notification to assigned customs department
   - Archive request in system
5. The system shall log withdrawal event in audit trail
6. After withdrawal, establishment shall be able to submit new AEO Authorization Request
7. Withdrawn requests shall remain viewable in history but not editable

**Dependencies:**
- US-AEO-010 (AEO Authorization Request must be submitted)
- User must have Commercial Establishment Account Manager role

---

#### **US-AEO-014: Complete and Resubmit Returned AEO Authorization Request**

**User Story:**  
As a **Commercial Establishment Account Manager or AEO Authorization Request Editor**, I want to **complete missing or incorrect information in my returned AEO Authorization Request and resubmit it**, so that **I can address customs department feedback and continue the application process**.

**Priority:** Must Have

**Reference:**  
- [BRD: Request Correction Process | SRD: Section 6.2.3.5, Page 180]
- [SRD: Section 5.4 - Return Reason Data, Page 68]

**Business Rules:**  
- **BR.10**: If request is returned for completion, establishment must complete data within 30 days from return date; if not completed, local customs can reject with "Expired" reason

**Acceptance Criteria:**
1. The system shall notify establishment when request is returned for completion via:
   - Email notification
   - Portal notification
   - Dashboard alert
2. The notification shall include:
   - Return reason from customs
   - Specific remarks/comments from customs officer
   - Fields requiring correction/completion (if specified)
   - Deadline for resubmission (30 days from return date)
3. The system shall display returned request in "Action Required" section on dashboard
4. The system shall allow editing all sections of the returned request except:
   - System-generated fields (reference number, submission date)
   - Trade license number (read-only)
5. The system shall highlight fields identified by customs for correction
6. The system shall display customs comments alongside relevant sections
7. The system shall validate all mandatory fields upon resubmission
8. Upon resubmission, system shall:
   - Update status to "AEO Authorization Request Received After Data Completion"
   - Record resubmission date and time
   - Restart review process with customs department
   - Send notification to customs department
   - Send confirmation to establishment
9. The system shall display countdown timer showing remaining days to complete request
10. If 30-day deadline expires without resubmission, system shall:
    - Enable customs to reject request with "Expired" reason
    - Send expiration notification to establishment
11. The system shall maintain version history showing original and updated data

**Dependencies:**
- US-AEO-010 (AEO Authorization Request submitted)
- Request must be in "Returned for Completion" status

---

#### **US-AEO-015: Receive AEO Authorization Request Notifications**

**User Story:**  
As a **Commercial Establishment Account Manager or AEO Authorization Request Editor**, I want to **receive notifications at all key stages of my AEO Authorization Request**, so that **I am immediately informed of status changes and required actions**.

**Priority:** Must Have

**Reference:**  
- [BRD: Communication and Notifications | SRD: Section 6.2.3.7, Page 184-185]

**Business Rules:**  
- N/A - Notifications are event-driven

**Acceptance Criteria:**
1. The system shall send notifications via:
   - Email
   - AEO Portal (in-app notifications)

2. The system shall send notification upon **Request Submission** containing:
   - Confirmation of successful submission
   - Reference number: AEO-AUTH-YYYY-####
   - Submission date
   - Estimated review timeline (30 days)
   - Next steps in process

3. The system shall send notification upon **Request Under Review** containing:
   - Confirmation that customs department began review
   - Assigned customs department name
   - Expected timeline for preliminary decision

4. The system shall send notification upon **Request Returned for Completion** containing:
   - Notification that request requires additional information
   - Return reason selected by customs
   - Specific remarks from customs officer
   - Fields requiring attention
   - Deadline for completion (30 days from return date)
   - Link to edit request

5. The system shall send notification upon **Request Approved** containing:
   - Congratulations on approval
   - Information that establishment will proceed to validation phase
   - Next steps: Self-Assessment Questionnaire (SAQ)
   - Timeline expectations

6. The system shall send notification upon **Request Rejected** containing:
   - Notification of rejection decision
   - Rejection reason
   - Detailed remarks from customs
   - Right to appeal information
   - Appeal submission deadline (30 days)

7. The system shall send notification upon **Request Withdrawn** containing:
   - Confirmation of withdrawal
   - Withdrawal date
   - Information about submitting new request

8. The system shall send notification upon **Request Canceled** (by customs) containing:
   - Notification of cancellation
   - Cancellation reason (if provided)
   - Right to appeal information

9. The system shall send notification upon **Request Expired** containing:
   - Notification that SLA duration exceeded
   - Explanation of expiration
   - Option to submit new request

10. All notifications shall be sent in the establishment's preferred communication language
11. Notifications shall be sent to:
    - Commercial Establishment Account Manager
    - All AEO Authorization Request Editors (where applicable)
12. The system shall maintain notification delivery log
13. The system shall allow users to view notification history in portal

**Dependencies:**
- US-AEO-010 (AEO Authorization Request submitted)
- Email service must be operational

---

### 2.3 User Management

---

#### **US-AEO-016: Add Users to Commercial Establishment Account**

**User Story:**  
As a **Commercial Establishment Account Manager**, I want to **add new users to my commercial establishment account and assign them specific roles**, so that **I can delegate AEO-related tasks to authorized team members with appropriate permissions**.

**Priority:** Must Have

**Reference:**  
- [BRD: User Management | SRD: Section 6.2.2.3, Page 170-172]
- [SRD: Section 5.3 - User Account Data, Page 56-58]
- [SRD: Section 6.1.1 - Roles and Responsibilities, Page 158-162]

**Business Rules:**  
- N/A - User management follows role-based access control principles

**Acceptance Criteria:**
1. The system shall provide "Add User" functionality accessible only to Commercial Establishment Account Manager
2. The "Add User" form shall require following mandatory fields:
   - Name in Arabic (Arabic letters only)
   - Name in English (English letters only)
   - Job Title
   - Phone Number (with country code, default UAE)
   - Email Address (must be unique, not associated with another user)
   - Preferred Communication Language
   - Role(s) - Multiple selection allowed

3. The system shall provide the following predefined roles for selection:
   - **Commercial Establishment Account Manager**: Full account management rights
   - **AEO Authorization Request Editor**: Can create/edit AEO authorization requests
   - **SAQ Editor**: Can complete Self-Assessment Questionnaire
   - **Assessment Report Editor**: Can review and comment on assessment reports
   - **Appeals Request Editor**: Can create and manage appeal requests

4. The system shall allow assigning multiple roles to a single user
5. Upon user creation, system shall:
   - Automatically generate username (identical to email address)
   - Automatically generate temporary password (16 characters, alphanumeric with special characters)
   - Send email notification to new user containing:
     - Welcome message
     - Username
     - Temporary password
     - Assigned role(s)
     - Link to login page
     - Instructions for first login and mandatory password change
6. The system shall validate email uniqueness before creating user
7. The system shall display list of all users in commercial establishment account
8. The system shall allow Account Manager to view user details including assigned roles
9. The system shall log user creation events in audit trail
10. First login shall force user to change temporary password

**Dependencies:**
- US-AEO-002 or US-AEO-003 (commercial establishment account must be approved)
- User performing action must have Commercial Establishment Account Manager role

---

#### **US-AEO-017: View and Update My Profile**

**User Story:**  
As a **Commercial Establishment user**, I want to **view my profile information and update my contact details**, so that **I can ensure the system has my current information for communications and notifications**.

**Priority:** Must Have

**Reference:**  
- [BRD: User Profile Management | SRD: Section 6.2.2.7, Page 173]
- [SRD: Section 5.3 - User Account Data, Page 56-58]

**Business Rules:**  
- N/A - Profile management is standard user functionality

**Acceptance Criteria:**
1. The system shall provide "My Profile" option accessible from user menu
2. The profile page shall display following information:
   - Name in Arabic (read-only, created by Account Manager)
   - Name in English (read-only, created by Account Manager)
   - Job Title (read-only, created by Account Manager)
   - Username (read-only, system-generated)
   - Assigned Role(s) (read-only, assigned by Account Manager)
   - Phone Number (editable by user)
   - Email Address (editable by user)
   - Preferred Communication Language (editable by user)
3. The system shall allow user to update:
   - Phone Number
   - Email Address (with validation for uniqueness)
   - Preferred Communication Language
4. The system shall validate email format and uniqueness when updated
5. The system shall save changes upon user confirmation
6. The system shall send confirmation email to new email address if email is changed
7. The system shall require email verification if email is changed
8. The system shall display "Change Password" option for users with username/password login method
9. The system shall NOT display password options for UAE PASS users
10. The system shall log profile updates in audit trail
11. The system shall display last login date and time

**Dependencies:**
- US-AEO-006 or US-AEO-007 (user must be logged in)

---

#### **US-AEO-018: View Audit Trail for Commercial Establishment Account**

**User Story:**  
As a **Commercial Establishment Account Manager**, I want to **view comprehensive audit trail of all actions performed in my commercial establishment account**, so that **I can track who did what and when for accountability and compliance purposes**.

**Priority:** Should Have

**Reference:**  
- [BRD: Audit and Compliance | SRD: Section 6.5.2, Page 350]
- [SRD: Section 5.37 - Audit Trails Data, Page 142-144]

**Business Rules:**  
- N/A - Audit trail is automatic system logging

**Acceptance Criteria:**
1. The system shall automatically capture and log all significant actions including:
   - Account creation request submission
   - User additions, modifications, deletions
   - AEO Authorization Request creation, editing, submission
   - Document uploads and deletions
   - SAQ responses submission
   - Assessment report reviews
   - Appeal submissions
   - Status changes
   - Login/logout events
   - Password changes

2. For each audit trail entry, system shall capture:
   - Timestamp (date and time of action)
   - Username of user who performed action (or "Customs user" if action by customs)
   - Full name of user (or customs department name if applicable)
   - Action performed (detailed description)
   - Record identifier (affected record/entity)
   - Previous value (before change, if applicable)
   - New value (after change, if applicable)

3. The system shall provide audit trail viewing functionality accessible to Account Manager
4. The audit trail view shall support:
   - Filtering by date range
   - Filtering by action type
   - Filtering by user
   - Search functionality
   - Export to PDF/Excel
5. The system shall display audit trail in chronological order (newest first, configurable)
6. The system shall maintain audit trail records permanently
7. The system shall prevent modification or deletion of audit trail entries
8. The system shall display audit trail in user's preferred language

**Dependencies:**
- All system features that generate audit events
- User must have Commercial Establishment Account Manager role

---

## 3. Local Customs Portal - User Stories

### 3.1 Account Creation Review

---

#### **US-LC-001: Review Commercial Establishment Account Creation Request**

**User Story:**  
As an **Administrator in the relevant customs department**, I want to **review commercial establishment account creation requests**, so that **I can verify the information and documents are complete and accurate before approving or rejecting the account**.

**Priority:** Must Have

**Reference:**  
- [BRD: Account Creation Review Process | SRD: Section 6.3.2.1, Page 226-227]
- [SRD: Section 5.1 - Account Creation Request Data, Page 49-55]

**Business Rules:**  
- **BR.3**: Review of account creation request is automatically assigned to administrator in customs department relevant to emirate that issued the trade license
- **BR.4**: Commercial establishment username format will be identical to provided email
- **BR.28**: System checks before submission if establishment has previously submitted request in progress or approved

**Acceptance Criteria:**
1. The system shall automatically route account creation request to relevant customs department based on emirate that issued trade license
2. The system shall notify Administrator via email and portal when new request is received
3. The system shall display list of pending account creation requests on Administrator dashboard
4. The request detail view shall display all information submitted by applicant:
   
   **Applicant Information:**
   - Name (Arabic and English)
   - Job Title
   - Role (Owner/Founder or Authorized Representative)
   - Phone Number
   - Email Address
   - Communication Language
   
   **Commercial Establishment Information:**
   - Commercial Establishment Name (Arabic and English)
   - Emirate
   - License Issuer
   - License Number
   
   **Attachments:**
   - Valid License (viewable in portal)
   - Copy of Applicant's Emirates ID (viewable in portal)
   - Authorization Document (if applicable, viewable in portal)

5. The system shall provide document viewing capabilities within portal
6. The system shall allow Administrator to download attachments for offline review
7. The Administrator shall have two action options:

   **Option A - Approve Request:**
   - Click "Approve" button
   - System automatically generates username (identical to provided email)
   - System automatically generates secure password (16 characters, alphanumeric with special characters)
   - System sends credentials to establishment via email
   - System updates status to "Account Creation Request Approved"
   - System records approval date and approving administrator

   **Option B - Reject Request:**
   - Click "Reject" button
   - System displays rejection reason selection (mandatory):
     - Missing data
     - Incorrect data
     - Irrelevant activities
     - Other (requires remarks in text field)
   - Enter remarks (optional, mandatory if "Other" selected)
   - System updates status to "Account Creation Request Rejected"
   - System sends rejection notification to applicant with reason and remarks
   - System records rejection date and rejecting administrator

8. The system shall validate mandatory fields before allowing submission of decision
9. The system shall log all review actions in audit trail
10. The system shall prevent review of requests not assigned to logged-in user's customs department
11. Once approved or rejected, request shall be removed from pending queue and moved to processed requests

**Dependencies:**
- US-AEO-002 or US-AEO-003 (account creation request must be submitted)

---

#### **US-LC-002: View Account Creation Request Status History**

**User Story:**  
As an **Administrator or Senior Administrator in customs department**, I want to **view complete status history of account creation requests**, so that **I can track processing timeline and see all actions taken**.

**Priority:** Should Have

**Reference:**  
- [BRD: Request Tracking | SRD: Section 6.3.2.2, Page 227]

**Business Rules:**  
- N/A - Status tracking is system functionality

**Acceptance Criteria:**
1. The system shall maintain complete status history for each account creation request
2. The system shall support following statuses:
   - **Account Creation Request Submitted**: When applicant submits request
   - **Account Creation Request Under Review**: When administrator begins review
   - **Account Creation Request Approved**: When request is approved
   - **Account Creation Request Rejected**: When request is rejected

3. For each status transition, system shall record:
   - Status name
   - Status start date/time
   - Status end date/time (when transitioning to next status)
   - User who triggered status change
   - Comments/remarks (if applicable)

4. The system shall display status history in:
   - Request detail view
   - Timeline visualization
   - Chronological list format

5. The system shall allow filtering requests by current status
6. The system shall calculate and display:
   - Total processing time
   - Time spent in each status
   - SLA compliance indicators

7. All status records shall be stored in audit trail and immutable

**Dependencies:**
- US-LC-001 (account creation requests must be processed)

---

#### **US-LC-003: Receive Notifications for Account Creation Requests**

**User Story:**  
As an **Administrator in customs department**, I want to **receive notifications when new account creation requests are submitted or require my attention**, so that **I can review them promptly and meet service level agreements**.

**Priority:** Must Have

**Reference:**  
- [BRD: Notifications | SRD: Section 6.3.2.3, Page 228]

**Business Rules:**  
- N/A - Notifications are event-driven

**Acceptance Criteria:**
1. The system shall send notification to Administrator when:
   - New account creation request is submitted and assigned to their customs department
   - Request requires review

2. Notification channels shall include:
   - Email
   - Local Customs AEO Management Portal (in-app notification)

3. The notification shall contain:
   - Commercial establishment name
   - Reference number
   - Submission date
   - Emirate
   - License issuer
   - Direct link to review request

4. The system shall display unread notification count on portal dashboard
5. The system shall maintain notification history
6. The system shall allow Administrator to mark notifications as read
7. The system shall send reminder notifications if request not reviewed within specified timeframe (configurable)
8. Notifications shall be sent in Administrator's preferred language

**Dependencies:**
- US-AEO-002 or US-AEO-003 (account creation request submitted)

---

### 3.2 AEO Authorization Request Review

---

#### **US-LC-004: Review AEO Authorization Request for Completeness**

**User Story:**  
As an **Administrator in the relevant customs department**, I want to **review AEO Authorization Request to verify all required information and documents are provided**, so that **I can make preliminary decision on whether the establishment is eligible to proceed to validation phase**.

**Priority:** Must Have

**Reference:**  
- [BRD: AEO Authorization Request Review Process | SRD: Section 6.3.3.1, Page 228-232]
- [SRD: Section 5.4 - AEO Authorization Request Form Data, Page 58-68]

**Business Rules:**  
- **BR.8**: When submitting AEO authorization request, system assigns request to administrator in customs department relevant to emirate that issued trade license
- **BR.9**: Relevant customs department is obligated to verify all requirements within 30 days from submission date
- **BR.10**: If request is returned for completion, establishment must complete data within 30 days; if not completed, local customs can reject with "Expired" reason
- **BR.27**: Relevant customs department has right to cancel AEO authorization request at any stage without restrictions

**Acceptance Criteria:**
1. The system shall automatically route AEO Authorization Request to relevant customs department based on license emirate
2. The system shall notify Administrator when new request is received
3. The system shall display list of pending AEO Authorization Requests on dashboard
4. The system shall display countdown showing remaining days to complete review (30 days from submission)
5. The request detail view shall display all sections submitted by establishment:
   - Commercial Establishment Details
   - Branch Information (if applicable)
   - Supply Chain Activities
   - Executive Management and Board Members (if applicable)
   - Shareholders/Owners (if applicable)
   - Accountant Information
   - Customs Procedures and Transactions (annual values and counts)
   - Applicant Information
   - All Attachments

6. The system shall provide document viewing and download capabilities
7. The system shall allow Administrator to add violations found during review:
   - Trade License Number (auto-filled, editable for branches added by customs)
   - Violation (mandatory, from violation lookup)
   - Violation Document (optional)
   - Violation Details (optional)

8. The system shall allow Administrator to add branches not previously mentioned by establishment:
   - All branch fields as defined in request form
   - Violations related to added branches

9. The Administrator shall have the following action options:

   **Option A - Initially Approve:**
   - Click "Initially Approve" button
   - System validates preliminary completeness
   - System initiates preliminary risk assessment process
   - System updates status to "Preliminary Risk Assessment Started"
   - System notifies:
     - Other local customs departments to participate in preliminary risk assessment
     - General Department of Customs (Federal)
     - Commercial establishment

   **Option B - Return for Completion:**
   - Click "Return for Completion" button
   - Select return reason from dropdown (mandatory)
   - Enter detailed remarks explaining required corrections (mandatory)
   - System updates status to "AEO Authorization Request Returned for Completion"
   - System sends notification to establishment with 30-day deadline
   - System starts 30-day countdown timer

   **Option C - Reject:**
   - Click "Reject" button
   - Select rejection reason (mandatory)
   - Enter detailed remarks (mandatory)
   - System updates status to "AEO Authorization Request Rejected"
   - System sends rejection notification to establishment with appeal rights information

   **Option D - Mark as Exceptional Case:**
   - Click "Mark as Exceptional Case" button
   - System updates status indicator
   - System notifies Senior Administrator and AEO Program Manager
   - Senior Administrator must review and make final decision

10. The system shall validate mandatory fields before allowing decision submission
11. The system shall log all review actions in audit trail
12. The system shall prevent review of requests not assigned to logged-in user's customs department
13. The system shall track and display SLA compliance (30 days for initial review)

**Dependencies:**
- US-AEO-010 (AEO Authorization Request must be submitted)

---

#### **US-LC-005: Cancel AEO Authorization Request**

**User Story:**  
As an **Administrator or Senior Administrator in customs department**, I want to **cancel an AEO Authorization Request at any stage of processing**, so that **I can terminate the application process if circumstances warrant cancellation**.

**Priority:** Must Have

**Reference:**  
- [BRD: Request Cancellation | SRD: Section 6.3.3.2, Page 232]

**Business Rules:**  
- **BR.27**: Relevant customs department has right to cancel AEO authorization request at any stage without restrictions

**Acceptance Criteria:**
1. The system shall provide "Cancel Request" functionality accessible to Administrator and Senior Administrator
2. The cancellation option shall be available for requests in any status except:
   - Already Rejected
   - Already Withdrawn
   - Already Canceled
   - Certificate Issued (after final approval)

3. Upon clicking "Cancel Request", system shall:
   - Display confirmation dialog explaining cancellation is irreversible
   - Require mandatory cancellation reason selection
   - Require mandatory remarks explaining cancellation

4. Upon confirmed cancellation, system shall:
   - Update request status to "AEO Authorization Request Canceled"
   - Record cancellation date, time, and canceling officer
   - Send notification to:
     - Commercial establishment with cancellation reason and remarks
     - All customs officers involved in the request
     - General Department of Customs (Federal)
   - Archive request (maintains visibility but prevents further processing)

5. The system shall log cancellation event in audit trail with full details
6. Canceled requests shall remain viewable in system for historical reference
7. After cancellation, establishment shall be able to submit new AEO Authorization Request
8. The system shall prevent any further processing actions on canceled requests

**Dependencies:**
- US-AEO-010 (AEO Authorization Request must exist)
- User must have Administrator or Senior Administrator role

---

#### **US-LC-006: View AEO Authorization Request Status and History**

**User Story:**  
As an **Administrator, Senior Administrator, or AEO Program Manager**, I want to **view comprehensive status information and processing history of AEO Authorization Requests**, so that **I can track progress, identify bottlenecks, and ensure SLA compliance**.

**Priority:** Must Have

**Reference:**  
- [BRD: Request Tracking | SRD: Section 6.3.3.3, Page 233-237]

**Business Rules:**  
- **BR.9**: Relevant customs department must verify all requirements within 30 days from submission

**Acceptance Criteria:**
1. The system shall maintain complete status history for each AEO Authorization Request
2. The system shall support following statuses (from customs perspective):
   - **AEO Authorization Request Submitted**: Initial submission received
   - **AEO Authorization Request Under Review**: Administrator reviewing application
   - **AEO Authorization Request Returned for Completion**: Sent back to establishment
   - **AEO Authorization Request Received After Data Completion**: Resubmitted by establishment
   - **Preliminary Risk Assessment Started**: Approved for risk assessment
   - **Preliminary Risk Assessment Ready for Review**: All assessments completed
   - **AEO Authorization Request Approved**: Approved to proceed to validation
   - **AEO Authorization Request Rejected**: Application rejected
   - **AEO Authorization Request Withdrawn**: Withdrawn by establishment
   - **AEO Authorization Request Canceled**: Canceled by customs
   - **AEO Authorization Request Expired**: SLA exceeded
   - **AEO Authorization Request Marked as Exceptional Case**: Requires senior review

3. The system shall display for each request:
   - Current status with description
   - Reference number
   - Commercial establishment name
   - Submission date
   - Last updated date
   - Days in current status
   - SLA compliance indicator (green/yellow/red based on 30-day deadline)
   - Assigned officer
   - Timeline visualization of all status transitions

4. The system shall provide filtering capabilities:
   - By status
   - By date range
   - By emirate
   - By assigned officer
   - By SLA compliance
   - By exceptional case flag

5. The system shall provide search functionality by:
   - Reference number
   - Establishment name
   - License number

6. The system shall calculate and display:
   - Total processing time
   - Average time per status
   - SLA compliance percentage
   - Number of requests by status

7. The system shall allow exporting status reports to PDF/Excel
8. The system shall display status history with:
   - Status name
   - Start date/time
   - End date/time
   - Duration in status
   - Officer who triggered status change
   - Comments/actions taken

9. All status transitions shall be logged in audit trail

**Dependencies:**
- US-AEO-010 (AEO Authorization Requests must exist)
- US-LC-004 (requests must be processed)

---

#### **US-LC-007: Receive Notifications for AEO Authorization Request Events**

**User Story:**  
As an **Administrator, Senior Administrator, or AEO Program Manager**, I want to **receive notifications for all significant events related to AEO Authorization Requests**, so that **I can take timely action and maintain awareness of request progress**.

**Priority:** Must Have

**Reference:**  
- [BRD: Communication and Notifications | SRD: Section 6.3.3.4, Page 237-239]

**Business Rules:**  
- N/A - Notifications are event-driven

**Acceptance Criteria:**
1. The system shall send notifications via:
   - Email
   - Local Customs AEO Management Portal (in-app)

2. The system shall send notification to **Administrator** when:
   - New AEO Authorization Request received and assigned
   - Request resubmitted after data completion
   - Request marked as exceptional case by another officer
   - SLA warning (e.g., 25 days elapsed, 5 days remaining)
   - Request withdrawn by establishment

3. The system shall send notification to **Senior Administrator** when:
   - Preliminary risk assessment ready for review
   - Request marked as exceptional case requiring senior decision
   - SLA exceeded on any request in their department

4. The system shall send notification to **All Relevant Officers** when:
   - Request canceled by any officer
   - Request status changes significantly

5. The system shall send notification to **Other Local Customs Departments** when:
   - AEO Authorization Request received requiring their participation in preliminary risk assessment
   - Preliminary risk assessment submitted by other department

6. The system shall send notification to **Federal Administrator (General Department of Customs)** when:
   - AEO Authorization Request approved by local customs
   - Request rejected by local customs
   - Preliminary risk assessment completed

7. Each notification shall contain:
   - Commercial establishment name
   - Reference number
   - Event description
   - Current status
   - Action required (if applicable)
   - Deadline (if applicable)
   - Direct link to request in portal

8. The system shall display notification count on portal dashboard
9. The system shall highlight urgent notifications (SLA warnings, deadlines)
10. The system shall maintain notification history
11. The system shall allow marking notifications as read/unread
12. The system shall send email summary of pending actions daily (configurable)
13. Notifications shall be sent in recipient's preferred language

**Dependencies:**
- All AEO Authorization Request processing features
- Email service must be operational

---

#### **US-LC-008: View My Profile and Update Preferences**

**User Story:**  
As a **Local Customs user**, I want to **view my profile information and update my communication preferences**, so that **I can ensure I receive notifications in my preferred language**.

**Priority:** Must Have

**Reference:**  
- [BRD: User Profile | SRD: Section 6.3.1, Page 226]
- [SRD: Section 5.19 - Local and Federal Customs Users Data, Page 113-116]

**Business Rules:**  
- N/A - Profile data is maintained centrally by Federal System Administrator

**Acceptance Criteria:**
1. The system shall provide "My Profile" option accessible from user menu
2. The profile page shall display following information (read-only, maintained by Federal System Administrator):
   - Name in Arabic
   - Name in English
   - Employee Code
   - Job Title
   - Customs Department
   - Role(s)
   - Email Address
   - Phone Number
   - Office Location

3. The system shall allow user to update ONLY:
   - Preferred Communication Language (Arabic or English)

4. The system shall save language preference upon user confirmation
5. The system shall apply language preference to:
   - Portal interface language
   - Email notifications
   - System-generated documents

6. The system shall display last login date and time
7. The system shall display assigned roles and their descriptions
8. All profile data updates shall be logged in audit trail

**Dependencies:**
- User must be authenticated and authorized to access Local Customs Portal

---

## Document History

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | November 7, 2025 | AEO Project Team | Initial Phase 1 User Stories Document |

---

## Traceability Matrix Summary

| User Story ID | Feature Area | BRD Reference | SRD Reference | Priority |
|--------------|--------------|---------------|---------------|----------|
| US-AEO-001 | Program Information | Section 1.2 | Section 6.2.1 | Must Have |
| US-AEO-002 | UAE PASS Registration | Section 4.1.1 | Section 6.2.2.1, 8 | Must Have |
| US-AEO-003 | Manual Registration | Section 4.1.1 | Section 6.2.2.1, 5.1 | Must Have |
| US-AEO-004 | Request Tracking | Section 4.1.1 | Section 6.2.2.2, 5.2 | Must Have |
| US-AEO-005 | Notifications | Section 4.1.1 | Section 6.2.2.9 | Must Have |
| US-AEO-006 | UAE PASS Login | Account Access | Section 6.2.2.1, 8 | Must Have |
| US-AEO-007 | Credential Login | Account Access | Section 6.2.2.1, 5.3 | Must Have |
| US-AEO-008 | Forgot Password | Account Security | Section 6.2.2.6 | Must Have |
| US-AEO-009 | Change Password | Account Security | Section 6.2.2.5 | Must Have |
| US-AEO-010 | Submit AEO Request | Section 4.1.2 | Section 6.2.3.1, 5.4 | Must Have |
| US-AEO-011 | Save as Draft | Section 4.1.2 | Section 6.2.3.3 | Must Have |
| US-AEO-012 | Track Request Status | Section 4.1.2 | Section 6.2.3.2, 6.2.3.6 | Must Have |
| US-AEO-013 | Withdraw Request | Request Management | Section 6.2.3.4 | Must Have |
| US-AEO-014 | Complete Returned Request | Section 4.1.2 | Section 6.2.3.5, 5.4 | Must Have |
| US-AEO-015 | Request Notifications | Communication | Section 6.2.3.7 | Must Have |
| US-AEO-016 | Add Users | User Management | Section 6.2.2.3, 5.3, 6.1.1 | Must Have |
| US-AEO-017 | View/Update Profile | User Profile | Section 6.2.2.7, 5.3 | Must Have |
| US-AEO-018 | View Audit Trail | Audit/Compliance | Section 6.5.2, 5.37 | Should Have |
| US-LC-001 | Review Account Request | Section 4.1.1 | Section 6.3.2.1, 5.1 | Must Have |
| US-LC-002 | View Status History | Request Tracking | Section 6.3.2.2 | Should Have |
| US-LC-003 | Account Notifications | Notifications | Section 6.3.2.3 | Must Have |
| US-LC-004 | Review AEO Request | Section 4.1.2 | Section 6.3.3.1, 5.4 | Must Have |
| US-LC-005 | Cancel Request | Request Management | Section 6.3.3.2 | Must Have |
| US-LC-006 | View Request History | Request Tracking | Section 6.3.3.3 | Must Have |
| US-LC-007 | AEO Request Notifications | Communication | Section 6.3.3.4 | Must Have |
| US-LC-008 | View Profile | User Profile | Section 6.3.1, 5.19 | Must Have |

---

**End of Phase 1 User Stories Document**
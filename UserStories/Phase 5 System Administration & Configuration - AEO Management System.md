# AEO Management System - User Stories
## Phase 5: System Administration & Configuration

**Document Version:** 1.0  
**Date:** November 08, 2025  
**Project:** Authorized Economic Operator (AEO) Management System  
**Source Documents:**  
- Business Requirements Document (BRD) V1.11  
- System Requirements Document (SRD) V1.2.5

---

## Document Overview

### Purpose
This document contains detailed user stories for **Phase 5: System Administration & Configuration** of the AEO Management System. All user stories are directly derived from the Business Requirements Document (BRD V1.11) and System Requirements Document (SRD V1.2.5) without assumptions.

### Scope
Phase 5 covers comprehensive system administration and configuration capabilities including:
- **Benefits and Benefits Groups Management** (Federal Customs)
- **Violations Lookup Management** (Federal Customs)
- **Control Plan Actions Lookup Management** (Federal Customs)
- **Mutual Recognition Agreements (MRA) Management** (Federal Customs)
- **User and Role Management** (Federal Customs)
- **System Settings Configuration** (Federal Customs)
- **Notifications and Reminders Configuration** (Federal Customs)
- **Content Management** (Federal Customs)
- **Additional Lookup Management** (Federal Customs)

**Note:** Question Bank Management, Risks Bank Management, and SAQ Template Management are covered in Phase 2 user stories and are referenced here where applicable.

### User Roles

#### Federal Customs Portal
- **Federal System Administrator:** Manages user roles, access control, notifications, reminders, system settings, meeting settings, and content management
- **Federal Administrator:** Manages benefits, benefits groups, MRAs, violations lookup, control plan actions lookup, assessment tools lookup, and other system configurations
- **Senior Federal Administrator:** Reviews and approves critical configurations and settings

---

## Table of Contents
1. [Federal Customs Portal - Benefits and Benefits Groups Management](#benefits-management)
2. [Federal Customs Portal - Violations Lookup Management](#violations-lookup)
3. [Federal Customs Portal - Control Plan Actions Lookup Management](#control-plan-actions)
4. [Federal Customs Portal - MRA Management](#mra-management)
5. [Federal Customs Portal - User and Role Management](#user-role-management)
6. [Federal Customs Portal - System Settings Configuration](#system-settings)
7. [Federal Customs Portal - Notifications and Reminders Configuration](#notifications-reminders)
8. [Federal Customs Portal - Content Management](#content-management)
9. [Federal Customs Portal - Additional Lookup Management](#additional-lookups)

---

<a name="benefits-management"></a>
## 1. Federal Customs Portal - Benefits and Benefits Groups Management

### Epic: Benefits and Benefits Groups Management
Enable Federal Customs to create and manage benefit groups and individual benefits for National, GCC, and MRA AEO programs.

---

### US-ADMIN-001: Create National Benefit Group

**As a** Federal Administrator  
**I want to** create national benefit groups  
**So that** AEO benefits can be organized and assigned systematically

**Acceptance Criteria:**
1. System displays option to manage National Benefit Groups `[SRD Section 6.4.6]`
2. Federal Administrator can create new benefit group with following fields: `[SRD Section 5.14]`
   - Benefit Group Name (Arabic) - Mandatory
   - Benefit Group Name (English) - Mandatory
   - Benefit Group Description (Arabic) - Mandatory
   - Benefit Group Description (English) - Mandatory
3. System validates that group name is unique
4. System saves benefit group and makes it available for benefit assignment
5. System allows Federal Administrator to edit existing benefit groups
6. System allows Federal Administrator to delete benefit groups that are not assigned to any AEO
7. System prevents deletion of benefit groups that are currently assigned to AEOs
8. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Benefits management
- **SRD:** Section 6.4.6 "Managing National and GCC Benefit Groups", Section 5.14 "National and GCC Benefits Groups Data", Pages 96-97, 315

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-002: Create GCC Benefit Group

**As a** Federal Administrator  
**I want to** create GCC benefit groups  
**So that** benefits for GCC-recognized AEOs can be managed separately

**Acceptance Criteria:**
1. System provides separate section for GCC Benefit Groups `[SRD Section 6.4.6]`
2. Federal Administrator can create new GCC benefit group with following fields: `[SRD Section 5.14]`
   - Benefit Group Name (Arabic) - Mandatory
   - Benefit Group Name (English) - Mandatory
   - Benefit Group Description (Arabic) - Mandatory
   - Benefit Group Description (English) - Mandatory
3. System validates that group name is unique within GCC benefit groups
4. System saves GCC benefit group separately from National benefit groups
5. System allows Federal Administrator to edit existing GCC benefit groups
6. System allows Federal Administrator to delete GCC benefit groups not assigned to any AEO
7. System prevents deletion of GCC benefit groups currently assigned to AEOs
8. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** GCC benefits management
- **SRD:** Section 6.4.6 "Managing National and GCC Benefit Groups", Section 5.14 "National and GCC Benefits Groups Data", Pages 96-97, 315

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-003: Create MRA Benefit Group

**As a** Federal Administrator  
**I want to** create MRA benefit groups for each mutual recognition agreement  
**So that** benefits specific to each MRA can be managed

**Acceptance Criteria:**
1. System provides section for MRA Benefit Groups `[SRD Section 6.4.6]`
2. Federal Administrator can create new MRA benefit group with following fields: `[SRD Section 5.32]`
   - Name of MRA Group (Arabic) - Mandatory
   - Name of MRA Group (English) - Mandatory
   - MRA Group Description (Arabic) - Mandatory
   - MRA Group Description (English) - Mandatory
3. System validates that MRA group name is unique
4. System saves MRA benefit group
5. MRA benefit groups are linked to specific MRA agreements
6. System allows Federal Administrator to edit existing MRA benefit groups
7. System allows Federal Administrator to delete MRA benefit groups not linked to any active MRA
8. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** MRA benefits management
- **SRD:** Section 6.4.6 "Managing National and GCC Benefit Groups", Section 5.32 "MRAs Benefits Group Data", Pages 139, 315

**Dependencies:**
- US-ADMIN-013 (MRA must be created first)

**Priority:** Must Have

---

### US-ADMIN-004: Add National Benefits

**As a** Federal Administrator  
**I want to** add individual benefits to national benefit groups  
**So that** specific benefits can be assigned to certified AEOs

**Acceptance Criteria:**
1. System displays list of all national benefit groups `[SRD Section 6.4.7]`
2. Federal Administrator selects a benefit group to add benefits
3. System provides form to add benefit with following fields: `[SRD Section 5.15]`
   - Benefit Name (Arabic) - Mandatory
   - Benefit Name (English) - Mandatory
   - Benefit Description (Arabic) - Mandatory
   - Benefit Description (English) - Mandatory
4. System validates that benefit name is unique within the benefit group
5. System saves benefit and associates it with selected benefit group
6. System allows adding multiple benefits to same benefit group
7. System allows Federal Administrator to edit existing benefits
8. System allows Federal Administrator to delete benefits not currently assigned to any AEO
9. System prevents deletion of benefits currently assigned to AEOs
10. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Benefits management
- **SRD:** Section 6.4.7 "Managing National and GCC Benefits", Section 5.15 "National and GCC Benefits Data", Pages 97-98, 316

**Dependencies:**
- US-ADMIN-001

**Priority:** Must Have

---

### US-ADMIN-005: Add GCC Benefits

**As a** Federal Administrator  
**I want to** add individual benefits to GCC benefit groups  
**So that** GCC-specific benefits can be assigned to recognized AEOs

**Acceptance Criteria:**
1. System displays list of all GCC benefit groups `[SRD Section 6.4.7]`
2. Federal Administrator selects a GCC benefit group to add benefits
3. System provides form to add benefit with following fields: `[SRD Section 5.15]`
   - Benefit Name (Arabic) - Mandatory
   - Benefit Name (English) - Mandatory
   - Benefit Description (Arabic) - Mandatory
   - Benefit Description (English) - Mandatory
4. System validates that benefit name is unique within the GCC benefit group
5. System saves benefit and associates it with selected GCC benefit group
6. GCC benefits are managed separately from National benefits
7. System allows Federal Administrator to edit existing GCC benefits
8. System allows Federal Administrator to delete GCC benefits not assigned to any AEO
9. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** GCC benefits management
- **SRD:** Section 6.4.7 "Managing National and GCC Benefits", Section 5.15 "National and GCC Benefits Data", Pages 97-98, 316

**Dependencies:**
- US-ADMIN-002

**Priority:** Must Have

---

### US-ADMIN-006: Add MRA Benefits

**As a** Federal Administrator  
**I want to** add individual benefits to MRA benefit groups  
**So that** MRA-specific benefits can be communicated to partner countries

**Acceptance Criteria:**
1. System displays list of all MRA benefit groups
2. Federal Administrator selects an MRA benefit group to add benefits
3. System provides form to add benefit with following fields: `[SRD Section 5.16]`
   - Benefit Name (Arabic) - Mandatory
   - Benefit Name (English) - Mandatory
   - Benefit Description (Arabic) - Mandatory
   - Benefit Description (English) - Mandatory
4. System validates that benefit name is unique within the MRA benefit group
5. System saves benefit and associates it with selected MRA benefit group
6. MRA benefits are displayed on AEO Portal for logged-in users `[SRD Section 6.2.1]`
7. System allows Federal Administrator to edit existing MRA benefits
8. System allows Federal Administrator to delete MRA benefits not linked to active MRAs
9. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** MRA benefits management
- **SRD:** Section 6.2.1 "About the AEO Program", Section 5.16 "MRAs Benefits Data", Pages 98, 165-166

**Dependencies:**
- US-ADMIN-003

**Priority:** Must Have

---

<a name="violations-lookup"></a>
## 2. Federal Customs Portal - Violations Lookup Management

### Epic: Violations Lookup Management
Enable Federal Customs to define and manage a standardized list of violations that can be applied to commercial establishments.

---

### US-ADMIN-007: Manage Violations Lookup

**As a** Federal Administrator  
**I want to** define and manage violations lookup list  
**So that** violations can be applied consistently during AEO authorization and post-certification phases

**Acceptance Criteria:**
1. System provides Violations Lookup management interface `[SRD Section 6.4.10.15]`
2. Federal Administrator can add new violations to the lookup list `[SRD Section 6.4.10.15]`
3. System provides form to define violation with required fields (to be detailed when violation data becomes available) `[SRD Section 6.4.10.15]`
4. Violations can be applied to commercial establishments during:
   - AEO Authorization Request phase `[SRD Section 6.4.10.15]`
   - After AEO status has been granted `[SRD Section 6.4.10.15]`
5. System allows Federal Administrator to edit existing violations
6. System allows Federal Administrator to delete violations not currently applied to any establishment
7. System maintains version history of violations lookup
8. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Violations management
- **SRD:** Section 6.4.10.15 "Managing Violations Look ups", Page 335

**Dependencies:**
- None

**Priority:** Must Have

**Note:** Detailed violation data structure will be defined once required data becomes available.

---

<a name="control-plan-actions"></a>
## 3. Federal Customs Portal - Control Plan Actions Lookup Management

### Epic: Control Plan Actions Lookup Management
Enable Federal Customs to define standardized control plan actions for monitoring AEOs.

---

### US-ADMIN-008: Add Control Plan Action Lookup

**As a** Federal Administrator  
**I want to** add control plan action options to the lookup list  
**So that** validation teams and key account managers can select standardized monitoring actions

**Acceptance Criteria:**
1. System provides Control Plan Actions Lookup management interface `[SRD Section 6.4.10.12]`
2. Federal Administrator can add new control plan action with following fields: `[SRD Section 5.31]`
   - Lookup Option (Arabic) - Mandatory - Accepts Arabic letters
   - Lookup Option (English) - Mandatory - Accepts English letters
   - Description Option (Arabic) - Mandatory - Accepts Arabic letters
   - Description Option (English) - Mandatory - Accepts English letters
3. System validates that lookup option is unique
4. System saves control plan action option
5. After adding, option becomes available for Validation Team and Key Account Managers when preparing or updating control plan `[SRD Section 6.4.10.12]`
6. System allows Federal Administrator to edit existing control plan actions
7. System allows Federal Administrator to delete actions not currently used in any control plan
8. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Control plan actions management
- **SRD:** Section 6.4.10.12 "Managing Lookups for Control Plan Actions", Section 5.31 "Control plan Actions Lookup Data", Pages 138, 333-334

**Dependencies:**
- None

**Priority:** Must Have

---

<a name="mra-management"></a>
## 4. Federal Customs Portal - MRA Management

### Epic: Mutual Recognition Agreements (MRA) Management
Enable Federal Customs to manage mutual recognition agreements with partner countries.

---

### US-ADMIN-009: Add New MRA

**As a** Federal Administrator  
**I want to** add new mutual recognition agreement  
**So that** benefits of MRAs can be communicated to stakeholders

**Acceptance Criteria:**
1. System provides MRA management interface `[SRD Section 6.4.4]`
2. Federal Administrator can add new MRA with following fields: `[SRD Section 5.17]`
   - Country Name (Arabic) - Mandatory
   - Country Name (English) - Mandatory
   - Signed Agreement Date - Mandatory
   - Agreement Effective Date - Mandatory
   - Agreement Link - Optional - URL to agreement document
   - Country Image - Optional - Country flag or logo
   - Agreement Details (Arabic) - Optional - Description of agreement
   - Agreement Details (English) - Optional - Description of agreement
3. System validates that country name is unique
4. System validates date formats
5. Once MRA is added, it automatically appears on AEO Portal in list of countries with benefits `[SRD Section 6.2.1]`
6. MRA benefits associated with this agreement are displayed to logged-in users on AEO Portal `[SRD Section 6.2.1]`
7. System allows Federal Administrator to edit existing MRA details
8. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** MRA management
- **SRD:** Section 6.4.4 "Managing Mutual Recognition Agreements", Section 6.2.1 "About the AEO Program", Section 5.17 "Adding MRAs Data", Pages 98-99, 165-166, 314

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-010: Revoke MRA

**As a** Federal Administrator  
**I want to** revoke mutual recognition agreement  
**So that** outdated or terminated agreements are not displayed to users

**Acceptance Criteria:**
1. System displays list of all active MRAs
2. Federal Administrator can select MRA to revoke
3. System prompts for confirmation before revocation
4. Once MRA is revoked, system automatically hides it from AEO Portal `[SRD Section 6.2.1]`
5. Revoked MRAs are no longer visible to AEO Portal users
6. System maintains history of revoked MRAs for audit purposes
7. Federal Administrator can view list of revoked MRAs separately
8. System prevents restoration of revoked MRAs (new MRA must be created if needed)
9. Revocation is recorded in audit trail with timestamp and user details

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** MRA revocation
- **SRD:** Section 6.2.1 "About the AEO Program", Pages 165-166

**Dependencies:**
- US-ADMIN-009

**Priority:** Must Have

---

### US-ADMIN-011: Upload MRA Country AEOs List

**As a** Federal Administrator  
**I want to** upload Excel sheet containing AEOs from MRA partner countries  
**So that** the list is available for viewing on AEO Portal

**Acceptance Criteria:**
1. System provides interface to upload Excel sheet with AEOs from MRA countries `[SRD Section 6.4.4]`
2. Federal Administrator selects MRA country
3. System allows upload of Excel file containing AEO data
4. Excel file should contain following fields for each AEO: `[SRD Section 6.2.1]`
   - Name of establishment (English)
   - Name of establishment (Arabic) - Optional
   - Address
   - Authorization date
   - Activities in supply chain
5. System validates Excel file format and data
6. System imports AEO data and associates it with selected MRA country
7. Imported AEOs are displayed on AEO Portal under respective MRA country `[SRD Section 6.2.1]`
8. List is visible only to logged-in users on AEO Portal `[SRD Section 6.2.1]`
9. System allows filtering AEOs by activities in supply chain `[SRD Section 6.2.1]`
10. System allows Federal Administrator to update the list by uploading new Excel file
11. Upload history is maintained in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** MRA country AEOs management
- **SRD:** Section 6.4.4 "Managing Mutual Recognition Agreements", Section 6.2.1 "About the AEO Program", Pages 165-166, 314

**Dependencies:**
- US-ADMIN-009

**Priority:** Must Have

---

### US-ADMIN-012: Share National AEOs with MRA Countries

**As a** Federal Administrator  
**I want to** share list of national AEOs with MRA partner countries  
**So that** partner countries have current information about UAE AEOs

**Acceptance Criteria:**
1. System provides interface to share national AEOs list with MRA countries `[SRD Section 6.4.5]`
2. Federal Administrator can select one or more MRA countries to share list with
3. System generates list of all certified national AEOs with following information:
   - AEO name (Arabic and English)
   - Certificate number
   - Certificate issue date
   - Certificate validity period
   - Activities in supply chain
   - Contact information
4. System allows Federal Administrator to review list before sharing
5. System provides export functionality in agreed format (Excel, PDF, or XML)
6. System records sharing action with:
   - Date and time of sharing
   - Countries shared with
   - User who performed sharing
   - Number of AEOs shared
7. System sends notification to Senior Federal Administrator when list is shared `[SRD Section 6.4.10.22, Table 83]`
8. All sharing activities are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** National AEOs sharing with MRA countries
- **SRD:** Section 6.4.5 "Sharing National AEOs with the MRA Partner Country", Section 6.4.10.22 "Notifications & Reminders Settings", Pages 315, 341-347

**Dependencies:**
- US-ADMIN-009
- US-CERT-009 (National AEOs must be certified)

**Priority:** Must Have

---

<a name="user-role-management"></a>
## 5. Federal Customs Portal - User and Role Management

### Epic: User and Role Management
Enable Federal System Administrator to manage users, roles, and access control across the AEO system.

---

### US-ADMIN-013: Define and Manage System Roles

**As a** Federal System Administrator  
**I want to** define and manage system roles with specific permissions  
**So that** access control is properly implemented across the system

**Acceptance Criteria:**
1. System implements Role-Based Access Control (RBAC) `[SRD Section 6.4.10.16]`
2. System displays list of all defined roles and their associated permissions `[SRD Section 6.4.10.16]`
3. Federal System Administrator can perform following actions: `[SRD Section 6.4.10.16]`
   - View role and its permissions
   - Edit role title
   - Add permissions to role
   - Remove permissions from role
   - Delete roles that are not assigned to any users
4. System prevents deletion of roles currently assigned to users
5. Permissions are granted to roles, and roles are assigned to users `[SRD Section 6.4.10.16]`
6. System ensures users can only perform actions and access information necessary for their responsibilities `[SRD Section 6.4.10.16]`
7. Changes to roles take effect immediately for all users assigned to that role
8. System sends notification to affected users when their role permissions change `[SRD Section 6.4.10.16.1]`
9. All role changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Role-based access control
- **SRD:** Section 6.4.10.16 "Role-Based Access Control (RBAC)", Section 6.4.10.16.1 "Notification", Pages 335-336

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-014: Manage Federal Customs Users

**As a** Federal System Administrator  
**I want to** manage access for Federal Customs employees  
**So that** they can perform their assigned duties in the system

**Acceptance Criteria:**
1. System provides user management interface for Federal Customs employees `[SRD Section 6.1.3, Table 46]`
2. Federal System Administrator can add new Federal Customs user with following data: `[SRD Section 5.19]`
   - Name (Arabic) - Mandatory
   - Name (English) - Mandatory
   - Employee Code - Mandatory - Unique
   - Job Title - Mandatory
   - Email Address - Mandatory - Unique - Must be valid email format
   - Phone Number - Mandatory - UAE format
   - Office Location - Mandatory
   - Preferred Language - Mandatory - Arabic or English
   - Role(s) - Mandatory - One or more roles
3. System validates:
   - Email address is unique and valid format
   - Employee code is unique
   - Phone number is valid UAE format
4. System sends account creation notification to new user
5. Federal System Administrator can:
   - View list of all Federal Customs users
   - Edit user information (except employee code)
   - Change user role(s)
   - Activate or deactivate user accounts `[SRD Section 6.1.3, Table 46]`
6. Deactivated users cannot access the system
7. System maintains user status history
8. All user management actions are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** User management
- **SRD:** Section 6.1.3 "Federal Customs Roles", Section 5.19 "Local and Federal Customs Users Data", Pages 113-116, 163-165

**Dependencies:**
- US-ADMIN-013

**Priority:** Must Have

---

### US-ADMIN-015: Manage Local Customs Users

**As a** Federal System Administrator  
**I want to** manage access for Local Customs employees  
**So that** they can perform their duties in their respective customs departments

**Acceptance Criteria:**
1. System provides user management interface for Local Customs employees `[SRD Section 6.1.2, Table 46]`
2. Federal System Administrator can add new Local Customs user with following data: `[SRD Section 5.19]`
   - Name (Arabic) - Mandatory
   - Name (English) - Mandatory
   - Employee Code - Mandatory - Unique
   - Job Title - Mandatory
   - Customs Department - Mandatory - Selected from list of local customs departments
   - Email Address - Mandatory - Unique - Valid email format
   - Phone Number - Mandatory - UAE format
   - Office Location - Mandatory
   - Preferred Language - Mandatory - Arabic or English
   - Role(s) - Mandatory - One or more local customs roles
3. System validates:
   - Email address is unique and valid
   - Employee code is unique
   - Phone number is valid UAE format
   - Selected role is appropriate for local customs
4. System sends account creation notification to new user
5. Federal System Administrator can:
   - View list of all Local Customs users (filterable by customs department)
   - Edit user information
   - Change user role(s) `[SRD Section 6.1.3, Table 46]`
   - Activate or deactivate user accounts `[SRD Section 6.1.3, Table 46]`
6. Users can only access data and functions for their assigned customs department
7. All user management actions are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Local customs user management
- **SRD:** Section 6.1.2 "Local Customs Roles", Section 6.1.3 "Federal Customs Roles", Section 5.19 "Local and Federal Customs Users Data", Pages 113-116, 162-165

**Dependencies:**
- US-ADMIN-013

**Priority:** Must Have

---

<a name="system-settings"></a>
## 6. Federal Customs Portal - System Settings Configuration

### Epic: System Settings Configuration
Enable Federal Administrator to configure various system settings and timeframes for AEO processes.

---

### US-ADMIN-016: Configure Authorization Request Settings

**As a** Federal Administrator  
**I want to** configure authorization request processing timeframes  
**So that** service level agreements are properly enforced

**Acceptance Criteria:**
1. System provides Authorization Request Settings interface `[SRD Section 6.4.10.19]`
2. Federal Administrator can configure following settings (all in working days): `[SRD Section 6.4.10.19]`
   - **Preliminary Risk Assessment Period:**
     - Period given to local customs to prepare and approve preliminary risk assessment
     - Enter number of working days - Mandatory
   - **Commercial Establishment Response to Returned Request:**
     - Period given to commercial establishment to complete and resubmit returned authorization request
     - Enter number of working days - Mandatory
3. System validates that entered values are positive integers
4. Settings apply to all new authorization requests after configuration
5. System enforces these timeframes in workflows and SLA tracking
6. Changes to settings do not affect requests already in progress
7. System displays current settings on configuration page
8. All changes are recorded in audit trail with effective date

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Authorization request settings
- **SRD:** Section 6.4.10.19 "Authorization Request Settings", Pages 339-340

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-017: Configure Validation and Risk Assessment Settings

**As a** Federal Administrator  
**I want to** configure validation and assessment processing timeframes  
**So that** validation processes are completed within defined periods

**Acceptance Criteria:**
1. System provides Validation and Risk Assessment Settings interface `[SRD Section 6.4.10.20]`
2. Federal Administrator can configure following settings (all in working days): `[SRD Section 6.4.10.20]`
   - **SAQ Response Period:**
     - Period given to commercial establishment to complete SAQ
     - Enter number of working days - Mandatory
   - **Commercial Establishment Response to Returned SAQ:**
     - Period given to commercial establishment to modify and resubmit returned SAQ
     - Enter number of working days - Mandatory
   - **Commercial Establishment Response to Preliminary Risk Assessment:**
     - Period given to commercial establishment to approve preliminary risk assessment
     - Enter number of working days - Mandatory
   - **Commercial Establishment Response to Draft Assessment Report:**
     - Period given to commercial establishment to approve or provide comments on draft assessment/re-assessment report
     - Enter number of working days - Mandatory
   - **Maximum Extension Period for Compliance Improvement Plan:**
     - Maximum extended period given to commercial establishment to complete compliance improvement plan
     - Enter number of working days - Mandatory
3. System validates that entered values are positive integers
4. Settings apply to all new validation processes after configuration
5. System enforces these timeframes in workflows and reminders
6. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Validation and assessment settings
- **SRD:** Section 6.4.10.20 "Validation and Risk Assessment Settings", Pages 340-341

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-018: Configure KPI Sharing Settings

**As a** Federal Administrator  
**I want to** configure when local customs should share KPIs  
**So that** KPI reporting is consistent and timely

**Acceptance Criteria:**
1. System provides KPI Sharing Settings interface `[SRD Section 6.4.10.21]`
2. Federal Administrator can configure: `[SRD Section 6.4.10.21]`
   - **Submission Day of the Period:**
     - Specifies exact day of selected period (e.g., 10th day of first month in each quarter) by which KPIs should be submitted
     - Type: Numeric (1-31) - Mandatory
3. System validates that day is between 1 and 31
4. System uses this setting to:
   - Calculate KPI submission deadlines
   - Send reminders to local customs before deadline
   - Track compliance with KPI submission requirements
5. Setting applies to all local customs departments
6. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** KPI sharing configuration
- **SRD:** Section 6.4.10.21 "KPIs Sharing Settings", Page 341

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-019: Configure Meeting Settings

**As a** Federal System Administrator  
**I want to** configure meeting scheduling requirements  
**So that** commercial establishments receive adequate notice for meetings

**Acceptance Criteria:**
1. System provides Meeting Settings interface `[SRD Section 6.4.10.23]`
2. Federal System Administrator can configure: `[SRD Section 6.4.10.23]`
   - **Commercial Establishment Response Period for Meeting Requests:**
     - Period given to respond to suggested meetings
     - Enter number of working days - Mandatory
   - **Minimum Notification Period - AEO Meeting Setup:**
     - Minimum days required before scheduling meetings for validation, revalidation, and monitoring phases
     - Enter number of days - Optional
   - **Minimum Notification Period - Hearing Session Setup:**
     - Minimum days required before scheduling hearing sessions after appeal rejections
     - Enter number of days - Optional
3. System validates that entered values are positive integers
4. For minimum notification period: `[SRD Section 6.4.10.23]`
   - System enforces restriction to prevent scheduling within defined period
   - Example: If minimum notice is 9 days and today is July 1st, earliest meeting date is July 10th
   - System blocks any attempt to schedule before minimum period
5. This setting can be enabled or disabled: `[SRD Section 6.4.10.23]`
   - When disabled, meetings can be scheduled immediately without minimum notice period
6. Settings apply to all meeting scheduling functions
7. System uses settings to validate meeting dates during scheduling
8. All changes are recorded in audit trail

**Business Rules:**
- BR.26: When scheduling meetings whether field visits, remote meetings, or a hearing session for an appeal request, the commercial establishment shall be notified of a specific period in advance, as defined in the system settings. The system will not allow scheduling any meeting with a date earlier than the defined notification period.

**Traceability:**
- **BRD:** Meeting scheduling requirements
- **SRD:** Section 6.4.10.23 "Meetings setting", Pages 347-349

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-020: Configure Appeal Settings

**As a** Federal Administrator  
**I want to** configure appeal process timeframes  
**So that** appeal procedures follow consistent timelines

**Acceptance Criteria:**
1. System provides Appeal Settings interface `[SRD Section 6.4.11]`
2. Federal Administrator can configure: `[SRD Section 6.4.11]`
   - **Number of Days Allowed for Submitting Arguments:**
     - Period during which commercial establishment can submit additional arguments/justifications after hearing session minutes are shared
     - Enter number of days - Mandatory
   - **Enable/Disable Argument Submission:**
     - Option to activate or deactivate argument submission feature
     - Toggle option - Mandatory
3. Once defined period expires, commercial establishment can no longer submit arguments or justifications `[SRD Section 6.4.11]`
4. When feature is disabled, commercial establishments cannot submit additional arguments regardless of timeframe
5. System enforces configured timeframe in appeal workflow
6. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Appeal process configuration
- **SRD:** Section 6.4.11 "Appeal settings", Page 349

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-021: Configure Communication Settings

**As a** Federal Administrator  
**I want to** configure communication response timeframes  
**So that** local customs respond to commercial establishments in timely manner

**Acceptance Criteria:**
1. System provides Communication Settings interface `[SRD Section 6.4.12]`
2. Federal Administrator can configure: `[SRD Section 6.4.12]`
   - **Local Customs Response to Message:**
     - Period during which local customs should reply to messages received from commercial establishments
     - Enter number of working days - Mandatory
3. System validates that entered value is positive integer
4. System uses this setting to:
   - Track response times
   - Send reminders to local customs users
   - Generate escalations if response deadline is exceeded
5. Setting applies to all communications between local customs and commercial establishments
6. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Communication response timeframes
- **SRD:** Section 6.4.12 "Communication with Commercial Establishment Settings", Page 349

**Dependencies:**
- None

**Priority:** Must Have

---

<a name="notifications-reminders"></a>
## 7. Federal Customs Portal - Notifications and Reminders Configuration

### Epic: Notifications and Reminders Configuration
Enable Federal System Administrator to configure all system notifications, reminders, and escalations.

---

### US-ADMIN-022: Configure Reminder Settings

**As a** Federal System Administrator  
**I want to** configure reminder settings for procedures  
**So that** users receive timely reminders about pending actions

**Acceptance Criteria:**
1. System provides centralized Reminders Configuration interface `[SRD Section 6.4.10.22]`
2. System displays list of all procedures that can have reminders configured `[SRD Section 6.4.10.22, Table 83]`
3. For each procedure, Federal System Administrator can configure: `[SRD Section 5.42]`
   - **Reminder Group:**
     - AEO Portal notifications
     - Local Customs AEO management portal notifications
     - Federal AEO management portal notifications
     - Single choice list - Mandatory
   - **Reminder Type:**
     - Predefined list of reminders in system
     - Single choice selection - Mandatory
   - **Reminder Description:**
     - Predefined description to help understand reminder
     - Read only
   - **First Reminder:**
     - First Reminder Timing: Value (number) + Unit (day, week, month, year) - Mandatory
     - Reminder Arabic Subject - Mandatory
     - Reminder English Subject - Mandatory
     - Reminder Arabic Body - Mandatory (can use dynamic tokens)
     - Reminder English Body - Mandatory (can use dynamic tokens)
     - Is Enabled? - Single choice (Enabled/Disabled) - Default: Enabled
     - Reminder Recipient - Auto-captured by system
   - **Second Reminder:**
     - Second Reminder Timing: Value (number) + Unit (day, week, month, year) - Mandatory
     - Reminder Arabic Subject - Mandatory
     - Reminder English Subject - Mandatory
     - Reminder Arabic Body - Mandatory (can use dynamic tokens)
     - Reminder English Body - Mandatory (can use dynamic tokens)
     - Is Enabled? - Single choice (Enabled/Disabled) - Default: Enabled
     - Reminder Recipient - Auto-captured by system
   - **Escalation:**
     - Escalation Timing: Value (number) + Unit (day, month, year) - Mandatory - After end of allowed duration
     - Escalation Arabic Subject - Mandatory
     - Escalation English Subject - Mandatory
     - Escalation Arabic Body - Mandatory (can use dynamic tokens)
     - Escalation English Body - Mandatory (can use dynamic tokens)
     - Is Enabled? - Single choice (Enabled/Disabled) - Default: Enabled
     - Escalation Recipient - Single choice list - Mandatory
4. System allows user to specify whether escalation is applicable `[SRD Section 6.4.10.22]`
5. If escalation is applicable, user can define recipient role for escalations `[SRD Section 6.4.10.22]`
6. If reminder is disabled, system will not send it `[SRD Section 5.42]`
7. System supports following dynamic tokens in message body: `[SRD Section 6.4.10.22, Table 84]`
   - [CompanyName] - Name of commercial establishment
   - [UserName] - Name of user (first name + last name)
   - [AccountCreationsRefNumber] - Commercial Establish Account Creation Request reference number
   - [ApplicationRefNumber] - AEO Authorization Request reference number
   - [CertificateNumber] - AEO certificate number
   - [AppealRefNumber] - Appeal request reference number
   - [DueDate] - Deadline for completing procedure
   - [AEOPortal] - URL of AEO portal
   - [LocalCustomsPortal] - URL of local customs management portal
   - [FedralCustomsPortal] - URL of local department of general customs management portal
8. Tokens are automatically replaced with actual values when reminder/escalation is sent `[SRD Section 6.4.10.22]`
9. System calculates reminder timing before end of allowed duration for procedure
10. System calculates escalation timing after end of allowed duration for procedure
11. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Reminders and escalations configuration
- **SRD:** Section 6.4.10.22 "Notifications & Reminders Settings", Section 5.42 "Reminders Settings Data", Pages 151-155, 341-347

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-023: Configure Notification Settings

**As a** Federal System Administrator  
**I want to** configure notification settings for system events  
**So that** users receive appropriate notifications for important actions

**Acceptance Criteria:**
1. System provides centralized Notifications Configuration interface `[SRD Section 6.4.10.22]`
2. System displays all notification triggers referenced throughout various functions of AEO program `[SRD Section 6.4.10.22]`
3. For each notification, Federal System Administrator can configure: `[SRD Section 5.41]`
   - **Notification Group:**
     - AEO portal notifications
     - Local customs AEO management portal notifications
     - Federal AEO management portal notifications
     - System-wide notifications
     - Single choice selection - Mandatory
   - **Notification Trigger:**
     - Predefined specific system event or action that initiates notification
     - Single choice selection - Mandatory
   - **Notification Description:**
     - Predefined description to help understand notification
     - Read only
   - **Notification Arabic Subject** - Mandatory
   - **Notification English Subject** - Mandatory
   - **Notification Arabic Body** - Mandatory (can use dynamic tokens)
   - **Notification English Body** - Mandatory (can use dynamic tokens)
   - **Is Enabled?** - Single choice (Enabled/Disabled) - Default: Enabled
4. If notification is disabled, system will not send it `[SRD Section 5.41]`
5. System supports dynamic tokens in notification body (same as reminders) `[SRD Section 6.4.10.22]`
6. User can choose notification channel: `[SRD Section 6.4.10.22]`
   - Email
   - In application
   - Both
7. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Notifications configuration
- **SRD:** Section 6.4.10.22 "Notifications & Reminders Settings", Section 5.41 "Notification Settings Data", Pages 149-150, 341-347

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-024: Create System-Wide Notifications

**As a** Federal System Administrator  
**I want to** create and publish system-wide notifications  
**So that** important announcements reach all users across all portals

**Acceptance Criteria:**
1. System provides System-Wide Notifications interface `[SRD Section 6.4.10.22]`
2. Federal System Administrator can create system-wide notification with:
   - **Target Audience:**
     - AEO Portal
     - Local Customs Portal
     - Federal Customs Portal
     - Multiple selections allowed - Mandatory
   - **Notification Channel:**
     - Email
     - In application
     - Both
     - Single selection - Mandatory
   - **Arabic Subject** - Mandatory
   - **English Subject** - Mandatory
   - **Arabic Body** - Mandatory
   - **English Body** - Mandatory
   - **Effective Date/Time** - Mandatory
   - **Expiry Date/Time** - Optional
3. System-wide notifications are used for: `[SRD Section 6.4.10.22]`
   - Planned maintenance announcements
   - Major system updates
   - Critical incidents
   - General announcements
4. System validates that effective date is not in the past
5. System validates that expiry date is after effective date (if provided)
6. Once published, notification appears to all users in selected target audiences
7. Notifications automatically expire after expiry date (if set)
8. System tracks which users have read the notification
9. All system-wide notifications are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** System-wide notifications
- **SRD:** Section 6.4.10.22 "Notifications & Reminders Settings", Pages 341-347

**Dependencies:**
- None

**Priority:** Must Have

---

<a name="content-management"></a>
## 8. Federal Customs Portal - Content Management

### Epic: Content Management
Enable Federal System Administrator to manage content displayed on AEO Portal about the program.

---

### US-ADMIN-025: Manage AEO Program Content

**As a** Federal System Administrator  
**I want to** manage content about AEO program displayed on AEO Portal  
**So that** accurate and current information is available to all users

**Acceptance Criteria:**
1. System provides Content Management interface `[SRD Section 6.4.10.10]`
2. Federal System Administrator can manage following content sections: `[SRD Section 6.2.1]`
   - **Definition of AEO Program:**
     - Arabic content - Mandatory
     - English content - Mandatory
   - **Overview of National, GCC, and MRA Benefits:**
     - Arabic content - Mandatory
     - English content - Mandatory
   - **Eligibility Requirements and Conditions:**
     - Arabic content - Mandatory
     - English content - Mandatory
   - **Application Steps and Procedures:**
     - Arabic content - Mandatory
     - English content - Mandatory
   - **Frequently Asked Questions (FAQ):**
     - Can add/edit/delete FAQ items
     - Each FAQ has question and answer in both Arabic and English
3. System provides rich text editor for content creation with:
   - Text formatting (bold, italic, underline)
   - Lists (bulleted, numbered)
   - Links
   - Image upload
   - Tables
4. System allows preview of content before publishing
5. Federal System Administrator can:
   - Create new content sections
   - Edit existing content
   - Delete content sections
   - Reorder content sections
   - Publish/unpublish content
6. Content changes are effective immediately on AEO Portal after publishing
7. System maintains version history of content changes
8. All content changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Content management
- **SRD:** Section 6.4.10.10 "Content Management", Section 6.2.1 "About the AEO Program", Pages 165-166, 331

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-026: View Commercial Establishment Documents

**As a** Federal Customs User  
**I want to** view all documents related to each commercial establishment  
**So that** I can access complete documentation when needed

**Acceptance Criteria:**
1. System provides interface for Federal Customs users to view commercial establishment documents `[SRD Section 6.4.13]`
2. Federal Customs users can search for commercial establishment by:
   - Establishment name
   - Registration number
   - Certificate number
   - Application reference number
3. System displays list of all documents for selected establishment
4. Documents are organized by category/phase:
   - Account creation documents
   - Authorization request documents
   - SAQ documents
   - Assessment documents
   - Certification documents
   - Post-certification documents
5. For each document, system displays:
   - Document name
   - Document type
   - Upload date
   - Uploaded by
   - Document status
6. Federal Customs users can view/download documents
7. Access to documents follows same rules as "Commercial Establishment Documents Management" in Local Customs Portal `[SRD Section 6.4.13]`
8. All document access is recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Document access for federal customs
- **SRD:** Section 6.4.13 "Commercial Establishment Documents Management", Page 349-350

**Dependencies:**
- None

**Priority:** Should Have

---

<a name="additional-lookups"></a>
## 9. Federal Customs Portal - Additional Lookup Management

### Epic: Additional Lookup Management
Enable Federal Administrator to manage additional lookup lists used throughout the system.

---

### US-ADMIN-027: Manage Initial Risk Assessment Lookups

**As a** Federal Administrator  
**I want to** manage lookup values for initial risk assessment  
**So that** validation teams have standardized options during assessment

**Acceptance Criteria:**
1. System provides Initial Risk Assessment Lookups management interface `[SRD Section 6.4.10.11]`
2. Federal Administrator can manage lookup values for:
   - Assessment tools
   - Assessment methods
   - Other risk assessment categories (to be defined)
3. For each lookup, Federal Administrator can:
   - Add new lookup option
   - Edit existing lookup option
   - Delete lookup option (if not in use)
   - Enable/disable lookup option
4. System validates that lookup values are unique
5. Lookup options become available for Validation Team during initial risk assessment
6. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Risk assessment lookup management
- **SRD:** Section 6.4.10.11 "Managing Lookup for Initial Risk Assessment", Page 333

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-028: Manage SAQ Additional Inquiries Lookups

**As a** Federal Administrator  
**I want to** manage lookup values for SAQ additional inquiries  
**So that** validation teams have standardized inquiry options

**Acceptance Criteria:**
1. System provides SAQ Additional Inquiries Lookups management interface `[SRD Section 6.4.10.13]`
2. Federal Administrator can define predefined lookup options for "Additional Inquiries" that might be required by Validation Team Member/Lead while preparing SAQ `[SRD Section 6.4.10.13]`
3. System provides form with required fields as defined in "SAQ Inquiries Lookups Data" `[SRD Section 6.4.10.13]`
4. After adding inquiry option, it becomes available for Validation Team when preparing SAQ `[SRD Section 6.4.10.13]`
5. Federal Administrator can:
   - Add new inquiry option
   - Edit existing inquiry option
   - Delete inquiry option (if not in use)
6. System validates that inquiry options are unique
7. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ inquiries lookup management
- **SRD:** Section 6.4.10.13 "Managing Lookups Additionally Inquiries in the SAQ", Page 334

**Dependencies:**
- None

**Priority:** Must Have

---

### US-ADMIN-029: Manage Meeting Purpose Lookups

**As a** Federal System Administrator  
**I want to** manage meeting purpose lookup values  
**So that** meetings can be categorized consistently

**Acceptance Criteria:**
1. System provides Meeting Purpose Lookups management interface `[SRD Section 6.4.10.14]`
2. Federal System Administrator can define meeting purpose lookup values used when: `[SRD Section 6.4.10.14]`
   - Validation team arranges meeting with commercial establishment
   - Key Account Manager arranges meeting with commercial establishment
3. Federal System Administrator can add meeting purpose with data specified in "Meeting Purpose Lookup Data" `[SRD Section 6.4.10.14]`
4. System allows:
   - Adding new meeting purpose
   - Editing existing meeting purpose
   - Deleting meeting purpose (if not in use)
5. Meeting purposes become available in meeting scheduling interface
6. All changes are recorded in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Meeting purpose lookup management
- **SRD:** Section 6.4.10.14 "Managing Lookups for Meeting purposes", Pages 334-335

**Dependencies:**
- None

**Priority:** Must Have

---

## Summary Tables

### Phase 5 User Stories Summary by Functional Area

| Functional Area | User Stories Count | User Story IDs |
|----------------|-------------------|---------------|
| **Benefits and Benefits Groups Management** | 6 | US-ADMIN-001 to US-ADMIN-006 |
| **Violations Lookup Management** | 1 | US-ADMIN-007 |
| **Control Plan Actions Lookup** | 1 | US-ADMIN-008 |
| **MRA Management** | 4 | US-ADMIN-009 to US-ADMIN-012 |
| **User and Role Management** | 3 | US-ADMIN-013 to US-ADMIN-015 |
| **System Settings Configuration** | 6 | US-ADMIN-016 to US-ADMIN-021 |
| **Notifications and Reminders** | 3 | US-ADMIN-022 to US-ADMIN-024 |
| **Content Management** | 2 | US-ADMIN-025 to US-ADMIN-026 |
| **Additional Lookup Management** | 3 | US-ADMIN-027 to US-ADMIN-029 |
| **TOTAL** | **29** | **US-ADMIN-001 to US-ADMIN-029** |

---

### Priority Distribution

| Priority | Count | Percentage |
|----------|-------|------------|
| Must Have | 28 | 96.6% |
| Should Have | 1 | 3.4% |
| Could Have | 0 | 0% |
| Won't Have | 0 | 0% |

---

### Business Rules Referenced

| Business Rule | Description | Referenced in User Stories |
|--------------|-------------|---------------------------|
| BR.26 | When scheduling meetings whether field visits, remote meetings, or a hearing session for an appeal request, the commercial establishment shall be notified of a specific period in advance, as defined in the system settings. The system will not allow scheduling any meeting with a date earlier than the defined notification period. | US-ADMIN-019 |

---

## Traceability Matrix

### Source Document References

| User Story | Feature Area | BRD Reference | SRD Reference | Page Numbers |
|------------|--------------|---------------|---------------|--------------|
| US-ADMIN-001 | National Benefit Groups | Benefits management | Section 6.4.6, 5.14 | 96-97, 315 |
| US-ADMIN-002 | GCC Benefit Groups | Benefits management | Section 6.4.6, 5.14 | 96-97, 315 |
| US-ADMIN-003 | MRA Benefit Groups | MRA benefits | Section 6.4.6, 5.32 | 139, 315 |
| US-ADMIN-004 | National Benefits | Benefits management | Section 6.4.7, 5.15 | 97-98, 316 |
| US-ADMIN-005 | GCC Benefits | Benefits management | Section 6.4.7, 5.15 | 97-98, 316 |
| US-ADMIN-006 | MRA Benefits | MRA benefits | Section 6.2.1, 5.16 | 98, 165-166 |
| US-ADMIN-007 | Violations Lookup | Violations management | Section 6.4.10.15 | 335 |
| US-ADMIN-008 | Control Plan Actions | Control plan | Section 6.4.10.12, 5.31 | 138, 333-334 |
| US-ADMIN-009 | Add MRA | MRA management | Section 6.4.4, 6.2.1, 5.17 | 98-99, 165-166, 314 |
| US-ADMIN-010 | Revoke MRA | MRA management | Section 6.2.1 | 165-166 |
| US-ADMIN-011 | Upload MRA AEOs | MRA management | Section 6.4.4, 6.2.1 | 165-166, 314 |
| US-ADMIN-012 | Share National AEOs | MRA sharing | Section 6.4.5, 6.4.10.22 | 315, 341-347 |
| US-ADMIN-013 | Role Management | RBAC | Section 6.4.10.16, 6.4.10.16.1 | 335-336 |
| US-ADMIN-014 | Federal Users | User management | Section 6.1.3, 5.19 | 113-116, 163-165 |
| US-ADMIN-015 | Local Users | User management | Section 6.1.2, 6.1.3, 5.19 | 113-116, 162-165 |
| US-ADMIN-016 | Authorization Settings | System settings | Section 6.4.10.19 | 339-340 |
| US-ADMIN-017 | Validation Settings | System settings | Section 6.4.10.20 | 340-341 |
| US-ADMIN-018 | KPI Settings | System settings | Section 6.4.10.21 | 341 |
| US-ADMIN-019 | Meeting Settings | System settings | Section 6.4.10.23 | 347-349 |
| US-ADMIN-020 | Appeal Settings | System settings | Section 6.4.11 | 349 |
| US-ADMIN-021 | Communication Settings | System settings | Section 6.4.12 | 349 |
| US-ADMIN-022 | Reminder Settings | Notifications | Section 6.4.10.22, 5.42 | 151-155, 341-347 |
| US-ADMIN-023 | Notification Settings | Notifications | Section 6.4.10.22, 5.41 | 149-150, 341-347 |
| US-ADMIN-024 | System-Wide Notifications | Notifications | Section 6.4.10.22 | 341-347 |
| US-ADMIN-025 | Content Management | Content | Section 6.4.10.10, 6.2.1 | 165-166, 331 |
| US-ADMIN-026 | Document Access | Document management | Section 6.4.13 | 349-350 |
| US-ADMIN-027 | Risk Assessment Lookups | Lookups | Section 6.4.10.11 | 333 |
| US-ADMIN-028 | SAQ Inquiries Lookups | Lookups | Section 6.4.10.13 | 334 |
| US-ADMIN-029 | Meeting Purpose Lookups | Lookups | Section 6.4.10.14 | 334-335 |

---

## Integration with Other Phases

### Dependencies on Other Phases

| This Phase (Phase 5) | Depends On | Reason |
|---------------------|-----------|---------|
| US-ADMIN-003 | US-ADMIN-009 (MRA creation) | MRA benefit groups require MRA to exist |
| US-ADMIN-006 | US-ADMIN-003 (MRA benefit groups) | MRA benefits require benefit groups |
| US-ADMIN-012 | US-ADMIN-009 (MRA creation) | Sharing requires active MRAs |
| US-ADMIN-012 | Phase 4 (US-CERT-009) | National AEOs must be certified |

### Supports Other Phases

| This Phase (Phase 5) | Supports | How |
|---------------------|----------|-----|
| US-ADMIN-001 to US-ADMIN-006 | Phase 4 (Certificate issuance) | Benefits are assigned to certified AEOs |
| US-ADMIN-007 | Phases 1-4 (All phases) | Violations can be applied throughout lifecycle |
| US-ADMIN-008 | Phase 3 & 4 (Control plan) | Actions used in control plan development |
| US-ADMIN-009 to US-ADMIN-012 | Phase 4 (Post-certification) | MRA benefits for certified AEOs |
| US-ADMIN-013 to US-ADMIN-015 | All Phases | User access required for all system functions |
| US-ADMIN-016 to US-ADMIN-021 | All Phases | Settings control workflows across all phases |
| US-ADMIN-022 to US-ADMIN-024 | All Phases | Notifications support all processes |
| US-ADMIN-025 | Phase 1 (Account creation) | Content displayed on AEO Portal |
| US-ADMIN-027 to US-ADMIN-029 | Phases 2-4 | Lookups used in various processes |

---

## Cross-Reference with Phase 2

The following functionality related to system administration was already documented in Phase 2 and is referenced here:

| Functionality | Phase 2 User Stories | Description |
|--------------|---------------------|-------------|
| Question Bank Management | US-SAQ-001 to US-SAQ-005 | Creating, modifying, and approving question bank |
| Risks Bank Management | US-SAQ-006 to US-SAQ-008 | Creating, modifying, and managing risks bank |
| SAQ Template Management | US-SAQ-009 to US-SAQ-012 | Creating and approving SAQ templates |

These capabilities are integral parts of the system administration but were documented in Phase 2 due to their direct connection to the SAQ process.

---

## System Configuration Overview

Phase 5 provides comprehensive administrative control over the AEO system through the following configuration areas:

### 1. Master Data Management
- Benefits and benefit groups (National, GCC, MRA)
- Violations lookup
- Control plan actions
- Various operational lookups

### 2. Reference Data Management
- Mutual Recognition Agreements
- MRA partner country AEOs
- National AEO listings

### 3. User and Access Management
- Role-based access control
- Federal customs users
- Local customs users
- User activation/deactivation

### 4. Process Configuration
- Authorization request timeframes
- Validation and assessment periods
- KPI submission schedules
- Meeting scheduling rules
- Appeal process timelines
- Communication response periods

### 5. Communication Management
- Notification configuration
- Reminder settings
- Escalation rules
- System-wide announcements

### 6. Content Management
- AEO program information
- FAQ management
- Eligibility criteria
- Application procedures

---

## Implementation Notes

### Configuration Sequence
The following sequence is recommended for initial system configuration:

1. **User and Role Setup** (US-ADMIN-013 to US-ADMIN-015)
   - Define roles and permissions first
   - Create user accounts for administrators
   
2. **Master Data Setup** (US-ADMIN-001 to US-ADMIN-008)
   - Configure benefit groups and benefits
   - Set up violations and control plan actions
   - Configure operational lookups

3. **Process Configuration** (US-ADMIN-016 to US-ADMIN-021)
   - Define timeframes for all processes
   - Configure meeting and appeal settings
   - Set communication standards

4. **Communication Setup** (US-ADMIN-022 to US-ADMIN-024)
   - Configure notifications for all events
   - Set up reminders and escalations
   - Test notification delivery

5. **Content Publication** (US-ADMIN-025)
   - Publish AEO program information
   - Create FAQ content
   - Review and approve all content

6. **MRA Configuration** (US-ADMIN-009 to US-ADMIN-012) - If applicable
   - Add MRA agreements
   - Configure MRA benefits
   - Upload partner country AEO lists

### Data Migration Considerations
- Existing benefits and benefit groups need to be migrated during system setup
- Historical violation data may need to be imported
- Existing user accounts and roles should be mapped to new system

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 08, 2025 | AEO Project Team | Initial version - Phase 5 System Administration & Configuration User Stories |

---

**End of Phase 5 User Stories Document**
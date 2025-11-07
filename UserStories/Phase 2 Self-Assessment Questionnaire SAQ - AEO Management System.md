# AEO Management System - User Stories
## Phase 2: Self-Assessment Questionnaire (SAQ)

**Document Version:** 1.0  
**Date:** November 07, 2025  
**Project:** Authorized Economic Operator (AEO) Management System  
**Source Documents:**  
- Business Requirements Document (BRD) V1.11  
- System Requirements Document (SRD) V1.2.5

---

## Document Overview

### Purpose
This document contains detailed user stories for **Phase 2: Self-Assessment Questionnaire (SAQ)** of the AEO Management System. All user stories are directly derived from the Business Requirements Document (BRD V1.11) and System Requirements Document (SRD V1.2.5) without assumptions.

### Scope
Phase 2 covers the complete SAQ lifecycle including:
- **Question Bank Management** (Federal Customs)
- **Risks Bank Management** (Federal Customs)
- **SAQ Template Creation** (Federal Customs)
- **SAQ Preparation and Sharing** (Local Customs)
- **SAQ Completion** (Commercial Establishment)
- **SAQ Review and Approval** (Local Customs)
- **SAQ Workflow Management** (All Portals)

### User Roles

#### Federal Customs Portal
- **Federal Administrator:** Manages Question Bank, Risks Bank, and SAQ Templates
- **Senior Federal Administrator:** Reviews and approves Question Bank changes and SAQ Templates

#### Local Customs Portal
- **Validation Team Member:** Prepares SAQ, reviews responses, conducts assessments
- **Validation Team Lead:** Shares SAQ, approves responses, manages validation process
- **Senior Administrator:** Assigns validation teams

#### AEO Portal (Commercial Establishment)
- **Commercial Establishment Account Manager:** Manages SAQ submission and coordination
- **SAQ Editor:** Completes assigned SAQ sections

---

## Table of Contents
1. [Federal Customs Portal - Question Bank Management](#federal-customs-question-bank)
2. [Federal Customs Portal - Risks Bank Management](#federal-customs-risks-bank)
3. [Federal Customs Portal - SAQ Template Creation](#federal-customs-saq-template)
4. [Local Customs Portal - SAQ Preparation and Sharing](#local-customs-saq-preparation)
5. [AEO Portal - SAQ Completion](#aeo-portal-saq-completion)
6. [Local Customs Portal - SAQ Review and Approval](#local-customs-saq-review)
7. [All Portals - SAQ Workflow Management](#saq-workflow-management)

---

<a name="federal-customs-question-bank"></a>
## 1. Federal Customs Portal - Question Bank Management

### Epic: Question Bank Management
Enable Federal Customs to create, maintain, and manage a centralized repository of standardized questions for the Self-Assessment Questionnaire (SAQ).

---

### US-SAQ-001: Create Question Bank Groups and Leaf Groups

**As a** Federal Administrator  
**I want to** create hierarchical groups and leaf groups in the Question Bank  
**So that** questions can be organized logically by topic and business activity

**Acceptance Criteria:**
1. The system displays all top-level groups in the Question Bank
2. Federal Administrator can add new groups at any hierarchical level by clicking "Add Group"
3. System allows creation of subgroups under existing groups with unlimited hierarchical levels
4. Federal Administrator can mark a group as a "leaf group" (lowest level in hierarchy)
5. System displays "Add Question" button only for leaf groups
6. For each group/subgroup, system requires:
   - Group Name in Arabic (mandatory) `[SRD Section 5.27]`
   - Group Name in English (mandatory) `[SRD Section 5.27]`
   - Leaf Group designation (Yes/No, default: No) (mandatory) `[SRD Section 5.27]`
7. System supports mixed types at same hierarchical level (some leaf groups, some with subgroups)
8. All changes are saved with status "Draft" until submitted for review `[SRD Section 6.4.10.1]`
9. System provides "Save as Draft" option to temporarily save work `[SRD Section 6.4.10.1]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Questions Bank definition - centralized database organized by topic
- **SRD:** Section 6.4.10.1 "Managing The Questions Bank", Section 5.27 "Question Bank Group Data", Page 318-320

**Dependencies:**
- None

**Priority:** Must Have

---

### US-SAQ-002: Add Questions to Question Bank

**As a** Federal Administrator  
**I want to** add standardized questions to leaf groups in the Question Bank  
**So that** consistent evaluation criteria can be used across all local customs departments

**Acceptance Criteria:**
1. Federal Administrator navigates to a leaf group in the Question Bank
2. System displays "Add Question" button only for leaf groups
3. System presents question creation form with following mandatory fields:
   - Question Title (Arabic) - short title (mandatory) `[SRD Section 5.28]`
   - Question Title (English) - short title (mandatory) `[SRD Section 5.28]`
   - Question Text (Arabic) - full question text (mandatory) `[SRD Section 5.28]`
   - Question Text (English) - full question text (mandatory) `[SRD Section 5.28]`
   - Answer Type (mandatory) - options include: `[SRD Section 5.28]`
     - Text Area (multi-line, specify max characters)
     - Text Box (single line)
     - Single Choice List
     - Multiple Choice List
     - Yes/No
     - Numeric
     - Document
   - Activities in the Supply Chain (multiple choice) - at least one mandatory `[SRD Section 5.28]`
   - Is the Question Mandatory or Optional? (Single choice: Mandatory/Optional, default: Mandatory) (mandatory) `[SRD Section 5.28]`
4. System presents optional fields:
   - Question Explanatory Notes (Arabic and English) `[SRD Section 5.28]`
   - Question Introduction (Arabic and English) `[SRD Section 5.28]`
   - Require uploading an attachment (Yes/No) `[SRD Section 5.28]`
5. System allows Federal Administrator to designate question as "Conditional Question" `[SRD Section 5.28, 6.4.10.1]`
6. For conditional questions:
   - System displays all Yes/No, Single Choice, and Multiple Choice questions within same leaf group
   - Federal Administrator selects trigger question and specific answer option(s) that trigger the conditional question
   - System supports multiple conditional questions linked to same trigger answer
7. System saves question with status "Draft" until submitted for review
8. System provides "Save as Draft" option to continue work later

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Questions Bank supports multiple answer types and conditional questions
- **SRD:** Section 6.4.10.1 "Managing The Questions Bank", Section 5.28 "Question Data in the Question Bank", Pages 133-136, 318-320

**Dependencies:**
- US-SAQ-001 (Question Bank groups must exist)

**Priority:** Must Have

---

### US-SAQ-003: Modify Question Bank Groups and Questions

**As a** Federal Administrator  
**I want to** modify existing groups, subgroups, and questions in the Question Bank  
**So that** the Question Bank remains current and accurate

**Acceptance Criteria:**
1. Federal Administrator can edit any group, subgroup, or question in "Published" status
2. System allows modification of all editable attributes of groups and questions
3. For groups, if Federal Administrator changes "leaf group" attribute:
   - Changing TO leaf group: System warns that all subgroups and leaf groups under it will be deleted after approval
   - Changing FROM leaf group: System warns that all questions under it will be deleted after approval `[SRD Section 6.4.10.1]`
4. System tracks all changes and creates a change request
5. Federal Administrator can "Save as Draft" at any point during modifications
6. After completing modifications, Federal Administrator clicks "Submit" to submit changes for review
7. System changes Question Bank status to "Under Review" `[SRD Section 6.4.10.3]`
8. System sends notification to Senior Federal Administrator for review `[SRD Section 6.4.10.4]`
9. Changes do not affect published SAQ templates or SAQs already shared with commercial establishments `[SRD Section 6.4.10.1]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Question Bank modification capabilities
- **SRD:** Section 6.4.10.1 "Managing The Questions Bank", Section 6.4.10.3 "Statuses of the Question Bank", Pages 318-323

**Dependencies:**
- US-SAQ-001, US-SAQ-002

**Priority:** Must Have

---

### US-SAQ-004: Delete Question Bank Groups and Questions

**As a** Federal Administrator  
**I want to** delete groups or questions from the Question Bank  
**So that** outdated or irrelevant content can be removed

**Acceptance Criteria:**
1. Federal Administrator can select any group or question for deletion
2. System warns Federal Administrator about deletion consequences:
   - Deleting a group: All associated subgroups, leaf groups, and questions will be deleted `[SRD Section 6.4.10.1]`
   - Deleting a question: Question removed from Question Bank
3. Federal Administrator confirms deletion
4. System marks items for deletion and creates a change request
5. Federal Administrator submits deletion request for approval
6. System changes Question Bank status to "Under Review"
7. System sends notification to Senior Federal Administrator
8. Deletion does not take effect until approved by Senior Federal Administrator
9. Changes do not affect published SAQ templates or SAQs already shared with commercial establishments `[SRD Section 6.4.10.1]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Question Bank deletion capabilities
- **SRD:** Section 6.4.10.1 "Managing The Questions Bank", Pages 318-320

**Dependencies:**
- US-SAQ-001, US-SAQ-002

**Priority:** Must Have

---

### US-SAQ-005: Review and Approve Question Bank Changes

**As a** Senior Federal Administrator  
**I want to** review and approve/reject/return Question Bank changes  
**So that** quality and accuracy of the Question Bank is maintained

**Acceptance Criteria:**
1. System sends notification to Senior Federal Administrator when changes are submitted `[SRD Section 6.4.10.4]`
2. Senior Federal Administrator navigates to Question Bank management section
3. System displays list of all pending changes with visual indicators
4. For group changes (add/delete/modify):
   - System highlights the affected group
   - System displays available actions: Accept, Reject, Return `[SRD Section 6.4.10.2]`
5. For question changes (add/delete/modify):
   - System highlights groups containing affected questions
   - Senior Federal Administrator navigates through highlighted path to reach the question
   - System displays available actions next to the question: Accept, Reject, Return `[SRD Section 6.4.10.2]`
6. For "Return" action:
   - Senior Federal Administrator adds remarks on questions or groups
   - System returns changes to Federal Administrator with all remarks visible
   - System changes status to "Returned" `[SRD Section 6.4.10.3]`
7. For "Accept" action:
   - System updates Question Bank with approved changes
   - System changes status to "Published" `[SRD Section 6.4.10.3]`
   - Updated Question Bank becomes accessible for SAQ template configuration
   - System sends approval notification to Federal Administrator `[SRD Section 6.4.10.4]`
8. For "Reject" action:
   - System discards changes
   - System changes status to "Rejected" `[SRD Section 6.4.10.3]`
   - System sends rejection notification to Federal Administrator `[SRD Section 6.4.10.4]`
9. If pending changes exist, system restricts all modifications to Question Bank and SAQ templates until approved or rejected `[SRD Section 6.4.10.1]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Question Bank approval workflow
- **SRD:** Section 6.4.10.2 "Reviewing the Questions Bank", Section 6.4.10.3 "Statuses of the Question Bank", Section 6.4.10.4 "Notifications", Pages 320-323

**Dependencies:**
- US-SAQ-003, US-SAQ-004

**Priority:** Must Have

---

<a name="federal-customs-risks-bank"></a>
## 2. Federal Customs Portal - Risks Bank Management

### Epic: Risks Bank Management
Enable Federal Customs to create and maintain a centralized repository of standardized risks for validation and risk assessment.

---

### US-SAQ-006: Create Risks Bank Groups and Leaf Groups

**As a** Federal Administrator  
**I want to** create hierarchical groups and leaf groups in the Risks Bank  
**So that** risks can be organized logically for the validation process

**Acceptance Criteria:**
1. System displays all top-level groups in the Risks Bank
2. Federal Administrator can add new risk groups at any hierarchical level
3. System allows creation of subgroups under existing risk groups with unlimited hierarchical levels
4. Federal Administrator can mark a group as a "leaf group" (lowest level)
5. System displays "Add Risk" functionality only for leaf groups
6. For each risk group, system requires:
   - Group Name (Arabic) (mandatory) `[SRD Section 5.33]`
   - Group Name (English) (mandatory) `[SRD Section 5.33]`
   - Is it Leaf Group? (Yes/No, default: No) (mandatory) `[SRD Section 5.33]`
7. System supports mixed types at same hierarchical level
8. Changes are saved as per Risks Bank modification workflow

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Risks Bank definition - centralized repository of standardized risks
- **SRD:** Section 6.4.10.5 "Managing the Risks Bank", Section 5.33 "Risks Group Data", Pages 139-140, 324-325

**Dependencies:**
- None

**Priority:** Must Have

---

### US-SAQ-007: Add Risks to Risks Bank

**As a** Federal Administrator  
**I want to** add standardized risks to leaf groups in the Risks Bank  
**So that** validation teams can use consistent risk assessment criteria

**Acceptance Criteria:**
1. Federal Administrator navigates to a leaf group in the Risks Bank
2. System provides functionality to add risks to leaf groups
3. System presents risk creation form with required fields as per Risks Lookup Data `[SRD Section 5.34]`
4. Federal Administrator enters risk details in Arabic and English
5. System saves risk and associates it with the leaf group
6. Changes to Risks Bank do not affect approved/draft/under review "Initial Risk Assessment and Assessment Plan" `[SRD Section 6.4.10.5]`
7. Changes do not affect approved "Assessment File" `[SRD Section 6.4.10.5]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Risks Bank content management
- **SRD:** Section 6.4.10.5 "Managing the Risks Bank", Section 5.34 "Risks Lookup Data", Pages 140, 324-325

**Dependencies:**
- US-SAQ-006

**Priority:** Must Have

---

### US-SAQ-008: Modify and Delete Risks Bank Content

**As a** Federal Administrator  
**I want to** modify or delete risk groups and risks in the Risks Bank  
**So that** the Risks Bank remains current and accurate

**Acceptance Criteria:**
1. Federal Administrator can modify existing risk groups and risks
2. Federal Administrator can delete risk groups or individual risks
3. When deleting a risk group, system deletes all associated subgroups, leaf groups, and risks `[SRD Section 6.4.10.5]`
4. Changes follow same review and approval workflow as Question Bank
5. Changes do not impact previous assessments `[SRD Section 6.4.10.5]`
6. Changes do not affect approved/draft/under review "Initial Risk Assessment and Assessment Plan" `[SRD Section 6.4.10.5]`
7. Changes do not affect approved "Assessment File" `[SRD Section 6.4.10.5]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Risks Bank modification capabilities
- **SRD:** Section 6.4.10.5 "Managing the Risks Bank", Page 324-325

**Dependencies:**
- US-SAQ-006, US-SAQ-007

**Priority:** Must Have

---

<a name="federal-customs-saq-template"></a>
## 3. Federal Customs Portal - SAQ Template Creation

### Epic: SAQ Template Creation and Management
Enable Federal Customs to create standardized SAQ templates that will be used by local customs departments.

---

### US-SAQ-009: Create New SAQ Template from Scratch

**As a** Federal Administrator  
**I want to** create a new SAQ template from scratch  
**So that** local customs departments have a standardized framework for evaluating commercial establishments

**Acceptance Criteria:**
1. System displays list of all SAQ templates at various stages
2. Federal Administrator clicks "Create New Template"
3. System presents initial data entry form with fields: `[SRD Section 5.30]`
   - Template Name (mandatory)
   - Template Description (optional)
4. After saving initial data, template appears in SAQ template list with status "Draft" `[SRD Section 6.4.10.8]`
5. System displays edit icon next to the new template
6. Federal Administrator clicks edit icon to access template structure editor
7. System allows Federal Administrator to:
   - Add sections and sub-sections up to 3 levels `[SRD Section 6.4.10.6]`
   - Mark sections as "leaf sections" `[SRD Section 5.30]`
8. For each section/sub-section, system requires: `[SRD Section 5.30]`
   - Section Name (Arabic) (mandatory)
   - Section Name (English) (mandatory)
   - Section Introduction (Arabic) (optional)
   - Section Introduction (English) (optional)
   - Section Explanatory Notes (Arabic) (optional)
   - Section Explanatory Notes (English) (optional)
   - Is it Leaf Section? (Yes/No, default: No) (mandatory)
9. For each leaf section, Federal Administrator must define:
   - Questions: System retrieves all questions from Question Bank, allowing selection of relevant questions `[SRD Section 6.4.10.6]`
   - Risks: System retrieves all risk groups and leaf groups, allowing selection of risks for validation team `[SRD Section 6.4.10.6]`
10. Federal Administrator can "Save as Draft" at any point `[SRD Section 6.4.10.6]`
11. After completing structure, Federal Administrator clicks "Submit" to submit for review
12. System changes template status to "Under Review" `[SRD Section 6.4.10.8]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ Template Creation Process
- **SRD:** Section 4.4.6 "Self-Assessment Questionnaire (SAQ) Template Creation Process", Section 6.4.10.6 "Creating the SAQ Template", Section 5.30 "Self-Assessment Questionnaire Template Creation Data", Pages 48-49, 136-138, 325-327

**Dependencies:**
- US-SAQ-002 (Question Bank must have published questions)
- US-SAQ-007 (Risks Bank must have risks)

**Priority:** Must Have

---

### US-SAQ-010: Duplicate Existing SAQ Template

**As a** Federal Administrator  
**I want to** duplicate an existing published SAQ template  
**So that** I can quickly create variations of templates without starting from scratch

**Acceptance Criteria:**
1. Federal Administrator navigates to SAQ template list page
2. System displays copy icon next to each published template `[SRD Section 6.4.10.6]`
3. Federal Administrator clicks copy icon
4. System prompts for initial data: Template Name and Template Description `[SRD Section 6.4.10.6]`
5. Federal Administrator enters new template name and optional description
6. System creates new template with status "Draft" `[SRD Section 6.4.10.8]`
7. System automatically retrieves latest versions of all questions from Question Bank and updates them in copied template `[SRD Section 6.4.10.6]`
8. Federal Administrator can freely edit all elements: sections, sub-sections, questions `[SRD Section 6.4.10.6]`
9. Federal Administrator can "Save as Draft" to continue work later
10. After completing modifications, Federal Administrator submits template for review

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ Template duplication capability
- **SRD:** Section 6.4.10.6 "Creating the SAQ Template", Pages 326-327

**Dependencies:**
- US-SAQ-009 (At least one published template must exist)

**Priority:** Must Have

---

### US-SAQ-011: Review and Approve SAQ Template

**As a** Senior Federal Administrator  
**I want to** review and approve/reject/return SAQ templates  
**So that** only quality-assured templates are published to local customs departments

**Acceptance Criteria:**
1. System displays list of all SAQ templates at various stages
2. Senior Federal Administrator selects template with status "Under Review"
3. System displays full template structure including all sections and questions `[SRD Section 6.4.10.7]`
4. Senior Federal Administrator can add remarks by clicking "Add Remarks" next to: `[SRD Section 6.4.10.7]`
   - Sections
   - Sub-sections
   - Leaf sections
   - Questions
5. Senior Federal Administrator can "Save as Draft" and return later to complete review `[SRD Section 6.4.10.7]`
6. Upon completing review, Senior Federal Administrator has two options:
   
   **Option 1: Return for Revisions**
   - Senior Federal Administrator clicks "Return" button `[SRD Section 6.4.10.7]`
   - System returns template with all remarks visible to Federal Administrator
   - System changes status to "Returned" `[SRD Section 6.4.10.8]`
   - System sends notification to Federal Administrator `[SRD Section 6.4.10.9]`
   
   **Option 2: Approve Template**
   - Senior Federal Administrator clicks "Approve" button `[SRD Section 6.4.10.7]`
   - System publishes approved SAQ template to all local customs departments
   - System changes status to "Published" `[SRD Section 6.4.10.8]`
   - Template becomes locked and cannot be edited `[SRD Section 6.4.10.7]`
   - Template becomes available for use by all local customs departments
   - System sends approval notification to Federal Administrator `[SRD Section 6.4.10.9]`
   
7. Once published, modifications to questions in Question Bank will NOT be reflected in already published SAQ templates `[SRD Section 6.4.10.7]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ Template approval workflow
- **SRD:** Section 6.4.10.7 "Reviewing the SAQ Template", Section 6.4.10.8 "Statuses of the SAQ Template", Section 6.4.10.9 "Notifications", Pages 327-330

**Dependencies:**
- US-SAQ-009, US-SAQ-010

**Priority:** Must Have

---

<a name="local-customs-saq-preparation"></a>
## 4. Local Customs Portal - SAQ Preparation and Sharing

### Epic: SAQ Preparation and Distribution
Enable Local Customs to prepare customized SAQ for commercial establishments and share them for completion.

---

### US-SAQ-012: Assign Validation Team to AEO Authorization Request

**As a** Senior Administrator (Local Customs)  
**I want to** assign a validation team to an approved AEO Authorization Request  
**So that** the SAQ preparation process can begin

**Acceptance Criteria:**
1. Senior Administrator navigates to page displaying all requests accepted by relevant customs department
2. System displays "Assign Validation Team" button for each approved request `[SRD Section 6.3.4.1.1]`
3. Senior Administrator clicks "Assign Validation Team" button
4. System displays list of all available validation teams
5. Senior Administrator selects one validation team per request `[SRD Section 6.3.4.1.1]`
6. Upon assignment confirmation:
   - System automatically sends notification to selected validation team confirming assignment `[SRD Section 6.3.4.1.1, 6.3.4.1.5]`
   - System changes status to "Validation Team Assigned" `[SRD Section 6.3.4.1.4]`
7. Validation team receives notification via email and Local Customs AEO management portal `[SRD Section 6.3.4.1.5]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Validation team assignment process
- **SRD:** Section 6.3.4.1.1 "Assigning the Validation Team", Section 6.3.4.1.4 "Statuses of Self-Assessment Questionnaire", Section 6.3.4.1.5 "Notifications", Pages 239-240, 243-246

**Dependencies:**
- Phase 1 completed (AEO Authorization Request approved)

**Priority:** Must Have

---

### US-SAQ-013: Generate and Customize SAQ from Template

**As a** Validation Team Member/Lead  
**I want to** generate an SAQ from a template and customize it for the commercial establishment  
**So that** only relevant questions based on the establishment's supply chain activities are included

**Acceptance Criteria:**
1. Validation Team Member/Lead navigates to list of commercial establishments assigned to logged-in user `[SRD Section 6.3.4.1.2]`
2. Validation Team Member/Lead clicks "Create SAQ" button
3. System prompts user to select appropriate SAQ template from list of published SAQ templates `[SRD Section 6.3.4.1.2]`
4. System automatically filters and displays only questions and sections that correspond to supply chain activities in the "AEO Authorization Request" `[SRD Section 6.3.4.1.2]`
5. System enables user to add additional inquiries for commercial establishment, with fields: `[SRD Section 5.5]`
   - Question Title (Arabic) (mandatory)
   - Question Title (English) (mandatory)
   - Question Text (Arabic) (mandatory)
   - Question Text (English) (mandatory)
   - Answer Type (mandatory): Text Area, Text Box, Single Choice List, Multiple Choice List, Yes/No, Numeric, Document
   - Conditional Question? (Yes/No, default: No)
   - Question Explanatory Notes (Arabic and English) (optional)
   - Question Introduction (Arabic and English) (optional)
   - Is the Question Mandatory or Optional? (Mandatory/Optional, default: Mandatory) (mandatory)
6. For establishments with headquarters and branches:
   - Emirates allowing single request: One SAQ for headquarters and branches in that emirate `[SRD Section 6.3.4.1.2]`
   - Emirates not allowing single request: Separate SAQ for each branch `[SRD Section 6.3.4.1.2]`
7. System provides three actions:
   - **Share SAQ:** Assign SAQ to commercial establishment (Validation Team Lead only) `[SRD Section 6.3.4.1.2]`
   - **Cancel:** Discard SAQ creation process `[SRD Section 6.3.4.1.2]`
   - **Save as Draft:** Temporarily save SAQ to resume later `[SRD Section 6.3.4.1.2]`
8. When saved as draft, system changes status to "SAQ Generated" `[SRD Section 6.3.4.1.4]`
9. When preparation complete and ready to share, status changes to "SAQ Ready for Sharing" `[SRD Section 6.3.4.1.4]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ Preparation Process aligned with commercial establishment activities
- **SRD:** Section 4.2.1 "Self-Assessment Questionnaire Preparation Process", Section 6.3.4.1.2 "Preparing and Sharing the SAQ with the Commercial Establishment", Section 5.5 "Create SAQ Data", Pages 37, 69-71, 240-241

**Dependencies:**
- US-SAQ-011 (Published SAQ templates must exist)
- US-SAQ-012 (Validation team must be assigned)

**Priority:** Must Have

---

### US-SAQ-014: Share SAQ with Commercial Establishment

**As a** Validation Team Lead  
**I want to** share the prepared SAQ with the commercial establishment  
**So that** they can complete the questionnaire

**Acceptance Criteria:**
1. Validation Team Lead accesses SAQ with status "SAQ Ready for Sharing"
2. Validation Team Lead reviews complete SAQ structure and questions
3. Validation Team Lead clicks "Share SAQ" button
4. System officially assigns SAQ to commercial establishment
5. System changes status to "SAQ Shared" `[SRD Section 6.3.4.1.4]`
6. System sends notification to commercial establishment users:
   - Commercial Establishment Account Manager `[SRD Section 6.2.4.7]`
   - All SAQ Editors `[SRD Section 6.2.4.7]`
7. Notification sent via email and AEO Portal `[SRD Section 6.2.4.7]`
8. SAQ becomes accessible in Commercial Establishment's AEO Portal
9. Validation Team Lead receives confirmation that SAQ has been shared

**Business Rules:**
- BR.16: The commercial establishment must complete the self-assessment questionnaire within 15 business days from the date it was sent by the relevant customs administration `[SRD Section 6.2.4.1]`

**Traceability:**
- **BRD:** SAQ sharing with commercial establishment
- **SRD:** Section 6.3.4.1.2 "Preparing and Sharing the SAQ with the Commercial Establishment", Section 6.2.4.7 "Notifications", Pages 240-241, 191-192

**Dependencies:**
- US-SAQ-013

**Priority:** Must Have

---

<a name="aeo-portal-saq-completion"></a>
## 5. AEO Portal - SAQ Completion

### Epic: SAQ Completion by Commercial Establishment
Enable commercial establishments to complete the Self-Assessment Questionnaire shared by local customs.

---

### US-SAQ-015: Assign SAQ Sections to Users

**As a** Commercial Establishment Account Manager  
**I want to** assign SAQ sections to specific SAQ editors  
**So that** the questionnaire completion work can be distributed among team members

**Acceptance Criteria:**
1. Commercial Establishment Account Manager receives notification that SAQ is shared
2. Commercial Establishment Account Manager accesses SAQ in AEO Portal
3. System displays complete SAQ structure with all sections and questions
4. Commercial Establishment Account Manager can assign each section to a specific SAQ editor `[SRD Section 6.2.4.1]`
5. All SAQ sections are visible to all users assigned to the SAQ `[SRD Section 6.2.4.1]`
6. Only the owner of a section can amend/answer questions in that section `[SRD Section 6.2.4.1]`
7. Users not assigned to a section can add internal comments on that section `[SRD Section 6.2.4.1]`
8. Section owner can reply to internal comments `[SRD Section 6.2.4.1]`
9. System tracks section assignments for audit purposes

**Business Rules:**
- BR.14: Multiple users can fill out the self-assessment questionnaire simultaneously (in parallel) `[SRD Section 6.2.4.1]`

**Traceability:**
- **BRD:** SAQ collaborative completion capabilities
- **SRD:** Section 6.2.4.1 "Completing the Self-Assessment Questionnaire", Page 186-187

**Dependencies:**
- US-SAQ-014

**Priority:** Must Have

---

### US-SAQ-016: Complete SAQ Questions

**As an** SAQ Editor  
**I want to** answer questions in my assigned SAQ sections  
**So that** the commercial establishment can provide required information to customs

**Acceptance Criteria:**
1. SAQ Editor accesses assigned sections in AEO Portal
2. System displays current SAQ status as "SAQ Received" (when first received) or "SAQ In Progress" (when started) `[SRD Section 6.2.4.6]`
3. For each question, SAQ Editor has two options:
   - **If applicable:** Enter response in answer field based on answer type (text, choice, numeric, document upload) `[SRD Section 6.2.4.1]`
   - **If not applicable:** Click "Not Applicable" button next to question `[SRD Section 6.2.4.1]`
4. If question is marked as "Mandatory", system does not allow marking as "Not Applicable" `[SRD Section 5.28]`
5. For conditional questions, system displays question only when trigger condition is met
6. For questions requiring document upload, system provides file upload functionality
7. System validates answer format based on answer type (numeric, text length, etc.)
8. SAQ Editor can add internal comments on any section for collaboration
9. When SAQ Editor starts answering questions, status changes to "SAQ In Progress" `[SRD Section 6.2.4.6]`
10. System auto-saves progress periodically

**Business Rules:**
- BR.14: Multiple users can fill out the self-assessment questionnaire simultaneously (in parallel) `[SRD Section 6.2.4.1]`
- BR.15: The self-assessment questionnaire does not require sequential completion by section or subsection; users can freely navigate between questions `[SRD Section 6.2.4.1]`
- BR.16: The commercial establishment must complete the self-assessment questionnaire within 15 business days from the date it was sent by the relevant customs administration `[SRD Section 6.2.4.1]`

**Traceability:**
- **BRD:** SAQ completion by commercial establishment
- **SRD:** Section 6.2.4.1 "Completing the Self-Assessment Questionnaire", Section 6.2.4.6 "Statuses of Self-Assessment Questionnaire", Pages 186-191

**Dependencies:**
- US-SAQ-015

**Priority:** Must Have

---

### US-SAQ-017: Save SAQ as Draft

**As an** SAQ Editor  
**I want to** save the SAQ as draft while completing it  
**So that** I can continue work later without losing progress

**Acceptance Criteria:**
1. SAQ Editor clicks "Save as Draft" button at any time while completing SAQ `[SRD Section 6.2.4.2]`
2. System saves all entered responses and data
3. System maintains status as "SAQ In Progress" `[SRD Section 6.2.4.6]`
4. SAQ Editor can close and return later to continue work
5. Upon return, system displays SAQ with all previously saved responses
6. No notifications are sent when saving as draft

**Business Rules:**
- BR.15: The self-assessment questionnaire does not require sequential completion by section or subsection; users can freely navigate between questions `[SRD Section 6.2.4.1]`

**Traceability:**
- **BRD:** SAQ draft save capability
- **SRD:** Section 6.2.4.2 "Saving the Self-Assessment Questionnaire as a Draft", Page 188

**Dependencies:**
- US-SAQ-016

**Priority:** Must Have

---

### US-SAQ-018: Track SAQ Status

**As a** Commercial Establishment Account Manager or SAQ Editor  
**I want to** view the current status of the SAQ  
**So that** I can monitor progress and deadlines

**Acceptance Criteria:**
1. User navigates to account homepage in AEO Portal
2. System displays current SAQ status in the SAQ section `[SRD Section 6.2.4.3]`
3. Possible statuses displayed: `[SRD Section 6.2.4.6]`
   - SAQ Received
   - SAQ In Progress
   - SAQ Submitted
   - SAQ Under Review
   - SAQ Returned
   - SAQ Approved
   - SAQ Cancelled
   - SAQ Expired
4. System displays remaining days to submit SAQ (15 business days deadline)
5. System provides visual indicators for approaching deadline
6. User can click on status to view detailed SAQ information

**Business Rules:**
- BR.16: The commercial establishment must complete the self-assessment questionnaire within 15 business days from the date it was sent by the relevant customs administration `[SRD Section 6.2.4.1]`

**Traceability:**
- **BRD:** SAQ status visibility for commercial establishment
- **SRD:** Section 6.2.4.3 "Tracking the Status of the Self-Assessment Questionnaire", Section 6.2.4.6 "Statuses of Self-Assessment Questionnaire", Pages 188, 189-191

**Dependencies:**
- US-SAQ-014

**Priority:** Must Have

---

### US-SAQ-019: Filter and Search SAQ Questions

**As an** SAQ Editor  
**I want to** filter and search questions within the SAQ  
**So that** I can efficiently locate and manage specific questions

**Acceptance Criteria:**
1. System provides filtering functionality with following criteria: `[SRD Section 6.2.4.4]`
   - **Answer Status:** Answered, Unanswered, Applicable, Not Applicable, Accepted, Not Accepted
   - **Leaf Section:** Questions associated with specific leaf section
   - **Compound filtering:** Apply multiple filters simultaneously
2. User selects one or more filter criteria
3. System displays only questions matching selected criteria
4. System shows count of filtered results
5. User can clear filters to view all questions again
6. Filter selections persist during the session
7. System maintains filter state when navigating between sections

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ question filtering capabilities
- **SRD:** Section 6.2.4.4 "Filtering Questions within the Self-Assessment Questionnaire", Pages 187-188

**Dependencies:**
- US-SAQ-016

**Priority:** Should Have

---

### US-SAQ-020: Submit Completed SAQ

**As a** Commercial Establishment Account Manager  
**I want to** submit the completed SAQ to local customs  
**So that** the validation process can proceed

**Acceptance Criteria:**
1. Commercial Establishment Account Manager reviews all SAQ sections for completeness
2. System validates that all mandatory questions are answered or marked as "Not Applicable" (if allowed)
3. Commercial Establishment Account Manager clicks "Submit" button `[SRD Section 6.2.4.1]`
4. System confirms submission with user
5. Upon confirmation:
   - System changes status to "SAQ Submitted" `[SRD Section 6.2.4.6]`
   - System sends SAQ to relevant customs department via system
   - System sends confirmation notification to Commercial Establishment Account Manager and SAQ Editors `[SRD Section 6.2.4.7]`
   - Notification sent via email and AEO Portal `[SRD Section 6.2.4.7]`
6. System timestamps submission for compliance with 15 business days deadline
7. SAQ becomes read-only for commercial establishment users
8. System notifies Validation Team that SAQ is ready for review `[SRD Section 6.3.4.1.5]`

**Business Rules:**
- BR.16: The commercial establishment must complete the self-assessment questionnaire within 15 business days from the date it was sent by the relevant customs administration `[SRD Section 6.2.4.1]`

**Traceability:**
- **BRD:** SAQ submission to customs
- **SRD:** Section 6.2.4.1 "Completing the Self-Assessment Questionnaire", Section 6.2.4.6 "Statuses of Self-Assessment Questionnaire", Section 6.2.4.7 "Notifications", Pages 186-192

**Dependencies:**
- US-SAQ-016

**Priority:** Must Have

---

<a name="local-customs-saq-review"></a>
## 6. Local Customs Portal - SAQ Review and Approval

### Epic: SAQ Review and Evaluation
Enable Local Customs validation team to review SAQ responses and make acceptance decisions.

---

### US-SAQ-021: Allocate SAQ Sections to Validation Team Members

**As a** Validation Team Lead  
**I want to** assign SAQ sections to validation team members for review  
**So that** the review workload can be distributed efficiently

**Acceptance Criteria:**
1. System notifies Validation Team when SAQ is submitted by commercial establishment `[SRD Section 6.3.4.1.3, 6.3.4.1.5]`
2. System changes status to "SAQ Received" `[SRD Section 6.3.4.1.4]`
3. Validation Team Lead accesses submitted SAQ
4. System displays complete SAQ structure with all sections and responses
5. Validation Team Lead assigns each section to specific validation team member (including self) `[SRD Section 6.3.4.1.3]`
6. All SAQ sections are visible to all validators assigned to the SAQ `[SRD Section 6.3.4.1.3]`
7. Only the owner of a section can amend/evaluate questions in that section `[SRD Section 6.3.4.1.3]`
8. System tracks section assignments
9. Assigned validation team members receive notification of their assignments

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ review workload distribution
- **SRD:** Section 6.3.4.1.3 "Reviewing the SAQ", Section 6.3.4.1.5 "Notifications", Pages 241-243, 245-246

**Dependencies:**
- US-SAQ-020

**Priority:** Must Have

---

### US-SAQ-022: Review and Evaluate SAQ Responses

**As a** Validation Team Member/Lead  
**I want to** review each SAQ response and determine if it is acceptable  
**So that** I can assess the commercial establishment's compliance

**Acceptance Criteria:**
1. System displays list of commercial establishments with submitted SAQs assigned to logged-in validation team member
2. Validation Team Member/Lead clicks to review assigned SAQ sections
3. When review starts, system changes status to "SAQ Under Review" `[SRD Section 6.3.4.1.4]`
4. For each question response, Validation Team Member/Lead evaluates and marks as: `[SRD Section 6.3.4.1.3]`
   - **Acceptable:** Approve without further action; optionally add remarks for establishment to view
   - **Not Acceptable:** Must enter mandatory comment explaining rejection reason; comment visible to establishment when SAQ returned
5. When new comment is added, system assigns status "Open" to the comment `[SRD Section 6.3.4.1.3]`
6. Validation Team Member/Lead can mark comment as "Resolved" when establishment takes necessary action `[SRD Section 6.3.4.1.3]`
7. During review, validation team member can:
   - Add comments to any section (including sections not assigned to them) `[SRD Section 6.3.4.1.3]`
   - View internal comments added by other validation team members `[SRD Section 6.3.4.1.3]`
   - Identify which phase comments were added (SAQ review, initial risk assessment, on-site validation) `[SRD Section 6.3.4.1.3]`
   - Reply to comments `[SRD Section 6.3.4.1.3]`
8. System tracks all review activities in audit trail
9. System allows saving review progress

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ response evaluation by validation team
- **SRD:** Section 6.3.4.1.3 "Reviewing the SAQ", Pages 241-243

**Dependencies:**
- US-SAQ-021

**Priority:** Must Have

---

### US-SAQ-023: Return SAQ to Commercial Establishment for Modifications

**As a** Validation Team Lead  
**I want to** return the SAQ to the commercial establishment with comments  
**So that** they can address unacceptable answers and provide additional information

**Acceptance Criteria:**
1. Validation Team Lead reviews all evaluated SAQ responses
2. If there are "not acceptable" answers, Validation Team Lead clicks "Return" button `[SRD Section 6.3.4.1.3]`
3. System returns SAQ to commercial establishment through system with all associated comments `[SRD Section 6.3.4.1.3]`
4. System changes status to "SAQ Returned" `[SRD Section 6.3.4.1.4]`
5. System sends notification to Commercial Establishment Account Manager and SAQ Editors via email and AEO Portal `[SRD Section 6.2.4.7, 6.3.4.1.5]`
6. Commercial establishment can view:
   - All questions with classification: "Accepted" or "Not Accepted"
   - Remarks from customs department (visible via "Show Remark" button for questions with comments)
   - Remark status: "Open" or "Resolved"
7. If SAQ not returned within allowed time period, Validation Team Lead can mark it as "Expired" `[SRD Section 6.3.4.1.3, 6.3.4.1.4]`
8. System tracks return in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ return for corrections
- **SRD:** Section 6.3.4.1.3 "Reviewing the SAQ", Section 6.3.4.1.4 "Statuses of Self-Assessment Questionnaire", Section 6.2.4.5 "Modifying Self-Assessment Questionnaire Answers After Return", Pages 188-189, 241-245

**Dependencies:**
- US-SAQ-022

**Priority:** Must Have

---

### US-SAQ-024: Modify and Resubmit Returned SAQ

**As a** Commercial Establishment Account Manager or SAQ Editor  
**I want to** modify SAQ answers that were marked as "Not Accepted"  
**So that** I can address customs department's concerns and resubmit

**Acceptance Criteria:**
1. System sends notification when SAQ is returned `[SRD Section 6.2.4.5]`
2. System updates status to "SAQ Returned" `[SRD Section 6.2.4.6]`
3. Users access returned SAQ and view customs department remarks
4. For each question, system displays classification: "Accepted" or "Not Accepted" `[SRD Section 6.2.4.5]`
5. For questions with remarks, "Show Remark" button is displayed `[SRD Section 6.2.4.5]`
6. Clicking "Show Remark" opens popup containing customs remark and remark status (Open/Resolved) `[SRD Section 6.2.4.5]`
7. For "Not Accepted" questions, users have two options: `[SRD Section 6.2.4.5]`
   - **Edit Answer:** Click edit icon to modify response or mark as "Not Applicable"
   - **Add Comment:** Click "Add Remark" button to respond to customs remark
8. "Accepted" answers appear in read-only mode and cannot be modified `[SRD Section 6.2.4.5]`
9. After completing modifications, Commercial Establishment Account Manager clicks "Submit" button `[SRD Section 6.2.4.5]`
10. System changes status to "SAQ Submitted" `[SRD Section 6.2.4.6]`
11. System sends notification to Validation Team for re-review `[SRD Section 6.3.4.1.5]`
12. System logs all previous answers and modifications for audit `[SRD Section 6.2.4.5]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ modification after return
- **SRD:** Section 6.2.4.5 "Modifying Self-Assessment Questionnaire Answers After Return", Section 6.2.4.6 "Statuses of Self-Assessment Questionnaire", Pages 188-191

**Dependencies:**
- US-SAQ-023

**Priority:** Must Have

---

### US-SAQ-025: Review Resubmitted SAQ

**As a** Validation Team Member/Lead  
**I want to** review resubmitted SAQ with focus on modified answers  
**So that** I can efficiently re-evaluate changes without re-reviewing accepted items

**Acceptance Criteria:**
1. System reassigns resubmitted SAQ to same Validation Team `[SRD Section 6.3.4.1.3]`
2. System changes status to "SAQ Received" then "SAQ Under Review" when review starts `[SRD Section 6.3.4.1.4]`
3. System sends notification to Validation Team about resubmission `[SRD Section 6.3.4.1.5]`
4. System displays visual indicator highlighting questions that have been modified or responded to `[SRD Section 6.3.4.1.3]`
5. Previously accepted questions are shown in read-only mode and cannot be edited `[SRD Section 6.3.4.1.3]`
6. Validation Team focuses review on updated items
7. Validation Team Member/Lead evaluates modified responses and commercial establishment's comments
8. Validation Team Member/Lead marks responses as "Accepted" or "Not Accepted"
9. Validation Team Member/Lead can update remark status from "Open" to "Resolved"
10. After review, Validation Team Lead can:
    - Return SAQ again if still not acceptable (repeat cycle)
    - Approve SAQ if all responses are now acceptable

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Resubmitted SAQ review process
- **SRD:** Section 6.3.4.1.3 "Reviewing the SAQ", Pages 241-243

**Dependencies:**
- US-SAQ-024

**Priority:** Must Have

---

### US-SAQ-026: Approve SAQ and Proceed to Next Phase

**As a** Validation Team Lead  
**I want to** approve the SAQ when all responses are acceptable  
**So that** the validation process can proceed to initial risk assessment phase

**Acceptance Criteria:**
1. Validation Team Lead reviews all SAQ responses
2. All questions are classified as "Accepted" (no "Not Accepted" responses remain)
3. Validation Team Lead clicks "Approve" button `[SRD Section 6.3.4.1.3]`
4. System changes status to "SAQ Approved" `[SRD Section 6.3.4.1.4]`
5. System automatically sends notification to assigned Validation Team instructing them to initiate initial risk assessment process and prepare assessment plan `[SRD Section 6.3.4.1.3, 6.3.4.2]`
6. System sends notification to Commercial Establishment Account Manager and SAQ Editors `[SRD Section 6.2.4.7]`
7. Notification sent via email and respective portals `[SRD Section 6.2.4.7, 6.3.4.1.5]`
8. SAQ becomes locked and cannot be modified
9. System displays corresponding SAQ for initial risk assessment with sections, subsections, leaf sections, and related questions/answers `[SRD Section 6.3.4.2]`
10. System enables Validation Team to proceed with:
    - Initial risk assessment
    - Assessment plan preparation
    - Further validation activities

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ approval and transition to next phase
- **SRD:** Section 6.3.4.1.3 "Reviewing the SAQ", Section 6.3.4.1.4 "Statuses of Self-Assessment Questionnaire", Section 6.3.4.2 "Initial Risk Assessment and Assessment Plan Preparation", Section 6.2.4.7 "Notifications", Section 6.3.4.1.5 "Notifications", Pages 191-192, 241-247

**Dependencies:**
- US-SAQ-022 or US-SAQ-025

**Priority:** Must Have

---

<a name="saq-workflow-management"></a>
## 7. All Portals - SAQ Workflow Management

### Epic: SAQ Lifecycle and Workflow Controls
Enable users across all portals to manage SAQ lifecycle events, notifications, and status transitions.

---

### US-SAQ-027: Receive SAQ Notifications

**As a** user in any portal (Federal, Local Customs, or AEO)  
**I want to** receive timely notifications about SAQ events relevant to my role  
**So that** I can take appropriate actions on time

**Acceptance Criteria:**
1. System sends notifications for following events:

   **Federal Customs Portal:**
   - Question Bank Under Review (to Senior Federal Administrator) `[SRD Section 6.4.10.4]`
   - Question Bank Approved (to Federal Administrator) `[SRD Section 6.4.10.4]`
   - Question Bank Returned (to Federal Administrator) `[SRD Section 6.4.10.4]`
   - Question Bank Rejected (to Senior Federal Admin and Federal Admin) `[SRD Section 6.4.10.4]`
   - SAQ Template Under Review (to Senior Federal Administrator) `[SRD Section 6.4.10.9]`
   - SAQ Template Approved (to Federal Administrator) `[SRD Section 6.4.10.9]`
   - SAQ Template Returned (to Federal Administrator) `[SRD Section 6.4.10.9]`
   - SAQ Template Rejected (to Federal Administrator) `[SRD Section 6.4.10.9]`

   **Local Customs Portal:**
   - Validation Team Assigned (to Validation Team) `[SRD Section 6.3.4.1.5]`
   - Start of SAQ Review (to Validation Team) `[SRD Section 6.3.4.1.5]`
   - Review of Resubmitted SAQ (to Validation Team) `[SRD Section 6.3.4.1.5]`
   - Expiration of SAQ (to Validation Team) `[SRD Section 6.3.4.1.5]`

   **AEO Portal:**
   - Sharing the SAQ (to Commercial Establishment Account Manager and SAQ Editors) `[SRD Section 6.2.4.7]`
   - Confirmation of SAQ Submission (to Commercial Establishment Account Manager and SAQ Editors) `[SRD Section 6.2.4.7]`
   - SAQ Returned (to Commercial Establishment Account Manager and SAQ Editors) `[SRD Section 6.2.4.7]`
   - SAQ Under Review (to Commercial Establishment Account Manager and SAQ Editors) `[SRD Section 6.2.4.7]`
   - SAQ Approved (to Commercial Establishment Account Manager and SAQ Editors) `[SRD Section 6.2.4.7]`
   - Cancellation of SAQ (to Commercial Establishment Account Manager and SAQ Editors) `[SRD Section 6.2.4.7]`
   - Expiration of SAQ (to Commercial Establishment Account Manager and SAQ Editors) `[SRD Section 6.2.4.7]`

2. Each notification includes:
   - Event description
   - SAQ/Question Bank reference number
   - Action required (if any)
   - Link to relevant portal page
   - Timestamp

3. Notifications are sent via:
   - Email
   - In-portal notification center

4. Users can view notification history
5. System marks notifications as read/unread
6. Users can configure notification preferences (if applicable)

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Comprehensive notification system for SAQ lifecycle
- **SRD:** Section 6.2.4.7 "Notifications", Section 6.3.4.1.5 "Notifications", Section 6.4.10.4 "Notifications", Section 6.4.10.9 "Notifications", Pages 191-192, 245-246, 323, 330

**Dependencies:**
- All previous SAQ user stories

**Priority:** Must Have

---

### US-SAQ-028: Mark SAQ as Expired

**As a** Validation Team Lead  
**I want to** manually mark an SAQ as expired when the commercial establishment exceeds the configured SLA  
**So that** the authorization request can be properly concluded

**Acceptance Criteria:**
1. System tracks time elapsed since SAQ was shared with commercial establishment
2. System monitors configured SLA for SAQ submission (15 business days) `[BR.16]`
3. When commercial establishment exceeds SLA for SAQ submission:
   - System notifies Validation Team Lead
   - System displays option to mark SAQ as "Expired"
4. Validation Team Lead clicks "Mark as Expired" button `[SRD Section 6.2.4.6, 6.3.4.1.3]`
5. System confirms action with Validation Team Lead
6. Upon confirmation:
   - System changes status to "SAQ Expired" (final status) `[SRD Section 6.2.4.6, 6.3.4.1.4]`
   - System sends notification to Commercial Establishment Account Manager and SAQ Editors `[SRD Section 6.2.4.7]`
   - System sends notification to Validation Team `[SRD Section 6.3.4.1.5]`
7. SAQ becomes locked and cannot be submitted
8. Commercial establishment can no longer access SAQ for editing
9. System records expiration in audit trail with timestamp and responsible user

**Business Rules:**
- BR.16: The commercial establishment must complete the self-assessment questionnaire within 15 business days from the date it was sent by the relevant customs administration `[SRD Section 6.2.4.1]`

**Traceability:**
- **BRD:** SAQ expiration management
- **SRD:** Section 6.2.4.6 "Statuses of Self-Assessment Questionnaire", Section 6.3.4.1.3 "Reviewing the SAQ", Section 6.3.4.1.4 "Statuses of Self-Assessment Questionnaire", Section 6.2.4.7 "Notifications", Section 6.3.4.1.5 "Notifications", Pages 189-192, 241-246

**Dependencies:**
- US-SAQ-014

**Priority:** Must Have

---

### US-SAQ-029: Handle SAQ Cancellation Due to Authorization Request Cancellation

**As a** system administrator  
**I want to** automatically cancel the SAQ when the AEO Authorization Request is cancelled  
**So that** the SAQ lifecycle is properly terminated

**Acceptance Criteria:**
1. System monitors status of associated AEO Authorization Request
2. When commercial establishment cancels AEO Authorization Request during SAQ review (before SAQ acceptance):
   - System automatically changes SAQ status to "SAQ Cancelled" (final status) `[SRD Section 6.2.4.6, 6.3.4.1.4]`
   - Action is automatic (no manual intervention required) `[SRD Section 6.2.4.6]`
3. System sends notification to:
   - Commercial Establishment Account Manager and SAQ Editors `[SRD Section 6.2.4.7]`
   - Validation Team (if assigned)
4. Notifications sent via email and respective portals
5. SAQ becomes locked and inaccessible for editing
6. System records cancellation in audit trail with timestamp and reason
7. Cancellation is recorded as: "The SAQ has been cancelled due to the cancellation of the authorization request by the establishment during the review process of the SAQ" `[SRD Section 6.2.4.6]`

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** SAQ automatic cancellation workflow
- **SRD:** Section 6.2.4.6 "Statuses of Self-Assessment Questionnaire", Section 6.3.4.1.4 "Statuses of Self-Assessment Questionnaire", Section 6.2.4.7 "Notifications", Pages 189-192, 244-245

**Dependencies:**
- Phase 1 user stories (AEO Authorization Request cancellation)
- US-SAQ-014

**Priority:** Must Have

---

### US-SAQ-030: View SAQ Audit Trail and History

**As a** user with appropriate permissions in any portal  
**I want to** view complete SAQ audit trail and history  
**So that** I can track all changes, status transitions, and actions taken

**Acceptance Criteria:**
1. System maintains comprehensive audit trail for each SAQ including:
   - All status changes with timestamps
   - User actions (create, modify, submit, approve, return, reject, expire, cancel)
   - User who performed each action
   - Comments and remarks added
   - Answers modified
   - Section assignments
   - Notifications sent
2. Users can access audit trail from SAQ detail page
3. System displays audit trail in chronological order (newest first or oldest first based on user preference)
4. Each audit entry shows:
   - Date and time
   - User name and role
   - Action performed
   - Previous and new values (for modifications)
   - Comments/remarks (if applicable)
5. System allows filtering audit trail by:
   - Date range
   - User
   - Action type
   - Status
6. System allows exporting audit trail for reporting purposes
7. Audit trail is read-only and cannot be modified

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Comprehensive audit and traceability requirements
- **SRD:** Multiple sections reference audit trail recording - Section 6.2.4.5, 6.2.4.6, 6.3.4.1.4, 6.4.10.3, 6.4.10.8

**Dependencies:**
- All previous SAQ user stories

**Priority:** Must Have

---

### US-SAQ-031: Add Internal Comments for Collaboration

**As a** Commercial Establishment user or Validation Team Member  
**I want to** add internal comments on SAQ sections  
**So that** team members can collaborate effectively during SAQ completion or review

**Acceptance Criteria:**
1. Users can add internal comments on any section in the SAQ
2. For Commercial Establishment:
   - Users assigned to SAQ can add comments on sections not assigned to them `[SRD Section 6.2.4.1]`
   - Section owner can reply to comments `[SRD Section 6.2.4.1]`
   - Comments visible only to commercial establishment users
3. For Validation Team:
   - Team members can add comments on any section including those not assigned to them `[SRD Section 6.3.4.1.3, 6.3.4.2]`
   - System allows users to identify phase in which comments were added (SAQ review, initial risk assessment, on-site validation) `[SRD Section 6.3.4.1.3, 6.3.4.2]`
   - Users can reply to comments `[SRD Section 6.3.4.1.3, 6.3.4.2]`
   - Comments visible only to validation team members
4. Each comment includes:
   - Comment text
   - Author name and role
   - Timestamp
   - Phase/context (for validation team)
5. System displays comments in chronological order
6. Users receive notification when comments are added to their assigned sections
7. System maintains comment history in audit trail

**Business Rules:**
- None specified for this story

**Traceability:**
- **BRD:** Internal collaboration capabilities
- **SRD:** Section 6.2.4.1 "Completing the Self-Assessment Questionnaire", Section 6.3.4.1.3 "Reviewing the SAQ", Section 6.3.4.2 "Initial Risk Assessment and Assessment Plan Preparation", Pages 186-187, 241-247

**Dependencies:**
- US-SAQ-015, US-SAQ-021

**Priority:** Must Have

---

## Summary Tables

### Phase 2 User Stories Summary by Portal

| Portal | Epic | User Stories Count |
|--------|------|-------------------|
| **Federal Customs Portal** | Question Bank Management | 5 (US-SAQ-001 to US-SAQ-005) |
| **Federal Customs Portal** | Risks Bank Management | 3 (US-SAQ-006 to US-SAQ-008) |
| **Federal Customs Portal** | SAQ Template Creation | 3 (US-SAQ-009 to US-SAQ-011) |
| **Local Customs Portal** | SAQ Preparation and Sharing | 3 (US-SAQ-012 to US-SAQ-014) |
| **AEO Portal** | SAQ Completion | 6 (US-SAQ-015 to US-SAQ-020) |
| **Local Customs Portal** | SAQ Review and Approval | 6 (US-SAQ-021 to US-SAQ-026) |
| **All Portals** | SAQ Workflow Management | 5 (US-SAQ-027 to US-SAQ-031) |
| **TOTAL** | **7 Epics** | **31 User Stories** |

---

### Priority Distribution

| Priority | Count | Percentage |
|----------|-------|------------|
| Must Have | 30 | 96.8% |
| Should Have | 1 | 3.2% |
| Could Have | 0 | 0% |
| Won't Have | 0 | 0% |

---

### Business Rules Referenced

| Business Rule | Description | Referenced in User Stories |
|--------------|-------------|---------------------------|
| BR.14 | Multiple users can fill out the self-assessment questionnaire simultaneously (in parallel) | US-SAQ-015, US-SAQ-016 |
| BR.15 | The self-assessment questionnaire does not require sequential completion by section or subsection; users can freely navigate between questions | US-SAQ-016, US-SAQ-017 |
| BR.16 | The commercial establishment must complete the self-assessment questionnaire within 15 business days from the date it was sent by the relevant customs administration | US-SAQ-014, US-SAQ-016, US-SAQ-018, US-SAQ-020, US-SAQ-028 |

---

### Key SAQ Statuses

| Status | Description | Portal |
|--------|-------------|--------|
| Draft | Question Bank/SAQ Template being constructed | Federal |
| Under Review | Pending approval | Federal/Local |
| Published | Approved and available for use | Federal |
| Returned | Sent back for modifications | Federal/All |
| Rejected | Not approved | Federal |
| Validation Team Assigned | Team assigned to prepare SAQ | Local |
| SAQ Generated | SAQ creation in progress | Local |
| SAQ Ready for Sharing | SAQ finalized, ready to share | Local |
| SAQ Shared | SAQ shared with establishment | Local/AEO |
| SAQ Received | SAQ received by customs | AEO/Local |
| SAQ In Progress | Establishment filling SAQ | AEO |
| SAQ Submitted | SAQ submitted for review | AEO/Local |
| SAQ Under Review | Customs reviewing SAQ | Local |
| SAQ Returned | Returned to establishment | Local/AEO |
| SAQ Approved | SAQ accepted, proceed to next phase | Local/AEO |
| SAQ Cancelled | Cancelled due to request cancellation | All |
| SAQ Expired | Exceeded submission deadline | All |

---

### SAQ Workflow Diagram

```
Federal Customs:
Question Bank (Draft → Under Review → Published/Returned/Rejected)
            ↓
SAQ Template (Draft → Under Review → Published/Returned/Rejected)
            ↓
Local Customs:
Validation Team Assigned → SAQ Generated → SAQ Ready for Sharing → SAQ Shared
            ↓
Commercial Establishment:
SAQ Received → SAQ In Progress → SAQ Submitted
            ↓
Local Customs:
SAQ Under Review → SAQ Returned (back to establishment) OR SAQ Approved
            ↓
(If Returned)
Commercial Establishment:
Modify SAQ → SAQ Submitted (back to customs)
            ↓
(If Approved)
Next Phase: Initial Risk Assessment & Assessment Plan
```

---

## Traceability Matrix

### Source Document References

| User Story | BRD Reference | SRD Reference | Page Numbers |
|------------|---------------|---------------|--------------|
| US-SAQ-001 | Questions Bank definition | Section 6.4.10.1, 5.27 | 318-320 |
| US-SAQ-002 | Questions Bank content | Section 6.4.10.1, 5.28 | 133-136, 318-320 |
| US-SAQ-003 | Question Bank modifications | Section 6.4.10.1, 6.4.10.3 | 318-323 |
| US-SAQ-004 | Question Bank deletion | Section 6.4.10.1 | 318-320 |
| US-SAQ-005 | Question Bank approval | Section 6.4.10.2, 6.4.10.3, 6.4.10.4 | 320-323 |
| US-SAQ-006 | Risks Bank groups | Section 6.4.10.5, 5.33 | 139-140, 324-325 |
| US-SAQ-007 | Risks Bank content | Section 6.4.10.5, 5.34 | 140, 324-325 |
| US-SAQ-008 | Risks Bank modifications | Section 6.4.10.5 | 324-325 |
| US-SAQ-009 | SAQ Template creation | Section 4.4.6, 6.4.10.6, 5.30 | 48-49, 136-138, 325-327 |
| US-SAQ-010 | SAQ Template duplication | Section 6.4.10.6 | 326-327 |
| US-SAQ-011 | SAQ Template approval | Section 6.4.10.7, 6.4.10.8, 6.4.10.9 | 327-330 |
| US-SAQ-012 | Validation Team assignment | Section 6.3.4.1.1, 6.3.4.1.4, 6.3.4.1.5 | 239-246 |
| US-SAQ-013 | SAQ generation | Section 4.2.1, 6.3.4.1.2, 5.5 | 37, 69-71, 240-241 |
| US-SAQ-014 | SAQ sharing | Section 6.3.4.1.2, 6.2.4.7 | 240-241, 191-192 |
| US-SAQ-015 | SAQ section assignment | Section 6.2.4.1 | 186-187 |
| US-SAQ-016 | SAQ completion | Section 6.2.4.1, 6.2.4.6 | 186-191 |
| US-SAQ-017 | SAQ draft save | Section 6.2.4.2 | 188 |
| US-SAQ-018 | SAQ status tracking | Section 6.2.4.3, 6.2.4.6 | 188, 189-191 |
| US-SAQ-019 | SAQ filtering | Section 6.2.4.4 | 187-188 |
| US-SAQ-020 | SAQ submission | Section 6.2.4.1, 6.2.4.6, 6.2.4.7 | 186-192 |
| US-SAQ-021 | SAQ review allocation | Section 6.3.4.1.3, 6.3.4.1.5 | 241-246 |
| US-SAQ-022 | SAQ response evaluation | Section 6.3.4.1.3 | 241-243 |
| US-SAQ-023 | SAQ return | Section 6.3.4.1.3, 6.3.4.1.4, 6.2.4.5 | 188-189, 241-245 |
| US-SAQ-024 | SAQ modification after return | Section 6.2.4.5, 6.2.4.6 | 188-191 |
| US-SAQ-025 | Resubmitted SAQ review | Section 6.3.4.1.3 | 241-243 |
| US-SAQ-026 | SAQ approval | Section 6.3.4.1.3, 6.3.4.1.4, 6.3.4.2 | 191-192, 241-247 |
| US-SAQ-027 | SAQ notifications | Section 6.2.4.7, 6.3.4.1.5, 6.4.10.4, 6.4.10.9 | 191-192, 245-246, 323, 330 |
| US-SAQ-028 | SAQ expiration | Section 6.2.4.6, 6.3.4.1.3, 6.3.4.1.4 | 189-192, 241-246 |
| US-SAQ-029 | SAQ cancellation | Section 6.2.4.6, 6.3.4.1.4, 6.2.4.7 | 189-192, 244-245 |
| US-SAQ-030 | SAQ audit trail | Multiple sections | Throughout SRD |
| US-SAQ-031 | Internal comments | Section 6.2.4.1, 6.3.4.1.3, 6.3.4.2 | 186-187, 241-247 |

---

## Next Steps

**Phase 2 is now complete.** The next phase will be:

**Phase 3: Validation & Risk Assessment**
- Estimated 30-35 user stories covering:
  - Initial Risk Assessment
  - Assessment Plan Preparation
  - Validation Meetings
  - On-Site Validation
  - Assessment File Creation
  - Assessment Report Generation

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | November 07, 2025 | AEO Project Team | Initial version - Phase 2 SAQ User Stories |

---

**End of Phase 2 User Stories Document**
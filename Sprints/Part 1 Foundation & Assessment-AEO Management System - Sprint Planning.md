AEO Management System - Sprint Planning
Part 1: Foundation & Assessment (Phases 1-3)
Normal & Aggressive ScenariosDocument Version: 1.0
Date: November 08, 2025
Project: Authorized Economic Operator (AEO) Management System
Source Documents:

Business Requirements Document (BRD) V1.11
System Requirements Document (SRD) V1.2.5
AEO Project Backlog Part 1 (Phases 1-3) V1.0
Phase 1 User Stories Document V1.0
Phase 2 User Stories Document V1.0
Phase 3 User Stories Document V1.0
Document ControlVersionDateAuthorChanges1.0November 08, 2025AEO Project TeamInitial Sprint Planning - Part 1 (Phases 1-3)Executive SummaryPurpose
This document provides comprehensive sprint planning for Part 1 (Foundation & Assessment) of the AEO Management System, covering Phases 1-3 with 94 user stories totaling 687 story points. Two planning scenarios are presented:
Normal Sprint Planning: Single team, standard delivery pace
Aggressive Sprint Planning: Two parallel teams, accelerated delivery
Technology StackComponentTechnologyVersionPurposeFrontendReactJS18.xUser interfaces for all three portalsBackend.NET Core8.0REST API, business logic, servicesDatabaseMS SQL Server2022Data persistence and managementORMEntity Framework Core8.0Database access layerAuthenticationIdentityServer4 / Azure ADLatestOAuth 2.0, JWT tokensAPI DocumentationSwagger/OpenAPI3.0API documentationTestingxUnit, NUnit, JestLatestUnit and integration testingDevOpsAzure DevOps / Jenkins-CI/CD pipelineContainerizationDockerLatestApplication containerizationOrchestrationKubernetes1.28+Container orchestrationScope OverviewPhaseFocus AreaStoriesStory PointsPercentagePhase 1Account Creation & AEO Authorization Request2617525.5%Phase 2Self-Assessment Questionnaire (SAQ)3123534.2%Phase 3Validation & Risk Assessment3727740.3%TOTALFoundation & Assessment94687100%Key Planning ParametersNormal Sprint Planning

Team Size: 6 Developers, 2 QA, 1 BA, 1 DevOps = 10 team members
Sprint Duration: 2 weeks
Sprint Velocity: 35-42 story points (avg: 38 points)
Total Sprints: 19 sprints (including Sprint 0)
Total Duration: 38 weeks (9.5 months)
Go-Live Window: Month 10
Aggressive Sprint Planning

Team Size: 16 Developers (2 teams × 8), 4 QA, 1 BA (shared), 1 DevOps (shared) = 22 team members
Sprint Duration: 2 weeks
Sprint Velocity: 85-95 story points (avg: 90 points)
Maximum Parallel Workstreams: 3 concurrent streams
Total Sprints: 9 sprints (including Sprint 0)
Total Duration: 18 weeks (4.5 months)
Go-Live Window: Month 5
Critical Assumptions

Infrastructure Setup: 2 weeks (Sprint 0) required before development begins
Productive Hours: 30-32 hours per developer per week (accounting for 20-25% overhead for meetings/admin)
Story Point Calculation: 1 story point ≈ 8-10 development hours
Shared Resources: BA and DevOps shared across all teams in aggressive scenario
Full-Stack Developers: All developers capable of ReactJS frontend, .NET Core backend, and MS SQL Server database work
No External Dependencies: Phase 7 integrations (UAE Gateway, Central Bank, etc.) planned separately
.NET Core 8.0: Latest LTS version with full support for enterprise features
MS SQL Server 2022: Enterprise edition with full-text search, JSON support, and advanced analytics
Table of Contents
Planning Methodology
Technology Architecture
Resource Planning
Story Point Estimation
Normal Sprint Planning - Detailed
Aggressive Sprint Planning - Detailed
Sprint Tables - Normal Scenario
Sprint Tables - Aggressive Scenario
Parallel Execution Strategy
Dependency Management
Risk Mitigation
Quality Assurance Strategy
DevOps & CI/CD Strategy
Go-Live Readiness
<a name="planning-methodology"></a>
1. Planning Methodology1.1 Planning ApproachThis sprint planning document follows SAFe (Scaled Agile Framework) principles adapted for government/regulatory systems:
Epic-Based Planning: Stories grouped by epics for logical delivery
Dependency-First Sequencing: Critical path dependencies resolved before parallel work
Risk-Based Prioritization: High-risk/high-value features delivered early
Incremental Integration: Continuous integration within sprints
Test-Driven Development: QA involvement from sprint planning
1.2 Velocity CalculationFormula:
Sprint Velocity = (Number of Developers × Productive Hours per Week × Sprint Weeks) / Hours per Story PointNormal Team:

Velocity = (6 devs × 30 hours × 2 weeks) / 9.5 hours per point = 38 story points/sprint
Aggressive Teams (Combined):

Velocity = (16 devs × 30 hours × 2 weeks) / 9.5 hours per point = 101 story points/sprint
Adjusted for coordination overhead (10%): 90 story points/sprint
1.3 Story Point ScaleComplexityStory PointsDescriptionDev HoursExamplesXS1-2Simple CRUD, minor UI change8-20View list, simple formS3-5Standard feature, single integration24-50User login, profile updateM8Complex business logic, multiple components64-80SAQ completion workflowL13Major feature, multiple integrations104-130Risk assessment engineXL21Epic-level complexity, system-wide impact168-210End-to-end validation flow1.4 Sprint StructureEach sprint follows this standard structure:ActivityDurationParticipantsPurposeSprint Planning4 hoursFull teamSelect and commit to storiesDaily Standup15 min/dayFull teamProgress sync, blocker removalDevelopment8 daysDev, QABuild and test featuresCode ReviewOngoingDev teamQuality assuranceSprint Review2 hoursTeam + StakeholdersDemo completed workSprint Retrospective1.5 hoursFull teamProcess improvementSprint Backlog Refinement2 hoursTeam + POPrepare next sprint<a name="technology-architecture"></a>
2. Technology Architecture2.1 Architecture Overview┌─────────────────────────────────────────────────────────────────┐
│                         Frontend Layer                           │
│  ┌──────────────┐  ┌──────────────┐  ┌─────────────────────┐  │
│  │ AEO Portal   │  │ Fed Customs  │  │  Local Customs      │  │
│  │ (ReactJS)    │  │ Portal       │  │  Portal (ReactJS)   │  │
│  │              │  │ (ReactJS)    │  │                     │  │
│  └──────┬───────┘  └──────┬───────┘  └──────────┬──────────┘  │
└─────────┼──────────────────┼──────────────────────┼─────────────┘
          │                  │                      │
          └──────────────────┼──────────────────────┘
                             │
                    ┌────────▼────────┐
                    │   API Gateway   │
                    │  (NGINX/Azure)  │
                    └────────┬────────┘
                             │
          ┌──────────────────┼──────────────────────┐
          │                  │                      │
┌─────────▼────────┐ ┌───────▼───────┐  ┌─────────▼────────┐
│  Authentication  │ │   Business    │  │   Integration    │
│   Service        │ │   Logic API   │  │   Services       │
│  (.NET Core)     │ │  (.NET Core)  │  │  (.NET Core)     │
└─────────┬────────┘ └───────┬───────┘  └─────────┬────────┘
          │                  │                      │
          └──────────────────┼──────────────────────┘
                             │
                    ┌────────▼────────┐
                    │  Entity         │
                    │  Framework Core │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │  MS SQL Server  │
                    │  Database       │
                    └─────────────────┘2.2 Frontend Architecture (ReactJS)Technology Stack:

Framework: React 18.x with Hooks
State Management: Redux Toolkit / Zustand
Routing: React Router v6
UI Components: Material-UI (MUI) v5 or Ant Design
Forms: React Hook Form + Yup validation
API Client: Axios with interceptors
Internationalization: react-i18next (Arabic/English)
Testing: Jest + React Testing Library
Portal Structure:
src/
├── portals/
│   ├── aeo/                    # AEO Portal
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── store/
│   ├── federal/                # Federal Customs Portal
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── store/
│   └── local/                  # Local Customs Portal
│       ├── components/
│       ├── pages/
│       ├── services/
│       └── store/
├── shared/                     # Shared components
│   ├── components/
│   ├── utils/
│   └── hooks/
└── App.jsx2.3 Backend Architecture (.NET Core)Technology Stack:

Framework: .NET Core 8.0 (LTS)
API: ASP.NET Core Web API
ORM: Entity Framework Core 8.0
Authentication: IdentityServer4 / Microsoft.Identity
Validation: FluentValidation
Logging: Serilog
Caching: Redis / IMemoryCache
Background Jobs: Hangfire
Testing: xUnit + Moq
Solution Structure:
AEO.Solution/
├── src/
│   ├── AEO.API/                # Main API Project
│   │   ├── Controllers/
│   │   ├── Middleware/
│   │   └── Program.cs
│   ├── AEO.Core/               # Domain Models & Interfaces
│   │   ├── Entities/
│   │   ├── Interfaces/
│   │   └── DTOs/
│   ├── AEO.Infrastructure/     # Data Access & External Services
│   │   ├── Data/
│   │   │   ├── ApplicationDbContext.cs
│   │   │   └── Repositories/
│   │   ├── Services/
│   │   └── Migrations/
│   ├── AEO.Application/        # Business Logic
│   │   ├── Services/
│   │   ├── Validators/
│   │   └── Mappings/
│   └── AEO.Shared/             # Shared Utilities
│       ├── Constants/
│       ├── Helpers/
│       └── Extensions/
├── tests/
│   ├── AEO.UnitTests/
│   └── AEO.IntegrationTests/
└── AEO.Solution.sln2.4 Database Architecture (MS SQL Server)Database Configuration:

Edition: SQL Server 2022 Enterprise
Collation: Arabic_CI_AS (Case-Insensitive, Accent-Sensitive)
Recovery Model: Full
Compatibility Level: 160 (SQL Server 2022)
Key Features Utilized:

Full-Text Search: For Question Bank and SAQ content search
JSON Support: For storing flexible metadata and audit logs
Temporal Tables: For audit trail and versioning
Row-Level Security: For data isolation between customs departments
Always Encrypted: For sensitive establishment data
Database Schema Structure:
sql-- Core Schemas
dbo.                    -- Default schema
accounts.               -- Account management tables
authorization.          -- Authorization request tables
saq.                    -- Self-Assessment Questionnaire tables
validation.             -- Validation and assessment tables
admin.                  -- System administration tables
audit.                  -- Audit trail tablesSample Core Tables:
sql-- Account Management
accounts.CommercialEstablishment
accounts.EstablishmentUser
accounts.AccountCreationRequest

-- Authorization Requests
authorization.AEOAuthorizationRequest
authorization.RequestDocument
authorization.RequestStatus

-- SAQ Management
saq.QuestionBank
saq.QuestionBankVersion
saq.RisksBank
saq.SAQTemplate
saq.SAQInstance
saq.SAQResponse

-- Validation & Assessment
validation.RiskAssessment
validation.AssessmentPlan
validation.ValidationMeeting
validation.AssessmentFile
validation.AssessmentReport
validation.ControlPlan

-- Administration
admin.FederalUser
admin.LocalCustomsUser
admin.SystemConfiguration
admin.NotificationTemplate

-- Audit Trail
audit.AuditLog (Temporal Table)
audit.ChangeHistory2.5 Integration PointsIntegrationTechnologyPurposeUAE PASSOAuth 2.0, REST APIAuthentication and user dataEmail ServiceSMTP / SendGridNotifications and alertsSMS GatewayREST APICritical notificationsDocument StorageAzure Blob Storage / File SystemDocument managementReportingCrystal Reports / SSRSReport generation<a name="resource-planning"></a>
3. Resource Planning3.1 Normal Sprint Planning - Team StructureRoleCountResponsibilitiesAllocationSkills RequiredFull-Stack Developers6ReactJS frontend, .NET Core backend, MS SQL database100%React, .NET Core, SQL Server, Entity FrameworkQA Engineers2Test planning, automation (Selenium + xUnit), manual testing100%Selenium, xUnit, API testingBusiness Analyst1Requirements clarification, acceptance criteria validation100%BRD/SRD analysis, UATDevOps Engineer1Azure DevOps, Docker, Kubernetes, SQL Server DBA tasks100%CI/CD, Containers, SQL AdminProduct Owner1 (Part-time)Backlog prioritization, stakeholder liaison25%Agile, Domain knowledgeScrum Master1 (Part-time)Facilitation, impediment removal25%Agile ceremoniesTotal FTE: 10 full-time + 2 part-time = 10.5 FTE3.2 Aggressive Sprint Planning - Team StructureTeam Alpha (Frontend-Focused - 8 members)
RoleCountPrimary FocusSkillsFrontend Developers5ReactJS development for all 3 portalsReact, Redux, MUI/Ant Design, i18nFull-Stack Developers3Backend support + complex integrationsReact + .NET Core + SQL ServerQA Engineers2Frontend testing, E2E testingSelenium, Jest, React Testing LibraryTeam Bravo (Backend-Focused - 8 members)
RoleCountPrimary FocusSkillsBackend Developers5.NET Core APIs, business logic.NET Core, Entity Framework, LINQFull-Stack Developers3Database design + frontend support.NET Core + SQL Server + ReactQA Engineers2API testing, integration testingxUnit, Postman, SQL testingShared Resources
RoleCountResponsibilitiesAllocationBusiness Analyst1Support both teams, requirements clarification100% (split 50/50)DevOps Engineer1CI/CD for all teams, SQL Server administration100%Database Administrator1 (Part-time)SQL Server optimization, backup/recovery50%Product Owner1 (Part-time)Backlog management for both teams40%Scrum Master1 (Part-time)Facilitate both teams40%Total FTE: 22 full-time + 3 part-time = 23.3 FTE3.3 Skills Matrix RequiredSkillRequired LevelNormal TeamAggressive TeamCritical?ReactJSAdvanced6 developers11 developersYes.NET Core 8.0Advanced6 developers11 developersYesMS SQL Server 2022Intermediate6 developers11 developersYesEntity Framework CoreAdvanced6 developers11 developersYesREST API DesignAdvanced6 developers8 developersYesT-SQL & Stored ProceduresIntermediate4 developers8 developersYesReact Hooks & ReduxAdvanced6 developers11 developersYesxUnit TestingAdvanced2 QA4 QAYesSelenium WebDriverAdvanced2 QA4 QAYesAzure DevOpsAdvanced1 DevOps1 DevOpsYesDocker & KubernetesAdvanced1 DevOps1 DevOpsYesArabic LanguageIntermediate2+ developers4+ developersYesGovernment SystemsIntermediate2+ members4+ membersPreferred3.4 Ramp-Up PlanNormal Team:

Sprint 0 (2 weeks): Infrastructure setup, team onboarding, .NET Core + React training
Sprint 1-2: Team velocity stabilization (25-30 points)
Sprint 3+: Full velocity (38-42 points)
Aggressive Teams:

Sprint 0 (2 weeks): Infrastructure setup, team formation, role assignment, SQL Server setup
Sprint 1: Team velocity stabilization (70-75 points total)
Sprint 2+: Full velocity (85-95 points total)
<a name="story-point-estimation"></a>
4. Story Point Estimation4.1 Phase 1 Story Point Breakdown (175 points total)Epic 1.1: AEO Program Information Access (1 story - 8 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-AEO-001View AEO program informationMedium8React CMS page, .NET Core API, SQL Server content tablesTechnical Scope:

ReactJS: Public content display component, multilingual support (Arabic/English)
.NET Core: Content management API endpoints
SQL Server: Content tables with versioning
Epic 1.2: Commercial Establishment Account Creation (4 stories - 27 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-AEO-002Register via UAE PASSLarge13OAuth 2.0 integration, JWT handling, user provisioningUS-AEO-003Register manuallyMedium8Complex React form, .NET validation, SQL stored proceduresUS-AEO-004Track registration requestSmall3React dashboard, .NET API, SQL viewsUS-AEO-005Receive registration notificationsSmall3.NET background service, email templates, SQL triggersTechnical Scope:

US-AEO-002: OAuth 2.0 client (.NET), UAE PASS API integration, token management, IdentityServer4 setup
US-AEO-003: React Hook Form validation, .NET FluentValidation, Entity Framework models
US-AEO-004: React status timeline component, SignalR for real-time updates
US-AEO-005: Hangfire background jobs, SMTP integration, SQL Server Service Broker
Epic 1.3: AEO Portal Authentication & Security (4 stories - 18 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-AEO-006Login with UAE PASSMedium8OAuth redirect flow, JWT storage, React auth contextUS-AEO-007Login with username/passwordSmall5ASP.NET Identity, password hashing, React login formUS-AEO-008Reset passwordSmall3Email token generation, .NET password reset APIUS-AEO-009Change passwordXS2React form, .NET password validationTechnical Scope:

US-AEO-006: React OAuth callback handling, .NET OAuth middleware
US-AEO-007: ASP.NET Core Identity configuration, JWT generation
US-AEO-008: Token-based password reset, email service integration
US-AEO-009: React password strength validator
Epic 1.4: AEO Authorization Request Submission (6 stories - 37 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-AEO-010Submit AEO authorization requestLarge13Multi-step React form wizard, .NET validation pipeline, SQL complex schemaUS-AEO-011Save request as draftSmall5React auto-save, .NET draft API, SQL draft tablesUS-AEO-012Track request statusSmall5React timeline component, .NET status APIUS-AEO-013Withdraw submitted requestSmall3React confirmation dialog, .NET workflow APIUS-AEO-014Complete and resubmit returned requestMedium8React form pre-population, .NET change tracking, SQL historyUS-AEO-015Receive request status notificationsSmall3.NET notification service, SQL triggersTechnical Scope:

US-AEO-010: Complex multi-section form (React Hook Form), file upload (Azure Blob), validation rules engine (.NET)
US-AEO-011: Local storage + API sync, optimistic updates
US-AEO-012: SignalR real-time status updates, React timeline UI
US-AEO-014: Entity Framework change tracking, SQL temporal tables
Epic 1.5: Commercial Establishment User Management (3 stories - 16 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-AEO-016Add users to accountMedium8React user form, .NET role management API, SQL user tablesUS-AEO-017View and update profileSmall3React profile page, .NET CRUD APIUS-AEO-018View audit trailSmall5React audit log viewer, .NET audit API, SQL temporal tablesTechnical Scope:

US-AEO-016: ASP.NET Identity user management, role-based access control (RBAC)
US-AEO-018: SQL Server temporal tables for audit history, .NET audit query API
Epic 1.6: Local Customs - Account Creation Review (3 stories - 19 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-LC-001Review account creation requestMedium8React review interface, .NET review API, SQL review workflowUS-LC-002View account request status historySmall3React history component, SQL history viewsUS-LC-003Approve/reject account requestMedium8React decision form, .NET workflow engine, SQL state machineTechnical Scope:

US-LC-001: React data table with filters, .NET query optimization (EF Core)
US-LC-003: Workflow state machine (.NET), business rules engine, SQL stored procedures for status transitions
Epic 1.7: Local Customs - AEO Authorization Request Review (4 stories - 29 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-LC-004Review AEO authorization requestLarge13Complex React review UI, .NET document viewer API, SQL complex queriesUS-LC-005Cancel request at any stageSmall5React confirmation, .NET cancellation workflowUS-LC-006Approve/return requestMedium8React decision form with remarks, .NET workflow, SQL transactionsUS-LC-007Receive request notificationsSmall3.NET notification hub, SignalRTechnical Scope:

US-LC-004: PDF viewer integration (React), complex EF Core queries with includes/projections
US-LC-006: Business rules validation (.NET), transactional workflows (Entity Framework)
Epic 1.8: Local Customs User Profile (1 story - 5 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-LC-008Manage user profile and preferencesSmall5React profile page, .NET user API, SQL user preferences4.2 Phase 2 Story Point Breakdown (235 points total)Epic 2.1: Question Bank Management (5 stories - 39 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-SAQ-001Create Question Bank groupsMedium8React tree component, .NET hierarchical API, SQL hierarchyidUS-SAQ-002Create questions with metadataLarge13Complex React form, .NET question engine, SQL full-text searchUS-SAQ-003Modify/delete Question BankMedium8React CRUD UI, .NET versioning API, SQL version tablesUS-SAQ-004Search and filter questionsSmall5React search UI, .NET search API, SQL full-text indexesUS-SAQ-005View question version historySmall5React version viewer, .NET history API, SQL temporal tablesTechnical Scope:

US-SAQ-001: SQL Server hierarchyid for tree structures, recursive CTEs
US-SAQ-002: Multi-language support (i18next), conditional question logic (.NET)
US-SAQ-003: Entity Framework soft delete + versioning
US-SAQ-004: SQL Server full-text search, .NET LINQ dynamic queries
Epic 2.2: Risks Bank Management (3 stories - 24 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-SAQ-006Create Risks Bank groupsMedium8React tree UI, .NET risk API, SQL hierarchical tablesUS-SAQ-007Create risks with metadataMedium8React risk form, .NET risk engineUS-SAQ-008Modify/delete Risks BankMedium8React CRUD, .NET versioning, SQL soft deleteEpic 2.3: SAQ Template Creation (3 stories - 37 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-SAQ-009Create SAQ template from scratchX-Large21Complex React drag-drop builder, .NET template engine, SQL JSON storageUS-SAQ-010Duplicate existing templateMedium8React duplication UI, .NET deep copy logic, SQL version controlUS-SAQ-011Review and approve templateMedium8React approval workflow, .NET state machineTechnical Scope:

US-SAQ-009: React Beautiful DnD or similar, drag-and-drop section/question builder
US-SAQ-009: SQL Server JSON columns for flexible template structure
US-SAQ-009: .NET template rendering engine with conditional logic
Epic 2.4: SAQ Preparation and Sharing (3 stories - 26 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-SAQ-012Assign Validation TeamSmall5React team selector, .NET assignment APIUS-SAQ-013Generate SAQ from templateLarge13.NET SAQ generation engine, SQL instance tablesUS-SAQ-014Share SAQ with establishmentMedium8React share UI, .NET sharing workflow, notificationsTechnical Scope:

US-SAQ-013: Template-to-instance transformation engine (.NET), SQL bulk insert optimizations
Epic 2.5: SAQ Completion (6 stories - 42 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-SAQ-015View shared SAQMedium8React SAQ viewer, .NET SAQ APIUS-SAQ-016Complete SAQ collaborativelyLarge13React collaborative editor, SignalR real-time, SQL conflict resolutionUS-SAQ-017Upload supporting documentsSmall5React file upload, Azure Blob Storage integrationUS-SAQ-018View SAQ completion progressSmall5React progress dashboard, .NET progress calculatorUS-SAQ-019Submit completed SAQMedium8React submission, .NET validation pipeline, SQL transactionsUS-SAQ-020Receive SAQ status notificationsSmall3.NET notification serviceTechnical Scope:

US-SAQ-016: SignalR for real-time collaboration, optimistic concurrency control (Entity Framework)
US-SAQ-016: Conflict resolution strategy (last-write-wins or custom)
Epic 2.6: SAQ Review and Approval (6 stories - 50 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-SAQ-021Review submitted SAQLarge13React review interface, .NET review API, SQL aggregationsUS-SAQ-022Mark responses as accepted/not acceptedMedium8React marking UI, .NET marking APIUS-SAQ-023Add remarks to responsesSmall5React comments component, .NET comments APIUS-SAQ-024Return SAQ for modificationsMedium8React return workflow, .NET state transitionsUS-SAQ-025Review resubmitted SAQMedium8React diff viewer, .NET change trackingUS-SAQ-026Approve SAQMedium8React approval form, .NET approval workflowTechnical Scope:

US-SAQ-025: Change tracking visualization (React), SQL temporal tables for history comparison
Epic 2.7: SAQ Workflow Management (5 stories - 17 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-SAQ-027Receive SAQ notificationsSmall3.NET notification hub, email templatesUS-SAQ-028Track SAQ statusSmall3React status tracker, .NET status APIUS-SAQ-029Cancel SAQSmall3React cancellation, .NET workflowUS-SAQ-030Handle SAQ expirationSmall5.NET Hangfire scheduled jobs, SQL expiration logicUS-SAQ-031Add internal commentsSmall3React internal notes, .NET comments API4.3 Phase 3 Story Point Breakdown (277 points total)Epic 3.1: Initial Risk Assessment (6 stories - 68 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-VAL-001Conduct preliminary risk assessmentX-Large21Complex React assessment UI, .NET risk scoring engine, SQL stored proceduresUS-VAL-002Add findings to risk assessmentMedium8React findings form, .NET findings APIUS-VAL-003Generate risk scoresLarge13.NET scoring algorithms, SQL aggregate functionsUS-VAL-004Recommend validation approachMedium8.NET recommendation engine, business rulesUS-VAL-005Create assessment planLarge13React plan builder, .NET plan API, SQL plan tablesUS-VAL-006Approve assessment planSmall5React approval, .NET workflowTechnical Scope:

US-VAL-001: Complex risk scoring algorithms (.NET), weighted calculations, SQL aggregations
US-VAL-003: .NET business rules engine, configurable scoring matrix
Epic 3.2: Validation Meetings Management (5 stories - 29 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-VAL-007Schedule validation meetingsMedium8React calendar component, .NET scheduling API, SQL calendar tablesUS-VAL-008Send meeting invitationsSmall5.NET email service, iCalendar formatUS-VAL-009Record meeting minutesMedium8React rich text editor, .NET document APIUS-VAL-010Cancel/reschedule meetingsSmall5React meeting management, .NET calendar APIUS-VAL-011Track meeting attendanceSmall3React attendance tracker, SQL attendance tablesTechnical Scope:

US-VAL-007: Integration with calendar systems (iCal format)
US-VAL-009: Rich text editor (React Quill or similar), document storage
Epic 3.3: Meeting Coordination (2 stories - 8 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-VAL-012View scheduled meetings (AEO Portal)Small5React calendar view, .NET calendar APIUS-VAL-013Confirm meeting attendanceSmall3React confirmation, .NET attendance APIEpic 3.4: On-Site Validation and Assessment File (7 stories - 60 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-VAL-014Conduct on-site validationLarge13React validation checklist, .NET validation API, mobile-responsiveUS-VAL-015Document validation findingsMedium8React findings form, .NET document APIUS-VAL-016Use assessment toolsMedium8React assessment tools, .NET tools API, SQL tool templatesUS-VAL-017Create comprehensive assessment fileLarge13.NET file aggregation engine, SQL file assemblyUS-VAL-018Review assessment file (Team Lead)Medium8React review UI, .NET review APIUS-VAL-019Return assessment file for revisionSmall5React return workflow, .NET workflow engineUS-VAL-020Approve assessment fileSmall5React approval, .NET approval workflowTechnical Scope:

US-VAL-014: Offline-capable PWA features for on-site validation
US-VAL-017: Document aggregation from multiple sources, PDF generation
Epic 3.5: Assessment Report Generation (4 stories - 34 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-VAL-021Generate assessment reportLarge13.NET report generation engine (SSRS/Crystal), SQL report queriesUS-VAL-022Include mandatory contentMedium8.NET template engine, SQL data aggregationUS-VAL-023Select content to shareMedium8React content selector, .NET filtering APIUS-VAL-024Share report with establishmentSmall5React share UI, .NET sharing workflowTechnical Scope:

US-VAL-021: SQL Server Reporting Services (SSRS) or Crystal Reports integration
US-VAL-021: PDF generation with complex layouts and charts
Epic 3.6: Assessment Report Review and Response (6 stories - 37 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-VAL-025Review assessment reportMedium8React PDF viewer, .NET report APIUS-VAL-026Add comments to reportSmall5React comments UI, .NET comments APIUS-VAL-027Upload compliance improvement planMedium8React file upload, Azure Blob Storage, .NET validationUS-VAL-028Approve assessment reportSmall5React approval, .NET workflowUS-VAL-029Request extension for planSmall3React extension form, .NET extension APIUS-VAL-030Confirm plan implementationMedium8React confirmation, .NET verification APIEpic 3.7: Final Decision and Control Plan (7 stories - 58 points)
Story IDStory TitleComplexityPointsTechnical ComponentsUS-VAL-031Review returned/amended reportMedium8React review UI, .NET review APIUS-VAL-032Review compliance improvement planMedium8React plan viewer, .NET plan APIUS-VAL-033Verify plan implementationMedium8React verification form, .NET verification APIUS-VAL-034Submit final AEO recommendationMedium8React recommendation form, .NET recommendation APIUS-VAL-035Make final AEO decisionMedium8React decision form, .NET decision workflow, SQL decision tablesUS-VAL-036Develop control planLarge13React control plan builder, .NET plan engine, SQL plan templatesUS-VAL-037Approve control planSmall5React approval, .NET approval workflowTechnical Scope:

US-VAL-035: Business rules engine for decision logic, audit trail for decisions
US-VAL-036: Template-based control plan generator with customizable actions
4.4 Summary: Total Story Points by ComplexityComplexityStory CountAvg PointsTotal PointsPercentageXS (1-2)4281.2%S (3-5)42416824.5%M (8)36828841.9%L (13)101313018.9%XL (21)221426.1%Infra/Testing--517.4%TOTAL947.3687100%Technology Distribution:

ReactJS Work: ~40% (275 points) - Frontend components, forms, dashboards
.NET Core Work: ~35% (240 points) - APIs, business logic, workflows
MS SQL Server Work: ~15% (103 points) - Database design, stored procedures, optimization
Integration Work: ~10% (69 points) - UAE PASS, email, file storage
<a name="normal-sprint-planning"></a>
5. Normal Sprint Planning - Detailed5.1 Planning OverviewTeam Configuration: Single team of 10 members
Total Sprints: 19 sprints (including Sprint 0)
Total Duration: 38 weeks (9.5 months)
Sprint Velocity: 35-42 story points (average 38 points)
Working Hours per Sprint: 6 devs × 30 hours × 2 weeks = 360 developer-hours5.2 Sprint 0: Infrastructure & Environment Setup (2 weeks)Objectives:

Provision infrastructure and development environments
Setup CI/CD pipeline
Configure MS SQL Server databases
Establish development standards
Team onboarding and training
Activities:ActivityOwnerDurationDeliverableAzure/On-Prem infrastructure provisioningDevOps3 daysDev, Test, UAT, Prod environmentsMS SQL Server 2022 setup and configurationDevOps/DBA2 daysDatabase instances, backup/recovery.NET Core 8.0 solution structure setupLead Dev2 daysSolution template, project structureReactJS application scaffoldingFrontend Lead2 daysReact apps for 3 portalsAzure DevOps / Jenkins CI/CD pipelineDevOps3 daysBuild and deployment automationEntity Framework Core migrations setupBackend Dev1 dayMigration framework configuredCode quality tools (SonarQube, ESLint)DevOps1 dayCode quality gatesDocumentation templatesBA2 daysTechnical docs, user stories templatesTeam training (.NET Core 8, React 18, SQL 2022)All3 daysTeam skill ramp-upDeliverables:

✅ Development environment ready with .NET Core 8.0
✅ MS SQL Server 2022 databases created (Dev, Test)
✅ ReactJS applications scaffolded for all 3 portals
✅ CI/CD pipeline configured in Azure DevOps
✅ Git repository structure established with branching strategy
✅ Coding standards and guidelines documented
✅ Team access provisioned to all tools and systems
✅ Initial Entity Framework Core models and DbContext created
Success Criteria:

Dev environment fully operational for Sprint 1
All team members can build and run applications locally
CI/CD pipeline can build and deploy to Test environment
Database schema foundations in place
5.3 Phase 1 - Sprints 1-9 (Account Creation & Authorization Request)Sprint 1: Foundation & Public Portal (Week 3-4) - 38 pointsGoal: Establish AEO Portal foundation with public information access and basic authenticationTeam Focus:

Frontend: 3 devs on React components and routing
Backend: 3 devs on .NET Core API foundation and authentication
QA: Test automation framework setup
DevOps: Deployment pipeline refinement
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-AEO-001View AEO program information8Dev 1-2React CMS page, .NET Content API, SQL content tablesUS-AEO-007Login with username/password5Dev 3-4ASP.NET Identity, JWT tokens, React login formUS-AEO-009Change password2Dev 4React password form, .NET password APIUS-AEO-017View and update user profile3Dev 5React profile page, .NET profile APIUS-LC-008Manage LC user profile5Dev 5-6Local Customs portal profileInfrastructurePortal frameworks & auth module15AllReact routing, .NET middleware, SQL identity tablesSprint Total: 38 pointsKey Technical Activities:

ReactJS Setup:

Configure React Router v6 for all 3 portals
Setup Redux Toolkit store structure
Implement Material-UI (MUI) theme (Arabic RTL support)
Create shared components library



.NET Core Setup:

Configure ASP.NET Core Web API projects
Setup Entity Framework Core DbContext
Implement JWT authentication middleware
Configure ASP.NET Identity



MS SQL Server:

Create database schema for accounts
Setup AspNetUsers, AspNetRoles tables
Create content management tables
Configure full-text search catalog



Testing:

Setup xUnit test projects
Configure Jest for React testing
Create first integration tests


Definition of Done:

✅ Public can view AEO program information (Arabic/English)
✅ Users can login with username/password
✅ JWT tokens generated and validated
✅ Basic profile management functional
✅ All features tested (unit + integration)
✅ Code deployed to Test environment
✅ Code coverage > 70%
Sprint Deliverables:

Functional AEO Portal public pages
Working authentication system
Local Customs portal foundation
Test automation framework operational
Sprint 2: UAE PASS Integration & Account Creation (Week 5-6) - 40 pointsGoal: Enable commercial establishments to register accounts via UAE PASS and manual processTeam Focus:

Frontend: 4 devs on registration forms and OAuth flows
Backend: 2 devs on UAE PASS integration and registration workflow
QA: OAuth testing, form validation testing
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-AEO-002Register via UAE PASS13Dev 1-2-3OAuth 2.0 client, UAE PASS API, token managementUS-AEO-003Register manually8Dev 4-5Complex React form, .NET validation, SQL stored procsUS-AEO-004Track registration request3Dev 6React status dashboard, .NET APIUS-AEO-005Receive registration notifications3Dev 6Hangfire jobs, SMTP integrationUS-AEO-006Login with UAE PASS8Dev 1-2OAuth login flow, JWT generationUS-AEO-008Reset password3Dev 3Email token, password reset APIUS-AEO-016Add users to account (partial)2Dev 4Foundation for next sprintSprint Total: 40 pointsKey Technical Activities:

UAE PASS Integration:

Register application with UAE PASS portal
Configure OAuth 2.0 client in .NET Core
Implement authorization code flow
Handle UAE PASS callbacks
Map UAE PASS user data to local user model



Registration Forms:

Multi-step React form with validation
React Hook Form + Yup schema validation
File upload for trade license documents
Azure Blob Storage integration for documents



.NET Core Backend:

FluentValidation for business rules
Entity Framework models for establishment accounts
Registration workflow state machine
Email service with templating (Razor Pages)



MS SQL Server:

sql   CREATE TABLE accounts.AccountCreationRequest (
       RequestID uniqueidentifier PRIMARY KEY,
       EstablishmentNameAr nvarchar(200),
       EstablishmentNameEn nvarchar(200),
       TradeLicenseNumber varchar(50),
       Emirates int,
       Status varchar(50),
       CreatedDate datetime2,
       ModifiedDate datetime2,
       ...
   );
Background Jobs:

Hangfire dashboard configuration
Email notification jobs
Status update jobs


Definition of Done:

✅ Establishments can register via UAE PASS OAuth
✅ Establishments can register manually with complete form
✅ Registration status tracking functional
✅ Email notifications sent for registration events
✅ Password reset workflow working
✅ OAuth tokens securely stored
✅ All validation rules implemented and tested
✅ Code coverage > 75%
Sprint Deliverables:

UAE PASS OAuth integration complete
Registration workflows functional
Notification system operational
Document upload to Azure Blob Storage working
Sprint 3: Account Creation Review & User Management (Week 7-8) - 37 pointsGoal: Enable Local Customs to review account creation requests and complete user managementTeam Focus:

Frontend: 3 devs on Local Customs review interface and user management
Backend: 2 devs on review workflow and role-based access control
QA: Workflow testing, security testing
DevOps: Performance optimization
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-AEO-016Add users to account (carryover)6Dev 1-2Role management UI, .NET role API, SQL user tablesUS-AEO-018View audit trail5Dev 3React audit viewer, SQL temporal tablesUS-LC-001Review account creation request8Dev 4-5React review interface, .NET review APIUS-LC-002View account request history3Dev 5React history timeline, SQL viewsUS-LC-003Approve/reject account request8Dev 4-6React decision form, .NET workflow engine, SQL state machineTestingIntegration testing Phase 1.1-1.37QA TeamE2E tests, security testsSprint Total: 37 pointsKey Technical Activities:

Local Customs Portal - Review Interface:

React data table with advanced filtering (MUI DataGrid)
Document viewer for trade licenses (PDF.js)
Status management UI
Approval/rejection forms with remarks



Role-Based Access Control:

ASP.NET Core Claims-based authorization
Role hierarchy (Account Manager, Reviewer, Approver)
Permission-based actions
Entity Framework Include/ThenInclude for complex queries



Audit Trail System:

SQL Server temporal tables for automatic audit history



sql   CREATE TABLE accounts.EstablishmentUser (
       UserID uniqueidentifier PRIMARY KEY,
       EstablishmentID uniqueidentifier,
       UserName nvarchar(100),
       Email nvarchar(100),
       Role varchar(50),
       IsActive bit,
       SysStartTime datetime2 GENERATED ALWAYS AS ROW START,
       SysEndTime datetime2 GENERATED ALWAYS AS ROW END,
       PERIOD FOR SYSTEM_TIME (SysStartTime, SysEndTime)
   ) WITH (SYSTEM_VERSIONING = ON (HISTORY_TABLE = accounts.EstablishmentUser_History));

.NET API to query temporal data
React timeline component to visualize history

Workflow Engine:

State machine pattern in .NET
Business rules engine for approval logic
SQL stored procedures for atomic state transitions
Transaction management with Entity Framework



Testing:

xUnit integration tests for workflow
Selenium E2E tests for registration-to-approval flow
Security tests for RBAC


Definition of Done:

✅ User management complete (add/edit/deactivate users)
✅ Local Customs can review account creation requests
✅ Approval/rejection workflow functional with remarks
✅ Audit trail captures all account activities
✅ Role-based access control implemented and tested
✅ Integration tests for Phase 1 (Epics 1.1-1.6) passing
✅ Performance benchmarks met (review page < 2 sec load)
✅ Code coverage > 75%
Sprint Deliverables:

Local Customs review portal operational
Complete user management system
Audit trail system functional
Phase 1.1-1.3 integration tested
Sprint 4: AEO Authorization Request - Part 1 (Week 9-10) - 40 pointsGoal: Enable establishments to submit AEO authorization requestsTeam Focus:

Frontend: 4 devs on complex authorization request form
Backend: 2 devs on form validation and draft management
QA: Form validation testing, data integrity testing
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-AEO-010Submit AEO authorization request13Dev 1-2-3-4Multi-section form wizard, .NET validation, SQL complex schemaUS-AEO-011Save request as draft5Dev 5React auto-save, .NET draft API, SQL draft tablesUS-AEO-012Track request status5Dev 6React timeline, SignalR real-time updatesUS-AEO-013Withdraw submitted request3Dev 6React confirmation dialog, .NET workflowUS-AEO-015Receive request status notifications3Dev 5.NET notification hub, Hangfire jobsForm BuilderComplex form infrastructure11Dev 1-2Form state management, validation frameworkSprint Total: 40 pointsKey Technical Activities:

Authorization Request Form (ReactJS):

Multi-step form wizard with progress indicator
React Hook Form for each section:

Company Information
Business Activities
Financial Information
Compliance History
Supporting Documents


Conditional fields based on business type
Form validation with real-time feedback
Yup validation schemas per section



Draft Management:

Auto-save every 30 seconds (React useEffect)
Save to both local storage and API
Resume from draft with data restoration
Conflict resolution if draft modified on multiple devices



.NET Core Validation Pipeline:

csharp   public class AEOAuthorizationRequestValidator : AbstractValidator<AEOAuthorizationRequestDto>
   {
       public AEOAuthorizationRequestValidator()
       {
           RuleFor(x => x.TradeLicenseNumber)
               .NotEmpty().WithMessage("Trade license number is required")
               .Must(BeValidTradeLicense).WithMessage("Invalid trade license format");
           
           RuleFor(x => x.AnnualRevenue)
               .GreaterThan(0).When(x => x.RevenueDeclarationRequired);
           
           // Complex business rules...
       }
   }
Database Schema (MS SQL Server):

sql   CREATE TABLE authorization.AEOAuthorizationRequest (
       RequestID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       EstablishmentID uniqueidentifier NOT NULL,
       RequestNumber AS ('AEO-REQ-' + FORMAT(RequestDate, 'yyyyMMdd') + '-' + RIGHT('0000' + CAST(CHECKSUM(RequestID) % 10000 AS VARCHAR), 4)) PERSISTED,
       Status varchar(50) NOT NULL DEFAULT 'Draft',
       RequestData nvarchar(max) NOT NULL, -- JSON column for flexible schema
       SubmittedDate datetime2,
       LastModifiedDate datetime2 DEFAULT GETDATE(),
       LastModifiedBy uniqueidentifier,
       CONSTRAINT FK_Request_Establishment FOREIGN KEY (EstablishmentID) REFERENCES accounts.CommercialEstablishment(EstablishmentID),
       CONSTRAINT CHK_RequestData_JSON CHECK (ISJSON(RequestData) = 1)
   );
   
   CREATE TABLE authorization.RequestDocument (
       DocumentID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       RequestID uniqueidentifier NOT NULL,
       DocumentType varchar(100),
       FileName nvarchar(255),
       BlobStoragePath nvarchar(500),
       UploadedDate datetime2 DEFAULT GETDATE(),
       FileSize bigint,
       ContentType varchar(100),
       CONSTRAINT FK_Document_Request FOREIGN KEY (RequestID) REFERENCES authorization.AEOAuthorizationRequest(RequestID) ON DELETE CASCADE
   );
Real-Time Status Updates:

SignalR hub for real-time notifications



csharp   public class RequestStatusHub : Hub
   {
       public async Task SubscribeToRequest(string requestId)
       {
           await Groups.AddToGroupAsync(Context.ConnectionId, $"request-{requestId}");
       }
       
       public async Task NotifyStatusChange(string requestId, string newStatus)
       {
           await Clients.Group($"request-{requestId}").SendAsync("StatusChanged", newStatus);
       }
   }
React SignalR client integration

File Upload:

Azure Blob Storage integration
Chunked upload for large files
Progress indicator
File type validation (.pdf, .docx, .xlsx, .jpg)


Definition of Done:

✅ Establishments can submit complete AEO authorization requests
✅ Multi-section form with validation working
✅ Draft save/resume functional
✅ Document upload to Azure Blob Storage working
✅ Status tracking dashboard with real-time updates
✅ Withdrawal workflow functional
✅ Email notifications sent for all status changes
✅ Form validation rules match BRD requirements 100%
✅ Performance: Form submission < 5 seconds
✅ Code coverage > 75%
Sprint Deliverables:

Complex authorization request form operational
Draft management system functional
Real-time status tracking with SignalR
Document upload system integrated
Sprint 5: AEO Authorization Request - Part 2 & Local Customs Review (Week 11-12) - 39 pointsGoal: Complete AEO authorization request features and enable Local Customs preliminary reviewTeam Focus:

Frontend: 3 devs on resubmission UI and Local Customs review interface
Backend: 3 devs on workflow engine and review logic
QA: End-to-end testing of Phase 1
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-AEO-014Complete and resubmit returned request8Dev 1-2React form pre-population, .NET change tracking, SQL historyUS-LC-004Review AEO authorization request13Dev 3-4-5React review UI, .NET document viewer API, SQL complex queriesUS-LC-005Cancel request at any stage5Dev 5React confirmation, .NET cancellation workflow, SQL cascading updatesUS-LC-006Approve/return request8Dev 3-4React decision form with remarks, .NET workflow, SQL transactionsUS-LC-007Receive request notifications3Dev 6.NET notification hub, SignalRTestingPhase 1 end-to-end testing2QA TeamSelenium E2E, performance, securitySprint Total: 39 pointsKey Technical Activities:

Resubmission with Change Tracking:

React diff viewer to highlight changes requested
.NET change tracking with Entity Framework:



csharp   public class RequestAuditEntry
   {
       public string PropertyName { get; set; }
       public string OldValue { get; set; }
       public string NewValue { get; set; }
       public DateTime ChangeDate { get; set; }
       public string ChangedBy { get; set; }
   }

SQL temporal tables for historical comparison

Local Customs Review Interface:

Comprehensive review dashboard (React)
Multi-tab interface:

Request Details
Documents
History
Remarks/Comments


PDF viewer integration for documents
Side-by-side comparison for resubmissions



Workflow Engine - Review Process:

csharp   public class RequestWorkflowEngine
   {
       public async Task<WorkflowResult> ProcessReview(ReviewDecision decision)
       {
           using var transaction = await _context.Database.BeginTransactionAsync();
           try
           {
               // Update request status
               var request = await _context.Requests.FindAsync(decision.RequestId);
               request.Status = decision.Approve ? "Approved" : "Returned";
               request.ReviewerRemarks = decision.Remarks;
               request.ReviewDate = DateTime.UtcNow;
               request.ReviewedBy = decision.ReviewerId;
               
               // Log workflow history
               await _auditService.LogWorkflowStep(request.RequestID, "Review Complete");
               
               // Send notifications
               await _notificationService.NotifyEstablishment(request.EstablishmentID, "ReviewComplete");
               
               await _context.SaveChangesAsync();
               await transaction.CommitAsync();
               
               return WorkflowResult.Success();
           }
           catch (Exception ex)
           {
               await transaction.RollbackAsync();
               return WorkflowResult.Failure(ex.Message);
           }
       }
   }
Cancellation Workflow:

Soft delete pattern (IsDeleted flag)
Cascading updates to related entities
Notification to all stakeholders
Audit trail entry for cancellation



End-to-End Testing:

Selenium tests for complete flow:

Register → Login → Submit Request → LC Review → Approve/Return


Performance testing with JMeter
Security testing (OWASP Top 10)
Load testing (100 concurrent users)


Definition of Done:

✅ Establishments can resubmit returned requests with tracked changes
✅ Local Customs can review authorization requests comprehensively
✅ Approve/return workflow functional with remarks system
✅ Cancellation workflow working at any stage
✅ All Phase 1 features integration tested
✅ Performance benchmarks met (review page < 3 sec load)
✅ Security audit passed (no critical/high vulnerabilities)
✅ Code coverage > 80%
✅ Phase 1 ready for UAT
Sprint Deliverables:

Complete authorization request lifecycle functional
Local Customs review portal operational
End-to-end Phase 1 tested and stable
Performance and security validated
Sprint 6-7: Phase 1 UAT Support & Hardening (Week 13-16) - 45 points totalGoal: Stabilize Phase 1, conduct User Acceptance Testing, fix defects, optimize performanceTeam Focus:

All developers: Bug fixing, optimization, refactoring
QA: UAT coordination, regression testing
BA: User training, documentation
DevOps: Performance tuning, infrastructure optimization
Activities:Sprint 6 (Week 13-14) - 25 points:

User Acceptance Testing:

Coordinate with Federal Customs stakeholders
Coordinate with Local Customs departments
Coordinate with test commercial establishments
Capture feedback and defects in Azure DevOps



Defect Resolution:

Critical/High priority bugs: 15 points
Medium priority bugs: 5 points
UI/UX improvements: 3 points
Documentation fixes: 2 points



Performance Optimization:

SQL query optimization (indexes, query plans)
Entity Framework query tuning
React component optimization (memo, lazy loading)
API response caching (Redis)



Security Hardening:

Penetration testing remediation
SQL injection prevention validation
XSS prevention validation
CSRF token implementation
SSL/TLS configuration


Sprint 7 (Week 15-16) - 20 points:

Final UAT Round:

Regression testing of fixes
User training sessions
Create user manuals and videos



Final Defect Resolution:

Remaining medium/low priority bugs: 10 points
Polish and refinements: 5 points
Documentation completion: 5 points



Go-Live Preparation:

Production environment setup
Data migration scripts (if needed)
Backup and recovery procedures
Monitoring and alerting setup
Run book documentation


Success Criteria:

✅ UAT sign-off obtained from all stakeholder groups
✅ Zero critical/high defects remaining
✅ Performance benchmarks exceeded:

Page load times < 2 seconds (95th percentile)
API response times < 500ms (95th percentile)
Form submission < 3 seconds


✅ Security audit passed with no critical/high findings
✅ User training completed
✅ Documentation finalized (user manuals, technical docs, API docs)
✅ Production environment ready
✅ Code coverage > 80%
5.4 Phase 2 - Sprints 8-14 (Self-Assessment Questionnaire)Sprint 8: Federal Admin Configuration - Question & Risk Banks (Week 17-18) - 38 pointsGoal: Enable Federal Customs to manage Question Bank and Risks BankTeam Focus:

Frontend: 3 devs on hierarchical tree UI and question forms
Backend: 2 devs on hierarchical data management and full-text search
QA: Admin functionality testing
DevOps: Database optimization for hierarchical queries
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-SAQ-001Create Question Bank groups8Dev 1-2React tree component, .NET hierarchical API, SQL hierarchyidUS-SAQ-002Create questions with metadata13Dev 3-4-5Complex React form, .NET question engine, SQL full-text searchUS-SAQ-004Search and filter questions5Dev 6React search UI, .NET search API, SQL full-text indexesUS-SAQ-006Create Risks Bank groups8Dev 1-2React tree UI, .NET risk API, SQL hierarchical tablesUS-SAQ-007Create risks with metadata (partial)4Dev 3Begin risk creation formSprint Total: 38 pointsKey Technical Activities:

Hierarchical Data Structure (MS SQL Server):

sql   CREATE TABLE saq.QuestionBankGroup (
       GroupID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       ParentGroupID uniqueidentifier NULL,
       GroupNameAr nvarchar(200) NOT NULL,
       GroupNameEn nvarchar(200) NOT NULL,
       GroupPath hierarchyid NOT NULL,
       Level AS GroupPath.GetLevel(),
       SortOrder int,
       IsActive bit DEFAULT 1,
       CreatedDate datetime2 DEFAULT GETDATE(),
       CONSTRAINT FK_Group_Parent FOREIGN KEY (ParentGroupID) REFERENCES saq.QuestionBankGroup(GroupID)
   );
   
   CREATE INDEX IX_QuestionBankGroup_Path ON saq.QuestionBankGroup(GroupPath);
   
   CREATE TABLE saq.Question (
       QuestionID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       GroupID uniqueidentifier NOT NULL,
       QuestionNumber AS ('Q-' + RIGHT('0000' + CAST(CHECKSUM(QuestionID) % 10000 AS VARCHAR), 4)) PERSISTED,
       QuestionTitleAr nvarchar(500) NOT NULL,
       QuestionTitleEn nvarchar(500) NOT NULL,
       QuestionTextAr nvarchar(max) NOT NULL,
       QuestionTextEn nvarchar(max) NOT NULL,
       AnswerType varchar(50) NOT NULL, -- TextArea, TextBox, SingleChoice, MultipleChoice, YesNo, Numeric, Document
       IsConditional bit DEFAULT 0,
       ConditionalLogic nvarchar(max), -- JSON
       ExplanatoryNotesAr nvarchar(max),
       ExplanatoryNotesEn nvarchar(max),
       IsMandatory bit DEFAULT 1,
       Status varchar(50) NOT NULL DEFAULT 'Draft', -- Draft, UnderReview, Published, Archived
       Version int DEFAULT 1,
       PublishedDate datetime2,
       CreatedBy uniqueidentifier,
       CreatedDate datetime2 DEFAULT GETDATE(),
       ModifiedDate datetime2,
       CONSTRAINT FK_Question_Group FOREIGN KEY (GroupID) REFERENCES saq.QuestionBankGroup(GroupID),
       CONSTRAINT CHK_ConditionalLogic_JSON CHECK (ConditionalLogic IS NULL OR ISJSON(ConditionalLogic) = 1)
   );
   
   -- Full-text search for questions
   CREATE FULLTEXT CATALOG ft_SAQ_Catalog AS DEFAULT;
   CREATE FULLTEXT INDEX ON saq.Question(QuestionTitleAr, QuestionTitleEn, QuestionTextAr, QuestionTextEn)
       KEY INDEX PK__Question__xxx ON ft_SAQ_Catalog
       WITH STOPLIST = SYSTEM;
React Tree Component (Material-UI TreeView):

javascript   const QuestionBankTree = () => {
     const [treeData, setTreeData] = useState([]);
     const [selectedNode, setSelectedNode] = useState(null);
     
     // Fetch hierarchical data from API
     useEffect(() => {
       api.get('/saq/questionbank/tree').then(response => {
         setTreeData(response.data);
       });
     }, []);
     
     const handleNodeSelect = (nodeId) => {
       setSelectedNode(nodeId);
       // Load questions for selected group
     };
     
     return (
       <TreeView
         defaultCollapseIcon={<ExpandMoreIcon />}
         defaultExpandIcon={<ChevronRightIcon />}
         onNodeSelect={handleNodeSelect}
       >
         {renderTree(treeData)}
       </TreeView>
     );
   };
Question Creation Form (ReactJS):

Multi-language input fields (Arabic/English)
Answer type selection with dynamic form fields
Conditional question builder (if answer = X, show question Y)
Rich text editor for explanatory notes
File upload for question images/diagrams



.NET Core Question API:

csharp   [HttpPost("questions")]
   public async Task<IActionResult> CreateQuestion([FromBody] CreateQuestionDto dto)
   {
       var validator = new QuestionValidator();
       var validationResult = await validator.ValidateAsync(dto);
       
       if (!validationResult.IsValid)
           return BadRequest(validationResult.Errors);
       
       var question = _mapper.Map<Question>(dto);
       question.Status = "Draft";
       question.Version = 1;
       question.CreatedBy = User.GetUserId();
       
       _context.Questions.Add(question);
       await _context.SaveChangesAsync();
       
       // Index for full-text search is automatic
       
       return CreatedAtAction(nameof(GetQuestion), new { id = question.QuestionID }, question);
   }
Full-Text Search Implementation:

csharp   [HttpGet("questions/search")]
   public async Task<IActionResult> SearchQuestions([FromQuery] string searchTerm, [FromQuery] string language = "en")
   {
       var sql = language == "ar" 
           ? @"SELECT * FROM saq.Question WHERE CONTAINS((QuestionTitleAr, QuestionTextAr), @p0)"
           : @"SELECT * FROM saq.Question WHERE CONTAINS((QuestionTitleEn, QuestionTextEn), @p0)";
       
       var questions = await _context.Questions
           .FromSqlRaw(sql, searchTerm)
           .Include(q => q.Group)
           .ToListAsync();
       
       return Ok(questions);
   }Definition of Done:

✅ Federal admins can create hierarchical question groups
✅ Federal admins can create questions with all metadata
✅ Question Bank search functional (Arabic/English)
✅ Risk Bank groups can be created
✅ Multi-language support working correctly (Arabic RTL)
✅ Full-text search performant (< 1 second for any query)
✅ Code coverage > 75%
Sprint Deliverables:

Question Bank management operational
Risk Bank foundation ready
Full-text search functional
Hierarchical tree navigation working
Sprint 9: Question & Risk Bank Completion + SAQ Template Foundation (Week 19-20) - 42 pointsGoal: Complete Question/Risk Bank features and begin SAQ Template builderTeam Focus:

Frontend: 3 devs on version control UI and template builder foundation
Backend: 2 devs on versioning logic and template engine
QA: Version control testing
BA: Template requirements refinement
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-SAQ-007Create risks with metadata (carryover)4Dev 1Complete risk creation formUS-SAQ-003Modify/delete Question Bank8Dev 2-3React CRUD, .NET versioning, SQL version tablesUS-SAQ-005View question version history5Dev 3React version viewer, SQL temporal tablesUS-SAQ-008Modify/delete Risks Bank8Dev 4React CRUD, .NET versioning, SQL soft deleteUS-SAQ-009Create SAQ template from scratch (partial)17Dev 5-6Begin template builder - carry 4 points to Sprint 10Sprint Total: 42 pointsKey Technical Activities:

Version Control System:

Temporal tables for automatic versioning



sql   CREATE TABLE saq.QuestionVersion (
       VersionID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       QuestionID uniqueidentifier NOT NULL,
       Version int NOT NULL,
       QuestionData nvarchar(max) NOT NULL, -- JSON snapshot
       Status varchar(50),
       ChangeDescription nvarchar(500),
       ChangedBy uniqueidentifier,
       ChangeDate datetime2 DEFAULT GETDATE(),
       CONSTRAINT FK_Version_Question FOREIGN KEY (QuestionID) REFERENCES saq.Question(QuestionID)
   );

React version comparison UI
Restore from version functionality

Soft Delete Implementation:

csharp   public class Question : ISoftDeletable
   {
       public Guid QuestionID { get; set; }
       public bool IsDeleted { get; set; }
       public DateTime? DeletedDate { get; set; }
       public Guid? DeletedBy { get; set; }
       // ... other properties
   }
   
   // Global query filter in DbContext
   modelBuilder.Entity<Question>().HasQueryFilter(q => !q.IsDeleted);
SAQ Template Builder Foundation:

React drag-and-drop interface (react-beautiful-dnd)
Section/subsection builder
Question selector from Question Bank
Risk selector from Risks Bank
Template preview mode



Template Data Model:

sql   CREATE TABLE saq.SAQTemplate (
       TemplateID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       TemplateName nvarchar(200) NOT NULL,
       TemplateDescription nvarchar(500),
       TemplateStructure nvarchar(max) NOT NULL, -- JSON structure
       Status varchar(50) NOT NULL DEFAULT 'Draft',
       Version int DEFAULT 1,
       CreatedBy uniqueidentifier,
       CreatedDate datetime2 DEFAULT GETDATE(),
       PublishedDate datetime2,
       CONSTRAINT CHK_TemplateStructure_JSON CHECK (ISJSON(TemplateStructure) = 1)
   );
   
   -- Example template structure JSON:
   {
     "sections": [
       {
         "sectionId": "uuid",
         "nameAr": "معلومات الشركة",
         "nameEn": "Company Information",
         "isLeaf": true,
         "questions": ["uuid1", "uuid2"],
         "risks": ["uuid3", "uuid4"],
         "subsections": []
       }
     ]
   }Definition of Done:

✅ Question Bank fully functional with CRUD operations
✅ Version history tracking for questions
✅ Risk Bank fully functional with CRUD operations
✅ Soft delete implemented and tested
✅ SAQ Template builder foundation laid
✅ Drag-and-drop section builder working
✅ Code coverage > 75%
Sprint Deliverables:

Question/Risk Bank management complete
Version control system operational
SAQ Template builder foundation ready
Sprint 10: SAQ Template Builder Completion (Week 21-22) - 40 pointsGoal: Complete SAQ Template creation with all advanced featuresTeam Focus:

Frontend: 4 devs on template builder advanced features
Backend: 2 devs on template engine and approval workflow
QA: Template builder testing, complex scenario testing
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-SAQ-009Create SAQ template (carryover)4Dev 1-2Complete template builderUS-SAQ-010Duplicate existing template8Dev 3Template duplication with deep copyUS-SAQ-011Review and approve template8Dev 4Template approval workflowTemplate Advanced FeaturesConditional questions, risk mapping20All DevsComplex template featuresSprint Total: 40 pointsKey Technical Activities:

SAQ Template Builder (ReactJS):

Complete drag-and-drop interface
Section/subsection management (up to 3 levels deep)
Question search and selection from Question Bank
Risk search and selection from Risks Bank
Conditional question builder:



javascript     const ConditionalQuestionBuilder = ({ question }) => {
       const [conditions, setConditions] = useState([]);
       
       const addCondition = () => {
         setConditions([...conditions, {
           sourceQuestionId: '',
           operator: 'equals',
           value: '',
           targetQuestionIds: []
         }]);
       };
       
       return (
         <Box>
           {conditions.map((condition, index) => (
             <ConditionalRule
               key={index}
               condition={condition}
               onChange={(updated) => updateCondition(index, updated)}
             />
           ))}
           <Button onClick={addCondition}>Add Condition</Button>
         </Box>
       );
     };
Template preview mode with sample data
Template validation before submission

Template Duplication (.NET Core):

csharp   [HttpPost("templates/{id}/duplicate")]
   public async Task<IActionResult> DuplicateTemplate(Guid id, [FromBody] DuplicateTemplateDto dto)
   {
       var sourceTemplate = await _context.SAQTemplates
           .Include(t => t.Questions)
           .Include(t => t.Risks)
           .FirstOrDefaultAsync(t => t.TemplateID == id);
       
       if (sourceTemplate == null)
           return NotFound();
       
       // Deep copy with latest question versions
       var newTemplate = new SAQTemplate
       {
           TemplateName = dto.NewTemplateName,
           TemplateDescription = dto.NewTemplateDescription,
           TemplateStructure = sourceTemplate.TemplateStructure,
           Status = "Draft",
           Version = 1,
           CreatedBy = User.GetUserId()
       };
       
       // Update question references to latest versions
       var structure = JsonConvert.DeserializeObject<TemplateStructure>(newTemplate.TemplateStructure);
       foreach (var section in structure.Sections)
       {
           if (section.IsLeaf)
           {
               section.Questions = await GetLatestQuestionVersions(section.Questions);
           }
       }
       newTemplate.TemplateStructure = JsonConvert.SerializeObject(structure);
       
       _context.SAQTemplates.Add(newTemplate);
       await _context.SaveChangesAsync();
       
       return CreatedAtAction(nameof(GetTemplate), new { id = newTemplate.TemplateID }, newTemplate);
   }
Approval Workflow:

Senior Federal Administrator review interface
Accept/Reject/Return with remarks
Email notifications for workflow steps
Status tracking (Draft → Under Review → Published/Returned/Rejected)



Template Validation Engine:

csharp   public class TemplateValidationService
   {
       public ValidationResult ValidateTemplate(SAQTemplate template)
       {
           var result = new ValidationResult();
           
           // Check structure
           if (string.IsNullOrEmpty(template.TemplateStructure))
               result.Errors.Add("Template structure is required");
           
           var structure = JsonConvert.DeserializeObject<TemplateStructure>(template.TemplateStructure);
           
           // Validate sections
           if (!structure.Sections.Any())
               result.Errors.Add("Template must have at least one section");
           
           // Validate that all leaf sections have questions
           foreach (var section in structure.GetLeafSections())
           {
               if (!section.Questions.Any())
                   result.Errors.Add($"Leaf section '{section.NameEn}' must have at least one question");
           }
           
           // Validate conditional question logic
           foreach (var question in structure.GetAllQuestions())
           {
               if (question.IsConditional)
               {
                   var logic = JsonConvert.DeserializeObject<ConditionalLogic>(question.ConditionalLogic);
                   if (!ValidateConditionalLogic(logic, structure))
                       result.Errors.Add($"Invalid conditional logic for question '{question.QuestionNumber}'");
               }
           }
           
           return result;
       }
   }Definition of Done:

✅ SAQ Template builder fully functional with all features
✅ Templates can be created from scratch with sections/questions/risks
✅ Templates can be duplicated with latest question versions
✅ Conditional question logic working
✅ Risk mapping to template sections functional
✅ Template approval workflow complete
✅ Template validation comprehensive
✅ Preview mode accurately represents final SAQ
✅ Code coverage > 75%
Sprint Deliverables:

Complete SAQ Template creation system
Template approval workflow operational
Advanced features (conditional questions) working
Sprint 11: SAQ Preparation & Sharing (Week 23-24) - 41 pointsGoal: Enable Local Customs to generate and share SAQ with establishmentsTeam Focus:

Frontend: 3 devs on team assignment and SAQ generation UI
Backend: 2 devs on SAQ generation engine and sharing workflow
QA: SAQ generation testing, data integrity testing
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-SAQ-012Assign Validation Team5Dev 1React team selector, .NET assignment APIUS-SAQ-013Generate SAQ from template13Dev 2-3-4.NET SAQ generation engine, SQL instance tablesUS-SAQ-014Share SAQ with establishment8Dev 5React share UI, .NET sharing workflow, notificationsUS-SAQ-015View shared SAQ8Dev 6React SAQ viewer for establishmentsUS-SAQ-027Receive SAQ notifications3Dev 5.NET notification hub, email templatesUS-SAQ-028Track SAQ status3Dev 1React status tracker, .NET status APITestingIntegration testing1QATemplate-to-instance testingSprint Total: 41 pointsKey Technical Activities:

Validation Team Assignment:

React team member selector (multi-select)
Team lead designation
Team role assignment (validator, reviewer)



sql   CREATE TABLE validation.ValidationTeam (
       TeamID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       RequestID uniqueidentifier NOT NULL,
       TeamLead uniqueidentifier NOT NULL,
       AssignedDate datetime2 DEFAULT GETDATE(),
       CONSTRAINT FK_Team_Request FOREIGN KEY (RequestID) REFERENCES authorization.AEOAuthorizationRequest(RequestID)
   );
   
   CREATE TABLE validation.ValidationTeamMember (
       MemberID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       TeamID uniqueidentifier NOT NULL,
       UserID uniqueidentifier NOT NULL,
       Role varchar(50), -- Validator, Reviewer
       CONSTRAINT FK_Member_Team FOREIGN KEY (TeamID) REFERENCES validation.ValidationTeam(TeamID)
   );
SAQ Generation Engine (.NET Core):

csharp   public class SAQGenerationService
   {
       public async Task<SAQInstance> GenerateSAQFromTemplate(Guid templateId, Guid requestId)
       {
           var template = await _context.SAQTemplates
               .Include(t => t.Questions)
               .Include(t => t.Risks)
               .FirstOrDefaultAsync(t => t.TemplateID == templateId && t.Status == "Published");
           
           if (template == null)
               throw new InvalidOperationException("Published template not found");
           
           var saqInstance = new SAQInstance
           {
               SAQInstanceID = Guid.NewGuid(),
               TemplateID = templateId,
               RequestID = requestId,
               Status = "Generated",
               GeneratedDate = DateTime.UtcNow,
               ExpiryDate = DateTime.UtcNow.AddBusinessDays(15), // 15 business days deadline
               SAQStructure = template.TemplateStructure // Copy template structure
           };
           
           _context.SAQInstances.Add(saqInstance);
           
           // Create placeholder responses for all questions
           var structure = JsonConvert.DeserializeObject<TemplateStructure>(template.TemplateStructure);
           foreach (var question in structure.GetAllQuestions())
           {
               var response = new SAQResponse
               {
                   ResponseID = Guid.NewGuid(),
                   SAQInstanceID = saqInstance.SAQInstanceID,
                   QuestionID = question.QuestionID,
                   Status = "Pending"
               };
               _context.SAQResponses.Add(response);
           }
           
           await _context.SaveChangesAsync();
           
           return saqInstance;
       }
   }
SAQ Sharing Workflow:

Local Customs reviews generated SAQ before sharing
Adds any specific instructions or notes
Clicks "Share with Establishment"
System sends email + in-portal notification
Establishment users receive access



SAQ Viewer for Establishments (ReactJS):

Read-only view of SAQ structure
Section navigation (table of contents)
Question list with metadata
Progress indicator (questions answered/total)
Instructions and explanatory notes
Start button to begin completing SAQ



Database Schema for SAQ Instances:

sql   CREATE TABLE saq.SAQInstance (
       SAQInstanceID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       TemplateID uniqueidentifier NOT NULL,
       RequestID uniqueidentifier NOT NULL,
       ValidationTeamID uniqueidentifier NOT NULL,
       Status varchar(50) NOT NULL DEFAULT 'Generated', -- Generated, Shared, InProgress, Submitted, UnderReview, Returned, Approved, Cancelled, Expired
       SAQStructure nvarchar(max) NOT NULL, -- Copy of template structure at generation time
       GeneratedDate datetime2 DEFAULT GETDATE(),
       SharedDate datetime2,
       SubmittedDate datetime2,
       ExpiryDate datetime2,
       CONSTRAINT FK_SAQInstance_Template FOREIGN KEY (TemplateID) REFERENCES saq.SAQTemplate(TemplateID),
       CONSTRAINT FK_SAQInstance_Request FOREIGN KEY (RequestID) REFERENCES authorization.AEOAuthorizationRequest(RequestID),
       CONSTRAINT FK_SAQInstance_Team FOREIGN KEY (ValidationTeamID) REFERENCES validation.ValidationTeam(TeamID)
   );
   
   CREATE TABLE saq.SAQResponse (
       ResponseID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       SAQInstanceID uniqueidentifier NOT NULL,
       QuestionID uniqueidentifier NOT NULL,
       ResponseText nvarchar(max),
       ResponseData nvarchar(max), -- JSON for complex answer types
       Status varchar(50) NOT NULL DEFAULT 'Pending', -- Pending, InProgress, Completed, Accepted, NotAccepted
       CompletedBy uniqueidentifier,
       CompletedDate datetime2,
       ReviewedBy uniqueidentifier,
       ReviewedDate datetime2,
       ReviewerRemarks nvarchar(max),
       CONSTRAINT FK_Response_Instance FOREIGN KEY (SAQInstanceID) REFERENCES saq.SAQInstance(SAQInstanceID),
       CONSTRAINT FK_Response_Question FOREIGN KEY (QuestionID) REFERENCES saq.Question(QuestionID)
   );Definition of Done:

✅ Validation teams can be assigned to authorization requests
✅ SAQ instances generated from published templates
✅ SAQ can be shared with establishments
✅ Establishments can view shared SAQ
✅ Notifications sent for all SAQ events
✅ Status tracking accurate throughout lifecycle
✅ 15-business-day expiry calculation correct
✅ Code coverage > 75%
Sprint Deliverables:

SAQ generation engine operational
SAQ sharing workflow functional
Establishment SAQ viewer ready
Sprint 12: SAQ Completion by Establishments (Week 25-26) - 37 pointsGoal: Enable collaborative SAQ completion by establishment usersTeam Focus:

Frontend: 4 devs on collaborative SAQ editor with real-time features
Backend: 2 devs on multi-user coordination and conflict resolution
QA: Concurrency testing, collaboration testing
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-SAQ-016Complete SAQ collaboratively13Dev 1-2-3React collaborative editor, SignalR real-time, SQL conflict resolutionUS-SAQ-017Upload supporting documents5Dev 4React file upload, Azure Blob Storage integrationUS-SAQ-018View SAQ completion progress5Dev 5React progress dashboard, .NET progress calculatorUS-SAQ-019Submit completed SAQ8Dev 6React submission, .NET validation pipeline, SQL transactionsUS-SAQ-020Receive SAQ status notifications3Dev 4.NET notification serviceUS-SAQ-031Add internal comments3Dev 5React internal notes, .NET comments APISprint Total: 37 pointsKey Technical Activities:

Collaborative SAQ Editing (ReactJS + SignalR):

javascript   const CollaborativeSAQEditor = ({ saqInstanceId }) => {
     const [responses, setResponses] = useState({});
     const [activeUsers, setActiveUsers] = useState([]);
     const hubConnection = useRef(null);
     
     useEffect(() => {
       // Setup SignalR connection
       hubConnection.current = new signalR.HubConnectionBuilder()
         .withUrl("/hubs/saq")
         .withAutomaticReconnect()
         .build();
       
       hubConnection.current.on("UserJoined", (user) => {
         setActiveUsers(prev => [...prev, user]);
       });
       
       hubConnection.current.on("ResponseUpdated", (questionId, newValue, userId) => {
         if (userId !== currentUser.id) {
           setResponses(prev => ({
             ...prev,
             [questionId]: { value: newValue, updatedBy: userId }
           }));
         }
       });
       
       hubConnection.current.start().then(() => {
         hubConnection.current.invoke("JoinSAQSession", saqInstanceId);
       });
       
       return () => {
         hubConnection.current.stop();
       };
     }, [saqInstanceId]);
     
     const handleResponseChange = debounce((questionId, value) => {
       // Optimistic update
       setResponses(prev => ({ ...prev, [questionId]: { value, updatedBy: currentUser.id } }));
       
       // Send to server
       hubConnection.current.invoke("UpdateResponse", saqInstanceId, questionId, value);
       
       // Auto-save to API
       api.put(`/saq/responses/${questionId}`, { responseText: value });
     }, 500);
     
     return (
       <Box>
         <ActiveUsers users={activeUsers} />
         <SAQQuestions responses={responses} onChange={handleResponseChange} />
       </Box>
     );
   };
SignalR Hub (.NET Core):

csharp   public class SAQCollaborationHub : Hub
   {
       private readonly ISAQService _saqService;
       
       public async Task JoinSAQSession(Guid saqInstanceId)
       {
           await Groups.AddToGroupAsync(Context.ConnectionId, $"saq-{saqInstanceId}");
           await Clients.Group($"saq-{saqInstanceId}").SendAsync("UserJoined", Context.User.Identity.Name);
       }
       
       public async Task UpdateResponse(Guid saqInstanceId, Guid questionId, string responseText)
       {
           // Save to database with optimistic concurrency
           await _saqService.UpdateResponse(questionId, responseText, Context.User.GetUserId());
           
           // Broadcast to other users in the same SAQ session
           await Clients.OthersInGroup($"saq-{saqInstanceId}")
               .SendAsync("ResponseUpdated", questionId, responseText, Context.User.GetUserId());
       }
       
       public async Task LeaveSAQSession(Guid saqInstanceId)
       {
           await Groups.RemoveFromGroupAsync(Context.ConnectionId, $"saq-{saqInstanceId}");
           await Clients.Group($"saq-{saqInstanceId}").SendAsync("UserLeft", Context.User.Identity.Name);
       }
   }
Optimistic Concurrency Control (Entity Framework):

csharp   public class SAQResponse
   {
       public Guid ResponseID { get; set; }
       // ... other properties
       
       [Timestamp]
       public byte[] RowVersion { get; set; } // Concurrency token
   }
   
   public async Task<bool> UpdateResponse(Guid responseId, string responseText, Guid userId)
   {
       try
       {
           var response = await _context.SAQResponses.FindAsync(responseId);
           response.ResponseText = responseText;
           response.CompletedBy = userId;
           response.CompletedDate = DateTime.UtcNow;
           response.Status = "Completed";
           
           await _context.SaveChangesAsync();
           return true;
       }
       catch (DbUpdateConcurrencyException)
       {
           // Handle conflict: last-write-wins or prompt user
           return false;
       }
   }
Document Upload for Questions:

Azure Blob Storage integration
File type validation (.pdf, .docx, .xlsx, .jpg, .png)
File size limit (10MB per file)
Multiple files per question
Virus scanning integration



sql   CREATE TABLE saq.SAQResponseDocument (
       DocumentID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       ResponseID uniqueidentifier NOT NULL,
       FileName nvarchar(255) NOT NULL,
       BlobStoragePath nvarchar(500) NOT NULL,
       FileSize bigint,
       ContentType varchar(100),
       UploadedBy uniqueidentifier,
       UploadedDate datetime2 DEFAULT GETDATE(),
       CONSTRAINT FK_Document_Response FOREIGN KEY (ResponseID) REFERENCES saq.SAQResponse(ResponseID)
   );
Progress Calculation:

csharp   public class SAQProgressService
   {
       public async Task<SAQProgress> CalculateProgress(Guid saqInstanceId)
       {
           var totalQuestions = await _context.SAQResponses
               .Where(r => r.SAQInstanceID == saqInstanceId)
               .CountAsync();
           
           var completedQuestions = await _context.SAQResponses
               .Where(r => r.SAQInstanceID == saqInstanceId && r.Status == "Completed")
               .CountAsync();
           
           var mandatoryQuestions = await _context.SAQResponses
               .Where(r => r.SAQInstanceID == saqInstanceId)
               .Join(_context.Questions, r => r.QuestionID, q => q.QuestionID, (r, q) => new { Response = r, Question = q })
               .Where(x => x.Question.IsMandatory)
               .CountAsync();
           
           var completedMandatoryQuestions = await _context.SAQResponses
               .Where(r => r.SAQInstanceID == saqInstanceId && r.Status == "Completed")
               .Join(_context.Questions, r => r.QuestionID, q => q.QuestionID, (r, q) => new { Response = r, Question = q })
               .Where(x => x.Question.IsMandatory)
               .CountAsync();
           
           return new SAQProgress
           {
               TotalQuestions = totalQuestions,
               CompletedQuestions = completedQuestions,
               PercentageComplete = (completedQuestions * 100.0) / totalQuestions,
               MandatoryQuestions = mandatoryQuestions,
               CompletedMandatoryQuestions = completedMandatoryQuestions,
               CanSubmit = completedMandatoryQuestions == mandatoryQuestions
           };
       }
   }
SAQ Submission Validation:

All mandatory questions answered
All required documents uploaded
Conditional question logic satisfied
Account Manager approval (BR.15)



csharp   public class SAQSubmissionValidator
   {
       public async Task<ValidationResult> ValidateSubmission(Guid saqInstanceId)
       {
           var result = new ValidationResult();
           
           // Check all mandatory questions answered
           var unansweredMandatory = await _context.SAQResponses
               .Where(r => r.SAQInstanceID == saqInstanceId && r.Status != "Completed")
               .Join(_context.Questions, r => r.QuestionID, q => q.QuestionID, (r, q) => q)
               .Where(q => q.IsMandatory)
               .ToListAsync();
           
           if (unansweredMandatory.Any())
           {
               result.Errors.Add($"{unansweredMandatory.Count} mandatory questions remain unanswered");
           }
           
           // Check conditional question logic
           var allResponses = await _context.SAQResponses
               .Where(r => r.SAQInstanceID == saqInstanceId)
               .Include(r => r.Question)
               .ToListAsync();
           
           foreach (var response in allResponses.Where(r => r.Question.IsConditional))
           {
               var conditionalLogic = JsonConvert.DeserializeObject<ConditionalLogic>(response.Question.ConditionalLogic);
               if (!ValidateConditionalResponse(response, conditionalLogic, allResponses))
               {
                   result.Errors.Add($"Question {response.Question.QuestionNumber} has invalid conditional response");
               }
           }
           
           return result;
       }
   }Definition of Done:

✅ Multiple users can complete SAQ simultaneously
✅ Real-time updates visible to all collaborators
✅ Document upload functional for all question types
✅ Progress tracking accurate and real-time
✅ Submission validation comprehensive
✅ Internal comments working for collaboration
✅ Optimistic concurrency handling prevents data loss
✅ Performance: SAQ editor responsive with 100+ questions
✅ Code coverage > 75%
Sprint Deliverables:

Collaborative SAQ completion system functional
Real-time collaboration via SignalR working
Document upload system integrated
Progress tracking dashboard operational
Sprint 13: SAQ Review & Approval - Part 1 (Week 27-28) - 39 pointsGoal: Enable Validation Team to review and provide feedback on SAQTeam Focus:

Frontend: 3 devs on review interface and marking system
Backend: 2 devs on review API and remarks system
QA: Review workflow testing
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-SAQ-021Review submitted SAQ13Dev 1-2-3React review interface, .NET review API, SQL aggregationsUS-SAQ-022Mark responses as accepted/not accepted8Dev 4React marking UI, .NET marking APIUS-SAQ-023Add remarks to responses5Dev 5React comments component, .NET comments APIUS-SAQ-024Return SAQ for modifications8Dev 6React return workflow, .NET state transitionsUS-SAQ-025Review resubmitted SAQ5Dev 3React diff viewer, .NET change trackingSprint Total: 39 pointsKey Technical Activities:

SAQ Review Interface (ReactJS):

Side-by-side view:

Left: Question
Right: Establishment's response


Inline marking buttons (Accept/Not Accept)
Remarks text area for each question
Navigation tree for sections
Filter by status (All/Accepted/Not Accepted/Pending)
Bulk actions (Accept all in section)



Response Marking System:

csharp   [HttpPut("responses/{responseId}/mark")]
   public async Task<IActionResult> MarkResponse(Guid responseId, [FromBody] MarkResponseDto dto)
   {
       var response = await _context.SAQResponses.FindAsync(responseId);
       if (response == null)
           return NotFound();
       
       response.Status = dto.IsAccepted ? "Accepted" : "NotAccepted";
       response.ReviewedBy = User.GetUserId();
       response.ReviewedDate = DateTime.UtcNow;
       response.ReviewerRemarks = dto.Remarks;
       
       await _context.SaveChangesAsync();
       
       // Check if all responses marked - update SAQ status
       await CheckAndUpdateSAQStatus(response.SAQInstanceID);
       
       return Ok();
   }
Remarks/Comments System:

Rich text editor for detailed remarks
Attach documents to remarks
Remarks visible to establishment
Internal notes (visible only to validation team)



sql   CREATE TABLE saq.ResponseRemark (
       RemarkID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       ResponseID uniqueidentifier NOT NULL,
       RemarkText nvarchar(max) NOT NULL,
       IsInternal bit DEFAULT 0, -- Internal notes vs. shared with establishment
       CreatedBy uniqueidentifier NOT NULL,
       CreatedDate datetime2 DEFAULT GETDATE(),
       CONSTRAINT FK_Remark_Response FOREIGN KEY (ResponseID) REFERENCES saq.SAQResponse(ResponseID)
   );
Return Workflow:

Validation Team Lead clicks "Return to Establishment"
System prompts for overall remarks
System changes SAQ status to "Returned"
System sends notification to establishment with:

List of questions requiring revision (Not Accepted)
Remarks for each question
Instructions for resubmission


Establishment can view original responses and remarks
Establishment modifies responses
Establishment resubmits SAQ



Change Tracking for Resubmissions:

sql   CREATE TABLE saq.SAQResponseHistory (
       HistoryID uniqueidentifier PRIMARY KEY DEFAULT NEWID(),
       ResponseID uniqueidentifier NOT NULL,
       ResponseText nvarchar(max),
       ResponseData nvarchar(max),
       SubmittedBy uniqueidentifier,
       SubmittedDate datetime2,
       Version int,
       CONSTRAINT FK_History_Response FOREIGN KEY (ResponseID) REFERENCES saq.SAQResponse(ResponseID)
   );

Diff viewer shows:

Old response (greyed out)
New response (highlighted)
Changes summary



Review Progress Tracking:

Dashboard showing review progress
Responses by status (Accepted/Not Accepted/Pending Review)
Estimated time to complete review
Reviewer activity log


Definition of Done:

✅ Validation Team can review submitted SAQ responses
✅ Accept/Not Accept marking functional
✅ Remarks system working with rich text
✅ Return workflow complete with change tracking
✅ Resubmission review showing changes clearly
✅ Internal notes vs. shared remarks working
✅ Review progress tracking accurate
✅ Code coverage > 75%
Sprint Deliverables:

SAQ review interface operational
Response marking system functional
Remarks and return workflow complete
Change tracking for resubmissions working
Sprint 14: SAQ Approval & Workflow Management (Week 29-30) - 38 pointsGoal: Complete SAQ lifecycle with approval and workflow management featuresTeam Focus:

Frontend: 2 devs on approval UI and workflow features
Backend: 2 devs on approval workflow and expiration handling
QA: End-to-end Phase 2 testing
BA: Phase 2 documentation
Stories:
Story IDStory TitlePointsAssigneeTechnical TasksUS-SAQ-026Approve SAQ8Dev 1-2React approval form, .NET approval workflowUS-SAQ-029Cancel SAQ3Dev 3React cancellation, .NET workflowUS-SAQ-030Handle SAQ expiration5Dev 4.NET Hangfire scheduled jobs, SQL expiration logicPhase 2 TestingEnd-to-end Phase 2 testing12QA TeamSelenium E2E, performance, securityPhase 2 DocumentationUser guides, admin manuals10BA + DevsComprehensive documentationSprint Total: 38 pointsKey Technical Activities:

SAQ Approval Workflow:

Validation Team Lead clicks "Approve SAQ"
System validates:

All questions marked as "Accepted"
No open remarks
Account Manager approval obtained (BR.15)


System changes status to "Approved"
System triggers next phase (Initial Risk Assessment)
Notifications sent to:

Establishment
Validation Team
Assigned risk assessors





SAQ Cancellation:

Cancel due to authorization request cancellation
Cascade to SAQ instance
Preserve data for audit purposes (soft delete)
Notify all stakeholders



SAQ Expiration Handling (Hangfire):

csharp   public class SAQExpirationJob
   {
       [AutomaticRetry(Attempts = 0)]
       public async Task CheckExpiredSAQs()
       {
           var expiredSAQs = await _context.SAQInstances
               .Where(s => s.Status == "Shared" || s.Status == "InProgress")
               .Where(s => s.ExpiryDate < DateTime.UtcNow)
               .ToListAsync();
           
           foreach (var saq in expiredSAQs)
           {
               saq.Status = "Expired";
               
               // Notify establishment
               await _notificationService.NotifyEstablishment(
                   saq.RequestID,
                   "SAQExpired",
                   new { SAQInstanceID = saq.SAQInstanceID, OriginalExpiryDate = saq.ExpiryDate }
               );
               
               // Notify validation team
               await _notificationService.NotifyValidationTeam(
                   saq.ValidationTeamID,
                   "SAQExpired",
                   new { SAQInstanceID = saq.SAQInstanceID }
               );
               
               // Log audit entry
               await _auditService.LogEvent("SAQExpiration", saq.SAQInstanceID);
           }
           
           await _context.SaveChangesAsync();
       }
   }
   
   // Schedule in Startup.cs
   RecurringJob.AddOrUpdate<SAQExpirationJob>(
       "check-expired-saqs",
       job => job.CheckExpiredSAQs(),
       Cron.Hourly
   );
End-to-End Phase 2 Testing:

Selenium E2E test scenarios:

Federal Admin creates Question Bank → creates SAQ Template → approves template
Local Customs assigns team → generates SAQ → shares with establishment
Establishment completes SAQ → submits
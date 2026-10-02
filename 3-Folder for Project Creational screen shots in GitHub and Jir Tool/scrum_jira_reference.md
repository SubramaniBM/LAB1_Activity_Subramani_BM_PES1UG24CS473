# Scrum Project — Jira Reference & Document

## Subramani B M — PES1UG24CS473 — BPS#42

**Problem Statement #42:** Internal Microservice Catalog & Health Portal  
**Project Name:** Scrum_BPS#42  
**Project Key:** SBPS42  
**Project Type:** Software Development → SCRUM → Company-managed  

---

## Step-by-Step Instructions

### Step 1: Create Scrum Project
1. Open Jira → Click **"+"** next to Projects
2. Select **Software Development** → Choose **SCRUM** → Use template
3. Choose **Company-managed** project type
4. **Project Name:** `Scrum_BPS#42`
5. After creation, go to **Project Settings** → **Details** → Change **Key** to `SBPS42`
6. 📸 **Take Screenshot** of the empty SCRUM board

---

### Step 2: Add 5 FRs and 2 NFRs to the Board
(Same 7 requirements as Kanban — create as Tasks)

| # | Summary (Title) | Description | Priority |
|---|---|---|---|
| 1 | **FR-001: Health Monitoring** | The system shall ping microservice health endpoints at 30-second intervals and compute rolling 24-hour service availability percentages. | High |
| 2 | **FR-002: Catalog Management** | The system shall maintain a searchable catalog of all registered microservices, storing metadata including service name, owner team, version, repository URL, deployed environment(s), and API documentation link. | High |
| 3 | **FR-003: Dependency Mapping** | The system shall automatically discover and render an interactive dependency graph showing upstream and downstream relationships among all registered microservices. | High |
| 4 | **FR-004: Alerting & Notifications** | The system shall dispatch real-time downtime alert notifications (via email, Slack, and webhook) to the designated on-call contacts when the health checker detects an outage (3 consecutive failed probes). | Medium |
| 5 | **FR-005: API Documentation** | The system shall aggregate and display auto-generated API documentation (OpenAPI/Swagger specs) for each microservice, enabling developers to browse endpoints, request/response schemas, and example payloads. | Medium |
| 6 | **NFR-001: Performance & Scalability** | The service catalog dependency graph viewer must render interactive node architectures containing up to 200 services smoothly with pan, zoom, and click interactions completing within 2 seconds. | High |
| 7 | **NFR-002: Security & Compliance** | All communication shall be encrypted via TLS 1.2+, access requires enterprise SSO (OAuth 2.0/SAML), and health check credentials must be stored in an encrypted secrets vault. | High |

📸 **Take Screenshot** of board with all 7 items

---

### Step 3: Create 7 Epics
(Same Epics as Kanban project — create under Backlog panel)

| Epic # | Epic Name | Description | FR/NFR |
|--------|-----------|-------------|--------|
| **Epic 1** | Health Monitoring & Availability | Automated 30-second interval health probing with real-time dashboard and rolling availability. | FR-001 |
| **Epic 2** | Service Catalog Management | Register, update, search, and filter microservices in a centralized catalog. | FR-002 |
| **Epic 3** | Dependency Graph Visualization | Interactive upstream/downstream dependency graph with auto-discovery. | FR-003 |
| **Epic 4** | Alerting & Notification System | Multi-channel downtime alert dispatch (Email, Slack, Webhook). | FR-004 |
| **Epic 5** | API Documentation Aggregator | Aggregate and display OpenAPI/Swagger documentation per microservice. | FR-005 |
| **Epic 6** | Performance & Scalability | Graph rendering optimization for 200 nodes and 50 concurrent users. | NFR-001 |
| **Epic 7** | Security & Compliance | TLS 1.2+ encryption, enterprise SSO, and encrypted secrets vault. | NFR-002 |

Assign each requirement task to its corresponding Epic.
📸 **Take Screenshot** of Epics assigned to tasks

---

### Step 4: Create Stories for All 7 Requirements
(Same Stories as Kanban — create under each Epic)

Refer to the Kanban reference document for the full list of 18 Stories with their "As a… I want… So that…" descriptions.

📸 **Take Screenshot** of all Stories under their Epics

---

### Step 5: Add Tasks & Subtasks
(Same Tasks & Subtasks as Kanban — add as child issues to each Story)

Refer to the Kanban reference document for the full breakdown.

📸 **Take Screenshot** of Tasks and Subtasks expanded

---

### Step 6: Create Backlog & Assign Epics to Stories
📸 **Take Screenshot** of the backlog with Epic assignments

---

### Step 7: Assign Story Points (Fibonacci Scale)

| Story | Epic | Priority | Story Points |
|-------|------|----------|:---:|
| Story 1.1: Automated Health Probing | Epic 1 | High | 5 |
| Story 1.2: Real-Time Health Dashboard | Epic 1 | High | 3 |
| Story 1.3: Rolling 24-Hour Availability | Epic 1 | Medium | 3 |
| Story 2.1: Register New Microservice | Epic 2 | High | 5 |
| Story 2.2: Update Microservice Metadata | Epic 2 | High | 3 |
| Story 2.3: Search & Filter Catalog | Epic 2 | High | 3 |
| Story 3.1: Interactive Dependency Graph | Epic 3 | High | 5 |
| Story 3.2: Click-to-Navigate Nodes | Epic 3 | Medium | 2 |
| Story 4.1: Multi-Channel Downtime Alerts | Epic 4 | High | 5 |
| Story 4.2: Configure Alert Channels | Epic 4 | Medium | 2 |
| Story 5.1: Browse API Documentation | Epic 5 | High | 3 |
| Story 5.2: Upload OpenAPI Spec | Epic 5 | Medium | 2 |
| Story 6.1: Graph Rendering Optimization | Epic 6 | High | 3 |
| Story 6.2: Load Testing Under Peak Users | Epic 6 | Medium | 2 |
| Story 7.1: Enterprise SSO Authentication | Epic 7 | High | 5 |
| Story 7.2: TLS 1.2+ Encrypted Health Probes | Epic 7 | High | 3 |
| Story 7.3: Encrypted Secrets Vault | Epic 7 | High | 2 |

📸 **Take Screenshot** of Story Points assigned

---

### Step 8: Create Sprint 1 & Sprint 2

#### Sprint 1 (1-week duration) — 29 Story Points
Drag these into Sprint 1:

| Story | Epic | SP |
|-------|------|:---:|
| Story 1.1: Automated Health Probing | Epic 1 | 5 |
| Story 2.1: Register New Microservice | Epic 2 | 5 |
| Story 2.2: Update Microservice Metadata | Epic 2 | 3 |
| Story 2.3: Search & Filter Catalog | Epic 2 | 3 |
| Story 3.1: Interactive Dependency Graph | Epic 3 | 5 |
| Story 4.1: Multi-Channel Downtime Alerts | Epic 4 | 5 |
| Story 7.1: Enterprise SSO Authentication | Epic 7 | 3 |
| **Total** | | **29** |

1. Click **Start Sprint** → Set start date to today, end date = 1 week later
2. Move stories: **To Do → In Progress** (wait a few minutes) **→ Done**
3. 📸 **Take Screenshot** of Active Sprint board (with stories in To Do / In Progress / Done)
4. Click **Complete Sprint**

#### Sprint 2 (1-week duration) — 26 Story Points
Drag remaining stories into Sprint 2:

| Story | Epic | SP |
|-------|------|:---:|
| Story 1.2: Real-Time Health Dashboard | Epic 1 | 3 |
| Story 1.3: Rolling 24-Hour Availability | Epic 1 | 3 |
| Story 3.2: Click-to-Navigate Nodes | Epic 3 | 2 |
| Story 4.2: Configure Alert Channels | Epic 4 | 2 |
| Story 5.1: Browse API Documentation | Epic 5 | 3 |
| Story 5.2: Upload OpenAPI Spec | Epic 5 | 2 |
| Story 6.1: Graph Rendering Optimization | Epic 6 | 3 |
| Story 6.2: Load Testing Under Peak Users | Epic 6 | 2 |
| Story 7.2: TLS 1.2+ Encrypted Probes | Epic 7 | 3 |
| Story 7.3: Encrypted Secrets Vault | Epic 7 | 2 |
| **Total** | | **25** |

1. Start Sprint → Simulate → Complete Sprint
2. 📸 **Take Screenshot** of completed Sprint 2

---

### Step 9: Generate Burndown Chart
1. Go to **Reports** panel (next to Active Sprints)
2. Select **Burndown Chart**
3. 📸 **Take Screenshot** of the Burndown Chart

---

### Screenshots Checklist for Scrum.PDF

| # | Screenshot Required |
|---|---|
| 1 | SCRUM board creation |
| 2 | Board with 5 FRs & 2 NFRs |
| 3 | Epics created and assigned |
| 4 | Stories for all 7 requirements |
| 5 | Tasks & Subtasks expanded |
| 6 | Backlog with Epic assignments |
| 7 | Story Points assigned |
| 8 | Sprint 1 Active Sprint board |
| 9 | Sprint 2 Active Sprint board |
| 10 | Burndown Chart |

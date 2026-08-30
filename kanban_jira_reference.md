# Kanban Project — Jira Reference & Document

## Subramani B M — PES1UG24CS473 — BPS#42

**Problem Statement #42:** Internal Microservice Catalog & Health Portal  
**Project Name:** Kanban_BPS#42  
**Project Key:** KBPS42  
**Project Type:** Kanban  

---

## Step-by-Step Instructions

### Step 1: Create Kanban Project
1. Open Jira → Click **"+"** next to Projects
2. Select **Software Development** → Choose **Kanban** → Use template
3. Choose **Company-managed** project type
4. **Project Name:** `Kanban_BPS#42`
5. After creation, go to **Project Settings** (gear icon) → **Details** → Change **Key** to `KBPS42`
6. 📸 **Take Screenshot** of the empty board

---

### Step 2: Add 5 FRs and 2 NFRs to the Board
Create 7 board tasks (issues) — one for each requirement. Click **Create** → Type: **Task** for each:

| # | Summary (Title) | Description | Priority |
|---|---|---|---|
| 1 | **FR-001: Health Monitoring** | The system shall ping microservice health endpoints at 30-second intervals and compute rolling 24-hour service availability percentages. | High |
| 2 | **FR-002: Catalog Management** | The system shall maintain a searchable catalog of all registered microservices, storing metadata including service name, owner team, version, repository URL, deployed environment(s), and API documentation link. | High |
| 3 | **FR-003: Dependency Mapping** | The system shall automatically discover and render an interactive dependency graph showing upstream and downstream relationships among all registered microservices. | High |
| 4 | **FR-004: Alerting & Notifications** | The system shall dispatch real-time downtime alert notifications (via email, Slack, and webhook) to the designated on-call contacts when the health checker detects an outage (3 consecutive failed probes). | Medium |
| 5 | **FR-005: API Documentation** | The system shall aggregate and display auto-generated API documentation (OpenAPI/Swagger specs) for each microservice, enabling developers to browse endpoints, request/response schemas, and example payloads. | Medium |
| 6 | **NFR-001: Performance & Scalability** | The service catalog dependency graph viewer must render interactive node architectures containing up to 200 services smoothly with pan, zoom, and click interactions completing within 2 seconds. | High |
| 7 | **NFR-002: Security & Compliance** | All communication shall be encrypted via TLS 1.2+, access requires enterprise SSO (OAuth 2.0/SAML), and health check credentials must be stored in an encrypted secrets vault. | High |

📸 **Take Screenshot** of the board with all 7 items visible

---

### Step 3: Create Epics (7 Epics — one per Requirement)
Go to **Backlog** → Click **Create** → Type: **Epic** for each:

| Epic # | Epic Name | Description |
|--------|-----------|-------------|
| **Epic 1** | Health Monitoring & Availability | Implement automated 30-second interval health endpoint probing with rolling 24-hour availability calculation and real-time dashboard for all registered microservices. (FR-001) |
| **Epic 2** | Service Catalog Management | Enable DevOps engineers to register, update, search, and filter microservices in a centralized catalog storing metadata including name, owner, version, repo URL, environments, and API link. (FR-002) |
| **Epic 3** | Dependency Graph Visualization | Automatically discover and render an interactive upstream/downstream dependency graph for all registered microservices with click-to-navigate functionality. (FR-003) |
| **Epic 4** | Alerting & Notification System | Dispatch real-time multi-channel downtime alert notifications (Email, Slack, Webhook) to designated on-call contacts upon detecting outages (3 consecutive failed probes). (FR-004) |
| **Epic 5** | API Documentation Aggregator | Aggregate and display auto-generated API documentation (OpenAPI/Swagger specs) per microservice with endpoint browsing, schemas, and example payloads. (FR-005) |
| **Epic 6** | Performance & Scalability Optimization | Ensure the dependency graph viewer renders up to 200 services smoothly with pan/zoom/click interactions completing within 2 seconds under peak load (50 concurrent users). (NFR-001) |
| **Epic 7** | Security & Compliance Framework | Implement TLS 1.2+ encryption for all health probes, enterprise SSO authentication (OAuth 2.0/SAML), and encrypted secrets vault for health check credentials. (NFR-002) |

Assign each FR/NFR task to its corresponding Epic.

📸 **Take Screenshot** of board with Epics assigned to tasks

---

### Step 4: Create Stories for All 7 Requirements (Use Cases)
For each Epic, click the Epic → **Create work item** → Type: **Story**:

#### Epic 1: Health Monitoring — Stories

| Story | Summary | Description (As a… I want… So that…) | Priority |
|-------|---------|---------------------------------------|----------|
| **Story 1.1** | Automated Health Probing | As a DevOps Engineer, I want the system to automatically ping health endpoints every 30 seconds, so that I have continuous visibility into microservice status. | High |
| **Story 1.2** | Real-Time Health Dashboard | As a DevOps Engineer, I want to view a real-time health monitoring dashboard displaying live service status and response times, so that I can instantly assess system health. | High |
| **Story 1.3** | Rolling 24-Hour Availability | As a DevOps Engineer, I want the system to calculate rolling 24-hour availability percentages, so that I can track service reliability and meet SLA targets. | Medium |

#### Epic 2: Service Catalog — Stories

| Story | Summary | Description | Priority |
|-------|---------|-------------|----------|
| **Story 2.1** | Register New Microservice | As a DevOps Engineer, I want to register a new microservice by providing its name, owner team, version, and repository URL, so that it appears in the centralized catalog. | High |
| **Story 2.2** | Update Microservice Metadata | As a DevOps Engineer, I want to update existing microservice metadata (version, environment, owner), so that the catalog always reflects the current state. | High |
| **Story 2.3** | Search & Filter Catalog | As a System Architect, I want to search and filter the service catalog by name, team, environment, or tech stack, so that I can quickly find relevant microservices. | High |

#### Epic 3: Dependency Graph — Stories

| Story | Summary | Description | Priority |
|-------|---------|-------------|----------|
| **Story 3.1** | Interactive Dependency Graph | As a System Architect, I want to view an interactive dependency graph showing upstream/downstream relationships, so that I can understand the system topology. | High |
| **Story 3.2** | Click-to-Navigate Graph Nodes | As a System Architect, I want to click a graph node to navigate to that service's detail page, so that I can drill down from the graph view. | Medium |

#### Epic 4: Alerting & Notifications — Stories

| Story | Summary | Description | Priority |
|-------|---------|-------------|----------|
| **Story 4.1** | Multi-Channel Downtime Alerts | As a DevOps Engineer, I want the system to dispatch downtime alerts via Email, Slack, and Webhook when 3 consecutive probes fail, so that on-call personnel are notified. | High |
| **Story 4.2** | Configure Alert Channels | As a DevOps Engineer, I want to configure notification channels and on-call contacts per microservice, so that alerts reach the right team. | Medium |

#### Epic 5: API Documentation — Stories

| Story | Summary | Description | Priority |
|-------|---------|-------------|----------|
| **Story 5.1** | Browse API Documentation | As a Developer, I want to browse aggregated API documentation (endpoints, schemas, payloads) per microservice, so that I can integrate without consulting scattered docs. | High |
| **Story 5.2** | Upload OpenAPI Spec | As a DevOps Engineer, I want to upload or link an OpenAPI/Swagger spec during registration, so that API docs are auto-generated. | Medium |

#### Epic 6: Performance & Scalability — Stories

| Story | Summary | Description | Priority |
|-------|---------|-------------|----------|
| **Story 6.1** | Graph Rendering Optimization | As a System Architect, I want the dependency graph to render up to 200 service nodes within 2 seconds, so that I can explore complex architectures fluidly. | High |
| **Story 6.2** | Load Testing Under Peak Users | As a QA Engineer, I want the system to handle 50 concurrent users without performance degradation, so that peak-hour usage remains smooth. | Medium |

#### Epic 7: Security & Compliance — Stories

| Story | Summary | Description | Priority |
|-------|---------|-------------|----------|
| **Story 7.1** | Enterprise SSO Authentication | As a DevOps Engineer, I want to authenticate via enterprise SSO (OAuth 2.0/SAML), so that only authorized users access the portal. | High |
| **Story 7.2** | TLS 1.2+ Encrypted Health Probes | As a Security Engineer, I want all health probe communication encrypted via TLS 1.2+, so that credentials and health data are never exposed in plaintext. | High |
| **Story 7.3** | Encrypted Secrets Vault | As a DevOps Engineer, I want health check credentials stored in an encrypted secrets vault, so that sensitive authentication data is protected. | High |

📸 **Take Screenshot** of all Stories under their Epics

---

### Step 5: Add Tasks and Subtasks to All FRs and NFRs
For each Story, click the story → **Add child issue** → Type: **Subtask**:

#### FR-001 (Epic 1) — Tasks & Subtasks

**Story 1.1: Automated Health Probing**
- Task: Design health probe scheduler architecture
  - Subtask: Define probe interval configuration schema
  - Subtask: Implement HTTPS GET request module with TLS validation
- Task: Implement 30-second probe execution engine
  - Subtask: Build connection timeout handler (5 second threshold)
  - Subtask: Create probe result persistence layer

**Story 1.2: Real-Time Health Dashboard**
- Task: Design dashboard UI wireframe
  - Subtask: Create service status card component (Healthy/Down/Unknown)
  - Subtask: Implement live timestamp and response time display

**Story 1.3: Rolling 24-Hour Availability**
- Task: Implement availability percentage calculator
  - Subtask: Build time-series data aggregation pipeline
  - Subtask: Create availability trend chart visualization

#### FR-002 (Epic 2) — Tasks & Subtasks

**Story 2.1: Register New Microservice**
- Task: Design service registration form and API
  - Subtask: Create metadata input form (name, owner, version, repo URL)
  - Subtask: Implement server-side validation for required fields
- Task: Build catalog database schema
  - Subtask: Design microservice metadata table structure

**Story 2.2: Update Microservice Metadata**
- Task: Implement metadata update workflow
  - Subtask: Create edit form with pre-populated fields
  - Subtask: Add version history tracking

**Story 2.3: Search & Filter Catalog**
- Task: Build search and filter engine
  - Subtask: Implement full-text search across service names
  - Subtask: Add filter dropdowns for team, environment, tech stack

#### FR-003 (Epic 3) — Tasks & Subtasks

**Story 3.1: Interactive Dependency Graph**
- Task: Implement graph rendering engine
  - Subtask: Build force-directed layout algorithm for node positioning
  - Subtask: Implement pan, zoom, and drag interactions
- Task: Build dependency data API
  - Subtask: Create upstream/downstream relationship query endpoint

**Story 3.2: Click-to-Navigate Graph Nodes**
- Task: Add node click handler
  - Subtask: Implement navigation routing to service detail page

#### FR-004 (Epic 4) — Tasks & Subtasks

**Story 4.1: Multi-Channel Downtime Alerts**
- Task: Implement alert dispatch engine
  - Subtask: Build Email notification sender (SMTP integration)
  - Subtask: Build Slack webhook notification sender
  - Subtask: Build generic webhook notification sender
- Task: Implement 3-consecutive-failure detection logic
  - Subtask: Create failure counter with threshold trigger

**Story 4.2: Configure Alert Channels**
- Task: Build alert channel configuration UI
  - Subtask: Create channel selection form (Email, Slack, Webhook)
  - Subtask: Implement on-call contact assignment per microservice

#### FR-005 (Epic 5) — Tasks & Subtasks

**Story 5.1: Browse API Documentation**
- Task: Build API documentation viewer
  - Subtask: Implement OpenAPI spec parser and renderer
  - Subtask: Create endpoint browser with request/response schemas

**Story 5.2: Upload OpenAPI Spec**
- Task: Implement spec upload workflow
  - Subtask: Create file upload component for YAML/JSON specs
  - Subtask: Add URL linking for remote spec files

#### NFR-001 (Epic 6) — Tasks & Subtasks

**Story 6.1: Graph Rendering Optimization**
- Task: Optimize rendering pipeline
  - Subtask: Implement WebGL-based canvas rendering for large graphs
  - Subtask: Add virtual viewport culling for off-screen nodes

**Story 6.2: Load Testing Under Peak Users**
- Task: Design and execute load tests
  - Subtask: Create JMeter/k6 test scripts for 50 concurrent users
  - Subtask: Run benchmark tests and document results

#### NFR-002 (Epic 7) — Tasks & Subtasks

**Story 7.1: Enterprise SSO Authentication**
- Task: Implement OAuth 2.0 / SAML integration
  - Subtask: Configure SSO identity provider connection
  - Subtask: Implement token refresh and session management

**Story 7.2: TLS 1.2+ Encrypted Health Probes**
- Task: Enforce TLS in health probe module
  - Subtask: Configure minimum TLS version enforcement
  - Subtask: Implement certificate validation and rejection logic

**Story 7.3: Encrypted Secrets Vault**
- Task: Integrate secrets vault (HashiCorp Vault / AWS Secrets Manager)
  - Subtask: Implement credential retrieval API with caching
  - Subtask: Configure vault access policies and rotation schedules

📸 **Take Screenshot** of Stories with Tasks and Subtasks expanded

---

### Step 6: Create Backlog & Assign Epics
1. Go to **Backlog** panel
2. All Stories should be visible with their Epic labels
3. Ensure each backlog item has its Epic assigned (click story → set Epic link)
4. 📸 **Take Screenshot** of the full backlog with Epic assignments visible

---

### Screenshots Checklist for Kanban.PDF

| # | Screenshot Required | Description |
|---|---|---|
| 1 | Board creation | Empty Kanban board after project creation |
| 2 | Board with FRs & NFRs | All 7 requirements added as board tasks |
| 3 | Epics assigned | Epics created and assigned to board tasks |
| 4 | Stories created | All Stories visible under their Epics |
| 5 | Tasks & Subtasks | Expanded view showing tasks/subtasks for all requirements |
| 6 | Backlog with Epics | Full backlog panel with Epic assignments visible |

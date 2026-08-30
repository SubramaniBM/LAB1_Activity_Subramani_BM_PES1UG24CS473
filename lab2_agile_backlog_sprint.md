# Lab 2: Agile Backlog Creation & Sprint Simulation in Jira

## Problem Statement #42 — Internal Microservice Catalog & Health Portal

**Student Name:** Subramani B M &nbsp;|&nbsp; **SRN:** PES1UG24CS473 &nbsp;|&nbsp; **Section:** H  
**Course:** Software Engineering Lab 2 — Department of CSE, PES University  

---

## Jira Project Setup Reference

**Project Name:** MicroserviceCatalogPortal  
**Project Type:** Software Development → SCRUM → Company-managed  

---

## Epics (5 Epics mapped from Lab 1 Functional Requirements)

### Epic 1: Service Catalog Management
- **Description:** Enable DevOps engineers to register, update, search, and filter microservices in a centralized catalog storing metadata including service name, owner team, version, repository URL, deployed environment(s), and API documentation link. (Mapped from FR-002)

### Epic 2: Health Monitoring & Availability
- **Description:** Implement automated health endpoint probing at 30-second intervals with rolling 24-hour service availability percentage calculation for all registered microservices. (Mapped from FR-001)

### Epic 3: Dependency Graph Visualization
- **Description:** Automatically discover and render an interactive dependency graph showing upstream and downstream relationships among all registered microservices with click-to-navigate functionality. (Mapped from FR-003)

### Epic 4: Alerting & Notification System
- **Description:** Dispatch real-time multi-channel downtime alert notifications (Email, Slack, Webhook) to designated on-call contacts when the health checker detects an outage (3 consecutive failed probes). (Mapped from FR-004)

### Epic 5: API Documentation Aggregator
- **Description:** Aggregate and display auto-generated API documentation (OpenAPI/Swagger specs) for each microservice, enabling developers to browse endpoints, request/response schemas, and example payloads. (Mapped from FR-005)

---

## User Stories (15 User Stories in proper Agile format)

### Epic 1: Service Catalog Management — User Stories

**US-1.1: Register New Microservice**
- **Summary:** Register a new microservice in the catalog
- **Description:** As a DevOps Engineer, I want to register a new microservice by providing its name, owner team, version, and repository URL, so that it appears in the centralized catalog for discovery.
- **Priority:** High
- **Story Points:** 5

**US-1.2: Update Microservice Metadata**
- **Summary:** Update existing microservice metadata
- **Description:** As a DevOps Engineer, I want to update existing microservice metadata (version, environment, owner), so that the catalog always reflects the current state of the service.
- **Priority:** High
- **Story Points:** 3

**US-1.3: Search & Filter Service Catalog**
- **Summary:** Search and filter the service catalog
- **Description:** As a System Architect, I want to search and filter the service catalog by name, team, environment, or technology stack, so that I can quickly find relevant microservices.
- **Priority:** High
- **Story Points:** 3

**US-1.4: Validate Metadata Completeness**
- **Summary:** Validate metadata completeness on registration
- **Description:** As a DevOps Engineer, I want the system to validate metadata completeness upon registration, so that incomplete or invalid entries are rejected before being added to the catalog.
- **Priority:** Medium
- **Story Points:** 2

---

### Epic 2: Health Monitoring & Availability — User Stories

**US-2.1: Automated Health Probing**
- **Summary:** Automated health endpoint probing every 30 seconds
- **Description:** As a DevOps Engineer, I want the system to automatically ping health endpoints every 30 seconds, so that I have continuous visibility into microservice status.
- **Priority:** High
- **Story Points:** 5

**US-2.2: Real-Time Health Dashboard**
- **Summary:** View real-time health monitoring dashboard
- **Description:** As a DevOps Engineer, I want to view a real-time health monitoring dashboard displaying live service status, last-checked timestamps, and response times, so that I can instantly assess system health.
- **Priority:** High
- **Story Points:** 3

**US-2.3: Rolling 24-Hour Availability**
- **Summary:** Calculate rolling 24-hour availability percentages
- **Description:** As a DevOps Engineer, I want the system to calculate and display rolling 24-hour availability percentages, so that I can track service reliability over time and meet SLA targets.
- **Priority:** Medium
- **Story Points:** 3

**US-2.4: Custom Health Check Configuration**
- **Summary:** Configure custom health check intervals and timeouts
- **Description:** As a DevOps Engineer, I want to configure custom health check intervals and timeout thresholds per microservice, so that monitoring adapts to each service's requirements.
- **Priority:** Low
- **Story Points:** 2

---

### Epic 3: Dependency Graph Visualization — User Stories

**US-3.1: Interactive Dependency Graph**
- **Summary:** View interactive dependency graph of microservices
- **Description:** As a System Architect, I want to view an interactive dependency graph showing upstream and downstream relationships among microservices, so that I can understand the system topology.
- **Priority:** High
- **Story Points:** 5

**US-3.2: Click-to-Navigate Graph Nodes**
- **Summary:** Click graph node to navigate to service detail
- **Description:** As a System Architect, I want to click on a graph node to navigate to that service's detail page, so that I can drill down into specific services from the graph view.
- **Priority:** Medium
- **Story Points:** 2

**US-3.3: Auto-Discover Dependencies**
- **Summary:** Auto-discover and display new dependencies
- **Description:** As a System Architect, I want the graph to auto-discover and display new dependencies within 2 minutes of registration, so that the topology view stays current.
- **Priority:** Low
- **Story Points:** 1

---

### Epic 4: Alerting & Notification System — User Stories

**US-4.1: Multi-Channel Downtime Alerts**
- **Summary:** Dispatch downtime alerts via Email, Slack, and Webhook
- **Description:** As a DevOps Engineer, I want the system to dispatch downtime alerts via Email, Slack, and Webhook when 3 consecutive health probes fail, so that on-call personnel are notified immediately.
- **Priority:** High
- **Story Points:** 5

**US-4.2: Configure Notification Channels**
- **Summary:** Configure notification channels and on-call contacts
- **Description:** As a DevOps Engineer, I want to configure notification channels and on-call contacts per microservice, so that alerts reach the right team through their preferred channels.
- **Priority:** Medium
- **Story Points:** 2

**US-4.3: Service Recovery Notification**
- **Summary:** Receive recovery notification when service comes back up
- **Description:** As a DevOps Engineer, I want to receive a recovery notification when a previously down service becomes healthy again, so that I know when an incident has been resolved.
- **Priority:** Low
- **Story Points:** 1

---

### Epic 5: API Documentation Aggregator — User Stories

**US-5.1: Browse API Documentation**
- **Summary:** Browse aggregated API documentation per microservice
- **Description:** As a Developer, I want to browse aggregated API documentation (endpoints, request/response schemas, example payloads) for each microservice, so that I can integrate with services without consulting scattered docs.
- **Priority:** High
- **Story Points:** 3

**US-5.2: Upload OpenAPI Spec**
- **Summary:** Upload or link OpenAPI/Swagger spec during registration
- **Description:** As a DevOps Engineer, I want to upload or link an OpenAPI/Swagger spec during service registration, so that API documentation is auto-generated and browsable within 2 minutes.
- **Priority:** Medium
- **Story Points:** 2

---

## Sprint Plan

### Sprint 1 (1-week duration) — Target: 26 Story Points

| User Story | Epic | Priority | Story Points |
|-----------|------|----------|:---:|
| US-1.1: Register new microservice | Epic 1: Service Catalog Management | High | 5 |
| US-1.2: Update microservice metadata | Epic 1: Service Catalog Management | High | 3 |
| US-1.3: Search & filter catalog | Epic 1: Service Catalog Management | High | 3 |
| US-2.1: Automated health probing (30s) | Epic 2: Health Monitoring & Availability | High | 5 |
| US-2.2: Real-time health dashboard | Epic 2: Health Monitoring & Availability | High | 3 |
| US-3.1: Interactive dependency graph | Epic 3: Dependency Graph Visualization | High | 5 |
| US-4.1: Multi-channel downtime alerts | Epic 4: Alerting & Notification System | High | 2 |
| **Sprint 1 Total** | | | **26** |

### Sprint 2 (1-week duration) — Target: 21 Story Points

| User Story | Epic | Priority | Story Points |
|-----------|------|----------|:---:|
| US-4.1: Multi-channel alerts (continued) | Epic 4: Alerting & Notification System | High | 3 |
| US-5.1: Browse API documentation | Epic 5: API Documentation Aggregator | High | 3 |
| US-2.3: Rolling 24-hour availability | Epic 2: Health Monitoring & Availability | Medium | 3 |
| US-1.4: Validate metadata completeness | Epic 1: Service Catalog Management | Medium | 2 |
| US-4.2: Configure notification channels | Epic 4: Alerting & Notification System | Medium | 2 |
| US-5.2: Upload OpenAPI spec | Epic 5: API Documentation Aggregator | Medium | 2 |
| US-3.2: Click node → service detail | Epic 3: Dependency Graph Visualization | Medium | 2 |
| US-2.4: Custom health check intervals | Epic 2: Health Monitoring & Availability | Low | 2 |
| US-4.3: Recovery notification | Epic 4: Alerting & Notification System | Low | 1 |
| US-3.3: Auto-discover dependencies | Epic 3: Dependency Graph Visualization | Low | 1 |
| **Sprint 2 Total** | | | **21** |

---

## Reflection Questions

### 1. Did your estimations reflect the actual effort?

Yes, the Fibonacci-based story point estimates largely aligned with the simulated effort. High-complexity stories (US-1.1, US-2.1, US-3.1, US-4.1) at 5 points appropriately reflected their architectural significance and multi-component integration requirements. Supporting stories at 1–3 points matched their lower complexity. Sprint 1 carried 26 points compared to Sprint 2's 21 points, which in a real project would require velocity calibration after Sprint 1 to better balance capacity across iterations.

### 2. Was your backlog well-prioritized?

Yes. The backlog was structured following the MoSCoW (Must-have, Should-have, Could-have) prioritization principle. High-priority stories delivering core user value — service registration (US-1.1), health monitoring (US-2.1), dependency visualization (US-3.1), and downtime alerting (US-4.1) — were scheduled for Sprint 1, ensuring the minimum viable product was delivered first. Medium and Low-priority enhancement stories (custom intervals, recovery notifications, auto-discovery) were deferred to Sprint 2. This ensures the product backlog is ordered by user impact and business value.

### 3. How did your simulated sprint align with your plan?

The simulated sprint closely followed the plan. All High-priority stories in Sprint 1 were moved sequentially from To Do → In Progress → Done, reflecting realistic task progression where dependent stories were completed before independent ones. Sprint 2 completed the remaining backlog items without scope creep. Both sprints were completed within the 1-week timeboxed duration, demonstrating that the story point estimation and sprint capacity planning were well-calibrated.

### 4. What insights did the burndown chart give about your team's capacity?

The burndown chart revealed a steady, near-linear decline in remaining story points across both sprints, indicating well-distributed workload and consistent team velocity. Sprint 1's guideline (grey line) and actual remaining work (red line) tracked closely, suggesting accurate estimation. The slight difference between Sprint 1 (26 points) and Sprint 2 (21 points) totals reflects adaptive planning — using Sprint 1's actual velocity as input for Sprint 2's capacity, which is a core Agile principle. The chart confirmed no major estimation outliers or blockers occurred during execution.

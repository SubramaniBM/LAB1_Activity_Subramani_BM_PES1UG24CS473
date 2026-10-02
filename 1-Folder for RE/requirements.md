# Requirements Table & Requirements Traceability Matrix (RTM)

## Problem Statement #42 — Internal Microservice Catalog & Health Portal

**Student Name:** Subramani B M &nbsp;|&nbsp; **SRN:** PES1UG24CS473 &nbsp;|&nbsp; **Section:** H  
**Course:** Software Engineering Lab 1 — Department of CSE, PES University  

---

## 1. Functional Requirements (FR-001 to FR-005)

| ID | Type | Description | Priority | Acceptance Criteria | Rationale |
|:---|:---|:---|:---:|:---|:---|
| **FR-001** | Health Monitoring | The system shall ping microservice health endpoints at 30-second intervals and compute rolling 24-hour service availability percentages. | High | **Pass:** Downtime recorded and alert dispatched on 3 consecutive failed health probes.<br>**Fail:** Unreachable service marked healthy. | Continuous health monitoring is essential for ensuring service reliability and enabling rapid incident response in a microservice architecture. |
| **FR-002** | Catalog Management | The system shall maintain a searchable catalog of all registered microservices, storing metadata including service name, owner team, version, repository URL, deployed environment(s), and API documentation link. | High | **Pass:** A newly registered microservice appears in search results within 60 seconds and all metadata fields are accurately displayed.<br>**Fail:** A registered service is missing from the catalog or displays stale/incorrect metadata. | A centralized catalog gives DevOps engineers and system architects a single source of truth for discovering and understanding available microservices. |
| **FR-003** | Dependency Mapping | The system shall automatically discover and render an interactive dependency graph showing upstream and downstream relationships among all registered microservices. | High | **Pass:** Adding a dependency between two services is reflected in the graph within 2 minutes; clicking a node navigates to the service detail page.<br>**Fail:** A known dependency is absent from the graph, or the graph displays a dependency that does not exist. | Visualizing inter-service dependencies helps system architects identify critical paths, single points of failure, and the blast radius of potential outages. |
| **FR-004** | Alerting & Notifications | The system shall dispatch real-time downtime alert notifications (via email, Slack, and webhook) to the designated on-call contacts of a service when the health checker detects an outage (3 consecutive failed probes). | Medium | **Pass:** On-call contacts receive a notification on all configured channels within 60 seconds of the third consecutive failed probe.<br>**Fail:** An outage occurs and no notification is sent, or the notification is sent to the wrong contact. | Timely, multi-channel alerting ensures the right personnel are informed immediately, minimizing mean time to acknowledge (MTTA) and mean time to resolve (MTTR). |
| **FR-005** | API Documentation | The system shall aggregate and display auto-generated API documentation (OpenAPI / Swagger specs) for each microservice, enabling developers to browse endpoints, request/response schemas, and example payloads. | Medium | **Pass:** Uploading or linking an OpenAPI spec renders a browsable, accurate API reference page for the service within 2 minutes.<br>**Fail:** The rendered documentation is missing endpoints, shows incorrect schemas, or fails to render entirely. | Centralized API documentation reduces onboarding time for new developers and prevents integration errors caused by consulting outdated or scattered documentation. |

---

## 2. Non-Functional Requirements (NFR-001 & NFR-002)

| ID | Type | Description | Priority | Acceptance Criteria | Rationale |
|:---|:---|:---|:---:|:---|:---|
| **NFR-001** | Performance & Scalability | The service catalog dependency graph viewer must render interactive node architectures containing up to 200 services smoothly with pan, zoom, and click interactions completing within 2 seconds on a standard desktop browser. | High | **Pass:** Benchmarking tests confirm graph render time ≤ 2 seconds and interaction latency ≤ 200 ms under simulated peak load (50 concurrent users, 200-node graph).<br>**Fail:** Render time exceeds 2 seconds or UI becomes unresponsive during interaction. | A sluggish dependency graph undermines its usefulness; architects need fluid interaction to trace complex dependency chains during incident analysis and capacity planning. |
| **NFR-002** | Security & Compliance | All communication between the portal and microservice health endpoints shall be encrypted via TLS 1.2 or higher, and access to the portal shall require authentication via enterprise SSO (OAuth 2.0 / SAML). Health check credentials must be stored in an encrypted secrets vault. | High | **Pass:** Penetration testing confirms no plaintext credential exposure; unauthorized users are denied access; all health-check traffic uses TLS 1.2+.<br>**Fail:** Any credential is transmitted or stored in plaintext, or an unauthenticated user gains access to the portal. | The portal aggregates sensitive infrastructure data (service topology, health status, API specs). Unauthorized access could expose internal architecture to attackers, and unencrypted health probes could leak credentials. |

---

## 3. Requirements Traceability Matrix (RTM)

The Requirements Traceability Matrix correlates every system requirement (FR/NFR) to its associated UML Use Cases, Architectural Components, Verification Test Methods, and Implementation Status.

| Req ID | Requirement Description | Associated Use Cases | Architecture Component(s) | Test / Verification Method | Acceptance Verification Criteria | Status |
|:---|:---|:---|:---|:---|:---|:---:|
| **FR-001** | Automated 30s Health Probing & 24h Availability SLA | **UC-004:** Monitor Microservice Health & Availability | `Health Monitoring Service`, `TimescaleDB Subsystem`, `Target Microservices` | Automated periodic pinger synthetic test; simulated HTTP 503 outage | 3 consecutive failures trigger outage state; 24h availability percentage calculated dynamically | **Verified** |
| **FR-002** | Searchable Service Catalog & Metadata Registry | **UC-001:** Register / Update Microservice Metadata<br>**UC-002:** Search & Filter Service Catalog | `Catalog & Registry Service`, `PostgreSQL Subsystem`, `API Gateway & Auth` | API metadata validation test; Elasticsearch query indexing benchmark | Service discoverable in <60s; metadata schemas, owner tags, and repo URLs accurately indexed | **Verified** |
| **FR-003** | Interactive Upstream/Downstream Dependency Topology | **UC-003:** View Service Dependency Graph | `Dependency Mapping Engine`, `Neo4j Graph Database`, `API Gateway & Auth` | 200-node graph topology generation; cyclic dependency test | Graph renders within <2.0s SLA; node selection highlights blast radius and upstream callers | **Verified** |
| **FR-004** | Real-Time Multi-Channel Incident Alerting (<60s SLA) | **UC-004:** Monitor Health (Outage Trigger)<br>**UC-006:** Configure Alert Channels & On-Call | `Event Message Bus (RabbitMQ)`, `Alert & Notification Service`, `External Channels` | End-to-end incident dispatch test; webhook receipt timer | Alert dispatches to Slack, PagerDuty, and SMTP within 60s of 3rd failed probe | **Verified** |
| **FR-005** | Centralized OpenAPI / Swagger Documentation Aggregator | **UC-005:** Browse Aggregated API Documentation | `API Doc Aggregator Service`, `Redis Cache`, `API Gateway & Auth` | OpenAPI 3.0 JSON specification parsing test; dynamic endpoint mock runner | Swagger schema rendered in <2 minutes; request/response schemas and example payloads browsable | **Verified** |
| **NFR-001** | Sub-2.0s Interactive Graph Rendering for 200+ Nodes | **UC-003:** View Service Dependency Graph | `Dependency Mapping Engine`, `Neo4j Graph DB` | JMeter load test with 50 concurrent sessions querying 200-node topology | Render time ≤ 2.0s; interaction / pan-zoom latency ≤ 200ms | **Verified** |
| **NFR-002** | SSO Authentication (OAuth2/SAML) & Vault Secret Isolation | **All Use Cases** (UC-001 through UC-006) | `API Gateway & Auth Service`, `Enterprise Secrets Vault (HashiCorp)` | OWASP ZAP penetration test; TLS 1.2+ SSL cipher inspection; Vault token validation | Zero plaintext credentials; RBAC enforced on all routes; mTLS used for internal service traffic | **Verified** |

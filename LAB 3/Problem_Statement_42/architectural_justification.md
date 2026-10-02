# Architectural Pattern Selection & Component Modeling Justification

**Course:** Software Engineering Lab 3 — Component Modeling & Architectural Pattern Selection  
**Department:** Computer Science & Engineering, PES University  
**Student Name:** Subramani B M &nbsp;|&nbsp; **SRN:** PES1UG24CS473 &nbsp;|&nbsp; **Section:** H  
**Problem Statement #42:** Internal Microservice Catalog & Health Portal  

---

### Architecture Selection Statement
> **"We chose Microservices Architecture (Event-Driven with API Gateway) for the Internal Microservice Catalog & Health Portal System."**

---

### 1. Architectural Choice
We evaluated three principal architectural patterns for the Internal Microservice Catalog & Health Portal:
* **Layered Architecture:** Deemed unsuitable due to monolithic deployment coupling; high-frequency background health probes would compete for database and compute threads with user-facing interactive dependency graph rendering and catalog queries.
* **Client-Server Architecture:** Deemed insufficient because a centralized backend creates a single point of failure and bottleneck under 200+ concurrent service monitoring streams and multi-channel alerting.
* **Microservices Architecture (Selected):** Selected for its autonomous component lifecycles, fine-grained horizontal scalability, isolated failure domains, and event-driven decoupling between monitoring pingers and alerting dispatchers.

---

### 2. Two Specific Scenario-Related Reasons for Selection

1. **Decoupled Scaling & Workload Isolation for High-Frequency Health Probing (FR-001 vs. NFR-001):**  
   The system must ping hundreds of microservices at strict 30-second intervals and compute rolling 24-hour availability percentages (FR-001). Under peak load, continuous network polling and timeouts from degraded downstream services generate heavy, I/O-intensive workloads. In a microservices architecture, the **Health Monitoring & Periodic Pinger Service** scales independently and is completely isolated from the **Dependency Mapping & Graph Engine** and the **Catalog Management Service**. Consequently, probe network latency or transient service hangs never degrade the interactive rendering SLA of the 200-node dependency graph (NFR-001 < 2s).

2. **Autonomous Evolution & Fault Isolation in Alerting and Documentation Aggregation (FR-004 & FR-005):**  
   The portal integrates with heterogeneous third-party external channels (Slack Incoming Webhooks, PagerDuty Events API v2, SMTP) and dynamically ingests disparate OpenAPI/Swagger 3.0 schema definitions across dozens of developer teams. Isolating the **Alerting & Notification Dispatcher Service** and the **API Documentation Aggregator Service** into separate microservices prevents cascading failures: an upstream rate-limit on Slack or an invalid/corrupted Swagger schema uploaded by a team will never crash the core Service Registry or halt background health monitoring.

---

### 3. Security Advantage
* **Centralized API Gateway Enforcement & Encrypted Secrets Isolation (NFR-002):**  
  All incoming requests from DevOps Engineers and System Architects are terminated at an edge **API Gateway & Authentication Service** that strictly enforces enterprise Single Sign-On (SSO via OAuth 2.0 / SAML), TLS 1.2+ mutual encryption, and Role-Based Access Control (RBAC). Furthermore, health check probe credentials, service repository tokens, and webhook secrets are segregated into an internal **Enterprise Secrets Vault (HashiCorp Vault/KMS)** accessible only via mTLS by backend services. This ensures zero plaintext credential leakage and protects internal architectural topologies from unauthorized exposure.

---

### 4. Performance Benefit
* **Asynchronous Event-Driven Messaging & Specialized Polyglot Persistence (FR-003, FR-004, NFR-001):**  
  The architecture decouples outage detection from notification delivery using an **AMQP/RabbitMQ Event Broker** (`IAlertPublisher` $\rightarrow$ `IEventConsumer`), ensuring health probe loops complete instantaneously without blocking on external HTTP webhook delivery latency (guaranteeing alerts within 60s under FR-004). Moreover, the system leverages **Polyglot Persistence**: a dedicated Graph Database (**Neo4j**) executes sub-second recursive graph traversals across 200+ microservice dependency chains (easily achieving the < 2s render benchmark required by NFR-001), while **TimescaleDB** handles high-volume time-series telemetry and **Redis** caches active API documentation.

---

### 5. Component & Interface Specification Summary

| Component Name | Type / Layer | Provided Interfaces (Ball) | Required Interfaces (Socket) | Primary Responsibility |
|:---|:---|:---|:---|:---|
| **API Gateway & Auth Service** | Edge / Ingress | `IPortalGateway` (HTTPS/REST/JSON) | `ICatalogService`, `IHealthStatus`, `IDependencyGraph`, `IDocViewer`, `IVaultSecret` | TLS termination, SSO OAuth2/SAML validation, RBAC, and client request routing |
| **Catalog & Registry Service** | Core Domain | `ICatalogService` (gRPC / REST) | `JDBC/SQL` (Polyglot DB) | Searchable microservice registry, metadata management, and elastic indexing |
| **Health Monitoring Service** | Telemetry Core | `IHealthStatus` (REST / WebSocket) | `IHealthProbe` (HTTPS GET), `IAlertPublisher` (AMQP), `TimescaleDB Driver` | 30s automated health pings, rolling 24h availability calculation, outage detection |
| **Dependency Mapping Engine** | Graph Processing | `IDependencyGraph` (GraphQL / JSON) | `Bolt/Cypher` (Neo4j Graph DB), `ICatalogService` | Automated dependency discovery, interactive 200+ node graph generation (<2s SLA) |
| **Alert & Notification Service** | Notification Dispatch | `IAlertConfig` (REST) | `IEventConsumer` (AMQP), `INotificationChannel` (Slack/PagerDuty/SMTP) | Event-driven alert evaluation and guaranteed multi-channel dispatch within 60 seconds |
| **API Doc Aggregator Service** | Developer Portal | `IDocViewer` (OpenAPI UI / Redoc) | `ISpecFetcher` (Git/HTTP), `Redis Driver` | Ingests, parses, and validates OpenAPI 3.0 specs; serves interactive API sandboxes |

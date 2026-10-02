# Software Requirements Specification (SRS) & Work Breakdown Structure (WBS)

## Problem Statement #42 — Internal Microservice Catalog & Health Portal

**Student Name:** Subramani B M &nbsp;|&nbsp; **SRN:** PES1UG24CS473 &nbsp;|&nbsp; **Section:** H  
**Department:** Computer Science & Engineering, PES University  
**Course:** Software Engineering Lab — Individual Submission Deliverable  

---

## Part 1: Software Requirements Specification (SRS)

### 1. Introduction
#### 1.1 Purpose
This document provides the formal Software Requirements Specification (SRS) for the **Internal Microservice Catalog & Health Portal (Problem Statement #42)**. It defines the system's external interfaces, functional behaviors, performance thresholds, and operational constraints for development, quality assurance, and deployment.

#### 1.2 Document Conventions & Scope
- Requirements are prioritized as **High** or **Medium**.
- All interfaces adhere to UML 2.5 component modeling standards.
- Scope encompasses automated 30-second health polling across 200+ microservices, dynamic dependency mapping with sub-2.0s render latency, centralized OpenAPI specification aggregation, and multi-channel downtime alerting.

### 2. Overall System Description
#### 2.1 Product Perspective & Context
The portal functions as an internal developer platform (IDP) and operational control plane. It integrates with enterprise infrastructure including:
- **Target Monitored Services:** Exposing standard `/health`, `/metrics`, and `/swagger.json` endpoints.
- **Enterprise Secrets Vault:** HashiCorp Vault for mTLS certificates, tokens, and encrypted probe credentials.
- **External Notification Endpoints:** Slack incoming webhooks, PagerDuty Events API v2, and SMTP servers.

#### 2.2 User Classes and Characteristics
1. **DevOps Engineers (Primary Operators):** Responsible for service uptime, health threshold configuration, on-call alert escalation policies, and incident mitigation.
2. **System Architects (Topology Leads):** Responsible for inter-service dependency governance, blast radius assessment, API schema deprecation tracking, and capacity planning.

---

### 3. Specific Functional Requirements (FR)

| Req ID | Requirement Title | Detailed Specification | Acceptance Criteria |
|:---|:---|:---|:---|
| **FR-001** | Automated Health Monitoring | The system pings microservice health endpoints at 30-second intervals and computes rolling 24-hour service availability percentages. | **Pass:** Outage recorded and alert triggered on 3 consecutive failed probes.<br>**Fail:** Downed service marked healthy. |
| **FR-002** | Searchable Service Catalog | The system maintains a centralized, indexed registry of all microservices, storing service name, owner team, version, repo URL, deployed environments, and API documentation link. | **Pass:** Newly registered service indexed and discoverable in <60 seconds.<br>**Fail:** Service missing or displaying stale metadata. |
| **FR-003** | Interactive Dependency Mapping | The system discovers and renders an interactive directed graph visualizing upstream and downstream relationships for up to 200+ microservices. | **Pass:** Graph updates within 2 minutes of schema change; blast radius visualizer active.<br>**Fail:** Missing edges or unrendered graph. |
| **FR-004** | Real-Time Downtime Alerting | The system dispatches multi-channel downtime alerts (Slack, PagerDuty, SMTP) within 60 seconds of outage detection to designated on-call teams. | **Pass:** Notifications delivered across all channels in <60s.<br>**Fail:** Missed alert or incorrect recipient. |
| **FR-005** | API Documentation Aggregator | The system ingests and displays OpenAPI 3.0 / Swagger specifications with an interactive API test runner and schema explorer. | **Pass:** Specification rendered in <2 minutes with executable mock runner.<br>**Fail:** Spec ingestion failure or invalid schemas. |

---

### 4. Non-Functional Requirements (NFR)

| Req ID | Category | Metric / Specification | Verification Standard |
|:---|:---|:---|:---|
| **NFR-001** | Performance & Scalability | The dependency graph viewer must render up to 200 nodes smoothly with pan, zoom, and click interactions completing within **2.0 seconds** on standard desktop browsers under 50 concurrent users. | JMeter load test verifying render latency ≤ 2.0s and interaction response ≤ 200ms. |
| **NFR-002** | Security & Compliance | Mandatory TLS 1.2+ encryption on all external and internal ingress routes. Enterprise SSO (OAuth 2.0 / SAML) authentication. All credentials stored in HashiCorp Vault. | OWASP ZAP automated scan; zero plaintext credentials; RBAC validation on all endpoints. |

---

## Part 2: Work Breakdown Structure (WBS)

### 1. WBS Hierarchy (Level 1 to Level 4)

```
1.0 Internal Microservice Catalog & Health Portal (Problem Statement #42)
├── 1.1 Ingress & Security Subsystem (API Gateway & Vault)
│   ├── 1.1.1 OAuth 2.0 / SAML SSO Authentication Integration
│   ├── 1.1.2 Role-Based Access Control (RBAC) Enforcement Engine
│   └── 1.1.3 HashiCorp Vault Secrets Management & Dynamic Lease Rotator
├── 1.2 Service Catalog & Metadata Subsystem
│   ├── 1.2.1 Service Registration & Schema Validation API (gRPC / REST)
│   ├── 1.2.2 PostgreSQL Metadata Storage & Audit History Schema
│   └── 1.2.3 Elasticsearch Full-Text Query & Filter Indexer
├── 1.3 Health Monitoring & Probing Subsystem
│   ├── 1.3.1 Async Multi-Threaded HTTP/gRPC Pinger Engine (30s Polling Loop)
│   ├── 1.3.2 TimescaleDB 24h Rolling Availability Metric Aggregator
│   └── 1.3.3 Consecutive Failure Detector & Outage Event Generator
├── 1.4 Dependency Mapping & Topology Subsystem
│   ├── 1.4.1 Neo4j Graph Database Driver & Cypher Query Engine
│   ├── 1.4.2 Interactive 200+ Node Canvas Renderer (<2.0s SLA)
│   └── 1.4.3 Cascading Outage Blast Radius Calculation Module
├── 1.5 Asynchronous Eventing & Multi-Channel Alerting Subsystem
│   ├── 1.5.1 RabbitMQ AMQP Outage Event Exchange & Dead-Letter Queue
│   ├── 1.5.2 On-Call Routing Matrix & Policy Evaluator
│   └── 1.5.3 Dispatch Adapters: Slack Webhook, PagerDuty Events v2, Corporate SMTP
├── 1.6 API Documentation Aggregation Subsystem
│   ├── 1.6.1 OpenAPI 3.0 / Swagger JSON Ingestion Pipeline
│   ├── 1.6.2 Redis In-Memory Spec Caching Layer
│   └── 1.6.3 Interactive Redoc / Swagger UI Mock Sandbox Runner
└── 1.7 Verification, Integration & Deployment
    ├── 1.7.1 End-to-End System Integration Testing & SLA Benchmarking
    ├── 1.7.2 Docker & Kubernetes Container Deployment Manifests
    └── 1.7.3 CI/CD GitHub Actions Pipeline Configuration
```

---

### 2. WBS Work Package Dictionary & Jira Issue Mapping

| WBS Code | Work Package / Task Title | Jira Key | Estimated Story Points | Dependencies | Core Deliverable |
|:---|:---|:---:|:---:|:---:|:---|
| **1.1.1** | API Gateway SSO / OAuth2 Auth | `SBP42-1` | 5 SP | None | Ingress auth filter terminating TLS 1.2+ and verifying JWT tokens. |
| **1.1.3** | HashiCorp Vault Secrets Storage | `SBP42-2` | 3 SP | 1.1.1 | Secure credential client isolating Slack tokens and probe credentials. |
| **1.2.1** | Service Registration REST API | `KBPS42-1` | 5 SP | 1.1.1 | CRUD endpoints for service metadata onboarding and validation. |
| **1.2.2** | PostgreSQL Catalog Schema Setup | `KBPS42-2` | 3 SP | 1.2.1 | Relational database schema with audit tables and owner foreign keys. |
| **1.3.1** | 30s Health Pinger Engine | `SBP42-3` | 8 SP | 1.1.3 | High-concurrency worker polling 200+ endpoints every 30 seconds. |
| **1.3.2** | TimescaleDB Time-Series Metrics | `SBP42-4` | 5 SP | 1.3.1 | Hypertable storing timestamped probe latency and uptime percentages. |
| **1.4.1** | Neo4j Graph Topology Modeler | `SBP42-5` | 8 SP | 1.2.2 | Directed graph data store connecting upstream callers to downstream targets. |
| **1.4.2** | Sub-2.0s Graph UI Renderer | `SBP42-6` | 13 SP | 1.4.1 | Optimized front-end canvas fulfilling NFR-001 render SLA. |
| **1.5.1** | RabbitMQ Event Bus Integration | `SBP42-7` | 5 SP | 1.3.1 | AMQP topic exchange `outage.detected` buffering incident messages. |
| **1.5.3** | Slack & PagerDuty Alert Dispatcher | `KBPS42-5` | 5 SP | 1.5.1 | Multi-channel incident dispatcher satisfying <60s delivery SLA. |
| **1.6.1** | OpenAPI 3.0 Ingestion Pipeline | `KBPS42-6` | 5 SP | 1.2.1 | Auto-fetch parser converting Swagger JSON into interactive docs. |
| **1.7.1** | SLA Benchmarking & Regression Testing | `SBP42-8` | 8 SP | All | Comprehensive verification report validating all FRs, NFRs, and RTM criteria. |

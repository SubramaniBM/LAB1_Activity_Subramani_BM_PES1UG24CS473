# Use-Case Flow Specification

## Problem Statement #42 — Internal Microservice Catalog & Health Portal

**Student Name:** Subramani B M &nbsp;|&nbsp; **SRN:** PES1UG24CS473 &nbsp;|&nbsp; **Section:** H  
**Course:** Software Engineering Lab 1 — Department of CSE, PES University  

---

### Use Case: Monitor Service Health (UC-004 / FR-001)

| Field | Detail |
|-------|--------|
| **Use-Case ID** | UC-004 |
| **Use-Case Name** | Monitor Service Health & Availability |
| **Primary Actor** | DevOps Engineer |
| **Supporting Actor** | Notification Service (External System) |
| **Related Requirements** | FR-001, FR-004, NFR-002 |
| **Description** | The system continuously pings registered microservice health endpoints at configurable intervals (default 30 s), computes rolling 24-hour availability, and dispatches downtime alerts when an outage is detected. |

---

### Preconditions

1. The DevOps Engineer is authenticated via enterprise SSO (OAuth 2.0 / SAML).
2. At least one microservice is registered in the catalog with a valid HTTPS health-check endpoint URL.
3. Alert notification channels (Email, Slack, Webhook) have been configured for the microservice's on-call contacts.

### Postconditions

1. The health status of each monitored microservice is updated and visible on the portal dashboard in real-time.
2. Rolling 24-hour availability percentages are recalculated and displayed.
3. If an outage was detected, a downtime event is recorded in the system's incident log and alert notifications have been dispatched.

---

### Main Success Scenario

| Step | Actor / System | Action |
|------|---------------|--------|
| 1 | **DevOps Engineer** | Navigates to the Health Monitoring dashboard and selects a microservice (or service group) to monitor. |
| 2 | **System** | Validates the engineer's SSO session. *(«include» Authenticate via Enterprise SSO)* |
| 3 | **System** | Retrieves the health-check endpoint URL and configured ping interval (default 30 s) for the selected microservice(s) from the catalog. |
| 4 | **System** | Sends an HTTPS health probe (GET request over TLS 1.2+) to each microservice's health endpoint. |
| 5 | **System** | Receives a `200 OK` response within the timeout window (default 5 s). Records the probe result as **Healthy**. |
| 6 | **System** | Updates the microservice's status on the dashboard to **Healthy** with the timestamp of the last successful probe. |
| 7 | **System** | Recalculates and displays the rolling 24-hour availability percentage for the microservice. |
| 8 | **System** | Waits for the configured interval (default 30 s) and returns to **Step 4** for the next probe cycle. |
| 9 | **DevOps Engineer** | Views real-time health status, availability trends, and historical uptime data on the dashboard. |

---

### Alternate Flow — Outage Detected (3 Consecutive Failed Probes)

| Step | Actor / System | Action |
|------|---------------|--------|
| 5a | **System** | The health probe fails (non-200 response, timeout, or connection error). The system records the probe result as **Failed** and increments the consecutive-failure counter for the microservice. |
| 5b | **System** | The system repeats the health probe at the next interval. If the probe succeeds, the consecutive-failure counter is reset to 0 and the flow returns to **Step 6** of the Main Success Scenario. |
| 5c | **System** | If 3 consecutive probes fail, the system marks the microservice status as **Down** and records a downtime event in the incident log with the timestamp of the first failed probe. |
| 5d | **System** | *(«extend» Dispatch Downtime Alert)* The system dispatches alert notifications to the microservice's on-call contacts via all configured channels (email, Slack, webhook). |
| 5e | **Notification Service** | Delivers the alert messages to the designated recipients. |
| 5f | **DevOps Engineer** | Receives the downtime alert and navigates to the dashboard to view the incident details, dependency impact, and logs. |
| 5g | **System** | Continues probing at the configured interval. When a probe succeeds, the system marks the microservice as **Healthy**, records the recovery timestamp, calculates total downtime duration, and sends a **Recovery** notification. The flow returns to **Step 6** of the Main Success Scenario. |

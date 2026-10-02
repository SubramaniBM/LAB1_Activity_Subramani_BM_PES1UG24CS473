# Exception Flow Specification

## Problem Statement #42 — Internal Microservice Catalog & Health Portal

**Student Name:** Subramani B M &nbsp;|&nbsp; **SRN:** PES1UG24CS473 &nbsp;|&nbsp; **Section:** H  
**Course:** Software Engineering Lab 1 — Department of CSE, PES University  

---

### Overview & Purpose

This document specifies the **Exception Flows** for the core use case **UC-004: Monitor Microservice Health & Availability** and related portal operations. Exception flows detail unexpected error conditions, fault-handling logic, automated recovery actions, and system fallbacks that prevent system failure and data inconsistency.

---

### Exception Flows for UC-004 (Monitor Service Health)

#### EF-001: Health Probe Network Timeout / Unreachable Host

| Field | Detail |
|-------|--------|
| **Exception ID** | **EF-001** |
| **Trigger Step** | Step 4 of Main Scenario (Sending HTTPS health probe) |
| **Error Condition** | Target microservice endpoint does not respond within timeout window (default 5 s) or DNS resolution fails (`ETIMEDOUT` / `ENOTFOUND`). |
| **System Action** | 1. System logs connection timeout event with error code and target URI.<br>2. Records probe result as **Failed (Timeout)** and increments consecutive failure counter.<br>3. Does not immediately mark service down until threshold (3 consecutive failures) is breached.<br>4. Schedules next probe cycle at standard interval. |
| **Postcondition** | Probe attempt logged; consecutive failure counter updated; monitoring loop continues uninterrupted. |

---

#### EF-002: Notification Service Gateway Failure / Delivery Rejection

| Field | Detail |
|-------|--------|
| **Exception ID** | **EF-002** |
| **Trigger Step** | Step 5d of Alternate Flow (Dispatching downtime alert via «extend» UC-009) |
| **Error Condition** | External Notification Service (Slack webhook, SMTP server, or PagerDuty API) returns `5xx` error, `429 Rate Limited`, or network connection drops. |
| **System Action** | 1. System catches delivery exception and places alert payload into a persistent retry queue with exponential backoff (retry at 15 s, 30 s, 60 s).<br>2. Dispatches fallback alert to secondary notification channel (e.g., fallback email channel if Slack fails).<br>3. Logs notification delivery failure in portal system audit log with severity `CRITICAL`. |
| **Postcondition** | Alert queued for retry; fallback channel notified; incident recorded in portal dashboard with notification delivery warning badge. |

---

#### EF-003: Endpoint SSL/TLS Certificate Expiration or Handshake Failure

| Field | Detail |
|-------|--------|
| **Exception ID** | **EF-003** |
| **Trigger Step** | Step 4 of Main Scenario (HTTPS probe over TLS 1.2+) |
| **Error Condition** | Target microservice presents an expired, self-signed, or untrusted SSL/TLS certificate during TLS handshake (`CERT_HAS_EXPIRED` / `DEPTH_ZERO_SELF_SIGNED_CERT`). |
| **System Action** | 1. System rejects unencrypted/insecure connection in compliance with **NFR-002**.<br>2. Marks probe as **Failed (Security/TLS Violation)** and flags service metadata.<br>3. Sends dedicated **Security Warning Alert** to service owner and DevOps team.<br>4. Displays "TLS Certificate Error" on health monitoring dashboard. |
| **Postcondition** | Security exception logged; security alert dispatched; service marked with security warning status without exposing plaintext traffic. |

---

#### EF-004: Secrets Vault Unreachable for Endpoint Authentication

| Field | Detail |
|-------|--------|
| **Exception ID** | **EF-004** |
| **Trigger Step** | Step 3 of Main Scenario (Retrieving health-check credentials from vault) |
| **Error Condition** | Internal secrets vault (HashiCorp Vault / AWS Secrets Manager) is unreachable or token expired when fetching auth headers for probe. |
| **System Action** | 1. System falls back to short-lived in-memory encrypted cached credential if available (TTL < 5 min).<br>2. If cache miss occurs, pauses authenticated probes for affected service to prevent false downtime alerts caused by portal infrastructure issues.<br>3. Emits `PORTAL_INFRA_ERROR` alert to portal administrators. |
| **Postcondition** | Service is marked as **Status Unknown (Vault Unreachable)** rather than **Down**; administrator alerted. |

---

#### EF-005: Enterprise SSO Token Expiry During Monitoring Dashboard Session

| Field | Detail |
|-------|--------|
| **Exception ID** | **EF-005** |
| **Trigger Step** | Step 2 of Main Scenario («include» Authenticate via Enterprise SSO) |
| **Error Condition** | DevOps Engineer's OAuth 2.0 / SAML session token expires while actively viewing live health metrics. |
| **System Action** | 1. Background pinger continues running on server without interruption.<br>2. Dashboard UI attempts transparent silent token refresh using refresh token.<br>3. If refresh token is expired/revoked, preserves current dashboard view state in `sessionStorage` and prompts user with SSO re-authentication modal.<br>4. Upon re-authentication, automatically restores dashboard state without reload. |
| **Postcondition** | Secure session re-established without data loss; unauthenticated access prevented (satisfying **NFR-002**). |

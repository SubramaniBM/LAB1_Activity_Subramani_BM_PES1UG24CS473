# Bug Tracking Project — Jira Reference & Document

## Subramani B M — PES1UG24CS473 — BPS#42

**Problem Statement #42:** Internal Microservice Catalog & Health Portal  
**Project Name:** BugTracker_BPS#42  
**Project Key:** BTBPS42  
**Project Type:** Bug Tracking  

---

## Step-by-Step Instructions

### Step 1: Create Bug Tracking Project
1. Open Jira → Click **"+"** next to Projects
2. Select **Bug Tracking** template
3. Choose **Company-managed** project type
4. **Project Name:** `BugTracker_BPS#42`
5. 📸 **Take Screenshot** of the Bug Tracker board

---

### Step 2: Report Bugs
Create the following bugs. Click **Create** → Type: **Bug** for each:

#### Bug 1: Health Probe Returns False Healthy Status
| Field | Value |
|-------|-------|
| **Summary** | Health probe returns "Healthy" status for unreachable microservice |
| **Description** | When a microservice endpoint is completely unreachable (connection refused), the health monitoring system incorrectly marks the service as "Healthy" instead of "Down". This occurs when the probe timeout handler fails to propagate the connection error to the status updater. |
| **Priority** | Highest |
| **Severity** | Critical |
| **Steps to Reproduce** | 1. Register a microservice with a valid health endpoint URL. 2. Shut down the microservice completely. 3. Wait for the next 30-second probe cycle. 4. Observe the health dashboard. |
| **Expected Result** | Service status should show "Down" with a failed probe timestamp. |
| **Actual Result** | Service status remains "Healthy" despite the endpoint being unreachable. |
| **Component** | Health Monitoring (FR-001) |

---

#### Bug 2: Duplicate Microservice Registration Allowed
| Field | Value |
|-------|-------|
| **Summary** | System allows registering duplicate microservices with identical names and URLs |
| **Description** | The service catalog allows registering two microservices with the exact same name and repository URL. The metadata validation does not check for uniqueness constraints, leading to duplicate entries in the catalog and confusing search results. |
| **Priority** | High |
| **Severity** | Major |
| **Steps to Reproduce** | 1. Register microservice "auth-service" with repo URL "https://github.com/org/auth-service". 2. Register another microservice with the same name and URL. 3. Search for "auth-service" in the catalog. |
| **Expected Result** | System should reject the second registration with a "Duplicate service" error. |
| **Actual Result** | Both entries are created, and search returns two identical results. |
| **Component** | Service Catalog (FR-002) |

---

#### Bug 3: Dependency Graph Shows Stale Edges After Service Deletion
| Field | Value |
|-------|-------|
| **Summary** | Dependency graph displays edges to deleted microservices |
| **Description** | When a microservice is deregistered from the catalog, the dependency graph continues to display edges (relationships) pointing to the now-deleted service node. The graph does not update automatically and shows a "ghost node" with no service detail page. |
| **Priority** | High |
| **Severity** | Major |
| **Steps to Reproduce** | 1. Register Service A and Service B with a dependency A → B. 2. Delete Service B from the catalog. 3. Open the dependency graph viewer. |
| **Expected Result** | Service B node and the A → B edge should be removed from the graph. |
| **Actual Result** | Service B appears as a broken node with the dependency edge still visible. |
| **Component** | Dependency Graph (FR-003) |

---

#### Bug 4: Slack Notification Not Delivered When Webhook URL Contains Special Characters
| Field | Value |
|-------|-------|
| **Summary** | Slack downtime alert fails when webhook URL contains encoded characters |
| **Description** | When configuring a Slack notification channel, if the webhook URL contains URL-encoded characters (e.g., `%2F` for `/`), the alert dispatcher fails to deliver the notification and silently drops the alert without logging an error or triggering a fallback channel. |
| **Priority** | Medium |
| **Severity** | Major |
| **Steps to Reproduce** | 1. Configure a Slack webhook with URL containing encoded characters. 2. Trigger an outage (3 consecutive failed probes). 3. Check Slack channel for alert. |
| **Expected Result** | Alert should be delivered to Slack, or a fallback channel should be notified. |
| **Actual Result** | No Slack notification is sent. No error is logged. No fallback alert is triggered. |
| **Component** | Alerting (FR-004) |

---

#### Bug 5: OpenAPI Spec Upload Fails for YAML Files Larger Than 2MB
| Field | Value |
|-------|-------|
| **Summary** | API documentation upload rejects valid OpenAPI YAML files exceeding 2MB |
| **Description** | When uploading an OpenAPI/Swagger specification file in YAML format that is larger than 2MB, the system returns a generic "Upload Failed" error without indicating the file size limitation. Large enterprise APIs with extensive endpoint documentation regularly exceed this threshold. |
| **Priority** | Medium |
| **Severity** | Minor |
| **Steps to Reproduce** | 1. Prepare a valid OpenAPI 3.0 YAML spec file (~3MB). 2. Navigate to service registration → Upload OpenAPI Spec. 3. Select the file and click Upload. |
| **Expected Result** | File should upload successfully and API docs should render within 2 minutes. |
| **Actual Result** | Upload fails with generic error "Upload Failed. Please try again." |
| **Component** | API Documentation (FR-005) |

---

#### Bug 6: Graph Viewer Freezes When Rendering 150+ Service Nodes
| Field | Value |
|-------|-------|
| **Summary** | Dependency graph UI becomes unresponsive with 150+ service nodes |
| **Description** | The interactive dependency graph viewer freezes (no pan/zoom/click response) when rendering architectures with more than 150 microservice nodes. The browser tab shows high CPU usage and the graph takes over 10 seconds to render, violating the 2-second render time SLA defined in NFR-001. |
| **Priority** | High |
| **Severity** | Critical |
| **Steps to Reproduce** | 1. Register 150+ microservices with inter-service dependencies. 2. Open the dependency graph viewer. 3. Attempt to pan, zoom, or click any node. |
| **Expected Result** | Graph renders within 2 seconds and interactions complete within 200ms. |
| **Actual Result** | Graph takes 10+ seconds to render and UI is completely unresponsive. |
| **Component** | Performance (NFR-001) |

---

#### Bug 7: SSO Session Token Not Invalidated on Logout
| Field | Value |
|-------|-------|
| **Summary** | OAuth 2.0 session token remains valid after user logs out of the portal |
| **Description** | After a DevOps Engineer logs out of the portal, their OAuth 2.0 session token is not invalidated on the server side. If the token is captured (e.g., from browser storage), it can still be used to make authenticated API requests, violating the security requirements defined in NFR-002. |
| **Priority** | Highest |
| **Severity** | Critical |
| **Steps to Reproduce** | 1. Log into the portal via Enterprise SSO. 2. Copy the OAuth token from browser dev tools. 3. Click Logout. 4. Use the copied token to make an API request (e.g., GET /api/services). |
| **Expected Result** | API request should return 401 Unauthorized after logout. |
| **Actual Result** | API request succeeds with 200 OK, returning service data. |
| **Component** | Security (NFR-002) |

---

📸 **Take Screenshot** of all 7 Bugs reported in the Bug Tracker board

---

### Screenshots Checklist for BugReport.PDF

| # | Screenshot Required | Description |
|---|---|---|
| 1 | Bug Tracker board creation | Empty Bug Tracker project after creation |
| 2 | All Bugs reported | Board view showing all 7 bugs with priority and status |
| 3 | Bug detail view (optional) | Expanded view of at least 1-2 bugs showing full description |

# Problem Statement #42 — Internal Microservice Catalog & Health Portal

**Course:** Software Engineering Lab — Requirements Engineering, UML Modelling & Agile Jira Workspaces  
**Department:** Dept. of CSE, PES University  
**Student Name:** Subramani B M  
**SRN:** PES1UG24CS473  
**Section:** H  
**Domain:** Developer Tools & IT Operations  
**Target Stakeholders / Actors:** DevOps Engineer, System Architect  

---

## Problem Context & Overview

An enterprise developer portal mapping microservice dependencies, aggregating API documentation, and running automated periodic health check pingers with downtime alerts.

---

## Deliverables Summary

### 📂 Lab 1: Requirements Engineering & UML Use-Case Modelling

| # | Deliverable | Format | File Link |
|---|---|---|---|
| **0** | **Original Problem Statement** | PDF | [42_SE_Lab1_SE_Problem_Statements.pdf](42_SE_Lab1_SE_Problem_Statements.pdf) |
| **1** | **Complete Requirements Table** (FR-001 to FR-005, NFR-001 & NFR-002) with ID, Type, Description, Priority, Acceptance Criteria, and Rationale | Markdown & PDF | [requirements.md](requirements.md)<br>[requirements.pdf](requirements.pdf) *(1-Page Formatted PDF)* |
| **2** | **UML Use-Case Diagram (Primary System)** (Actors, Use Cases, System Boundary, `«include»` & `«extend»` relationships) | draw.io + StarUML + PNG | [use_case_diagram.drawio](use_case_diagram.drawio) (draw.io)<br>[use_case_diagram.mdj](use_case_diagram.mdj) (StarUML)<br>[use_case_diagram.png](use_case_diagram.png) (Preview) |
| **3** | **Alternate Flow UML Use-Case Diagram** (Outage Detection, Multi-Channel Alerting & Auto-Recovery Lifecycle) | draw.io + StarUML + PNG | [alternate_flow_use_case_diagram.drawio](alternate_flow_use_case_diagram.drawio) (draw.io)<br>[alternate_flow_use_case_diagram.mdj](alternate_flow_use_case_diagram.mdj) (StarUML)<br>[alternate_flow_use_case_diagram.png](alternate_flow_use_case_diagram.png) (Preview) |
| **4** | **Use-Case Flow Specification** (1-Page specification for *Monitor Service Health* with Preconditions, Postconditions, Main Success Scenario, Alternate Flow) | Markdown & PDF | [use_case_flow_specification.md](use_case_flow_specification.md)<br>[use_case_flow_specification.pdf](use_case_flow_specification.pdf) *(1-Page Formatted PDF)* |
| **5** | **Exception Flow Specification** (Fault handling for Network Timeout, Notification Delivery Failure, TLS Violation, Secrets Vault Unreachable, SSO Token Expiry) | Markdown & PDF | [exception_flow_specification.md](exception_flow_specification.md)<br>[exception_flow_specification.pdf](exception_flow_specification.pdf) *(1-Page Formatted PDF)* |

---

### 📂 Lab 2: Agile Jira Hands-On Deliverables (Upload to Google Form)

| # | Deliverable | Space / Project | File Link |
|---|---|---|---|
| **1** | **Kanban Project Deliverable** | `Kanban_BPS#42` (`KBPS42`) | **[Kanban.PDF](Kanban.PDF)** *(3-Page Complete PDF with 6 Screenshots)* |
| **2** | **Scrum Project Deliverable** | `Scrum_BPS#42` (`SBP42`) | **[Scrum.PDF](Scrum.PDF)** *(3-Page Complete PDF with Burndown Chart & Reflections)* |
| **3** | **Bug Tracking Deliverable** | `BugTracker_BPS#42` (`BTBPS42`) | **[BugReport.PDF](BugReport.PDF)** *(2-Page Complete PDF with Defect Logs)* |
| **Ref** | **Lab 2 Reference Docs & Handout** | Markdown & PDF | [kanban_jira_reference.md](kanban_jira_reference.md)<br>[scrum_jira_reference.md](scrum_jira_reference.md)<br>[bugtracker_jira_reference.md](bugtracker_jira_reference.md)<br>[Lab_2_Jira_Student_Handout.pdf](Lab_2_Jira_Student_Handout.pdf) |

---

## Primary UML Use-Case Diagram

![Primary UML Use-Case Diagram](use_case_diagram.png)

---

## Alternate Flow UML Use-Case Diagram

![Alternate Flow UML Use-Case Diagram](alternate_flow_use_case_diagram.png)

---

## Repository Structure

```
.
├── 42_SE_Lab1_SE_Problem_Statements.pdf      # Lab 1: Original problem statement handout (PS #42)
├── Lab_2_Jira_Student_Handout.pdf            # Lab 2: Jira student handout
├── Kanban.PDF                                # Lab 2 Deliverable 1: Kanban project PDF (6 screenshots)
├── Scrum.PDF                                 # Lab 2 Deliverable 2: Scrum project PDF (burndown chart + reflections)
├── BugReport.PDF                             # Lab 2 Deliverable 3: Bug tracking project PDF
├── README.md                                 # Master index and student information
├── requirements.md                           # Lab 1: Requirements Table (Markdown)
├── requirements.pdf                          # Lab 1: Requirements Table (PDF)
├── use_case_diagram.drawio                   # Lab 1: Primary UML Diagram (draw.io)
├── use_case_diagram.mdj                      # Lab 1: Primary UML Diagram (StarUML)
├── use_case_diagram.png                      # Lab 1: Primary UML Diagram (PNG)
├── alternate_flow_use_case_diagram.drawio    # Lab 1: Alternate Flow Diagram (draw.io)
├── alternate_flow_use_case_diagram.mdj       # Lab 1: Alternate Flow Diagram (StarUML)
├── alternate_flow_use_case_diagram.png       # Lab 1: Alternate Flow Diagram (PNG)
├── use_case_flow_specification.md            # Lab 1: Flow Specification (Markdown)
├── use_case_flow_specification.pdf           # Lab 1: Flow Specification (PDF)
├── exception_flow_specification.md           # Lab 1: Exception Flow Specification (Markdown)
├── exception_flow_specification.pdf          # Lab 1: Exception Flow Specification (PDF)
├── kanban_jira_reference.md                  # Lab 2: Kanban copy-paste reference
├── scrum_jira_reference.md                   # Lab 2: Scrum copy-paste reference
├── bugtracker_jira_reference.md              # Lab 2: Bug tracker copy-paste reference
└── Screenshots/                              # High-resolution screenshot assets
    ├── 1.png to 6.png                        # Kanban screenshots
    ├── scrum1.png to scrum5.png              # Scrum screenshots & Burndown chart
    └── bt1.png, bt2.png                      # Bug tracker screenshots
```

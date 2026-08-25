# Problem Statement #42 — Internal Microservice Catalog & Health Portal

**Course:** Software Engineering Lab 1 — Requirements Engineering & UML Use-Case Modelling  
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

| # | Deliverable | Format | File Link |
|---|---|---|---|
| **1** | **Complete Requirements Table** (FR-001 to FR-005, NFR-001 & NFR-002) with ID, Type, Description, Priority, Acceptance Criteria, and Rationale | Markdown | [requirements.md](requirements.md) |
| **2** | **UML Use-Case Diagram** (Actors, Use Cases, System Boundary, `«include»` & `«extend»` relationships) | draw.io + StarUML + PNG | [use_case_diagram.drawio](use_case_diagram.drawio) (draw.io)<br>[use_case_diagram.mdj](use_case_diagram.mdj) (StarUML)<br>[use_case_diagram.png](use_case_diagram.png) (Preview) |
| **3** | **Use-Case Flow Specification** (1-Page specification for *Monitor Service Health* with Preconditions, Postconditions, Main Success Scenario, Alternate Flow) | Markdown | [use_case_flow_specification.md](use_case_flow_specification.md) |

---

## UML Use-Case Diagram

![UML Use-Case Diagram](use_case_diagram.png)

### Tools Used
- **draw.io** — Open [use_case_diagram.drawio](use_case_diagram.drawio) at [app.diagrams.net](https://app.diagrams.net/)
- **StarUML** — Open [use_case_diagram.mdj](use_case_diagram.mdj) in [StarUML](https://staruml.io/)

---

## Repository Structure

```
.
├── README.md                        # Project overview, student info & deliverable index
├── requirements.md                  # 5 FRs + 2 NFRs with all 6 required attributes
├── use_case_diagram.drawio          # UML Use-Case Diagram (draw.io source)
├── use_case_diagram.mdj             # UML Use-Case Diagram (StarUML source)
├── use_case_diagram.png             # UML Use-Case Diagram (rendered preview)
└── use_case_flow_specification.md   # Detailed flow specification for UC-004
```

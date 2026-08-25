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
| **0** | **Original Problem Statement** | PDF | [42_SE_Lab1_SE_Problem_Statements.pdf](42_SE_Lab1_SE_Problem_Statements.pdf) |
| **1** | **Complete Requirements Table** (FR-001 to FR-005, NFR-001 & NFR-002) with ID, Type, Description, Priority, Acceptance Criteria, and Rationale | Markdown & PDF | [requirements.md](requirements.md)<br>[requirements.pdf](requirements.pdf) *(1-Page Formatted PDF)* |
| **2** | **UML Use-Case Diagram** (Actors, Use Cases, System Boundary, `«include»` & `«extend»` relationships) | draw.io + StarUML + PNG | [use_case_diagram.drawio](use_case_diagram.drawio) (draw.io)<br>[use_case_diagram.mdj](use_case_diagram.mdj) (StarUML)<br>[use_case_diagram.png](use_case_diagram.png) (Preview) |
| **3** | **Use-Case Flow Specification** (1-Page specification for *Monitor Service Health* with Preconditions, Postconditions, Main Success Scenario, Alternate Flow) | Markdown & PDF | [use_case_flow_specification.md](use_case_flow_specification.md)<br>[use_case_flow_specification.pdf](use_case_flow_specification.pdf) *(1-Page Formatted PDF)* |

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
├── 42_SE_Lab1_SE_Problem_Statements.pdf  # Original problem statement handout (PS #42)
├── README.md                             # Project overview, student info & deliverable index
├── requirements.md                       # Complete Requirements Table (Markdown)
├── requirements.pdf                      # Complete Requirements Table (1-Page Formatted PDF)
├── use_case_diagram.drawio               # UML Use-Case Diagram (draw.io source)
├── use_case_diagram.mdj                  # UML Use-Case Diagram (StarUML source)
├── use_case_diagram.png                  # UML Use-Case Diagram (rendered preview)
├── use_case_flow_specification.md        # Use-Case Flow Specification (Markdown)
└── use_case_flow_specification.pdf       # Use-Case Flow Specification (1-Page Formatted PDF)
```

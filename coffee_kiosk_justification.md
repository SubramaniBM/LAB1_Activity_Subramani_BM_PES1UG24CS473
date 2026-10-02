# Architectural Pattern Selection & Component Modeling Justification
## Scenario: Self-Service Coffee Kiosk System

**Course:** Software Engineering Lab 3 — Component Modeling & Architectural Pattern Selection  
**Department:** Computer Science & Engineering, PES University  
**Student Name:** Subramani B M &nbsp;|&nbsp; **SRN:** PES1UG24CS473 &nbsp;|&nbsp; **Section:** H  
**Assigned Lab Sheet Scenario:** Self-Service Coffee Kiosk System  

---

### Architecture Selection Statement
> **"We chose Layered / Client-Server Architecture for the Self-Service Coffee Kiosk System."**

---

### 1. Architectural Choice
We evaluated three principal architectural patterns for the Self-Service Coffee Kiosk System:
* **Microservices Architecture:** Over-engineered and inappropriate for a dedicated, standalone embedded kiosk terminal; introduces unnecessary network latency, inter-process communication overhead, and operational deployment complexity on single-node hardware.
* **Client-Server Architecture:** Provides centralized management for menu pricing updates while maintaining a local client terminal interface.
* **Layered Architecture (Selected for Local Terminal Software):** Organizes kiosk software into clean horizontal tiers: Presentation Layer (Touchscreen UI), Business Logic Layer (Order Manager), Service Integration Layer (Payment & Printer Controllers), and Data Access Layer (Menu & Pricing Database).

---

### 2. Two Specific Scenario-Related Reasons for Selection

1. **Deterministic Hardware Synchronization & Order State Machine Transition:**  
   The kiosk must orchestrate tightly coupled hardware interactions (touchscreen input, credit card pinpad authorization, and thermal receipt printing) in a strict sequential workflow: beverage selection (Espresso, Latte, Americano) $\rightarrow$ size choice (Small, Large) $\rightarrow$ payment confirmation $\rightarrow$ receipt printing. A layered modular architecture ensures strict transactional integrity, preventing receipt printing or dispense commands if payment authorization is declined.

2. **Standalone Fault Resilience & Embedded Resource Efficiency:**  
   In a busy café environment, network connectivity to central servers may be intermittent. The layered kiosk design encapsulates an embedded local SQLite database (`Menu & Pricing DB`) directly accessible via `IMenuData`. The kiosk continues serving customers, calculating accurate drink pricing and queuing transactions without depending on complex distributed orchestrators.

---

### 3. Security Advantage
* **Encapsulated PCI-DSS Payment Isolation & Tokenized Card Processing:**  
  Security is critical as the system accepts credit cards only. The **Payment Service Component** completely encapsulates all interactions with the EMV chip/contactless card reader hardware over an encrypted serial bus. The core application layers (Touchscreen UI, Order Manager, and Database) never handle, process, or store raw Primary Account Numbers (PAN) or CVVs. Only opaque cryptographic tokens and authorization codes are returned across the `IPaymentProcessor` interface, guaranteeing strict compliance with PCI-DSS standards.

---

### 4. Performance Benefit
* **Direct In-Memory Bus Execution & Sub-Second Latency:**  
  Because all components reside within the kiosk runtime, interactions across `IOrderService`, `IPrinterDriver`, and `IMenuData` occur via fast in-memory function calls and local device drivers (ESC/POS thermal protocol) rather than distributed network REST hops. This delivers near-zero UI input latency (< 50 ms) on the touchscreen and instant physical receipt generation upon transaction approval, maximizing customer throughput during peak café morning hours.

---

### 5. Component & Interface Specification Summary

| Component Name | Layer | Provided Interface (Ball) | Required Interface (Socket) | Primary Responsibility |
|:---|:---|:---|:---|:---|
| **Touchscreen UI Component** | Presentation | None (Direct Human Interaction) | `IOrderService`, `IMenuData` | Renders menu selection, drink sizes, order summary, and captures customer touch gestures |
| **Order Manager Component** | Business Logic | `IOrderService` (placeOrder, calculateTotal) | `IPaymentProcessor`, `IPrinterDriver` | Coordinates order state lifecycle, computes taxes/totals, and orchestrates post-order actions |
| **Payment Service Component** | Integration | `IPaymentProcessor` (authorizeCard, charge) | Card Reader Hardware USB Driver | Interfaces with EMV pinpad, executes secure card charging, and returns payment tokens |
| **Receipt Printer Controller** | Hardware Driver | `IPrinterDriver` (printReceipt) | Thermal Printer ESC/POS Driver | Formats receipt text with items, prices, timestamp, and sends print commands to hardware |
| **Menu & Pricing Database** | Data Persistence | `IMenuData` (getMenu, getPricing) | SQLite In-Memory Engine | Stores coffee types (Espresso, Americano, Latte), size multipliers, and base prices |

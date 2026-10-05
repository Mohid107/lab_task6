# Task 3 — Identify Constraint Violations

For each of the 8 formalized constraints, here is a realistic violation scenario, an explanation of the system failure, and how verification confirms the violation.

---

### 1. Train Safety Violation ($Train\_Present \to \neg Barrier\_Open$)
* **Violation Scenario:** 
  * $Train\_Present = \text{TRUE}$
  * $Barrier\_Open = \text{TRUE}$
* **Explanation:** A train has entered the crossing zone, but the controller failed to command the barriers down or a manual override left them raised. We know the constraint is violated because the conditional evaluation of $\text{TRUE} \to \text{FALSE}$ (since $\neg Barrier\_Open$ evaluates to false) results in a logical falsity, representing an immediate collision hazard.

### 2. Warning Activation Violation ($Barrier\_Closing \to Warnings\_Active$)
* **Violation Scenario:**
  * $Barrier\_Closing = \text{TRUE}$
  * $Warnings\_Active = \text{FALSE}$
* **Explanation:** The physical road barriers started descending to block traffic, but the warning lights and audible alarms failed to turn on due to a relay power fault. The implication fails because the antecedent is true while the consequent is false, meaning barriers are moving without public warning.

### 3. Traffic Signal Interlock Violation ($Barrier\_Closing \to Traffic\_Red$)
* **Violation Scenario:**
  * $Barrier\_Closing = \text{TRUE}$
  * $Traffic\_Red = \text{FALSE}$
* **Explanation:** The system initiated barrier closure while the road traffic lights remained green. Motorists are receiving conflicting signals (green light while barriers drop across their path), creating severe accident risks.

### 4. Barrier Pre-closure Violation ($Train\_Present \to Barrier\_Closed$)
* **Violation Scenario:**
  * $Train\_Present = \text{TRUE}$
  * $Barrier\_Closed = \text{FALSE}$ (and $Barrier\_Closing = \text{FALSE}$)
* **Explanation:** The train has already arrived at the crossing, yet the barriers remain fully open. The rule requiring full enclosure prior to train arrival is breached, as verified by sensor logs showing train presence while barrier state is open.

### 5. Sensor Failure Safe State Violation ($Sensor\_Failure \to Barrier\_Closed$)
* **Violation Scenario:**
  * $Sensor\_Failure = \text{TRUE}$
  * $Barrier\_Closed = \text{FALSE}$
* **Explanation:** The primary track sensor experienced an internal hardware fault, but instead of defaulting to a secure closed position, the system opened the barriers to let road traffic through. This violates fail-safe protocols when system integrity is compromised.

### 6. Communication Loss Safe State Violation ($Comm\_Loss \to \neg Barrier\_Open$)
* **Violation Scenario:**
  * $Comm\_Loss = \text{TRUE}$
  * $Barrier\_Open = \text{TRUE}$
* **Explanation:** Network connectivity between the local crossing controller and the safety-monitoring unit dropped. The local unit failed to default to a locked/closed position and instead kept the barriers open. Verification logs confirm communication timeout alongside an open barrier command.

### 7. Sensor Conflict Handling Violation ($Sensor\_Conflict \to Barrier\_Closed$)
* **Violation Scenario:**
  * $Sensor\_Conflict = \text{TRUE}$
  * $Barrier\_Closed = \text{FALSE}$
* **Explanation:** Redundant track sensors reported conflicting data (Sensor A detected a train; Sensor B reported clear). The arbitration logic failed to adopt the conservative safe stance, leaving the barriers open despite unverified track safety.

### 8. Emergency Override Violation ($Emergency \to Barrier\_Closed$)
* **Violation Scenario:**
  * $Emergency = \text{TRUE}$
  * $Barrier\_Closed = \text{FALSE}$
* **Explanation:** An operator triggered an emergency lockdown from the control center due to a stalled vehicle near the tracks, but the system software ignored the signal and kept the barriers open. The implication evaluates to false, exposing a critical safety override failure.

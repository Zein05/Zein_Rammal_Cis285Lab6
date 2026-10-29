<!--
Sync Impact Report
Version change: unversioned scaffold → 1.0.0 (initial adoption)
Modified principles: scaffold placeholders → Requirements Are Traceable and Classified;
  Object-Oriented Design with a Strict GUI Boundary; Exact Monetary Arithmetic;
  Automated Tests with JUnit 5; PlantUML Architecture Documentation;
  Human Review of AI Contributions
Added sections: Implementation Baseline; Requirements and Quality Controls
Removed sections: none
Follow-up TODO: confirm the original ratification date.
-->

# SplitSmart Constitution

## Core Principles

### I. Requirements Are Traceable and Classified
Customer requirements in `UserRequirement.md` are the product baseline; implementation
decisions are not customer requirements. Derived specifications MUST preserve that distinction
and trace every customer requirement to acceptance criteria, design elements, and verification
tests. Any conflict, scope change, or unmet customer requirement MUST be recorded and resolved
with an approved decision before the project claims that requirement is satisfied. In
particular, the customer's request for a primarily web-based product with Android and iOS apps
is not met merely by implementing a Java Swing desktop application.

### II. Object-Oriented Design with a Strict GUI Boundary
The application MUST use object-oriented design with clear responsibilities, encapsulated
state, and cohesive abstractions that serve identified requirements. Swing presentation code
MUST delegate business operations to application or domain logic. Business rules MUST NOT depend
on Swing classes, and the core expense and balance logic MUST be testable without launching the
GUI. This boundary keeps financial behavior consistent and independently verifiable.

### III. Exact Monetary Arithmetic
All monetary amounts and monetary calculations MUST use `BigDecimal`; binary floating-point
types MUST NOT be used for money. Currency scale, rounding mode, and allocation of any
split-rounding remainder MUST be explicit and consistent. Tests MUST verify that allocations
reconcile to the original expense and that balance updates preserve the value of payments and
expenses.

### IV. Automated Tests with JUnit 5
Automated tests MUST use JUnit 5. Business rules for expense splits, approvals, balances,
payments, and reports MUST be tested independently of Swing, including boundary and rounding
cases where applicable. Changes to behavior MUST include or update tests that demonstrate the
acceptance criteria; a successful build alone is not evidence that a customer requirement is
satisfied.

### V. PlantUML Architecture Documentation
Architecture diagrams maintained for the project MUST use PlantUML source checked into the
project. Diagrams MUST describe the relevant design, including the boundary between the GUI and
business logic, and MUST be updated when an architectural change makes them inaccurate. Keeping
diagram source reviewable makes design decisions traceable alongside code.

### VI. Human Review of AI Contributions
AI-generated or AI-assisted code, tests, requirements, diagrams, and documentation MUST be
reviewed and validated by a human before acceptance. Reviewers MUST verify correctness against
the customer requirements, design constraints, and tests; AI output is not evidence of
correctness and MUST NOT be accepted solely because it appears plausible.

## Implementation Baseline

The implementation baseline is Java 21, Maven, and Java Swing for the desktop GUI. Maven
configuration MUST target Java 21, and automated project tests MUST run with JUnit 5. PlantUML
MUST be used for architecture diagram source as stated above. These technologies are
implementation decisions, not additional customer requirements. They do not supersede the
customer's requested web, Android, and iOS support; any platform gap requires an explicit,
approved scope or architecture decision and MUST remain visible in requirements traceability.

## Requirements and Quality Controls

The original customer request MUST remain unchanged and be treated as the source for customer
needs, including accounts, groups, expenses and receipts, notifications, approvals, balances,
payments, reports, and supported platforms. Derived project artifacts MUST label customer
requirements separately from implementation decisions and maintain requirement-to-test
traceability. Human review MUST confirm the traceability and requirement status when changes
are proposed or accepted.

## Governance

This constitution governs project decisions and review. Amendments MUST be documented in the
constitution, reviewed by the project owner, and versioned using semantic versioning: MAJOR for
backward-incompatible governance changes, MINOR for new or materially expanded principles, and
PATCH for clarifications that do not change obligations. Every implementation or review MUST
check relevant changes for compliance with these principles and for customer-requirement
traceability. Any exception MUST be documented with its rationale, impact, approver, and
follow-up plan; exceptions MUST NOT silently redefine a customer requirement.

**Version**: 1.0.0 | **Ratified**: TODO(RATIFICATION_DATE): original adoption date is unknown | **Last Amended**: 2026-10-29

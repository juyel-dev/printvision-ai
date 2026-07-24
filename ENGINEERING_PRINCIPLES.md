# ENGINEERING PRINCIPLES

Project:
PW Print Optimizer

Document:
ENGINEERING_PRINCIPLES.md

Version:
1.0

Status:
PROJECT CONSTITUTION

---

# 1. Purpose

This document defines the engineering philosophy of PW Print Optimizer.

It is the highest-level technical document in the project.

If any future implementation conflicts with this document, this document takes precedence.

---

# 2. Engineering Philosophy

The project values:

Correctness

↓

Maintainability

↓

Predictability

↓

Performance

↓

Features

Features are always the lowest priority.

---

# 3. Project Philosophy

PW Print Optimizer solves one problem.

Transform educational PDFs into print-friendly documents.

Nothing more.

Every new feature must support this goal.

Otherwise,

it should not be added.

---

# 4. Architecture Principles

Every subsystem must have one responsibility.

Frontend

↓

Workflow

↓

Tiny Vision Model

↓

Rule Engine

↓

Rust Engine

↓

Layout Engine

↓

Export Engine

Responsibilities must never overlap.

---

# 5. Separation of Responsibilities

Frontend

User Interaction

Model

Understanding

Rule Engine

Decision Making

Rust

Execution

Layout

Arrangement

Export

PDF Generation

Never violate these boundaries.

---

# 6. AI Principles

AI exists to understand.

AI does not exist to edit.

AI should remain:

Tiny

Offline

Replaceable

Retrainable

Deterministic

Framework independent.

---

# 7. Dataset Principles

Dataset is the most valuable project asset.

The model is temporary.

The dataset is permanent.

Never compromise dataset quality.

---

# 8. Rule Engine Principles

Business logic belongs here.

Never inside:

Model

Frontend

Rust algorithms

Rules should remain readable.

Easy to update.

Easy to debug.

---

# 9. Rust Principles

Rust performs work.

Rust never guesses.

Rust should be deterministic.

Memory-safe.

Streaming-first.

Browser-first.

---

# 10. Browser Principles

Everything must execute locally.

No server processing.

No cloud dependency.

No mandatory internet connection.

---

# 11. User Experience Principles

Zero Configuration.

The user should never choose:

Threshold

Brightness

Contrast

Gamma

AI settings

Algorithm selection

Everything is automatic.

---

# 12. Memory Principles

Memory usage should remain approximately constant.

Never load entire documents.

Release temporary memory immediately.

Only one preview exists.

---

# 13. Performance Principles

Responsiveness is mandatory.

The UI must never freeze.

Long operations must expose progress.

Performance improvements must never reduce output quality without explicit justification.

---

# 14. Code Principles

Readable.

Modular.

Well documented.

Small functions.

Minimal dependencies.

Clear interfaces.

Avoid clever code.

Prefer obvious code.

---

# 15. Documentation Principles

Every module must contain:

README

Responsibilities

Inputs

Outputs

Dependencies

Limitations

No undocumented behavior.

---

# 16. Versioning

Everything is versioned.

Dataset

Annotations

Schema

Model

Rule Engine

Rust Engine

Layout Engine

Web App

Documentation

Nothing is overwritten.

---

# 17. Backward Compatibility

New versions should preserve:

Content Map

Public interfaces

Workflow

unless there is a major version change.

---

# 18. Security

Documents never leave the user's device.

No telemetry of document contents.

No cloud storage.

No hidden uploads.

Privacy is non-negotiable.

---

# 19. Testing Principles

Every release should include:

Unit Tests

Integration Tests

Regression Tests

Performance Tests

Browser Compatibility Tests

Memory Tests

Benchmark Comparison

---

# 20. AI Coding Agent Rules

Any coding AI working on this project must:

Read all architecture documents first.

Understand responsibilities before writing code.

Avoid architectural changes unless explicitly requested.

Respect module boundaries.

Never introduce unnecessary complexity.

Never add features outside the project scope.

Document all significant decisions.

---

# 21. Decision Framework

When choosing between two solutions:

Prefer:

Simpler

More maintainable

More predictable

Lower memory usage

Better browser compatibility

Fewer dependencies

Choose complexity only when measurable benefits justify it.

---

# 22. Release Principles

A release is acceptable only if:

Architecture remains intact.

Memory targets are met.

Performance targets are met.

Benchmark quality is maintained or improved.

Documentation is updated.

Regression tests pass.

---

# 23. Long-Term Evolution

The project should evolve by improving:

Dataset quality

Model quality

Rule quality

Rust algorithms

Performance

Compatibility

Not by accumulating unrelated features.

---

# 24. Source of Truth

The following documents define the project:

DOC-01 Project Vision

DOC-02 System Architecture

DOC-03 Dataset Specification

DOC-04 Dataset Labeling Guidelines

DOC-05 Vision Model Specification

DOC-06 Training Pipeline

DOC-07 Model Architecture

DOC-08 Rust Engine Specification

DOC-09 Web Application Specification

DOC-10 Engineering Principles

Together these documents are the project's Source of Truth.

---

# 25. Definition of Success

PW Print Optimizer is successful when:

A non-technical student can open the website,

upload educational PDFs,

click through a simple guided workflow,

and receive a high-quality print-ready PDF,

while every technical decision remains invisible,

every document remains private,

and the entire system continues to evolve without architectural rewrites.

---

# Final Engineering Motto

Understand.

Decide.

Optimize.

Layout.

Export.

Nothing More.

Nothing Less.

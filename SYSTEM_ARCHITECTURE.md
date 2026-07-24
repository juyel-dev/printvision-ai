# SYSTEM ARCHITECTURE

Project:
PW Print Optimizer

Version:
1.0

Status:
Architecture Freeze

---

# 1. Architecture Philosophy

The entire application is designed around one principle:

Small UI.
Small AI.
Powerful Engine.

Each component has exactly one responsibility.

No module should perform the responsibilities of another module.

---

# 2. High-Level Architecture

                Browser
                    │
                    ▼
           React Frontend
                    │
                    ▼
          Workflow Controller
                    │
 ┌──────────┬──────────┬──────────┐
 │          │          │
 ▼          ▼          ▼
Merge    Vision AI   Layout Engine
 │          │          │
 └──────────┴──────────┘
            │
            ▼
       Rust WASM Engine
            │
            ▼
      Optimized PDF Output

---

# 3. System Modules

The application consists of six independent modules.

Module 1

Frontend

Module 2

Merge Engine

Module 3

Tiny Vision Model

Module 4

Rust Processing Engine

Module 5

Layout Engine

Module 6

Export Engine

Each module should be independently maintainable.

---

# 4. Frontend Responsibilities

Frontend is responsible only for:

• UI

• Navigation

• Progress

• Preview

• User interaction

Frontend must NEVER perform image processing.

Frontend must NEVER perform AI inference.

Frontend must NEVER manipulate PDFs directly.

---

# 5. Merge Engine

Input

Multiple PDFs

Output

One merged PDF

Responsibilities

• Upload

• Rearrangement

• Merge

• Preview

• Download

• Memory cleanup

The Merge Engine knows nothing about AI.

---

# 6. Tiny Vision Model

Purpose

Understand the document.

Never edit the document.

Responsibilities

Detect:

• Text regions

• Highlight regions

• Photo regions

• Diagram regions

• Tables

• Handwriting

• Colored backgrounds

• Mixed content

Generate:

Content Map

Confidence Scores

Recommendations

The model NEVER edits pixels.

---

# 7. Rust Processing Engine

Purpose

Transform the document.

Responsibilities

Image Processing

Contrast

Background cleanup

Enhancement

Sharpening

Noise reduction

Thresholding

Print optimization

Streaming

Memory management

Rust Engine should never classify content.

Rust receives Content Map from the Tiny Vision Model.

---

# 8. Layout Engine

Input

Optimized PDF

Output

Final print layout

Responsibilities

4 Slides

6 Slides

8 Slides

10 Slides

Future

12

16

Custom

Layout Engine performs no image enhancement.

---

# 9. Export Engine

Responsibilities

Generate Final PDF

Compress output

Validate pages

Download

Clean temporary memory

---

# 10. Workflow

Phase 1

Upload

↓

Arrange

↓

Merge

↓

Preview

↓

Next

---

Phase 2

Analyze

↓

Content Map

↓

Rust Optimization

↓

Preview

↓

Next

---

Phase 3

Layout

↓

Preview

↓

Download

---

# 11. Data Flow

Raw PDFs

↓

Merge Engine

↓

Merged PDF

↓

Vision Model

↓

Content Map

↓

Rust Engine

↓

Optimized PDF

↓

Layout Engine

↓

Final PDF

↓

Download

No shortcuts are allowed.

---

# 12. Content Map

Rust never receives raw AI predictions.

Rust receives a standardized Content Map.

Example

{

version:1,

regions:[...],

recommendations:[...]

}

Future models must produce the same structure.

---

# 13. Module Independence

Frontend

must not know

Rust internals.

Rust

must not know

Frontend.

Tiny Model

must not know

Layout Engine.

Layout Engine

must not know

Vision internals.

Loose coupling.

High cohesion.

---

# 14. Memory Architecture

Maximum one preview.

Maximum one processing page.

Streaming only.

Workflow

Render

↓

Process

↓

Export

↓

Release Memory

↓

Next Page

Entire document should never be fully rendered into memory.

---

# 15. Temporary Files

Every phase creates temporary resources.

Every phase must destroy temporary resources before entering the next phase.

Memory leaks are unacceptable.

---

# 16. Error Recovery

Each module reports its own errors.

Frontend only displays user-friendly messages.

Technical logs remain internal.

---

# 17. Replaceability

Every major component should be replaceable.

Example

Vision Model v1

↓

Vision Model v2

No Rust changes.

Rust v1

↓

Rust v2

No Frontend changes.

Layout Engine

↓

New Layout Engine

No AI changes.

---

# 18. Future AI Runtime

Architecture should support future inference engines.

Possible runtimes

ONNX Runtime

WebNN

WebGPU

Future browser AI runtimes

The rest of the application should remain unchanged.

---

# 19. Scalability

The architecture should support:

Larger datasets

New model versions

Better algorithms

Additional layouts

Performance improvements

without rewriting the complete application.

---

# 20. Source of Truth

This document defines the system boundaries.

Every future implementation must respect these responsibilities.

No module may silently absorb another module's responsibilities.

Maintaining these boundaries is mandatory for long-term stability, maintainability, and AI-assisted development.

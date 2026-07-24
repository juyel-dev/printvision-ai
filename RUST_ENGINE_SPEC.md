# RUST ENGINE SPECIFICATION

Project:
PW Print Optimizer

Document:
RUST_ENGINE_SPEC.md

Version:
1.0

Status:
Frozen

---

# 1. Purpose

The Rust Engine is the execution core of PW Print Optimizer.

It receives structured information from the Tiny Vision Model and performs deterministic, high-performance document optimization.

The engine must never perform AI inference.

Its responsibility is execution, not understanding.

---

# 2. Core Philosophy

AI Understands.

Rust Executes.

Never reverse these responsibilities.

---

# 3. Primary Responsibilities

The Rust Engine is responsible for:

• PDF Rendering

• Image Processing

• Background Processing

• Contrast Optimization

• Highlight Preservation

• Photo Preservation

• Diagram Preservation

• Noise Reduction

• Memory Management

• Streaming Processing

• PDF Generation

• Layout Generation

Everything else belongs elsewhere.

---

# 4. Non Responsibilities

The Rust Engine must NEVER:

Run AI models

Detect content

Guess regions

Perform OCR

Store user data

Require internet

Access cloud services

Learn from user documents

---

# 5. Input

Input 1

Merged PDF

Input 2

Content Map

Input 3

Layout Configuration

The engine never receives raw neural network outputs.

---

# 6. Processing Pipeline

Merged PDF

↓

Render Current Page

↓

Receive Content Map

↓

Choose Processing Pipeline

↓

Apply Optimizations

↓

Generate Optimized Page

↓

Release Memory

↓

Load Next Page

Repeat until complete.

---

# 7. Streaming Architecture

The engine must process pages sequentially.

Never load the entire PDF into memory.

Workflow

Load

↓

Process

↓

Write

↓

Release

↓

Next

Streaming is mandatory.

---

# 8. Memory Policy

Maximum

One active page

One preview

One output buffer

All temporary buffers must be released immediately.

Memory growth should remain approximately constant regardless of document size.

---

# 9. Region Processing

The engine processes regions independently.

Example

Text

↓

Text Pipeline

Photo

↓

Photo Pipeline

Diagram

↓

Diagram Pipeline

Highlight

↓

Highlight Pipeline

Each pipeline is isolated.

---

# 10. Processing Pipelines

Pipeline A

Text Optimization

Increase readability

Improve contrast

Preserve edges

---

Pipeline B

Highlight Preservation

Protect highlight colors

Preserve underlying text

Avoid turning highlights black

---

Pipeline C

Photo Optimization

Preserve grayscale information

Avoid excessive thresholding

Maintain useful visual detail

---

Pipeline D

Diagram Optimization

Sharpen lines

Maintain geometry

Improve print clarity

---

Pipeline E

Background Cleanup

Remove unnecessary backgrounds

Convert dark backgrounds to print-friendly backgrounds

Preserve intentional colored elements

---

# 11. Adaptive Processing

The Rust Engine selects pipelines using recommendations from the Content Map.

The AI recommends.

Rust decides.

Example

Photo + Highlight

↓

Photo Pipeline

+

Highlight Pipeline

+

Background Cleanup

---

# 12. Unknown Content

If confidence is low,

use the safest processing strategy.

Never aggressively optimize unknown regions.

Conservative output is preferred over damaged output.

---

# 13. Parallelism

Parallel processing may be used only when:

Memory budget allows

Browser remains responsive

Ordering is preserved

Correctness is never sacrificed for speed.

---

# 14. PDF Generation

Generate pages incrementally.

Do not wait until every page has been processed.

Support progressive output internally.

---

# 15. Layout Integration

After optimization,

pages are passed to the Layout Engine.

The Rust Engine never decides layout.

---

# 16. WASM Integration

The engine is compiled to WebAssembly.

Requirements

Small binary

Fast startup

Low memory

Portable

Deterministic behavior

Browser compatible

---

# 17. Browser Constraints

The engine must tolerate:

Limited RAM

Limited CPU

No GPU

Mobile browsers

Background tab suspension

Long documents

---

# 18. Error Recovery

If one page fails,

continue processing remaining pages whenever possible.

Generate a detailed internal error report.

Show simple messages to users.

---

# 19. Logging

Development builds may produce detailed logs.

Production builds should produce minimal logs.

User document contents must never be logged.

---

# 20. Temporary Storage

Temporary data exists only during processing.

Delete immediately after use.

Nothing should persist after the browser tab closes.

---

# 21. Security

Never upload PDFs.

Never transmit images.

Never send Content Maps.

Never store processed documents remotely.

Everything remains local.

---

# 22. Performance Targets

Cold Start

As low as possible

Warm Start

Near instant

Memory

Constant

CPU

Efficient

Latency

Responsive UI at all times

---

# 23. Extensibility

Future versions may add:

New optimization pipelines

Better algorithms

Additional image operators

Improved layout support

without changing the public interface.

---

# 24. Replaceability

Image processing algorithms may evolve independently.

Pipeline A

↓

Pipeline A v2

↓

Pipeline A v3

The external workflow remains unchanged.

---

# 25. Determinism

Given the same:

PDF

Model

Content Map

Settings

The engine must always produce identical output.

No randomness.

---

# 26. Golden Rules

1.

Never perform AI inside Rust.

2.

Never load the whole document.

3.

Always stream.

4.

Always release memory immediately.

5.

Protect educational content before improving appearance.

6.

User data never leaves the device.

7.

Performance must remain predictable.

---

# 27. Definition of Success

The Rust Engine is successful when it can process hundreds of educational PDF pages with constant memory usage, deterministic output, responsive browser performance, and complete offline execution while faithfully preserving educational content.

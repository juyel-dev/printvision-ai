# VISION MODEL SPECIFICATION

Project:
PW Print Optimizer

Document:
VISION_MODEL_SPEC.md

Version:
1.0

Status:
Frozen

---

# 1. Purpose

The Tiny Vision Model is responsible for understanding educational document pages.

It does NOT edit images.

It does NOT optimize PDFs.

It only analyzes visual content and produces a structured Content Map for the Rust Engine.

---

# 2. Design Philosophy

Think before processing.

The model acts as the "eyes" of the system.

The Rust Engine acts as the "hands".

The model should never modify pixels.

The Rust Engine should never guess content.

---

# 3. Responsibilities

The model should:

• Understand page structure

• Identify important content

• Detect different visual regions

• Estimate confidence

• Recommend processing strategy

The model should NOT:

❌ Apply filters

❌ Modify images

❌ Generate PDFs

❌ Rearrange layouts

❌ Compress files

---

# 4. Model Requirements

Browser First

Offline

Tiny

Fast

Replaceable

Retrainable

Hardware Independent

---

# 5. Target Size

Preferred

3–5 MB

Maximum

10 MB

Future versions should remain below 10 MB whenever possible.

---

# 6. Runtime Requirements

Runs entirely inside browser.

No cloud inference.

No internet required.

Compatible with:

Desktop

Android

Future iOS support

---

# 7. Input

Input Type

RGB Image

Generated from PDF page.

The model never reads PDFs directly.

---

Input Resolution

224×224

Future versions may support adaptive resolutions.

---

# 8. Output

The model returns a structured Content Map.

The Content Map becomes the single source of truth for downstream processing.

---

# 9. Content Types

The model should recognize:

Text

Highlight

Photo

Diagram

Flowchart

Table

Formula

Graph

Handwriting

Colored Background

Dark Background

Screenshot

Mixed Content

Unknown

---

# 10. Region Detection

The model should identify visual regions.

Examples

Photo Region

Highlight Region

Diagram Region

Text Region

Table Region

Handwriting Region

The Rust Engine will use these regions during optimization.

---

# 11. Confidence

Every prediction must include confidence.

Example

Highlight

98%

Photo

93%

Diagram

85%

Unknown

15%

Confidence allows safer decision making.

---

# 12. Recommendations

The model should recommend processing strategies.

Example

Preserve Highlight

Avoid Threshold

Protect Photo

Increase Text Contrast

Background Whitening

Preserve Colored Diagram

The Rust Engine decides how to execute them.

---

# 13. Content Map

Example

{

version:1,

page_type:"mixed",

confidence:0.97,

regions:[...],

recommendations:[...]

}

This structure should remain stable across future versions.

---

# 14. Stable Interface

The Rust Engine must never depend on internal model architecture.

Only the Content Map matters.

Any future model must produce the same interface.

---

# 15. Replaceability

Future upgrades

model_v1

↓

model_v2

↓

model_v3

should require no Frontend changes.

No Rust rewrite.

Only replace the model file.

---

# 16. Retraining

The model must be easy to retrain.

Training should only require

New Dataset

↓

Training Pipeline

↓

Validation

↓

Benchmark

↓

Export

↓

Replace Model

No application changes.

---

# 17. Model Evolution

The architecture should support:

Better accuracy

New labels

New recommendations

New confidence estimation

without breaking compatibility.

---

# 18. Performance Targets

Inference

As fast as reasonably possible.

Memory

Minimal.

Suitable for 4 GB RAM Android devices.

The model must never become the memory bottleneck.

---

# 19. Failure Strategy

If confidence is low

↓

Return Unknown

↓

Rust Engine uses Safe Pipeline.

Never hallucinate content.

---

# 20. Future Compatibility

The model should eventually support:

Region Detection

Object Detection

Lightweight Segmentation

Context Understanding

without changing the external interface.

---

# 21. Export Format

The exported model should support long-term browser deployment.

Preferred:

ONNX

Future runtimes may also be supported.

The application should not depend on one ML framework.

---

# 22. Quantization

Models should support:

FP16

INT8

Future optimizations

The deployment format should prioritize browser performance over maximum accuracy.

---

# 23. Regression Policy

Every new model version must be tested against the benchmark dataset.

A newer model must never significantly reduce performance on previously solved pages.

---

# 24. Golden Rules

1.

Understand first.

Never edit.

2.

Small model.

Large dataset.

3.

Stable interface.

Replaceable model.

4.

Offline always.

5.

The model is an advisor.

The Rust Engine is the executor.

---

# 25. Long-Term Vision

The Tiny Vision Model should gradually become better at understanding educational documents as the dataset grows.

Its intelligence should increase over time.

Its interface should remain stable.

This ensures that future improvements only require replacing the model file, while the Browser App, Rust Engine, and User Experience remain unchanged.

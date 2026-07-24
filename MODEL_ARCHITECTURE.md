# MODEL ARCHITECTURE

Project:
PW Print Optimizer

Document:
MODEL_ARCHITECTURE.md

Version:
1.0

Status:
Frozen

---

# 1. Purpose

This document defines the internal architecture of the Tiny Vision Model.

The purpose is not to prescribe one exact neural network.

Instead, it defines the engineering constraints, design principles, and acceptable architecture choices.

The implementation may evolve while respecting these constraints.

---

# 2. Core Philosophy

The model is a visual understanding engine.

NOT

an image enhancement model.

NOT

a generative model.

NOT

a large multimodal model.

Its only job is to understand educational document pages.

---

# 3. Architecture Goals

Highest Priority

• Small model

• Fast inference

• Stable output

• Browser compatibility

• Easy retraining

• Easy replacement

Lower Priority

• Maximum accuracy

• Complex architectures

• Large parameter count

---

# 4. Architecture Constraints

Preferred Size

3–5 MB

Hard Limit

10 MB

Preferred RAM

<100 MB during inference

Target Device

4 GB Android phone

Browser deployment is mandatory.

---

# 5. Candidate Backbone Families

Preferred

MobileNetV3

EfficientNet Lite

MobileOne

ShuffleNet

GhostNet

Future

MobileViT

TinyViT

NanoDet-style backbone

The project should avoid architectures intended for server-scale inference.

---

# 6. Input Pipeline

PDF Page

↓

Render

↓

RGB Image

↓

Resize

↓

Normalize

↓

Model Input

The model never receives raw PDFs.

---

# 7. Feature Extraction

The backbone should learn:

Page layout

Visual hierarchy

Text blocks

Image blocks

Highlight regions

Background characteristics

Diagram structures

Handwritten regions

without relying on OCR.

---

# 8. Multi-Task Design

Instead of one large prediction,

the model should solve several small tasks simultaneously.

Example

Page Type

+

Background Type

+

Content Detection

+

Recommendation

Multi-task learning improves generalization.

---

# 9. Output Heads

Example

Head A

Page Classification

Head B

Region Detection

Head C

Highlight Detection

Head D

Background Classification

Head E

Pipeline Recommendation

Each head should be independently replaceable.

---

# 10. Confidence

Every prediction must include confidence.

Never force certainty.

Unknown is a valid prediction.

---

# 11. Region Representation

Future versions should support:

Bounding Boxes

↓

Polygon Regions

↓

Lightweight Segmentation

The interface should remain compatible.

---

# 12. Recommendation Layer

The model should suggest,

not decide.

Examples

Preserve Highlight

Protect Photo

Use White Background

Increase Contrast

Avoid Aggressive Threshold

The Rust Engine makes the final decision.

---

# 13. Output Interface

The internal architecture may change.

The output schema must not.

The Content Map is the only public interface.

---

# 14. Model Independence

The application must never depend on:

PyTorch

TensorFlow

Keras

Training framework

Only exported inference models are deployed.

---

# 15. Deployment Format

Preferred

ONNX

Future

WebNN

WebGPU

Other browser runtimes

The frontend should remain unchanged.

---

# 16. Quantization Strategy

Preferred

INT8

Fallback

FP16

Future

INT4 (if accuracy remains acceptable)

Quantization should be validated against benchmark quality.

---

# 17. Retraining Philosophy

Retraining should require only:

Updated Dataset

↓

Frozen Pipeline

↓

Training

↓

Benchmark

↓

Export

↓

Replace Model

No application code changes.

---

# 18. Upgrade Strategy

Model V1

↓

Model V2

↓

Model V3

Each version should improve at least one of:

Accuracy

Latency

Memory

Generalization

Compatibility

without breaking downstream systems.

---

# 19. Failure Handling

If confidence is insufficient,

the model must return Unknown.

The Rust Engine will use a conservative processing pipeline.

Never hallucinate content.

---

# 20. Benchmark Criteria

Every candidate model should be evaluated on:

Accuracy

Inference Time

Model Size

Memory Usage

Browser Compatibility

Android Compatibility

Cold Start Time

Warm Start Time

---

# 21. Future Evolution

The architecture should support future improvements such as:

Better region localization

More accurate recommendations

Improved layout understanding

Additional content categories

without requiring application redesign.

---

# 22. Non-Goals

The model will never:

Generate images

Edit images

Upscale images

Perform OCR editing

Replace the Rust Engine

Become a general-purpose vision model

Its scope remains intentionally narrow.

---

# 23. Golden Rules

1.

The dataset defines intelligence.

2.

The model extracts knowledge.

3.

The Rust Engine performs work.

4.

The browser executes everything locally.

5.

A smaller stable model is preferred over a larger complex model.

6.

Every future model must remain replaceable.

7.

The external interface must remain stable forever.

---

# 24. Definition of Success

The model is successful when it can reliably understand educational PDF pages,

produce a consistent Content Map,

operate fully offline,

fit within the browser resource budget,

and be upgraded independently without requiring changes to the frontend, Rust Engine, or user workflow.

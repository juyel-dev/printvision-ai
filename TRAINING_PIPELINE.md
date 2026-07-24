# TRAINING PIPELINE

Project:
PW Print Optimizer

Document:
TRAINING_PIPELINE.md

Version:
1.0

Status:
Frozen

---

# 1. Purpose

This document defines the complete lifecycle of the Tiny Vision Model.

Every future model version must follow this pipeline.

No stage should be skipped.

The pipeline prioritizes reproducibility, maintainability, and continuous improvement over rapid experimentation.

---

# 2. Engineering Philosophy

Dataset First

↓

Quality Second

↓

Training Third

↓

Deployment Last

Never train a model simply because new data exists.

Train only when the dataset meaningfully improves.

---

# 3. Complete Lifecycle

Raw PDFs

↓

Dataset Preparation

↓

Page Rendering

↓

Annotation

↓

Quality Review

↓

Dataset Freeze

↓

Training

↓

Validation

↓

Benchmark

↓

Quantization

↓

ONNX Export

↓

Regression Testing

↓

Model Release

---

# 4. Stage 1 — Dataset Preparation

Input

Raw educational PDFs

Requirements

• Original PDFs only

• No preprocessing

• No compression

• Preserve original source

Output

Dataset Version

---

# 5. Stage 2 — Rendering

Convert every PDF page into images.

Rules

Same renderer

Same DPI

Same rendering settings

Lossless

Consistent output

Output

Rendered Pages

---

# 6. Stage 3 — Annotation

Annotators label pages according to

DATASET_LABELING_GUIDELINES.md

Never train on unlabeled pages.

---

# 7. Stage 4 — Quality Review

Every annotation must pass review.

Checklist

Correct labels

Metadata complete

No corruption

No duplicates

Reviewer assigned

Only reviewed pages enter training.

---

# 8. Stage 5 — Dataset Freeze

Freeze the dataset.

Assign

Dataset Version

Annotation Version

Schema Version

Benchmark Version

After freezing,

the training dataset becomes immutable.

---

# 9. Stage 6 — Training

Input

Frozen Dataset

↓

Training Configuration

↓

Model Initialization

↓

Training

↓

Checkpoint Saving

↓

Validation

No manual intervention.

---

# 10. Stage 7 — Validation

Measure

Accuracy

Precision

Recall

F1 Score

Confusion Matrix

Per-class Accuracy

False Positives

False Negatives

Store every metric.

---

# 11. Stage 8 — Benchmark

Run the model against

Benchmark Dataset.

Compare

Previous Model

↓

Current Model

Reject regression.

---

# 12. Stage 9 — Quantization

Optimize the model for browser deployment.

Possible formats

FP16

INT8

Future

INT4

The optimized model should preserve acceptable accuracy.

---

# 13. Stage 10 — Export

Preferred Output

model.onnx

Include

Version

Training Date

Dataset Version

Model Version

Export Version

Checksum

---

# 14. Stage 11 — Regression Testing

Every exported model must pass

Benchmark Tests

Memory Tests

Latency Tests

Browser Compatibility Tests

Android Tests

Only passing models can be released.

---

# 15. Model Release

Release Package

model.onnx

metadata.json

CHANGELOG.md

LICENSE

README

Every release must be reproducible.

---

# 16. Versioning

Dataset

v1

↓

v2

↓

v3

Annotation

v1

↓

v2

↓

v3

Model

v1

↓

v2

↓

v3

Each version is independent.

---

# 17. Continuous Learning

New PDFs

↓

Review

↓

Annotate

↓

Dataset Expansion

↓

New Training

↓

Benchmark

↓

Release

Never overwrite previous datasets.

---

# 18. Failure Policy

If

Benchmark decreases

↓

Reject

If

Latency becomes unacceptable

↓

Reject

If

Model exceeds size budget

↓

Reject

If

Browser compatibility fails

↓

Reject

---

# 19. Release Criteria

A new model can only be released if:

✓ Better benchmark performance

✓ Stable latency

✓ Stable memory usage

✓ Stable interface

✓ Acceptable model size

✓ Browser compatibility

---

# 20. Long-Term Dataset Growth

v1

1,000 Pages

↓

v2

5,000 Pages

↓

v3

10,000 Pages

↓

v4

25,000 Pages

↓

v5

50,000 Pages

The dataset should continuously improve.

---

# 21. AI-Assisted Development

Coding AI agents may automate:

Rendering

Annotation Tools

Training

Validation

Benchmarking

Export

Documentation

However,

every release must remain deterministic and reproducible.

---

# 22. Golden Rules

1.

Never train from an unfinished dataset.

2.

Never skip benchmarking.

3.

Never release without regression testing.

4.

Never overwrite previous versions.

5.

Always be able to reproduce a released model.

6.

Dataset quality is more important than model complexity.

7.

A smaller, stable model is preferred over a larger, slightly more accurate model if it better satisfies browser performance goals.

---

# 23. Definition of Success

The training pipeline is successful when a future coding AI can retrain the Tiny Vision Model using only:

• The dataset

• This document

• The frozen architecture documents

without requiring undocumented knowledge or manual intervention.

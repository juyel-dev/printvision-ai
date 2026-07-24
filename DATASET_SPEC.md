# DATASET SPECIFICATION

Project:
PW Print Optimizer

Document:
DATASET_SPEC.md

Version:
1.0

Status:
Frozen

---

# 1. Purpose

The dataset is the foundation of the Tiny Vision Model.

The quality of the model depends primarily on the quality, diversity, consistency, and correctness of the dataset.

The dataset is considered a long-term project asset.

Models can be replaced.

Datasets should continuously improve.

---

# 2. Objectives

The dataset must teach the Tiny Vision Model how to understand educational PDF pages.

The dataset should NOT teach image enhancement.

Instead, it teaches:

• What exists

• Where it exists

• What kind of content it is

• How confident the model is

• Which optimization pipeline should be preferred

---

# 3. Dataset Philosophy

Dataset First.

Model Second.

Training Third.

Deployment Last.

Never collect data just to increase quantity.

Collect data to increase diversity.

---

# 4. Dataset Versions

dataset_v1/

dataset_v2/

dataset_v3/

...

Every version is immutable.

Never overwrite previous datasets.

---

# 5. Directory Structure

dataset/

    raw_pdf/

    rendered_pages/

    thumbnails/

    annotations/

    metadata/

    benchmark/

    splits/

    exports/

    docs/

---

# 6. Folder Description

## raw_pdf/

Original uploaded PDFs.

Never modified.

Never renamed after import.

Acts as the permanent source.

---

## rendered_pages/

One PNG per page.

Example

physics_page_0001.png

---

## thumbnails/

224×224

Used only for Tiny Vision Model inference/training.

Never used for print generation.

---

## annotations/

Ground truth.

One annotation per page.

Example

physics_page_0001.json

---

## metadata/

Information about PDFs.

Example

Teacher

Subject

Source

Language

Theme

Semester

Institute

Collection Date

Dataset Version

---

## benchmark/

Reference outputs.

Used for quality comparison.

Not used for training.

---

## splits/

Contains

train.txt

validation.txt

test.txt

No duplicate pages across splits.

---

## exports/

Generated datasets ready for training.

ONNX-compatible metadata.

Training manifests.

---

## docs/

Dataset documentation.

Change log.

Known issues.

Statistics.

Coverage report.

---

# 7. Naming Rules

Every page must have a globally unique ID.

Example

PW_PHY_2026_000001

PW_PHY_2026_000002

Never rename IDs.

IDs are permanent.

---

# 8. Rendering Rules

Every PDF page becomes:

PNG

Lossless

Same DPI

Same renderer

Same settings

Rendering settings must remain identical for the entire dataset.

---

# 9. Thumbnail Rules

Generated from rendered pages.

Never directly from PDF.

Fixed resolution.

224×224

RGB

Consistent preprocessing.

---

# 10. Annotation Philosophy

Annotations describe reality.

Never assumptions.

Never guesses.

If uncertain:

Mark as Unknown.

Never invent labels.

---

# 11. Annotation Granularity

Annotation is page-level.

Future versions may include region-level annotations.

The schema should support future expansion.

---

# 12. Metadata Fields

Every page should store:

Dataset Version

PDF ID

Page Number

Subject

Teacher

Language

Theme

Collection Source

Annotation Version

Reviewer

Date

---

# 13. Train / Validation / Test

Recommended

Train

70%

Validation

15%

Test

15%

Pages from the same PDF should never appear in different splits.

This prevents data leakage.

---

# 14. Diversity Requirements

The dataset should include:

Physics

Chemistry

Biology

Mathematics

Dark Slides

Light Slides

Colorful Slides

Teacher Photos

Handwriting

Printed Notes

Tables

Graphs

Flowcharts

Microscope Images

Chemical Structures

Biological Diagrams

Mixed Content

Old PDFs

New PDFs

Low-quality scans

High-quality exports

Different teachers

Different years

Different institutes

---

# 15. Benchmark Set

Benchmark pages should never be used during training.

Purpose

Quality evaluation

Regression testing

Performance comparison

Future model comparison

---

# 16. Dataset Growth Strategy

v1

1,000 pages

↓

v2

5,000 pages

↓

v3

10,000 pages

↓

v4

25,000 pages

↓

Continue growing.

Never discard valuable data.

---

# 17. Dataset Quality Rules

Reject pages that are:

Corrupted

Incomplete

Unreadable

Duplicate

Broken renders

Invalid PDFs

Accept difficult pages.

Difficult pages improve the model.

---

# 18. Dataset Balance

Avoid dominance of one content type.

Avoid collecting only one teacher.

Avoid collecting only one subject.

Balanced datasets generalize better.

---

# 19. Review Process

Every annotation should be reviewable.

Reviewer information should be stored.

Future corrections should create new annotation versions.

Never silently edit annotations.

---

# 20. Version Control

Dataset Version

Annotation Version

Schema Version

Export Version

Training Version

All should be independently tracked.

---

# 21. Future Compatibility

The dataset must support:

New labels

New annotation formats

Region annotations

Object detection

Segmentation

Future models

without rebuilding the entire dataset.

---

# 22. Long-Term Goal

The dataset should become the single source of truth for every future Tiny Vision Model.

Every future model must be trainable from this dataset with minimal additional work.

The dataset is expected to outlive multiple generations of models, engines, and web application versions.

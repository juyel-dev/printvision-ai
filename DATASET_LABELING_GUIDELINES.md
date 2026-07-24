# DATASET LABELING GUIDELINES

Project:
PW Print Optimizer

Document:
DATASET_LABELING_GUIDELINES.md

Version:
1.0

Status:
Frozen

---

# 1. Purpose

This document defines how every dataset page must be labeled.

The primary objective is consistency.

Correct and consistent labels are more valuable than a larger dataset with inconsistent annotations.

When uncertain, always choose consistency over complexity.

---

# 2. Labeling Philosophy

The model should learn:

"What is actually present?"

NOT

"What someone thinks should be there?"

Always label observable visual content.

Never label assumptions.

---

# 3. Annotation Levels

Current Version

Page-Level

Future Versions

Region-Level

Object-Level

Segmentation

Pixel-Level

The schema should support future expansion.

---

# 4. Primary Page Categories

Each page must belong to ONE primary category.

TEXT

Mostly printed text.

PHOTO

Mostly photographic content.

DIAGRAM

Mostly diagrams, graphs or illustrations.

HANDWRITING

Mostly handwritten content.

MIXED

Combination of multiple content types.

UNKNOWN

Reviewer cannot confidently classify.

---

# 5. Secondary Content Labels

A page may contain multiple secondary labels.

Highlight

Photo

Diagram

Graph

Flowchart

Table

Formula

Equation

Handwriting

Colored Background

Dark Theme

Logo

Watermark

QR Code

Screenshot

Sticky Note

Margin Notes

Teacher Annotation

Stamp

These are independent labels.

---

# 6. Highlight Detection

If highlighted text exists:

Record

Present

Approximate Color

Confidence

Possible colors

Yellow

Green

Blue

Pink

Orange

Other

Unknown

Future versions may include exact color values.

---

# 7. Background Type

Choose one.

White

Light

Dark

Colored

Gradient

Mixed

Unknown

---

# 8. Text Density

Low

Medium

High

Very High

Unknown

---

# 9. Image Density

None

Low

Medium

High

Very High

---

# 10. Handwriting

None

Small

Medium

Heavy

Unknown

---

# 11. Diagram Density

None

Few

Medium

Many

---

# 12. Tables

Present

Not Present

Unknown

---

# 13. Mathematical Content

Present

Not Present

Unknown

---

# 14. Scientific Illustrations

Present

Not Present

Unknown

Examples

Chemical Structures

Biological Diagrams

Physics Illustrations

Laboratory Images

Medical Images

---

# 15. Screenshot Detection

Present

Not Present

Unknown

Screenshots often require different optimization.

---

# 16. Color Complexity

Very Low

Low

Medium

High

Very High

Used for pipeline recommendation.

---

# 17. Print Difficulty

Easy

Medium

Hard

Very Hard

Unknown

This is not used for training directly.

Used for benchmarking.

---

# 18. Human Readability

Excellent

Good

Average

Poor

Unreadable

Reference only.

---

# 19. Recommended Processing Pipeline

Annotators may recommend

Pipeline_A

Pipeline_B

Pipeline_C

Pipeline_D

Pipeline_E

Future pipelines may be added.

This recommendation is optional.

---

# 20. Annotation Confidence

Very High

High

Medium

Low

Unknown

Never guess.

---

# 21. Difficult Cases

If unsure:

Use UNKNOWN.

Never invent labels.

Never force a decision.

---

# 22. Duplicate Pages

Duplicates should still be identified.

Metadata must indicate duplicate source.

Future deduplication tools may remove them.

---

# 23. Annotation Review

Every annotation should support:

Reviewer

Date

Version

Notes

Reason for correction

No anonymous edits.

---

# 24. Label Consistency Rules

Never change label definitions midway through a dataset.

If definitions evolve:

Create a new Annotation Version.

Never silently relabel old data.

---

# 25. Future Region Annotation

Future versions should support:

Bounding Boxes

Polygon Regions

Segmentation Masks

Region Metadata

Region Confidence

Without changing existing page annotations.

---

# 26. Quality Checklist

Before saving:

✓ Page category selected

✓ Secondary labels verified

✓ Background labeled

✓ Confidence assigned

✓ Metadata complete

✓ Reviewer information stored

---

# 27. Golden Rule

When two reviewers look at the same page,

they should produce nearly identical labels.

If they do not,

the labeling guideline is incomplete and must be improved.

The objective of this document is not maximum detail,

but maximum consistency across the entire dataset.

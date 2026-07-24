# CONTENT MAP SCHEMA

Project:
PW Print Optimizer

Document:
CONTENT_MAP_SCHEMA.md

Version:
1.0

Status:
Frozen

---

# 1. Purpose

The Content Map is the only communication protocol between the Tiny Vision Model and the downstream processing system.

The Tiny Vision Model produces it.

The Rule Engine consumes it.

The Rust Engine executes it.

No other interface is allowed.

---

# 2. Philosophy

The Content Map represents understanding.

It does NOT contain image pixels.

It does NOT contain processed images.

It only contains structured information describing the page.

---

# 3. Stability

The Content Map is a public API.

Internal model architecture may change.

Training framework may change.

Neural network may change.

The Content Map must remain stable.

---

# 4. Schema Version

Every Content Map contains

Schema Version

Example

schema_version

1

Future versions

2

3

4

must remain backward compatible whenever possible.

---

# 5. Page Information

Each page begins with

Page ID

PDF ID

Page Number

Width

Height

Rotation

Orientation

Example

Landscape

Portrait

---

# 6. Page Classification

Exactly one

Text

Mixed

Photo

Diagram

Handwriting

Unknown

Confidence included.

---

# 7. Background

Type

White

Dark

Colored

Gradient

Mixed

Confidence included.

---

# 8. Page Statistics

Estimated

Text Density

Image Density

Diagram Density

Highlight Density

Color Complexity

These values help pipeline selection.

---

# 9. Regions

Each detected region contains

Region ID

Type

Bounding Box

Confidence

Priority

Visibility

Recommended Pipeline

Every region is independent.

---

# 10. Region Types

Text

Photo

Diagram

Highlight

Formula

Table

Graph

Handwriting

Logo

Watermark

Screenshot

Unknown

Future types may be added.

---

# 11. Bounding Box

Coordinates

x

y

width

height

Normalized coordinates are preferred.

Independent of page resolution.

---

# 12. Priority

Critical

High

Medium

Low

Priority indicates preservation importance.

Example

Highlighted Formula

↓

Critical

Background Decoration

↓

Low

---

# 13. Visibility

Visible

Partially Visible

Occluded

Unknown

---

# 14. Recommendations

The model suggests actions.

Examples

Preserve Highlight

Avoid Threshold

Preserve Photo

Increase Contrast

Whiten Background

Protect Diagram

Recommendations are advisory.

---

# 15. Processing Risk

Very Low

Low

Medium

High

Very High

High-risk regions should receive conservative processing.

---

# 16. Confidence

Every prediction contains confidence.

Range

0.0

↓

1.0

Low confidence should never trigger aggressive processing.

---

# 17. Global Recommendations

Entire page recommendations.

Examples

Photo-heavy

Dark Theme

Mixed Content

Text Dominant

Large Diagram

These guide Rule Engine decisions.

---

# 18. Unknown Handling

Unknown is always valid.

Unknown never causes failure.

Unknown triggers Safe Processing.

---

# 19. Extensibility

Future versions may include

Reading Order

Nested Regions

Relationships

Semantic Groups

Segmentation Masks

without breaking existing implementations.

---

# 20. Validation Rules

Every Content Map must pass validation.

Required

Version

Page Info

Page Type

Confidence

Missing fields invalidate the Content Map.

---

# 21. Rule Engine Contract

The Rule Engine must never inspect pixels.

It only reads the Content Map.

All processing decisions originate here.

---

# 22. Rust Engine Contract

Rust never performs classification.

Rust never estimates confidence.

Rust only executes the selected processing strategy.

---

# 23. Debug Mode

Development builds may visualize

Bounding Boxes

Labels

Confidence

Priority

Pipeline Selection

Production builds disable visualization.

---

# 24. Backward Compatibility

Older Content Maps should continue working whenever practical.

Schema evolution must be versioned.

Breaking changes require a major version.

---

# 25. Example Structure

Page

↓

Metadata

↓

Statistics

↓

Regions

↓

Recommendations

↓

Validation

↓

End

---

# 26. Golden Rules

The Content Map is the single source of truth.

Never bypass it.

Never duplicate its responsibilities.

Never embed business logic inside it.

It describes.

It never decides.

---

# 27. Definition of Success

The Content Map is successful when any compliant Rule Engine can make correct decisions without knowing anything about the underlying AI model.

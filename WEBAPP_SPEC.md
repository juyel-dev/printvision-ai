# WEB APPLICATION SPECIFICATION

Project:
PW Print Optimizer

Version:
1.0

Status:
Frozen

---

# 1. Vision

The web application should feel effortless.

The user should complete the entire workflow with almost no learning.

The interface should guide the user one step at a time.

The application is a workflow, not a dashboard.

---

# 2. Core Principles

Minimal

Fast

Responsive

Offline

Accessible

Predictable

No unnecessary features.

---

# 3. Technology

Frontend

React

TypeScript

Rust WASM

Framer Motion

PDF Rendering Library

No backend required.

Deploy on GitHub Pages.

---

# 4. User Workflow

Phase 1

Upload PDFs

↓

Arrange

↓

Merge

↓

Preview

↓

Download (Optional)

↓

Next

---

Phase 2

Analyze

↓

Optimize

↓

Preview

↓

Download (Optional)

↓

Next

---

Phase 3

Choose Layout

↓

Generate

↓

Preview

↓

Download

---

Done

↓

Try Another

↓

Feedback

---

# 5. Navigation

Each phase occupies one screen.

No hidden pages.

No sidebars.

No settings panel.

Users always know where they are.

---

# 6. Progress

Display:

Current Phase

Current Step

Current Page

Estimated Remaining Time (optional)

Processing Status

Examples:

Analyzing...

Optimizing Photos...

Generating Layout...

Writing PDF...

---

# 7. Preview

Preview is temporary.

Rules:

One preview only.

Destroy preview after Next.

Never keep previous previews in memory.

Preview should use reduced resolution.

High-resolution data remains internal.

---

# 8. Memory Policy

Maximum:

One Preview

One Processing Page

One Output Buffer

Release memory immediately after each phase.

No hidden caches.

---

# 9. Animations

Animations should communicate state.

Use:

Fade

Slide

Progress

Success

Never delay processing.

Animation should never reduce responsiveness.

---

# 10. Error Handling

Simple messages.

Examples:

PDF cannot be opened.

Unsupported PDF.

Processing failed.

Browser memory is insufficient.

Avoid technical jargon.

---

# 11. Download

Allow download after every major phase.

Merged PDF

↓

Optimized PDF

↓

Final Print PDF

Users should never lose progress.

---

# 12. Feedback

Final screen only.

★★★★★

Optional message

Send

Telegram Bot

↓

Google Apps Script

↓

Developer

No document data is transmitted.

Only feedback text.

---

# 13. Mobile Support

Responsive.

Touch friendly.

Large buttons.

Readable typography.

No hover-only interactions.

---

# 14. Accessibility

Keyboard navigation.

Screen reader labels.

High contrast.

Large touch targets.

---

# 15. Performance Goals

Startup < 3 seconds (typical device)

Responsive UI

No frozen interface

Streaming processing

Constant memory usage

---

# 16. Privacy

No uploads.

No accounts.

No login.

No analytics on PDFs.

Everything runs locally.

---

# 17. Future Compatibility

New layouts

New models

New Rust engines

New processing pipelines

without redesigning the UI.

---

# 18. Golden Rules

The UI never exposes internal complexity.

Users should only think:

Upload

↓

Next

↓

Next

↓

Download

Everything else is automatic.

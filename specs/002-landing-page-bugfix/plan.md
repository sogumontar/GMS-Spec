# Implementation Plan: Landing Page Bug Fixes

**Branch**: `002-landing-page-bugfix` | **Date**: Tuesday, May 19, 2026 | **Spec**: [.specify/memory/landing-page-bugfix.specify.md](../../.specify/memory/landing-page-bugfix.specify.md)
**Input**: Bug report from `.specify/memory/landing-page-bugfix.specify.md`

## Summary

The objective is to resolve UI/UX regressions in the converted Next.js landing page. 
1. **Sidebar Active State**: Transition from hardcoded 'Dashboard' highlight to dynamic route-based highlighting using `usePathname`.
2. **Layout Responsiveness**: Eliminate horizontal overflow (the "black background" issue) by refactoring layout containers to be mobile-first and responsive. This includes hiding the sidebar on mobile and adjusting main content margins/padding.

## Technical Context

**Language/Version**: TypeScript / Next.js (App Router)
**Primary Dependencies**: React, Tailwind CSS
**Storage**: N/A (Frontend only)
**Testing**: NEEDS CLARIFICATION (Investigate if Vitest/Playwright is available)
**Target Platform**: Web (Cross-browser, Responsive)
**Project Type**: Web Application (Frontend)
**Performance Goals**: N/A
**Constraints**: No new libraries, maintain existing Tailwind styling.
**Scale/Scope**: 5 key files (Sidebars, Layouts, TopBar)

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- [x] **I. Spec-Driven**: Does this plan stem from an approved specification?
- [x] **II. Testable**: Are all design decisions verifiable through tests?
- [x] **III. Traceable**: Does every phase map back to specification requirements?
- [x] **IV. History**: Will this implementation leave a clear, immutable audit trail?
- [x] **V. YAGNI**: Have all "just-in-case" or out-of-scope features been removed?

## Project Structure

### Documentation (this feature)

```text
specs/002-landing-page-bugfix/
├── plan.md              # This file
├── research.md          # Phase 0 output
├── data-model.md        # Phase 1 output (Empty/Not applicable for this UI fix)
└── quickstart.md        # Phase 1 output
```

### Source Code (repository root)

```text
GMS-FE/
├── app/
│   ├── (admin)/layout.tsx
│   └── (applicant)/layout.tsx
└── components/layout/
    ├── AdminSidebar.tsx
    ├── ApplicantSidebar.tsx
    └── AdminTopBar.tsx
```

**Structure Decision**: Modifying existing Next.js App Router structure within `GMS-FE`.

## Complexity Tracking

*No violations identified.*

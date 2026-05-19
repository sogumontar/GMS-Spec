# Tasks: Landing Page Bug Fixes

**Input**: Design documents from `specs/002-landing-page-bugfix/`
**Prerequisites**: plan.md, spec.md, research.md, quickstart.md

**Tests**: Manual verification as per `research.md` (no automated test framework available).

**Organization**: Tasks are grouped by bug report (User Story) to enable independent implementation and testing.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (US1: Sidebar Active State, US2: Layout Responsiveness)
- Include exact file paths in descriptions

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Verification of current state and preparation

- [X] T001 Verify current UI bugs (Sidebar highlight and horizontal overflow) in development environment as described in quickstart.md

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure for UI fixes

- [X] T002 Ensure project uses Next.js 13+ App Router (confirmed in plan.md) to support `usePathname`

**Checkpoint**: Foundation ready - UI bug fixes can now begin

---

## Phase 3: User Story 1 - Sidebar Active State (Priority: P1) 🎯 MVP

**Goal**: Sidebar navigation dynamically tracks and highlights the active page based on the current URL.

**Independent Test**: Navigate between different routes (e.g., `/admin/dashboard` vs `/admin/operations`) and verify that the highlight moves to the correct link.

### Implementation for User Story 1

- [X] T003 [P] [US1] Implement dynamic active state using `usePathname` in `GMS-FE/components/layout/AdminSidebar.tsx`
- [X] T004 [P] [US1] Implement dynamic active state using `usePathname` in `GMS-FE/components/layout/ApplicantSidebar.tsx`
- [X] T005 [US1] Verify sidebar highlighting updates correctly on page refresh and navigation

**Checkpoint**: Sidebar Active State should be fully functional and testable independently

---

## Phase 4: User Story 2 - Layout Responsiveness & Overflow (Priority: P2)

**Goal**: Eliminate horizontal overflow and ensure the layout adapts to mobile devices with a toggleable sidebar.

**Independent Test**: Resize browser to mobile width (<768px). Verify that the sidebar is hidden, the black background is gone, and the "Hamburger" menu opens the sidebar.

### Implementation for User Story 2

- [X] T006 [US2] Add sidebar toggle state (mobile menu) in `GMS-FE/app/(admin)/layout.tsx`
- [X] T007 [US2] Make `AdminSidebar` visibility responsive (hidden on mobile, fixed on desktop) and controlled by state in `GMS-FE/app/(admin)/layout.tsx`
- [X] T008 [US2] Update `AdminTopBar.tsx` to accept and trigger the sidebar toggle function
- [X] T009 [US2] Refactor `GMS-FE/app/(admin)/layout.tsx` to use responsive margins (e.g., `md:ml-[260px] ml-0`) on the main content container
- [X] T010 [US2] Refactor `GMS-FE/app/(applicant)/layout.tsx` to use responsive margins and eliminate `w-full` overflow issue
- [X] T011 [US2] Verify elimination of horizontal overflow ("black background") across all breakpoints

**Checkpoint**: Layout Responsiveness should be fully functional and testable independently

---

## Phase 5: Polish & Cross-Cutting Concerns

**Purpose**: Final validation

- [X] T012 Code cleanup: Remove hardcoded active classes that were replaced by dynamic logic
- [X] T013 Run full validation as per `specs/002-landing-page-bugfix/quickstart.md`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: Can start immediately
- **Foundational (Phase 2)**: Depends on Phase 1
- **User Story 1 (Phase 3)**: Depends on Phase 2
- **User Story 2 (Phase 4)**: Depends on Phase 2
- **Polish (Phase 5)**: Depends on Phases 3 and 4

### Parallel Opportunities

- T003 and T004 (Admin vs Applicant sidebars) can be done in parallel.
- Once the active state logic is proven in one sidebar, it can be applied to the other.
- Layout responsiveness (US2) can be worked on independently of US1.

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Setup and Foundational checks.
2. Fix the Sidebar Active State (US1) first as it provides immediate visual feedback on navigation correctness.
3. Validate US1 independently.

### Incremental Delivery

1. Fix Sidebar Active State.
2. Fix Admin Layout responsiveness (higher complexity due to toggle).
3. Fix Applicant Layout responsiveness (simpler margin fix).
4. Final polish.

# Tasks: Stitch AI Prototype Integration

**Input**: Design documents from `/specs/001-stitch-ai-prototype/`
**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, quickstart.md

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

---

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Project initialization and basic structure

- [x] T001 Create `GMS-FE` directory structure per implementation plan
- [x] T002 Initialize Next.js project in `GMS-FE/` with TypeScript and App Router
- [x] T003 [P] Configure Sonner or React-Hot-Toast for mock notifications in `GMS-FE/package.json`
- [x] T004 [P] Copy all assets from `stitch-source/` to `public/stitch-assets/`

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure for mocking and layout that MUST be complete before ANY user story

- [x] T005 [P] Implement `MockProvider` and `useMockAction` hook in `GMS-FE/components/providers/MockProvider.tsx`
- [x] T006 [P] Create `PublicLayout` in `GMS-FE/app/(public)/layout.tsx` (Header/Footer)
- [x] T007 [P] Create `AdminLayout` in `GMS-FE/app/(admin)/layout.tsx` (Sidebar/TopBar)
- [x] T008 [P] Create `ApplicantLayout` in `GMS-FE/app/(applicant)/layout.tsx` (Sidebar/BottomNav)
- [x] T009 [P] Implement `ui` atomic components (Button, Input, Badge) in `GMS-FE/components/ui/`

**Checkpoint**: Foundation ready - user story implementation can now begin.

---

## Phase 3: User Story 1 - Seamless Navigation (Priority: P1) 🎯 MVP

**Goal**: Enable navigation between all 10 prototype pages.

**Independent Test**: Start at `/` and click through to all admin and applicant routes.

### Implementation for User Story 1

- [x] T010 [P] [US1] Create Landing Page in `GMS-FE/app/(public)/page.tsx` using `LandingPage.html`
- [x] T011 [P] [US1] Create Registration Page in `GMS-FE/app/(public)/register/page.tsx` using `RegistrationPage.html`
- [x] T012 [P] [US1] Create Admin Dashboard shell in `GMS-FE/app/(admin)/admin/dashboard/page.tsx`
- [x] T013 [P] [US1] Create Applicant Dashboard shell in `GMS-FE/app/(applicant)/applicant/dashboard/page.tsx`
- [x] T014 [US1] Update all `<a>` tags in `PublicHeader` to use Next.js `Link` in `GMS-FE/components/layout/PublicHeader.tsx`
- [x] T015 [US1] Update all `<a>` tags in `AdminSidebar` to use Next.js `Link` in `GMS-FE/components/layout/AdminSidebar.tsx`
- [x] T016 [US1] Implement "Placeholder" page for missing routes in `GMS-FE/app/not-found.tsx`

**Checkpoint**: Navigation MVP complete.

---

## Phase 4: User Story 2 - Interactive Form Feedback (Priority: P1)

**Goal**: Mock success feedback for all form submissions.

**Independent Test**: Submit the Registration form and verify the success toast appears.

### Implementation for User Story 2

- [x] T017 [P] [US2] Extract `RegistrationForm` component to `GMS-FE/components/features/RegistrationForm.tsx`
- [x] T018 [P] [US2] Extract `ApplicationForm` component to `GMS-FE/components/features/ApplicationForm.tsx`
- [x] T019 [US2] Attach `useMockAction` to `RegistrationForm` submit in `GMS-FE/components/features/RegistrationForm.tsx`
- [x] T020 [US2] Attach `useMockAction` to `ApplicationForm` submit in `GMS-FE/components/features/ApplicationForm.tsx`
- [x] T021 [US2] Implement automatic redirect from Registration to Dashboard after mock success in `GMS-FE/components/features/RegistrationForm.tsx`

---

## Phase 5: User Story 3 - Mock Data Presentation (Priority: P2)

**Goal**: Populate dashboards and tables with realistic mock data.

**Independent Test**: Navigate to `/admin/inventory` and see 5+ rows of inventory items.

### Implementation for User Story 3

- [x] T022 [P] [US3] Create mock data constants in `GMS-FE/lib/mock-data.ts` (Inventory, Users, Applications)
- [x] T023 [P] [US3] Implement `DataTable` component in `GMS-FE/components/ui/DataTable.tsx`
- [x] T024 [P] [US3] Implement `MetricCard` component in `GMS-FE/components/features/MetricCard.tsx`
- [x] T025 [US3] Populate Inventory Page in `GMS-FE/app/(admin)/admin/inventory/page.tsx` with mock data
- [x] T026 [US3] Populate User Management Page in `GMS-FE/app/(admin)/admin/users/page.tsx` with mock data
- [x] T027 [US3] Populate Dashboard metrics in `GMS-FE/app/(admin)/admin/dashboard/page.tsx`

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [x] T028 [P] Replace all `<img>` tags with Next.js `Image` across all components
- [x] T029 [P] Audit all JSX for Constitution compliance (className, self-closing tags)
- [x] T030 Final walkthrough of all 10 pages to ensure visual consistency with `stitch-source`
- [x] T031 Run `quickstart.md` validation to ensure all instructions are accurate

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies.
- **Foundational (Phase 2)**: Depends on Setup.
- **User Stories (Phase 3+)**: All depend on Foundational completion.
  - US1 (Navigation) is the prerequisite for meaningful US2/US3 testing.

### Parallel Opportunities

- T003, T004 (Setup)
- T005, T006, T007, T008, T009 (Foundational UI & Layouts)
- All [US1] page creations (T010 - T013)
- All [US3] mock data UI (T022 - T024)

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1 & 2.
2. Complete Phase 3 (Navigation).
3. **VALIDATE**: Ensure all 10 pages are reachable.

### Incremental Delivery

1. Foundation -> Navigation (MVP) -> Interaction (US2) -> Data (US3) -> Polish.

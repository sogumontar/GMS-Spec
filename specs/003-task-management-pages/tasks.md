# Tasks: Task Management Module

**Input**: Design documents from `/specs/003-task-management-pages/`
**Prerequisites**: plan.md, spec.md, research.md, data-model.md

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

---

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Project initialization and basic structure

- [x] T001 Update `GMS-FE/components/layout/AdminSidebar.tsx` to include "Tasks" link with active route highlighting
- [x] T002 [P] Extend `GMS-FE/lib/mock-data.ts` with initial `TASK_DATA` and `ASSIGNEE_DATA` based on data-model.md
- [x] T003 [P] Ensure Tailwind CSS configuration in `GMS-FE/tailwind.config.ts` includes the specific color palette from `MyTaskPage.html`

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [x] T004 [P] Create `GMS-FE/lib/types/tasks.ts` and define TypeScript interfaces for `Task`, `Assignee`, `Attachment`, and `Activity`
- [x] T005 [P] Create `TaskBadge` component in `GMS-FE/components/ui/Badge.tsx` (or update existing) for status visualization
- [x] T006 [P] Create `WorkloadBar` component in `GMS-FE/components/ui/WorkloadBar.tsx` for resource visualization

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - Manage Personal Task List (Priority: P1) 🎯 MVP

**Goal**: Recruitment Officer can view, search, and filter their priority tasks in a centralized list.

**Independent Test**: Navigate to `/admin/tasks` and verify the list displays mock data, search filters by title, and status dropdown updates the view.

### Implementation for User Story 1

- [x] T007 [P] [US1] Create `TaskCard` component in `GMS-FE/components/tasks/TaskCard.tsx` following `MyTaskPage.html` design
- [x] T008 [P] [US1] Create `FilterSelect` component in `GMS-FE/components/tasks/FilterSelect.tsx` for status and category filtering
- [x] T009 [US1] Implement main task list page in `GMS-FE/app/(admin)/admin/tasks/page.tsx` with search and filter functionality

**Checkpoint**: User Story 1 is functional and testable independently.

---

## Phase 4: User Story 2 - Create New Workflow Task (Priority: P2)

**Goal**: Recruitment Officer can initiate new recruitment workflow tasks via a creation form.

**Independent Test**: Navigate to `/admin/tasks/new`, fill the form, and verify submission adds a task (to local mock state).

### Implementation for User Story 2

- [x] T010 [P] [US2] Create `TaskForm` component in `GMS-FE/components/tasks/TaskForm.tsx` supporting title, description, and priority fields
- [x] T011 [US2] Implement creation page in `GMS-FE/app/(admin)/admin/tasks/new/page.tsx` using `TaskForm`

**Checkpoint**: User Story 2 is functional and testable independently.

---

## Phase 5: User Story 3 - View and Edit Task Details (Priority: P2)

**Goal**: Recruitment Officer can see detailed information/attachments and update task details.

**Independent Test**: Click a task to view `/admin/tasks/[id]`, verify metadata and attachments, then navigate to `/admin/tasks/[id]/edit` and save changes.

### Implementation for User Story 3

- [x] T012 [P] [US3] Create `TaskDetailSidebar` component in `GMS-FE/components/tasks/TaskDetailSidebar.tsx` showing assignee and metadata
- [x] T013 [P] [US3] Create `AttachmentList` component in `GMS-FE/components/tasks/AttachmentList.tsx` for displaying task files
- [x] T014 [US3] Implement detail view page in `GMS-FE/app/(admin)/admin/tasks/[id]/page.tsx`
- [x] T015 [US3] Implement edit page in `GMS-FE/app/(admin)/admin/tasks/[id]/edit/page.tsx` reusing `TaskForm`

**Checkpoint**: User Story 3 is functional and testable independently.

---

## Phase 6: User Story 4 - Assign Tasks to Team Members (Priority: P3)

**Goal**: Recruitment Officer can assign tasks to team members based on workload.

**Independent Test**: Navigate to `/admin/tasks/[id]/assign`, search for a user, and click "Assign" to verify status update.

### Implementation for User Story 4

- [x] T016 [P] [US4] Create `UserCard` component in `GMS-FE/components/tasks/UserCard.tsx` with workload visualization
- [x] T017 [US4] Implement assignment page in `GMS-FE/app/(admin)/admin/tasks/[id]/assign/page.tsx` with user search

**Checkpoint**: User Story 4 is functional and testable independently.

---

## Phase 7: Polish & Cross-Cutting Concerns

**Purpose**: Visual refinements and final validation

- [x] T018 [P] Apply micro-interactions and hover effects to `TaskCard` and buttons per `stitch-source` references
- [x] T019 [P] Verify `next/image` usage for all avatars and assets per project constitution
- [x] T020 Run all validation scenarios from `specs/003-task-management-pages/quickstart.md`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: Can start immediately.
- **Foundational (Phase 2)**: Depends on T001-T003 completion.
- **User Stories (Phase 3+)**: All depend on Phase 2 completion.
- **Polish (Phase 7)**: Depends on all user stories being complete.

### User Story Dependencies

- **US1 (P1)**: Independent after Phase 2.
- **US2 (P2)**: Independent after Phase 2.
- **US3 (P2)**: Independent after Phase 2.
- **US4 (P3)**: Independent after Phase 2.

### Parallel Opportunities

- T002 and T003 can be done in parallel.
- T004, T005, T006 can be done in parallel.
- US1, US2, US3, and US4 can be developed in parallel once Phase 2 is complete.
- All tasks marked `[P]` within a phase can run in parallel.

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1 & 2 (Setup and Foundation).
2. Complete Phase 3 (US1).
3. Validate US1 via `/admin/tasks`.

### Incremental Delivery

1. Foundation ready.
2. US1 added → Test independently.
3. US2 added → Test independently.
4. US3 added → Test independently.
5. US4 added → Test independently.

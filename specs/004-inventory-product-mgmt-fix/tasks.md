# Tasks: Inventory & Product Management Enhancements

**Input**: Design documents from `/specs/004-inventory-product-mgmt-fix/`
**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, contracts/

**Tests**: The examples below include test tasks. Tests are OPTIONAL - only include them if explicitly requested in the feature specification.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- **Single project**: `src/`, `tests/` at repository root
- **Web app**: `backend/src/`, `frontend/src/`
- **Mobile**: `api/src/`, `ios/src/` or `android/src/`
- Paths shown below assume single project - adjust based on plan.md structure

## Phase 1: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [x] T001 Create new types for Product and Inventory Metrics in `GMS-FE/lib/types/inventory.ts`.
- [x] T002 Extend `INVENTORY_DATA` in `GMS-FE/lib/mock-data.ts` to include richer product data (matching `Product` entity).
- [x] T003 Ensure `TASK_DATA` in `GMS-FE/lib/mock-data.ts` provides sufficient sample data for task pages if needed for styling fixes.

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 2: User Story 1 - Rich Inventory Overview (Priority: P1) 🎯 MVP

**Goal**: Provide a comprehensive overview of inventory, matching `InventoryManagement.html`.

**Independent Test**: Navigate to `/admin/inventory` and visually verify the layout, presence of Bento grid metrics, and the detailed product data table.

### Implementation for User Story 1

- [x] T004 [US1] Create `InventoryOverview.tsx` component for Bento grid metrics in `GMS-FE/components/features/inventory/InventoryOverview.tsx` (converting relevant parts of `InventoryManagement.html`).
- [x] T005 [US1] Modify `GMS-FE/app/(admin)/admin/inventory/page.tsx` to implement the main layout, integrate `InventoryOverview.tsx`, and adapt the data table structure from `InventoryManagement.html`.
- [x] T006 [US1] Enhance or ensure `DataTable.tsx` (or a dedicated table component for inventory) in `GMS-FE/components/ui/DataTable.tsx` supports the required features for inventory display.
- [x] T007 [US1] Ensure proper styling and responsiveness for the entire Inventory page (`/admin/inventory`) using Tailwind CSS, adhering to `InventoryManagement.html` visuals.

**Checkpoint**: At this point, User Story 1 should be fully functional and testable independently

---

## Phase 3: User Story 2 - Product Lifecycle Management (Priority: P2)

**Goal**: Enable adding, viewing, and editing products via dedicated responsive pages.

**Independent Test**: Navigate to `/admin/inventory/new`, `/admin/inventory/[id]`, `/admin/inventory/[id]/edit` and verify form fields, data display, and responsiveness against `ProductAdd.html`, `ProductDetail.html`, and `ProductEdit.html`.

### Implementation for User Story 2

- [x] T008 [P] [US2] Create `ProductForm.tsx` component (for Add/Edit product forms) in `GMS-FE/components/features/inventory/ProductForm.tsx`, converting form elements from `ProductAdd.html` and `ProductEdit.html` to JSX.
- [x] T009 [P] [US2] Create `ProductDetailView.tsx` component (for product details display) in `GMS-FE/components/features/inventory/ProductDetailView.tsx`, converting `ProductDetail.html` to JSX.
- [x] T010 [US2] Create new page `GMS-FE/app/(admin)/admin/inventory/new/page.tsx` for adding new products, integrating `ProductForm.tsx`.
- [x] T011 [US2] Create dynamic route page `GMS-FE/app/(admin)/admin/inventory/[id]/page.tsx` for displaying product details, integrating `ProductDetailView.tsx`.
- [x] T012 [US2] Create dynamic route page `GMS-FE/app/(admin)/admin/inventory/[id]/edit/page.tsx` for editing products, integrating `ProductForm.tsx`.
- [x] T013 [US2] Implement mock data handling for Add, View, and Edit product functionality within `GMS-FE/lib/mock-data.ts` to support the new pages.

**Checkpoint**: At this point, User Stories 1 AND 2 should both work independently

---

## Phase 4: User Story 3 - Navigation & Task Page Consistency (Priority: P2)

**Goal**: Update sidebar for inventory and fix transparent task page backgrounds.

**Independent Test**: Visually inspect `AdminSidebar` for the new "Inventory" link and navigate to task pages (e.g., `/admin/tasks`, `/admin/tasks/new`, `/admin/tasks/[id]`) to check for a solid, consistent background.

### Implementation for User Story 3

- [x] T014 [US3] Update `GMS-FE/components/layout/AdminSidebar.tsx` to include an active navigation link to `/admin/inventory` with an appropriate Material Symbols icon.
- [x] T015 [US3] Apply solid background styling to `GMS-FE/app/(admin)/admin/tasks/page.tsx` to resolve transparency issues and align with the project's design system.
- [x] T016 [P] [US3] Review and apply solid background styling to other task-related pages such as `GMS-FE/app/(admin)/admin/tasks/[id]/page.tsx` and `GMS-FE/app/(admin)/admin/tasks/new/page.tsx` to ensure consistent visual appearance.

**Checkpoint**: All user stories should now be independently functional

---

## Phase 5: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [x] T017 Conduct a final review of all new and modified components for responsiveness across various screen sizes and adherence to overall project conventions.
- [x] T018 Update `specs/004-inventory-product-mgmt-fix/quickstart.md` with clear instructions to run the application and test all new and modified features.

---

## Dependencies & Execution Order

### Phase Dependencies

- **Foundational (Phase 1)**: No dependencies - can start immediately. BLOCKS all user stories.
- **User Stories (Phase 2, 3, 4)**: All depend on Foundational phase completion.
  - User stories can then proceed in parallel (if staffed) or sequentially in priority order.
- **Polish (Phase 5)**: Depends on all desired user stories being complete.

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 1) - No dependencies on other stories.
- **User Story 2 (P2)**: Can start after Foundational (Phase 1) - May integrate with US1 but should be independently testable.
- **User Story 3 (P2)**: Can start after Foundational (Phase 1) - No direct dependencies on US1 or US2, but relies on `AdminSidebar` existing.

### Within Each User Story

- Models/Types before components that use them.
- Components before pages that integrate them.
- Core implementation before styling/responsiveness refinements.

### Parallel Opportunities

- Tasks T001, T002, T003 in Phase 1 can be initiated in parallel.
- Once Foundational phase completes, User Stories 1, 2, and 3 can be worked on in parallel by different team members.
- Within User Story 2, tasks T008 and T009 ([P] tasks) can be developed in parallel.
- Within User Story 3, task T016 ([P] task) can be done in parallel with T015.

---

## Parallel Example: User Story 2

```bash
# Launch all independent component creations for User Story 2 together:
Task: "T008 [P] [US2] Create `ProductForm.tsx` component ..."
Task: "T009 [P] [US2] Create `ProductDetailView.tsx` component ..."
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Foundational
2. Complete Phase 2: User Story 1
3. **STOP and VALIDATE**: Test User Story 1 independently
4. Deploy/demo if ready

### Incremental Delivery

1. Complete Foundational Phase → Foundation ready
2. Add User Story 1 → Test independently → Deploy/Demo (MVP!)
3. Add User Story 2 → Test independently → Deploy/Demo
4. Add User Story 3 → Test independently → Deploy/Demo
5. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Foundational Phase together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
3. Stories complete and integrate independently

---

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and testable
- Commit after each task or logical group
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence

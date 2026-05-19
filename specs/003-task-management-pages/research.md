# Research: Task Management Module

## Decision: Component-Based Implementation with Next.js App Router

The Task Management module will be implemented as a set of responsive Next.js pages within the existing `GMS-FE` admin dashboard layout. UI elements will be decomposed into modular, reusable React components to ensure maintainability and consistency.

### Rationale

- **Modularity**: Following the project constitution, breaking down raw HTML into components (e.g., `TaskCard`, `TaskForm`) prevents large, unmanageable files.
- **Consistency**: Reusing the existing `AdminSidebar` and `AdminTopBar` ensures the new pages feel like a native part of the application.
- **Efficiency**: Identifying common UI patterns (status badges, form inputs) across the five HTML references allows for code reuse.
- **Type Safety**: Using TypeScript for all components and data structures ensures robustness.

### Findings

#### 1. Component Decomposition

| Component | Description | HTML Source |
|-----------|-------------|-------------|
| `TaskCard` | Summary card for the task list | `MyTaskPage.html` |
| `TaskBadge` | Status/Priority indicator | Multiple |
| `TaskForm` | Reusable form for New/Edit task | `NewTaskPage.html`, `EditTaskDetailPage.html` |
| `TaskDetailSidebar` | Metadata view for task details | `TaskDetailPage.html` |
| `UserCard` | Assignee selection card | `AssignTask.html` |
| `AttachmentList` | List of files with download actions | `TaskDetailPage.html` |
| `WorkloadBar` | Progress bar for user workload | `AssignTask.html` |

#### 2. Layout Integration

- **Sidebar**: Update `GMS-FE/components/layout/AdminSidebar.tsx` to include a "Tasks" link pointing to `/admin/tasks`.
- **Active State**: The "Tasks" link should be active when the pathname starts with `/admin/tasks`.

#### 3. Data Modeling

- New `Task` and `Assignee` interfaces will be added.
- `GMS-FE/lib/mock-data.ts` will be extended with `TASK_DATA` and `ASSIGNEE_DATA`.

### Alternatives Considered

- **Single Page Application with Tabs**: Rejected because the individual pages (Detail, New, Assign) have distinct workflows and sub-routes are better for deep linking and navigation history.
- **Client-only State Management**: Selected for this prototype phase as per the spec, using React state and mock data, avoiding real backend integration.

### Unknowns Resolved

- **Sidebar Integration**: The `AdminSidebar` uses a `navItems` array, making it easy to add the "Tasks" route.
- **Icon Library**: The project uses `material-symbols-outlined` for icons, which matches the HTML references.
- **Tailwind Config**: The HTML files use specific custom colors (e.g., `surface-container-low`, `primary-container`). These should be ensured to exist in the project's `tailwind.config.ts`. (Verified: `GMS-FE/tailwind.config.ts` was seen in the file list earlier).

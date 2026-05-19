# Quickstart: Task Management Module

This guide provides instructions on how to access and test the new Task Management features in the GovJobs Portal prototype.

## Accessing the Module

Once implemented, the Task Management module can be accessed via the sidebar:
1.  Navigate to the **Admin Console** (e.g., `/admin/dashboard`).
2.  Click on the **Tasks** link in the left sidebar.
3.  Alternatively, go directly to `/admin/tasks`.

## Key Routes

- **My Tasks**: `/admin/tasks` - View and filter priority tasks.
- **New Task**: `/admin/tasks/new` - Create a new recruitment workflow task.
- **Task Detail**: `/admin/tasks/[id]` - View full details, attachments, and activity log.
- **Edit Task**: `/admin/tasks/[id]/edit` - Update task metadata.
- **Assign Task**: `/admin/tasks/[id]/assign` - Assign a task to a team member.

## Testing Scenarios

### 1. View Task List
- Navigate to `/admin/tasks`.
- Verify the list of tasks is displayed correctly.
- Use the search bar to filter tasks by title.
- Use the status dropdown to filter by "Overdue" or "Due Soon".

### 2. Create a New Task
- Click "New Task" from the sidebar or the task list page.
- Fill in the form fields.
- Click "Create Task" and verify it appears in the list (mocked).

### 3. View Task Details
- Click on any task from the list.
- Verify the detail page displays the correct description, assignee, and due date.
- Check that attachments are listed in the sidebar.

### 4. Assign a Task
- From the Task Detail page, click "Assign Task" (if applicable) or navigate to `/admin/tasks/[id]/assign`.
- Search for a team member and click "Assign".
- Verify the success notification appears.

## Technical Notes

- This feature uses **mock data** defined in `GMS-FE/lib/mock-data.ts`.
- No real database or backend API is required for this prototype.
- Responsive behavior can be tested by resizing the browser or using DevTools mobile emulation.

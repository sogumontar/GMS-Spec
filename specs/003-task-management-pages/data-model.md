# Data Model: Task Management Module

## Core Entities

### Task
Represents a workflow item within the recruitment process.

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string` | Unique identifier (e.g., "REF-2023-0492") |
| `title` | `string` | Short name of the task |
| `description`| `string` | Detailed instructions or context |
| `status` | `enum` | `OPEN`, `IN_PROGRESS`, `COMPLETED`, `OVERDUE`, `LATE` |
| `priority` | `enum` | `LOW`, `MEDIUM`, `HIGH` |
| `assigneeId` | `string` | Reference to the User (Assignee) |
| `dueDate` | `string` | ISO date string |
| `createdDate`| `string` | ISO date string |
| `category` | `string` | e.g., "Background Check", "Security Clearance" |

### User (Assignee)
Represents a staff member who can be assigned to tasks.

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string` | Unique identifier |
| `name` | `string` | Full name |
| `role` | `string` | Professional title (e.g., "Senior Recruiter") |
| `department` | `string` | e.g., "Talent Acquisition" |
| `avatarUrl` | `string` | Path to profile image |
| `workload` | `number` | Current number of assigned tasks |
| `maxWorkload`| `number` | Maximum task capacity (default: 5) |

### Attachment
A file associated with a task.

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string` | Unique identifier |
| `name` | `string` | Filename (e.g., "Transcript.pdf") |
| `size` | `string` | Human-readable size (e.g., "2.4 MB") |
| `type` | `string` | MIME type or extension |
| `url` | `string` | Download URL |

### Activity
A record of a change made to a task.

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string` | Unique identifier |
| `taskId` | `string` | Reference to the Task |
| `userId` | `string` | Reference to the User who performed the action |
| `action` | `string` | Description of change (e.g., "Status updated to COMPLETED") |
| `timestamp` | `string` | ISO date string |

## Relationships

- **Task (1) <---> (0..*) Attachment**: A task can have multiple attachments.
- **Task (1) <---> (0..*) Activity**: A task tracks multiple activities.
- **User (1) <---> (0..*) Task**: A user can be assigned to multiple tasks.
- **Task (1) <---> (1) User**: Each task has exactly one assignee (for this prototype).

## State Transitions (Task Status)

1. `OPEN` -> `IN_PROGRESS` (When work starts)
2. `IN_PROGRESS` -> `COMPLETED` (When work finishes)
3. `OPEN`/`IN_PROGRESS` -> `OVERDUE` (When current date > due date)
4. `OPEN`/`IN_PROGRESS` -> `LATE` (Specific "late" status from HTML ref)

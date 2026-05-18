# Data Model: Stitch AI Prototype

This feature is a frontend prototype with mocked data. The "data model" here refers to the TypeScript interfaces and mock data structures used to populate the UI.

## Mock Entities

### 1. InventoryItem (InventoryManagement)
| Field | Type | Description |
|-------|------|-------------|
| id | string | Unique identifier |
| name | string | Product name |
| sku | string | Stock Keeping Unit |
| quantity | number | Current stock level |
| status | 'In Stock' \| 'Low Stock' \| 'Out of Stock' | Availability status |

### 2. User (UserManagement)
| Field | Type | Description |
|-------|------|-------------|
| id | string | Unique identifier |
| name | string | Full name |
| email | string | Email address |
| role | 'Admin' \| 'Viewer' \| 'Editor' | System role |
| status | 'Active' \| 'Inactive' | Account status |

### 3. Application (ApplicationDashboard)
| Field | Type | Description |
|-------|------|-------------|
| id | string | Unique identifier |
| type | string | Type of application |
| submittedAt | string | ISO date string |
| status | 'Draft' \| 'Submitted' \| 'Under Review' \| 'Approved' | Progress status |

## State Management

### Mock Context
A global React Context will track:
- **Notifications**: Queue of toast messages to display.
- **Current User**: Mock session for displaying name/avatar in headers.
- **Form State**: Temporary storage for "submitted" values to show in subsequent views (e.g., name from Registration appearing in Dashboard).

## Validation Rules
- All form inputs will use standard HTML5 validation.
- Mock success feedback will be triggered even if form is empty (to focus on UI flow).

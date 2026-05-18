# Quickstart: Stitch AI Prototype

This guide helps you run and navigate the integrated Stitch AI prototype.

## Setup

1. **Install Dependencies**:
   ```bash
   cd GMS-FE
   npm install
   ```

2. **Run Development Server**:
   ```bash
   npm run dev
   ```

3. **Access Prototype**:
   Open [http://localhost:3000](http://localhost:3000) in your browser.

## Navigation Map

| Page | Route | Source HTML |
|------|-------|-------------|
| Landing Page | `/` | `LandingPage.html` |
| Registration | `/register` | `RegistrationPage.html` |
| Admin Dashboard | `/admin/dashboard` | `Dashboard.html` |
| User Management | `/admin/users` | `UserManagement.html` |
| Inventory | `/admin/inventory` | `InventoryManagement.html` |
| Ops Center | `/admin/operations` | `OperationCenter.html` |
| Applicant Home | `/applicant/dashboard` | `ApplicationDashboard.html` |
| Application Form | `/applicant/apply` | `ApplicationForm.html` |
| Documents | `/applicant/documents` | `DocumentUpload.html` |
| Final Review | `/applicant/resume` | `FinalResume.html` |

## Interaction Guide

- **Buttons & Links**: All primary navigation links are functional.
- **Forms**: Clicking "Submit" on any form will trigger a mock success toast.
- **Mock Data**: Tables and dashboards are populated with realistic mock data defined in `data-model.md`.

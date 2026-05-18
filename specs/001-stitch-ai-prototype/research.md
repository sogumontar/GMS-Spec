# Research: Stitch AI Prototype Integration

## Decisions

### 1. Component Architecture
- **Decision**: Adopt a tiered component structure.
- **Rationale**: The 10 HTML files share many repeating patterns but differ in high-level layouts (Public vs. Applicant vs. Admin).
- **Tiers**:
  - `components/ui`: Atomic elements (Button, Input, Badge, Table).
  - `components/layout`: Structural components (AdminSidebar, ApplicantSidebar, PublicHeader, Footer).
  - `components/features`: Complex, domain-specific modules (MetricCard, LogViewer, ApplicationStepper).

### 2. Route Mapping
- **Decision**: Use Next.js Route Groups to manage different layouts.
- **Mapping**:
  - `(public)/page.tsx` <- `LandingPage.html`
  - `(public)/register/page.tsx` <- `RegistrationPage.html`
  - `(applicant)/applicant/dashboard/page.tsx` <- `ApplicationDashboard.html`
  - `(applicant)/applicant/apply/page.tsx` <- `ApplicationForm.html`
  - `(applicant)/applicant/documents/page.tsx` <- `DocumentUpload.html`
  - `(applicant)/applicant/resume/page.tsx` <- `FinalResume.html`
  - `(admin)/admin/dashboard/page.tsx` <- `Dashboard.html`
  - `(admin)/admin/inventory/page.tsx` <- `InventoryManagement.html`
  - `(admin)/admin/operations/page.tsx` <- `OperationCenter.html`
  - `(admin)/admin/users/page.tsx` <- `UserManagement.html`

### 3. Interaction Mocking
- **Decision**: Implement a global `MockProvider` and `useMockAction` hook.
- **Rationale**: Consistent feedback (e.g., Toast notification) for all buttons and forms without needing individual logic for every page.
- **Mock Behavior**:
  - Click Submit -> Show "Form submitted successfully (Mock)" toast.
  - Optional: Redirect after delay for flows like Registration -> Dashboard.

### 4. Asset Management
- **Decision**: Move all assets to `public/stitch-assets/`.
- **Rationale**: Keeps original assets isolated and easy to reference using Next.js `Image` component.

## Alternatives Considered

- **Single Layout**: Rejected because the Admin console has a fixed sidebar navigation which is fundamentally different from the Landing Page header/footer.
- **In-page Form Logic**: Rejected in favor of a global hook to minimize repetitive code and ensure SC-002 (feedback performance) is met consistently.

## Dependencies

- `lucide-react`: For icons (to replace any custom SVG icons if needed, though we will try to preserve original SVGs first).
- `sonner` or `react-hot-toast`: For quick mock feedback notifications.

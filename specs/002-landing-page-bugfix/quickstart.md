# Quickstart: Landing Page Bug Fixes

## Development Workflow

1. **Verify Current State**:
   - Run the development server: `npm run dev` (inside `GMS-FE`)
   - Navigate to `/admin/dashboard` and other admin pages. Observe that the sidebar highlight doesn't change.
   - Resize the browser to mobile width. Observe the horizontal scroll and the black background on the right.

2. **Apply Sidebar Fixes**:
   - Update `AdminSidebar.tsx` and `ApplicantSidebar.tsx` to use `usePathname`.
   - Verify that clicking different links updates the active highlight.

3. **Apply Responsiveness Fixes**:
   - Update `AdminLayout.tsx` and `ApplicantLayout.tsx` with responsive Tailwind classes.
   - Implement the sidebar toggle state in `AdminLayout`.
   - Update `AdminTopBar.tsx` to call the toggle function.

4. **Final Verification**:
   - Check all breakpoints (Desktop, Tablet, Mobile).
   - Ensure no horizontal overflow exists.
   - Verify sidebar toggles correctly on mobile.

## Key Components

- `GMS-FE/components/layout/AdminSidebar.tsx`: Dynamic highlighting logic.
- `GMS-FE/app/(admin)/layout.tsx`: Responsive container and mobile toggle state.
- `GMS-FE/components/layout/AdminTopBar.tsx`: Hamburger menu button.
- `GMS-FE/components/layout/ApplicantSidebar.tsx`: Dynamic highlighting logic.
- `GMS-FE/app/(applicant)/layout.tsx`: Responsive container.

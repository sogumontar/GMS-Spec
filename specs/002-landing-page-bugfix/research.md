# Research: Landing Page Bug Fixes

## Findings

### 1. Sidebar Active State
- **Current implementation**: Both `AdminSidebar.tsx` and `ApplicantSidebar.tsx` use hardcoded Tailwind classes for the 'Dashboard' link to indicate an active state.
- **Dynamic Solution**: Next.js App Router provides the `usePathname` hook from `next/navigation`. By checking if the `pathname` starts with or matches the link's `href`, we can conditionally apply the active classes.
- **Constraints**: No new libraries required. `usePathname` is a built-in hook.

### 2. Layout Responsiveness & Overflow
- **Root Cause (Admin)**: `AdminLayout.tsx` uses `ml-[260px]` on the main content container, while the `AdminSidebar` is `fixed`. On small screens, this `ml-[260px]` remains, pushing content out of the viewport.
- **Root Cause (Applicant)**: `ApplicantLayout.tsx` uses `w-full md:ml-72`. The `w-full` combined with `ml-72` (even if it's `md:`) can cause overflow if not handled correctly.
- **Responsive Solution**:
    - **Admin**: Change `ml-[260px]` to `md:ml-[260px] ml-0`. Hide sidebar on mobile (`hidden md:flex`).
    - **Mobile Menu**: Implement a sidebar toggle using `useState` in the Layout and pass it to `AdminTopBar`. Use a "Hamburger" icon to trigger the toggle.
    - **Overflow**: Ensure `flex-1` is used without `w-full` where margins are involved, or use `overflow-hidden` on parent containers if necessary.

### 3. Testing Setup
- **Status**: No existing testing framework (Jest/Vitest/Cypress) found in `package.json` or project root.
- **Recommendation**: Manual visual verification is currently the only available method unless a testing framework is added. Given the constraint "DO NOT introduce any new external libraries", we will stick to manual verification.

## Decisions

- **Active State**: Use `usePathname()` in both sidebar components.
- **Responsiveness**:
    - Make layouts mobile-first.
    - Sidebar will be hidden by default on mobile and slide in when toggled.
    - Use Tailwind's `md:` breakpoint for desktop layouts.
- **Mobile Toggle**: Add a stateful toggle in `AdminLayout` to control sidebar visibility on mobile.

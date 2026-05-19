# Specification: Landing Page Bug Fixes

## 1. Context and Objective
The initial conversion of the static HTML landing page into Next.js components has been completed. However, during testing, several UI/UX issues (bugs) were identified regarding component interactivity and layout responsiveness. The objective of this task is to fix these specific issues without breaking the existing core structure or styling.

## 2. Bug Reports & Expected Behavior

### Bug 1: Sidebar Active State (Highlight) Issue
- **Current Behavior:** The sidebar navigation's active state indicator (e.g., highlight, text color, or icon change) remains stuck on the 'Dashboard' item, even when the user navigates to other pages within the application. This gives a misleading visual cue about the currently active page.
- **Expected Behavior:**
    - The sidebar navigation must dynamically track and update its active state based on the current URL path.
    - Implement the necessary React logic, utilizing `usePathname` from `next/navigation` (for Next.js App Router), to accurately determine the currently active page.
    - Apply appropriate CSS classes or styles conditionally to the corresponding sidebar navigation item to visually indicate its active status.
    - Ensure the active state updates correctly upon direct navigation or page refreshes.

### Bug 2: Overall Layout Responsiveness & Overflow Issue
- **Current Behavior:** The entire application layout is not responsive. When viewed on mobile devices or smaller screen sizes, components become misaligned, disproportionate, or overlap. Specifically, a noticeable black background appears on the right side of the viewport, indicating horizontal overflow and a failure to adapt to smaller screens.
- **Expected Behavior:**
    - Refactor all affected components to ensure they are fully responsive and adapt gracefully across various screen sizes, from desktop to mobile viewports.
    - Utilize responsive design principles and utility classes (e.g., from Tailwind CSS if in use) to adjust layouts, spacing (padding/margins), font sizes, and component visibility.
    - Address and eliminate the horizontal overflow issue, specifically the black background appearing on the right side, by ensuring all elements constrain within the viewport width.
    - Implement flexible layouts (e.g., using Flexbox or Grid with responsive breakpoints) that adjust or collapse appropriately on smaller screens (e.g., grid columns stacking vertically on mobile).
    - The final UI must be clean, readable, and visually consistent with the original design intent on all devices, without any horizontal scrolling or visual artifacts.

## 3. Constraints & Guardrails
- **DO NOT** rewrite the entire components from scratch; only modify the specific parts of the code causing these bugs.
- **DO NOT** introduce any new external libraries or packages to solve these UI issues.
- Maintain consistency with the existing styling approach (e.g., keep using Tailwind classes if that's what is currently used).
- Prioritize semantic HTML and accessibility where applicable during refactoring.

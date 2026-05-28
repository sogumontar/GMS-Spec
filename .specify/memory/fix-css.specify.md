# Specification: Fix Missing CSS / UI Unstyled Bug

## 1. Context and Objective
The UI has suddenly lost all its styling and colors, rendering as plain unstyled HTML text. The objective is to debug and fix the global CSS configuration or Tailwind setup so that the components render with their intended styles.

## 2. Bug Report & Expected Behavior
- **Current Behavior:** The components (like navigation, links, and text) appear without any CSS styles applied.
- **Expected Behavior:** All Tailwind utility classes and global styles must apply correctly across the entire application.

## 3. Investigation & Fix Requirements
The AI must perform the following checks and apply necessary fixes:
1. **Global Styles Import:** Check `layout.tsx` (App Router) or `_app.tsx` (Pages Router) to ensure the global CSS file (e.g., `globals.css`) is properly imported at the top of the file.
2. **Tailwind Directives:** Verify that the `globals.css` file contains the required `@tailwind base;`, `@tailwind components;`, and `@tailwind utilities;` directives.
3. **Tailwind Config Content Paths:** Check `tailwind.config.ts` (or `.js`) to ensure the `content` array includes the correct paths to all directories containing components (e.g., `./app/**/*.{js,ts,jsx,tsx}`, `./components/**/*.{js,ts,jsx,tsx}`).
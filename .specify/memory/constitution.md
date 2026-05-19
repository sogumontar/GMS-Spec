# Frontend Project Constitution (Project DNA)

## 1. Tech Stack
- This project uses **Next.js (App Router)**.
- The primary programming languages used are **TypeScript** and **React**.
- All pages must be located within the `GMS-FE/app/` directory.

## 2. UI Conversion Rules (Stich.ai to React)
- DO NOT place long, raw HTML code into a single file. All UI MUST be broken down into small, modular, and reusable React components inside the `/components` folder (parallel to the `app` folder).
- When converting static HTML references into React JSX, strictly adhere to the following rules:
    - MUST change all `class` attributes to `className`.
    - MUST properly close self-closing tags to be valid in JSX (e.g., `<input>` becomes `<input />`, `<hr>` becomes `<hr />`).
    - MUST change the `for` attribute on labels to `htmlFor`.
    - HTML attributes using *kebab-case* (such as `stroke-width`) must be converted to *camelCase* (such as `strokeWidth`) within SVGs or other elements.

## 3. Asset Management
- DO NOT use the standard HTML `<img>` tag. All images MUST use the built-in `<Image />` component from `next/image`.
- All static assets (images, icons, etc.) from the reference files must be placed inside the `/public` folder.

## 4. AI Behavior (Guardrails)
- Do not create connections to a real Backend API or database unless explicitly instructed to do so within the specification file (`.specify`).
- If in doubt regarding styling or layout, always use the Stich.ai HTML/CSS files in the reference folder as the absolute Source of Truth.
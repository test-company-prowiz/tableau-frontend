# tailwind.config.js

> **Source File:** [tailwind.config.js](https://github.com/test-company-prowiz/tableau-frontend/blob/main/tailwind.config.js)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

# tailwind.config.js

### Overview
This file configures Tailwind CSS for the project. It defines the paths to application files that Tailwind should scan for utility classes and extends the default theme with custom typography settings.

### Architecture & Role
This file resides in the project's build configuration layer, specifically for styling. It acts as an input for the Tailwind CSS Just-In-Time (JIT) compiler, guiding the stylesheet generation process based on the detected utility classes and custom theme definitions.

### Key Components
- `module.exports`: The primary export of a configuration object that Tailwind CSS consumes.
- `content`: An array of glob patterns specifying files (`.js`, `.jsx`, `.ts`, `.tsx` within `src/`) that Tailwind should parse to identify used utility classes.
- `theme.extend.fontFamily`: An object that adds custom font families (`inter` and `outfit`) to Tailwind's default theme, making them available as utility classes (e.g., `font-inter`).
- `plugins`: An empty array indicating no additional Tailwind plugins are currently in use.

### Execution Flow / Behavior
This file is not executed at application runtime. Instead, it is processed by the Tailwind CSS build tool (e.g., via PostCSS) during the development server startup or when the project is built for production. The configuration directs Tailwind to generate an optimized CSS bundle containing only the utility classes actually used in the specified content files, along with the custom font definitions.

### Dependencies
- **`tailwindcss`**: This configuration file is directly dependent on the `tailwindcss` library, which interprets its structure and values. The `@type` JSDoc comment explicitly references `import('tailwindcss').Config`.
- There are no explicit internal file dependencies.

### Design Notes
- The `content` configuration is crucial for Tailwind's tree-shaking capability, ensuring that the final CSS bundle only includes styles that are actively used in the project, minimizing file size.
- Extending `fontFamily` in the `theme` provides a centralized and consistent way to manage typography across the application, promoting design system adherence.
- An empty `plugins` array suggests a lean Tailwind setup, relying primarily on its core utility classes without additional custom functionality.

### Diagram (Optional)
None significant.
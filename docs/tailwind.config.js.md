# tailwind.config.js

> **Source File:** [tailwind.config.js](https://github.com/tableau-frontend/blob/main/tailwind.config.js)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

### Overview
This file serves as the configuration entry point for Tailwind CSS, defining how the framework should process source files and customize its default theme for the project.

### Architecture & Role
Architecturally, this file acts as a configuration asset consumed by the frontend build process. It belongs to the styling layer, dictating the design system's utility-first approach and theme customization. The Tailwind CSS CLI or PostCSS plugin reads this configuration during compilation to generate the project's final CSS stylesheet.

### Key Components
*   `module.exports`: Standard Node.js syntax for exporting the configuration object.
*   `content`: An array of glob patterns specifying the files that Tailwind CSS should scan for class names to include in the final compiled CSS. The current configuration targets all JavaScript/TypeScript files (`.js`, `.jsx`, `.ts`, `.tsx`) within the `src` directory and its subdirectories.
*   `theme.extend`: An object used to extend Tailwind's default theme without overwriting it.
*   `fontFamily`: A sub-property within `theme.extend` that defines custom font families. It adds `inter` and `outfit` to the available font utilities, both with a `sans-serif` fallback.
*   `plugins`: An empty array, indicating that no custom Tailwind plugins are currently active in this configuration.

### Execution Flow / Behavior
During the build process (e.g., when running a development server or creating a production build), the Tailwind CSS engine reads this configuration file. It then scans all files matching the `content` patterns to identify every Tailwind utility class used. Based on these detected classes and any theme extensions (like `fontFamily` defined here), Tailwind generates a highly optimized, minimal CSS file containing only the necessary styles, which is then injected into the application.

### Dependencies
The primary external dependency is the `tailwindcss` npm package, which interprets and utilizes this configuration. Implicitly, for the custom fonts (`Inter`, `Outfit`) to render correctly, they must be linked or imported into the project's CSS or HTML.

### Design Notes
The use of `theme.extend` is a core design pattern for maintaining Tailwind's comprehensive default utility set while introducing project-specific design tokens, such as custom fonts. The broad `content` glob pattern `"./src/**/*.{js,jsx,ts,tsx}"` is typical for component-based frontend frameworks, ensuring all relevant code is processed for style generation. The absence of custom plugins indicates a reliance on Tailwind's core features.

### Diagram (Optional)
None significant.
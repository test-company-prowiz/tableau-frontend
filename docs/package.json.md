# package.json

### Overview
This file serves as the manifest for a React-based frontend application named `tableau_frontend`. It defines project metadata, manages project dependencies, and specifies scripts for common development tasks such as starting, building, testing, and ejecting the application.

### Architecture & Role
Architecturally, this file defines the foundational configuration for a client-side frontend application. It operates at the project configuration layer, dictating the development environment, build tools, and runtime libraries required for the React application to function. It enables standard development workflows within a JavaScript ecosystem.

### Key Components
*   **name**: Identifies the project as `tableau_frontend`.
*   **version**: Current version of the project, `0.1.0`.
*   **private**: Set to `true`, indicating this package is not intended for publication to a public npm registry.
*   **dependencies**: Lists runtime dependencies required by the application. This includes React, UI libraries (Ant Design), routing (React Router DOM), HTTP client (Axios), and authentication (@react-oauth/google).
*   **devDependencies**: Lists development-only dependencies, specifically `tailwindcss` for styling.
*   **scripts**: Defines command-line scripts for common tasks:
    *   `start`: Initiates the development server.
    *   `build`: Compiles the application for production deployment.
    *   `test`: Runs application tests.
    *   `eject`: Detaches the project from `react-scripts` configurations.
*   **eslintConfig**: Specifies ESLint configuration, extending `react-app` and `react-app/jest` rules for code quality and testing.
*   **browserslist**: Defines browser compatibility targets for production and development builds.

### Execution Flow / Behavior
The `scripts` section defines the primary execution behaviors. When `npm start` is executed, `react-scripts start` launches a local development server. Similarly, `npm build` triggers `react-scripts build` to compile optimized production assets. `npm test` runs `react-scripts test` to execute configured test suites. These scripts encapsulate the standard Create React App development lifecycle.

### Dependencies
*   **@react-oauth/google**: Provides Google OAuth functionality for user authentication.
*   **@testing-library/jest-dom**, **@testing-library/react**, **@testing-library/user-event**: Core libraries for testing React components.
*   **antd**: A widely used UI component library, providing pre-built components.
*   **axios**: A promise-based HTTP client for making API requests.
*   **react**, **react-dom**: Core libraries for building user interfaces with React.
*   **react-hook-form**: Library for form validation and management.
*   **react-icons**: Provides a collection of popular icon libraries.
*   **react-router-dom**: Enables declarative routing within the application.
*   **react-scripts**: Core dependency for Create React App, abstracting build tools and configurations.
*   **react-slick**, **slick-carousel**: Libraries for creating carousels and sliders.
*   **react-toastify**: Provides components for displaying toast notifications.
*   **web-vitals**: For measuring and reporting on crucial user experience metrics.
*   **tailwindcss** (devDependencies): A utility-first CSS framework used for styling during development.

### Design Notes
The project leverages `react-scripts` to manage its build system, testing setup, and development server, reducing the need for manual Webpack or Babel configurations. This simplifies project setup and maintenance. The reliance on a comprehensive UI library like Ant Design suggests a focus on rapid UI development and adherence to established design patterns. The use of `@react-oauth/google` indicates integration with external authentication providers.

### Diagram (Optional)
None significant.
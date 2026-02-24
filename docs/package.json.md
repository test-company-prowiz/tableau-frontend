# package.json

> **Source File:** [package.json](https://github.com/tableau-frontend/blob/main/package.json)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

### Overview
This file serves as the manifest for the `tableau_frontend` project. It defines metadata, project dependencies (both runtime and development), and a collection of executable scripts for common development tasks such as starting the application, building for production, and running tests. It is fundamental for managing the project's environment and build process.

### Architecture & Role
Architecturally, `package.json` is a core configuration file at the root of a JavaScript project, specifically a React-based frontend application. It operates at the foundational build and dependency management layer, instructing package managers like npm on how to set up the project's environment and execute predefined tasks. It does not contain application logic but rather defines the scaffolding and external libraries the application relies on.

### Key Components
*   **`name`, `version`, `private`**: Basic project identification and status. `private: true` indicates this package is not intended for public npm registry publication.
*   **`dependencies`**: Specifies external libraries required for the application to run in production. Notable dependencies include `react`, `react-dom` for UI, `react-router-dom` for client-side routing, `axios` for HTTP requests, `antd` for UI components, and `@react-oauth/google` for Google OAuth integration.
*   **`devDependencies`**: Lists libraries used exclusively for development and testing purposes, such as `tailwindcss` for styling.
*   **`scripts`**: Defines shell commands to automate common tasks:
    *   `start`: Launches the development server.
    *   `build`: Compiles the application for production deployment.
    *   `test`: Executes project tests.
    *   `eject`: Removes the `react-scripts` abstraction, exposing underlying configuration files.
*   **`eslintConfig`**: Configures ESLint, a linter, to enforce code quality and style based on React app best practices.
*   **`browserslist`**: Specifies the target browsers and their versions for transpilation and polyfilling, ensuring broad compatibility for the built application.

### Execution Flow / Behavior
When a developer or CI/CD system interacts with the project, `package.json` drives several behaviors:
1.  **Dependency Resolution**: Commands like `npm install` read the `dependencies` and `devDependencies` sections to fetch and install required packages into the `node_modules` directory.
2.  **Script Execution**: Commands like `npm start` or `npm build` invoke the corresponding scripts defined in the `scripts` section, which in turn execute `react-scripts` commands to manage the development server, build process, or test runner.
3.  **Environment Configuration**: The `eslintConfig` and `browserslist` sections implicitly guide the tools (ESLint, Babel/Webpack via `react-scripts`) on how to analyze code and compile assets.

### Dependencies
This file itself is a configuration, but it defines the following categories of dependencies for the project:

*   **Runtime Libraries**:
    *   `react`, `react-dom`: Core libraries for building user interfaces.
    *   `react-router-dom`: Enables declarative routing in the React application.
    *   `axios`: A promise-based HTTP client for making API requests.
    *   `antd`: A comprehensive UI component library for enterprise-level applications.
    *   `@react-oauth/google`: Facilitates integration with Google OAuth for authentication.
    *   `react-hook-form`: A library for form validation and management.
    *   `react-icons`: Provides a collection of popular icons.
    *   `react-slick`, `slick-carousel`: Libraries for building carousels and sliders.
    *   `react-toastify`: For displaying toast notifications.
*   **Development & Build Tools**:
    *   `react-scripts`: Abstracts Webpack, Babel, ESLint, and other configurations for a Create React App project.
    *   `@testing-library/*`: Libraries for robust and user-centric testing of React components.
    *   `web-vitals`: For measuring performance metrics in web applications.
    *   `tailwindcss` (dev dependency): A utility-first CSS framework used during development for styling.

### Design Notes
The project leverages `create-react-app`'s `react-scripts` for its build toolchain, which provides a pre-configured development environment, build process, and testing setup without requiring manual configuration of Webpack, Babel, etc. This decision prioritizes rapid development and a standardized setup over custom build flexibility. The inclusion of `private: true` ensures that this frontend application is not accidentally published as a standalone npm package, which is appropriate for a client-side application. The choice of `antd` suggests an emphasis on a rich, enterprise-grade UI experience.

### Diagram (Optional)
None significant.
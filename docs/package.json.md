# package.json

### Overview
This file defines the project metadata, script commands, and direct dependencies for the `tableau_frontend` application. It is standard for Node.js-based projects, providing essential configuration for development, building, and testing.

### Architecture & Role
This file is foundational to the frontend application's development environment and build process. It dictates the runtime and development dependencies, setting up the ecosystem for a React-based single-page application (SPA). Architecturally, it resides at the root of the frontend project, configuring the environment rather than directly implementing application logic.

### Key Components
*   **`name`**: `tableau_frontend` - Identifier for the project.
*   **`version`**: `0.1.0` - Current iteration of the project.
*   **`private`**: `true` - Indicates this package is not intended for publication to a package registry.
*   **`dependencies`**: Specifies runtime dependencies required for the application to function. Key dependencies include React, Ant Design for UI components, Axios for HTTP requests, `react-router-dom` for routing, and `@react-oauth/google` for Google authentication.
*   **`scripts`**: Defines command-line aliases for common tasks:
    *   `start`: Initiates the development server.
    *   `build`: Compiles the application for production deployment.
    *   `test`: Runs unit tests.
    *   `eject`: Detaches the project from `react-scripts` configurations.
*   **`eslintConfig`**: Configures ESLint settings, extending base React application and Jest configurations for code linting.
*   **`browserslist`**: Specifies the target browser environments for transpilation and polyfilling, ensuring compatibility across different production and development browsers.
*   **`devDependencies`**: Contains packages necessary only during development or build processes, such as `tailwindcss` for styling.

### Execution Flow / Behavior
The `scripts` section defines shell commands that are executed via `npm run <script-name>`.
*   `npm start` launches a local development server using `react-scripts`, enabling hot-reloading and development tooling.
*   `npm build` executes `react-scripts build`, compiling the React application into static assets for deployment.
*   `npm test` runs tests using the configured testing framework via `react-scripts test`.
*   `npm eject` is a one-time operation to remove the abstraction of `react-scripts` and expose the underlying webpack and Babel configurations.

### Dependencies
*   **Core Framework**: `react`, `react-dom` provide the fundamental libraries for building user interfaces.
*   **UI/UX Libraries**: `antd` offers a comprehensive set of enterprise-level UI components. `react-icons` provides a library of common icons. `react-slick` and `slick-carousel` are used for implementing carousels. `react-toastify` for notifications.
*   **State & Routing**: `react-router-dom` handles client-side routing. `react-hook-form` manages form state and validation.
*   **API Interaction**: `axios` is an HTTP client for making API requests to backend services.
*   **Authentication**: `@react-oauth/google` integrates Google OAuth for user authentication.
*   **Development Tooling**: `react-scripts` encapsulates the build, test, and start scripts. `@testing-library/*` packages support component testing. `tailwindcss` is a utility-first CSS framework used during development.

### Design Notes
The presence of `react-scripts` indicates this project was likely initiated with Create React App, providing a pre-configured development environment. The inclusion of `antd` suggests a preference for a rich, opinionated UI component library. The use of `@react-oauth/google` points to a strategy for social login integration. The `private: true` flag confirms that this is an application package not intended for public distribution on npm.

### Diagram (Optional)
None significant.
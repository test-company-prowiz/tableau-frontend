# package.json

### Overview
This file defines the project's metadata, scripts, and package dependencies for a React-based frontend application. It serves as the manifest for the `tableau_frontend` project.

### Architecture & Role
This file is an integral part of the frontend layer, specifically for a client-side React application. It outlines the necessary external libraries and tools required for development, building, testing, and running the application, thereby establishing the foundation of its runtime environment.

### Key Components
*   **`name`**: `tableau_frontend` – The unique identifier for this project.
*   **`version`**: `0.1.0` – The current version of the application.
*   **`private`**: `true` – Indicates that this package is not intended for publication to a public registry.
*   **`dependencies`**: Lists all packages required for the application to run in a production environment.
*   **`devDependencies`**: Lists packages used exclusively for development and build processes.
*   **`scripts`**: Defines command-line aliases for common tasks, such as starting the development server, building the application, and running tests.
*   **`eslintConfig`**: Specifies ESLint configuration presets for code quality checks.
*   **`browserslist`**: Defines the target browser compatibility for the application's compiled assets.

### Execution Flow / Behavior
The `scripts` section defines various entry points for operating on the project:
*   **`npm start`**: Executes `react-scripts start`, which typically launches a development server and opens the application in a web browser.
*   **`npm build`**: Executes `react-scripts build`, which compiles the application into static files suitable for production deployment.
*   **`npm test`**: Executes `react-scripts test`, which runs unit and integration tests configured for the project.
*   **`npm eject`**: Executes `react-scripts eject`, a one-way operation to copy configuration files and build dependencies into the project, removing the abstraction of `react-scripts`.

### Dependencies
*   **Core UI & State Management**: `react`, `react-dom`, `react-hook-form`.
*   **Routing**: `react-router-dom`.
*   **UI Components & Styling**: `antd`, `react-icons`, `tailwindcss` (dev dependency).
*   **Data Fetching**: `axios`.
*   **Authentication**: `@react-oauth/google`.
*   **UI Utilities**: `react-slick`, `slick-carousel` (for carousels), `react-toastify` (for notifications).
*   **Development & Testing Tools**: `react-scripts`, `@testing-library/jest-dom`, `@testing-library/react`, `@testing-library/user-event`, `web-vitals`.

### Design Notes
The `private: true` setting is a standard practice for frontend applications not intended to be consumed as a library. The reliance on `react-scripts` centralizes build configurations, simplifying setup but limiting direct control over underlying webpack/babel settings unless `eject` is used. The selection of UI libraries like Ant Design and component-specific libraries like `react-slick` indicates a focus on rich, interactive user interfaces.

### Diagram (Optional)
None significant.
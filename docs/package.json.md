# package.json

### Overview
This file defines the metadata, dependencies, and scripts for a frontend application named "tableau_frontend". It serves as the manifest for the project, enabling package managers to install required libraries and execute predefined development and build tasks.

### Architecture & Role
This file sits at the root of the frontend application, serving as its core configuration and dependency manifest. Architecturally, it defines the necessary client-side libraries and tools required for the application's development, building, testing, and runtime operation. It belongs to the build and dependency management layer of the frontend stack.

### Key Components
*   **`name`, `version`, `private`**: Basic project identifiers and a flag indicating the package is not intended for public publication.
*   **`dependencies`**: Lists all third-party libraries essential for the application's runtime functionality. This includes core React libraries, UI components (Ant Design), HTTP client (Axios), routing (React Router DOM), authentication (`@react-oauth/google`), and utility libraries.
*   **`devDependencies`**: Lists libraries used exclusively during development, such as `tailwindcss` for styling.
*   **`scripts`**: Defines command-line aliases for common tasks: `start` (development server), `build` (production build), `test` (run tests), and `eject` (expose `react-scripts` configurations).
*   **`eslintConfig`**: Specifies the ESLint configuration, extending standard React application settings.
*   **`browserslist`**: Configures the target browser compatibility for the application's compiled output in both production and development environments.

### Execution Flow / Behavior
The `package.json` file itself is declarative and does not execute code. Its behavior is realized when a package manager (like `npm` or `yarn`) reads it to:
*   Install listed `dependencies` and `devDependencies`.
*   Execute commands defined in the `scripts` section. For example:
    *   `npm start`: Initiates the development server using `react-scripts start`.
    *   `npm build`: Compiles the application for production using `react-scripts build`.
    *   `npm test`: Runs automated tests using `react-scripts test`.

### Dependencies
The file declares a comprehensive set of dependencies crucial for a modern React frontend:
*   **Core Framework**: `react`, `react-dom` provide the fundamental UI library.
*   **Build Tools**: `react-scripts` encapsulates the Webpack and Babel configurations, likely indicating a Create React App setup.
*   **UI Components & Styling**: `antd` provides a robust UI component library, while `tailwindcss` (dev dependency) is used for utility-first CSS styling.
*   **Data Fetching**: `axios` is an HTTP client for making API requests.
*   **Routing**: `react-router-dom` enables client-side navigation.
*   **State & Forms**: `react-hook-form` assists with form management.
*   **Authentication**: `@react-oauth/google` integrates Google OAuth for user authentication.
*   **UI Enhancements**: `react-icons` for iconography, `react-slick` and `slick-carousel` for carousels, and `react-toastify` for notifications.
*   **Testing**: `@testing-library/jest-dom`, `@testing-library/react`, and `@testing-library/user-event` are used for unit and integration testing.
*   **Performance Monitoring**: `web-vitals` reports core web vitals metrics.

### Design Notes
*   The `private: true` field prevents accidental publication of this application to a public package registry, which is standard practice for application-level `package.json` files.
*   The heavy reliance on `react-scripts` indicates that this project benefits from the standardized build toolchain provided by Create React App, simplifying configuration management for development, testing, and production builds.
*   The explicit separation of `dependencies` and `devDependencies` is a common pattern for optimizing the production bundle size by excluding development-only tools.
*   The `browserslist` configuration ensures that the compiled JavaScript and CSS are compatible with the specified target browsers, providing consistent user experience across the defined environments.

### Diagram (Optional)
None significant.
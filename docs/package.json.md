# package.json

### Overview
This file serves as the manifest for the `tableau_frontend` project, detailing its metadata, external dependencies (both runtime and development), and a collection of executable scripts. It defines the project's environment and build configuration.

### Architecture & Role
Architecturally, this file resides at the root of the frontend application. It defines the foundational environment for the React application, dictating which packages are available, how development and production builds are managed, and how various development tasks like testing and linting are executed. It primarily configures the build and runtime aspects of the client-side application.

### Key Components
*   **`name`**: Identifies the project as `tableau_frontend`, indicating its role as a client-side interface.
*   **`private: true`**: Flags the project as private, preventing accidental publication to a package registry.
*   **`dependencies`**: Specifies the core libraries required for the application to run in production, including React, UI frameworks (Ant Design, React Slick), HTTP client (Axios), routing (React Router DOM), and authentication (@react-oauth/google).
*   **`devDependencies`**: Lists tools used during development and build processes, such as `tailwindcss` for styling and `@testing-library/*` for testing.
*   **`scripts`**: Defines command-line shortcuts for common operations like `start` (development server), `build` (production build), and `test`.
*   **`react-scripts`**: Indicates that the project is built upon Create React App, abstracting complex build configurations.
*   **`eslintConfig`**: Configures code linting rules, extending standard React application settings.
*   **`browserslist`**: Specifies the target browser environments for both development and production builds.

### Execution Flow / Behavior
The `package.json` file itself is a static configuration. Its "behavior" is primarily expressed through the `scripts` section:
*   Executing `npm start` or `yarn start` invokes `react-scripts start`, which launches a local development server for the application.
*   Executing `npm build` or `yarn build` invokes `react-scripts build`, which compiles the React application into static files suitable for deployment.
*   Executing `npm test` or `yarn test` runs tests using `react-scripts test`.

### Dependencies
The project relies on a comprehensive set of external packages:
*   **Core UI & State Management**: `react`, `react-dom`, `antd` (Ant Design UI library).
*   **Routing**: `react-router-dom`.
*   **HTTP Client**: `axios` for making API requests.
*   **Authentication**: `@react-oauth/google` for Google OAuth integration.
*   **Forms**: `react-hook-form` for robust form management.
*   **UI Components**: `react-slick`, `slick-carousel` for carousels; `react-icons` for vector icons; `react-toastify` for notifications.
*   **Development & Build Tools**: `react-scripts` (Create React App utility), `@testing-library/*` (for testing), `tailwindcss` (CSS framework).
*   **Performance Monitoring**: `web-vitals`.

### Design Notes
The project's design choices are evident through its dependencies:
*   **Rapid Development**: Reliance on `react-scripts` suggests a standard Create React App setup, simplifying initial configuration and build tooling.
*   **Rich User Interface**: The inclusion of `antd`, `tailwindcss`, `react-slick`, and `react-icons` points to an application with a modern, feature-rich, and potentially customizable user interface.
*   **External Integration**: The presence of `@react-oauth/google` and `axios` indicates the application interacts with external APIs and services, including third-party authentication.
*   **Testing**: `@testing-library/*` signifies an intent for robust unit and integration testing.
*   **Deployment**: The `private: true` flag implies this frontend application is part of a larger system and not intended as a standalone reusable library for public consumption.

### Diagram (Optional)
None significant.
# package.json

### Overview
This file serves as the manifest for the `tableau_frontend` project, detailing its metadata, dependencies, and essential scripts. It defines the project as a private React application.

### Architecture & Role
This `package.json` file resides at the root of the `tableau_frontend` project, acting as the primary configuration file for Node.js package management. It dictates the project's runtime environment, build process, and development tooling, positioning it as a foundational component for the frontend application layer.

### Key Components
*   **`name`**: Identifies the project as `tableau_frontend`.
*   **`version`**: Specifies the current version as `0.1.0`.
*   **`private`**: Set to `true`, indicating this package is not intended for publication to a registry.
*   **`dependencies`**: Lists all runtime dependencies required for the frontend application, including React, UI libraries, routing, state management, and API clients.
*   **`scripts`**: Defines command-line aliases for common tasks such as `start` (development server), `build` (production build), `test` (run tests), and `eject` (expose `react-scripts` configurations).
*   **`eslintConfig`**: Configures ESLint with presets for React applications and Jest testing.
*   **`browserslist`**: Specifies browser compatibility targets for the application's client-side code, impacting tools like Babel and Autoprefixer.
*   **`devDependencies`**: Lists dependencies used solely for development purposes, such as `tailwindcss` for styling.

### Execution Flow / Behavior
When `npm` or `yarn` commands are executed within the project directory:
*   `npm install` (or `yarn`) reads the `dependencies` and `devDependencies` to install required packages.
*   `npm start` executes `react-scripts start`, which launches a development server and enables hot module reloading.
*   `npm build` executes `react-scripts build`, compiling the React application into static assets for production deployment.
*   `npm test` executes `react-scripts test`, running tests configured for the project.

### Dependencies
*   **`@react-oauth/google`**: Integrates Google OAuth for authentication purposes.
*   **`antd`**: A UI library providing a set of enterprise-level components.
*   **`axios`**: A promise-based HTTP client for making API requests.
*   **`react`**, **`react-dom`**: Core libraries for building user interfaces with React.
*   **`react-hook-form`**: A library for form validation with an emphasis on performance and developer experience.
*   **`react-router-dom`**: Provides declarative routing for React applications.
*   **`react-scripts`**: A set of scripts from Create React App to handle development, building, and testing without manual configuration.
*   **`react-toastify`**: For displaying toast notifications in the UI.
*   **`tailwindcss` (devDependency)**: A utility-first CSS framework for rapid UI development.
*   Testing libraries (`@testing-library/*`, `web-vitals`): For unit and integration testing and performance measurement.

### Design Notes
The project leverages `create-react-app`'s `react-scripts` for managing its build toolchain, which abstracts away complex Webpack and Babel configurations. This approach prioritizes rapid development and a standardized setup but limits direct control over the underlying build process unless `eject` is used. The inclusion of `antd` and `tailwindcss` suggests a hybrid approach to UI styling, potentially using Ant Design for complex components and Tailwind CSS for custom styling or utilities. Google OAuth integration indicates an external authentication strategy.

### Diagram (Optional)
None significant.
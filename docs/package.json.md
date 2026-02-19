# package.json

### Overview
This file serves as the manifest for the `tableau_frontend` project, defining its metadata, essential package dependencies, and predefined scripts for development and build processes. It is standard for Node.js-based projects, particularly those built with React.

### Architecture & Role
Architecturally, `package.json` resides at the root of the frontend application and acts as a central configuration file. It is not part of the runtime bundle but is critical for the development environment, build tooling, and dependency management. It dictates how the project is set up and run by package managers like `npm`.

### Key Components
*   **name**: Identifies the project as `tableau_frontend`.
*   **version**: Specifies the current version of the project, `0.1.0`.
*   **private**: Set to `true`, indicating this package is not intended for publication to a package registry.
*   **dependencies**: Lists the production runtime libraries required by the application.
*   **scripts**: Defines executable commands for common tasks like starting the development server, building for production, running tests, and ejecting configuration.
*   **eslintConfig**: Configures ESLint rules for code quality, extending standard React application settings.
*   **browserslist**: Specifies the target browser environments for frontend assets, ensuring compatibility across different versions and usage statistics.
*   **devDependencies**: Lists packages required only during development and build processes, such as `tailwindcss`.

### Execution Flow / Behavior
The `scripts` section defines entry points for various operations:
*   `start`: Initiates the development server.
*   `build`: Compiles the application for production deployment.
*   `test`: Executes the project's test suite.
*   `eject`: Unveils the hidden configurations used by `react-scripts`.
These scripts are typically invoked via the `npm run <script-name>` command. The `dependencies` are installed once the project is set up, enabling the code to function.

### Dependencies
*   **Production Dependencies**:
    *   `react`, `react-dom`: Core libraries for building user interfaces.
    *   `react-router-dom`: For client-side routing.
    *   `antd`: A UI component library.
    *   `axios`: HTTP client for making API requests.
    *   `@react-oauth/google`: Integration for Google OAuth authentication.
    *   `react-hook-form`: For form validation and management.
    *   `react-icons`: A collection of popular SVG icons.
    *   `react-slick`, `slick-carousel`: For carousels and sliders.
    *   `react-toastify`: For notifications.
    *   `react-scripts`: A set of scripts and configuration used by Create React App.
*   **Development Dependencies**:
    *   `tailwindcss`: A utility-first CSS framework used for styling during development and build.
*   **Testing Dependencies**:
    *   `@testing-library/jest-dom`, `@testing-library/react`, `@testing-library/user-event`: Tools for unit and integration testing.

### Design Notes
The project is bootstrapped using `create-react-app` based on the `react-scripts` dependency. This provides a managed build toolchain and a consistent development experience. The `browserslist` configuration indicates a focus on modern browser compatibility. The inclusion of `antd` and `tailwindcss` suggests a hybrid approach to UI development, potentially leveraging Ant Design's pre-built components while allowing for granular styling with Tailwind CSS.

### Diagram (Optional)
None significant.
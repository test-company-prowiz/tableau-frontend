# package.json

### Overview
This file defines the project's metadata, manages its dependencies, and specifies scripts for common development and build tasks. It serves as the manifest for the `tableau_frontend` React application, enabling consistent environment setup and operation.

### Architecture & Role
Within the overall system, this `package.json` file is foundational to the frontend layer, specifically a React-based client-side application. It specifies all third-party libraries required for both development and production, and it defines the commands used to interact with the build toolchain (Create React App scripts). It dictates how the frontend project is built, run, and tested, making it central to the development workflow.

### Key Components
*   **`name`**: `tableau_frontend` - Identifies this specific frontend application module.
*   **`version`**: `0.1.0` - Indicates the current iteration of the project.
*   **`private`**: `true` - Denotes that this package is not intended for publication to a package registry (e.g., npm public registry).
*   **`dependencies`**: Lists all runtime libraries essential for the application's functionality, including core React, UI frameworks (Ant Design), HTTP client (Axios), routing (React Router DOM), and authentication (@react-oauth/google).
*   **`scripts`**: Defines shell commands for starting the development server (`start`), building for production (`build`), running tests (`test`), and ejecting from Create React App configurations (`eject`).
*   **`eslintConfig`**: Specifies the linting configuration, extending standard React application rules.
*   **`browserslist`**: Configures the target browsers for transpilation and polyfilling, ensuring broad compatibility.
*   **`devDependencies`**: Lists libraries used exclusively during development, such as Tailwind CSS for styling.

### Execution Flow / Behavior
When `npm install` or `yarn install` is executed, the package manager reads the `dependencies` and `devDependencies` sections to download and install all specified packages. Subsequently, developers use the `scripts` commands, such as `npm start`, which executes `react-scripts start`. This command initiates the development server, compiles the React application, and serves it, often with hot-reloading capabilities. Similarly, `npm build` executes `react-scripts build` to compile the application into a production-ready static asset bundle.

### Dependencies
*   **Runtime Libraries**:
    *   `react`, `react-dom`: Core libraries for building user interfaces.
    *   `antd`: A comprehensive UI component library.
    *   `axios`: Promise-based HTTP client for making API requests.
    *   `react-router-dom`: Enables declarative routing in the application.
    *   `@react-oauth/google`: Facilitates Google OAuth authentication.
    *   `react-hook-form`: Manages form state and validation efficiently.
    *   `react-icons`: Provides a collection of popular icon libraries.
    *   `react-slick`, `slick-carousel`: Libraries for building carousels and sliders.
    *   `react-toastify`: Adds toast notifications to the application.
*   **Development & Testing Libraries**:
    *   `@testing-library/jest-dom`, `@testing-library/react`, `@testing-library/user-event`: Tools for robust React component testing.
    *   `react-scripts`: A set of scripts used by Create React App to manage the development environment, build process, and testing setup.
    *   `web-vitals`: For measuring core web vital metrics.
    *   `tailwindcss`: A utility-first CSS framework for rapid UI development.

### Design Notes
The project is configured as a private frontend application, indicating it's likely part of a larger system or micro-frontend architecture rather than a standalone open-source library. The reliance on `react-scripts` suggests a Create React App boilerplate setup, which simplifies configuration at the cost of some customizability. The selection of `antd` and other UI component libraries points towards building a feature-rich, visually consistent user interface. The inclusion of `@react-oauth/google` and `axios` indicates the application integrates with external services for authentication and data fetching.

### Diagram (Optional)
None significant.
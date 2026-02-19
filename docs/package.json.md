# package.json

### Overview
This file defines the project's metadata, external dependencies, and a set of scripts for managing development, build, and testing processes for a frontend application.

### Architecture & Role
This file serves as the core configuration for the project's build and dependency management. It operates at the foundational layer, dictating the environment and tooling necessary for a React-based frontend application to function, be developed, and be deployed.

### Key Components
- `name`: `tableau_frontend` - The identifier for the project package.
- `version`: `0.1.0` - The current version of the project.
- `private`: `true` - Designates the package as private, preventing accidental publication to an npm registry.
- `dependencies`: A list of packages required by the application at runtime.
- `scripts`: Defines shell commands aliased for common development tasks.
- `eslintConfig`: Specifies ESLint configuration, inheriting from `react-app` presets.
- `browserslist`: Configures target browsers for CSS autoprefixing and JavaScript transpilation.
- `devDependencies`: A list of packages required only during development and build processes.

### Execution Flow / Behavior
- `npm install`: Reads `dependencies` and `devDependencies` to fetch and install required modules into the `node_modules` directory.
- `npm start`: Executes `react-scripts start`, initiating a local development server with hot module reloading.
- `npm build`: Executes `react-scripts build`, compiling the application for production deployment into static assets.
- `npm test`: Executes `react-scripts test`, running the project's test suite.
- `npm eject`: Executes `react-scripts eject`, removing the abstraction of `react-scripts` and exposing the underlying webpack, Babel, and ESLint configurations.

### Dependencies
- **Runtime Dependencies:**
    - `@react-oauth/google`: Integrates Google OAuth for user authentication.
    - `antd`: A comprehensive UI component library.
    - `axios`: A promise-based HTTP client for making API requests.
    - `react`, `react-dom`: Core libraries for building user interfaces.
    - `react-hook-form`: A library for managing form states and validation.
    - `react-icons`: Provides a collection of popular icons.
    - `react-router-dom`: Enables declarative routing within the application.
    - `react-scripts`: Provides scripts for common operations (start, build, test) as part of Create React App.
    - `react-slick`, `slick-carousel`: Components for creating carousels and sliders.
    - `react-toastify`: For displaying toast notifications.
    - `@testing-library/jest-dom`, `@testing-library/react`, `@testing-library/user-event`, `web-vitals`: Utilities for testing React components and measuring web performance.
- **Development Dependencies:**
    - `tailwindcss`: A utility-first CSS framework used for styling during development.

### Design Notes
- The `private: true` flag indicates this project is likely an internal application not intended for public package distribution.
- The reliance on `react-scripts` suggests the project was initialized using Create React App, benefiting from its opinionated setup for quick starts and reduced configuration burden.
- The use of `antd` and `tailwindcss` concurrently suggests a strategy combining a robust component library with a utility-first CSS framework for flexible styling.
- The extensive list of testing libraries points to an emphasis on comprehensive unit and integration testing.

### Diagram (Optional)
None significant.
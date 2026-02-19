# tableau-frontend — Repository Overview

### High-Level Purpose
This repository implements the `tableau_frontend` project, a client-side React-based frontend application. Its primary objective is to deliver an interactive user interface, managing all necessary project dependencies, build processes, and runtime configurations.

### Architectural Structure
This repository represents a single-page application (SPA) built using React. Its architectural setup is based on `create-react-app` conventions, leveraging `react-scripts` to standardize and manage core development activities such as starting the development server, compiling for production, and running tests.

### Core Components
*   **Application Manifest**: The `package.json` file serves as the central manifest, defining project metadata, versioning, and privacy settings.
*   **Package Dependencies**: Categorized into `dependencies` for runtime requirements (e.g., UI, routing, data fetching) and `devDependencies` for build and quality assurance tools.
*   **Development Scripts**: Pre-defined command-line scripts (`start`, `build`, `test`, `eject`) to automate common development and deployment tasks.
*   **Configuration**: Integrated configurations for ESLint for code quality and `browserslist` for target browser compatibility.

### Interaction & Data Flow
The application's runtime interaction primarily occurs client-side through the React UI. Data retrieval from external services is managed via `axios`. User authentication processes utilize `@react-oauth/google`. During development, `npm start` initiates the application, while `npm build` generates deployable assets. `npm test` executes the configured test suite.

### Technology Stack
*   **Frontend Framework**: React (`react`, `react-dom`).
*   **UI Components & Styling**: Ant Design (`antd`), React Icons, React Slick (`react-slick`, `slick-carousel`), Tailwind CSS (`tailwindcss` - dev).
*   **Routing**: React Router DOM (`react-router-dom`).
*   **Form Management**: React Hook Form (`react-hook-form`).
*   **Data Fetching**: Axios (`axios`).
*   **Authentication**: Google OAuth via `@react-oauth/google`.
*   **Build & Development Tools**: `react-scripts` (Create React App), ESLint.
*   **Testing**: React Testing Library (`@testing-library/*`).

### Design Observations
The repository is configured as a private package, indicating it is not intended for publication as a library. The use of `react-scripts` centralizes and simplifies build and configuration management, trading direct control over underlying tools for ease of setup. The selection of comprehensive UI libraries like Ant Design and component-specific libraries such as React Slick suggests an emphasis on creating a rich, interactive, and visually appealing user experience.

### System Diagram (Optional)
None significant.
# tableau-frontend — Repository Overview

### High-Level Purpose
This repository hosts a React-based single-page application (SPA) designed to provide a frontend interface. Its primary objective is to present interactive content, notably through the integration of Tableau dashboards, while supporting user authentication via Google OAuth and offering Progressive Web App (PWA) capabilities.

### Architectural Structure
The repository is organized to support a Create React App-based frontend.
*   **Root Configuration**: `package.json` defines project metadata, dependencies, and core development scripts.
*   **Public Assets**: The `public/` directory contains static assets, including the `index.html` entry point, the `manifest.json` for PWA features, and application icons. `index.html` is the foundational HTML document and the mount point for the client-side JavaScript application.
*   **Source Code**: The `src/` directory is intended for the application's React components, logic, and associated styling (e.g., `App.css`).
*   **Dependency Management**: External libraries are managed via npm, with installed modules residing in `node_modules`.

### Core Components
*   **React Application**: The central user interface built with React, rendered into the `<div id="root">` element in `index.html`.
*   **Tableau Embedding API**: Loaded directly in `index.html`, this API facilitates the embedding and interaction with Tableau dashboards within the application.
*   **UI Frameworks**: Ant Design provides a comprehensive set of UI components, complemented by Tailwind CSS for utility-first styling.
*   **Routing**: `react-router-dom` manages client-side navigation and view transitions.
*   **Form Management**: `react-hook-form` is used for handling form states and validation.
*   **HTTP Client**: `axios` is the primary library for making API requests to backend services.
*   **Authentication**: `@react-oauth/google` integrates Google OAuth for user authentication.
*   **PWA Manifest**: `manifest.json` configures the application for "Add to Home Screen" and app-like behavior on user devices.
*   **Global Styling**: `App.css` defines base layouts, global styles, and specific overrides for UI components like carousels and loading indicators.

### Interaction & Data Flow
1.  A user's browser requests the `index.html` file, which is the application's entry point.
2.  `index.html` loads critical resources, including the Tableau Embedding API script, and defines the `<div id="root">`.
3.  The main JavaScript bundle (the compiled React application) loads and executes, mounting its root component into the `#root` element.
4.  The React application uses `react-router-dom` to manage different views and navigation.
5.  `axios` performs asynchronous HTTP requests to external backend APIs for data retrieval and submission.
6.  The `@react-oauth/google` library handles user authentication flows, typically redirecting to Google for sign-in.
7.  The Tableau Embedding API is then utilized by React components to render and interact with embedded Tableau dashboards.
8.  Styling from `App.css`, Ant Design, and Tailwind CSS is applied throughout the UI rendering process.

### Technology Stack
*   **Frontend Framework**: React.js
*   **Build Tooling**: Create React App (`react-scripts`)
*   **UI Libraries**: Ant Design, Slick Carousel
*   **Styling**: Tailwind CSS, standard CSS
*   **Routing**: React Router DOM
*   **HTTP Client**: Axios
*   **Authentication**: Google OAuth (`@react-oauth/google`)
*   **Data Visualization Integration**: Tableau Embedding API
*   **Testing**: React Testing Library, Jest
*   **Linting**: ESLint
*   **Web Performance**: Web Vitals

### Design Observations
*   The project leverages Create React App, benefiting from its opinionated setup for rapid development and reduced configuration overhead.
*   The `private: true` flag in `package.json` suggests this is an internal application not intended for public npm distribution.
*   The application adopts a hybrid styling strategy, combining a comprehensive component library (Ant Design) with a utility-first CSS framework (Tailwind CSS) for flexible and efficient styling.
*   Early inclusion of the Tableau Embedding API script in `index.html` indicates that Tableau dashboard integration is a core and foundational aspect of the application's functionality.
*   The presence of `manifest.json` and related metadata points to an emphasis on Progressive Web App features, aiming for an installable, app-like user experience.
*   Extensive testing dependencies (e.g., React Testing Library, Jest) suggest a strong focus on unit and integration testing.

### System Diagram (Optional)
```mermaid
graph TD
Browser --> A[public/index.html]
A --> B[Load Tableau Embedding API]
A --> C[Mount React App into #root]
C --> D[React Application]
D --> E[Backend API (Axios)]
D --> F[Google OAuth Service]
D --> G[Tableau Embedding API]
```
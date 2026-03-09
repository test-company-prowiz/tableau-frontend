 tableau-frontend — Repository Overview

 High-Level Purpose
This repository hosts a client-side web application, built as a Single-Page Application SPA, primarily focused on displaying and interacting with Tableau dashboards. It integrates user authentication, leverages modern UI frameworks, and provides a structured interface for accessing Tableau visualizations.

 Architectural Structure
The repository is structured around a standard Create React App CRA project layout

*   **Root Level** Contains project configuration files such as `package.json` for dependency management and `tailwind.config.js` for styling framework configuration.
*   **`public/` Directory** Serves static assets, including the main `index.html` entry point, application manifest `manifest.json`, and various icons.
*   **`src/` Directory** Houses the applications source code, organized into functional concerns
    *   **`src/Pages/`** Top-level React components representing distinct application views e.g., `Login`, `Dashboard`.
    *   **`src/Mock/`** Contains static mock data used for development and testing purposes.
    *   **`src/App.css`** Global application styles.
    *   Other implicitly present directories for components, utilities, and services common in a React application.

 Core Components
*   **`package.json`** Manages project metadata, dependencies, and build/development scripts.
*   **`public/index.html`** The single HTML entry point for the SPA, responsible for loading the React application and initializing the Tableau Embedding API.
*   **React Components** Modular UI elements `src/Pages/Login.jsx`, `src/Pages/Dashboard.jsx` that handle user interaction, state management, and data presentation.
*   **Tableau Embedding API** An external JavaScript library integrated via `index.html` and utilized by the `Dashboard` component to embed interactive Tableau visualizations.
*   **Authentication Logic** Implemented within the `Login` component, supporting both email/password and Google OAuth, interacting with a backend API.
*   **HTTP Client `axios`** Used across components for making API requests to backend services for authentication and Tableau token retrieval.
*   **Styling System** A combination of Tailwind CSS configured via `tailwind.config.js` for utility-first styling and Ant Design for pre-built UI components, augmented by global CSS in `src/App.css`.
*   **Client-side Router `react-router-dom`** Manages navigation between different application views.

 Interaction & Data Flow
1.  A users browser requests `index.html`, which serves as the applications entry point.
2.  `index.html` loads the core React application bundle, the Tableau Embedding API script, and other static assets.
3.  The React application mounts, displaying either a `Login` or `Dashboard` view based on routing and authentication state.
4.  **Authentication Flow**
    *   The `Login` component captures user credentials email/password or initiates a Google OAuth flow.
    *   Credentials or the Google access token are sent to a backend authentication API via `axios`.
    *   Upon successful authentication, the user is navigated to the applications home or dashboard route.
5.  **Dashboard Display Flow**
    *   The `Dashboard` component receives Tableau dashboard path information.
    *   It requests a Tableau authentication token from a backend API via `axios`.
    *   Using the retrieved token and the Tableau Embedding API, the `Dashboard` component dynamically injects a `tableau-viz` custom element into the DOM, rendering the specified Tableau visualization.
6.  User interactions trigger further state updates and potentially new API calls within the React application.

 Technology Stack
*   **Frontend Framework** React.js
*   **Build System** Create React App `react-scripts`
*   **Styling** Tailwind CSS, Ant Design, CSS
*   **HTTP Client** `axios`
*   **Routing** `react-router-dom`
*   **Authentication** Google OAuth `@react-oauth/google`
*   **Form Management** `react-hook-form`
*   **UI Components** `antd`, `react-slick`, `react-toastify`, `react-icons`
*   **Embedded Content** Tableau Embedding API JavaScript, `tableau-viz` web component
*   **Development Tools** Node.js, npm

 Design Observations
The project employs a standard Create React App setup, which simplifies build tooling but can limit customization without ejecting. The use of both Ant Design and Tailwind CSS offers flexibility but may require careful management to maintain visual consistency. Direct DOM manipulation for embedding Tableau dashboards, while functional, bypasses Reacts virtual DOM, requiring attention to lifecycle management. A basic client-side token caching mechanism is present, but could be enhanced for robustness. The inclusion of `manifest.json` indicates support for Progressive Web App PWA features. Mock data is used for development, demonstrating a decoupled frontend development approach.

 System Diagram
```mermaid
graph TD
Browser -- Frontend SPA
Frontend SPA -- Auth Backend
Frontend SPA -- Tableau Token Backend
Frontend SPA -- Tableau Embedding JS API
Tableau Embedding JS API -- Tableau Server
```
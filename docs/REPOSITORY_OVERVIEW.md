 tableau-frontend — Repository Overview

 High-Level Purpose
The `tableau-frontend` repository hosts a single-page application SPA built with React, primarily designed to embed and display interactive Tableau dashboards. Its core function involves user authentication, secure retrieval of Tableau access tokens from a backend, and the dynamic rendering of specific Tableau visualizations within its interface. It also incorporates Progressive Web App PWA capabilities for an enhanced user experience.

 Architectural Structure
The repository is structured as a client-side React application.
*   **`public/`** Contains static assets such as `index.html` the SPA entry point, manifest files `manifest.json`, and application icons.
*   **`src/`** Houses the core application logic, React components, styling, and utility modules.
    *   **`src/Pages/`** Contains top-level page components, like `Login.jsx` and `Dashboard.jsx`, which define major views.
    *   **`src/Mock/`** Stores static mock data used for development and testing purposes.
    *   **`src/App.css`** Global application styling.
*   **`package.json`** Manages project metadata, dependencies, and build scripts.
*   **`tailwind.config.js`** Configures Tailwind CSS for utility-first styling.

 Core Components
*   **`package.json`** Defines project dependencies React, Ant Design, Axios, React Router, development scripts start, build, test, and build configurations ESLint, browserslist.
*   **`public/index.html`** The main HTML entry point, which loads the React application and pre-loads critical external scripts like the Tableau Embedding API. It also defines the `root` mount point for the React app.
*   **`public/manifest.json`** Provides metadata for Progressive Web Application PWA features, including app name, icons, and display modes.
*   **`src/Pages/Login.jsx`** Manages user authentication, supporting both email/password login and Google OAuth, interacting with a backend authentication API.
*   **`src/Pages/Dashboard.jsx`** Responsible for fetching Tableau authentication tokens from a backend, dynamically embedding Tableau dashboards using the `tableau-viz` web component, and providing navigation controls.
*   **`src/App.css`** Contains global styles and overrides for UI components, particularly `react-slick` carousels and loading indicators.
*   **`src/Mock/view.js`** Provides static mock data for views, used to simulate backend responses during development.

 Interaction & Data Flow
1.  **Application Load** A browser request fetches `public/index.html`. This document loads the Tableau Embedding API script and serves as the mount point for the React application.
2.  **Authentication** The React application initializes, typically rendering the `Login` page. Users can log in via email/password or Google OAuth. Both methods send authentication requests to a backend API `${API}/auth/`.
3.  **Navigation** Upon successful authentication, the application navigates to the `/home` route or directly to a specific dashboard.
4.  **Dashboard Display** The `Dashboard` component, when mounted, extracts the target Tableau dashboard path from route state. It then requests a secure Tableau authentication token from a backend endpoint `${API}/tableau/token`.
5.  **Tableau Embedding** With the token, the `Dashboard` component dynamically creates and injects a `tableau-viz` web component into the DOM, embedding the specified Tableau visualization.
6.  **User Interaction** Users can interact with the embedded Tableau dashboard and navigate back to the home view or log out, which clears the session cookie and redirects to the login page.

 Technology Stack
*   **Frontend Framework** React
*   **Build Tooling** Create React App implied by `react-scripts`, Webpack, Babel
*   **UI Libraries** Ant Design `antd`, Tailwind CSS
*   **Styling** CSS, PostCSS
*   **HTTP Client** Axios
*   **Routing** React Router DOM
*   **Form Management** React Hook Form
*   **Authentication** Google OAuth `@react-oauth/google`
*   **Icons** React Icons `react-icons`
*   **Carousel** React Slick `react-slick`, Slick Carousel
*   **Notifications** React Toastify `react-toastify`
*   **Embedded Visualization** Tableau Embedding API
*   **Development Utilities** ESLint, Web Vitals
*   **Package Manager** npm Node.js

 Design Observations
The application leverages Create React Apps managed build configuration, abstracting complex tooling setup. It combines `antd` for structured UI components with `tailwindcss` for flexible, utility-first styling, indicating a hybrid approach to design. Tableau dashboard embedding is implemented via direct DOM manipulation of the `tableau-viz` web component. A client-side caching mechanism for the Tableau authentication token is present to optimize backend calls. The `manifest.json` enables PWA features for enhanced installability and user experience. The inclusion of `npm` and `i` in `dependencies` is an unusual configuration for a production application and could warrant review. The use of `!important` in global CSS for `.workbooks` suggests specific styling overrides for layout elements.

 System Diagram
None significant.
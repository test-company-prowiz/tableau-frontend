 tableau-frontend — Repository Overview

 High-Level Purpose
The `tableau-frontend` repository hosts a client-side React application designed to provide authenticated users with access to and interaction with Tableau dashboards and views. Its primary objective is to serve as a user interface for discovering, browsing, and displaying Tableau visualizations, integrating user authentication and dynamic content loading.

 Architectural Structure
The repository follows a conventional Create React App CRA structure, indicating a Single-Page Application SPA architecture.

-   **`public/`** Contains static assets like `index.html` the applications entry point, `manifest.json` for PWA capabilities, and various icon files.
-   **`src/`** Houses the core application logic, components, pages, and services.
    -   **`src/App.jsx`** The root React component, responsible for defining global routing and application-wide configurations e.g., API base URL.
    -   **`src/Pages/`** Contains top-level page components e.g., `Login`, `Home`, `Dashboard`, each encapsulating the logic and UI for a specific application view.
    -   **`src/Components/`** Likely for reusable UI components, though `Sidenav` is imported but not used in the provided summaries.
    -   **`src/Services/`** Intended for API interaction logic, with `api_service` imported but not directly used in the current `Login.jsx` logic.
    -   **`src/Mock/`** Contains static mock data for development or testing purposes e.g., `view.js`, `workbooks.js`.
    -   **`src/App.css`** Global stylesheet for the application.
-   **Configuration Files** `package.json` manages dependencies and scripts, `tailwind.config.js` configures Tailwind CSS.

 Core Components
-   **React Application `App.jsx`** The orchestrator for client-side routing and page rendering.
-   **Routing `react-router-dom`** Manages navigation between `Login`, `Home`, and `Dashboard` pages.
-   **Authentication Pages `Login.jsx`** Handles user authentication via email/password forms and Google OAuth, interacting with a backend authentication service.
-   **Home Page `Home.jsx`** Displays carousels of Tableau workbooks and lists of views, with search and filtering capabilities, fetching data from a backend Tableau proxy.
-   **Dashboard Page `Dashboard.jsx`** Embeds specific Tableau dashboards using the Tableau Embedding API and `tableau-viz` web components, securing access with tokens fetched from the backend.
-   **UI Frameworks** `antd` provides a comprehensive set of UI components, while `tailwindcss` is used for utility-first styling.
-   **Data Fetching `axios`** Handles HTTP requests to the backend for authentication, Tableau data, and Tableau tokens.
-   **Carousel `react-slick`** Used on the `Home` page for displaying workbooks.
-   **Form Management `react-hook-form`** Streamlines form state and validation, used in `Login.jsx`.
-   **Notifications `react-toastify`** Provides user feedback for success or error states.
-   **Tableau Embedding API** An external JavaScript library `tableau.embedding.3.latest.js` integrated via `index.html` for rendering interactive Tableau visualizations.

 Interaction & Data Flow
1.  **Application Bootstrapping** A browser requests `public/index.html`. This HTML loads the Tableau Embedding API and acts as the mount point for the React application.
2.  **User Authentication** The `Login` page is initially displayed. Users can authenticate using email/password or Google OAuth. Both methods send credentials/tokens to a backend authentication service `${API}/auth/`.
3.  **Session Establishment** Upon successful authentication, the backend likely sets a session cookie managed by `document.cookie` on logout.
4.  **Home Page Interaction** After login, the user is redirected to the `Home` page. This page fetches lists of Tableau workbooks `${API}/tableau/workbooks` and views `${API}/tableau/views` from the backend. Users can browse workbooks via a carousel, search views, and filter views based on selected workbooks.
5.  **Dashboard Display** When a user selects a specific view from the `Home` page, they are navigated to the `Dashboard` page. The `Dashboard` page retrieves a short-lived Tableau authentication token from the backend `${API}/tableau/token` and dynamically injects a `tableau-viz` web component into the DOM to render the chosen Tableau dashboard securely.
6.  **Logout** A logout action clears the local session cookie and redirects the user back to the `Login` page.

 Technology Stack
-   **Frontend Framework** React with `create-react-app` setup.
-   **Language** JavaScript ES6+.
-   **Build Tooling** `react-scripts`, PostCSS for Tailwind CSS processing.
-   **Package Manager** `npm`.
-   **UI Libraries** `antd`, `tailwindcss`.
-   **HTTP Client** `axios`.
-   **Routing** `react-router-dom`.
-   **Authentication** Google OAuth `@react-oauth/google`.
-   **Form Management** `react-hook-form`.
-   **UI Components** `react-slick`, `react-icons`, `@ant-design/icons`, `react-toastify`.
-   **External APIs** Tableau Embedding API.

 Design Observations
-   **CRA Simplification** The use of `react-scripts` provides an opinionated and managed build configuration, abstracting complex Webpack and Babel setups. The `private true` in `package.json` confirms it as an application, not a library.
-   **Hybrid UI Styling** The project uses both `antd` for structured components and `tailwindcss` for utility-first styling. This approach might offer flexibility but could also lead to inconsistent styling patterns or increased bundle size if not managed carefully.
-   **Direct Tableau Embedding** Tableau visualizations are embedded by dynamically injecting raw HTML containing the `tableau-viz` custom element, a standard method for integrating web components.
-   **Client-Side Token Caching** The `Dashboard` component implements a short-term 10 minute client-side cache for Tableau authentication tokens, reducing redundant backend requests.
-   **Incomplete Authentication Flow** The `isUserLoggedIn` state in `App.jsx` is hardcoded to `true`, indicating that the complete authentication check logic via `apiService` is pending or bypassed for development.
-   **Atypical Dependencies** The `package.json` lists `i` npm install alias and `npm` itself in `dependencies`, which is unusual for a runtime application and might warrant review.
-   **Mock Data Presence** Mock data files exist but are not actively used by the `Home` pages data fetching logic, suggesting they were for initial development or are intended for specific testing scenarios.
-   **Direct Cookie Manipulation** The logout functionality directly clears `document.cookie`, which is effective but can be less encapsulated than using a dedicated authentication service.

 System Diagram
None significant.
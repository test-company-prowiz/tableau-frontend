# tableau-frontend — Repository Overview

### High-Level Purpose
This repository contains a React frontend application designed to integrate with Tableau dashboards. Its primary objective is to authenticate users, enable browsing and searching of Tableau workbooks and views, and securely embed interactive Tableau dashboards within the application interface. The system provides a unified portal for accessing and interacting with Tableau content.

### Architectural Structure
The repository is structured as a single-page application (SPA) built with React.
*   **Root Level**: Configuration files like `package.json` (dependency and build management) and `tailwind.config.js` (styling configuration).
*   **`public/`**: Contains static assets, including `index.html` (the SPA entry point), `manifest.json` (PWA configuration), and application icons.
*   **`src/`**: Houses the core application logic and components:
    *   **`src/App.jsx`**: The root React component, responsible for client-side routing.
    *   **`src/Pages/`**: Contains high-level page components such as `Login`, `Home`, and `Dashboard`.
    *   **`src/Components/`**: Intended for reusable UI components (e.g., `Sidenav`).
    *   **`src/Services/`**: Dedicated for API service abstraction (e.g., `api_service`).
    *   **`src/Mock/`**: Provides static mock data for development and testing.
    *   **`src/App.css`**: Contains global application-wide styles.

### Core Components
*   **Dependency and Build Manifest (`package.json`)**: Defines project metadata, runtime and development dependencies, and scripts for build, start, and test operations.
*   **SPA Entry Point (`public/index.html`)**: The initial HTML document loaded by the browser, providing the root element for the React application and pre-loading the Tableau Embedding API.
*   **Application Router (`src/App.jsx`)**: Configures `react-router-dom` to manage client-side navigation between different application views.
*   **Authentication Page (`src/Pages/Login.jsx`)**: Manages user authentication through traditional email/password forms and Google OAuth, interacting with a backend authentication API.
*   **Home/Browser Page (`src/Pages/Home.jsx`)**: Displays available Tableau workbooks in a carousel, lists associated views, and provides search/filtering capabilities. It fetches data from a backend API.
*   **Dashboard Embedding Page (`src/Pages/Dashboard.jsx`)**: Dynamically embeds a selected Tableau dashboard using the Tableau Embedding API, including fetching necessary authentication tokens from the backend.
*   **PWA Manifest (`public/manifest.json`)**: Configures the application for Progressive Web App features, specifying icons, display modes, and other metadata for device integration.
*   **Styling Configuration (`tailwind.config.js`, `src/App.css`)**: Manages custom Tailwind CSS settings and global CSS rules for application-wide visual presentation.

### Interaction & Data Flow
1.  **Initial Application Load**: A user's browser request for the application URL results in the web server serving `public/index.html`. This document loads the compiled React application bundle and the Tableau Embedding API script.
2.  **Client-Side Routing**: The `src/App.jsx` component initializes `react-router-dom`, directing unauthenticated users to the `src/Pages/Login.jsx` page.
3.  **User Authentication**: On the `Login` page, users authenticate either via an email/password form or Google OAuth. `axios` requests are sent to the backend's `/auth/` endpoint. Upon successful authentication, the application navigates to `src/Pages/Home.jsx`.
4.  **Data Retrieval on Home**: The `src/Pages/Home.jsx` component fetches lists of Tableau workbooks and views from specific backend API endpoints (`/tableau/workbooks`, `/tableau/views`) using `axios`. These are then displayed, allowing users to search, filter, and select content.
5.  **Dashboard Navigation**: When a user selects a specific view on the `Home` page, `react-router-dom` navigates to `src/Pages/Dashboard.jsx`, passing the selected view's content URL as state.
6.  **Tableau Dashboard Embedding**: The `src/Pages/Dashboard.jsx` component requests a Tableau authentication token from the backend (`/tableau/token`) using `axios`. This token is then used to dynamically create and inject a `tableau-viz` web component into the DOM, which renders the interactive Tableau dashboard fetched from the Tableau Server.
7.  **Logout**: Logout functionality, available on `Home.jsx` and `Dashboard.jsx`, clears the `session` cookie and redirects the user to the root login path.

### Technology Stack
*   **Frontend Framework**: React (with Create React App tooling, implied by `react-scripts`).
*   **Routing**: `react-router-dom`.
*   **UI Libraries**: Ant Design (`antd`), Tailwind CSS (primarily for development and utility-first styling).
*   **HTTP Client**: `axios`.
*   **Authentication**: Google OAuth (`@react-oauth/google`).
*   **Form Management**: `react-hook-form`.
*   **Carousel**: `react-slick`, `slick-carousel`.
*   **Icons**: `react-icons`, `@ant-design/icons`.
*   **Notifications**: `react-toastify`.
*   **Tableau Integration**: Tableau Embedding API (via `tableau.embedding.3.latest.js`).
*   **Language**: JavaScript/JSX.
*   **Build Tooling**: npm (managed via `package.json`).

### Design Observations
*   The application adheres to a Single-Page Application (SPA) architecture, with `index.html` as the sole entry point and client-side routing.
*   It appears to be bootstrapped with Create React App (CRA) due to the presence of `react-scripts` and the use of `%PUBLIC_URL%` placeholders, indicating a managed and opinionated build setup.
*   The UI layers combine Ant Design components for structured elements with Tailwind CSS for utility-first styling, potentially leading to a larger CSS footprint if not efficiently managed.
*   Authentication is handled by a backend service, supporting both traditional and Google OAuth methods, with `session` cookies used for state management. A client-side caching mechanism for the Tableau token is implemented for performance.
*   The `isUserLoggedIn` state in `src/App.jsx` is hardcoded `true`, indicating a development state where backend authentication is bypassed for accessing internal routes.
*   The `Sidenav` component is present but commented out, suggesting an incomplete or paused feature related to application navigation.
*   Tableau integration is achieved through direct DOM manipulation to embed the `tableau-viz` web component, which requires careful management of the embedding API and secure token handling.
*   The project includes mock data files, indicating a strategy for independent frontend development, though the live application relies on `axios` for data fetching.

### System Diagram
```mermaid
graph TD
A[Browser Request] -- B[Web Server]
B -- C[index html]
C -- D[React App]
D -- E[Router]
E -- F[Login Page]
F -- G[Backend Auth API]
G -- F
F -- H[Home Page]
E -- H
H -- I[Backend Tableau Data API]
I -- H
H -- J[Dashboard Page]
E -- J
J -- K[Backend Tableau Token API]
K -- J
J -- L[Tableau Embedding API]
L -- M[Tableau Server]
```
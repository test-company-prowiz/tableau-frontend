# src/Pages/Dashboard.jsx

> **Source File:** [src/Pages/Dashboard.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Pages/Dashboard.jsx)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

# src/Pages/Dashboard.jsx

### Overview
This file defines the Dashboard React component, which is responsible for displaying an embedded Tableau dashboard. It handles authentication with a backend service to retrieve a Tableau token and dynamically injects the Tableau visualization into the page.

### Architecture & Role
This file functions as a client-side page component within a React application. It resides in the presentation layer, specifically a "Pages" directory, indicating it represents a primary view. Its role is to orchestrate the display of external Tableau content and manage user navigation and logout actions.

### Key Components
*   **`Dashboard` Function Component**: The main React component that renders the dashboard page.
*   **`useLocation` Hook**: Used to access the state passed during navigation, specifically to retrieve the Tableau dashboard URL.
*   **`useNavigate` Hook**: Provides programmatic navigation capabilities within the application.
*   **`useEffect` Hook**: Manages side effects, specifically initiating the Tableau dashboard loading process when the component mounts.
*   **`getToken` Async Function**: Fetches an authentication token from the backend API (`/tableau/token`) required to embed the Tableau visualization. It caches the token client-side for a limited duration (10 minutes).
*   **`loadTableau` Async Function**: Takes a dashboard path, retrieves an authentication token using `getToken`, and dynamically injects a `<tableau-viz>` custom element into the DOM.
*   **`IoArrowBackSharp`**: An icon used for navigating back to the home page.

### Execution Flow / Behavior
1.  When the `Dashboard` component mounts, the `useEffect` hook is triggered.
2.  Inside `useEffect`, the dashboard URL is extracted from `location.state.data` and processed to remove an initial path segment.
3.  The `loadTableau` function is called with the processed URL.
4.  `loadTableau` first invokes `getToken` to acquire a Tableau authentication token.
5.  `getToken` performs an asynchronous HTTP GET request to `${API}/tableau/token`.
6.  Upon successful token retrieval, `getToken` stores the token in a local `token` variable and sets a timeout to nullify it after 10 minutes (6e5 milliseconds).
7.  Once `getToken` returns a valid token, `loadTableau` constructs an HTML string containing a `<tableau-viz>` custom element. This element is configured with the Tableau host, content URL, dashboard path, fetched token, and specified dimensions.
8.  This HTML string is then injected directly into the `innerHTML` of the `div` element with `id="tableau"`, effectively embedding the Tableau dashboard.
9.  Users can navigate back to the home page using the back arrow icon or log out by clicking "Logout," which clears the `session` cookie and redirects to the root path (`/`).

### Dependencies
*   **`react`**: Core library for building user interfaces.
*   **`react-router-dom`**: For client-side routing and navigation context.
*   **`axios`**: Promise-based HTTP client used for making API requests to the backend.
*   **`react-icons/io5`**: Provides the back arrow icon used in the navigation header.
*   **`../App` (local)**: Imports the `API` constant, which defines the base URL for backend API calls.

### Design Notes
*   The component uses direct DOM manipulation (`document.getElementById("tableau").innerHTML = tp;`) to embed the Tableau visualization, which deviates from typical React declarative patterns.
*   Tableau authentication tokens are cached client-side within the component's scope using a `let` variable and a `setTimeout` for invalidation. This reduces repeated backend calls for tokens during a user session but is not persistent across page reloads.
*   The Tableau host and content URL are hardcoded constants within the component.
*   Logout functionality directly manipulates the `document.cookie` to clear the session.

### Diagram
```mermaid
graph TD
A[Dashboard Component Mount] --> B{useEffect}
B --> C[Parse Dashboard URL from State]
C --> D[Call loadTableau]
D --> E[Call getToken]
E --> F[API GET /tableau/token]
F --> G{Token Received?}
G -- Yes --> H[Cache Token for 10 min]
G -- No --> I[Handle Token Error]
H --> J[Construct tableau-viz HTML]
J --> K[Inject HTML into "tableau" div]
K --> L[Tableau Dashboard Displayed]
```
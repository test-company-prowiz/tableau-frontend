# src/Pages/Dashboard.jsx

> **Source File:** [src/Pages/Dashboard.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Pages/Dashboard.jsx)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

# src/Pages/Dashboard.jsx

### Overview
This file defines a React component responsible for rendering a Tableau dashboard within the application. It manages fetching an authentication token from a backend service and dynamically embedding the Tableau visualization using a web component.

### Architecture & Role
This file functions as a presentation layer component, specifically a page within the application's user interface. It integrates with the `react-router-dom` for navigation and state management, acting as the target for displaying specific Tableau content. It depends on a backend API endpoint to acquire necessary authentication tokens for accessing Tableau.

### Key Components
*   **`Dashboard` function component**: The primary React component that renders the Tableau dashboard UI, including navigation controls.
*   **`useLocation` hook**: Utilized to access navigation state, specifically to retrieve the Tableau dashboard path passed from a preceding route.
*   **`useNavigate` hook**: Provides functionality for programmatic navigation to other routes within the application (e.g., `/home`, `/`).
*   **`useEffect` hook**: Triggers the initial loading and rendering of the Tableau dashboard once the component mounts.
*   **`getToken` async function**: Handles the retrieval of a Tableau authentication token from the application's backend API. It implements a client-side caching mechanism for the token with a 10-minute expiry.
*   **`loadTableau` async function**: Takes a dashboard path, retrieves an authentication token via `getToken`, and dynamically injects the `<tableau-viz>` web component into the DOM to display the Tableau dashboard.
*   **`IoArrowBackSharp`**: An icon component used for the "Back" navigation button.

### Execution Flow / Behavior
1.  When the `Dashboard` component mounts, the `useEffect` hook is triggered.
2.  Inside `useEffect`, `useLocation().state.data` is accessed to obtain the Tableau view's URL path. This path is then parsed by removing a segment.
3.  The `loadTableau` function is invoked with the parsed dashboard path.
4.  `loadTableau` calls `getToken` to acquire an authentication token.
5.  `getToken` first checks if a `token` is already cached and valid. If not, it makes an authenticated GET request to `${API}/tableau/token` using Axios. If successful, the received token is cached locally for 10 minutes.
6.  Once `getToken` returns a valid token, `loadTableau` constructs an HTML string representing a `<tableau-viz>` web component, including the Tableau host, content URL, dashboard path, token, and display properties.
7.  This constructed HTML is then injected into the `innerHTML` of the `div` element with `id="tableau"`, causing the Tableau dashboard to render.
8.  Users can navigate back to the `/home` route by clicking the `IoArrowBackSharp` icon, which uses `navigate("/home")`.
9.  Clicking the "Logout" text clears the `session` cookie by setting its expiration date to a past value and then navigates the user to the root path (`/`).

### Dependencies
*   **`react`**: The core library for building the user interface.
*   **`react-router-dom`**: Provides routing functionalities, specifically `useLocation` for accessing route state and `useNavigate` for programmatic navigation.
*   **`axios`**: An HTTP client used for making asynchronous requests to the backend API to retrieve the Tableau authentication token.
*   **`../App`**: An internal dependency providing the `API` constant, which defines the base URL for backend API calls.
*   **`react-icons/io5`**: Provides the `IoArrowBackSharp` icon used for UI navigation.
*   **Tableau Embedding API (runtime)**: The functionality implicitly relies on the Tableau Embedding JavaScript library being loaded globally in the browser environment, as it defines the `<tableau-viz>` web component.

### Design Notes
*   **Dynamic Web Component Injection**: The Tableau dashboard is embedded by dynamically constructing and injecting a `<tableau-viz>` web component via `innerHTML`. This approach assumes the Tableau Embedding API script is loaded externally, making the custom element available.
*   **Client-Side Token Caching**: The `getToken` function caches the Tableau authentication token for a period of 10 minutes. This reduces the number of calls to the backend API, optimizing token retrieval frequency. The `withCredentials: true` option in the Axios request indicates that cookies, potentially including session identifiers, are sent with the request to the backend.
*   **State-Based Data Transfer**: The specific Tableau dashboard to display is expected to be passed to this component through `location.state.data` from the navigating component. This couples the `Dashboard` component to the data structure provided by previous routes.
*   **Hardcoded Tableau Configuration**: The `TABLEAU_HOST` and `TABLEAU_CONTENT_URL` are hardcoded. This simplifies configuration but reduces flexibility if the Tableau environment needs to change or if multiple content URLs are required.
*   **URL Parsing Logic**: The dashboard path from `location.state.data` undergoes a specific parsing operation (`split("/").filter((_, i) => i !== 1).join("/")`). This indicates an expectation of a particular URL structure where the second segment needs to be removed.
*   **Potential XSS Concern**: Using `innerHTML` to inject dynamically constructed HTML can introduce Cross-Site Scripting (XSS) vulnerabilities if the data used to construct the HTML (e.g., `dash`, `token`) comes from untrusted or unvalidated sources. Given `dash` is derived from `location.state` and `token` from a backend API, the trust model for these inputs is critical.

### Diagram
```mermaid
graph TD
A[Dashboard Component Mounts] --> B{Get Tableau Dashboard Path from location.state};
B --> C[Call loadTableaupath];
C --> D{Call getToken()};
D --> E{Is Token Cached and Valid?};
E -- No --> F[Make API Request to Backend for Token];
F --> G[Receive Tableau Token];
E -- Yes --> G;
G --> H[Construct tableau-viz HTML string];
H --> I[Inject HTML into DOM id="tableau"];
I --> J[Tableau Dashboard Rendered];
```
# src/Pages/Dashboard.jsx

> **Source File:** [src/Pages/Dashboard.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Pages/Dashboard.jsx)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

 src/Pages/Dashboard.jsx

 Overview
This file defines the `Dashboard` React component, which is responsible for rendering an embedded Tableau dashboard. It handles fetching an authentication token from a backend service and dynamically injecting the `tableau-viz` web component to display the specified dashboard.

 Architecture & Role
This file resides in the frontends presentation layer as a React component. It functions as a view component that displays external content Tableau dashboards to the user. It interacts with both the client-side routing system `react-router-dom` and a backend API `axios` to fulfill its purpose.

 Key Components
*   **`Dashboard` Functional Component** The primary React component rendered as a page.
*   **`useEffect` Hook** Manages the side effect of loading the Tableau dashboard upon component mount.
*   **`useLocation` Hook** Retrieves state data, specifically the Tableau dashboard URL, passed during navigation.
*   **`useNavigate` Hook** Provides programmatic navigation capabilities within the application.
*   **`getToken` Async Function** Fetches a Tableau authentication token from the configured backend API endpoint and implements a client-side token caching mechanism with a 10-minute expiration.
*   **`loadTableaudash` Async Function** Orchestrates the embedding process by first acquiring a token and then constructing and injecting the `tableau-viz` custom element into the DOM.
*   **`TABLEAU_HOST`, `TABLEAU_CONTENT_URL`** Constants defining the Tableau Online instance and content URL.
*   **`IoArrowBackSharp`** An icon used for navigation back to the home page.

 Execution Flow / Behavior
1.  The `Dashboard` component mounts and retrieves `data` expected to be a Tableau dashboard path from `location.state`.
2.  The `useEffect` hook triggers on mount. It parses the received `data` URL and calls `loadTableau` with the modified path.
3.  The `loadTableau` function calls `getToken` to acquire an authentication token.
4.  `getToken` makes an `HTTP GET` request to the backend at `${API}/tableau/token` to obtain a fresh token if the local `token` variable is null. Upon successful retrieval, it stores the token and sets a 10-minute timeout to clear it, implementing a simple client-side cache.
5.  Once `loadTableau` receives a token, it constructs an HTML string for the `tableau-viz` custom element, including the dashboard source, the retrieved token, and presentation attributes.
6.  This HTML string is then directly inserted into the `div` element with `id=tableau` using `innerHTML`, which renders the Tableau dashboard.
7.  User interactions are handled
    *   Clicking the back arrow `IoArrowBackSharp` navigates the user to the `/home` route.
    *   Clicking Logout clears the `session` cookie and navigates the user to the root `/` route.

 Dependencies
*   **`react`** Core React library for UI development.
*   **`react-router-dom`** Provides routing hooks `useLocation`, `useNavigate`.
*   **`axios`** HTTP client for making API requests to the backend.
*   **`../App`** Imports the `API` constant, which presumably holds the base URL for backend services.
*   **`react-icons/io5`** Provides the `IoArrowBackSharp` icon used in the UI.
*   **Tableau `tableau-viz` Custom Element** This component is expected to be globally available in the browser environment, likely loaded via a script tag, as its used directly in `innerHTML` without a direct import.

 Design Notes
*   **Direct DOM Manipulation** The component directly manipulates the DOM using `document.getElementById.innerHTML` to embed the `tableau-viz` custom element. This bypasses Reacts virtual DOM and component lifecycle management for the embedded content.
*   **Client-Side Token Caching** The Tableau token is managed using a local variable and a `setTimeout` for expiration. This is a basic client-side cache, but its not integrated with Reacts state management and would reset if the component unmounts and remounts within the 10-minute window.
*   **Hardcoded Tableau Configuration** The `TABLEAU_HOST` and `TABLEAU_CONTENT_URL` constants are hardcoded within the file, making it less flexible for deployment to different Tableau environments without code changes.
*   **Fixed Dimensions** The `tableau-viz` element is rendered with fixed `height=90vh` and `width=3300px`, which might lead to unexpected layout or horizontal scrolling issues on various screen sizes.
*   **Logout Mechanism** The logout functionality directly manipulates `document.cookie` to clear the session. While functional, encapsulating this in a dedicated authentication context or utility could offer a more centralized and maintainable approach.

 Diagram
```mermaid
graph TD
A[Dashboard Component Mounts] -- B{Get Dashboard Data from Location State}
B -- C[Call loadTableau with Parsed Data]
C -- D[getToken Function]
D -- Fetches from -- E[Backend API /tableau/token]
E -- Returns token -- D
D -- F{Is Token Valid?}
F -- Yes -- G[Construct tableau-viz HTML String]
G -- H[Inject HTML into tableau Div]
H -- I[Tableau Dashboard Rendered]
I -- J[User Interaction]
J -- Click Back -- K[Navigate to /home]
J -- Click Logout -- L[Clear Session Cookie & Navigate to /]
```
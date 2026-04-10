# src/App.jsx

> **Source File:** [src/App.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/App.jsx)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/App.jsx

### Overview
This file defines the root React component for the application, `App.jsx`. It sets up client-side routing using `react-router-dom` to manage navigation between different pages, including a login page and protected routes for authenticated users.

### Architecture & Role
This file serves as the entry point for the client-side application's user interface. It resides in the presentation layer and acts as the top-level container that orchestrates global layout, routing, and initial state management related to user authentication.

### Key Components
*   **`App` function component**: The primary component that renders the `BrowserRouter` and main `Routes` for the application.
*   **`Main` function component**: A sub-component rendered for all paths other than the root (`/*`). It manages the `isUserLoggedIn` state and defines routes accessible post-authentication, such as `/home` and `/dashboard`.
*   **`API` constant**: An exported string defining the base URL for the backend API endpoint.
*   **`BrowserRouter`**: React Router component enabling URL-based navigation.
*   **`Routes`**: React Router component for defining a collection of route definitions.
*   **`Route`**: React Router component for mapping specific URL paths to corresponding React elements.
*   **`useState` hook**: Used within `Main` to manage the `isUserLoggedIn` state.
*   **`useNavigate` hook**: Used within `Main` for programmatic navigation.

### Execution Flow / Behavior
1.  The `App` component is the root of the React application.
2.  It initializes `BrowserRouter` to enable client-side routing.
3.  The main `Routes` block defines two top-level routes:
    *   `path="/" `: Renders the `Login` component, serving as the application's entry page.
    *   `path="/*"`: Renders the `Main` component for all other paths, acting as a catch-all for application content beyond login.
4.  Inside the `Main` component:
    *   It initializes `isUserLoggedIn` state to `true` (currently hardcoded).
    *   A nested `Routes` block conditionally renders based on `isUserLoggedIn`. If true, it defines routes for `/home` (rendering `Home`) and `/dashboard` (rendering `Dashboard`).
    *   Commented-out code suggests an `useEffect` hook that would `checkUser` for authentication status via `apiService` and redirect unauthenticated users to `/`.

### Dependencies
*   **`react-router-dom`**: Provides `BrowserRouter`, `Route`, `Routes`, and `useNavigate` for declarative routing.
*   **`react`**: Provides the `useState` hook for managing component state.
*   **`./App.css`**: Imports global application styles.
*   **`./Pages/Login`**: The component rendered for the root path.
*   **`./Pages/Home`**: A page component rendered on the `/home` path within `Main`.
*   **`./Pages/Dashboard`**: A page component rendered on the `/dashboard` path within `Main`.
*   **`./Components/Sidenav`**: A layout component, imported but not currently rendered in the visible `Routes` structure.
*   **`./Services/api_service`**: Commented out, indicating a planned or historical dependency for authentication checks.

### Design Notes
*   The current implementation hardcodes `isUserLoggedIn` to `true` within the `Main` component. The commented-out authentication logic suggests this is a placeholder and real authentication would involve `apiService.isLoggedIn()`.
*   The `Sidenav` component is imported but not utilized in the present `Routes` structure, implying it might be part of a broader layout component not shown or planned for future integration.
*   The `API` endpoint is a hardcoded constant, which typically would be managed via environment variables for different deployment environments.
*   The use of nested `Routes` (one in `App`, another in `Main`) effectively segregates public and authenticated routes.

### Diagram
```mermaid
graph TD
App[App] --> BrowserRouter[BrowserRouter]
BrowserRouter --> AppRoutes[Routes App]
AppRoutes --> RouteRoot[/ - Login]
AppRoutes --> RouteMain[/* - Main]
Main --> IsUserLoggedIn[isUserLoggedIn state]
IsUserLoggedIn --> |true| MainRoutes[Routes Main]
MainRoutes --> RouteHome[/home - Home]
MainRoutes --> RouteDashboard[/dashboard - Dashboard]
```
# src/App.jsx

> **Source File:** [src/App.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/App.jsx)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

 src/App.jsx

 Overview
This file serves as the root component of the React application, responsible for setting up the main client-side routing using `react-router-dom`. It defines the initial routes and the applications top-level structure.

 Architecture & Role
This file sits at the top level of the applications presentation layer. It acts as the primary application shell, defining the initial routing logic that directs users to different pages like Login, Home, and Dashboard. It integrates core navigation functionality and provides a global API endpoint configuration.

 Key Components
- `App` function The main React component that renders the applications routing structure.
- `Main` component A functional component nested within `App` that handles authenticated routes.
- `BrowserRouter` A router component from `react-router-dom` that uses the HTML5 history API for client-side routing.
- `Routes` A container component for defining individual `Route` components.
- `Route` Defines a specific path and the component to render for that path.
- `API` An exported constant string representing the base URL for the backend API.
- `useState` React hook used in `Main` for managing the `isUserLoggedIn` state.

 Execution Flow / Behavior
The `App` component is the entry point. It renders a `BrowserRouter` to enable client-side navigation. Inside, it defines two main routes
1. The root path `/` renders the `Login` page.
2. A catch-all path `/*` renders the `Main` component.

The `Main` component, when rendered, utilizes the `useNavigate` hook for programmatic navigation. It maintains an `isUserLoggedIn` state, which is currently hardcoded to `true`. If `isUserLoggedIn` is true, it renders a nested set of `Routes` for `/home` and `/dashboard`, displaying the `Home` and `Dashboard` components respectively. Commented-out code suggests an intention to implement an asynchronous user authentication check using `apiService` in the future.

 Dependencies
- `react-router-dom` Provides routing capabilities through `BrowserRouter`, `Route`, `Routes`, and `useNavigate`.
- `react` Provides core React functionality, specifically the `useState` hook.
- `./App.css` Stylesheet for the `App` component.
- `./Pages/Login` The component rendered for the root path.
- `./Pages/Home` A page component rendered within the authenticated routes.
- `./Pages/Dashboard` Another page component rendered within the authenticated routes.
- `./Components/Sidenav` Imported but not currently used in the rendered JSX.
- `./Services/api_service` Commented-out import, indicating a planned dependency for authentication logic.

 Design Notes
- The `isUserLoggedIn` state in the `Main` component is currently hardcoded to `true`. This bypasses actual authentication checks and allows access to authenticated routes `/home`, `/dashboard`. The commented-out code block suggests that a proper authentication flow involving an `apiService` was planned but not fully implemented.
- The `Sidenav` component is imported but not rendered, indicating it might be a component intended for future use or was part of a previous iteration of the UI.
- The `API` constant explicitly defines the backend endpoint. This centralizes the API base URL.
- The use of nested `Routes` within `Main` suggests a pattern for protecting routes that require user authentication, although the authentication logic itself is pending.

 Diagram
None significant.
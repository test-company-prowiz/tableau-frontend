# src/Components/Sidenav.jsx

> **Source File:** [src/Components/Sidenav.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Components/Sidenav.jsx)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Components/Sidenav.jsx

### Overview
This file defines the `Sidenav` React component, which renders the primary navigation sidebar for the application. It displays a list of main navigation links, such as "Workbooks" and "Views", allowing users to navigate between different sections of the application.

### Architecture & Role
The `Sidenav` component operates within the presentation layer of the frontend application. It acts as a static navigation UI element, responsible solely for rendering the sidebar and managing the visual state of its navigation links. It is a child component that likely integrates into a main layout component.

### Key Components
*   **`Sidenav` (Functional Component)**: The primary export of this file, responsible for rendering the entire sidebar navigation structure.
*   **`sideMenu` (State Variable)**: A local state variable initialized with an array of objects, each representing a main navigation item including its `path` and `name`. This acts as the data source for the rendered navigation links.
*   **`NavLink`**: A component from `react-router-dom` used to create navigation links that automatically apply an `active` class when the current URL matches the link's `to` prop.

### Execution Flow / Behavior
The `Sidenav` component renders a fixed-width, full-height sidebar. Upon rendering:
1.  It initializes a `sideMenu` state array with predefined navigation items ("Workbooks", "Views").
2.  It displays a static title "Qadence by TQG".
3.  It iterates through the `sideMenu` array, rendering a `NavLink` for each item.
4.  Each `NavLink` is configured to navigate to its respective `path`.
5.  Custom CSS classes are applied to `NavLink` elements based on the current URL's `location.pathname` using regex, specifically handling active states for `/event-logs` and `/camera-view` routes, overriding default `NavLink` active behavior.
6.  The component includes commented-out logic for submenus, which currently renders a `div` element rather than a navigable link.

### Dependencies
*   **`react`**: Implicitly used for JSX syntax and the `useState` hook. The `useEffect` hook is imported but commented out and not utilized.
*   **`react-router-dom`**: Used for `NavLink` components to handle client-side routing and the `useLocation` hook to access the current URL path for dynamic class assignment.

### Design Notes
*   The navigation structure is currently hardcoded within the `sideMenu` state variable, making it static. Dynamic menu configuration would require external data fetching or prop-based configuration.
*   The `activeclassName` prop for `NavLink` is deprecated in `react-router-dom` v6, suggesting an older version or a need for update. The custom regex-based class assignment for active links might conflict with or override default `NavLink` active styling.
*   Submenu functionality is incomplete; `NavLink` components for sub-items are commented out and replaced with non-navigable `div` elements, indicating this feature is either under development or intentionally static.
*   The `useEffect` hook import is commented out, implying no side effects (like data fetching or subscriptions) are currently managed by this component.

### Diagram
None significant.
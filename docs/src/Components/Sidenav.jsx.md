# src/Components/Sidenav.jsx

> **Source File:** [src/Components/Sidenav.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Components/Sidenav.jsx)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Components/Sidenav.jsx

### Overview
This file defines the `Sidenav` React component, which renders the primary navigation sidebar for the application. It provides links to main sections like "Workbooks" and "Views," forming a persistent navigation element within the user interface.

### Architecture & Role
This component operates within the frontend presentation layer. It functions as a foundational UI element responsible for application-level navigation, typically positioned on the left side of the screen as part of the main layout.

### Key Components
*   **`Sidenav` functional component**: The main React component responsible for rendering the sidebar and its navigation items.
*   **`sideMenu` state**: An array managing the predefined list of navigation objects, each containing a `path` and `name`.
*   **`NavLink`**: A component from `react-router-dom` (though its import is commented out) intended for declarative navigation.
*   **`useLocation`**: A hook from `react-router-dom` (though its import is commented out) used to access the current URL path for conditional styling.

### Execution Flow / Behavior
The `Sidenav` component renders a fixed-width vertical sidebar.
1.  It initializes its `sideMenu` state with two navigation entries: "Workbooks" (`/home`) and "Views" (`/camera-view`).
2.  It displays a brand title "Qadence by TQG".
3.  It maps over the `sideMenu` array to render a `NavLink` for each item.
4.  Each `NavLink` is styled with a base set of utility classes.
5.  Custom active link styling is applied:
    *   The `activeClassName="not-active"` prop is used, which, if `NavLink` were active, would apply a class indicating an inactive state.
    *   An additional `className` conditional logic uses `useLocation().pathname` to apply the `'not-active'` class if the current path matches `/event-logs/` or `/camera-view/` routes, potentially overriding or inverting the intended active styling for these specific paths.
6.  A commented-out block for rendering submenus indicates potential future functionality for nested navigation.

### Dependencies
*   **`react`**: Used for component creation and the `useState` hook. (Import is commented out in the provided code).
*   **`react-router-dom`**: Provides `NavLink` for client-side routing and `useLocation` for route-aware component logic. (Imports are commented out in the provided code).

### Design Notes
*   **Commented Imports**: Crucially, the `import` statements for `React`, `useEffect`, `useState`, `NavLink`, and `useLocation` are all commented out. The component, as provided, would not compile or function correctly without these necessary imports being uncommented.
*   **Hardcoded Navigation**: The navigation menu items are hardcoded directly within the component's state. For larger applications, it might be more maintainable to manage these items centrally, perhaps from a configuration file or API.
*   **Custom Active Link Logic**: The combination of `activeClassName="not-active"` and conditional `className` logic that applies `'not-active'` via regex for specific paths suggests a highly customized and potentially inverted approach to active link styling, which deviates from standard `NavLink` behavior. This implementation may lead to active links visually appearing inactive under certain conditions.
*   **Styling**: Styling is primarily managed using inline utility classes, likely from a framework like Tailwind CSS.
*   **Unused `useEffect`**: The `useEffect` import is present in the commented section but is not utilized within the component's logic.
*   **Submenu Placeholder**: The presence of a commented-out section for rendering submenus implies a planned feature for hierarchical navigation that is not yet implemented.

### Diagram
None significant.
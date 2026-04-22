# src/Components/Sidenav.jsx

> **Source File:** [src/Components/Sidenav.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Components/Sidenav.jsx)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Components/Sidenav.jsx

### Overview
This file defines a React component named `Sidenav`. Its purpose is to render a fixed-width sidebar navigation menu for the application, providing links to key sections such as "Workbooks" and "Views".

### Architecture & Role
This file resides in the UI/Presentation Layer of the application architecture. It functions as a foundational layout component, intended to provide global and persistent navigation across the application's various routes.

### Key Components
- **`Sidenav` functional component**: This is the primary export.
    - It accepts `children` as a prop, though it is not currently utilized within the component's rendering logic.
    - It manages the navigation menu structure using a `useState` hook for `sideMenu`.
    - It uses `useLocation` from `react-router-dom` to access the current URL path, enabling dynamic styling for active navigation links.
    - It renders a static header "Qadence by TQG".
    - It maps through the `sideMenu` array to render `NavLink` components, which facilitate client-side routing.
    - Conditional `className` logic is applied to `NavLink` elements based on regex matching of `location.pathname` for specific routes (`/event-logs/` and `/camera-view/`), assigning a `not-active` class.
    - It includes partially implemented rendering for submenus, which are currently displayed as static `div` elements rather than interactive `NavLink` components.

### Execution Flow / Behavior
When the `Sidenav` component is rendered, it initializes its `sideMenu` state with predefined navigation entries. It then iterates over this state to render `NavLink` components. The `useLocation` hook ensures that as the user navigates, the component re-renders, allowing the `className` logic to dynamically apply styling to the navigation items based on the current route. The regex patterns ensure specific parent routes maintain a `not-active` visual state for their main menu item when child routes are active. Submenu items are rendered as static elements and do not currently trigger navigation.

### Dependencies
- **`react`**: Provides core React functionality including `useState` for managing component state and functional component definition.
- **`react-router-dom`**:
    - `NavLink`: Used for declarative navigation links that automatically apply an `activeclassName` based on the current route.
    - `useLocation`: Provides access to the current URL, enabling conditional rendering and styling logic based on the application's navigation state.

### Design Notes
The entire file content is currently commented out, indicating that this component is not actively being compiled or used in the application's current state. The `children` prop is defined but not utilized within the component's JSX, suggesting potential future expansion or a remnant from a prior design. The navigation link active state logic uses both `activeclassName` and a custom `className` with regex conditions; this dual approach may lead to styling conflicts or unexpected behavior depending on CSS specificity rules. The submenu functionality is incomplete, with `NavLink` elements commented out in favor of non-interactive `div`s. The `sideMenu` configuration also includes commented-out `icon` properties.

### Diagram
None significant.
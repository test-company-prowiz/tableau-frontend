# src/Components/Sidenav.jsx

> **Source File:** [src/Components/Sidenav.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Components/Sidenav.jsx)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Components/Sidenav.jsx

### Overview
This file defines the `Sidenav` functional component, intended to render a persistent navigation sidebar for the application. In its current state, the entire file content is commented out, rendering it inactive.

### Architecture & Role
If active, this file would reside in the UI/presentation layer, specifically as a shared layout component. It would function as a top-level navigation element, distinct from the main content area, providing global application navigation.

### Key Components
- **`Sidenav` functional component:** The primary export, responsible for rendering the sidebar structure and navigation links.
- **`sideMenu` state:** An internal state variable that holds an array of navigation objects, each defining a `path` and `name` for a menu item.

### Execution Flow / Behavior
If uncommented and rendered:
1. The `Sidenav` component would initialize with a `sideMenu` state containing predefined navigation paths for "Workbooks" and "Views".
2. It would render a fixed-width (`17vw`) and full-height (`100vh`) `div` element, styled as a sidebar.
3. It would display a static title "Qadence by TQG".
4. It would iterate through the `sideMenu` array, rendering `NavLink` components for each item.
5. The `NavLink` components would conditionally apply a `not-active` CSS class if the current URL matches specific patterns (`/event-logs/` or `/camera-view/`).
6. The commented-out `submenu` logic suggests an intention for nested navigation, currently rendering plain `div` elements for sub-items.

### Dependencies
- **`react`:** For defining the functional component and managing state (`useState`). (Currently commented out).
- **`react-router-dom`:** Specifically `NavLink` for declarative navigation and `useLocation` for accessing the current URL to apply conditional styling. (Currently commented out).

### Design Notes
- The entire file is currently commented out, indicating it is either under development, deprecated, or temporarily disabled.
- The component uses inline Tailwind CSS classes for styling, defining layout, colors, and typography directly within the JSX.
- The conditional `className` logic for `NavLink` uses regular expressions to determine if a parent link should be styled as `not-active` when a child route is active. This logic could be centralized or abstracted for maintainability.
- The `submenu` rendering is present but commented out, and the rendering logic for sub-items uses a `div` instead of `NavLink`, suggesting an incomplete feature or a temporary placeholder.

### Diagram
None significant.
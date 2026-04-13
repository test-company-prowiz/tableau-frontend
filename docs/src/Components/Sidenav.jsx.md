# src/Components/Sidenav.jsx

> **Source File:** [src/Components/Sidenav.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Components/Sidenav.jsx)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Components/Sidenav.jsx

### Overview
This file contains a commented-out React component designed to render a fixed-width sidebar navigation for a web application. Its purpose is to display a list of navigation links, manage their active states based on the current URL, and provide a consistent navigation experience.

### Architecture & Role
This component functions as a presentational UI element within the client-side application. It is intended to reside in the presentation layer, typically integrated into a main layout or dashboard component to provide global navigation. Its architecture is self-contained as a functional React component.

### Key Components
*   `Sidenav` (functional component): The primary export, responsible for rendering the entire sidebar structure and its navigation items.
*   `sideMenu` (state): A React state variable initialized with an array of objects. Each object represents a navigation link, defining its `path` and `name`.
*   `NavLink`: A component from `react-router-dom` used to create declarative navigation links that automatically apply an active class when the target route matches the current URL.
*   `useLocation`: A hook from `react-router-dom` used to access the current URL's location object, enabling conditional rendering or styling based on the active route.

### Execution Flow / Behavior
1.  When the `Sidenav` component is rendered (if uncommented), it initializes its internal `sideMenu` state with a predefined set of navigation items.
2.  It then uses the `useLocation` hook to obtain the current browser URL path.
3.  The component iterates through the `sideMenu` array. For each item, it renders a `NavLink` component.
4.  Each `NavLink` is configured with a `to` prop corresponding to the item's `path` and displays the item's `name`. It also includes a placeholder for `item.icon`, although the initial `sideMenu` state does not define icons.
5.  Styling for active/inactive links is managed through dynamic `className` logic:
    *   It applies a `not-active` class if the current `location.pathname` matches specific regex patterns (`/event-logs/` or `/camera-view/`).
    *   It explicitly sets `activeclassName="not-active"`, which would apply this class when the link's `to` prop matches the current route.
6.  The component includes commented-out logic for rendering nested `submenu` items, though the initial `sideMenu` state does not contain submenu data.

### Dependencies
*   `react`: Provides core React functionality, including component definition (`function Sidenav`) and state management (`useState`).
*   `react-router-dom`: Essential for client-side routing, specifically `NavLink` for navigation links and `useLocation` for accessing route information.

### Design Notes
*   The entire file is currently commented out, indicating that this sidebar component is not actively in use within the application's current build. It represents either a historical implementation, a work-in-progress, or a placeholder for future functionality.
*   The navigation menu items are initially hardcoded within the `sideMenu` state. While `useState` allows for dynamic updates, the current structure suggests a static sidebar configuration.
*   The `NavLink` `className` logic, particularly the use of `activeclassName="not-active"` in conjunction with conditional `not-active` classes based on other route patterns, suggests a potentially inverted or custom approach to styling active links that might require clarification or refactoring if this component were to be reactivated.
*   The presence of submenu rendering logic, despite `sideMenu` not containing `submenu` data, implies an intention to support multi-level navigation which was not fully realized or integrated.

### Diagram
None significant.
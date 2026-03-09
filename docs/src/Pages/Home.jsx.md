# src/Pages/Home.jsx

> **Source File:** [src/Pages/Home.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Pages/Home.jsx)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

# src/Pages/Home.jsx

### Overview
This file implements the `Home` page of the application, serving as the main entry point for users to browse and interact with Tableau workbooks and views. It fetches data from a backend API, displays workbooks in a carousel, allows searching and filtering of views, and provides navigation to individual view dashboards.

### Architecture & Role
This file represents a presentation layer component within the application's frontend architecture. It is a React functional component responsible for rendering the user interface, managing local state, and coordinating data fetching from the backend API. It interacts with the `react-router-dom` for navigation and leverages `axios` for network requests.

### Key Components
*   **`Home` Function Component**: The primary React functional component for the Home page, managing state, data fetching, and rendering.
*   **`SamplePrevArrow` / `SampleNextArrow`**: Custom functional components used by `react-slick` to render navigation arrows for the workbook slider, styled with `react-icons`.
*   **`useState` Hooks**: Manage component state including:
    *   `inputSearch`: Stores the current value of the view search input.
    *   `loading`: Boolean indicating if initial workbook and view data is being fetched.
    *   `viewsLoading`: Boolean indicating if views are currently being fetched (e.g., after clicking a workbook or "All Views").
    *   `views`: Stores the array of all available views.
    *   `filteredViews`: Stores the array of views after applying search filters.
    *   `workbooks`: Stores the array of available workbooks.
*   **`useRef` (`slideRef`)**: Used to gain direct access to the `react-slick` Slider component instance.
*   **`useEffect` Hook**: Triggers the `fetchAllData` function once when the component mounts to load initial workbooks and views.
*   **`sliderSettings`**: Configuration object for the `react-slick` `Slider` component, defining display properties and custom arrow components.
*   **`fetchViews(id)`**: Asynchronous function to fetch views associated with a specific workbook ID from the backend.
*   **`onSearch(e)`**: Handles changes in the search input field, filtering the `views` based on `contentUrl` and updating `filteredViews`.
*   **`fetchAllViews()`**: Asynchronous function to re-fetch all available views from the backend.
*   **`fetchAllData()`**: Asynchronous function called on component mount to fetch both all workbooks and all views concurrently.

### Execution Flow / Behavior
1.  **Initialization**: When the `Home` component mounts, the `useEffect` hook triggers `fetchAllData()`.
2.  **Initial Data Fetch**: `fetchAllData()` makes two concurrent `axios` requests to the backend: one for all workbooks (`/tableau/workbooks`) and another for all views (`/tableau/views`). Loading states (`loading`) are managed during this process.
3.  **Display Workbooks**: Once workbooks are fetched, they are rendered in a `react-slick` carousel (`Slider`). Each workbook item is clickable.
4.  **Display Views**: All initially fetched views are displayed as a list below the workbooks.
5.  **Workbook Interaction**: Clicking on a workbook item triggers `fetchViews(id)`, which fetches views specific to that workbook from the backend. The views list is then updated.
6.  **View Search**: Users can type into a search input. The `onSearch` function filters the currently loaded `views` array (based on `contentUrl`) and updates the `filteredViews` state, which is then rendered.
7.  **"All Views" Button**: Clicking this button triggers `fetchAllViews()`, which re-fetches all views from the backend, effectively clearing any current filtering applied by workbook selection or search.
8.  **View Navigation**: Clicking on a specific view item navigates the user to the `/dashboard` route, passing the view's `contentUrl` as state.
9.  **Logout**: The "Logout" button clears the `session` cookie and navigates the user to the root path (`/`).
10. **Loading Indicators**: `Skeleton` components from Ant Design are displayed while initial workbook and view data is loading. A `Spin` component is displayed for `viewsLoading` when views are being fetched specifically.

### Dependencies
*   **`react`**: Core library for building UI components.
*   **`react-slick`, `slick-carousel`**: Provides carousel functionality for displaying workbooks.
*   **`react-icons/ai`**: Provides arrow icons for the carousel navigation.
*   **`react-icons/fa`**: Provides the search icon for the input field.
*   **`@ant-design/icons`**: Provides `LoadingOutlined` for the spin indicator.
*   **`axios`**: HTTP client for making API requests to the backend (`/tableau/views` and `/tableau/workbooks`). Requests are made with `withCredentials: true` for session handling.
*   **`react-router-dom`**: Provides `useNavigate` for programmatic navigation and `Link` (though `Link` is not directly used for navigation in this file, `navigate` is).
*   **`antd`**: Ant Design UI library for components like `Input` (including `Search`), `Skeleton`, `Space`, and `Spin`.
*   **`../App`**: Imports the `API` constant, which likely defines the base URL for backend API calls.
*   **`../Mock/workbooks`, `../Mock/view`**: These mock data imports are present but not utilized in the current runtime logic, which instead relies on `axios` for fetching actual data.

### Design Notes
*   The component uses a combination of client-side filtering (`onSearch`) and server-side fetching (`fetchViews`, `fetchAllViews`) for managing the list of views, depending on the user action.
*   Loading states are handled with dedicated boolean flags (`loading`, `viewsLoading`) and corresponding UI feedback using Ant Design components (`Skeleton`, `Spin`).
*   The application uses cookies for session management, explicitly clearing the `session` cookie on logout.
*   The `API` constant is imported from `../App`, centralizing the backend endpoint configuration.
*   The unused `allWorkBooks` and `allViews` imports from `../Mock` suggest a potential earlier design choice or placeholder that is no longer active. These could be removed to clean up the code.

### Diagram 

```mermaid
graph TD
A[Home Component Load] -- B[Initial Data Fetch]
B -- C[Workbooks Display]
B -- D[Views Display]
C -- E{User Clicks Workbook}
E -- F[Fetch Specific Views]
F -- D
D -- G{User Searches Views}
G -- H[Filter Views]
H -- D
D -- I{User Clicks View}
I -- J[Navigate To Dashboard]
```
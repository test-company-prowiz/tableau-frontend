# src/Pages/Home.jsx

> **Source File:** [src/Pages/Home.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Pages/Home.jsx)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

 src/Pages/Home.jsx

 Overview
This file implements the `Home` page component, serving as the primary landing page for the application. It displays a list of Tableau workbooks in a carousel and a list of Tableau views, allowing users to browse, search, and navigate to specific dashboards.

 Architecture & Role
This file represents a top-level page component within the frontend architecture. It is responsible for orchestrating data fetching from a backend API presumably a Tableau proxy and rendering the main user interface for discovering and accessing Tableau assets. It sits at the presentation layer, handling UI logic, state management, and interaction with the applications routing system.

 Key Components
*   **`Home` Function Component** The main React functional component that manages the pages state, data fetching, and rendering.
*   **`SamplePrevArrow` / `SampleNextArrow`** Custom components for navigating the `react-slick` carousel, providing visual arrow buttons.
*   **`useState` Hooks** Used to manage various UI and data states, including `inputSearch`, `loading` for initial data, `viewsLoading` for view-specific loading, `views`, `filteredViews`, and `workbooks`.
*   **`useEffect` Hook** Triggers the initial `fetchAllData` call when the component mounts to populate workbooks and views.
*   **`sliderSettings` Object** Configures the behavior and appearance of the `react-slick` carousel for workbooks.
*   **`fetchViewsid`** An asynchronous function to fetch views associated with a specific workbook ID.
*   **`onSearche`** Filters the currently displayed views based on user input in the search bar.
*   **`fetchAllViews`** An asynchronous function to fetch all available views, typically used when the All Views button is clicked.
*   **`fetchAllData`** An asynchronous function called on component mount to fetch both all workbooks and all views initially.
*   **`Slider` from `react-slick`** Renders the interactive carousel for workbooks.
*   **`Input`, `Skeleton`, `Spin` from `antd`** UI components used for search input, loading placeholders, and loading indicators, respectively.
*   **`useNavigate` from `react-router-dom`** Provides programmatic navigation within the application, used to go to the dashboard or log out.

 Execution Flow / Behavior
1.  **Initial Load** When the `Home` component mounts, `useEffect` triggers `fetchAllData`.
2.  **Data Fetching** `fetchAllData` asynchronously fetches all Tableau workbooks and all Tableau views from the configured backend API `API/tableau/workbooks` and `API/tableau/views`. During this fetch, a global `loading` state is true, displaying `Skeleton` loaders.
3.  **Display Workbooks** Once workbooks are fetched, they are rendered within a `Slider` carousel. Each workbook item displays its name.
4.  **Display Views** Once all views are fetched, they are displayed as a list below the workbooks. Initially, `filteredViews` is empty, so `views` are rendered.
5.  **Workbook Interaction** Clicking a workbook in the carousel calls `fetchViewsid` for that workbook. This fetches views specific to that workbook, updates the `views` state, and re-renders the views list. A `viewsLoading` state provides a `Spin` indicator during this process.
6.  **Search Functionality** Typing into the search input triggers `onSearch`, which filters the current `views` list based on the input value case-insensitive `contentUrl` matching. The `filteredViews` state is updated, and the views list re-renders to show only matching views.
7.  **All Views Button** Clicking this button calls `fetchAllViews`, which re-fetches all views, effectively resetting any workbook-specific or search-filtered view list to the comprehensive list.
8.  **View Navigation** Clicking on a view item navigates the user to the `/dashboard` route, passing the views `contentUrl` as state data.
9.  **Logout** Clicking the Logout link clears the `session` cookie by setting its expiration to the past and then navigates the user to the root path `/`.

 Dependencies
*   **`react`** Core library for building UI components.
*   **`react-slick`** Carousel component for displaying workbooks `Slider`.
    *   `slick-carousel/slick/slick.css`, `slick-carousel/slick/slick-theme.css` Styling for `react-slick`.
*   **`react-icons/ai`** Icon library for arrow navigation `AiOutlineArrowLeft`, `AiOutlineArrowRight`.
*   **`react-icons/fa`** Icon library for search input `FaSearch`.
*   **`@ant-design/icons`** Icon library for loading indicators `LoadingOutlined`.
*   **`axios`** HTTP client for making API requests to the backend.
*   **`react-router-dom`** For routing and navigation `Link`, `useNavigate`.
*   **`antd` Ant Design** UI component library providing `Input` including `Search`, `Skeleton`, `Space`, and `Spin` for enhanced UI elements and loading states.
*   **`../App`** Imports the `API` constant, likely the base URL for backend API requests.
*   **`../Mock/workbooks`** Mock data for workbooks. Appears to be unused in the final code, as actual data is fetched via `axios`.
*   **`../Mock/view`** Mock data for views. Appears to be unused in the final code, as actual data is fetched via `axios`.

 Design Notes
*   The component relies heavily on `useState` for managing UI and data states, leading to a reactive UI based on API responses and user interactions.
*   Data fetching is performed directly within the component using `axios`, which is common for smaller applications but could benefit from centralization in a larger application e.g., using a custom hook or a data fetching library.
*   Loading states are handled granularly for initial data `loading` and specific view fetches `viewsLoading`, improving user experience with visual feedback via `Skeleton` and `Spin` components.
*   The logout mechanism directly manipulates `document.cookie`, which is a straightforward way to clear a session cookie.
*   The `Mock` data imports are present but not utilized in the `fetchAllData` function, indicating they might have been used during development or for testing without a live API.

 Diagram
None significant.
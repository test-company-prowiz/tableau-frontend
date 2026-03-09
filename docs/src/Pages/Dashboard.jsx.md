# src/Pages/Dashboard.jsx

> **Source File:** [src/Pages/Dashboard.jsx](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Pages/Dashboard.jsx)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

 src/Pages/Dashboard.jsx

 Overview
This file defines the `Dashboard` React functional component. Its primary purpose is to display an embedded Tableau dashboard by dynamically creating and inserting a `tableau-viz` web component. It manages the retrieval of a Tableau authentication token from a backend API to enable secure access to the dashboard.

 Architecture & Role
This file functions as a presentation layer component within the frontend application, specifically a page component. It is responsible for rendering the Tableau visualization and managing the user interface elements related to it, such as navigation and logout. It interacts with the applications backend to procure necessary authentication data for the Tableau embedded component.

 Key Components
- **`Dashboard` function component** The main React component that orchestrates the display of the Tableau dashboard and includes navigation controls.
- **`useEffect` hook** Initiates the loading of the Tableau dashboard when the component first mounts. It extracts and processes the target dashboard URL from the `location.state`.
- **`getToken` async function** Responsible for making an authenticated HTTP GET request to the backend at `${API}/tableau/token` to retrieve a Tableau authentication token. It implements a basic client-side caching mechanism, storing the token for 10 minutes.
- **`loadTableau` async function** Constructs the HTML string for the `tableau-viz` web component, incorporating the Tableau host, content URL, dashboard path, and the acquired authentication token. This HTML is then injected into a designated `div` element in the DOM.
- **`TABLEAU_HOST`** A constant specifying the base URL for the Tableau Online instance.
- **`TABLEAU_CONTENT_URL`** A constant identifying the Tableau site content URL within the host.
- **`IoArrowBackSharp`** An icon from `react-icons` used for the back navigation functionality.

 Execution Flow / Behavior
1. Upon the `Dashboard` components initial render, the `useEffect` hook executes.
2. Inside `useEffect`, the dashboard path is extracted from the `location.state.data` prop and pre-processed by removing a specific segment from its URL.
3. The `loadTableau` function is then invoked with the processed dashboard path.
4. `loadTableau` first calls `getToken` to obtain an authentication token.
5. `getToken` performs an asynchronous API call to the backend. If successful, it stores the token and sets a timeout to clear it after 10 minutes 600,000 milliseconds.
6. Once `getToken` returns a valid token, `loadTableau` dynamically generates the HTML markup for a `tableau-viz` web component, embedding the token, host, content URL, and dashboard path.
7. This generated HTML is subsequently injected into the `div` element with the ID `tableau`, causing the Tableau dashboard to render within the page.
8. The component also renders a header containing a back button navigating to `/home` and a logout button that clears the `session` cookie and redirects to the root path `/`.

 Dependencies
- **`react`** For core React functionalities, including `useEffect`.
- **`react-router-dom`** Provides `useLocation` to access route state and `useNavigate` for programmatic routing.
- **`../App`** Imports the `API` constant, which serves as the base URL for backend API requests.
- **`axios`** An HTTP client used to make asynchronous requests to the backend for the Tableau token.
- **`react-icons/io5`** Imports specific icons, such as `IoArrowBackSharp`, for UI elements.
- **Tableau JavaScript API implicit** The `tableau-viz` web component implicitly relies on the Tableau embedding library to function correctly.

 Design Notes
- The component employs a client-side caching strategy for the Tableau authentication token, valid for 10 minutes, to reduce frequent backend requests.
- Tableau dashboard embedding is achieved by injecting raw HTML containing the `tableau-viz` custom element directly into the DOM, which is a common pattern for integrating web components.
- The logic for parsing `data` from `location.state` explicitly filters out the second segment of the URL, suggesting a specific, expected URL structure passed via route state.
- The `tableau-viz` component is given a fixed `width=3300px`, which may lead to horizontal scrollbars or layout issues on displays smaller than this width. This might be a candidate for responsive design improvements.
- Logout functionality directly manipulates `document.cookie` to expire the `session` cookie.

 Diagram Optional
None significant.
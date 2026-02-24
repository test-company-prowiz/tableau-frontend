# src/Mock/view.js

> **Source File:** [src/Mock/view.js](https://github.com/tableau-frontend/blob/main/src/Mock/view.js)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

### Overview
This file defines and exports `allViews`, a constant object that serves as mock data for a collection of view entities. It provides a static dataset structured to resemble an API response, containing detailed information for several distinct views.

### Architecture & Role
This file functions as a data mock within the application's development or testing environment. It resides at the data layer, specifically providing static, in-memory data that simulates what would typically be fetched from a backend service or database for "view" resources. Its role is to enable other application components to develop and test functionality that consumes view data without requiring a live backend connection.

### Key Components
*   `allViews`: A constant object exported by the file. It contains a top-level `data` property, which encapsulates a `views` array.
*   `views` array: An array of objects, where each object represents a single view. Each view object includes properties such as:
    *   `id`: Unique identifier for the view.
    *   `name`: Display name of the view.
    *   `contentUrl`: A path or URL fragment pointing to the view's content.
    *   `viewUrlName`: A URL-friendly name for the view.
    *   `owner`: An object containing the owner's ID.
    *   `project`: An object containing the project's ID.
    *   `location`: An object specifying the location's ID and type.
    *   `tags`: An empty object, likely a placeholder for future tag data.
    *   `createdAt`, `updatedAt`: Timestamps indicating creation and last update.

### Execution Flow / Behavior
The file's primary behavior is to make the `allViews` constant available for import. There is no executable logic or runtime processing defined within this file. When imported, other modules gain immediate access to the entire static `allViews` dataset.

### Dependencies
None significant. This file is self-contained and does not import any external modules or internal files.

### Design Notes
*   **Purpose of Mock Data**: The explicit purpose of this file is to provide a consistent and readily available dataset for views, which is crucial for unit testing, integration testing, and local development where a full backend setup might be impractical or slow.
*   **API Response Mimicry**: The structure with a top-level `data` key containing the `views` array is a common pattern for API responses, indicating this mock is designed to closely simulate a service endpoint.
*   **Static Nature**: Being a static constant, `allViews` offers predictable behavior but lacks dynamic capabilities such as filtering, sorting, or pagination that a real API would provide. Any changes to the mock data require manual modification of the file.

### Diagram (Optional)
None significant.
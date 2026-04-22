# src/Mock/view.js

> **Source File:** [src/Mock/view.js](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Mock/view.js)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Mock/view.js

### Overview
This file exports a constant `allViews` which contains mock data representing a collection of dashboard views. Its primary purpose is to provide static data for development, testing, or demonstration environments, simulating a backend API response for view listings.

### Architecture & Role
Architecturally, this file acts as a mock data provider within the application. It resides in the `Mock` directory, indicating its role in supplying dummy data when actual backend services are unavailable or being bypassed. It belongs to the data layer, specifically for client-side mocking.

### Key Components
-   **`allViews`**: A JavaScript object constant that exports an array of view objects. Each view object includes properties such as `owner`, `project`, `tags`, `location`, `id`, `name`, `contentUrl`, `createdAt`, `updatedAt`, and `viewUrlName`.

### Execution Flow / Behavior
When imported by another module, the `allViews` constant becomes available as a static data structure. There is no dynamic behavior, function execution, or external calls associated with this file; it merely provides pre-defined data.

### Dependencies
None significant. This file does not import any other modules or external libraries.

### Design Notes
This file embodies a common practice for frontend development to decouple from backend dependencies during early development or for unit testing. By providing structured mock data, developers can build and test UI components that rely on view data without needing a live API endpoint. The main trade-off is that this data is static and does not reflect real-time changes or complex server-side logic.

### Diagram
None significant.
# src/Mock/view.js

> **Source File:** [src/Mock/view.js](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Mock/view.js)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Mock/view.js

### Overview
This file exports a static JavaScript object, `allViews`, which serves as a mock dataset for various "view" entities. Its primary purpose is to provide sample data for development, testing, or showcasing UI components without requiring a live backend connection.

### Architecture & Role
Architecturally, this file belongs to the mocking layer of the application. It acts as a local data source, providing predefined data structures to frontend components that would otherwise fetch similar data from a real API endpoint. This isolates frontend development from backend dependencies and facilitates unit and integration testing.

### Key Components
*   `allViews`: A constant object containing a `data` field, which in turn holds an array named `views`. Each object within the `views` array represents a single view entity with the following structure:
    *   `owner`: An object containing an `id`.
    *   `project`: An object containing an `id`.
    *   `tags`: An empty object.
    *   `location`: An object with `id` and `type` fields.
    *   `id`: A unique identifier for the view.
    *   `name`: The display name of the view.
    *   `contentUrl`: A relative URL path to the view's content.
    *   `createdAt`: Timestamp of creation.
    *   `updatedAt`: Timestamp of last update.
    *   `viewUrlName`: A URL-friendly name for the view.

### Execution Flow / Behavior
This file does not contain executable logic. It solely defines and exports a static data structure. When imported by other modules, the `allViews` object is directly accessible, allowing consuming components to use this predefined data as if it were retrieved from a backend service.

### Dependencies
None significant.

### Design Notes
This file exemplifies the use of mock data for development and testing. It allows frontend features dependent on "view" data to be built and validated independently. A potential improvement area could involve generating this mock data more dynamically or from a schema to ensure it remains aligned with actual API responses as the system evolves.

### Diagram
None significant.
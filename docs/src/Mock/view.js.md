# src/Mock/view.js

> **Source File:** [src/Mock/view.js](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Mock/view.js)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Mock/view.js

### Overview
This file exports a constant `allViews` that provides a collection of mock data representing various dashboard or report views. It serves as a static data source for simulating view-related API responses.

### Architecture & Role
This file resides within the `Mock` directory, indicating its role as a mock data provider. Architecturally, it functions as a simulated data layer, typically used during development or testing to decouple front-end components from live API endpoints, allowing for independent feature development and unit testing.

### Key Components
-   **`allViews`**: A top-level constant export. It contains an object with a `data` property, which holds an array named `views`.
    -   Each object within the `views` array represents a single view and includes properties such as:
        -   `owner`: An object with an `id`.
        -   `project`: An object with an `id`.
        -   `tags`: An empty object.
        -   `location`: An object with `id` and `type` (e.g., "Project").
        -   `id`: A unique identifier for the view.
        -   `name`: The display name of the view.
        -   `contentUrl`: A path to the content, often indicating a specific sheet or report.
        -   `createdAt`: Timestamp of creation.
        -   `updatedAt`: Timestamp of last update.
        -   `viewUrlName`: A URL-friendly name for the view.

### Execution Flow / Behavior
The file itself does not contain any executable logic or functions. Its behavior is limited to exporting a predefined, static JavaScript object. When imported by other modules, the `allViews` constant is directly accessible, providing its data without requiring any runtime computation or external calls.

### Dependencies
This file has no explicit internal or external code dependencies (imports/exports) beyond its own definition. Its data structure, however, implies an implicit dependency on a schema or data model for "view" objects used elsewhere in the application.

### Design Notes
The purpose of this file is to supply representative mock data, which is crucial for front-end development when the backend API might be unavailable or still under construction. Using static mock data avoids network requests, making development faster and tests more reliable. The structure mirrors a typical API response for a list of views, ensuring consistency with expected production data shapes.

### Diagram
None significant.
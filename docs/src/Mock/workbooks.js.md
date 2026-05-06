# src/Mock/workbooks.js

> **Source File:** [src/Mock/workbooks.js](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/Mock/workbooks.js)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/Mock/workbooks.js

### Overview
This file exports a static JavaScript object, `allWorkBooks`, which contains a predefined dataset representing a collection of workbooks. It functions as a mock data source for development and testing purposes, simulating a response that would typically be retrieved from a backend API.

### Architecture & Role
This file resides within the `Mock` directory, indicating its role as part of the mocking layer within the application's architecture. It provides predefined data structures to frontend components or services during development, allowing them to function without requiring a live backend connection. This decouples frontend development from backend availability.

### Key Components
*   `allWorkBooks`: A constant object export that contains an array of workbook records under `data.workbooks`. Each workbook object includes details such as `project`, `location`, `owner`, `id`, `name`, `contentUrl`, `webpageUrl`, and various timestamps and configuration flags.

### Execution Flow / Behavior
This file does not contain executable logic beyond its declaration. At runtime, it simply provides the `allWorkBooks` object when imported by other modules. There is no dynamic data processing, API calls, or state management within this file; it serves as a pure data provider.

### Dependencies
This file has no internal or external code dependencies. It is a self-contained data export. Its structure, however, implies an implicit dependency on the data schema expected by the application, likely mirroring a real API response for workbooks.

### Design Notes
The use of a mock data file like this facilitates isolated development and testing of UI components and business logic that consume workbook data. It allows developers to work without setting up a full backend environment or dealing with network latency. A trade-off is that this data is static and does not reflect real-time changes or complex data interactions. For production, this mock would be replaced by actual API integrations.

### Diagram
None significant.
# src/Mock/workbooks.js

> **Source File:** [src/Mock/workbooks.js](https://github.com/tableau-frontend/blob/main/src/Mock/workbooks.js)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

### Overview
This file serves as a mock data source, exporting a static JavaScript object named `allWorkBooks`. It contains a structured array of workbook entities, intended to simulate responses from a backend API or data service for development and testing purposes.

### Architecture & Role
Architecturally, this file acts as a client-side data provider within a development or testing environment. It resides at the data layer or mock service layer, where it substitutes actual network requests to an external API for retrieving workbook lists. Its role is to enable front-end development and unit/integration testing without requiring a live backend connection.

### Key Components
- `allWorkBooks`: A constant JavaScript object that is the sole export of this module. It contains a `data` property, which in turn has a `workbooks` array.
- Workbook Object Structure: Each object within the `workbooks` array represents a single workbook and includes properties such as:
    - `id`: Unique identifier for the workbook.
    - `name`: Display name of the workbook.
    - `project`: Object containing `id` and `name` of the associated project.
    - `location`: Object detailing the location (e.g., project).
    - `owner`: Object with `id` and `name` of the workbook owner.
    - `contentUrl`: URL slug for the workbook content.
    - `webpageUrl`: Full URL to access the workbook on a web platform (e.g., Tableau Online).
    - `createdAt`, `updatedAt`: Timestamps for creation and last update.
    - Other properties like `tags`, `dataAccelerationConfig`, `showTabs`, `size`, `encryptExtracts`, `defaultViewId`.

### Execution Flow / Behavior
This file does not contain any executable logic or functions; it merely exports a static data structure. When imported into another module, the `allWorkBooks` object becomes available for direct access. There is no runtime behavior beyond the initial loading and parsing of this constant data upon module import.

### Dependencies
None significant.
This file is a standalone data export and does not import other modules. Other parts of the application, typically UI components or data fetching utilities in a development context, will depend on this file by importing the `allWorkBooks` constant.

### Design Notes
This module's design as a hardcoded mock data file simplifies development by providing immediate data for UI rendering and logic testing without needing a live backend. However, it presents a few considerations:
- **Maintainability**: As the application grows or API contracts change, this static data must be manually updated, potentially leading to discrepancies if not regularly synchronized.
- **Dynamic Scenarios**: It cannot simulate dynamic behaviors such as loading states, pagination, error conditions, or varied data sets based on user input, which a more sophisticated mock service or actual API would provide.
- **Production Readiness**: This file is strictly for development and testing environments and must not be included in production builds to avoid exposing internal data structures or incorrect behavior.

### Diagram (Optional)
None significant.
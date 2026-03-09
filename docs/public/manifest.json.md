# public/manifest.json

> **Source File:** [public/manifest.json](https://github.com/test-company-prowiz/tableau-frontend/blob/main/public/manifest.json)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

# public/manifest.json

### Overview
This file defines the web application's metadata, enabling it to be installed on a user's device and function as a Progressive Web App (PWA). It specifies information like the app's name, icons, start URL, and display characteristics for the browser and operating system.

### Architecture & Role
This `manifest.json` file serves as a static configuration asset. It is typically served by the web server alongside other public assets (like `index.html`, CSS, and JavaScript files). Browsers, especially those supporting PWAs, automatically discover and parse this manifest when an associated HTML page links to it (e.g., via `<link rel="manifest" href="/manifest.json">`). Its primary role is to provide a standardized way for web applications to describe themselves for a more integrated user experience.

### Key Components
*   `short_name`: A concise name for the application, displayed when space is limited (e.g., on a home screen icon).
*   `name`: The full, human-readable name of the application.
*   `icons`: An array of image objects specifying application icons for various resolutions and purposes.
    *   `src`: The path to the icon image file.
    *   `sizes`: The dimensions of the icon in pixels.
    *   `type`: The MIME type of the icon image.
*   `start_url`: The URL that is loaded when the user launches the application from their home screen. A value of `.` indicates the current directory.
*   `display`: Defines the preferred display mode for the web application (e.g., `standalone` for an app-like experience without browser UI).
*   `theme_color`: The default theme color for the application, influencing browser UI elements like the address bar.
*   `background_color`: The placeholder background color for the application splash screen, displayed before the web application content has loaded.

### Execution Flow / Behavior
This file is not executed but consumed. When a browser loads an HTML page that references this manifest via a `<link>` tag, the browser fetches and parses its JSON content. It then uses the information provided to:
*   Prompt the user to "add to home screen" or "install app".
*   Display the correct icons and names in app launchers or task switchers.
*   Configure the application's display mode (e.g., full screen, standalone window).
*   Set the initial theme and background colors for the user interface.

### Dependencies
*   **Internal**:
    *   `favicon.ico`: Referenced by the `icons` array for smaller resolutions.
    *   `logo192.png`: Referenced by the `icons` array for medium resolutions.
    *   `logo512.png`: Referenced by the `icons` array for larger resolutions.
These image files must exist at the specified paths relative to the manifest file for the icons to load correctly.
*   **External**: None, as this is a self-contained configuration file.

### Design Notes
The `manifest.json` adheres to the Web App Manifest standard, critical for enabling Progressive Web Application features. The inclusion of multiple icon sizes ensures optimal display across diverse devices and operating system environments. The `start_url` relative path (`.`) is a common pattern for single-page applications, pointing to the root of the application. The `display: "standalone"` property is a key decision for a more native application feel, removing typical browser UI elements. The `theme_color` and `background_color` provide visual continuity during loading and integration with the OS.

### Diagram (Optional)
None significant.
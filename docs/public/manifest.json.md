# public/manifest.json

> **Source File:** [public/manifest.json](https://github.com/tableau-frontend/blob/main/public/manifest.json)  
> **Repository:** `tableau-frontend`  
> **Branch:** `main`

### Overview
This file serves as the Web App Manifest for the application. It provides metadata about the web application in a JSON format, which browsers can use to enable Progressive Web App (PWA) features and integrate the application more deeply with the user's operating system.

### Architecture & Role
Architecturally, `manifest.json` is a client-side configuration file. It resides in the `public` directory, making it directly accessible by the web server. It is typically linked by the `index.html` file using a `<link rel="manifest" href="/manifest.json">` tag. Its role is to define how the application should appear and behave when installed on a user's device, rather than just being viewed in a browser tab.

### Key Components
*   `short_name`: A short, human-readable name for the application. Used when space is limited, such as on a home screen icon.
*   `name`: The full, human-readable name of the application.
*   `icons`: An array of objects, each defining an application icon at different sizes and types. These are used for various contexts like home screens, app launchers, and splash screens.
*   `start_url`: Specifies the URL that should be loaded when the user launches the application from an installed icon. A value of `.` indicates the root of the application.
*   `display`: Defines the preferred display mode for the application. `standalone` suggests that the application should run without any browser UI elements (like address bar, back/forward buttons).
*   `theme_color`: The default theme color for the application. This may influence the color of the operating system's UI elements, such as the task switcher or status bar.
*   `background_color`: The background color that is displayed on the splash screen while the application is loading.

### Execution Flow / Behavior
When a browser encounters the `<link rel="manifest" ...>` tag in `index.html`, it fetches this `manifest.json` file. The browser then parses its content to understand the application's metadata. If the application meets PWA criteria (e.g., served over HTTPS, has a service worker), the browser may offer the user an "Add to Home Screen" or "Install App" prompt. Upon installation, the browser uses the information in this manifest (like `name`, `short_name`, `icons`, `start_url`, `display`, `theme_color`, `background_color`) to create an app-like experience, including a dedicated icon and potentially a splash screen.

### Dependencies
*   **index.html**: Relies on `index.html` to link to it via a `<link>` tag so browsers can discover it.
*   **Icon Image Files**: Explicitly references image files such as `favicon.ico`, `logo192.png`, and `logo512.png` for application icons. The availability of these files at the specified paths is crucial for the manifest to function correctly.

### Design Notes
This file is a standard component for modern web applications aiming for PWA capabilities. Its declarative nature simplifies the configuration of app-like behavior without requiring specific browser extensions or platform-dependent code. The inclusion of multiple icon sizes ensures optimal display across a range of devices and operating system UI scales. Using `standalone` display mode and defining `theme_color` and `background_color` are key for delivering an integrated, native-like user experience.

### Diagram (Optional)
None significant.
# public/index.html

### Overview
This file serves as the root HTML document and the primary entry point for the web application. It defines the basic page structure, metadata, external resource links, and a mount point for the client-side application.

### Architecture & Role
Architecturally, this file is the foundation of the user interface layer. It is a static asset served by a web server, loaded first by the client's browser. It is responsible for initializing the browser environment, loading critical third-party scripts like the Tableau Embedding API, and providing the `div` element where the main JavaScript application will render its content.

### Key Components
*   **`<!DOCTYPE html>`**: Declares the document as an HTML5 page.
*   **`<html lang="en">`**: The root element, specifying English as the document language.
*   **`<head>`**: Contains metadata, document title, and links to external resources:
    *   **`<meta>` tags**: Define character set, viewport settings, theme color, and a description for search engines.
    *   **`<link rel="icon">`, `<link rel="apple-touch-icon">`**: Reference favicon and touch icon assets.
    *   **Google Fonts links**: Preloads custom fonts from `fonts.googleapis.com`.
    *   **`<link rel="manifest">`**: Links to `manifest.json` for Progressive Web App (PWA) features.
    *   **`<title>`**: Sets the browser tab title to "Qadence by TQG".
    *   **Tableau Embedding API Script**: Loads `tableau.embedding.3.latest.js` from `public.tableau.com`, enabling embedding Tableau dashboards.
*   **`<body>`**: Contains the visible content of the page:
    *   **`<noscript>`**: Displays a message if JavaScript is disabled in the browser.
    *   **`<div id="root">`**: An empty `div` element designated as the mount point for a client-side JavaScript application.

### Execution Flow / Behavior
1.  A browser requests the application's root URL, which typically serves this `index.html` file.
2.  The browser parses the HTML, sets up the document structure, and processes metadata.
3.  External stylesheets (via Google Fonts) are fetched, and the Tableau Embedding API script is loaded.
4.  The `div id="root"` element is made available in the Document Object Model (DOM).
5.  Following the load of this HTML, a client-side JavaScript bundle (injected into the `<body>` during the build process, as indicated by comments) executes. This bundle then typically targets and renders application components into the `div id="root"` element, activating the single-page application experience.

### Dependencies
*   **Internal Public Assets**:
    *   `%PUBLIC_URL%/favicon.ico`: Page icon.
    *   `%PUBLIC_URL%/logo192.png`: Apple touch icon.
    *   `%PUBLIC_URL%/manifest.json`: Web app manifest for PWA features.
*   **External Assets**:
    *   `https://fonts.googleapis.com/css2?family=Exo:wght@300;400;600&family=Inter:wght@600;400&family=Outfit&display=swap`: Google Fonts for custom typography.
    *   `https://public.tableau.com/javascripts/api/tableau.embedding.3.latest.js`: Tableau JavaScript API for embedding interactive dashboards.

### Design Notes
*   This file serves as a template, indicating that its content (specifically the `<body>` scripts) will be modified by a build process (e.g., `npm run build`) before deployment.
*   The use of `%PUBLIC_URL%` is a placeholder mechanism commonly found in frameworks like Create React App, ensuring correct asset paths regardless of the deployment environment's base URL.
*   The inclusion of the Tableau Embedding API directly in the head signifies that Tableau integration is a core and early requirement for the application.
*   The `<div id="root">` element explicitly designates a single mount point for a client-side JavaScript framework, confirming a Single Page Application (SPA) architecture.

### Diagram (Optional)
```mermaid
graph TD
A[Browser Request] --> B[index.html]
B --> C[Load Tableau Embedding API]
B --> D[Define App Root Element (#root)]
```
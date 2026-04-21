# src/App.css

> **Source File:** [src/App.css](https://github.com/test-company-prowiz/tableau-frontend/blob/main/src/App.css)
> **Repository:** `tableau-frontend`
> **Branch:** `main`

# src/App.css

### Overview
This file defines global and component-specific styling for the main application layout and common UI elements. It primarily customizes the appearance of `slick-carousel` components and provides styles for loading indicators.

### Architecture & Role
This file operates within the presentation layer, providing cascading style rules. It is likely imported globally or by the root `App` component to define the visual aesthetics and layout for various parts of the user interface.

### Key Components
*   `.App`: Establishes the primary application container with a flexbox row layout.
*   `.slick-slide`, `.slick-slider`, `.slick-list`: Customizes padding and spacing for elements within a `slick-carousel` instance.
*   `.slick-arrow.slick-next`, `.slick-arrow.slick-prev`: Styles the navigation arrows for carousels, including background color, dimensions, shape, and hover effects.
*   `.slick-prev::before`, `.slick-next::before`: Explicitly hides the default content (icons) for the carousel navigation arrows.
*   `.arrows`: Defines specific dimensions for custom arrow elements.
*   `.workbooks`: Styles a flex container to arrange workbook-related content horizontally and centrally.
*   `.spinning_indicator`, `.spinning_indicator_views`: Defines styles for full-page and partial-page loading overlays, including absolute positioning, background, opacity, and centering of content.

### Execution Flow / Behavior
When HTML elements with these class names are rendered, the browser applies the corresponding CSS rules defined in this file. These rules dictate visual properties such as layout (`display`, `flex-direction`), spacing (`padding`, `margin`), appearance (`background-color`, `border-radius`, `opacity`), and positioning (`position`, `z-index`).

### Dependencies
*   **Implicit HTML Structure**: Relies on the application's HTML markup using specific class names (e.g., `App`, `slick-slide`, `spinning_indicator`).
*   **Slick Carousel Library**: The styles are specifically designed to override or augment the default styling of a `slick-carousel`-based library (e.g., React Slick).

### Design Notes
*   Flexbox is utilized for primary layout (`.App`, `.workbooks`) and content centering (`.spinning_indicator`).
*   Custom styling for `slick-carousel` arrows and slide spacing ensures a consistent visual theme.
*   The use of absolute positioning and `z-index` for loading indicators provides overlay functionality.
*   `!important` declarations on `.workbooks` indicate that these styles are intended to override potentially conflicting rules with higher specificity elsewhere in the stylesheet cascade.

### Diagram
None significant.
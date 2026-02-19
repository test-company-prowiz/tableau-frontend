# tableau-frontend — Repository Overview

### High-Level Purpose
The `tableau-frontend` repository hosts a React-based single-page application (SPA) designed to provide user interface and experience. Its primary objective is to render dynamic content, manage user interaction, and facilitate communication with backend services and external authentication providers.

### Architectural Structure
This repository establishes a standard Node.js-based frontend application structure. The `package.json` file, located at the root, defines the project's metadata, dependencies, and build scripts. The overall architecture is typical for a client-side application, where application logic and UI components are compiled into static assets for deployment.

### Core Components
*   **User Interface (UI) Framework**: Built on React, leveraging `react-dom` for rendering.
*   **UI Component Library**: Utilizes Ant Design (`antd`) for a comprehensive set of enterprise-level UI components.
*   **Client-Side Routing**: `react-router-dom` manages navigation and different views within the application.
*   **API Interaction**: `axios` serves as the HTTP client for making requests to backend services.
*   **Authentication**: Integrates with Google OAuth via `@react-oauth/google` for user authentication workflows.
*   **Development Tooling**: `react-scripts` provides encapsulated scripts for starting the development server, building the application, and running tests.

### Interaction & Data Flow
The frontend application initiates interactions primarily through user actions or lifecycle events.
*   HTTP requests are made to backend services using `axios` to fetch or submit data.
*   User authentication is handled by delegating to Google's OAuth service through `@react-oauth/google`.
*   Client-side routing ensures that different application views are rendered dynamically without full page reloads.

### Technology Stack
*   **Core Libraries**: React, React DOM
*   **UI Libraries**: Ant Design (`antd`), React Icons, React Slick, Slick Carousel, React Toastify
*   **State & Routing**: React Router DOM, React Hook Form
*   **API Client**: Axios
*   **Authentication**: Google OAuth (`@react-oauth/google`)
*   **Development & Build**: React Scripts, ESLint, Jest, React Testing Library
*   **Styling**: Tailwind CSS

### Design Observations
The project's use of `react-scripts` indicates an initial setup with Create React App, providing a pre-configured and managed development environment. The choice of Ant Design suggests a preference for a feature-rich, opinionated UI library suitable for enterprise applications. Integration with Google OAuth points to a strategy for social login, streamlining user onboarding. The `private: true` flag in `package.json` confirms that this application is not intended for public package distribution but rather as a standalone application.

### System Diagram (Optional)
None significant.
# Svelte E-commerce Product Page

This project is a responsive web interface for an e-commerce product page, built using Svelte and styled with Tailwind CSS. It features a clean, modern UI, dark mode, and dynamic product details with color and size selection.

## Project Overview

-   **Framework:** Svelte
-   **Styling:** Tailwind CSS
-   **UI Components:** Custom-built responsive components.
-   **Features:**
    -   Responsive design for desktop and mobile.
    -   Dark mode toggle.
    -   Product listing page.
    -   Dynamic product detail page with image gallery (main image for desktop, thumbnails for mobile).
    -   Product color and size selection options.

## Architecture

The application is structured into several Svelte components:

-   `src/App.svelte`: The main application component, handling routing and overall layout.
-   `src/lib/Header.svelte`: Responsive header with navigation and theme switcher.
-   `src/lib/ThemeSwitcher.svelte`: Component for toggling dark/light mode.
-   `src/lib/Shop.svelte`: Displays a list of products using `ProductCard` components.
-   `src/lib/ProductCard.svelte`: Individual product card displayed on the shop page.
-   `src/lib/ProductDetail.svelte`: Displays detailed information for a single product, including image gallery, description, and options.
-   `src/lib/Modal.svelte`: Reusable modal component for displaying content (e.g., image carousel).
-   `src/lib/Carousel.svelte`: Image carousel component used within the modal.
-   `src/data.js`: Contains static product data, including descriptions, images, colors, and sizes.

Routing is handled using `svelte-routing` to navigate between the shop page and individual product detail pages.

## Getting Started

Follow these instructions to set up and run the project locally.

### Prerequisites

-   Node.js (LTS version recommended)
-   npm (Node Package Manager)
-   Docker (optional, for containerized deployment)

### Local Development

1.  **Navigate to the project directory:**
    ```bash
    cd svelte-ecommerce-page
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Run the development server:**
    ```bash
    npm run dev
    ```
    The application will be accessible at `http://localhost:5173` (or another port if 5173 is in use).

### Building for Production

To create a production-ready build of the application:

```bash
npm run build
```

This will generate optimized static assets in the `dist/` directory.

### Running with Docker (Optional)

To build and run the application using Docker:

1.  **Build the Docker image:**
    ```bash
    docker build -t svelte-ecommerce .
    ```

2.  **Run the Docker container:**
    ```bash
    docker run -p 8080:80 svelte-ecommerce
    ```
    The application will be accessible at `http://localhost:8080`.

## Git Repository Instructions

If you are setting up a new Git repository for this project:

1.  **Initialize a new Git repository (if not already done):**
    ```bash
    git init
    ```

2.  **Add all project files to the staging area:**
    ```bash
    git add .
    ```

3.  **Commit your changes:**
    ```bash
    git commit -m "Initial commit: Svelte E-commerce Product Page"
    ```

4.  **Add a remote repository (replace `<your-repository-url>` with your actual repository URL):**
    ```bash
    git remote add origin <your-repository-url>
    ```

5.  **Push your local commits to the remote repository:**
    ```bash
    git push -u origin main
    ```
    (Use `master` instead of `main` if your default branch is named `master`.)

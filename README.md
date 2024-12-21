# Tailwind CSS Project Setup

This README provides instructions for setting up a basic Tailwind CSS project with separate `src` and `dist` folders. This structure helps keep your source CSS organized and separate from the final compiled CSS.

## Steps to Set Up the Project

1.  **Create the Project Structure**

    Create the following folders and files in your project directory:

    ```
    project-folder/
    ├── src/
    │   └── input.css
    └── dist/
        └── index.html
    ```

    *   **`project-folder/`**: This is the root directory of your project. You can name it whatever you like.
    *   **`src/`**: This folder will contain your source CSS files, including your `input.css`.
    *   **`dist/`**: This folder will contain your compiled CSS (generated by Tailwind) and your HTML files. `dist` stands for "distribution".

2.  **Initialize Tailwind CSS**

    Open your terminal and navigate to your `project-folder/` using the `cd` command. Then, initialize Tailwind CSS by running:

    ```bash
    npx tailwindcss init
    ```

    This command creates a `tailwind.config.js` file in your project's root directory. This file is where you'll customize your Tailwind installation.

3.  **Update `tailwind.config.js`**

    Open the `tailwind.config.js` file and update the `content` array to tell Tailwind where to look for your HTML files that use Tailwind classes. This is important so that Tailwind can purge unused CSS in the final build.

    ```javascript
    module.exports = {
      content: ["./dist/index.html"], // The path of your index.html
      theme: {
        extend: {},
      },
      plugins: [],
    };
    ```

4.  **Run the Build Command**

    In your terminal, run the following command to build your CSS and start a watch process:

    ```bash
    npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
    ```

    *   **`npx tailwindcss`**: This runs the Tailwind CSS CLI.
    *   **`-i ./src/input.css`**: This specifies the input CSS file (`input.css` in the `src` folder).
    *   **`-o ./dist/output.css`**: This specifies the output CSS file (`output.css` in the `dist` folder).
    *   **`--watch`**: This flag tells Tailwind to watch for changes in your `input.css` file and your HTML files specified in `tailwind.config.js`. When changes are detected, it will automatically rebuild the `output.css` file. This is extremely useful during development.

5.  **Start Working on Your Project**

    *   **`dist/index.html`**:  Use this file as the starting point for your HTML structure.
    *   **Link the CSS:** Add the following line inside the `<head>` of your `dist/index.html` file to link the generated Tailwind CSS file:

        ```html
        <link rel="stylesheet" href="output.css">
        ```

    *   **`src/input.css`**: Add Tailwind directives to this file to begin styling. These directives are:

        ```css
        @tailwind base;
        @tailwind components;
        @tailwind utilities;
        ```
        You can write custom CSS in this file alongside the `@tailwind` directives.

**Now you're ready to start building!**  Any changes you make to `input.css` or `index.html` will automatically be reflected in your browser after Tailwind rebuilds the CSS.

**Key Takeaways:**

*   **Organized Structure:** The `src` and `dist` folders separate your source code from the compiled output.
*   **Customization:** `tailwind.config.js` allows you to customize your Tailwind setup.
*   **Watch Mode:** The `--watch` flag provides a smooth development workflow.

This setup will allow you to use Tailwind efficiently while keeping your project clean and easy to maintain. Happy coding!
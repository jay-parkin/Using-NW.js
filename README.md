# Setting Up NW.js to Package a React Project into an Executable

This repository serves as a comprehensive guide and a practical example for using NW.js to package a React application into a desktop executable. Below is an outline of what you can expect in this repository.

## Structure of the Repository

### Documentation

- A detailed step-by-step guide (`README.md`) explaining how to install and set up NW.js, prepare your React project, and package it into a desktop application.
- Troubleshooting tips for common errors encountered during the process.

### Starter Files

- A sample `package.json` template configured for NW.js, designed to work with a typical React project's `build/` directory.
- Example NW.js window settings, such as dimensions, icons, and toolbar preferences.

### NW.js Project Integration:

- A structured example directory for how to organise your NW.js project, including the placement of the React `build/` files and the NW.js-specific `package.json`.
- Clear notes on how to align the React app's `index.html` with the NW.js main entry point.

## Prerequisites

- **Node.js and npm installed:** Ensure you have Node.js (v12 or later) installed on your system.
- **A React project:** Your project should already be built using tools like `create-react-app` or a similar React setup.

## Step 1: Install NW.js

1. **Download NW.js:**

   - Visit the [NW.js download page](https://nwjs.io/downloads/).
   - Choose the appropriate version for your operating system (e.g., Normal, SDK, or LTS).
     - SDK will allow devtools

2. **Extract NW.js:**
   - Extract the downloaded archive to a desired directory. For example:
     ```
     /path/to/nwjs/
     ```

## Step 2: Build Your React Project

1. **Navigate to your React project directory:**
   ```bash
   cd /path/to/your-react-project
   ```
2. **Build the React project**
   ```bash
   npm run build
   ```
   This creates a `build/` directory containing your project-ready React app.

## Step 3: Prepare the NW.js Application

1.  **Create a new `package.json` for NW.js: - In your React project directory (or a new directory to house your NW.js app), create a file named `package.json` with the following structure:**

    ```json
    {
      "name": "your-app-name",
      "version": "1.0.0",
      "main": "build/index.html",
      "node-remote": "path/to/remote-files",
      "window": {
        "title": "window-title",
        "icon": "path/to/icon.png",
        "toolbar": true,
        "frame": true,
        "width": 800,
        "height": 800
      },
      "chromium-args": "--enable-logging --remote-debugging-port=9222 --no-sandbox"
    }
    ```

    Adjust the `width`, `height`, and other window properties as needed.

2.  **Copy the `build/` directory into the NW.js folder:**

    - Place the entire folder of your React `build/` directory into the NW.js directory:

3.  **Place the `package.json` inside the same app directory**:
    ```bash
    /path/to/nwjs/package.json
    ```

## Troubleshooting

1. **Application doesn't launch:**

   - Verify the main property in `package.json` points to the correct location of your `index.html` file.

2. **Errors in packaging:**
   - Double-check that all required files are included in the `build/` directory.

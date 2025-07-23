# PHP Docker Environment Generator

This is a web-based utility to quickly generate a flexible, containerized PHP development environment using Docker Compose. It allows you to select the services you need (database, cache, etc.), customize settings, and download a ready-to-use `.zip` archive.

This project was built to be a framework-agnostic, modern alternative to tools like Laravel Sail, suitable for any PHP project.

**Live Demo:** [Link to your hosted generator] *(Replace this with the URL where you host the `index.html` file)*

## Features

- **Modular Services:** Choose only the services you need.
    - **Databases:** MySQL, MariaDB, PostgreSQL.
    - **Caching:** Redis.
    - **Utilities:** Mailpit for email catching, Typesense for search.
    - **Admin Tools:** phpMyAdmin, pgAdmin.
- **Customizable:**
    - Select PHP versions from 7.4 to 8.3.
    - Configure application name, port, and all database credentials.
- **AI-Powered READMEs:** If configured locally, it uses the Gemini API to generate a detailed, project-specific `README.md` for the environment it creates.
- **Zero Dependencies:** Runs entirely in the browser. Just open the `index.html` file.

## How to Use

### For End-Users

The easiest way to use the generator is to visit the live demo link above.

Alternatively, you can download the `index.html` file from this repository and open it directly in your web browser.

1.  Select your desired PHP version and services.
2.  Expand the "Advanced Options" to customize ports, names, or passwords if needed.
3.  Click "Generate & Download ZIP".
4.  Extract the downloaded `.zip` file into your new project folder.
5.  Follow the instructions in the generated `README.md` file to start your environment.

## How to Develop or Contribute

This project is a single HTML file with embedded CSS and JavaScript. You can edit `index.html` directly.

To enable the AI-powered README generation feature for local development, you need to provide your own Google Gemini API key.

### Enabling AI Features Locally

The application is designed to be secure. It will only enable the AI features if it detects a `config.js` file containing an API key. This file is intentionally excluded from version control and should **never** be committed.

**Step 1: Get a Gemini API Key**

1.  Visit [Google AI Studio](https://aistudio.google.com/).
2.  Log in with your Google account.
3.  Click on **"Get API key"** and then **"Create API key in new project"**.
4.  Copy the generated API key. Google provides a generous free tier that is more than sufficient for development purposes.

**Step 2: Create `config.js`**

In the same directory as `index.html`, create a new file named `config.js`. Place your API key inside this file like so:

```javascript
// config.js
// This file contains your secret API key for local development.
// DO NOT commit this file to Git.

const GEMINI_API_KEY = "YOUR_API_KEY_HERE";
```

**Step 3: Run the Generator**

Now, when you open `index.html` in your browser, the script will detect `GEMINI_API_KEY` and automatically enable the "✨ Use AI for a more detailed README" option.

### Git Configuration (`.gitignore`)

To ensure your secret API key is never accidentally committed to the repository, create a `.gitignore` file in your project root with the following content.

```
# .gitignore

# Ignore the local configuration file containing the API key
config.js

# Ignore common OS files
.DS_Store
Thumbs.db

# Ignore IDE/editor specific files
.idea/
.vscode/
```

With this setup, you can safely work on the project, use the AI features locally, and collaborate with others without exposing your secret key.

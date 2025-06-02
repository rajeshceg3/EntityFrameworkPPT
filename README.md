# Entity Framework Mastery - Slidev Presentation

This project contains a comprehensive presentation on Entity Framework (EF) Core, created using Slidev. It covers various aspects of EF Core, from basic concepts to advanced features and best practices.

## Running the Presentation

To view and interact with this presentation, you'll need to have Node.js and npm (or yarn) installed on your system.

### Prerequisites

*   **Node.js:** (LTS version recommended). You can download it from [https://nodejs.org/](https://nodejs.org/).
*   **npm:** (Usually comes with Node.js) or **yarn** (optional: [https://yarnpkg.com/](https://yarnpkg.com/)).

### Installation

1.  Clone this repository to your local machine.
2.  Open a terminal in the project's root directory.
3.  Install the dependencies:
    ```bash
    npm install
    ```
    or if you prefer yarn:
    ```bash
    yarn install
    ```

### Viewing Locally

To start the Slidev presentation in development mode (with hot-reloading):

```bash
npm run dev
```
or
```bash
yarn dev
```
This will typically open the presentation in your default web browser at `http://localhost:3030/`.

### Building for Production

To build the presentation into static HTML files (usually in a `dist/` directory):

```bash
npm run build
```
or
```bash
yarn build
```
These static files can then be hosted on any web server.

### Exporting

Slidev allows you to export your presentation in different formats:

*   **PDF:**
    ```bash
    npm run export
    ```
    or
    ```bash
    yarn export
    ```
    This will generate a PDF of your slides. You might need to install `playwright-chromium` separately if issues arise (`npm install playwright-chromium` or `npx playwright install chromium`).

*   **PNGs (Screenshots of each slide):**
    ```bash
    npm run export -- --format png
    ```
    or
    ```bash
    yarn export --format png
    ```

*   **Single-Page Application (SPA) with Clickable Slides:**
    The `npm run build` command already creates a SPA in the `dist/` folder.

## How to Use This Presentation

This project is a Slidev-based presentation. Here are the primary ways you can use it:

*   **Local Viewing & Development:**
    Run `npm run dev` to view the slides in your browser. This is ideal for making changes to the `slides.md` file and seeing live updates. It's also great for presenting directly if you're running it on your machine.

*   **Static Hosting:**
    After running `npm run build`, the contents of the `dist/` directory can be uploaded to any static web hosting service (like GitHub Pages, Netlify, Vercel, AWS S3, etc.). This creates a shareable, web-accessible version of your presentation.

*   **PDF Export:**
    Use `npm run export` to generate a PDF document. This is useful for:
    *   Sharing the presentation as a single file.
    *   Offline viewing.
    *   Creating handouts.

*   **PNG/Image Export:**
    Exporting slides as PNGs (`npm run export -- --format png`) can be useful for:
    *   Embedding individual slides in other documents or websites.
    *   Quickly sharing specific points.

*   **Learning Resource:**
    The `slides.md` file itself is a valuable Markdown document containing detailed information about Entity Framework Core. You can read through it or use it as a reference.

## Scanning and Fixing Bugs

While this project is primarily a presentation, you might encounter issues related to content, styling, or the Slidev framework itself. Here’s how to approach "bugs":

*   **Content Errors (Typos, Technical Inaccuracies):**
    *   **Scanning:** Carefully read through the `slides.md` file. Review the presented information for any typos, grammatical errors, or technical inaccuracies regarding Entity Framework Core.
    *   **Fixing:** Edit the `slides.md` file directly to correct these errors.

*   **Styling or Layout Issues:**
    *   **Scanning:** When viewing the presentation (using `npm run dev`), check each slide for visual consistency, readability, and any layout problems (e.g., overlapping text, elements not appearing correctly).
    *   **Fixing:**
        *   Inspect custom styles in `styles/custom.css` or any other linked CSS files.
        *   Check Slidev's layout components or frontmatter configurations in `slides.md`.
        *   Use your browser's developer tools (Inspect Element) to diagnose CSS issues.
        *   Refer to the [Slidev documentation](https://sli.dev/) for guidance on theming and styling.

*   **Framework or Dependency Issues:**
    *   **Scanning:** Look for error messages in the terminal where you ran `npm run dev` or `npm run build`. Check the browser's developer console for JavaScript errors.
    *   **Fixing:**
        *   **Node Modules Corruption:** If you suspect issues with installed dependencies, try deleting the `node_modules` folder and the `package-lock.json` (or `yarn.lock`) file, then reinstall:
            ```bash
            # For npm
            rm -rf node_modules package-lock.json
            npm install

            # For yarn
            rm -rf node_modules yarn.lock
            yarn install
            ```
        *   **Dependency Version Conflicts:** Ensure versions of `@slidev/cli`, themes, and other dependencies listed in `package.json` are compatible. You might need to update or downgrade packages.
        *   **Consult Slidev Documentation:** The [Slidev GitHub issues](https://github.com/slidevjs/slidev/issues) or documentation might have solutions for common problems.
        *   **Playwright Issues during Export:** If PDF/PNG export fails, it's often due to `playwright-chromium` not being installed correctly. Try:
            ```bash
            npx playwright install chromium
            ```
            or ensure `playwright-chromium` is in your `devDependencies` and reinstall it.

*   **General Troubleshooting:**
    *   **Restart Dev Server:** Sometimes, simply stopping and restarting `npm run dev` can resolve minor glitches.
    *   **Check Node.js/npm Versions:** Ensure your Node.js and npm/yarn versions are compatible with Slidev's requirements (usually listed in its documentation).

## CI/CD Pipeline Setup (Best Practices)

Setting up a CI/CD (Continuous Integration/Continuous Deployment) pipeline can automate testing, building, and deploying your presentation. Here are some industry-standard best practices, adaptable to platforms like GitHub Actions, GitLab CI, Jenkins, etc.

### Continuous Integration (CI)

The CI pipeline should run on every push to the main branch or on pull requests to ensure the presentation is always in a good state.

**Typical CI Steps:**

1.  **Trigger:** Configure the pipeline to trigger automatically on code pushes (e.g., to `main` or `develop` branches) or pull requests.
2.  **Setup Environment:**
    *   Check out the code.
    *   Set up the correct Node.js version (e.g., using `actions/setup-node` in GitHub Actions).
3.  **Install Dependencies:**
    *   Use `npm ci` (recommended for CI as it uses `package-lock.json` for deterministic builds) or `yarn install --frozen-lockfile`.
    ```bash
    npm ci
    ```
4.  **Linting & Formatting (Optional but Recommended):**
    *   If you have linters (e.g., ESLint for JavaScript, Markdownlint for Markdown), run them to enforce code style and catch errors.
    ```bash
    # Example: npm run lint
    ```
5.  **Build Presentation:**
    *   Run the build command to ensure the presentation compiles correctly.
    ```bash
    npm run build
    ```
6.  **Export (Optional Test):**
    *   You might want to run an export to ensure that functionality is working.
    ```bash
    npm run export -- --output slides.pdf
    ```
7.  **Archive Artifacts (Optional):**
    *   Store the built presentation (`dist/` folder) and any exported files (like `slides.pdf`) as build artifacts. This allows you to download them from the CI server.

**Example CI Workflow Snippet (Conceptual for GitHub Actions):**

```yaml
# .github/workflows/ci.yml
name: Slidev CI

on: [push, pull_request]

jobs:
  build_and_test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18' # Specify your Node.js version
        cache: 'npm'
    - name: Install dependencies
      run: npm ci
    - name: Build presentation
      run: npm run build
    - name: Export PDF (optional test)
      run: |
        # Ensure Playwright browsers are installed for export
        npx playwright install --with-deps chromium
        npm run export -- --output slides-ci.pdf
    - name: Upload PDF artifact (optional)
      uses: actions/upload-artifact@v3
      with:
        name: presentation-pdf
        path: slides-ci.pdf
    - name: Upload Build artifact (optional)
      uses: actions/upload-artifact@v3
      with:
        name: presentation-html
        path: dist/
```

### Continuous Deployment (CD)

The CD pipeline automates the deployment of your presentation, typically after a successful CI run on the main branch.

**Typical CD Steps (Example: Deploying to GitHub Pages):**

1.  **Trigger:** Configure to run after successful CI on the `main` branch.
2.  **Build:** Perform all CI steps (install, build).
3.  **Deploy:**
    *   **GitHub Pages:** Use a GitHub Action like `peaceiris/actions-gh-pages` to deploy the contents of your `dist/` folder to the `gh-pages` branch, making it available online.
    *   **Netlify/Vercel:** These platforms often auto-deploy when linked to a Git repository and can detect Slidev projects, or you can configure them to serve the `dist/` folder.
    *   **Other Hosting:** Use tools like `rsync`, `aws s3 sync`, or specific deployment actions/scripts for your chosen hosting provider.

**Example CD Workflow Snippet (Conceptual for GitHub Actions deploying to GitHub Pages):**

```yaml
# .github/workflows/cd.yml (can be part of ci.yml or separate)
name: Slidev CD to GitHub Pages

on:
  push:
    branches:
      - main # Trigger only on pushes to main

jobs:
  deploy:
    runs-on: ubuntu-latest
    needs: build_and_test # Assuming you have a build_and_test job in your CI
    steps:
    - uses: actions/checkout@v3
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
        cache: 'npm'
    - name: Install dependencies
      run: npm ci
    - name: Build presentation
      run: npm run build
      # Potentially adjust base path in vite.config.js for GitHub Pages if needed
      # Example: export SLIDEV_BUILD_BASE=/your-repo-name/
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./dist
        # user_name: 'github-actions[bot]' # Optional
        # user_email: 'github-actions[bot]@users.noreply.github.com' # Optional
        # commit_message: 'Deploy to GitHub Pages' # Optional
```

**Security & Best Practices:**
*   **Secrets Management:** For any sensitive keys (e.g., deployment tokens if not using `GITHUB_TOKEN`), use your CI/CD platform's secret management system.
*   **Deterministic Builds:** `npm ci` helps ensure that the same dependencies are installed each time.
*   **Cache Dependencies:** Cache `node_modules` between CI runs to speed up pipeline execution. Most CI platforms offer a caching mechanism.
*   **Small, Focused Steps:** Keep each step in your pipeline focused on a single task for better readability and debugging.

# CareerFlow Job Tracker

A clean React + Vite job application tracker inspired by the workflow and feature set of the supplied CareerFlow reference website. It starts directly at the **login page**—there is no marketing or landing page.

## Features
- Login and sign-up screens
- Dashboard with application, interview, offer and response-rate summaries
- Add, edit, search, filter and delete job applications
- Application stages: Saved, Applied, Under Review, Interview, Offer, Rejected
- Interview schedule management
- Follow-up reminders with completion checkboxes
- Analytics calculated from your saved applications
- Responsive layout for desktop and mobile
- Browser `localStorage` persistence

## Requirements
Install Node.js LTS from https://nodejs.org/ and Git from https://git-scm.com/downloads. A GitHub account is also needed.

## Run on your computer
1. Extract the ZIP file.
2. Open the extracted `careerflow-tracker` folder in VS Code.
3. Open **Terminal → New Terminal**.
4. Run:

```bash
npm install
npm run dev
```

5. Open the local address shown by Vite (usually `http://localhost:5173`).

## Login / signup
- Select **Create account** to register a demo account.
- Then sign in using the same email and password.
- For quick testing, the login screen also lets you sign in with any non-empty email and password.
- Data is saved in the current browser using localStorage.

## Important demo limitation
This project is a frontend-only learning/demo application. Login and data are stored in the browser and are **not secure production authentication**. There is no server/database, password recovery email, cross-device sync, or real email notifications. Do not use a real password. For a real public product, connect a backend such as Supabase or Firebase and implement server-side authentication and per-user database security.

## Upload to GitHub
### Method A — VS Code
1. Create a new **empty** repository on GitHub. Example name: `careerflow-tracker`.
2. Do not add a README, `.gitignore`, or license on GitHub (this project already has them).
3. In VS Code, open the extracted project folder.
4. Open Terminal and run these commands one by one (replace the URL with your repository's URL):

```bash
git init
git add .
git commit -m "Create CareerFlow job tracker"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/careerflow-tracker.git
git push -u origin main
```

5. Refresh your GitHub repository. Your project files should appear.

### Method B — GitHub website upload
1. Create a new repository on GitHub.
2. Open the repository and select **Add file → Upload files**.
3. Extract the ZIP first, then drag the files and folders from inside `careerflow-tracker` into the upload area.
4. Select **Commit changes**.

## Publish with GitHub Pages
GitHub Pages needs a build/deployment workflow for Vite.

1. In the project, create this folder: `.github/workflows`
2. Inside it, create `deploy.yml` with the following content:

```yaml
name: Deploy CareerFlow to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - name: Install dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: dist
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy
        id: deployment
        uses: actions/deploy-pages@v4
```

3. Commit and push the workflow:

```bash
git add .
git commit -m "Add GitHub Pages deployment"
git push
```

4. On GitHub, open **Settings → Pages**.
5. Under **Build and deployment → Source**, choose **GitHub Actions**.
6. Open the **Actions** tab and wait for the deployment workflow to finish successfully.
7. Your site address will look like `https://YOUR-USERNAME.github.io/careerflow-tracker/`.

## Update the website later
After changing files, run:

```bash
git add .
git commit -m "Update website"
git push
```

GitHub Actions will rebuild and publish the updated site automatically.

## Project structure

```text
careerflow-tracker/
├── .github/                 # Add workflow here for Pages deployment
├── index.html
├── package.json
├── vite.config.js
├── .gitignore
├── README.md
└── src/
    ├── App.jsx
    ├── main.jsx
    └── style.css
```
"# CareerTracker" 

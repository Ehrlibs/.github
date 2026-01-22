# GitHub Pages Setup Instructions

This repository now includes a GitHub Actions workflow to automatically deploy the `index.html` file to GitHub Pages at https://ehrlibs.github.io/.github/

**Note**: To publish at the root URL (https://ehrlibs.github.io/), the repository would need to be renamed to `ehrlibs.github.io`. See `FIX_URL_INSTRUCTIONS.md` for details.

## What Was Added

- A GitHub Actions workflow file at `.github/workflows/pages.yml`
- The workflow automatically deploys to GitHub Pages on every push to the `main` branch
- Can also be triggered manually from the Actions tab

## Required Manual Configuration

To complete the setup, a repository administrator needs to enable GitHub Pages in the repository settings:

1. Go to the repository settings: https://github.com/Ehrlibs/.github/settings
2. Navigate to the "Pages" section in the left sidebar
3. Under "Build and deployment":
   - **Source**: Select "GitHub Actions" (not the legacy "Deploy from a branch" option)
4. Save the settings

## Testing the Deployment

After enabling GitHub Pages in the settings:

1. The workflow will run automatically on the next push to `main`
2. Or you can trigger it manually:
   - Go to the "Actions" tab
   - Select "Deploy to GitHub Pages" workflow
   - Click "Run workflow"
3. Once the workflow completes successfully, the site will be available at https://ehrlibs.github.io/.github/

## Workflow Details

The workflow:
- Triggers on pushes to the `main` branch
- Checks out the repository
- Configures GitHub Pages
- Uploads the entire repository as a Pages artifact
- Deploys the artifact to GitHub Pages

The `index.html` file in the root of the repository will be served as the homepage.

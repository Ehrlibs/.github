# How to Publish at https://ehrlibs.github.io/ Instead of https://ehrlibs.github.io/.github/

## Current Situation

The index.html is currently published at `https://ehrlibs.github.io/.github/` because the repository is named `.github`.

## The Issue

GitHub Pages works as follows:
- A repository named `<org>.github.io` (e.g., `ehrlibs.github.io`) → publishes at `https://<org>.github.io/`
- Any other repository name → publishes at `https://<org>.github.io/<repository-name>/`

Since this repository is named `.github`, it publishes at the subdirectory path `/.github/`.

## Solution: Rename the Repository

To publish directly at `https://ehrlibs.github.io/`, the repository needs to be renamed from `.github` to `ehrlibs.github.io`.

### Steps to Rename (Repository Admin Required)

1. Go to the repository settings: https://github.com/Ehrlibs/.github/settings
2. Scroll down to the "Danger Zone" section
3. Click "Rename repository"
4. Change the name from `.github` to `ehrlibs.github.io`
5. Click "I understand, rename repository"

### After Renaming

- The repository URL will change from `https://github.com/Ehrlibs/.github` to `https://github.com/Ehrlibs/ehrlibs.github.io`
- GitHub will automatically redirect from the old URL
- The GitHub Pages site will be available at `https://ehrlibs.github.io/` (root) instead of `https://ehrlibs.github.io/.github/`
- The existing GitHub Actions workflow will continue to work without any changes
- Local git clones will need to update their remote URL:
  ```bash
  git remote set-url origin https://github.com/Ehrlibs/ehrlibs.github.io.git
  ```

## Important Note about the `.github` Repository

The `.github` repository name is special in GitHub organizations - it's typically used for:
- Organization profile README (shown on the organization page)
- Community health files (CODE_OF_CONDUCT, CONTRIBUTING, etc.)
- Workflow templates

If you want to keep these special features AND have a GitHub Pages site at the root URL, you'll need:
1. A repository named `.github` for the organization profile and community files
2. A separate repository named `ehrlibs.github.io` for the GitHub Pages site

In this case, you would:
1. Create a new repository named `ehrlibs.github.io`
2. Move the `index.html` and `.github/workflows/pages.yml` to the new repository
3. Keep the `.github` repository for the profile README and community health files

## Alternative: Accept the Current URL

If renaming is not desirable, you can accept the current behavior and update documentation to reflect that the site is at `https://ehrlibs.github.io/.github/` instead of `https://ehrlibs.github.io/`.

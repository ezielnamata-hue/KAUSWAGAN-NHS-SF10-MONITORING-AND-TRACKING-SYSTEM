# KNHS SF10 Transmittal & Monitoring System — GitHub Pages

This package is a static GitHub Pages version of the KNHS SF10 application with optional
automatic synchronization to the configured Google Drive folder.

## Important

GitHub Pages hosts the HTML/JavaScript. It does **not** provide a server-side database.
The application therefore:

- keeps the working database in browser Local Storage;
- uses Google OAuth in the browser when the user connects Drive;
- creates/updates `KNHS_SF10_LiveDatabase.json` in the configured Drive folder;
- can still download a standalone JSON backup.

No Google password, OAuth client secret, or service-account private key belongs in this repository.

## Publish on GitHub Pages

1. Create a GitHub repository.
2. Upload `index.html` and `.nojekyll` from this folder.
3. In the repository, open **Settings → Pages**.
4. Select the branch/folder containing `index.html`, then save.
5. Open the published site.

GitHub Pages will serve the site over HTTPS.

## Configure Google Drive

The application is already pointed at the requested repository folder:

`https://drive.google.com/drive/u/0/folders/1JdX3VnhTNDeIsisCWFYdNkENI5yOCna9`

Before connecting:

1. In Google Cloud Console, create/select a project.
2. Enable the Google Drive API.
3. Configure the OAuth consent screen.
4. Create an **OAuth 2.0 Client ID** with application type **Web application**.
5. Add the exact GitHub Pages origin shown by the browser to **Authorized JavaScript origins**.
   - Example project site: `https://YOUR-USERNAME.github.io`
   - Example repository site: `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY`
   - For OAuth, the origin is normally the scheme + host, so use the origin shown by the app's Setup dialog.
6. Open the site, click **Drive Settings**, paste the OAuth Web Client ID, and click **Connect Google Drive**.
7. Sign in with a Google account that has access to the target Drive folder.

## Data behavior

The app does not put the school database into the GitHub repository. The repository contains only
the application code. Live records are stored locally in the browser and synchronized to the
Google Drive JSON file after the user authorizes Drive access.

For multi-user school-wide operation, a server-side backend or Google Apps Script architecture is
recommended so all users share one authoritative database and permissions can be centrally managed.

# SKM Community Platform Proposal

Static web proposal (`index.html`) configured for automatic deployment to **Firebase Hosting** via GitHub Actions while keeping this repository private.

## One-Time Firebase Setup

1. Open the [Firebase Console](https://console.firebase.google.com/) and create (or select) a Firebase project.
2. In the left menu, go to **Build → Hosting** and click **Get started** to initialize Hosting for the project.
3. Create a service account key:
   - Open [Google Cloud Console → IAM & Admin → Service Accounts](https://console.cloud.google.com/iam-admin/serviceaccounts) for the same project.
   - Click **Create Service Account**, grant it the **Firebase Hosting Admin** (`roles/firebasehosting.admin`) and **Service Usage Consumer** (`roles/serviceusage.serviceUsageConsumer`) roles.
   - Open the created service account → **Keys** tab → **Add key → Create new key → JSON** to download the JSON key file.
4. Add the secret in GitHub:
   - Go to **Settings → Secrets and variables → Actions → New repository secret**.
   - Name: `FIREBASE_SERVICE_ACCOUNT`
   - Value: paste the entire contents of the downloaded JSON file.
5. Publish:
   - Go to **Actions → Deploy to Firebase Hosting → Run workflow** (or push any commit to `main`).
   - Your live URL (`https://<your-project-id>.web.app`) will appear in the workflow run summary.

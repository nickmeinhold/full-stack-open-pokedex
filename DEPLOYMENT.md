# Deployment Guide

## Firebase Hosting Setup

This project is configured to deploy to Firebase Hosting automatically via GitHub Actions.

### Initial Setup

1. **Firebase CLI Login**

   ```bash
   firebase login
   ```

2. **Generate CI Token**

   ```bash
   firebase login:ci
   ```

   Copy the token that's generated.

3. **Add GitHub Secret**
   - Go to GitHub repository → Settings → Secrets and variables → Actions
   - Create new secret: `FIREBASE_SERVICE_ACCOUNT`
   - Paste the token from step 2

### Manual Deployment

```bash
# Build and deploy
npm run deploy:full

# Or deploy without rebuilding
npm run deploy
```

### Automatic Deployment (CI/CD)

The GitHub Actions pipeline automatically:

- Runs on pushes to `main` or `fullstackopen` branches
- Checks code formatting
- Runs linting
- Builds the application
- Runs unit tests
- Runs e2e tests
- Deploys to Firebase (if all tests pass)

### Skip Deployment

Include `#skip` in your commit message to skip deployment:

```bash
git commit -m "Update README #skip"
```

### Firebase Project

- Project ID: `fullstackopen-part11`
- Hosting URL: <https://fullstackopen-part11.web.app>

### Configuration Files

- `firebase.json` - Firebase hosting configuration
- `.firebaserc` - Firebase project settings
- `.github/workflows/pipeline.yml` - CI/CD pipeline

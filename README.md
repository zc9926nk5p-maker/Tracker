# Baby Log

Feeds, sleep and weather for two parents. A static web app: no build step, just these files.

## Files
- `index.html` the whole app
- `sw.js` offline support
- `manifest.json`, `icon-192.png`, `icon-512.png` install-to-home-screen

## Put it online (GitHub Pages)
1. Create a new GitHub repository and upload every file in this folder to the top level.
2. Repository Settings, Pages, Build and deployment: deploy from the `main` branch, `/ (root)`.
3. After a minute your site is live at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

## Share between two phones (Firebase, free tier)
1. console.firebase.google.com: Add project, then Build, Firestore Database, Create database.
2. Project settings, Your apps, Web (`</>`): copy the `firebaseConfig` object.
3. In `index.html`, paste it in place of `const FIREBASE_CONFIG = null;`, then commit.
4. Firestore, Rules: paste the rules below and Publish.

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /families/{family}/events/{event} {
      allow read, write: if true;
    }
  }
}
```

5. Open the site on your phone, Settings tab, Share invite link, and open it on your partner's phone.

Your data is separated by a long random family code inside the invite link. Don't post the link publicly.

## Install on a phone
- Android (Chrome): menu, Install app. Then open it in a floating or split-screen window next to a video.
- iPhone (Safari): Share, Add to Home Screen.

## Changing the weather location
Edit the `WX` line near the top of the script in `index.html` (latitude, longitude, timezone, place name).

## After you edit files
Bump the version in `sw.js` (`baby-log-v7` to `baby-log-v8`) so phones pick up the change.

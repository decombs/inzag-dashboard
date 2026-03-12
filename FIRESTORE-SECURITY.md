# Firestore Security Guide

## Current Risk

Your Firestore database is likely in **test mode**, which means anyone with the Firebase API key (visible in the HTML source) can read and write all data. This is fine for development but dangerous for production.

## Step 1: Enable Anonymous Authentication

This is the simplest approach — it doesn't require user accounts but prevents unauthenticated access.

1. Go to [Firebase Console](https://console.firebase.google.com/) > your project (`inzag-dashboard`)
2. Click **Authentication** in the left sidebar
3. Click **Sign-in method** tab
4. Enable **Anonymous** sign-in
5. Click **Save**

## Step 2: Add Anonymous Auth to the Dashboard

In `index.html`, after the Firebase initialization, add:

```javascript
import { getAuth, signInAnonymously } from 'https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js';

const auth = getAuth(app);

// Sign in anonymously before accessing Firestore
await signInAnonymously(auth);
```

This should be called in the `loadFromFirebase()` function or in the initialization block, before any Firestore reads/writes.

## Step 3: Set Firestore Security Rules

Go to Firebase Console > Firestore Database > **Rules** tab, and replace the rules with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    // All collections: require authentication
    match /projects/{docId} {
      allow read, write: if request.auth != null;
    }
    match /todos/{docId} {
      allow read, write: if request.auth != null;
    }
    match /lois/{docId} {
      allow read, write: if request.auth != null;
    }
    match /ecas/{docId} {
      allow read, write: if request.auth != null;
    }
    match /banks_epcf/{docId} {
      allow read, write: if request.auth != null;
    }
    match /banks_packager/{docId} {
      allow read, write: if request.auth != null;
    }

    // Changelog: append-only (no one can edit or delete entries)
    match /changelog/{docId} {
      allow read: if request.auth != null;
      allow create: if request.auth != null;
      allow update, delete: if false;
    }
  }
}
```

Click **Publish** to apply.

## What This Achieves

- **Anonymous Auth** = any visitor to the dashboard gets a temporary Firebase identity
- **Security Rules** = only authenticated requests can read/write data
- **Changelog protection** = audit trail entries cannot be modified or deleted
- **API key exposure** = no longer a risk (the key alone isn't enough without auth)

## Optional: Restrict to Known Users

For tighter security, you could use Firebase Custom Claims or Email/Password auth. But for a small internal team, anonymous auth + password gate is a practical solution.

## Testing

After applying rules:
1. Open the dashboard and log in normally — should work
2. Open a new incognito window and try accessing Firestore directly via the API key — should be denied
3. Check the Activity tab — changelog entries should appear and be uneditable

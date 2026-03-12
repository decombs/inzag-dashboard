# How to Add Users

Quick guide for adding new people to the dashboard.

---

## How Passwords Work Now

Passwords are stored as **SHA-256 hashes** (not plain text). This means:
- Even if someone reads the source code, they can't see the actual passwords
- You use a browser console tool to generate the hash for a new password
- Each user also has a **role**: `editor` (can change data) or `viewer` (read-only)

---

## Adding a New User

### Step 1: Generate the Password Hash

1. Open the dashboard in your browser
2. Log in as an editor
3. Open the browser console (press `F12`, then click "Console" tab)
4. Type this command and press Enter:

```
generatePasswordHash('sarah2025')
```

5. The console will print something like:
```
Hash for "sarah2025":
a1b2c3d4e5f6...  (64-character string)
Add to USER_MAP: 'a1b2c3d4e5f6...': { name: 'New User', initials: 'NU', role: 'editor' },
```

6. Copy the full line it suggests

### Step 2: Add to USER_MAP

1. Open `index.html` in a text editor
2. Find the `USER_MAP` section (search for "USER_MAP")
3. Add the new line:

```javascript
const USER_MAP = {
  '3242343d0ff...': { name: 'Leandro Fernandez', initials: 'LF', role: 'editor' },
  '68ccae2140...': { name: 'Achim Becker', initials: 'AB', role: 'editor' },
  'a1b2c3d4e5...': { name: 'Sarah Schmidt', initials: 'SS', role: 'editor' },  // NEW
};
```

4. Save the file
5. Upload to GitHub (push) or wherever you're hosting it
6. Tell Sarah her password: `sarah2025`

---

## Roles

- **`editor`** — Full access: can add, edit, delete projects, tasks, and LoIs
- **`viewer`** — Read-only: can see everything but cannot make changes

To add a view-only user, set `role: 'viewer'` instead of `role: 'editor'`.

---

## Changing an Existing Password

1. Generate a hash for the new password using `generatePasswordHash('newpassword')`
2. Replace the old hash key in USER_MAP with the new one
3. Save and upload

The user will need to clear their browser data (or use incognito) to log in fresh.

---

## Tips

- **Keep passwords simple** — something like `firstname2025` works fine
- **Don't use special characters** in passwords (stick to letters and numbers)
- **The comma matters!** Each line except the last one needs a comma at the end
- **Case sensitive:** `Demo` and `demo` are different passwords
- **Test in incognito** after adding a new user to verify it works

---

## Security Note

Passwords are now hashed with SHA-256. Even if the source code is public on GitHub, attackers cannot easily recover the original passwords. However, for best security:
- Use passwords that are at least 8 characters
- Don't reuse important personal passwords
- Consider enabling Firebase Anonymous Auth (see FIRESTORE-SECURITY.md)

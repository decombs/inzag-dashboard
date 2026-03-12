# Dashboard password (when hosted online)

When the dashboard is opened from a **website** (e.g. https://www.inzag.de/dashboard/), a password screen is shown. The data (projects, to-dos) is **encrypted** in the browser; without the password, the content cannot be read even if someone views the page source or the stored data.

---

inzag2025 → logs in as Leandro Fernandez (LF)
achim123 → logs in as Achim Becker (AB)
demo → logs in as Demo User (DU)


Share this only with people who should see the dashboard. They enter it once per browser session (or per page load, depending on use).

---

## Changing the password

The password is checked using a **hash** (the code never stores the actual password). To set your own password:

1. Open the dashboard in the browser (after entering the current password).
2. Open the **browser console** (F12 or right‑click → Inspect → Console).
3. Run this (replace `YourNewPassword` with your desired password):

   ```javascript
   (async () => {
     const p = prompt('Enter new password');
     if (!p) return;
     const h = Array.from(new Uint8Array(await crypto.subtle.digest('SHA-256', new TextEncoder().encode(p)))).map(b => b.toString(16).padStart(2, '0')).join('');
     localStorage.setItem('inzag_pw_hash', h);
     alert('Password updated. From the next login, use the new password.');
   })();
   ```

4. From the next time someone opens the page, they must use the **new** password. The old one no longer works.

---

## Local use (no password)

When you open **index.html** **from your computer** (double‑click or `file://`), the password screen is **not** shown and data is stored normally (no encryption). Password and encryption apply only when the page is loaded from **http** or **https** (e.g. on inzag.de).

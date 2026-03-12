# Host the dashboard on www.inzag.de (WordPress)

With access to WordPress on inzag.de, you can put the dashboard on your own site. Then you share a link like **https://www.inzag.de/dashboard/** or **https://www.inzag.de/projects/** and it opens in the browser (no download).

**Password protection:** When the dashboard is opened from a website (https), a **password screen** is shown. The data is **encrypted** in the browser, so even if someone views the page source or the stored data, they cannot read the projects/to-dos without the password. Default password: **INZAG-Pipeline**. See **PASSWORD.md** in this folder for details and how to change it.

---

## Option 1 – Upload the file (simplest)

You only need to get **index.html** onto the server so the site can serve it as a normal page.

### A) Via WordPress Media Library (if your host allows .html)

1. In WordPress admin, go to **Media** → **Add New**.
2. Upload **index.html** from your Pipeline dashboard folder.
3. After upload, click the file and copy the **File URL** (e.g. `https://www.inzag.de/wp-content/uploads/2025/02/index.html`).
4. **Share that URL.** It should open the dashboard in the browser.  
   If your host blocks .html uploads, use Option B.

### B) Via hosting File Manager or FTP (most reliable)

1. Log in to your **hosting control panel** (where you manage inzag.de – e.g. cPanel, Plesk, or your host’s “File Manager”).
2. Go to the **web root** of the site (often `public_html` or `www` or the folder that contains `wp-admin`).
3. Create a new folder, e.g. **dashboard** or **projects** (so the URL is clean).
4. Upload **index.html** into that folder.
5. The dashboard will be at:
   - **https://www.inzag.de/dashboard/**  
   or  
   - **https://www.inzag.de/dashboard/index.html**  
   (depending on server config; many servers show `index.html` when you open `/dashboard/`).
6. **Share that link** (e.g. https://www.inzag.de/dashboard/). It opens in the browser.

---

## Option 2 – Link from the inzag.de menu

After the dashboard is online (Option 1):

1. In WordPress, go to **Appearance** → **Menus** (or **Appearance** → **Customize** → **Menus**).
2. Add a **Custom Link**:
   - **URL:** `https://www.inzag.de/dashboard/` (or the exact URL you used above).
   - **Link text:** e.g. “Projects Dashboard” or “Pipeline”.
3. Add it to the menu and save. Visitors can then open the dashboard from your site.

---

## Option 3 – WordPress page that redirects (if you can’t upload .html)

If you **cannot** upload .html (e.g. host blocks it and you have no FTP/File Manager):

1. Create a new **Page** in WordPress (e.g. “Projects Dashboard”).
2. In the page content, add a **Custom HTML** block with only this (replace the URL with your real dashboard URL if it’s different):

   ```html
   <p><a href="https://www.inzag.de/dashboard/">Open the Projects Dashboard</a></p>
   <script>window.location.href = "https://www.inzag.de/dashboard/";</script>
   ```

3. Publish the page.  
   This redirects people to the dashboard. The dashboard itself must still be available at that URL (so you still need Option 1A or 1B to put **index.html** somewhere).

---

## Summary

| Step | Action |
|------|--------|
| 1 | Upload **index.html** via **Media** (if allowed) or **File Manager / FTP** into a folder like `dashboard`. |
| 2 | Get the URL (e.g. **https://www.inzag.de/dashboard/** or **.../dashboard/index.html**). |
| 3 | Open that URL in the browser to confirm the dashboard loads. |
| 4 | Share that link; optionally add it to the site menu (Option 2). |

Once the file is on the server at inzag.de, the link will open in the browser like your local version (no download).

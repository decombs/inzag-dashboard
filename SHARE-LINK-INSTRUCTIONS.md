# How to get an actual link to the dashboard file

"Copy link" / "Share" in OneDrive and SharePoint usually gives you a **special viewer URL** (preview page, login redirect, etc.), not the **actual file URL** that opens the dashboard in the browser. Below is how to get the **real file link**.

---

## Your format (agzagope-my.sharepoint.com / OneDrive)

If your link looks like this (folder view with `?id=...&viewid=...`):

`https://agzagope-my.sharepoint.com/my?id=%2Fpersonal%2Fleandro%5Ffernandez%5Finzag%5Fde%2FDocuments%2FAdmin%20Fin&viewid=...`

**Do this:**

1. Take the **host**: `agzagope-my.sharepoint.com`
2. Take the **path** from the `id` parameter (decode it in your head):
   - `%2F` = `/`
   - `%5F` = `_`
   - `%20` = space  
   So `%2Fpersonal%2Fleandro%5Ffernandez%5Finzag%5Fde%2FDocuments%2FAdmin%20Fin` →  
   `/personal/leandro_fernandez_inzag_de/Documents/Admin Fin`
3. Build the **direct file URL** by putting host + path + the filename:
   - **Direct link to the dashboard (index.html in "Admin Fin"):**  
     **`https://agzagope-my.sharepoint.com/personal/leandro_fernandez_inzag_de/Documents/Admin%20Fin/index.html`**
4. Use that URL as the link. When people open it (signed in to Microsoft 365), the dashboard opens in the browser.

**If Chrome (or the browser) downloads the file instead of opening it:**  
Microsoft often sends HTML with "download" behavior. Try these links in order:

- Add **`?download=0`** at the end:  
  `https://agzagope-my.sharepoint.com/.../Admin%20Fin/index.html?download=0`
- If it still downloads, try **`?web=1`**:  
  `https://agzagope-my.sharepoint.com/.../Admin%20Fin/index.html?web=1`

If both still trigger a download, the server is set to force-download HTML. Use the **"Host the file elsewhere"** section below so the link opens in the browser.

**Rule for any folder:**  
If your folder URL has `id=%2Fpersonal%2F...%2FDocuments%2FYourFolderName`, then the **actual link to the dashboard** is:

`https://agzagope-my.sharepoint.com/personal/leandro_fernandez_inzag_de/Documents/YourFolderName/index.html`

(Use `%20` for spaces in the folder name, e.g. `Admin%20Fin`.)

---

## Option A – SharePoint: get the direct file path, then add ?web=1

1. Open your **SharePoint** site and go to the **document library** where **index.html** is stored.
2. Find **index.html** in the list. Click the **three dots (…)** next to it.
3. Click **Details** (or **View details**). A panel opens on the right.
4. In the panel, click **More details** (or look for **Path**).
5. Find the **Path** field. It looks like:  
   `https://yourcompany.sharepoint.com/sites/SiteName/Shared%20Documents/index.html`  
   Click the path to **copy** it (or select and copy).
6. **Paste the link somewhere** (e.g. Notepad). At the **end** of the URL, add:  
   **`?web=1`**  
   So the full link is:  
   `https://yourcompany.sharepoint.com/sites/.../index.html?web=1`  
   The `?web=1` tells SharePoint to **open the file in the browser** instead of downloading it.
7. **Use this final link** when you share with people (email, Teams, intranet). When they open it, they should see the dashboard in the browser.

**If you don’t see "Details" or "Path":**  
- Try right‑clicking the file → **Open in new tab**. When the dashboard (or a preview) opens, look at the **address bar**. The URL might be the direct file URL; copy it and add **?web=1** at the end, then use that as the link.

---

## Option B – OneDrive: open in browser, then copy the URL

1. Open **OneDrive** in your browser and go to the folder where **index.html** is.
2. **Right‑click** on **index.html**.
3. Choose **Open in browser** or **Preview** (wording may be "Open" or "View in browser").
4. The dashboard should open in a new tab. The **address bar** now shows the **actual file URL** (e.g. `https://...sharepoint.com/.../index.html` or similar).
5. **Copy that URL** from the address bar (Ctrl+C or Cmd+C). This is the **real link** to the file.
6. **Share this URL** with your team. When they open it (and are signed in if your org requires it), they get the dashboard in the browser.

**If "Open in browser" isn’t there:**  
- Click **index.html** once so it opens in the OneDrive preview. Then check the address bar: sometimes the URL can be edited to remove extra parameters. Copy the base URL (up to and including `index.html`) and try that as the link.

---

## Option C – Build the link from the folder URL (SharePoint or OneDrive)

1. In **SharePoint** or **OneDrive**, open the **folder** that contains **index.html** (don’t open the file).
2. Look at the **address bar**. The URL might look like:  
   `https://yourcompany.sharepoint.com/.../Documents/Projects%20dashboard`  
   or  
   `https://...-my.sharepoint.com/.../Documents/Projects%20dashboard`
3. At the **end** of that URL, add:  
   **`/index.html`**  
   So you get:  
   `https://.../Documents/Projects%20dashboard/index.html`
4. For **SharePoint**, add **`?web=1`** at the very end:  
   `https://.../Documents/Projects%20dashboard/index.html?web=1`
5. Open that full URL in a new tab. If the dashboard loads, that’s your **actual link** — use it when sharing.

---

## If the link still downloads: host the file somewhere that opens in the browser

When OneDrive/SharePoint always sends the file as a download, use a **free host** that serves HTML as a page. Then share **that** link — it will open the dashboard in the browser.

### Option 1 – GitHub Gist (no account needed to view; you need a free GitHub account to create)

1. Go to **https://gist.github.com** and sign in (or create a free account).
2. In **Filename**, type: `index.html`
3. Open your **index.html** from the Pipeline dashboard folder in a text editor (e.g. Notepad, VS Code). Select **all** (Ctrl+A / Cmd+A), **copy** (Ctrl+C / Cmd+C).
4. Paste the full content into the big text area on the Gist page.
5. Click **Create public gist**.
6. On the next page, click **Raw** (top right). The browser will show the raw HTML or open it. Copy the **URL from the address bar** — it looks like:  
   `https://gist.githubusercontent.com/username/abc123.../raw/.../index.html`
7. **Share that URL.** When people open it, the dashboard loads in the browser (no download). Data is stored in their browser as before.

**To update the dashboard later:** Edit the Gist, paste the new HTML, save. The same Raw URL will show the new version.

### Option 2 – Netlify Drop (no account for a quick test)

1. Go to **https://app.netlify.com/drop**
2. Drag and drop your **Pipeline dashboard folder** (the one that contains **index.html**) onto the page.
3. Netlify will give you a link like `https://random-name-123.netlify.net`. That link **opens the dashboard in the browser**.
4. Share that link. (Free tier may have limits; for long-term use you can create a free account and keep the site.)

---

## Quick summary

| Where the file is | How to get the actual link |
|-------------------|----------------------------|
| **SharePoint**    | Three dots → **Details** → **Path** → copy → add **?web=1** at the end. |
| **OneDrive**     | Right‑click file → **Open in browser** → copy the URL from the address bar. |
| **Either**        | Open the **folder** in the browser, copy the folder URL from the address bar, add **/index.html** (and for SharePoint add **?web=1**). |

The link you want always points **directly to the file** (it ends with `index.html` or `index.html?web=1`), not to a SharePoint/OneDrive “view” or “share” page.

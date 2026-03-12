# Sovereign Projects Dashboard

A single-page dashboard for tracking finance projects across 3 countries: projects, progress, and next-step to-dos. No server needed—runs in your browser and saves data locally. Works on your computer or on **SharePoint (Office 365)**.

---

## How to use it

1. **Open the dashboard**  
   Double-click `index.html` to open it in your browser (Chrome, Edge, or Safari).

2. **Rename the 3 countries**  
   The default names are "Country 1", "Country 2", "Country 3". Click each name at the top of its tab and type your real country names (e.g. Kenya, Nigeria, Ghana).

3. **Add projects**  
   In each country tab, click **"+ Add project"** and enter the project name. You can add as many projects per country as you need.

4. **Set progress**  
   Use the slider under each project (0–100%) to show how far along it is. The bar turns green when at 100%.

5. **Add next steps / to-dos**  
   Click **"+ Next step"** for a quick to-do, or use the form at the bottom of the "Next steps" card. You can optionally link a to-do to a project (choose from the dropdown). Tick the box next to a to-do when it’s done.

6. **Overview**  
   The cards at the top summarize each country: number of projects, average progress, and to-dos done. Click a card to jump to that country’s tab.

**Where is my data stored?**  
In your browser (localStorage). So:
- On your PC: data stays in that browser on that computer.
- On SharePoint: data stays in the browser of whoever is viewing the page (each person has their own copy unless you later connect it to a shared list).

---

## Share with a link (use OneDrive so it opens in the browser)

You only need **one file**: `index.html`. **Use OneDrive** (not a SharePoint document library) so the link opens in the browser — see **SHARE-LINK-INSTRUCTIONS.md** in this folder for full steps.

### Step 1 – Open your SharePoint site

1. In your browser, go to your company’s SharePoint site (e.g. **https://yourcompany.sharepoint.com** or the link your IT gave you).
2. Sign in with your Office 365 / work account if asked.

### Step 2 – Upload the dashboard file

1. On the SharePoint site, click **Documents** in the left menu (or **Documents** under “Quick launch”).  
   If you don’t see it, click **Site contents**, then open the **Documents** library.
2. Click **Upload** → **Files** (or drag and drop).
3. Choose the **index.html** file from your **Pipeline dashboard** folder (on your Desktop).
4. Wait until the upload finishes. You should see **index.html** in the list of documents.

### Step 3 – Share the link with your team

1. Click the **three dots (…)** next to **index.html**, or right‑click the file.
2. Click **Copy link** (or **Share**).
3. Choose who can use the link (e.g. “People in INZAG” or “Anyone with the link”, depending on your policy).
4. Copy the link and send it by email or Teams to whoever should use the dashboard.

### Step 4 – Open the dashboard

- You or your colleagues open that link in a browser (Chrome, Edge, or Safari).  
- The dashboard will open and work like on your computer.  
- Each person’s data (projects, progress, to-dos) is stored in their own browser.

---

### Optional: Put the dashboard on a SharePoint page

If you want the dashboard to appear **inside** a normal SharePoint page (instead of opening the file directly):

1. Upload **index.html** as in Steps 1–2 above.
2. Click the **three dots** next to **index.html** → **Copy link**. Paste the link somewhere (e.g. Notepad) and keep it.
3. On your SharePoint site, go to **Site contents** → **Site pages** → **New** → **Blank page**. Give the page a name (e.g. “Projects Dashboard”) and click **Create**.
4. On the new page, click **Edit** (top right).
5. Click the **+** to add a section, then look for **Embed** or **Code** (the name depends on your SharePoint version).
6. If you see **Embed**:
   - Choose **Embed** → **Code** (or “Add an embed”).
   - Paste this (replace `PASTE-YOUR-LINK-HERE` with the link you copied in step 2):

   ```html
   <iframe src="PASTE-YOUR-LINK-HERE" width="100%" height="800" title="INZAG Projects Dashboard"></iframe>
   ```

7. Click **Insert** or **Apply**, then **Publish** (or **Republish**) so others can see the page.

---

**If something doesn’t work:** Some companies block opening HTML files from SharePoint. If the link opens but the page is blank or downloads the file instead of showing the dashboard, ask your IT department to allow opening `.html` files in the browser from that document library, or use the “Optional” method above so the dashboard is embedded in a normal SharePoint page.

---

## Files

- **index.html** – The whole dashboard (HTML, CSS, and JavaScript in one file). This is the only file you need to upload to SharePoint. Logo and your photo are loaded from the INZAG website.

No install, no database, no coding required. Edit country names and add projects and to-dos directly in the page.

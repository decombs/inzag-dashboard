# SharePoint lists setup (shared storage for the dashboard)

So that **everyone sees the same projects and to-dos**, the dashboard can use two SharePoint lists on the **same site** where the dashboard is hosted. Create the lists once; then all users who open the dashboard from that site will load and save from these lists.

**Important:** The dashboard must be **opened from that SharePoint site** (e.g. from a document library or page on the site). The URL must contain your SharePoint domain (e.g. `...sharepoint.com/sites/YourSite/...`). Then the script can read/write the lists on the same site.

---

## Step 1 – Create the lists on your SharePoint site

1. Open your **SharePoint site** (the one where you will host or link to the dashboard).
2. Click **Settings** (gear icon) → **Site contents** → **New** → **List** (or **App**).
3. Create **two** lists with these exact names (so the dashboard finds them):
   - **DashboardProjects**
   - **DashboardTodos**

---

## Step 2 – Add columns to **DashboardProjects**

1. Open the **DashboardProjects** list.
2. Click **Settings** (gear) → **List settings** (or add columns from the list view).
3. Under **Columns**, add these columns (if not already there):

| Column name   | Type        | Required |
|---------------|-------------|----------|
| CountryId     | Single line of text | No  |
| SizeMillion   | Number      | No  |
| Status        | Single line of text | No  |
| Client        | Single line of text | No  |
| Progress      | Number      | No  |
| OurId         | Single line of text | No  |

- **Title** already exists (use it for the project name). Do not delete it.
- For **Number** columns (SizeMillion, Progress), you can set decimal places to 0 or 2 as you prefer.

---

## Step 3 – Add columns to **DashboardTodos**

1. Open the **DashboardTodos** list.
2. Add these columns:

| Column name   | Type        | Required |
|---------------|-------------|----------|
| CountryId     | Single line of text | No  |
| Done          | Yes/No      | No  |
| ProjectId     | Single line of text | No  |
| OurId         | Single line of text | No  |

- **Title** already exists (use it for the to-do text). Do not delete it.

---

## Step 4 – Permissions

- Give **Edit** (or **Contribute**) permission to everyone who should add or change projects and to-dos.
- The dashboard uses the **current user’s** login to call SharePoint; no extra app registration is needed as long as the page is opened from the same site.

---

## Step 5 – Put the dashboard on the same site

- Upload **index.html** to a **document library** on **this same SharePoint site** (or link to it from a page on this site).
- When users open the dashboard from a URL like  
  `https://yourtenant.sharepoint.com/sites/YourSite/Shared%20Documents/dashboard/index.html`  
  the script will:
  - **Load** projects and to-dos from **DashboardProjects** and **DashboardTodos**.
  - **Save** every change (new to-do, progress, new project, etc.) back to these lists.

So changes made by one user are stored in SharePoint and appear for everyone who opens the dashboard from that site.

---

## Troubleshooting

- **“SharePoint load failed” in the browser console**  
  Check that the two lists exist with the **exact** names **DashboardProjects** and **DashboardTodos**, and that the column names match (CountryId, OurId, etc.).

- **Data not shared**  
  Make sure everyone opens the dashboard from a URL on the **same** SharePoint site (same `/sites/YourSite/...`). If some open from OneDrive or another site, they will not use these lists.

- **Saving fails**  
  Ensure the current user has **Edit** permission on both lists.

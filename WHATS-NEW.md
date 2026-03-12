# What's New — Dashboard v2.0

**Updated:** February 2026

---

## 🎉 Major Upgrades

### 1. **Firebase Integration — Shared Data in Real-Time**

Everyone now sees the same projects and tasks! When someone updates a project or marks a task done, it syncs instantly to everyone else's dashboard.

**What this means:** No more "everyone has their own copy." The data is stored in the cloud (Firebase) and shared across the team.

### 2. **Multi-User Password System**

Each person has their own password, and your name appears in the top-right corner when you log in.

**Current passwords:**
- `inzag2025` → Leandro Fernandez
- `achim123` → Achim Becker
- `demo` → Demo User

**To add more users:** Edit the `USER_MAP` in the HTML file (lines ~400-404) and add more password → name mappings.

### 3. **Stay Logged In**

Enter your password once, and you're logged in until you clear your browser data. No need to re-enter it every time.

### 4. **Pipeline Tab — See All Deals Across All Countries**

Click "📊 Pipeline" at the top to see a kanban board with all projects organized by deal stage:
- Origination → Feasibility → Structuring → Financial Close → Construction → Completed

**Each column shows:**
- Number of projects in that stage
- **Total €M value** (the subtotal you requested!)
- Project cards with country flag, name, size, and client

This is your company-wide deal pipeline view.

### 5. **All Tasks Tab — Company-Wide To-Do List**

Click "✓ All Tasks" to see every open task across all countries in one table.

No more jumping between country tabs to find what needs to be done. Sort by country, owner, or due date.

### 6. **6 Deal Stages (Instead of 4)**

The old generic statuses (Planning, In Progress, Completed, On Hold) have been replaced with export finance-specific stages:

1. **Origination** — New lead, first contact
2. **Feasibility** — Technical/financial analysis
3. **Structuring** — ECA application, terms negotiation
4. **Financial Close** — Contracts signed, funds committed
5. **Construction** — Disbursement, work ongoing
6. **Completed** — Project delivered

### 7. **Export Finance Fields Added to Projects**

Each project now has fields for:
- **ECA** (Export Credit Agency: KfW, UK Export Finance, etc.)
- **Coverage %** (How much the ECA covers, e.g., 85%)
- **Tenor** (Repayment period in years)
- **Financial Close Date**
- **Notes** (Free text for status updates)

*Note: These aren't visible in the UI yet, but they're in the data model. We can add them to the interface next.*

### 8. **Smaller, Africa-Focused Map**

The map now shows only Africa + Germany (removed other continents to save space). Clicking a country still jumps to that country's tab.

---

## 📋 How to Use the New Features

### **Viewing the Pipeline**
1. Click "📊 Pipeline" in the top navigation
2. See all projects organized by stage
3. Each column shows the total €M for that stage at the top

### **Viewing All Tasks**
1. Click "✓ All Tasks" in the top navigation
2. See every open task across all countries
3. Check the box to mark a task done, or click × to delete it

### **Country Tabs Still Work**
- The original country tabs (Germany, Angola, Ghana, Uganda) still work exactly as before
- Click a country name (or the map marker) to see just that country's projects and tasks

---

## 🔐 Logging In

**First time:**
1. Open the dashboard
2. Enter your password (e.g., `inzag2025`)
3. Click "Sign In"

**After that:** You're automatically logged in. Your name appears in the top-right corner.

**To log out:** Clear your browser data (or use incognito mode to test different users).

---

## 🚀 What's Next (Phase 2)

These weren't built yet, but they're on the roadmap:
- Drag-and-drop projects between pipeline stages
- Add due dates and owners directly in the UI (currently they exist in the data but no edit form yet)
- Click a project to see a detail modal with all export finance info, notes, and linked tasks
- Export pipeline report to PDF

---

## 🛠️ Technical Notes

- **Hosted on:** inzag.de or wherever you choose (still a single HTML file)
- **Database:** Firebase Firestore (real-time sync)
- **Backup:** Your old version is saved as `index-backup-[date].html` in the same folder

---

## 💡 Tips

1. **Everyone needs internet** to sync data. If offline, changes are queued and sync when reconnected.
2. **The password system is simple** — it's not full user accounts, just password → name mapping. Good enough for internal use.
3. **Firebase is free** up to 50K reads + 20K writes per day (way more than you'll need).

---

**Questions?** Ask Leandro or just experiment — the old backup file is there if you need to roll back!

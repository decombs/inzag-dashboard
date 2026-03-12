# INZAG Sovereign Projects Dashboard — Assessment & Improvement Plan

**Prepared by:** Leandro Fernandez
**Date:** February 2026
**Purpose:** Internal tool evaluation for company-wide project management and communication

---

## 1. What the Tool Is Today

The Pipeline Dashboard is a **single HTML file** (no server, no installation needed) that tracks INZAG's sovereign infrastructure projects across 4 countries: Germany, Angola, Ghana, and Uganda. It runs entirely in the browser — open the file and it works.

### Current Features

| Feature | What It Does | Status |
|---------|-------------|--------|
| **Country overview cards** | Shows project count, average progress, and to-do completion per country at a glance | Working |
| **Interactive world map** | Click a country marker to jump to its projects | Working |
| **Project table per country** | Lists each project with name, size (€M), status, client, and progress bar | Working |
| **Progress sliders** | Drag a slider to update project completion (0–100%) | Working |
| **To-do / next steps** | Add action items, optionally linked to a specific project, mark as done | Working |
| **4 project statuses** | Planning, In Progress, Completed, On Hold — color-coded | Working |
| **Password protection** | When hosted online (not local), a password gate with AES-256 encryption protects data | Working |
| **SharePoint integration** | Can read/write to SharePoint lists so multiple people share the same data | Working |
| **Multiple hosting options** | Works locally (double-click), on SharePoint, OneDrive, WordPress (inzag.de), GitHub, or Netlify | Documented |
| **Mobile responsive** | Adjusts layout for smaller screens | Basic |
| **INZAG branding** | Company logo, colors, Leandro's profile photo pulled from inzag.de | Working |

### How Data Is Stored

- **Local use (file://):** Plain localStorage in the browser — each person has their own copy.
- **Online (https):** Encrypted localStorage — password required to decrypt.
- **SharePoint:** Shared storage via two SharePoint lists (DashboardProjects, DashboardTodos) — everyone sees the same data.

---

## 2. What's Good About It (Strengths)

**Zero friction deployment.** One HTML file, no install, no database, no IT department needed. This is a huge advantage at a company like INZAG where the team is lean and infrastructure-heavy IT projects would slow things down.

**Relevant to the business.** The tool is already structured around INZAG's actual operating model — country-based project portfolios with export finance deal sizes, client names, and progress tracking. The seed data includes real-world projects (Soyo Airport, Cuchi–Cutato Road, Eastern Corridor Road) that match INZAG's public track record.

**SharePoint-ready.** The SharePoint list integration is genuinely useful — it means you can move from "personal tool" to "team tool" without rebuilding anything. Just create two lists and everyone shares the same data.

**Professional appearance.** Dark theme, clean typography (DM Sans), flag icons, map visualization — this looks like a product, not a spreadsheet. That matters for internal credibility.

---

## 3. What's Missing (Gaps for Your Goals)

Your goals are: **(1) internal communication, (2) project management, (3) company-wide to-do tracking, and (4) making you look good by shipping something useful solo.**

Here's what's missing for each:

### 3a. For Internal Communication

| Gap | Why It Matters |
|-----|---------------|
| **No project details/notes** | People can see "Road Cuchi–Cutato" at 72% but not *what's happening*. There's no place for status updates, milestones, or context. |
| **No timeline or dates** | No start dates, deadlines, or milestones. In export finance, deal timelines (ECA approval, disbursement, construction phases) are everything. |
| **No activity log** | Nobody can see what changed or when. If Achim updates a project, Leandro doesn't know unless they talk. |
| **No export/print view** | Can't generate a one-pager or PDF to share in a management meeting or send to a partner. |

### 3b. For Project Management

| Gap | Why It Matters |
|-----|---------------|
| **No deal pipeline stages** | INZAG projects go through specific stages: origination → feasibility → ECA structuring → financial close → construction → completion. The current "Planning / In Progress / Completed / On Hold" is too generic. |
| **No financial tracking** | Only "size in €M" exists. No breakdown of ECA coverage, local contribution, disbursement status, or budget vs. actual. |
| **No document links** | Can't attach or link to key documents (term sheets, ECA applications, construction contracts). |
| **No responsible person / owner** | No way to assign who's leading each project or task. |
| **No priority or urgency on tasks** | All to-dos look the same. No way to flag critical next steps. |
| **No due dates on tasks** | To-dos have no deadlines, so nothing creates urgency. |

### 3c. For Company-Wide To-Do Tracking

| Gap | Why It Matters |
|-----|---------------|
| **To-dos are per-country only** | No "all company" view. You can't see every open task across all countries in one place. |
| **No filtering or search** | Can't filter by person, priority, due date, or project. |
| **No "My Tasks" view** | Each person should be able to see just their action items. |
| **No notifications** | Nobody gets reminded of overdue or upcoming tasks. |

### 3d. For Looking Good

| Strength | Risk |
|----------|------|
| It already looks professional | But if people use it and find it too limited, it reflects poorly |
| It's impressive you built it solo | But only if it's *actually useful* day-to-day |
| Zero-install is great | But the localStorage limitation (each browser = separate data) will confuse people unless SharePoint is set up |

---

## 4. Recommended Improvements (Prioritized)

### Phase 1 — Quick Wins (make it useful this week)

These changes keep the single-file approach and don't require any new infrastructure.

1. **Add a "Company Overview" tab** — Show ALL projects across all countries in one table, sortable by status, progress, or size. Add an "All Open Tasks" section below it. This is the #1 thing that makes it feel like a real management tool.

2. **Add due dates to tasks** — A simple date picker next to each to-do. Color-code overdue items in red. This alone creates accountability.

3. **Add an "Owner" field to tasks** — A text field for who's responsible. Even without login, just typing "Achim" or "Leandro" makes it clear who does what.

4. **Add INZAG-specific pipeline stages** — Replace the 4 generic statuses with stages that match your actual workflow: Origination → Feasibility → ECA Structuring → Financial Close → Under Construction → Completed → On Hold.

5. **Add a notes/comments field per project** — A simple text area where someone can write "Waiting for KfW response" or "Site visit scheduled March 15." This is the cheapest way to enable internal communication.

### Phase 2 — Make It Sticky (next 2–4 weeks)

6. **Add a project detail view** — Click a project name to expand/open a detail card with: notes, linked tasks, key dates (start, expected completion), document links, and responsible person.

7. **Add task filtering** — Filter by: owner, country, project, status (open/done), overdue. This makes the "All Tasks" view actually usable.

8. **Add a simple activity log** — Every time someone adds/edits/completes something, log it with a timestamp. Show the last 20 activities on the overview page. ("Leandro marked 'Site survey' as done — 2 hours ago.")

9. **Add priority levels to tasks** — High / Medium / Low with color coding. High-priority items float to the top.

10. **Add a dashboard summary bar** — Total portfolio value (€M), number of active projects, overdue tasks, completion rate. One glance = full picture.

### Phase 3 — Professional Polish (month 2+)

11. **Export to PDF** — A "Print Report" button that generates a clean summary for management meetings.

12. **Financial breakdown per project** — ECA amount, local contribution, disbursement %, budget vs. actual.

13. **Gantt-style timeline view** — Visual timeline of all projects showing overlaps and deadlines.

14. **Email digest / notification** — Weekly summary of what changed, what's overdue, what's coming up. (This would require a small backend or integration.)

---

## 5. What NOT to Do

- **Don't switch to a complex framework (React, Angular, etc.)** — The single-file HTML approach is your biggest advantage. Keep it simple.
- **Don't add user accounts yet** — The password gate + SharePoint auth is enough for now. User accounts add massive complexity.
- **Don't try to replace Excel** — This tool is for *visibility and communication*, not detailed financial modeling. Excel stays for the heavy number-crunching.
- **Don't over-design it** — Ship small improvements frequently. Each one is a visible win for you internally.

---

## 6. Technical Notes

- The entire app is ~1,100 lines of HTML/CSS/JS in one file — very manageable.
- Data model is clean: countries → projects → todos, with simple JSON in localStorage or SharePoint lists.
- SharePoint integration uses REST API with same-origin credentials — no app registration needed.
- Encryption uses Web Crypto API (AES-GCM) — solid for browser-side protection.
- The seed data includes realistic INZAG projects which is good for demos but should be replaceable with real data.

---

## 7. Bottom Line

You have a **solid foundation** — a working, professional-looking, zero-install dashboard that's already tailored to INZAG's business. The main gap is that it's currently a *project tracker* but not yet a *project management and communication tool*.

The fastest path to making you look good: **implement Phase 1 items (company overview, due dates, owners, pipeline stages, notes).** These 5 changes transform it from "nice demo" to "tool I actually use every morning." And because it's a single HTML file that anyone can open, the adoption barrier is zero — which is exactly what makes solo-shipped tools succeed in small companies.

# Roadmap Planner Tool (Gantt-based Timeline & Delivery Management)

A **single-file, self-contained HTML Roadmap Planner Tool** — a Gantt-chart-based project timeline viewer, KPI tracker, raw source parser, and interactive visual builder.

Works completely client-side in any modern browser without needing a backend server or complex build tools. All timeline data and configurations persist automatically to `localStorage`.

---

## ⚡ 1-Click / Auto Deploy to Vercel

This repository is pre-configured with `vercel.json` and `public/index.html` for instant Vercel deployment:

1. Go to [vercel.com/new](https://vercel.com/new)
2. Import this repository: **`HuyTruong14/RoadmapForBatch`**
3. Framework Preset: **Other** (Output Directory: `public` is auto-detected via `vercel.json`)
4. Click **Deploy**

Every push to the `main` branch will automatically trigger a new deployment with a permanent production URL!

---

## 🚀 Key Features

### 1. Gantt Chart Timeline
- **Working-days only (Mon–Fri)**: Automatically excludes Saturdays and Sundays from the timeline grid.
- **Collapsible project rows**: View stacked stage bars on master rows, or expand to inspect each stage in detail.
- **Dynamic timeline indicators**:
  - Vertical **"Today" line** (dynamic current day or configurable override).
  - Vertical **"RFP" deadline line** (dashed marker for each project).
  - Alternating subtle day column stripes and clear day-of-week headers (Mon, Tue, etc.).

### 2. KPI Dashboard Strip
- **Total Projects**: Real-time count of tracked projects.
- **On-track**: Count of projects meeting schedules (green badge).
- **Delayed**: Count of off-track or delayed deliverables (red badge).
- **Base RFP**: Common target delivery milestone across projects.

### 3. Three Integrated Modal Panels
1. **⚙️ Settings (`#modal-settings`)**:
   - Customize roadmap title, subtitle, month (1–12), year, start day, end day, and today override.
   - Persisted in `localStorage` under `roadmap_config`.
2. **📝 Edit Source (`#modal-source`)**:
   - Flexible text parser supporting freeform syntax (e.g., `BE (1 day) - ETA: 14.10`, `FE (2 days): 15-16.10`, `QC Testing & Fix Bug BO Tool`).
   - One-click **Load Sample Data** to quickly reset or explore.
   - Persisted in `localStorage` under `roadmap_raw_text`.
3. **🛠️ Timeline Builder (`#modal-builder`)**:
   - Visual form editor to add/edit projects and stages with drag/input ease.
   - Stage types: **BE**, **FE**, **PL/BO**, **QC**, **Integrate**, **Asset**, **Milestone / RFP**.
   - Auto-fills stage titles, manages focus, and supports **Import Current** & **Apply Timeline**.

### 4. Usability & Aesthetics
- **Theme toggle**: Seamless Light mode and Dark mode support (`prefers-color-scheme` and manual toggle).
- **Quick Export & Copy**:
  - **Copy**: Instant Markdown summary copied to clipboard.
  - **Export**: Exports or opens clean standalone HTML for distribution.
- **Real-time Search & Filter**: Filter by project name, project code, or status tabs (All, On-track, Delayed).

---

## 💻 Local Quick Start

### Option 1: Direct File Opening
Double-click `index.html` or open in any web browser:
```bash
open index.html
```

### Option 2: Local HTTP Server
Run a lightweight HTTP server:
```bash
python3 -m http.server 5180
```
Then visit:
```
http://localhost:5180
```

---

## 📁 Repository Structure
```
.
├── public/
│   └── index.html     ← Production asset served by Vercel
├── index.html         ← Root standalone copy
├── package.json       ← Vercel project metadata & serve script
├── vercel.json        ← Vercel routing & cache headers configuration
└── README.md          ← Documentation & deployment guide
```

---

## 🔒 Privacy & Persistence
- **Zero backend required**: 100% client-side execution.
- **Safe data handling**: All inputs are sanitized against XSS before rendering.
- **Local storage keys**:
  - `roadmap_config`: JSON configuration (title, dates, overrides).
  - `roadmap_raw_text`: Raw markdown timeline text.
  - `roadmap_theme`: User theme preference (`light` or `dark`).

# TruckPark Pro – Multi-Location Parking Management

Responsive one-file HTML prototype for multi-location truck parking management with interactive slot map, booking modal, and Google Sheets occupancy sync.

> **This is a front-end prototype.** All data is stored in memory. In production it can be connected to a backend, CRM, payment gateway, and admin dashboard.

---

## Features

- **Multi-location support** – Switch between 4 parking locations from a sidebar or mobile dropdown
- **Interactive parking map** – Top-down satellite-style visualization of parking stalls
- **Live occupancy display** – Green = available, red = occupied, yellow highlight = selected
- **Spot detail panel** – Click any spot to see row, section, dimensions, and availability
- **Booking / registration modal** – Reserve a free spot by entering carrier, driver, plate, trailer, and duration
- **Filter bar** – Show all spots, only available, or only occupied
- **Stats bar** – Real-time counts of available, occupied, and total spots per location
- **Google Sheets CSV sync** – Fetch live occupancy data from a published Google Sheets CSV URL
- **Local demo data fallback** – Deterministic demo data is used when no CSV is configured
- **Toast notifications** – Inline status messages for booking confirmations and sync results
- **Fully responsive** – Works on desktop, tablet, and mobile (collapsible sidebar + bottom drawer)
- **Zero dependencies** – Pure HTML, CSS, and vanilla JavaScript; no build tools or npm

---

## File Structure

```
truck-parking-management-prototype/
├── index.html            # Complete single-file prototype (UI + CSS + JS)
├── sample-occupancy.csv  # Example CSV showing the expected occupancy format
├── README.md             # This file
└── .gitignore            # Excludes OS artifacts (.DS_Store, Thumbs.db)
```

---

## How to Run Locally

No build step is needed. Open `index.html` directly in any modern browser:

```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Windows
start index.html
```

Or serve it with any static server:

```bash
# Python 3
python -m http.server 8080

# Node (npx)
npx serve .
```

Then visit `http://localhost:8080`.

---

## Google Sheets CSV Sync

Occupancy status can be managed through a published Google Sheets document without any backend.

### Setup steps

1. Create a Google Sheet with three columns: `park`, `spot`, `status`
2. Go to **File → Share → Publish to web**
3. Select the sheet, choose **Comma-separated values (.csv)**, and click **Publish**
4. Copy the generated URL
5. In the prototype, click **Sync CSV** in the top-right header
6. Paste the URL and click **Fetch & Sync**

The prototype will fetch the CSV, parse it, and update occupancy for all matching locations and spots instantly.

---

## Expected CSV Format

```csv
park,spot,status
North Freight Yard,A01,1
North Freight Yard,A02,0
South Industrial Depot,B03,1
```

| Column   | Description                                 |
|----------|---------------------------------------------|
| `park`   | Location name — must match exactly           |
| `spot`   | Spot identifier (e.g. `A01`, `C07`)          |
| `status` | `1` = occupied / `0` = available             |

See [`sample-occupancy.csv`](./sample-occupancy.csv) for a complete example covering all four demo locations.

---

## Parking Locations (Demo)

| Location                  | Sections      | Total Spots |
|---------------------------|---------------|-------------|
| North Freight Yard        | A, B, C, D    | 32          |
| South Industrial Depot    | A, B, C       | 24          |
| East Logistics Hub        | A, B, C, D    | 20          |
| West Distribution Center  | A, B, C, D    | 28          |

---

## GitHub Pages Deployment

This prototype is ready for GitHub Pages deployment from the repository root.

1. Push the repository to GitHub
2. Go to **Settings → Pages**
3. Set **Source** to `Deploy from a branch`, select `main` (or your default branch), and choose `/ (root)`
4. Click **Save** — the prototype will be live at `https://<username>.github.io/<repo-name>/`

---

## Future Extensions

This prototype is designed to be the front-end foundation for a production system. Potential next steps:

- Backend API for persistent booking storage
- Authentication and role-based access (dispatcher, driver, admin)
- Payment and invoice integration
- Real-time WebSocket updates for spot status
- Admin dashboard with reporting and analytics
- Native mobile app (PWA or React Native)

---

## Repository Info

**Suggested description:** Responsive one-file HTML prototype for multi-location truck parking management with interactive slot map, booking modal, and Google Sheets occupancy sync.

**Suggested topics:** `html` `css` `javascript` `prototype` `parking-management` `fleet-management` `interactive-map` `google-sheets` `static-site`

**Suggested first commit message:** `Initial commit: add truck parking management prototype`

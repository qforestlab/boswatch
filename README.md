# BosWatch Field Tracker

BosWatch Field Tracker is a lightweight, mobile-first web app for recording Bosland field inspection checks during site visits. It is designed for on-site data collection, incomplete-item review, and CSV export without needing a backend or external database.

## Overview

This project is a single-page application built in plain HTML, CSS, and JavaScript. It lets an operator:

- enter their name
- start a new inspection visit
- work through 8 BOS stations
- complete inspection checklists for LF, BR, HB, and SP sensors
- record moisture values, remarks, and pass/fail status
- review incomplete items before moving forward
- export completed visits as CSV files
- restore a saved in-progress visit from a checkpoint JSON file
- review historical visit records stored in the browser

## Features

### Visit workflow

- Operator entry screen with start/continue flow
- In-progress visit banner when work has already been started
- Station-by-station progress tracking with a visual progress bar and station dots
- Eight BOS station entries with site and location metadata
- Sensor groups with structured checklists and serial number display

### Inspection checks

Each station includes sensor-specific fields such as:

- photo documentation checks
- cleaning and lid checks
- battery replacement checks
- data download completion
- moisture percentage entry
- desiccant replacement
- solar panel inspection
- remarks for notes and context

### Quality controls

- yes/no/N/A answer buttons for individual checks
- high moisture alert for values >= 40%
- blank detection before moving to the next station or exporting
- acknowledgment overlay to confirm incomplete entries before continuing
- confirm dialog for destructive actions such as discarding or deleting data

### Data persistence

- visit state is saved in localStorage
- checkpoint JSON files can be uploaded to restore progress if browser storage is lost
- browser history stores previous exported visits
- an incognito/private mode warning is shown when persistence may not work

### CSV export

Completed visits can be exported to CSV with one click. The export includes:

- export date and time
- operator name
- station date/time
- site and location
- sensor serial numbers
- all checklist values and remarks


## Running the app

This project is a static web page, so there is no build step or package install required.

### Option 1: open directly

Open `index.html` in a browser.

### Option 2: serve locally

From the project folder, run:

```bash
python3 -m http.server 8000
```

Then open in a browser:

```text
http://localhost:8000
```

## Usage

1. Enter the operator name.
2. Click `Start new visit`.
3. Move through each BOS station and complete the required checks.
4. Use `Next station` to advance.
5. If required, acknowledge any incomplete items before proceeding.
6. Use `Export CSV` when the visit is complete.
7. Review exported records from the History tab.

## Notes

- This app is intentionally lightweight and client-side only.
- It is best suited for field use on a laptop or tablet browser.
- Data is stored in the browser, so use a browser that supports localStorage for reliable persistence.
- In private/incognito mode, storage may not persist after the tab is closed.
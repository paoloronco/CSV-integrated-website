# CSV Data Table Demo — Inline & External

Two zero-dependency HTML demos that render a searchable/sortable/paginable CSV table and export the filtered view.

## Structure
```
repo/
├─ inline/
│  └─ index.html          # CSV embedded inside the HTML (no fetch)
├─ external/
│  ├─ index.html          # Loads ./mock-data.csv from the same folder (via fetch)
│  └─ mock-data.csv       # Mock data used by the external demo
└─ README.md
```

## Inline version (`inline/index.html`)
- The CSV is embedded inside:
  ```html
  <script id="csv-data" type="text/plain">
  ID,Name,Category,Price,Link,Status,Owner,Priority,Tags,Created_At,Updated_At,Region,Notes
  1001,Onboarding Campaign,Marketing,€2,500,https://example.com/items/1001,Active,Ada Lovelace,High,"email;welcome",2025-01-15,2025-08-01,EU,Phase 2 live
  <!-- ... -->
  </script>
  ```
- **To customize:** edit the header row to match your columns, then add/replace data rows.  
- If a column is named **`Link`**, values are rendered as clickable links.
- You can open this file by double‑clicking it (no local server required).

## External version (`external/index.html` + `external/mock-data.csv`)
- The page fetches `./mock-data.csv`. The CSV must sit **in the same folder** as `index.html`.
- This version does **not** allow picking a different CSV (no file input, no URL override).

### Run locally (required for fetch)
Browsers block `fetch` when opening files via `file://`. Start a tiny local server from the `external/` folder:
First, rename csv-table-external.html to index.html, so the server serves it automatically.

**macOS / Linux**
```bash
cd external
python3 -m http.server 5500
# then open http://localhost:5500/
```

**Windows (PowerShell)**
```powershell
cd external
python -m http.server 5500
# then open http://localhost:5500/
```

## CSV schema used in the mock
```
ID, Name, Category, Price, Link, Status, Owner, Priority, Tags, Created_At, Updated_At, Region, Notes
```
- Rename/add/remove columns freely; the table renders from the CSV header.
- Sorting is locale‑aware with **numeric** comparison for mixed text+numbers.

## Troubleshooting
- **Failed to fetch (external):** run the local server (`python -m http.server`) or deploy on Pages.
- **Weird characters:** save the CSV as UTF‑8.
- **Quotes/commas inside fields:** keep values quoted; double double‑quotes (`""`) inside quoted fields.

## License
MIT

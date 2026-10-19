# Fiber Bleaching Daily Electricity Consumption – dashboard (GitHub Pages)

Password-protected static dashboard built from the daily KWH report.
The readings in `data.js` are encrypted; the site shows nothing without the password.

## One-time setup
1. Create a GitHub repository (e.g. `ems`). On a free account the site address is public, but the data stays locked by the password.
2. Upload everything from this folder to the repository root (keep the `.github` folder).
3. **Settings → Secrets and variables → Actions → New repository secret**: name `EMS_PASSWORD`, value = the dashboard password (use the same one the current data.js was built with, or any new one – the next update will use it).
4. **Settings → Pages**: Deploy from a branch, branch `main`, folder `/ (root)`, Save.
5. Your link appears at the top of the Pages screen after about a minute.

## Daily update
1. Add the new day in Excel and save the file.
2. In the repository: **Add file → Upload files**, upload `KWH_REPORT.xlsx` (exact name), Commit changes.
3. Wait 2–3 minutes; check **Actions** for a green tick. Refresh the dashboard (Ctrl+F5).

## Privacy
Do not upload `KWH_REPORT.xlsx` to a public repository unless you accept that anyone can download it – the password only protects the dashboard page, not the Excel file.
Use a private repository (needs a paid plan for Pages) or run `build_data.py` on your own computer and upload only `data.js`:
```
pip install openpyxl pandas numpy cryptography
EMS_PASSWORD=yourpassword python build_data.py KWH_REPORT.xlsx
```

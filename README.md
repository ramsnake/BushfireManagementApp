# BushfireManagementApp

# Brigade Activity Hub

A small, device-local demonstration for conversations with volunteer bushfire brigades in regional Western Australia. All initial members and records are fictional.

## Run

Requires Python 3. From this checkout:

```sh
python3 -m http.server 3000 --bind 0.0.0.0
```

Open the app using a browser served from this origin. No package installation, API credentials or database is required. `npm start` runs the same server if Node is available.

The app supports recording incidents, training, maintenance and community activities; selecting crew; calculating attendance hours; saving drafts; submitting for demonstration review; approving records; filtering records; and CSV activity and attendance exports. Use the sample data or add a record with the Record activity button.

## Offline behaviour and limitations

Service workers require HTTPS or localhost. Load the application once while connected and wait for the service worker to install before going offline. Its shell is cached, and records persist in localStorage on the same browser and origin. Reload while offline to exercise this behaviour. Clearing site data removes records. Export CSV files for portable copies; import is not implemented.

This prototype has **no remote synchronisation, accounts, verified officer authorisation, backup service, dispatch or live tracking**. An internet connection does not upload records. Member management is a fixed fictional roster. Approved records are read-only in the UI. Times describe same-day activities in Western Australia; split overnight activities into separate daily records. Summary hours include every status. Exports label their statuses and have an approved-only option. CSV export protects leading formula characters in user-entered spreadsheet cells.

The generic CSV reports are not official DFES or council submissions. Confirm reporting fields, retention, permissions and real brigade workflows before considering operational deployment. Avoid real personal or incident information in this demonstration. The included Python server is for development.

## Validation

`npm test` runs the browser smoke tests when Playwright and Chromium are installed in the development environment. The tests cover saving and reloading records, validation, review, CSV downloads, mobile layout and offline reload. Tests use isolated browser contexts and do not modify a developer's records.

For manual checks: create an incident with crew, submit it, open it under Activity records, approve it, export approved records under Reports & exports, and reload offline. Check the member hours reflect the new attendance.

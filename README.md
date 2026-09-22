# Claim Investigation Case Manager

A single-page tool for health insurance claim investigators: log cases, track
document-collection status (hospital/patient parts, questionnaires, PA/Death
verifications), and auto-generate the Withdrawal Letter and Fraud Letter from
case data. The Employee Info Form and Patient Questionnaire are provided as
downloads of the original PDFs, unedited.

## Project structure

```
claim-investigation-tool/
├── index.html              # the whole app (HTML/CSS/JS, no build step)
├── assets/
│   ├── employee_info_form.pdf
│   └── patient_questionnaire.pdf
└── README.md
```

## Run locally

Just open `index.html` in a browser — no server or build step required.
(Opening via `file://` works, but some browsers restrict clipboard/print
pop-ups on `file://`; a local server avoids that: `python3 -m http.server`
then visit `http://localhost:8000`.)

## Deploy on GitHub Pages

1. Create a new GitHub repository and push this folder's contents to it:
   ```
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. In the repo: **Settings → Pages → Build and deployment → Source** → select
   **Deploy from a branch**, branch **main**, folder **/ (root)** → **Save**.
3. GitHub gives you a URL shortly after
   (`https://<your-username>.github.io/<repo-name>/`).

## Notes

- All case data is stored in the browser's `localStorage`, per-visitor, per-domain.
  Nothing is sent to a server, and nothing is shared between different people
  visiting the page — each investigator's cases stay in their own browser.
- Clearing browser data/localStorage will erase saved cases; there's no
  export/import built in yet.
- "Print / Save as PDF" opens the letter in a new tab and calls the browser's
  print dialog — allow pop-ups for the site if it doesn't open.

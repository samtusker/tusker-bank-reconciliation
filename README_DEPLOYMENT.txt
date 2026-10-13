TUSKER BANK RECONCILIATION — BROWSER BUILD

Files
- index.html: single-page browser app. Uses the existing Supabase project and its public publishable key.
- README_DEPLOYMENT.txt: deployment and security notes.

Included in this update
- Supabase email/password sign-in and role-aware controls (Viewer, Editor, Administrator; role names are case-insensitive).
- Search across transaction fields, status/date/amount filters, sortable headings, and per-column multi-select filters including blank values.
- Select a row to load it into the transaction form; Editor/Administrator can add and update it.
- Archive Cleared items, view archived items, restore checked items, and Administrator-only permanent deletion.
- Duplicate highlighting and duplicate-only view; check/uncheck rows; keyboard Space toggles a focused row checkbox.
- Bank balance, released total and available balance; released amount is derived using the app's Released/future-cheque-month rule.
- Excel export, template download and Excel/CSV import.
- Saved print column layout and separate checkboxes for Current Bank Balance, Total Released Amount, Available Balance, and totals for selected amount columns.
- Responsive layout for phones and tablets; light/dark theme preference is saved in the browser.
- Default Released Amount filter is greater than 20, matching the desktop app's default view.

Important data/security notes
- The app connects to Supabase project wwdcwqedrkvbqgzckamm using the publishable (browser-safe) key. A publishable key is expected to be visible in client code.
- NEVER put a Supabase service_role/secret key in index.html or any static hosting environment.
- Supabase Row Level Security (RLS) must remain enabled and correctly configured on public.transactions, public.settings and public.user_roles. RLS, not the browser interface, is the real security boundary.
- Confirm the policies allow authenticated users to read transactions, Viewer users cannot write, Editor users can insert/update, and only Administrator users can delete. Confirm settings writes are restricted to authorized roles. Test with one account per role before using this with live financial records.
- This package does not migrate, reset, or delete existing Supabase records.

To publish using GitHub Pages (HTTPS static hosting)
1. Download and unzip this package.
2. In your GitHub repository, upload index.html to the repository root and commit it. Keep README_DEPLOYMENT.txt for reference if desired.
3. Open the repository's Settings > Pages.
4. Under Build and deployment, choose Deploy from a branch; select the main branch and /(root), then Save.
5. Wait for GitHub Pages to provide the site URL. Open that URL on desktop and phone and test sign-in, search, editing, archive/restore, import/export and printing.
6. Only share the URL after checking the Supabase RLS policies and testing Viewer, Editor and Administrator accounts.

Deployment status
This is a deploy-ready static package, not a live hosted site yet. Publishing requires an authenticated action in the owner's GitHub account; this workspace has no connected GitHub deployment authorization. No live deployment is claimed.

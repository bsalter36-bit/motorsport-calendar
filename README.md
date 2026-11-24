# Motorsport Calendar

F1, F2, F3 and rally championship dates in one calendar that works on phones and laptops.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app, with all current dates built in |
| `manifest.webmanifest`, `icon-*.png`, `apple-touch-icon.png`, `favicon-32.png` | App name and icons used by "Add to Home Screen" |
| `events.csv` | Every event, ready to import into a Google Sheet (optional, see below) |

## Publish on GitHub Pages

1. In your repository, choose **Add file → Upload files** and drag in every file from this folder.
2. Choose **Commit changes**.
3. Go to **Settings → Pages**, set **Source** to "Deploy from a branch", pick `main` and `/ (root)`, then **Save**.
4. After about a minute the site is live at `https://<your-username>.github.io/<repository-name>/`.

On iPhone, open the link in Safari, tap **Share → Add to Home Screen**. On Android, open it in Chrome and choose **Install app**.

## Optional: edit dates in a Google Sheet

With this set up, anyone you give edit access to the sheet can add or change events, and every viewer sees the change the next time they open the site (allow up to about 5 minutes for Google to publish it). Viewers never need an account.

1. Create a Google Sheet and use **File → Import** to bring in `events.csv`.
2. Choose **File → Share → Publish to web**, pick the sheet tab, choose **Comma-separated values (.csv)**, then **Publish** and copy the link.
3. Open `index.html` in GitHub (pencil icon to edit) and find `CONFIG` near the top of the script:
   - paste the published link into `DATA_URL`
   - paste the sheet's normal editing link into `ADD_EVENT_URL` (this makes the **+** button open the sheet)
4. Commit the change.

### Sheet columns

| Column | Example | Notes |
|---|---|---|
| `catCode` | `BRC` | Code, short name or full name: `WelshRC`, `Welsh` or `Pirelli Welsh Rally Championship` all work |
| `label` | `BRC R2 Jim Clark` | Shown on the calendar |
| `startDate` | `2027-05-28` | `YYYY-MM-DD` is safest; `28/05/2027` also works |
| `endDate` | `2027-05-29` | Leave blank for one-day events |
| `status` | `provisional` | `provisional` shows the event striped; anything else counts as confirmed |
| `note` | `Date announced, round TBC` | Optional, shown in the event details |

Rows the site can't read are skipped, and the count appears under **Series → Dates** so you can fix them. If the sheet can't be reached, the site shows the last copy it loaded, or the dates built into `index.html`.

## Adding a new championship

Find `CHAMPIONSHIPS` near the top of the script in `index.html` and add a line with a code, full name, short name, colour and text colour, following the existing lines.

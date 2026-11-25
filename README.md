# Content Path Checker (MKCL): shared team version

For courses where Hindi and Marathi videos translated by CrossLingua are being added in CDP.
Everyone who opens the Netlify link sees the same courses, reports and stored report files.

## What's in this folder

| File / folder | Purpose |
|---|---|
| `public/index.html` | The web page |
| `netlify/functions/api.mjs` | Small server that saves the shared data (Netlify Blobs) |
| `netlify.toml`, `package.json` | Settings Netlify reads when it deploys |

> Do **not** use Netlify's drag-and-drop ("Upload your project files") deploy. It does not deploy the server part, so data would only be saved in each person's browser.

---

## ⚠️ Saving Netlify credits (important)

The free plan has **300 credits a month**. **Every deploy costs 15 credits**, and **every GitHub commit causes a deploy**. That means about **20 updates a month** at most.

- Put **all changed files into ONE commit** (see "Updating the site" below). Never commit files one by one.
- **Don't delete a file before uploading its new version.** Uploading a file with the same name in the same folder replaces it.
- Don't make test edits on GitHub. Each one is a deploy.
- If credits run out, the site is paused until the next month. Take a backup regularly (🧰 Backup & more tools → Download backup).

---

## Step 1: Put the files on GitHub (one commit)

1. Sign in at **github.com** → **+** (top right) → **New repository**.
2. Name it, e.g. `content-path-checker-v2`, choose **Private**, and **don't** tick "Add a README". Click **Create repository**.
3. On the empty repository page, click **"uploading an existing file"**.
4. Unzip `content-path-checker-netlify.zip`. Open the extracted folder, select **everything inside it** (`netlify`, `public`, `netlify.toml`, `package.json`, `README.md`), and drag it onto the GitHub page from **File Explorer** (not "choose your files").
5. Check the list shows `netlify/functions/api.mjs` and `public/index.html`, then click **Commit changes**.

## Step 2: Create the site on the new Netlify account

1. Sign in to the new Netlify account → **Add new project** → **Import an existing project** → **GitHub**.
2. Allow Netlify to access the new repository (**Only select repositories** → pick it → **Install**).
3. Select the repository. The settings fill in automatically:
   - Branch `main`, Base directory *(empty)*, Publish directory `public`, Functions directory `netlify/functions`.
4. Click **Deploy** and wait for **Published**.
5. Optional: **Project configuration → Change project name**, e.g. `mkcl-content-path-checker`.
6. Open the link and check the top right says **● Shared with your team**.

## Step 3: Bring your data back

The data from the old site stays with the old site. It doesn't move automatically.

- **If you have a backup file** (`content_path_backup_….json`): on the new site, open **🧰 Backup & more tools → Restore from backup** and choose it. All languages and courses come back, with their original files.
- **If the old site is paused and you have no backup:** either upload the content path reports again on the new site, or wait until the old site's credits reset next month, then download a backup from it and restore it on the new site.

## Optional: team passcode

New site → **Project configuration → Environment variables → Add a variable**: key `TEAM_PASSCODE`, value: your passcode.
It applies from the **next** deploy. Add it **before** Step 2's deploy (or together with your next update) to avoid spending an extra deploy.

---

## Updating the site later (one commit = one deploy)

1. Open your repository on GitHub's main page.
2. Click **Add file → Upload files**.
3. Drag in the changed files **with their folders**. For example, drag the `public` folder and the `netlify` folder from the new package. GitHub replaces files that have the same name and path.
4. Check the paths in the list (`public/index.html`, `netlify/functions/api.mjs`), then click **Commit changes** once.
5. Netlify redeploys once. Wait for **Published**, then press **Ctrl+F5** on the site.

Your saved courses are not affected by updates.

## Notes

- Each language (English, Hindi, Marathi, …) has its own list of saved courses. Add languages with **+ Add language**.
- **📊 Common videos report:** one consolidated report of videos found in 2 or more courses, for one language or all languages, downloadable as Excel.
- The page checks for others' changes every 5 minutes, and when you come back to the tab. Click **↻ Refresh** to check right away.
- Original report files up to 3.5 MB are stored. For bigger files only the content paths are saved.

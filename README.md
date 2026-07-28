# masonclement.com

My portfolio site. Plain HTML/CSS/JS — no build tools needed to edit it.

## Updating the live site

Every time you make changes and want them to show up
on masonclement.com, open a terminal in this folder and run:

```
git add .
git commit -m "describe what you changed"
git push
```

That's it. Render watches the GitHub repo and rebuilds the live site
automatically within a minute or two of every push to `main`.

## Adding a new certificate

1. Drop the file into `/Certificates` — PNG or JPG, since PDFs don't preview
   reliably inline. If you want a "Download" button to show up on it too,
   put a PDF with the **exact same filename** (just a different extension)
   in the same folder.
2. Run:
   ```
   node scripts/build-certificates.js
   ```
3. Commit and push like above (`git add .`, `git commit -m "..."`, `git push`).

Both the homepage carousel and the Certificates page read from one
auto-generated file, so this is the only step needed — nothing else to edit.

## First-time setup

You won't need this again unless you're setting the project up on a new
computer. From this folder:

```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/masonclement/masonclement.com.git
git push -u origin main
```

Then, one time, in Render: **New → Static Site → connect this GitHub repo**.
Leave the build command blank and set the publish directory to `.`.

## Domain (already set up, for reference)

- Render → your static site → **Settings → Custom Domains** → add
  `masonclement.com` and `www.masonclement.com`.
- Namecheap → **Domain List → Manage → Advanced DNS** → add the CNAME/ALIAS
  records Render shows you.
- DNS changes can take a few hours to kick in; Render issues HTTPS
  automatically once it verifies.

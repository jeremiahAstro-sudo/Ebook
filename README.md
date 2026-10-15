# Greenleaf Library — static ebook website

A local-first ebook library starter designed for GitHub Pages. It includes a reader catalogue, chapter reader, local admin workspace, PDF/DOCX text extraction, device-local notes, and browser-side access passes with a repeating reader watermark.

## Start locally

Because PDF/DOCX parsing libraries are loaded from CDNs, use a local static server rather than opening HTML files directly. From the project folder, run:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deploy to GitHub Pages

1. Create a GitHub repository.
2. Upload the contents of this folder to the repository root.
3. Open **Settings → Pages**.
4. Choose **Deploy from a branch**, select `main` and `/(root)`, then save.
5. Wait for GitHub Pages to publish the site.

## Admin workflow (current static version)

1. Open `/admin.html`.
2. Create a local admin password on that browser, then sign in.
3. Add a PDF or DOCX book, review extracted text and chapter headings, and save.
4. Create book-specific access passes and set validity (3, 4, 5 weeks or custom days).
5. Export the library data JSON.
6. Replace `data/library.js` with the exported JSON before committing the update to GitHub.

### Important limitation

This is a static starter, not a secure publishing backend. The local admin state is stored in that browser and does not automatically become the published site's data. Exporting JSON and committing the update is still required. A one-click Publish button that writes to GitHub needs a trusted GitHub Actions trigger or server-side publishing service; never put a GitHub write token in public JavaScript.

GitHub Pages serves public static files. Client-side tokens, local admin passwords, watermarks, anti-copying controls, and device-clock expiration can be inspected or bypassed by a determined visitor. Do not use this version for confidential content or as robust access control.

## Included reader features

- Responsive catalogue and category/search filters
- Chapter navigation and table of contents
- Reader username + token form
- Repeating watermark with book title, username and shortened pass reference
- Font-size controls, dark reading mode, progress indicator
- Device-local bookmarks, notes and reading preferences
- Context-menu/copy/print-shortcut deterrents (not foolproof)

## Current limitations

- Book and token data are local until exported and deployed.
- Comments are not shared between readers in this backend-free version.
- Device-local notes and preferences do not sync across devices.
- PDF text extraction works best with text-based PDFs. Scanned documents need OCR.
- PDF/DOCX parsing libraries are loaded from CDNs and therefore require internet access for the upload conversion feature.
- The local admin password is a convenience lock only, not secure authentication.

## Folder structure

```text
index.html
reader.html
admin.html
css/styles.css
js/store.js
js/catalog.js
js/reader.js
js/admin.js
data/library.js
README.md
```

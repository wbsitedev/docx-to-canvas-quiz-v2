# Word → Canvas Quiz Converter

A single-page web tool that converts a **Word `.docx`** of test questions into a
**Canvas-ready QTI 1.2 `.zip`** that faculty can import directly into a course.

Everything runs **in the browser** — no server, no upload, no account. Nothing a
faculty member opens ever leaves their device, which keeps it simple for IT/FERPA review.

**Live tool:** https://YOUR-USERNAME.github.io/docx-to-canvas-quiz-v2/
*(update this link after enabling GitHub Pages)*

> This is **v2** — images are packaged as files (`$IMS-CC-FILEBASE$`) instead of inline data-URIs.
> The previous version remains available in its own repository.

---

## For faculty — how to use it

1. Open the link above.
2. Format your questions in Word using four small rules (a copy-paste example and a
   downloadable sample are built into the page):
   - Start each question with a number: `1.` `2.` `3.`
   - Start each answer choice with a letter: `a)` `b)` `c)`
   - Put an asterisk `*` before the **correct** choice(s)
   - Optional tags on their own line: `Type: Essay`, `Points: 5`, `Title: …`
3. Enter a quiz title, drop your `.docx` on the page, and review the parsed questions.
4. Click **Download Canvas QTI .zip**.
5. In Canvas: **Settings → Import Course Content → “QTI .zip file”** → choose the file → **Import**.

### Question types supported
Multiple choice · True/False · Multiple answers (select-all) · Fill-in-the-blank /
short answer · Essay. Images pasted into Word are carried into the question automatically.

Type is auto-detected: one `*` choice → Multiple Choice · a True/False pair → True/False ·
two or more `*` choices → Multiple Answers · `*`answers with no letters → Fill-in-the-Blank ·
no choices or answers → Essay. Use `Type:` to override.

---

## For the maintainer

- The entire app is one self-contained file: [`index.html`](index.html)
  (the [fflate](https://github.com/101arrowz/fflate) zip library is inlined; no build step).
- **Update it:** edit `index.html`, commit, and push — GitHub Pages redeploys automatically.
- Generates IMS **QTI 1.2**, which imports into both Canvas **Classic** and **New Quizzes**.
- **Images** are packaged as real files under `web_resources/media/` and referenced with Canvas's
  `$IMS-CC-FILEBASE$` token (declared as `webcontent` resources in the manifest) — the same way a
  Canvas export carries images. On import Canvas uploads them to course **Files** and links them.
- **New Quizzes + images:** the New Quizzes importer sometimes drops QTI-packaged images. The reliable
  path is to import into **Classic Quizzes** first (images come in), then **⋮ → Migrate to New Quizzes**,
  which carries the images over. The tool documents this for faculty in-page.

## License

MIT — free for institutional and personal use.

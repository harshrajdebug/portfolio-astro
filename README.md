# harshrajdebug.in in Astro

My portfolio site ([harshrajdebug.in](https://harshrajdebug.in)), rebuilt in Astro from the original hand-written HTML, CSS and JavaScript. The goal was a faithful port: the same design, the same terminal behaviour and the same content, with a component structure that is easier to maintain. The only content change is the fix notes for two findings, updated after their pull requests changed.

## What changed in the port

- **Layout and components.** `src/layouts/Base.astro` holds the page shell (status bar, boot log, prompt and navigation), and each module is its own component in `src/components/`.
- **Findings as data.** The findings live in `src/data/findings.js`. `Work.astro` renders the findings table from that module at build time, so the table is in the HTML even with JavaScript off, and the client script imports the same module for the case pages and the prompt commands.
- **Bundled assets.** The stylesheet and the terminal script are imported and bundled by Astro.

I compared the port against the original by serving both locally and taking headless Chrome screenshots of the home page, the work table and a case page. All three are pixel-identical, and the rendered text matches.

## Run it

```bash
npm install
npm run dev
```

`npm run build` writes the static site to `dist/`. Pushing to `main` deploys it to GitHub Pages through `.github/workflows/deploy.yml`.

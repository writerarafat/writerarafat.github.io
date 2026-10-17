# Arafat — A Literary World

A premium dark, bilingual (Bangla/English), responsive static literary website for GitHub Pages.

## Included

- Responsive homepage, archive, author bio, and post detail page
- Bangla/English toggle
- Search by title, excerpt, and content; category filter
- JSON-powered writing archive (`posts/posts.json`)
- Basic SEO metadata, canonical links, `robots.txt`, `sitemap.xml`, favicon, and 404 page
- Optional Utterances comments integration (requires setup)
- Decap CMS starter files (requires a secure GitHub OAuth setup before use)

## Publish on GitHub Pages

1. Download/unzip these files.
2. Open `https://github.com/WriterArafat/writerarafat.github.io`.
3. Before replacing anything, download a backup of the current repository.
4. Upload the files and folders from this package to the repository root. Keep the folders exactly as they are.
5. Commit to the branch configured for GitHub Pages (usually `main`).
6. In repository **Settings → Pages**, select **Deploy from a branch**, choose `main` and `/ (root)`, then save.
7. Wait for the deployment to finish, then open `https://writerarafat.github.io`.

## Add your own writing

Edit `posts/posts.json`. Each item should follow this shape:

```json
{
  "slug": "my-poem-title",
  "category": "poetry",
  "date": "2026-10-17",
  "featured": true,
  "title_bn": "বাংলা শিরোনাম",
  "title_en": "English title",
  "excerpt_bn": "বাংলা সারাংশ",
  "excerpt_en": "Short English summary",
  "body_bn": "বাংলা লেখার প্রথম অনুচ্ছেদ।\n\nদ্বিতীয় অনুচ্ছেদ।",
  "body_en": "First paragraph in English.\n\nSecond paragraph."
}
```

Allowed categories: `poetry`, `story`, `essay`, `reflection`. Use a unique `slug` with English letters, numbers, and hyphens. If you only have Bangla, leave the English fields blank or repeat a carefully translated version later. The three included sample pieces are demonstration content; replace them with your own work.

## Comments (Utterances)

The template includes a comments placeholder. To enable actual comments:
1. Make sure the repository is public.
2. Install/enable the Utterances GitHub App for the repository.
3. In `assets/js/main.js`, find `setupUtterances()` and uncomment the script lines.
4. Confirm the repository name is `WriterArafat/writerarafat.github.io` and choose a GitHub issue label that exists (or create `reader-comments`).
5. Commit and test a post page. Readers need a GitHub account to comment.

Comments are public GitHub issues. Do not enable this if you do not want public discussion attached to the repository.

## Admin / CMS

`admin/` contains a Decap CMS starter configuration, not a fully working authenticated admin yet. GitHub backend authentication needs a supported OAuth server/application configured separately. Do **not** place a personal access token in `admin/config.yml`, JavaScript, or any public file.

Important: this CMS starter writes to `content/posts/`, while the live site currently reads `posts/posts.json`. To make CMS publishing live, add a build/publishing workflow that merges the CMS content into `posts/posts.json`, or change the site data model to consume individual JSON files. Do not assume the CMS is live until this integration is completed. The simplest safe first version is to edit `posts/posts.json` in GitHub directly.

## SEO notes

- The sitemap lists the static pages. Add every real article URL to `sitemap.xml` if you later create one HTML file per post.
- The current detail page uses a query-string slug (`post.html?slug=...`); crawlers may treat these pages less ideally than individual static HTML pages. For stronger SEO, generate a separate HTML page for each published article as part of a build step.
- After publishing, add the site to Google Search Console and submit `https://writerarafat.github.io/sitemap.xml`.
- Search engines decide when/if to index pages; sitemap submission does not guarantee indexing.

## Customize before publishing

- Replace the sample posts in `posts/posts.json` with your own writing.
- Edit biography text in `about.html`.
- Add public contact and social links only if you want them public.
- Update dates and SEO descriptions when you publish.
- Keep the repo public for the free GitHub Pages workflow.

## Security

GitHub Pages is static hosting. It cannot securely store secrets or run a private server. Never put passwords, API keys, or GitHub personal access tokens in the repository. For a fully working admin panel or server-backed comment system, use a properly configured CMS/auth provider or backend.

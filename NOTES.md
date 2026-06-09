# Seneca Site — Setup Notes

## Domain
- **Registrar:** Namecheap
- **Domain:** senecathoughtsgovwwwsenecathoughts.xyz
- **URL:** https://www.senecathoughtsgovwwwsenecathoughts.xyz
- **DNS:** CNAME record, Host: `www`, Value: `jwjunk24.github.io`

## Hosting
- **Platform:** GitHub Pages
- **Repo:** https://github.com/jwjunk24/seneca
- **Fallback URL:** https://jwjunk24.github.io/seneca

## Auth
- GitHub PAT is stored in `.seneca-pat` (gitignored, never committed)
- PAT needs `repo` → Contents: Read and write

## Daily task
- Scheduled task `seneca-daily` runs at 6AM every day
- Generates a new Seneca letter post, writes HTML to `posts/`, updates `index.html`, commits and pushes to GitHub
- Task prompt managed via Cowork scheduled tasks

## Site structure
- `index.html` — archive/index of all posts
- `posts/YYYY-MM-DD.html` — individual letter pages
- `seneca.css` — shared styles
- `CNAME` — custom domain config for GitHub Pages

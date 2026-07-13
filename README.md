# Potoybichchya Economics Hub

Статичний **Economics Hub** (гість + вендор + P&L). Доступ — **Vercel + Password Protection**, не публічний GitHub Pages.

Джерело: `docs/economics/` у робочому проєкті `Потойбіччя` → `python tools/sync_economics_hub_pages.py --push`.

## Деплой і безпека

Див. **[DEPLOY.md](DEPLOY.md)** — Vercel CLI, Password Protection, вимкнення GitHub Pages.

## SEO

- `robots.txt` — Disallow для пошуковиків
- `<meta robots noindex>` + `X-Robots-Tag` у `vercel.json`

# Potoybichchya Economics Hub

Статичний **Economics Hub** (гість + вендор + P&L).

- **Production:** https://potoybichchya-economics.vercel.app
- **Доступ:** Vercel Password Protection (Settings -> Deployment Protection)
- **Оновлення:** у проєкті `Потойбіччя` -> `python tools/sync_economics_hub_pages.py --publish`

Джерело: `docs/economics/` у робочому проєкті.

## Деплой

Git push у цей репо автоматично деплоїть на Vercel (інтеграція GitHub).

Див. **[DEPLOY.md](DEPLOY.md)**.

## SEO

- `robots.txt` + `<meta robots noindex>` + `X-Robots-Tag` у `vercel.json`

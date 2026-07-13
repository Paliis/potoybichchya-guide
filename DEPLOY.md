# Деплой Economics Hub на Vercel (захищений доступ)

Статичний гід: `index.html` → `potoybichchya-economics.html` + `balance-guest-guide.html`.

**Джерело правди:** репо `Потойбіччя` → `python tools/sync_economics_hub_pages.py --push` копіює артефакти сюди.

---

## Крок 1. Синхронізація з робочого проєкту

```powershell
cd "c:\Users\user\Desktop\Курсор\Потойбіччя\tools"
python sync_economics_hub_pages.py --push
```

---

## Крок 2. Перший деплой на Vercel (без Git)

У папці **potoybichchya-guide**:

```powershell
cd "c:\Users\user\Desktop\Курсор\potoybichchya-guide"
npx vercel@latest
```

- **Set up and deploy?** — Yes  
- **Link to existing project?** — No (перший раз) або Yes, якщо проєкт уже є  
- **Project name:** `potoybichchya-economics` (або Enter)  
- **Directory:** Enter (корінь репо)  
- Build / Output: Vercel побачить лише HTML — **без** `npm run build`

Після деплою з’явиться URL типу `https://potoybichchya-economics-xxxx.vercel.app`.

---

## Крок 3. Password Protection (обовʼязково)

1. [Vercel Dashboard](https://vercel.com) → проєкт **potoybichchya-economics**  
2. **Settings → Deployment Protection**  
3. Увімкнути **Password Protection** (Standard Protection)  
4. Задати пароль → зберегти  
5. Роздати колегам: **URL + пароль** (не публікувати в open web)

Альтернатива (якщо є Pro): **Vercel Authentication** — доступ лише для email з allowlist.

Посилання з Stage Builder (той самий акаунт `paliis-projects`):  
https://vercel.com/docs/security/deployment-protection

---

## Крок 4. Автодеплой з GitHub (опційно)

1. Vercel → **Add New Project** → Import `Paliis/potoybichchya-guide` (або ваш fork)  
2. Framework Preset: **Other** (статичні файли)  
3. Build Command: порожньо  
4. Output Directory: `.` (корінь)  
5. Після кожного `sync --push` Vercel перезбере сайт автоматично  

**Password Protection** лишається в налаштуваннях проєкту — не злітає після redeploy.

---

## GitHub Pages (legacy)

Раніше: `https://paliis.github.io/potoybichchya-guide/` — **публічно, без пароля**.

Рекомендація: у GitHub repo **Settings → Pages → Disable** або не ділитись старим URL після переходу на Vercel.

---

## Що вже в репо

| Файл | Роль |
|------|------|
| `robots.txt` | Заборона індексації пошуковиками |
| `vercel.json` | `X-Robots-Tag: noindex` на всіх відповідях |
| HTML `<meta robots>` | Другий шар noindex у сторінках |

**Примітка:** noindex + robots **не** замінюють пароль — лише ховають від Google. Справжній gate — **Deployment Protection** на Vercel.

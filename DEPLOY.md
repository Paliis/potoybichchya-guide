# Деплой Economics Hub на Vercel (захищений доступ)

**Production:** https://potoybichchya-economics.vercel.app  
**Проєкт Vercel:** `paliis-projects/potoybichchya-economics` (GitHub `Paliis/potoybichchya-guide` підключено)

---

## Оновлення після змін у `Потойбіччя` (рекомендовано)

```powershell
cd "c:\Users\user\Desktop\Курсор\Потойбіччя\tools"
python sync_economics_hub_pages.py --publish
```

Що відбувається:
1. `balance_guest_export` + `economics_hub_export`
2. Копіювання HTML + `robots.txt` + `vercel.json` у `potoybichchya-guide`
3. `git push` -> **Vercel автоматично перезбирає** (GitHub integration)

Миттєвий CLI-деплой (без очікування Git hook):

```powershell
python sync_economics_hub_pages.py --publish --deploy
```

---

## Password Protection (зробити один раз)

1. https://vercel.com/paliis-projects/potoybichchya-economics/settings/deployment-protection
2. Увімкнути **Password Protection**
3. Задати пароль -> роздати колегам URL + пароль

---

## Вимкнути публічний GitHub Pages (рекомендовано)

Старий URL `https://paliis.github.io/potoybichchya-guide/` лишається публічним, поки Pages увімкнено.

GitHub -> `potoybichchya-guide` -> **Settings -> Pages -> Disable**

Або CLI: `gh api -X DELETE repos/Paliis/potoybichchya-guide/pages`

---

## Перший деплой (вже зроблено)

```powershell
cd potoybichchya-guide
npx vercel@latest link --yes --project potoybichchya-economics
npx vercel@latest --prod --yes
```

---

## Файли в репо

| Файл | Роль |
|------|------|
| `robots.txt` | Disallow пошуковиків |
| `vercel.json` | `X-Robots-Tag: noindex` |
| HTML | `<meta robots noindex>` |

noindex **не** замінює пароль. Gate = **Deployment Protection**.

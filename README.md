# Dclick IA — Landing Page Astro

## Stack
- **Astro 4** — framework SSG
- **Tailwind CSS 3** — styles (compilé, pas de CDN)
- **n8n webhook** — formulaire → EspoCRM

## Dev local
```bash
npm install
npm run dev
# → http://localhost:4321
```

## Build
```bash
npm run build
# output → dist/
```

## Déploiement Coolify

### Option A — Dockerfile (recommandé)
1. Coolify → New Resource → **Docker**
2. Source : repo GitHub
3. **Dockerfile** détecté automatiquement
4. Domain : `dclick-ia.fr` + `www.dclick-ia.fr`
5. → Deploy ✅

### Option B — Static Site
1. Coolify → New Resource → **Static Site**
2. Build command : `npm run build`
3. Publish directory : `dist`
4. Domain : `dclick-ia.fr`

## DNS (OVH / registrar)
| Type | Nom | Valeur |
|------|-----|--------|
| A | @ | <IP VPS nebt.pro> |
| A | www | <IP VPS nebt.pro> |

## Structure
```
src/
├── components/
│   ├── Header.astro
│   ├── Hero.astro
│   ├── Contact.astro   ← webhook n8n intégré
│   └── Footer.astro
├── layouts/
│   └── Layout.astro    ← SEO, meta OG
├── pages/
│   └── index.astro     ← page principale
└── styles/
    └── global.css
public/
└── LogoDclickV2.png    ← à placer ici !
```

## ⚠️ Avant le déploiement
1. Placer `LogoDclickV2.png` dans `/public/`
2. Activer le workflow n8n `dclick-ia-contact`
3. Ajouter `dclick-ia.fr` dans les Allowed Origins du webhook n8n

# 🛠️ Configuration de l'Environnement Front-End

Ce document récapitule la configuration technique mise en place pour le projet, optimisée pour un développement rapide et stable sur Windows.

## 🚀 Stack Technique
- **Runtime** : [Node.js v22.12.0](https://nodejs.org/) (Recommandé)
- **Bundler** : [Vite v7.3.0](https://vitejs.dev/)
- **Templating** : [Nunjucks](https://mozilla.github.io/nunjucks/) (via plugin personnalisé)
- **CSS** : [Tailwind CSS v3.4.1](https://tailwindcss.com/) + [PostCSS](https://postcss.org/)
- **UI & Interaction** :
  - [Preline UI](https://preline.co/) (Composants & Plugins)
  - [Alpine.js v3.15.3](https://alpinejs.dev/)
- **Design System** :
  - **Font** : [Poppins](https://fonts.google.com/specimen/Poppins) (Hébergée localement)
  - **Documentation** : [Storybook v8+](https://storybook.js.org/)

## 📁 Structure du Projet (Atomic Design)
```text
flunch-group/
├── src/
│   ├── components/         # Composants Atomic Design
│   │   ├── atoms/          # Éléments indivisibles (Button, Badge, Input...)
│   │   ├── molecules/      # Groupes simples (FormField, Card, Alert...)
│   │   └── organisms/      # Sections complexes (Header, Footer, Form...)
│   ├── templates/          # Layouts globaux
│   │   └── layouts/        # (base.njk)
│   ├── styles/             # Styles CSS (main.css + Tailwind)
│   ├── js/                 # Logique JavaScript (main.js)
│   ├── stories/            # Documentation Design System (Couleurs, Typo)
│   ├── index.html          # Page d'accueil
│   ├── styleguide.html     # Page de démonstration des composants
│   └── colors-guide.html   # Guide visuel de la palette
├── .storybook/             # Configuration Storybook
├── public/                 # Assets (images, fonts/poppins)
└── vite.config.js          # Config Vite + Plugin Nunjucks
```

## 🎨 Thème Personnalisé
Le projet utilise une palette de couleurs personnalisée définie dans `tailwind.config.cjs` :
- **Primary** : Nuances de Bleu (`primary-50` à `primary-700`)
- **Secondary** : Nuances de Rouge/Terre (`secondary-50` à `secondary-700`)
- **Accent** : Couleurs d'état et de mise en valeur (`accent-50` à `accent-500`)
- **Neutral** : Teintes douces (`cream`, `beige`, `sand`)

La police **Poppins** est servie localement depuis `public/fonts/poppins/` sans dépendance Google Fonts.

## 🛠️ Commandes Utiles

### Développement
```bash
npm run dev
```
Lance le serveur de développement sur [http://localhost:3000](http://localhost:3000).

### Storybook (Documentation)
```bash
npm run storybook
```
Lance l'interface de documentation des composants sur [http://localhost:6006](http://localhost:6006).

### Production (Build)
```bash
npm run build
```
Compile et optimise tous les fichiers dans le dossier `/dist`.

### Aperçu de la Production
```bash
npm run preview
```
Lance un serveur local pour tester le contenu du dossier `/dist`.

## ⚙️ Détails de l'implémentation Nunjucks
Un plugin personnalisé dans `vite.config.js` gère la compilation Nunjucks :
- Supporte les `{% include "components/atoms/..." %}`
- Supporte les `{% extends "layouts/..." %}`
- Compatible avec le rechargement à chaud (HMR) de Vite

## ⚠️ Notes importantes pour Windows
Si vous rencontrez des erreurs de type "unknown path" ou "template not found" :
1. Assurez-vous d'utiliser **Node 18+** (v22 de préférence).
2. Ne modifiez pas la section `nunjucksPlugin` dans `vite.config.js` sans tester la compatibilité des chemins.

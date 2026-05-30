# Ma boîte à outils

Recueil de petits outils HTML interactifs, déployés sur Netlify.

## Structure

```
boite-a-outils/
├── index.html          ← page d'accueil (galerie des outils)
├── netlify.toml        ← config de déploiement
├── profit-first/
│   └── index.html      ← outil Profit First
└── (un dossier par outil)
```

## Ajouter un nouvel outil

1. Crée un dossier à la racine, ex. `mon-outil/`
2. Place le fichier HTML dedans en le nommant `index.html`
   (le nommer `index.html` permet d'accéder à l'outil via une URL propre : `/mon-outil/`)
3. Dans `index.html` (la page d'accueil), duplique le bloc `<!-- MODÈLE -->`
   et adapte le lien, le titre, la description, l'icône et la couleur.
4. Pousse sur GitHub : Netlify redéploie automatiquement.

## Couleurs disponibles (convention archétypale)

- `var(--roi)` — doré
- `var(--guerrier)` — orange
- `var(--securite)` — bleu
- `var(--intendance)` — vert

## Déploiement

Connecté à Netlify via GitHub. Chaque `git push` sur la branche principale
déclenche un nouveau déploiement.

URL suggérée : `outils.steevencadel.fr` (sous-domaine à configurer dans Netlify).

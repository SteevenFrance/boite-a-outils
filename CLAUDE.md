# Instructions projet — Ma boîte à outils

Ce dépôt est un recueil de petits outils HTML interactifs, déployés sur Netlify.
Chaque outil est autonome (HTML + CSS + JS dans un seul fichier, sans dépendance externe à installer).

## Contexte

- Propriétaire : Steeven Cadel (steevencadel.fr)
- Hébergement : Netlify, connecté à ce dépôt GitHub. Chaque `git push` sur la branche principale redéploie automatiquement.
- URL cible : `outils.steevencadel.fr`
- Public : usage personnel + démonstration. Outils en français.

## Structure du dépôt

```
.
├── index.html          ← page d'accueil (galerie de cartes vers les outils)
├── netlify.toml        ← config de déploiement (publie la racine)
├── README.md           ← mode d'emploi humain
├── CLAUDE.md           ← ce fichier
└── <slug-outil>/
    └── index.html      ← un outil = un dossier contenant index.html
```

Règle d'or : **un outil = un dossier à la racine, contenant un `index.html`**.
Nommer le fichier `index.html` donne une URL propre (`/profit-first/` plutôt que `/profit-first/outil.html`).

## Identité visuelle (à respecter pour tout nouvel outil et toute modification)

Tous les outils partagent la même charte. Réutilise systématiquement ces tokens CSS :

```css
--bg: #0e1410;          /* fond */
--bg-card: #161e18;     /* cartes */
--bg-input: #0a0f0c;    /* champs */
--ink: #f2efe6;         /* texte */
--muted: #8a9a8e;       /* texte secondaire */
--line: #283129;        /* bordures */
--gold: #c9a84a;        /* accent principal */
```

Couleurs archétypales (convention de Steeven — à utiliser pour catégoriser/colorer) :
```css
--roi: #c9a84a;         /* doré */
--guerrier: #d8743f;    /* orange */
--securite: #5f8fb0;    /* bleu */
--intendance: #6fae7a;  /* vert */
```

Polices (importées via Google Fonts dans chaque fichier) :
- Titres : `'Fraunces', serif` (poids 900 pour les gros titres, italique pour les accents)
- Corps et UI : `'Outfit', sans-serif`

Style général : fond sombre, dégradés radiaux discrets en haut-droite et bas-gauche,
cartes à coin arrondi avec bordure supérieure colorée, animations sobres au survol.
Garder une mise en page centrée, largeur max ~760px pour un outil, ~880px pour la galerie.

## Ajouter un nouvel outil

1. Crée un dossier à la racine avec un slug en minuscules-avec-tirets (ex. `calculateur-tva/`).
2. Place le HTML dedans, nommé `index.html`, en respectant la charte ci-dessus.
3. Dans la page d'accueil `index.html` (racine), duplique le bloc commenté `<!-- MODÈLE -->`
   et renseigne : lien (`./slug/`), icône (emoji), titre, description courte, couleur (`--c`).
4. Si une carte « À venir » occupe encore une place, tu peux la remplacer.
5. Mets à jour la liste des outils dans le README si pertinent.
6. Commit + push (voir ci-dessous).

## Modifier un outil existant

- Édite directement le `index.html` du dossier concerné.
- Ne casse pas la charte visuelle ni la structure des tokens CSS.
- Teste mentalement que le JS reste autonome (aucun appel réseau requis pour fonctionner).

## Déploiement

```bash
git add .
git commit -m "Description claire du changement"
git push
```

Netlify redéploie seul. Si le MCP Netlify est disponible, tu peux vérifier le statut
du déploiement ou déclencher/inspecter un build via les outils Netlify plutôt que par l'interface web.

## Conventions de commit

Messages courts et explicites, en français, à l'impératif :
- `Ajoute l'outil calculateur-tva`
- `Corrige l'équilibrage des ratios dans profit-first`
- `Met à jour la charte couleurs de la galerie`

## Ce qu'il ne faut PAS faire

- Pas de framework, pas de build step, pas de `node_modules`. Tout reste en HTML/CSS/JS natif, un fichier par outil.
- Pas de stockage navigateur (`localStorage`/`sessionStorage`) requis pour qu'un outil fonctionne — garder l'état en mémoire JS.
- Pas de dépendances chargées depuis un CDN si on peut l'éviter (les Google Fonts sont tolérées).

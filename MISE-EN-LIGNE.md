# Première mise en ligne — pas à pas

À faire une seule fois, pour publier le dépôt. Ensuite, un simple `git push` suffit.

## Prérequis

- Git installé
- Un compte GitHub et un compte Netlify (déjà reliés à ton GitHub)

## 1. Initialiser le dépôt local

Place-toi dans le dossier `boite-a-outils/`, puis :

```bash
git init
git add .
git commit -m "Initialise la boîte à outils avec Profit First"
git branch -M main
```

## 2. Créer le dépôt distant sur GitHub

Option A — avec la CLI GitHub (`gh`) si tu l'as :

```bash
gh repo create boite-a-outils --public --source=. --remote=origin --push
```

Cette commande crée le repo, l'ajoute comme `origin` et pousse tout d'un coup.

Option B — manuellement :
1. Crée un dépôt vide sur github.com (sans README, sans .gitignore).
2. Puis :

```bash
git remote add origin https://github.com/<ton-pseudo>/boite-a-outils.git
git push -u origin main
```

## 3. Déployer sur Netlify

1. Sur app.netlify.com : « Add new site » → « Import an existing project ».
2. Choisis GitHub, puis le dépôt `boite-a-outils`.
3. Laisse les réglages par défaut (le `netlify.toml` s'occupe de publier la racine).
4. « Deploy site ». Au bout de quelques secondes, tu as une URL en `*.netlify.app`.

## 4. (Optionnel) Brancher le sous-domaine

1. Dans Netlify : Site settings → Domain management → Add a domain.
2. Saisis `outils.steevencadel.fr`.
3. Netlify t'indique l'enregistrement DNS à créer (un CNAME pointant vers ton site Netlify).
4. Crée ce CNAME chez le gestionnaire DNS de steevencadel.fr.
5. Attends la propagation (quelques minutes à quelques heures) ; le HTTPS est automatique.

## Cycle de vie ensuite

Pour toute modification ou nouvel outil :

```bash
git add .
git commit -m "Message clair"
git push
```

→ Netlify redéploie automatiquement.

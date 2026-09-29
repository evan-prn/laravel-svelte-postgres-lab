# Décisions

> Chaque choix, les options écartées et le pourquoi. Une décision ne s'efface pas : si elle
> change, une nouvelle entrée la remplace et le dit.

---

## D1. Architecture front et back

*2026-09-29*

**Décision** : une API Laravel dans `backend/` et SvelteKit en SPA (`adapter-static`) dans
`frontend/`.

| Option | Pour | Contre |
|---|---|---|
| **A. API Laravel + SvelteKit en SPA** (retenue) | Séparation nette, conception d'une API REST, front compilé en fichiers statiques servables par Apache | Deux applications à configurer, authentification d'une SPA plus délicate |
| B. Laravel + Inertia + Svelte | Une seule application, pas de CORS, session native, un seul déploiement | Inertia masque la conception d'API, Svelte y tourne sans SvelteKit |
| C. SvelteKit avec rendu serveur | Rendu côté serveur | Un serveur Node en production, deux adresses d'API (côté serveur et côté navigateur) dans Docker |

**Pourquoi A** : c'est l'option qui fait pratiquer le plus de sujets (API REST, codes HTTP,
validation côté API, `fetch` côté front). Avec Inertia (B), le contrôleur renvoie
`Inertia::render('Page', $props)` au lieu de JSON : l'avoir compris suffit pour en discuter.

**Conséquences**

- **Pas de CORS.** En développement, le proxy Vite (`server.proxy`) transmet `/api` à Laravel.
  En production, Apache sert le front statique et `/api` sur le même domaine : même origine.
- **SPA** : `export const ssr = false` et une page de repli (`fallback`). Apache doit réécrire
  toute URL inconnue vers cette page (jalon 6).
- **Authentification reportée** après l'entretien : Sanctum en mode SPA, par cookies de session
  sur le même domaine.

---

## D2. Domaine métier

*2026-09-29*

**Décision** : suivi de dossiers annuels.

- Une organisation a plusieurs clients (1-N).
- Un client a au plus un dossier par exercice (1-N, unicité composée sur client et exercice).
- Un dossier contient des documents déposés (1-N).
- Un gestionnaire suit plusieurs clients, un client a plusieurs gestionnaires (N-N, table pivot).

| Option | Pour | Contre |
|---|---|---|
| **Dossiers annuels** (retenue) | Couvre toutes les notions visées, proche d'une application de gestion réelle | Vocabulaire à garder générique |
| Bibliothèque (prêts, retours) | Domaine connu de tous | Loin d'une application de gestion, pas de notion d'exercice |
| Tickets de support | Évoque le support applicatif | Pas d'unicité composée naturelle |

**Couverture des notions**

| Notion | Où |
|---|---|
| Relations 1-N | organisation, clients, dossiers, documents |
| Relation N-N | gestionnaires et clients |
| Unicité composée | un seul dossier par client et par exercice |
| Contrainte `CHECK` | exercice dans une plage, statut dans une liste |
| Transaction | créer un dossier avec ses documents initiaux |
| Agrégats, fonctions de fenêtre | documents par dossier, top 3 des clients par organisation |
| Trouver les absents | clients sans dossier pour un exercice donné |
| Droits d'accès | un gestionnaire ne voit que ses clients (après l'entretien) |

Les noms des tables et des colonnes seront fixés au jalon 2, en anglais.

---

## D3. Environnement de développement

*2026-09-29*

**Décision** : PHP et Node en natif sur Windows, PostgreSQL seul en conteneur.

| Option | Pour | Contre |
|---|---|---|
| **A. Natif + PostgreSQL en conteneur** (retenue) | Rapide, rechargement à chaud de Vite fiable | Extensions PHP à activer, écart avec la production |
| B. Tout en conteneurs | Proche de la production | Montages depuis `C:\` lents (milliers de fichiers dans `vendor/`), événements de fichiers perdus pour Vite |

**Conséquences**

- Activer `pdo_pgsql`, `pgsql` et `intl` dans le `php.ini`. Sous Windows, `pdo_pgsql` charge
  `libpq.dll`, fournie à la racine du dossier PHP, qui doit donc être dans le `PATH`.
- Pas de `psql` natif : on passe par `docker compose exec`.
- L'écart avec la production est comblé au jalon 6 (image `php:8.5-apache`).

---

## D4. Dépôt GitHub

*2026-09-29*

**Décision** : dépôt `laravel-svelte-postgres-lab`, public. Création sur confirmation explicite.

| Option | Pour | Contre |
|---|---|---|
| Nom lié à l'entreprise visée | Explicite | Contredit la neutralité, inutilisable pour une autre candidature |
| **Nom neutre** (retenu) | Réutilisable, décrit la stack | |
| **Public** (retenu) | Montrable sans dépendre d'un portable, minutes GitHub Actions gratuites et illimitées sur les runners standards | Tout ce qui est versionné devient lisible |
| Privé | Rien n'est exposé | Minutes Actions prises sur un quota mensuel, montrable seulement en local |

**CLAUDE.md reste versionné** : il montre concrètement le cadre de travail avec l'IA (qui écrit
quoi). Le chemin qui contenait le nom d'utilisateur Windows a été retiré. Les sections propres à
l'entretien seront retirées après celui-ci. Option écartée : l'ignorer dans `.gitignore`.

Le dossier local garde son nom : le nom du dépôt distant en est indépendant.

---

## D5. Modes de travail

*2026-09-29*

- **Démo** pour la plomberie : Git, Docker, configuration, CI.
- **Guidé** dès la première migration. Le SQL et les composants Svelte restent écrits à la main,
  en mode guidé ou défi.
- **Bonus hors feuille de route** : basculer un projet Laravel existant de MySQL vers PostgreSQL
  et noter ce qui casse, seulement si un jalon finit en avance.

---

## D6. Versions épinglées

*2026-09-29*

**Décision** : dernières versions stables, vérifiées sur les sources officielles, tableau dans
`README.md`.

**Écartées**

- PostgreSQL 19 : encore en bêta (`19beta4`).
- Node 26 : branche « Current », pas encore LTS.
- SvelteKit 3 : seulement en pré-version (`next`).

**Précisions**

- L'image est épinglée avec sa variante (`postgres:18.6-trixie`) : la distribution de base
  devient visible, et elle change parfois d'une version à l'autre. Un épinglage strict passerait
  par l'empreinte (`@sha256:...`), superflu ici.
- Poste de développement en PHP 8.5.6 et Node 24.19 : même branche que les versions épinglées,
  suffisant pour développer. La CI et l'image Docker utilisent les versions du tableau.

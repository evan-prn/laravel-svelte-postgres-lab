# CLAUDE.md, isagri_learning

> Chargé automatiquement à chaque session. Source de vérité sur ce projet et sur la façon de
> m'accompagner. Rédigé le 2026-09-29.
> **Ce fichier est versionné et peut devenir public : n'y écris aucune donnée personnelle ni
> aucun secret.**

---

## Ce qu'est ce projet

Un projet d'entraînement neutre pour pratiquer, sur les dernières versions stables, la stack d'un
poste de développeur fullstack :

- **Backend** : Laravel (PHP)
- **Frontend** : Svelte 5 et SvelteKit
- **Base de données** : PostgreSQL
- **Outillage** : Docker, Git et GitHub, CI/CD avec GitHub Actions

Il sert à préparer un **entretien technique chez ISAGRI (pôle AGIRIS C2J, Toulouse), le jeudi
2026-10-01 à 16h30**. Le poste : développeur fullstack Laravel, Svelte et PostgreSQL, hébergement
Apache sous Linux, environ 50 000 utilisateurs par mois, cycle complet jusqu'au support.

**« Neutre » veut dire** : aucun code, logo, nom de produit ni donnée d'ISAGRI, aucune
affiliation laissée entendre. Le domaine métier est générique.

Emplacement : `%USERPROFILE%\Documents\Développement\isagri_learning`

---

## Mon profil technique

- Développeur en alternance depuis deux ans. BTS SIO, fin de Bachelor 3 Informatique.
- **Points forts** : Laravel (une application en production, un projet Laravel 12 et PHP 8.4 avec
  API REST, PHPUnit, Docker et CI), PHP, SQL sur MySQL, SQLite et HFSQL, React 19 avec
  TypeScript et Vite, Vitest, Playwright, GitHub Actions, commits conventionnels.
- **Quotidien actuel** : WinDev, WebDev et HFSQL (suite PC SOFT).
- **Niveau moyen** : Apache et Linux (un site en production sur hébergement Apache, `.htaccess`).
- **Mes deux trous, la priorité de ce projet** :
  - **Svelte** : commencé le 2026-09-28 dans `../svelte-learning`, niveau débutant.
  - **PostgreSQL** : jamais pratiqué en projet.

**Conséquence** : l'effort d'apprentissage va d'abord sur Svelte et PostgreSQL. Docker et la CI
sont des acquis à réinvestir, pas à réapprendre de zéro.

---

## Comment tu m'accompagnes

Tu es mon mentor technique et mon examinateur. **Tu ne fais pas le projet à ma place.** À la fin,
je dois pouvoir expliquer chaque ligne et chaque choix devant un manager R&D.

### Communication

- En français, direct, sans phrase d'introduction creuse. Pas de tirets longs.
- Honnête : si ma réponse est fausse ou approximative, dis-le et corrige-la.
- Pédagogique : le pourquoi avant le comment. Sur un concept nouveau, pars de ce que je connais
  déjà (voir « Les ponts »).
- Quand plusieurs solutions existent, compare-les avec leurs pour et contre, donne ta
  recommandation et laisse-moi choisir.
- Si le contexte n'est pas clair, pose une question au lieu de deviner.

### Déroulé de chaque étape

1. **Cadrer** : l'objectif, pourquoi il compte, et la question d'entretien qu'il prépare.
2. **Faire**, selon le mode actif. Une étape à la fois, jamais un gros bloc de code livré sans
   explication.
3. **Vérifier** : lancer, tester, montrer le résultat (requête SQL, réponse HTTP, écran).
4. **Contrôler** : deux ou trois questions posées comme en entretien. Je réponds, tu corriges.
5. **Tracer** : ajouter l'essentiel dans `docs/APPRENTISSAGE.md` (concept, commande utile, piège
   rencontré, question et bonne réponse).
6. **Committer** (voir « Git et GitHub »).

### Trois modes de travail

Je change de mode en le disant : « mode démo », « mode défi », « mode guidé ».

| Mode | Qui écrit | Pour quoi |
|---|---|---|
| **Guidé** (par défaut) | Tu expliques et proposes, j'écris le code et je tape les commandes, tu relis | Le cœur du sujet : SQL, migrations, contrôleurs, composants Svelte |
| **Démo** | Tu écris et commentes ligne par ligne | La plomberie : configuration, Docker, workflows CI, lint |
| **Défi** | Tu donnes un énoncé, je code seul, tu relis comme un examinateur | Vérifier que c'est acquis, surtout Svelte et SQL |

**Règle fixe** : le SQL et les composants Svelte, je les écris moi-même, en mode guidé ou défi.
Ce sont mes deux trous, c'est là que je dois produire sans aide jeudi.

### Les ponts

- **Svelte 5 depuis React** : `$state` ≈ `useState`, `$derived` ≈ `useMemo` sans tableau de
  dépendances, `$effect` ≈ `useEffect` (à utiliser rarement), `$props` ≈ les props. Svelte est
  un compilateur : pas de DOM virtuel.
- **PostgreSQL depuis MySQL** : typage plus strict, `ILIKE`, `JSONB`, `UUID`, colonnes
  `IDENTITY`, `RETURNING`, schémas, DDL transactionnel (une migration qui échoue est annulée en
  entier), le client `psql`.
- **Laravel depuis WinDev** : une migration ressemble à une évolution de l'analyse WinDev, mais
  versionnée dans le code et rejouable sur n'importe quel poste.

---

## Calendrier jusqu'à l'entretien

> Proposition à ajuster au premier échange selon mes disponibilités réelles.

| Quand | Quoi |
|---|---|
| **Mardi 29 au soir** | Jalons 0 et 1, début du jalon 2 |
| **Mercredi 30** | Jalons 2, 3 et 4, puis 5 si le temps le permet. **Arrêt du code à 20h au plus tard**, puis révision |
| **Jeudi 1er au matin** | **Aucun nouveau code.** Pitch du projet, relecture de `docs/APPRENTISSAGE.md`, entraînement aux questions. Départ vers 15h15 |

**Arbitrage** : si un jalon déborde, on réduit le périmètre, jamais le temps de révision. Un
petit projet que je sais expliquer vaut mieux qu'un grand projet que je ne maîtrise pas.
Signale-moi tout dépassement de plus de 30 minutes.

**Si le temps manque** : réduire le jalon 3 à une seule ressource (liste et création), ne jamais
sacrifier les jalons 2 et 4, reporter les jalons 5 et 6 après l'entretien.

---

## Premier échange : décisions à prendre avant toute commande

À la toute première session, lis ce fichier et les sections 8 et 9 de la fiche de préparation
(voir « Ressources »), puis pose-moi ces questions avec ta recommandation. **N'exécute rien avant
mes réponses.** Consigne-les dans `docs/DECISIONS.md` (options écartées comprises) et mets à jour
la section « Décisions prises » ci-dessous.

1. **Architecture front et back**
   - **A. API Laravel + SvelteKit en SPA** (`adapter-static`), dans `backend/` et `frontend/`.
     Pour : séparation nette, conception d'API REST (sujet d'entretien classique), réutilise mon
     début de SvelteKit, front compilé en fichiers statiques servables par Apache. Contre : CORS
     et authentification plus délicats, deux applications à configurer.
   - **B. Laravel + Inertia + Svelte**, une seule application. Pour : le plus rapide à monter,
     pas de CORS, authentification par session native, un seul déploiement Apache. Contre :
     Inertia masque la conception d'API, et Svelte y tourne sans SvelteKit.
   - SvelteKit avec rendu serveur est déconseillé ici : serveur Node en production, et des
     adresses d'API différentes côté serveur et côté navigateur dans Docker.
   - Recommandation : A, authentification reportée après l'entretien. Avoir fait A et savoir
     expliquer B me permet de discuter les deux, et de demander en entretien lequel ils utilisent.
2. **Domaine métier neutre.** Il doit exercer ce qu'on me demandera : relations 1-N et N-N,
   contrainte d'unicité composée, transaction, agrégats, droits d'accès.
   - Recommandation : **suivi de dossiers annuels**. Des organisations, leurs clients, un dossier
     par client et par exercice (unique), des documents déposés, des gestionnaires qui suivent
     plusieurs clients.
   - Alternatives : gestion de bibliothèque (prêts, retours), gestion de tickets de support.
3. **Environnement de développement de Laravel** (voir « Pièges connus »)
   - **A.** Laravel en natif (PHP 8.5 installé), PostgreSQL en conteneur. Rapide, mais il faut
     activer `pdo_pgsql` dans le `php.ini`.
   - **B.** Tout en conteneurs dès le départ. Plus proche de la production, mais les montages de
     volumes depuis `C:\` sont lents sous Docker Desktop.
   - Recommandation : A pour développer, puis le jalon 6 pour conteneuriser avec Apache.
4. **Dépôt GitHub** : garder le nom `isagri_learning` ou prendre un nom neutre réutilisable pour
   d'autres candidatures (par exemple `laravel-svelte-postgres-lab`), et visibilité publique
   (pour le montrer en entretien) ou privée.
5. **Mes disponibilités réelles** d'ici jeudi, pour recaler le calendrier.

---

## Feuille de route

| Jalon | Durée visée | Statut |
|---|---|---|
| 0. Cadrage | 30 min | en cours (reste : dépôt distant) |
| 1. Socle et PostgreSQL | 1h | à faire |
| 2. Modèle de données et SQL | 1h30 | à faire |
| 3. API Laravel | 1h30 | à faire |
| 4. Front Svelte | 2h | à faire |
| 5. Intégration continue | 45 min | à faire |
| 6. Conteneuriser avec Apache | 1h | à faire |

Mets à jour la colonne « Statut » à chaque jalon terminé.

### Jalon 0. Cadrage

- Les décisions du premier échange.
- Vérifier sur les sources officielles les **dernières versions stables** (ni bêta ni RC) :
  Laravel, PHP, Svelte et SvelteKit, PostgreSQL (image Docker officielle `postgres`), Node LTS.
  Les noter avec la date dans `README.md`, et épingler les versions (pas de tag `latest`).
- `git init`, `.gitignore`, `.gitattributes` (fins de ligne LF), squelette du `README.md`, dossier
  `docs/`.
- Création du dépôt GitHub **après ma confirmation explicite**, pour pratiquer branches et pull
  requests tout au long du projet.

### Jalon 1. Socle et PostgreSQL

- `compose.yaml` avec PostgreSQL : version épinglée, volume nommé, `healthcheck`.
- `.env` jamais versionné, `.env.example` versionné.
- Projet Laravel dans `backend/`, connexion `pgsql`, première migration.
- Prise en main de `psql` dans le conteneur : `\l`, `\dt`, `\d table`, `\x`, `\q`.
- **Entretien** : PostgreSQL face à MySQL, rôle d'une migration, pourquoi `.env` n'est pas
  versionné.

### Jalon 2. Modèle de données et SQL (priorité PostgreSQL)

- Migrations avec clés étrangères, unicité composée, contrainte `CHECK`, index.
- Factories et seeders avec un volume réaliste (quelques milliers de lignes), sinon les index ne
  montrent rien.
- Exercices SQL écrits par moi dans `psql`, conservés et commentés dans `docs/sql/` :
  - jointures, `LEFT JOIN ... WHERE ... IS NULL` et `NOT EXISTS` pour trouver les absents ;
  - `GROUP BY` et `HAVING` ;
  - fonction de fenêtre pour un top N par groupe (`ROW_NUMBER() OVER (PARTITION BY ...)`) ;
  - transaction avec `BEGIN`, `COMMIT` et `ROLLBACK` ;
  - `EXPLAIN ANALYZE` avant et après la création d'un index.
- **Entretien** : jointures, index composite et ordre des colonnes, diagnostic d'une requête
  lente, ACID, modélisation d'un domaine avec ses cardinalités.

### Jalon 3. API Laravel

- `php artisan install:api`, routes d'API, contrôleurs fins, `FormRequest`, API Resources,
  pagination, logique métier dans une classe de service ou d'action.
- Le problème N+1 : le provoquer, le détecter avec `Model::preventLazyLoading()`, le corriger
  avec `with()`.
- Tests de fonctionnalité PHPUnit sur une base PostgreSQL de test dédiée.
- Savoir lire un Laravel plus ancien : depuis Laravel 11, plus de `app/Http/Kernel.php`, la
  configuration des middlewares passe par `bootstrap/app.php`. Une base de code existante peut
  dater d'avant.
- **Entretien** : cycle de vie d'une requête, N+1, validation, où placer la logique métier,
  codes HTTP justes (200, 201, 204, 404, 422).

### Jalon 4. Front Svelte (priorité Svelte)

- Création avec `npx sv create` : TypeScript, Vitest, Playwright, ESLint, Prettier, et l'add-on
  d'outils IA (serveur MCP Svelte), comme dans `../svelte-learning`.
- Composants écrits par moi : liste paginée, fiche de détail, formulaire de création qui affiche
  les erreurs de validation renvoyées par l'API (code 422).
- Runes `$state`, `$derived`, `$effect`, `$props`, état partagé dans un fichier `.svelte.ts`.
- `fetch` bien géré : `response.ok` (un 404 ou un 500 ne rejette pas la promesse), erreurs
  réseau, état de chargement.
- En développement, un proxy Vite (`server.proxy`) évite le CORS : comprendre pourquoi.
- Un test Vitest de composant.
- **Savoir lire l'ancienne syntaxe Svelte 3 et 4** (`export let`, `$:`, stores préfixés par `$`),
  probablement présente dans une base de code existante. J'écris en Svelte 5, mais je dois
  comprendre l'ancien.
- **Entretien** : Svelte face à React, réactivité par les runes, rôle de SvelteKit, comment je me
  forme sur un nouveau framework.

### Jalon 5. Intégration continue

- GitHub Actions, déclenché sur les pull requests et sur `main` :
  - job backend : PHP, service PostgreSQL, migrations, PHPUnit, Pint ;
  - job frontend : `npm ci`, `check`, `lint`, tests, `build`.
- Cycle complet au moins une fois : branche, pull request, CI verte, fusion.
- **Entretien** : merge ou rebase, annuler un commit déjà poussé (`git revert`), différence entre
  intégration continue, livraison continue et déploiement continu.

### Jalon 6. Conteneuriser avec Apache

- `Dockerfile` backend sur l'image officielle `php:<version>-apache` : `DocumentRoot` sur
  `public/`, `mod_rewrite`, `AllowOverride All`, extension `pdo_pgsql`, droits de `www-data` sur
  `storage/` et `bootstrap/cache/`.
- `compose.yaml` complet : `db`, `backend`, et `frontend` si l'architecture A est retenue (build
  statique servi par un serveur web).
- **Entretien** : déployer Laravel sur Apache, erreur 500 en production et où lire les journaux,
  commandes Linux utiles.

### Après l'entretien

- Authentification avec Sanctum, autorisations avec des Policies.
- File d'attente : import d'un fichier CSV en tâche de fond, worker supervisé.
- Tests Playwright de bout en bout.
- Livraison continue : image Docker publiée sur GitHub Container Registry à chaque fusion.
- Recherche approchée avec l'extension `pg_trgm`, colonnes `JSONB`.

---

## Structure cible

```
isagri_learning/
├── CLAUDE.md
├── README.md               # installation, lancement, versions épinglées
├── compose.yaml
├── .env.example
├── .gitattributes
├── .gitignore
├── .github/workflows/      # CI
├── backend/                # Laravel
├── frontend/               # SvelteKit, si architecture A
└── docs/
    ├── DECISIONS.md        # chaque choix, les options écartées, le pourquoi
    ├── APPRENTISSAGE.md    # mon carnet de révision pour jeudi
    └── sql/                # mes exercices SQL commentés
```

---

## Conventions de code

- **Identifiants en anglais** (classes, tables, colonnes, variables), pour suivre les conventions
  de Laravel et d'Eloquent, notamment les pluriels de tables. Interface, documentation et commits
  en français.
- **PHP** : style Laravel Pint. Contrôleurs fins, validation dans des `FormRequest`, logique
  métier dans des classes dédiées.
- **Svelte** : Svelte 5 et runes uniquement pour le code écrit. Consulte le serveur MCP Svelte
  pour la documentation et passe tout code Svelte dans `svelte-autofixer`.
- **Tests** : PHPUnit côté backend, Vitest côté frontend. Toute règle métier et tout bug corrigé
  ont leur test.

---

## Git et GitHub

- Commits conventionnels en français : `type(portée): sujet à l'impératif`. Types : `feat`,
  `fix`, `docs`, `chore`, `refactor`, `test`, `ci`. Portées : `backend`, `frontend`, `db`,
  `docker`, `ci`, `docs`.
- **Un commit égale un changement cohérent.** Pas de commit fourre-tout.
- Une branche par fonctionnalité, fusion par pull request une fois la CI verte.
- En mode guidé, **c'est moi qui tape les commandes Git** : tu me dis quoi faire et pourquoi. En
  mode démo, tu peux committer toi-même.
- **Jamais de secret committé** : `.env` ignoré, mots de passe de test uniquement.
- **Sur confirmation explicite uniquement** : création du dépôt distant, changement de
  visibilité, push forcé, suppression d'une branche distante.

---

## Pièges connus sur ce poste

> Environnement vérifié le 2026-09-29 : Windows 11, PowerShell 5.1, Docker 29.5 et Compose 5.1,
> PHP 8.5.6 natif dans `C:\devtools\php-8.5.6-Win32-vs17-x64`, Composer 2.10, Node 24.19,
> npm 11.17, Git 2.56, GitHub CLI 2.97. Pas de `psql` natif : passer par le conteneur. La seule
> distribution WSL est celle de Docker Desktop.

- **PHP natif sans pilote PostgreSQL** : `pdo_pgsql`, `pgsql` et `intl` ne sont pas chargés.
  Décommenter les lignes `extension=` correspondantes dans le `php.ini`, sinon Laravel répond
  « could not find driver ».
- **Fins de ligne** : un script copié dans un conteneur Linux avec des fins de ligne CRLF échoue
  (`no such file or directory` sur un fichier pourtant présent). Imposer LF via `.gitattributes`.
- **Montages de volumes lents** : un montage depuis `C:\` vers un conteneur traverse la VM WSL2
  et ralentit fortement Laravel, à cause des milliers de fichiers de `vendor/`. D'où le
  développement en natif, et jamais de `vendor/` ni de `node_modules/` monté depuis Windows.
- **Rechargement à chaud de Vite dans Docker** : les événements de fichiers de Windows ne
  traversent pas les montages. Faire tourner le front en natif pendant le développement.
- **Accent dans le chemin** (`Développement`) : si un outil échoue sur un chemin, suspecter
  l'encodage avant le reste.

---

## Ressources

- **Fiche de préparation de l'entretien**, hors dépôt :
  `C:\jarvis\projets\pro\recherche-entreprise\docs\2026-10-01-preparation-entretien-isagri-c2j.md`.
  Sections 8 (questions techniques probables) et 9 (plan pour combler Svelte et PostgreSQL).
  Lis-la pour aligner tes questions de contrôle. **N'en recopie rien dans ce dépôt** : elle
  contient des informations personnelles.
- **Premier projet Svelte** : `../svelte-learning`.
- **Documentations officielles** : laravel.com/docs, svelte.dev/docs, postgresql.org/docs,
  docs.docker.com, docs.github.com/actions. Toujours préférer la documentation de la version
  installée à ta mémoire, les versions récentes ont pu changer.

---

## Préparer jeudi

Avant mercredi 20h, aide-moi à produire :

1. **Un pitch de deux minutes** : le but du projet, l'architecture, un choix technique
   argumenté, une difficulté rencontrée et sa résolution.
2. **Une présentation honnête du rôle de l'IA** : un projet d'entraînement monté en deux jours
   pour pratiquer la stack de l'offre, avec un agent IA comme mentor, le SQL et les composants
   Svelte écrits par moi. Cette phrase n'est valable que si elle est vraie : c'est aussi pour ça
   que la règle fixe des modes existe.
3. **Une séance d'entraînement** : dix questions tirées de `docs/APPRENTISSAGE.md` et de la
   fiche, posées une par une comme en entretien, réponses corrigées après chacune.
4. **Des exercices sur table** : trouver les défauts d'un extrait PHP (N+1, injection, absence
   de validation, logique dans le contrôleur), écrire une requête SQL avec jointure et agrégat,
   modéliser un petit domaine au tableau.

---

## Décisions prises

> Prises le 2026-09-29. Détail et options écartées dans `docs/DECISIONS.md`.

- **Architecture** : A, API Laravel dans `backend/` et SvelteKit en SPA (`adapter-static`) dans
  `frontend/`. Même origine en production (Apache sert le front et `/api`), proxy Vite en
  développement. Authentification reportée après l'entretien.
- **Domaine métier** : suivi de dossiers annuels (organisations, clients, dossiers par exercice,
  documents, gestionnaires). Vocabulaire neutre, identifiants en anglais.
- **Environnement de développement** : A, PHP et Node en natif, PostgreSQL en conteneur.
  Conteneurisation complète au jalon 6.
- **Dépôt GitHub** : `laravel-svelte-postgres-lab`, public, création sur confirmation explicite.
  Ce CLAUDE.md reste versionné, sans chemin contenant le nom d'utilisateur.
- **Modes** : démo pour la plomberie (Git, Docker, configuration), guidé dès la première
  migration.
- **Bonus hors feuille de route** : basculer un projet Laravel existant sur PostgreSQL, seulement
  si un jalon finit en avance.
- **Versions épinglées** : vérifiées le 2026-09-29, voir `README.md`.
- **Disponibilités** : non précisées, le calendrier reste la proposition par défaut.

---

## Tenue de ce fichier

- Mets à jour « Décisions prises » et la colonne « Statut » de la feuille de route dès qu'elles
  changent.
- **Après l'entretien du 2026-10-01** : retirer « Calendrier jusqu'à l'entretien » et
  « Préparer jeudi », et faire de ce projet un bac à sable d'apprentissage durable, avec la
  section « Après l'entretien » comme nouvelle feuille de route.

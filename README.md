# laravel-svelte-postgres-lab

Projet d'entraînement fullstack : une API Laravel, un front SvelteKit en SPA et une base
PostgreSQL, sur un domaine métier générique de suivi de dossiers annuels.

> Projet d'apprentissage mené avec un agent IA dans le rôle de mentor. Le SQL et les composants
> Svelte sont écrits à la main. Les choix et leurs raisons sont dans
> [`docs/DECISIONS.md`](docs/DECISIONS.md).

## Stack et versions

Dernières versions stables (ni bêta ni RC), vérifiées le **2026-09-29** sur les sources
officielles.

| Composant | Version | Source |
|---|---|---|
| PHP | 8.5.11 | php.net |
| Laravel (framework) | 13.34.0 | github.com/laravel/framework |
| PostgreSQL | 18.6, image `postgres:18.6-trixie` | postgresql.org, Docker Hub |
| Node.js (LTS) | 24.21.0 | nodejs.org |
| Svelte | 5.57.1 | npm |
| SvelteKit | 2.70.3 | npm |
| `@sveltejs/adapter-static` | 3.0.10 | npm |
| CLI `sv` | 0.17.1 | npm |

Les images Docker sont épinglées par tag de version, jamais `latest`. Les dépendances PHP et
JavaScript sont figées par `composer.lock` et `package-lock.json`.

## Prérequis

- PHP 8.5 avec les extensions `pdo_pgsql`, `pgsql` et `intl`
- Composer 2
- Node.js 24 LTS et npm
- Docker avec Docker Compose

## Installation

> À compléter au fil des jalons.

## Structure

```
.
├── compose.yaml            # PostgreSQL (puis backend et frontend au jalon 6)
├── .env.example            # modèle de configuration, sans secret
├── .github/workflows/      # intégration continue
├── backend/                # API Laravel
├── frontend/               # SvelteKit en SPA
└── docs/
    ├── DECISIONS.md        # chaque choix, les options écartées, le pourquoi
    ├── APPRENTISSAGE.md    # carnet de révision
    └── sql/                # exercices SQL commentés
```

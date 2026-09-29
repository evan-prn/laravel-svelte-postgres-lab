# Carnet d'apprentissage

> Mon carnet de révision : pour chaque jalon, les concepts, les commandes utiles, les pièges
> rencontrés, et les questions d'entretien avec la bonne réponse.

---

## Jalon 0. Cadrage

### Concepts

- **Fins de ligne.** Windows écrit CRLF (`\r\n`), Linux LF (`\n`). Sous Windows,
  `core.autocrlf=true` convertit en CRLF à l'extraction. Dans `.gitattributes`,
  `* text=auto eol=lf` a priorité sur ce réglage : les fichiers texte restent en LF, dans le
  dépôt comme dans le dossier de travail. Le réglage voyage avec le dépôt, alors que
  `core.autocrlf` dépend de chaque poste.
- **`.env` non versionné, `.env.example` versionné.** `.env` contient les secrets et la
  configuration propre à chaque environnement (poste, CI, production). `.env.example` documente
  les clés attendues, sans valeur sensible, pour qu'un nouveau venu sache quoi remplir.
- **Épingler les versions.** Le tag `latest` change sans prévenir : le même `compose.yaml`
  donnerait une base différente demain. Tags de version pour les images, fichiers de
  verrouillage (`composer.lock`, `package-lock.json`) pour les dépendances.
- **Stable, LTS, Current.** Une version stable n'est ni bêta ni RC. Pour Node, seules les
  versions paires deviennent LTS (support long) ; la branche « Current » bouge encore.

### Commandes

```bash
git init -b main                 # créer le dépôt avec main comme branche initiale
git ls-files --eol               # fin de ligne de chaque fichier : index (i/) et dossier de travail (w/)
git check-attr -a -- README.md   # attributs .gitattributes appliqués à un fichier
git config --get core.autocrlf   # réglage local des fins de ligne
```

### Pièges

- Git pour Windows crée `master` par défaut (`init.defaultBranch`) : préciser `-b main`.
- Un script shell en CRLF dans un conteneur Linux échoue avec « no such file or directory » ou
  `bad interpreter` : le `\r` fait partie du nom de l'interpréteur lu sur la première ligne.
- `Host key verification failed` au premier `git push` en SSH : l'empreinte du serveur n'est pas
  dans `~/.ssh/known_hosts`. SSH refuse par défaut un hôte inconnu, pour se protéger d'une
  attaque de l'homme du milieu. Deux solutions : ajouter l'empreinte après l'avoir comparée à
  celle publiée par GitHub, ou pousser en HTTPS (`git remote set-url origin https://...`).
- `gh repo create` crée le remote avec le protocole configuré dans `gh` : il peut différer de
  celui des autres dépôts du poste.

### Questions d'entretien

> Réponses modèles : à s'entraîner à dire à voix haute, avec ses propres mots.

**« Un `entrypoint.sh` échoue dans le conteneur avec *no such file or directory*, alors que le
fichier est présent. Pourquoi, et comment l'éviter pour toute l'équipe ? »**

Le script a été enregistré en CRLF sous Windows. La première ligne `#!/bin/sh\r` fait chercher un
interpréteur nommé `sh\r`, qui n'existe pas. Pour toute l'équipe : un `.gitattributes` versionné
avec `* text=auto eol=lf`, appliqué sur chaque poste quel que soit `core.autocrlf`. Pour corriger
les fichiers déjà commités : `git add --renormalize .`, puis vérifier avec `git ls-files --eol`.

**« Pourquoi ne jamais écrire `postgres:latest` ? Et à quoi sert `composer.lock` si
`composer.json` indique déjà les versions ? »**

`latest` change à chaque sortie : un simple `docker compose pull` peut faire passer la base à la
version majeure suivante, et PostgreSQL refuse de démarrer sur les fichiers d'une autre version
majeure sans migration (`pg_upgrade`, ou sauvegarde puis restauration). Le build n'est plus
reproductible. `composer.json` exprime des contraintes (`^13.0` accepte toute 13.x) ;
`composer.lock` fige la version exacte de chaque paquet, dépendances indirectes comprises.
`composer install` suit le lock : même code sur chaque poste, en CI et en production.
`composer update` recalcule et réécrit le lock.

**« Votre front est une SPA qui appelle une API Laravel. On va avoir des problèmes de CORS. »**

CORS ne s'applique qu'entre origines différentes (schéma, domaine ou port). En production, Apache
sert le front statique et l'API sous `/api` sur le même domaine : même origine, pas de CORS. En
développement, Vite et Laravel tournent sur deux ports, mais le proxy Vite (`server.proxy`)
relaie `/api` côté serveur : le navigateur ne voit qu'une origine. Si le front et l'API
changeaient un jour de domaine, on configurerait les origines autorisées côté Laravel. CORS est
une protection du navigateur : `curl` ou Postman n'y sont pas soumis.

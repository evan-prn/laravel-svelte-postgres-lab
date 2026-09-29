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

### Questions d'entretien

> À compléter après les questions de contrôle du jalon.

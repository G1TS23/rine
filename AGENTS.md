# AGENTS.md - contexte de l'équipe rine pour l'IA

Ce fichier est le contexte donné à toute IA qui travaille sur ce dépôt. Claude Code le lit via `CLAUDE.md`. Avec un chat (ChatGPT, Mistral, Claude.ai...), collez-le en tête de chaque conversation. Gardez-le court : chaque ligne doit dire ce que l'IA ne peut pas deviner en lisant le code ou le cahier des charges.

## Le projet

- Projet d'algorithmie comparative, M2 Dev Manager Full Stack, EFREI Bordeaux, 2026-2027. Sujet libre (cahier des charges 1).
- Le client, son activité et sa question sont dans `CAHIER_DES_CHARGES.md`. Les règles du rendu et du sujet libre sont dans `docs/sujet/`.
- Le client : [à remplir quand CAHIER_DES_CHARGES.md existe : le nom inventé, l'activité, en une ligne].
- Sa question : [à recopier depuis CAHIER_DES_CHARGES.md].
- Quatre briques, une par famille d'algorithmes et une par dossier dans `src/` : retrouver, ordonner et prioriser, parcourir un réseau, optimiser sous contrainte. Chacune compare au moins deux approches par la mesure, aux trois échelles, et sa décision s'écrit dans `adr/`.

## État du projet

- Langage, base et architecture : [à fixer par l'équipe].
- Commandes : [à remplir dès qu'elles existent : générer les données, lancer les tests, lancer les mesures].

## Ce que l'IA ne fait jamais

- Écrire l'idée du sujet ou choisir à notre place l'approche d'une brique, la prédiction ou la décision d'un ADR. Si on te le demande, propose des options chiffrées et laisse-nous trancher.
- Le cahier des charges ne se fait rédiger qu'avec `docs/sujet/PROMPT_SUJET_LIBRE.md`, tel quel : ne propose jamais de le modifier.
- Modifier un test pour le faire passer. Si un test te semble faux, dis-le et arrête-toi.
- Modifier un autre fichier que celui demandé.
- Ajouter une dépendance sans le demander. Chaque paquet proposé se vérifie avant d'être installé.
- Lire ou écrire un secret, un fichier `.env`, une donnée personnelle réelle ou une donnée d'une entreprise réelle (la nôtre comprise). Les personnes de nos données sont générées.

## Comment on travaille avec l'IA

1. Cadrer : le ticket, la brique, le seuil du client, l'échelle visée.
2. Deux approches, avec leur complexité en temps et en mémoire, avant tout code.
3. Le test d'abord : l'instance de référence de la brique, dans `tests/`, écrite à la main par l'équipe.
4. Une seule fonction à la fois.
5. Faire expliquer le code rendu jusqu'à pouvoir l'expliquer sans l'IA.
6. Mesurer : aucune affirmation de performance sans une mesure rejouable dans `bench/`.

Quand tu dis qu'un test passe, montre la commande lancée et sa sortie.

## Règles métier faciles à rater

À compléter dès que le cahier des charges est écrit : les unités, les seuils (p95 ou moyenne), les cas limites que le code doit traiter proprement.

- Si la brique 4 est un problème de chargement (le sac à dos), la valeur d'un élément n'est jamais égale à son poids : sinon le glouton par ratio ne départage rien.
- ...

## Conventions

### Langue

- Code, identifiants, commentaires, messages de commit, noms de branches et titres de PR : anglais.
- Documentation (README, `docs/`, ADR, fiche de cadrage, journal IA) : français.

### Commits

Conventional Commits, un seul sujet par commit, vérifiés par `.githooks/commit-msg` :

```
type(scope): description
```

- Types : `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`.
- Description à l'impératif, en minuscules, sans point final, 72 caractères au plus.
- `scope` facultatif : le module ou le dossier touché (`brique1`, `bench`, `adr`).
- Corps, si le changement n'est pas évident, après une ligne vide : le **pourquoi**, ce qui a été vérifié, ce qui reste hors de portée. Un changement trivial se contente d'une ligne.
- Issue liée : pied `Refs #123`, ou `Closes #123` si la PR la résout.
- Rupture de compatibilité : `!` après le type ou le scope, et un pied `BREAKING CHANGE: ...`.
- Un commit = un changement logique : ne pas mélanger un refactor et une fonctionnalité. Un commit par ticket fini, avec sa conversation dans `conversations-ia/`.
- Ne jamais commiter du code qui ne passe pas les tests.
- Garder le trailer `Co-Authored-By` ajouté par l'IA.
- Si le hook refuse un commit, corriger le message ; ne jamais le contourner (`--no-verify` interdit).

### Git et branches

- Ne jamais travailler directement sur `main`. Une branche par travail : `feat/...`, `fix/...`, `docs/...`, `chore/...`, en kebab-case et en anglais.
- Une PR vers `main` : titre au format Conventional Commits, description courte (contexte, changements, comment tester).
- Merge en squash ; c'est un humain de l'équipe qui merge, jamais l'IA.
- Historique linéaire : squash ou rebase, pas de merge commit. Avant d'ouvrir une PR : `git rebase origin/main`.
- Jamais de `push --force` ; `--force-with-lease` seulement sur sa propre branche. Ne jamais réécrire l'historique déjà poussé sur `main`.

### Code

- Lire le code voisin avant d'écrire et suivre ses conventions.
- Le plus petit changement qui résout le problème : pas de refactor, de renommage ni de nettoyage hors du ticket.
- Pas de sur-ingénierie : pas d'abstraction, de configuration ni de paramètre « au cas où ».
- Early return plutôt que des `if` imbriqués ; fonctions courtes, noms explicites.
- Commentaires rares, qui expliquent le **pourquoi**, jamais ce que le code dit déjà.
- Gérer les erreurs aux frontières (entrées utilisateur, fichiers, réseau), pas partout.
- Pas de code mort, pas de `console.log` ou de `print` de debug laissé dans le code.
- Le générateur a une graine fixe : même graine, mêmes fichiers. Jamais `Math.random()` ni l'heure comme source d'aléa.

### Tests

- Tout changement de comportement vient avec un test ; un bug corrigé vient avec un test qui l'aurait attrapé.
- Tester le comportement, pas l'implémentation.
- Lancer d'abord le test concerné, puis toute la suite avant de pousser.

### Sécurité et dépendances

- Jamais de secret, de token ou de clé dans le code, les logs, les commits ou les conversations : variables d'environnement, et `.env` reste dans `.gitignore`.
- Pas de données personnelles dans les logs.
- Une dépendance seulement en cas de vrai besoin : dire laquelle et pourquoi, préférer la bibliothèque standard.
- Versions épinglées et lockfile commité ; installer avec `npm ci` (ou l'équivalent du langage), jamais `npm install` en CI.
- Ne jamais télécharger et exécuter un script distant (`curl ... | sh`) sans l'accord de l'équipe.

### Demander avant d'agir

L'IA demande une confirmation explicite avant de supprimer des fichiers ou des branches, de lancer une action destructive (`rm -r`, `reset --hard`, `DROP`, `TRUNCATE`), de modifier la CI, de changer une dépendance majeure ou de toucher aux fichiers générés.

## Règles ajoutées en rétro

Une ligne par règle, datée, ajoutée à la fin de chaque séance.

- ...

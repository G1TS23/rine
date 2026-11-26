# Fiche de cadrage - rine

Algorithmie comparative - M2 Dev Manager Full Stack - EFREI Bordeaux - 2026-2027 - Alexandre STOPPINI

Copiez ce fichier à la racine du dépôt de votre équipe sous le nom `FICHE_DE_CADRAGE.md` puis remplissez-le ensemble. Il se pousse au plus tard le vendredi 27 novembre 2026 au soir. Un exemple rempli est dans `FICHE_DE_CADRAGE_exemple.md`.

Les choix de cette fiche sont ceux de l'équipe : les approches, les prédictions, les seuils. L'IA peut vous aider à la mettre en forme, pas à choisir à votre place. Remplacez chaque `...` ; une ligne incertaine vaut mieux qu'une case vide. Vous pourrez la corriger plus tard : dites-le dans un commit.

## 1. L'équipe

- Nom de l'équipe : rine
- Adresse du dépôt : ...

| Prénom et nom | Brique dont il ou elle est responsable |
| --- | --- |
| ... | ... |
| ... | ... |
| ... | ... |

En trio, chacun est responsable d'au moins une brique ; en duo, chacun en a deux. Le responsable porte les commits, l'ADR et les questions de sa brique : au pitch du 5 mars, c'est lui qui répond.

## 2. Le sujet

- Le sujet choisi (1 pour le sujet libre ; 2, 3, 4 ou 5) : 1, le sujet libre.
- Le client, en une ligne (l'entreprise, son activité) : ...
- Sa question, telle que le cahier des charges la pose : ...
- Ce que votre application vise à lui faire gagner, chiffré (la mesure le confirmera ou non) : ...

Sujet libre : votre cahier des charges est dans `CAHIER_DES_CHARGES.md`, à la racine du dépôt.

## 3. Les données

- D'où elles viennent : votre générateur, dans `bench/`, écrit avec le prompt de votre sujet (`PROMPT_GENERATEUR.md`) ; sa graine : ...
- Si vous partez de données ouvertes : la source et la licence : ...

| Échelle | Ce qu'elle représente | Les volumes (ceux du cahier des charges) |
| --- | --- | --- |
| Petite | ... | ... |
| Moyenne | ... | ... |
| Grande | ... | ... |

## 4. Les quatre briques

Une section par brique. Les deux approches se choisissent dans la liste du cours de la famille, recopiée dans votre cahier des charges ; une troisième peut venir d'ailleurs (un moteur de recherche dédié, une bibliothèque, une base de graphes), mesurée comme les autres. La prédiction s'écrit maintenant, avant toute mesure : une prédiction fausse ne coûte rien, elle se compare à la mesure dans l'ADR.

### Brique 1 - Retrouver : ...

| | |
| --- | --- |
| Le besoin du client, en une phrase | ... |
| Le critère d'acceptation (le seuil chiffré) | ... |
| La taille du problème aux trois échelles | petite : ... ; moyenne : ... ; grande : ... |
| Approche A | ... |
| Approche B | ... |
| Une troisième approche, si vous en mesurez une | ... |
| La prédiction : laquelle gagnera, à quelle échelle et pourquoi (la complexité) | ... |
| L'instance de référence : sa taille, ce qu'elle doit piéger | ... |
| Le ou la responsable | ... |

### Brique 2 - Ordonner et prioriser : ...

| | |
| --- | --- |
| Le besoin du client, en une phrase | ... |
| Le critère d'acceptation (le seuil chiffré) | ... |
| La taille du problème aux trois échelles | petite : ... ; moyenne : ... ; grande : ... |
| Approche A | ... |
| Approche B | ... |
| Une troisième approche, si vous en mesurez une | ... |
| La prédiction : laquelle gagnera, à quelle échelle et pourquoi (la complexité) | ... |
| L'instance de référence : sa taille, ce qu'elle doit piéger | ... |
| Le ou la responsable | ... |

### Brique 3 - Parcourir un réseau : ...

| | |
| --- | --- |
| Le besoin du client, en une phrase | ... |
| Le critère d'acceptation (le seuil chiffré) | ... |
| La taille du problème aux trois échelles | petite : ... ; moyenne : ... ; grande : ... |
| Approche A | ... |
| Approche B | ... |
| Une troisième approche, si vous en mesurez une | ... |
| La prédiction : laquelle gagnera, à quelle échelle et pourquoi (la complexité) | ... |
| L'instance de référence : sa taille, ce qu'elle doit piéger | ... |
| Le ou la responsable | ... |

### Brique 4 - Optimiser sous contrainte : ...

| | |
| --- | --- |
| Le besoin du client, en une phrase | ... |
| Le critère d'acceptation (le seuil chiffré) | ... |
| La taille du problème aux trois échelles | petite : ... ; moyenne : ... ; grande : ... |
| Approche A | ... |
| Approche B | ... |
| Une troisième approche, si vous en mesurez une | ... |
| La prédiction : laquelle gagnera, à quelle échelle et pourquoi (la complexité) | ... |
| L'instance de référence : sa taille, ce qu'elle doit piéger | ... |
| Le ou la responsable | ... |

Si votre brique 4 est un problème de chargement (le sac à dos), la valeur des éléments n'est pas partout égale à leur poids : sinon, tous les rapports valeur sur poids valent 1 et le glouton par ratio ne départage rien.

## 5. Le premier sprint, jusqu'au 2 décembre

Un ticket est une tâche qu'une personne finit en une séance au plus. Il est fini quand son test passe, que son responsable l'explique sans l'IA et que le journal IA est à jour.

| Ticket | Brique | Qui | Fini quand |
| --- | --- | --- | --- |
| ... | ... | ... | ... |
| ... | ... | ... | ... |
| ... | ... | ... | ... |

Les sprints suivants se planifient dans `BACKLOG.md`, au début de chaque séance.

## 6. L'IA dans l'équipe

- Le ou les outils que l'équipe utilise : ...
- Le fichier de contexte que vous donnez à l'IA (`CLAUDE.md`, `AGENTS.md` ou un texte à coller en tête de chaque conversation) et son chemin dans le dépôt : ...
- Où vous commitez l'export complet de vos conversations, à chaque séance : `conversations-ia/`, un fichier par conversation (voir `conversations-ia/README.md`).
- Une règle que l'équipe s'impose avec l'IA, en plus de celles du cours : ...

## 7. Vos questions pour le 2 décembre

- ...

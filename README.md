# rine

Projet d'algorithmie comparative de l'équipe rine. M2 Dev Manager Full Stack, EFREI Bordeaux, 2026-2027. Sujet libre (cahier des charges 1).

[Une phrase sur le client et sa question, quand `CAHIER_DES_CHARGES.md` sera écrit.]

## La commande unique

[À écrire : la commande qui génère la petite échelle puis lance les tests et les mesures. Elle doit tourner en moins de dix minutes : c'est celle que le prof rejoue avant le pitch.]

```bash
# à remplir
```

## La machine des mesures

| | |
| --- | --- |
| Processeur | ... |
| Mémoire | ... |
| Système | ... |
| Runtime et version | ... |

## Les trois échelles

| Échelle | Ce qu'elle représente | Volumes |
| --- | --- | --- |
| Petite | ... | ... |
| Moyenne | le volume réel du client aujourd'hui | ... |
| Grande | au moins dix fois la moyenne | ... |

## Les données

Générées par `bench/` avec une graine fixe : [graine]. Données ouvertes éventuelles : [source et licence]. Aucune donnée personnelle réelle.

## Le dépôt

| Chemin | Contenu |
| --- | --- |
| `CAHIER_DES_CHARGES.md` | le client, sa question, les quatre briques, les trois échelles |
| `FICHE_DE_CADRAGE.md` | l'équipe, les approches et les prédictions, le premier sprint |
| `BACKLOG.md` | les tickets de chaque sprint |
| `src/brique<N>-*/` | l'application, une brique par dossier |
| `bench/` | le générateur de données et les mesures |
| `tests/` | l'instance de référence de chaque brique, les cas extrêmes |
| `adr/` | un ADR par brique (gabarit : `adr/ADR-000-gabarit.md`) |
| `JOURNAL_IA.md` | par brique : demandé, gardé, rejeté, une erreur de l'IA trouvée |
| `conversations-ia/` | l'export complet de chaque conversation avec l'IA |
| `AGENTS.md`, `CLAUDE.md`, `.claude/` | le contexte et les réglages donnés à l'IA |
| `docs/` | les étapes du projet, l'idée du sujet, les documents du cours |

## Démarrer

Après le clone, activez le hook qui vérifie le format des messages de commit :

```bash
git config core.hooksPath .githooks
```

Les étapes à suivre, de la fiche de cadrage au pitch du 5 mars : `docs/ETAPES_PROJET.md`.

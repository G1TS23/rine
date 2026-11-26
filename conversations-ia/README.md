# Conversations avec l'IA

L'export complet de chaque conversation avec une IA, commité à chaque séance avec le code qu'elle a produit. Le prof les lit pour faire un retour à l'équipe sur sa façon de demander : on n'en retire rien, même les conversations ratées.

## Nommer un fichier

`<AAAA-MM-JJ>-<qui>-<brique>-<sujet>.md`, en minuscules et sans accents. Par exemple :

- `2026-11-26-olivier-cdc-cahier-des-charges.md`
- `2026-11-26-olivier-bench-generateur.md`
- `2026-12-02-<prenom>-brique1-index-trigrammes.md`

Pour `<brique>` : `brique1` à `brique4`, ou `cdc`, `bench`, `doc` hors briques.

## Exporter

- Claude Code : `/export conversations-ia/<nom-du-fichier>.md`
- Un chat (ChatGPT, Mistral, Claude.ai...) : copier toute la conversation dans un fichier `.md`, questions et réponses comprises.

## Avant de commiter

- Aucun secret, aucun token, aucune donnée personnelle réelle dans l'export.
- Une ligne dans `JOURNAL_IA.md` qui renvoie à ce fichier.

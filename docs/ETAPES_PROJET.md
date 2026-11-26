# Projet d'algorithmie comparative : les étapes à réaliser

Checklist tirée du deck J6, du sujet du rendu 2 (`EFREI_AlgoComparative_Rendu2_Projet_v3.pdf`), des cinq cahiers des charges, de `FICHE_DE_CADRAGE.md` et des deux prompts. Cochez au fil de l'eau.

Rappels qui valent pour toutes les étapes :

- Les choix restent à l'équipe : l'approche de chaque brique, la prédiction, la décision de l'ADR. L'IA peut coder, documenter, aider à préparer les oraux.
- Chaque conversation avec l'IA est exportée dans `conversations-ia/` (Claude Code : `/export <fichier>` ; un chat : copier dans un `.md`) et commitée avec le code qu'elle a produit.
- `JOURNAL_IA.md`, par brique : ce qui a été demandé, ce qui a été gardé ou rejeté, une erreur de l'IA trouvée.
- Aucun secret ni aucune donnée réelle dans le dépôt ou dans une conversation. Chaque paquet proposé par l'IA se vérifie avant d'être installé.
- Un ticket est fini quand son test passe, que son responsable l'explique sans l'IA et que le journal IA est à jour.

---

## Étape 0 - Jeudi 26 novembre, avant 12h30 : l'équipe

- [x] Former une équipe de trois (ou de deux).
- [x] Choisir un nom d'équipe.
- [x] Poster dans le chat de la visio : le nom de l'équipe, ses membres, le sujet qui vous tente.

## Étape 1 - Jeudi 26 novembre, atelier de 15h35 à 17h30 : cadrer

### 1.1 Choisir le sujet

- [x] Choisir parmi les cinq sujets :
  - 1 : sujet libre ;
  - 2 : Rive Droite Express ;
  - 3 : Panier Girondin ;
  - 4 : Festival des Quais ;
  - 5 : Tremplin Alternance.
- [ ] Relire le cahier des charges du sujet choisi (`EFREI_AlgoComparative_CDC<n>_*.pdf`) : la question du client, les quatre briques et leurs seuils, les trois échelles.

Sujet libre seulement :

- [x] Remplir en équipe, **sans IA**, la partie « VOTRE IDÉE » de `PROMPT_SUJET_LIBRE.md`.
- [ ] Faire rédiger le cahier des charges avec ce prompt, **tel quel** : le modifier est une utilisation non autorisée.
- [ ] Itérer jusqu'à ce que le tableau « Contrôle du cadre » soit entièrement OK (R1 à R9) ; relire chaque chiffre.
- [ ] Le copier dans `CAHIER_DES_CHARGES.md` à la racine du dépôt.
- [ ] Ajouter une ligne dans `JOURNAL_IA.md` et commiter l'export de la conversation dans `conversations-ia/`.
- [ ] Vérifier que le sujet ne fait pas partie de ce qui est refusé :
  - une brique plaquée ;
  - une variante des sujets 2 à 5 ;
  - un sujet déjà rendu ailleurs ;
  - des données réelles d'une entreprise ;
  - des approches choisies par l'IA.

### 1.2 Créer le dépôt de l'équipe

- [x] Créer le dépôt git et donner l'accès aux membres de l'équipe.
- [ ] Mettre en place la structure demandée :

```text
<équipe>/
  README.md              la commande unique, la machine, les trois échelles
  FICHE_DE_CADRAGE.md    l'équipe, le sujet, les quatre briques, le premier sprint
  CAHIER_DES_CHARGES.md  sujet libre seulement
  BACKLOG.md             les tickets de chaque sprint
  src/                   l'application, une brique par dossier
  bench/                 les mesures et leurs fichiers ; le générateur de données
  tests/                 l'instance de référence de chaque brique, les cas extrêmes
  adr/                   un ADR par brique
  JOURNAL_IA.md          par brique : demandé, gardé, rejeté, une erreur de l'IA trouvée
  conversations-ia/      l'export complet des conversations avec l'IA
```

- [ ] Écrire le fichier de contexte donné à l'IA : `CLAUDE.md`, `AGENTS.md` ou un texte à coller en tête de chaque conversation. Garder ce que l'IA ne peut pas deviner : les règles de l'équipe et les règles métier faciles à rater. Supprimer ce que le code et le cahier des charges disent déjà.
- [ ] (Optionnel) Créer le GitHub Project :
  - une milestone par sprint ;
  - un label par brique ;
  - une issue par ticket ;
  - un modèle d'issue avec la définition de « fini ».

  Le rendu exige quand même `BACKLOG.md` : garder un `BACKLOG.md` qui renvoie aux issues de chaque sprint, et poser la question au prof (section 7 de la fiche).

### 1.3 Remplir la fiche de cadrage

Copier `FICHE_DE_CADRAGE.md` à la racine du dépôt et remplacer chaque `...`. Une ligne incertaine vaut mieux qu'une case vide. Modèle du niveau attendu : `FICHE_DE_CADRAGE_exemple.md`.

- [ ] **1. L'équipe** : nom, adresse du dépôt, responsable de chaque brique (en trio, au moins une brique chacun ; en duo, deux).
- [ ] **2. Le sujet** : le client en une ligne, sa question telle que posée, le gain visé chiffré.
- [ ] **3. Les données** : le générateur dans `bench/`, sa graine, les données ouvertes éventuelles (source et licence), le tableau des trois échelles avec leurs volumes.
- [ ] **4. Les quatre briques**. Pour chacune :
  - [ ] le besoin du client en une phrase ;
  - [ ] le critère d'acceptation (seuil chiffré) ;
  - [ ] la taille du problème aux trois échelles ;
  - [ ] l'approche A et l'approche B, prises dans la liste du cours de la famille ; une troisième facultative, d'où qu'elle vienne, mesurée comme les autres ;
  - [ ] **la prédiction, écrite avant toute mesure** : laquelle gagnera, à quelle échelle, pourquoi (la complexité) ;
  - [ ] l'instance de référence : sa taille et ce qu'elle doit piéger ;
  - [ ] le ou la responsable.
  - [ ] Brique 4 en sac à dos : la valeur n'est jamais égale au poids.
- [ ] **5. Le premier sprint jusqu'au 2 décembre** : les tickets, leur brique, qui, « fini quand ». Un ticket tient en une séance au plus.
- [ ] **6. L'IA dans l'équipe** : les outils, le chemin du fichier de contexte, `conversations-ia/`, une règle de plus que celles du cours.
- [ ] **7. Les questions pour le 2 décembre** (par exemple : le backlog dans les issues GitHub au lieu de `BACKLOG.md` ?).

### 1.4 Le générateur de données

- [ ] Compléter `PROMPT_GENERATEUR.md` : remplacer `<LANGAGE>` et `<BLOC DU SUJET>`, puis trancher chaque `[à fixer par l'équipe]` (part des fautes de frappe, formule du score, nombre de places...).
- [ ] Le faire écrire dans une conversation neuve, en un seul fichier `bench/generer.<ext>`. Il prend une graine et une échelle et écrit un JSON par sorte d'objet dans `data/<échelle>/`.
- [ ] Relire le code et se faire expliquer ce qui n'est pas compris.
- [ ] Vérifier la graine : deux lancements avec la même graine donnent les mêmes empreintes. Selon le système :

  ```bash
  shasum data/petite/*.json
  ```

  sous Linux, `sha1sum` ; sous Windows, `Get-FileHash -Algorithm SHA1`.
- [ ] Vérifier les volumes de chaque échelle.
- [ ] Retrouver chaque cas limite dans les fichiers de la petite échelle.
- [ ] Vérifier que les champs « tirés à part » ne se calculent pas l'un à partir de l'autre (volume et montant, prix et préférence...).
- [ ] Commiter le générateur, l'export de la conversation et une ligne de `JOURNAL_IA.md`.

## Étape 2 - Vendredi 27 novembre au soir : le premier dépôt

- [ ] Pousser le dépôt avec `FICHE_DE_CADRAGE.md` remplie et le premier sprint planifié.
- [ ] Sujet libre : pousser aussi `CAHIER_DES_CHARGES.md`.
- [ ] Poster dans le chat le sujet et la répartition des briques.

## Étape 3 - Jusqu'au 1er décembre : finir le module

- [ ] Rendre les ADR des ateliers 10 et 11.
- [ ] Sujet libre : lire la réponse du prof (au plus tard le 30 novembre). Si le sujet est refusé, choisir un des sujets 2 à 5 avant le mercredi 2 décembre à 9h00.

## Étape 4 - Sprint 1, jusqu'au mercredi 2 décembre

- [ ] Pour chaque brique, écrire à la main l'instance de référence dans `tests/`, avec les résultats attendus. C'est le premier test de la brique ; il échoue tant que la brique n'existe pas.
- [ ] Rédiger le README : la commande unique et la machine. Un autre membre doit pouvoir la relancer sans aide.
- [ ] Faire chaque ticket avec l'IA en suivant les six gestes :
  - [ ] cadrer ;
  - [ ] deux approches ;
  - [ ] le test d'abord ;
  - [ ] une seule fonction ;
  - [ ] la faire expliquer ;
  - [ ] mesurer.
- [ ] Un commit par ticket fini, avec sa conversation.
- [ ] Sujet libre : préparer la présentation de l'instance de référence de chaque brique pour le 2 décembre.

## Étape 5 - Mercredi 2 décembre : séance de projet

- [ ] Début : la théorie (le backtracking) puis le planning du sprint 2 dans `BACKLOG.md` (ou dans les issues).
- [ ] Pendant : les tickets du sprint ; le travail à plusieurs agents IA sur plusieurs postes.
- [ ] Revue : chaque responsable montre ce qui tourne et explique une fonction écrite avec l'IA.
- [ ] Rétro : ce que l'IA a bien fait et mal fait ; ajouter une règle au fichier de contexte.
- [ ] Fin : un commit poussé, avec les conversations de la séance.

## Étape 6 - Décembre et janvier : le POC

- [ ] Un premier POC « quick & dirty » qui va de bout en bout : les données générées traversent les quatre briques.
- [ ] Implémenter les approches A et B de chaque brique.
- [ ] Mettre en place les mesures dans `bench/` aux trois échelles : temps (p95 quand le seuil l'exige), mémoire, qualité de la solution.
- [ ] Sujet libre : le générateur doit produire les trois échelles au plus tard le 8 février.
- [ ] Tenir `BACKLOG.md`, `JOURNAL_IA.md` et `conversations-ia/` à jour à chaque sprint.

## Étape 7 - Lundi 8 février : briques 1 et 2 livrées

- [ ] Briques 1 (retrouver) et 2 (ordonner et prioriser) qui fonctionnent, cas extrêmes compris.
- [ ] Les mesurer aux trois échelles.
- [ ] Rédiger l'ADR de chacune dans `adr/` : les approches comparées, la prédiction de la fiche confrontée à la mesure, la décision, les limites. Si rien ne casse à la grande échelle, donner, par la mesure ou par la complexité, le volume où la plus rapide casserait.

## Étape 8 - Mardi 9 février : briques 3 et 4 livrées, application assemblée

- [ ] Briques 3 (parcourir un réseau) et 4 (optimiser sous contrainte) livrées, mesurées, avec leur ADR.
- [ ] Brique 4 avec un critère de qualité : vérifier la part de la meilleure solution à la petite échelle, où la référence exacte se calcule (backtracking ou force brute).
- [ ] Assembler l'application et la mesurer de bout en bout.
- [ ] Répondre chiffres à l'appui à la question du client.

## Étape 9 - Jusqu'au lundi 1er mars, 23h59 : le rendu final

- [ ] Chaque brique fonctionne, est conforme à son ADR et passe ses cas extrêmes : 2 points par brique, 8 au total.
- [ ] Vérifier la cohérence de l'ensemble et la documentation (2 points) : le README avec la commande unique et la machine, la source et la licence des données ouvertes éventuelles.
- [ ] Vérifier que la petite échelle tourne en moins de dix minutes avec la commande unique : le prof la rejoue avant le pitch.
- [ ] `conversations-ia/` complet et commité, `JOURNAL_IA.md` à jour pour chaque brique.
- [ ] Faire le dernier commit et le pousser avant 23h59.

## Étape 10 - Vendredi 5 mars : la défense et le pitch

Les créneaux et la durée de chaque passage seront donnés en février.

- [ ] Préparer le côté commercial :
  - le client et son problème en une phrase ;
  - la promesse chiffrée ;
  - pourquoi vous et pas une feuille de calcul.
- [ ] Préparer le côté technique : les choix et les mesures brique par brique, ce qui casse et quand.
- [ ] Chaque responsable s'entraîne à expliquer sa brique et à la modifier en direct (6 points d'oral).
- [ ] S'entraîner à vulgariser pour quelqu'un qui ne code pas (4 points d'oral) : par exemple se faire interroger par l'IA.
- [ ] Matin : défendre le projet devant un public qui ne code pas. Après-midi : le pitch façon « Shark Tank ».

---

## La note : 20 points, 50 % du module

| Partie | Points | Ce qui compte |
| --- | --- | --- |
| Oral : le projet et le code | 6 | les expliquer, les modifier si on le demande |
| Oral : la vulgarisation | 4 | expliquer à quelqu'un qui ne code pas |
| Rendu : les briques | 8 | 2 points par brique qui fonctionne, conforme à son ADR, cas extrêmes compris |
| Rendu : l'ensemble | 2 | la cohérence du projet et la documentation |

Contact : Alexandre Stoppini, sur Teams ou LinkedIn. Il répond dans l'heure sur des horaires normaux.

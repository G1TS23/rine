# Fiche de cadrage - Les Haltères (exemple rempli)

Algorithmie comparative - M2 Dev Manager Full Stack - EFREI Bordeaux - 2026-2027 - Alexandre STOPPINI

Cet exemple reprend le Club Atlantique, le découpage donné en exemple dans le cahier des charges 1. Il montre le niveau attendu ; il ne peut pas être choisi comme sujet. Les noms de l'équipe sont inventés.

## 1. L'équipe

- Nom de l'équipe : Les Haltères
- Adresse du dépôt : https://github.com/les-halteres/club-atlantique

| Prénom et nom | Brique dont il ou elle est responsable |
| --- | --- |
| Léa Martin | Brique 1, retrouver un adhérent |
| Hugo Bernard | Brique 2, la liste d'attente ; brique 4, le programme de la semaine |
| Inès Dubois | Brique 3, la salle la plus proche |

## 2. Le sujet

- Le sujet choisi : 1, le sujet libre.
- Le client : Club Atlantique, douze salles de sport en Gironde, 30 000 adhérents.
- Sa question : "Peut-on ouvrir les réservations à tous les adhérents en même temps ? Jusqu'à combien d'adhérents ?"
- Ce que l'application vise à lui faire gagner : ouvrir les réservations du dimanche à 20h à tous les adhérents d'un coup, sans panne, jusqu'à au moins 300 000 adhérents.

## 3. Les données

- D'où elles viennent : notre générateur, dans `bench/generer.ts`, graine 2026. Il produit les adhérents, les cours de la semaine, les demandes de réservation du dimanche et le réseau des transports.
- Données ouvertes : les arrêts et les lignes du réseau de transport de la métropole, en open data ; la source et la licence sont dans le README.

| Échelle | Ce qu'elle représente | Les volumes |
| --- | --- | --- |
| Petite | une salle | 2 500 adhérents, 100 cours par semaine |
| Moyenne | le réseau actuel, douze salles | 30 000 adhérents, 1 200 cours par semaine |
| Grande | une franchise nationale | 300 000 adhérents, 12 000 cours par semaine |

## 4. Les quatre briques

### Brique 1 - Retrouver : retrouver un adhérent à l'accueil

| | |
| --- | --- |
| Le besoin du client, en une phrase | À l'accueil, retrouver un adhérent par son nom, même mal orthographié, pendant qu'il attend devant le comptoir. |
| Le critère d'acceptation | Moins de 50 ms pour 95 recherches sur 100. |
| La taille du problème aux trois échelles | petite : 2 500 noms ; moyenne : 30 000 ; grande : 300 000 |
| Approche A | Map des préfixes |
| Approche B | index de trigrammes |
| Une troisième approche | index PostgreSQL pg_trgm |
| La prédiction | Pour un nom tapé sans faute, la Map des préfixes gagne à toutes les échelles : une lecture par lettre tapée. Pour une faute au milieu du nom ("Dubios" pour "Dubois"), elle ne trouve plus rien dès la quatrième lettre ; l'index de trigrammes retrouve Dubois, parce que les deux noms partagent encore des morceaux de trois lettres. Nous pensons que les trigrammes tiennent les 50 ms jusqu'à la grande échelle, parce qu'ils ne comparent la saisie qu'aux noms qui partagent ses morceaux et pas aux 300 000. |
| L'instance de référence | 20 adhérents, dont deux homonymes, un nom à particule et trois saisies avec faute ; les résultats attendus écrits à la main. |
| Le ou la responsable | Léa Martin |

### Brique 2 - Ordonner et prioriser : la liste d'attente d'un cours complet

| | |
| --- | --- |
| Le besoin du client, en une phrase | Quand un cours est complet, faire entrer les adhérents de la liste d'attente dans l'ordre, les abonnés premium d'abord. |
| Le critère d'acceptation | Toutes les demandes du dimanche entre 20h00 et 20h05 servies en moins d'une seconde au total. |
| La taille du problème aux trois échelles | petite : 1 500 demandes ; moyenne : 18 000 ; grande : 180 000 |
| Approche A | tas binaire |
| Approche B | file à seaux par niveau d'abonnement |
| Une troisième approche | aucune |
| La prédiction | La file à seaux gagne à la grande échelle : avec trois niveaux d'abonnement seulement, ranger et sortir un adhérent se fait en temps constant, contre un temps en log n pour le tas. À la petite échelle, l'écart ne se verra pas. |
| L'instance de référence | 12 demandes sur un cours de 8 places : deux premium arrivés en dernier, deux demandes à la même seconde. |
| Le ou la responsable | Hugo Bernard |

### Brique 3 - Parcourir un réseau : la salle la plus proche

| | |
| --- | --- |
| Le besoin du client, en une phrase | Proposer à l'adhérent la salle la plus proche de chez lui en transports en commun. |
| Le critère d'acceptation | La réponse en moins de 200 ms. |
| La taille du problème aux trois échelles | petite : 300 arrêts ; moyenne : 4 000 arrêts ; grande : 40 000 arrêts |
| Approche A | Dijkstra avec tas, arrêté à la première salle atteinte |
| Approche B | A* vers chaque salle |
| Une troisième approche | aucune |
| La prédiction | Dijkstra arrêté gagne quand les salles sont nombreuses : un seul parcours, qui s'arrête dès qu'il atteint une salle, contre un A* par salle (12 à la moyenne échelle). A* pourrait gagner s'il n'y avait qu'une ou deux salles à viser. |
| L'instance de référence | 9 arrêts et 2 salles, avec une salle plus proche à vol d'oiseau mais plus loin en transports. |
| Le ou la responsable | Inès Dubois |

### Brique 4 - Optimiser sous contrainte : le programme de la semaine

| | |
| --- | --- |
| Le besoin du client, en une phrase | Composer le programme d'un adhérent sous ses heures libres de la semaine, en maximisant ses préférences. |
| Le critère d'acceptation | Le programme en moins d'une seconde et au moins 95 % de la satisfaction du meilleur programme possible. |
| La taille du problème aux trois échelles | petite : 20 cours et 6 heures libres ; moyenne : 60 cours et 10 heures ; grande : 200 cours et 20 heures |
| Approche A | glouton par ratio (préférence par heure) |
| Approche B | programmation dynamique, la capacité comptée en quarts d'heure |
| Une troisième approche | backtracking, sur la petite échelle seulement, comme référence exacte |
| La prédiction | La programmation dynamique trouve toujours le meilleur programme ; sa table compte cours fois quarts d'heure cases, soit 200 fois 80 à la grande échelle, ce qui reste petit. Le glouton sera plus rapide mais ratera parfois le meilleur : nous pensons qu'il restera au-dessus des 95 %. Le backtracking explosera au-delà de 30 cours environ. |
| L'instance de référence | 5 cours et 2 heures libres, dont un cours long très apprécié qui piège le glouton ; la préférence n'est jamais égale à la durée. |
| Le ou la responsable | Hugo Bernard |

## 5. Le premier sprint, jusqu'au 2 décembre

| Ticket | Brique | Qui | Fini quand |
| --- | --- | --- | --- |
| Le générateur des adhérents, aux trois échelles, avec la graine 2026 | toutes | Léa | deux lancements donnent la même empreinte sha1 |
| L'instance de référence de la brique 1 et son test | 1 | Léa | le test échoue tant que la brique n'existe pas |
| Les instances de référence des briques 2 et 4 | 2, 4 | Hugo | les résultats attendus sont écrits à la main, vérifiés à deux |
| Le réseau des transports chargé depuis l'open data | 3 | Inès | 4 000 arrêts chargés, le temps de chargement mesuré |
| Le README : la commande unique, la machine | toutes | Inès | un membre de l'équipe la relance sur son poste sans aide |

## 6. L'IA dans l'équipe

- Les outils : Claude Code pour Léa, le chat gratuit pour Hugo et Inès.
- Le fichier de contexte : `AGENTS.md`, à la racine, lu par Claude Code et collé en tête de chaque conversation par les deux autres.
- L'export des conversations : `conversations-ia/`, un fichier par conversation, nommé par date et par brique.
- Notre règle : aucune fonction n'est commitée tant que son responsable ne sait pas l'expliquer sans l'IA.

## 7. Nos questions pour le 2 décembre

- Peut-on garder le backlog dans les issues GitHub plutôt que dans `BACKLOG.md` ?

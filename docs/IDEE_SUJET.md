# Notre idée de sujet, à remplir en équipe et sans IA

C'est la partie « VOTRE IDÉE » de `docs/sujet/PROMPT_SUJET_LIBRE.md`. On la remplit ici, à trois et sans IA, puis on la colle à la fin du prompt. Une ligne incertaine vaut mieux qu'une case vide : une idée vide est refusée.

Avant d'envoyer, on vérifie que l'idée n'est pas refusée d'avance :

- ce n'est pas une variante des sujets 2 à 5 : la livraison de colis ou de repas, la recherche dans une marketplace de produits locaux, la billetterie d'un festival, le rapprochement d'offres d'emploi et de candidats ;
- ce n'est pas un sujet déjà rendu dans un autre module ou un projet commencé ailleurs ;
- l'entreprise est fictive : aucun nom, code, donnée ou document d'une entreprise réelle, celle de notre alternance comprise ;
- chaque famille a un besoin naturel chez le client, sans brique plaquée.

## VOTRE IDÉE

Le nom de votre équipe : RINE

Le secteur ou le service dont vous partez : Cyclisme et plus précisément le bikepacking ou les courses d'ultra-distance

Ce qui vous en a donné l'idée (alternance, stage, service que vous utilisez ; sans nom réel) : On utilise un outil d'itinéraires pour planifier nos courses ou nos voyages, mais il est assez limité dans la pertinence des itinéraires proposés et il ne permet pas de prendre en compte les préférences personnelles de l'utilisateur (type de terrain, type de route, dénivelé, etc.).

Qui utilise la plateforme et pour quoi faire : Les utilisateurs sont des cyclistes qui souhaitent planifier leurs itinéraires avec des checkpoints ou sections obligatoires. L'objectif est de trouver le meilleur itinéraire possible en fonction des préférences de l'utilisateur et des contraintes imposées par les checkpoints. La carte d'Europe pour la grande échelle, et les paliers du département aux deux pays.

Ce qui coince aujourd'hui, selon vous : Les itinéraires proposés par l'outil qu'on utilise aujourd'hui ne sont pas toujours pertinents et ne prennent pas en compte les préférences personnelles de l'utilisateur.

La question que le client se pose, avec vos mots : Comment trouver le meilleur itinéraire selon mes préférences et mes checkpoints, et que traiter en premier quand l'urgence d'un ravitaillement change en course ?

Le besoin que vous voyez pour chaque famille (une ligne, même incertaine) :
- Retrouver : le cycliste saisit le nom d'un lieu (col, village, refuge, point d'eau) pour en faire un checkpoint, même avec une faute de frappe, dans le catalogue des lieux.
- Ordonner et prioriser : les K meilleurs ravitaillements devant le coureur. On prend n candidats dans un couloir devant lui (de 10⁴ à 5·10⁴ sur 2 000 km). Chacun reçoit un score : coût du détour, horaires d'ouverture, type de point.
- Parcourir un réseau : entre deux checkpoints consécutifs, trouver le chemin de moindre coût sur le réseau de routes et de pistes. Avec les détours intégrés : les détours optionnels deviennent un coût sur les arêtes ou des points de passage. Le coût d'une arête combine le temps, le dénivelé et la préférence de terrain.
- Optimiser sous contrainte : plan de ravitaillement. Choisir les arrêts le long de l'itinéraire sans jamais dépasser l'autonomie (par exemple X km d'eau), en minimisant le temps perdu en détours et en arrêts.

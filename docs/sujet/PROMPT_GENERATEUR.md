# Prompt : faire écrire le générateur de données de votre projet

Algorithmie comparative - M2 Dev Manager Full Stack - EFREI Bordeaux - 2026-2027 - Alexandre STOPPINI

Chaque équipe écrit son générateur de données, quel que soit son sujet. Vous pouvez le faire écrire par une IA avec ce prompt. Il contient un bloc commun et un bloc par sujet : c'est le bloc de votre sujet qui dit à l'IA quelles données produire.

## Les mots d'abord

- **Un générateur à graine fixe** produit des données pseudo-aléatoires à partir d'une valeur de départ, la graine : avec la même graine, il écrit les mêmes fichiers à chaque lancement. C'est ce qui rend vos mesures rejouables.
- **Une échelle** est un volume de données : petite, moyenne ou grande. Seul le volume change d'une échelle à l'autre.
- **Un cas limite** est une donnée rare qui fait échouer un code trop naïf : une adresse introuvable, deux éléments à égalité, un objet trop gros pour toute capacité.
- **Tirés à part** : deux champs dont l'un ne se calcule pas à partir de l'autre, comme le prix et la préférence d'un produit. Si la valeur de chaque élément est égale à son poids, tous les rapports valeur sur poids valent 1 et le glouton par ratio ne départage plus rien.
- **L'instance de référence** d'une brique est un jeu de données assez petit pour être résolu à la main. Elle ne sort pas du générateur : vous l'écrivez à la main dans `tests/` avec ses résultats attendus.

## Mode d'emploi

1. Ouvrez une conversation neuve dans l'IA de votre choix (la version gratuite suffit).
2. Collez le bloc commun de "DÉBUT DU PROMPT" à "FIN DU PROMPT". Remplacez `<LANGAGE>` par le langage de l'équipe et `<BLOC DU SUJET>` par le bloc de votre sujet, plus bas. Complétez chaque `[à fixer par l'équipe]` avant d'envoyer : ce sont vos décisions, pas celles de l'IA.
3. Relisez le code rendu, faites-vous expliquer ce que vous ne comprenez pas puis lancez-le deux fois avec la même graine.
4. Vérifiez que les deux lancements donnent les mêmes empreintes. Sous Linux : `sha1sum data/petite/*.json`. Sous macOS : `shasum data/petite/*.json`. Sous Windows, dans PowerShell : `Get-FileHash -Algorithm SHA1 data\petite\*.json`.
5. Vérifiez les volumes de chaque échelle et retrouvez chaque cas limite dans les fichiers de la petite échelle.
6. Commitez le générateur dans `bench/`, l'export complet de la conversation dans `conversations-ia/` et une ligne dans `JOURNAL_IA.md`.

---

DÉBUT DU PROMPT

Écris le générateur de données de notre projet d'algorithmie comparative, en <LANGAGE>.

Ce qu'il doit faire :
- Une seule commande qui prend une graine et une échelle (petite, moyenne ou grande), par exemple : générer 2026 moyenne.
- Avec la même graine, il écrit exactement les mêmes fichiers à chaque lancement. Il n'utilise aucune source d'aléa sans graine : ni l'heure ni Math.random() en JavaScript ni un générateur global non initialisé.
- Il écrit un fichier JSON par sorte d'objet dans data/<échelle>/.
- Il n'écrit que des données : aucun algorithme des briques, aucun index, aucune structure de recherche.

Ce que tu me rends :
- le code, dans un seul fichier bench/generer avec l'extension du langage ;
- la commande pour le lancer sous Windows, macOS et Linux ;
- une explication courte : comment la graine est utilisée et comment chaque cas limite est produit.

Ne décide rien à notre place : si une information manque dans le bloc ci-dessous, pose-nous la question au lieu de l'inventer.

<BLOC DU SUJET>

FIN DU PROMPT

---

## Sujet 1 : le sujet libre

```text
Notre sujet : <le nom de votre entreprise et son activité, d'après votre CAHIER_DES_CHARGES.md>.

Les trois échelles et leurs volumes : <recopiez le tableau "Les volumes et les trois échelles" de votre cahier des charges>.

Les objets et leurs champs : <recopiez la section "Les données" de votre cahier des charges>.

Ce qui rend les données réalistes : [à fixer par l'équipe : les heures de pointe, les fautes de frappe, les doublons, ce qui est fréquent et ce qui est rare].

Les cas limites à produire, dès la petite échelle : [à fixer par l'équipe : un par brique au moins].

Si notre brique 4 est un problème de chargement : la valeur et le poids de chaque élément sont tirés à part.
```

## Sujet 2 : Rive Droite Express

```text
Notre sujet : Rive Droite Express, la livraison en moins de deux heures sur la rive droite de Bordeaux.

Les données déjà fournies, à lire et non à générer : le référentiel des adresses et le réseau routier du dépôt du cours.

Les trois échelles :
- petite : une heure de pointe sur un quartier, 600 commandes, 10 coursiers ;
- moyenne : une journée sur Bordeaux, 3 000 commandes, 40 coursiers ;
- grande : une journée de soldes sur la métropole, 9 000 commandes, 120 coursiers.

Les objets et leurs champs :
- Commande : identifiant, horodatage de passage, adresse telle que le client l'a tapée, adresse attendue dans le référentiel, heure limite (deux heures après le passage), volume en litres, montant en euros.
- Coursier : identifiant, point de départ sur le réseau, capacité de sa caisse en litres.

Ce qui rend les données réalistes :
- à l'échelle moyenne, 600 des 3 000 commandes arrivent entre 18h et 19h ;
- une part des adresses est tapée avec une ou deux fautes (lettre oubliée, en trop ou remplacée, accent oublié) : [part à fixer par l'équipe] ;
- le volume et le montant d'une commande sont tirés à part.

Les cas limites à produire, dès la petite échelle :
- une adresse tapée qui n'existe pas dans le référentiel ;
- deux commandes à la même adresse dans la même minute ;
- une commande plus volumineuse que toutes les caisses ;
- deux commandes à la même heure limite.
```

## Sujet 3 : Panier Girondin

```text
Notre sujet : Panier Girondin, la recherche et le panier d'une marketplace de producteurs girondins.

Les données déjà fournies, à lire et non à générer : le référentiel des adresses de la métropole et le réseau routier du dépôt du cours.

Les trois échelles :
- petite : 4 000 produits, 120 producteurs, 10 000 recherches rejouées ;
- moyenne : 40 000 produits, 1 200 producteurs, 100 000 recherches rejouées ;
- grande : 400 000 produits, 6 000 producteurs, 1 000 000 de recherches rejouées.

Les objets et leurs champs :
- Produit : identifiant, nom, catégorie, producteur, prix en euros, note sur 5, stock.
- Producteur : identifiant, nom, adresse prise dans le référentiel.
- Recherche : le texte tapé lettre par lettre, avec ou sans fautes, et le produit visé.
- Client : identifiant, adresse prise dans le référentiel, budget de la semaine (40 euros par défaut), préférence de 1 à 10 pour une partie des produits.

Ce qui rend les données réalistes :
- des noms de produits locaux plausibles (fromages, légumes, vins, viandes), dont plusieurs partagent leur début ("camembert", "camomille") ;
- quelques produits très recherchés, la plupart rarement ;
- des fautes réalistes : accents oubliés, lettres doublées ou inversées ("camanbert") ;
- le prix et la préférence d'un produit sont tirés à part.

Les cas limites à produire, dès la petite échelle :
- une recherche d'une seule lettre ;
- un produit en rupture de stock ;
- un client sans aucun producteur à moins de trente minutes de route ;
- un produit préféré plus cher que le budget à lui seul.
```

## Sujet 4 : Festival des Quais

```text
Notre sujet : Festival des Quais, la billetterie d'un festival de trois jours sur les quais de Bordeaux.

Les trois échelles :
- petite : 2 000 billets, 5 000 connexions à l'ouverture des ventes, 200 groupes pour les navettes ;
- moyenne : 40 000 billets, 200 000 connexions, 4 000 groupes ;
- grande : 120 000 billets (trois jours), 1 000 000 de connexions, 12 000 groupes.

Les objets et leurs champs :
- Billet : code, nom du spectateur, type (jour, pass trois jours, prévente), mobilité réduite ou non, déjà scanné ou non.
- Connexion : horodatage à la milliseconde, acheteur, priorité (mobilité réduite, pass trois jours, prévente, aucune).
- Place en tribune : identifiant, tribune, rang, note de qualité, libre ou vendue ; nombre de places : [à fixer par l'équipe].
- Plan du site : des points (entrées, scènes, carrefours d'allées) et des allées (deux points, longueur en mètres, avec ou sans marches).
- Groupe : identifiant, nombre de personnes, nombre de personnes à mobilité réduite parmi elles, parking de départ.

Ce qui rend les données réalistes :
- les connexions se massent dans les premières secondes de l'ouverture des ventes puis retombent ;
- des noms de spectateurs tapés au guichet avec des fautes ;
- quelques allées avec marches, dont certaines sur le chemin le plus court vers une scène ;
- une part des groupes compte des personnes à mobilité réduite : [part à fixer par l'équipe] ; leur nombre est tiré à part de la taille du groupe.

Les cas limites à produire, dès la petite échelle :
- un billet inexistant et un billet déjà scanné ;
- une scène qu'on n'atteint sans marches que par un détour ;
- un groupe de 50 personnes tout juste et un groupe de plus de 50 ;
- deux connexions à la même milliseconde.
```

## Sujet 5 : Tremplin Alternance

```text
Notre sujet : Tremplin Alternance, le rapprochement des offres d'alternance et des candidats en Nouvelle-Aquitaine.

Les trois échelles :
- petite : 5 000 offres, 10 000 candidats, 400 compétences ;
- moyenne : 50 000 offres, 100 000 candidats, 400 compétences ;
- grande : 150 000 offres, 300 000 candidats, 400 compétences.

Les objets et leurs champs :
- Offre : identifiant, titre, description de quelques dizaines de mots, compétences demandées, ville.
- Candidat : identifiant, compétences acquises, ville.
- Recherche : les mots-clés tapés, avec ou sans fautes, et une offre attendue.
- Lien du graphe des compétences : la compétence prérequise, la compétence suivante, le nombre d'heures pour l'apprendre.
- Formation : identifiant, compétences apportées, durée en heures.
- La formule du score d'adéquation entre une offre et un candidat : [à fixer par l'équipe, par exemple la part des compétences de l'offre que le candidat possède].

Ce qui rend les données réalistes :
- quelques compétences très demandées, beaucoup de rares ;
- des titres d'offres plausibles (développeur, comptable, technicien de maintenance) ;
- des fautes dans les recherches ("dévelopeur") ;
- la durée d'une formation est tirée à part des compétences qu'elle apporte.

Les cas limites à produire, dès la petite échelle :
- un candidat sans aucune compétence ;
- une compétence qu'aucun chemin ne relie à celles d'un candidat ;
- une formation plus longue que le budget d'heures ;
- deux offres au même score pour un même candidat.
```

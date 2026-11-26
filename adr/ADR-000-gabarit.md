# ADR-000 - Titre de la décision (une ligne, à l'infinitif : "Retrouver un élément malgré les fautes de frappe")

Une page par brique. Copiez ce fichier en `ADR-00N-<brique>.md` et remplacez chaque bloc. Gabarit repris du module, adapté au projet.

- Brique : N, <famille>
- Responsable : ...

## 1. Contexte

Le besoin du client pour cette brique, les volumes aux trois échelles, le critère d'acceptation (le seuil chiffré du cahier des charges). Trois à cinq lignes.

## 2. Options comparées

Deux au moins, prises dans la liste du cours de la famille ; une troisième peut venir d'ailleurs, mesurée comme les autres. Une ligne par option, avec la complexité annoncée.

- Option A : ... Complexité annoncée : O(...).
- Option B : ... Complexité annoncée : O(...).
- Option C (facultative) : ... Complexité annoncée : O(...).

## 3. La prédiction, confrontée à la mesure

La prédiction recopiée de `FICHE_DE_CADRAGE.md`, telle qu'elle a été écrite avant la mesure, puis ce que la mesure en dit : juste, fausse ou à moitié, et pourquoi. Une prédiction fausse ne coûte rien.

## 4. Mesures

Le protocole en cinq lignes, puis le tableau, puis la courbe.

- Machine : processeur, mémoire, système, runtime et version.
- Jeux : la graine et les trois échelles du générateur.
- Répétitions et échauffement : combien.
- Statistique retenue : la médiane, ou le p95 si le seuil du client est un p95.
- Ce qui est mesuré : temps par appel, temps de construction, mémoire, qualité de la solution.

| Option | Petite | Moyenne | Grande | Mémoire | Seuil tenu ? |
| --- | --- | --- | --- | --- | --- |
| A | ... | ... | ... | ... Mo | ... |
| B | ... | ... | ... | ... Mo | ... |

Courbe : `bench/resultats/<horodatage>-<brique>.svg`.

Les cas extrêmes vérifiés : l'instance de référence de `tests/` et ce qu'elle piège.

## 5. Décision

Une phrase : l'option retenue et le critère qui a tranché.

## 6. Conséquences et limites

Ce que la décision coûte (mémoire, code, dépendance), ce qui n'a pas été mesuré. Trois à cinq lignes.

Domaine de validité : les paramètres que l'on a fait varier et leurs valeurs, ceux que l'on n'a pas fait varier, et à partir de quel volume la décision ne tient plus. Si rien ne casse à la grande échelle, le volume où la plus rapide casserait, par la mesure ou par la complexité.

## 7. En trois phrases pour le client

La même décision, sans un seul terme technique. Le client doit pouvoir la répéter à ses équipes.

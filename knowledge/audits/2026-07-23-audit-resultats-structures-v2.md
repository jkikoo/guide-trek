# Audit post-corrections des résultats structurés v2

Date : 2026-07-23

## Objet

Cet audit vérifie la version qui suit l'audit v1. Après la première refonte de l'affichage, des formulations trop directes restaient dans certaines checklists. Elles ont été corrigées sur les cas les plus risqués.

## Corrections appliquées après v1

### Météo

Les branches froid/pluie et hypothermie ne demandent plus simplement de "couper le vent" ou de "mettre hors du froid" comme si une protection existait forcément.

Formulations ajoutées :

- arrêter hors eau et hors exposition **si quelques mètres suffisent** ;
- chercher ou improviser une protection avec abri, vêtement, sursac, tarp, sac ou partage ;
- isoler du sol avec ce qui existe, même imparfaitement ;
- si aucune protection ne tient, préparer sortie courte, aide ou appel.

La branche visibilité faible ne suppose plus un point stable déjà disponible. Elle dit maintenant d'avancer seulement jusqu'au premier arrêt possible si aucun point stable n'est visible.

### Secours

Les branches d'appel et de réseau ne supposent plus une attente protégée déjà disponible. Elles parlent de créer une protection d'attente avec ce qui existe, même imparfaite, et de ne déplacer le groupe que pour quitter un danger supérieur.

### Eau / chaleur

Les branches chaleur ne demandent plus seulement "mets-toi à l'ombre". Elles distinguent :

- ombre si elle existe ;
- ombre improvisée ;
- réduction de l'exposition directe ;
- attente d'une période moins chaude si bouger empire la situation.

## Tests effectués

Contrôles techniques :

- parsing du script dans `index.html` : OK ;
- `git diff --check` : OK.

Scénarios testés en rendu HTML :

| Domaine | Scénario | Attendu |
|---|---|---|
| Météo | froid/pluie sans protection | bloc "Si aucune protection ne tient" et texte "avec ce qui existe" |
| Météo | orage sans abri fermé | bloc "Si aucun abri fermé n'est accessible" |
| Santé | altitude avec symptômes persistants | bloc "Terrain avant déplacement" |
| Secours | réseau proche mais groupe non protégé | bloc "Si l'attente n'est pas protégée" |
| Eau | chaleur persistante, eau très faible, pas de source/sortie | bloc "Si aucune eau, source ou sortie n'est confirmée" et ombre conditionnelle |
| Bivouac | froid sans abri | bloc "Abri de fortune" |
| Matériel | chaussure et réparation échouée | bloc "Fonction touchée" |
| Navigation | doute + nuit/batterie | bloc "Protocole STOP" |
| Nourriture | faiblesse + snacks + énergie basse | bloc "Inventaire commun" |
| Blessure | douleur de pied persistante | bloc "Test ou déplacement" |

## Etat après v2

La refonte atteint maintenant le cœur de l'objectif :

- l'utilisateur voit les faits retenus ;
- le résultat distingue mieux action immédiate, condition, alternative et surveillance ;
- les cas les plus dangereux où une recommandation pouvait demander l'impossible ont été corrigés ;
- l'exemple météo/pluie/froid sans abri reçoit une conduite dégradée au lieu d'un simple "mets-toi à l'abri".

## Résidu acceptable

Toutes les 117 branches n'ont pas été réécrites une par une en objets structurés. Le rendu structuré est généré par domaine et par réponses cochées, ce qui couvre les risques transversaux sans multiplier immédiatement le code.

Ce résidu est acceptable pour cette itération parce que :

- les branches continuent de produire un avis correct ;
- les blocs ajoutés interceptent les principaux cas impossibles ;
- les checklists critiques météo, secours et eau ont été reformulées ;
- les tests couvrent les failles relevées par l'audit initial.

## Recommandation suivante

La prochaine amélioration, non bloquante, serait de migrer progressivement les branches les plus utilisées vers un format explicite `R({ c, t, w, facts, blocks, s })`. Cela permettrait de choisir les faits et les blocs au cas par cas, au lieu de s'appuyer seulement sur la génération par domaine.

Priorité proposée :

1. météo froid/pluie ;
2. santé malaise/altitude ;
3. secours attente ;
4. eau chaleur ;
5. bivouac froid ;
6. navigation STOP ;
7. blessure marche impossible ;
8. matériel fonction critique.

## Verdict

Validation v2 : les recommandations finales sont nettement plus complètes et contextualisées. Les actions idéales sont maintenant accompagnées d'une alternative quand elles ne sont pas possibles. Aucune correction bloquante supplémentaire n'est ressortie des tests ciblés de cette itération.

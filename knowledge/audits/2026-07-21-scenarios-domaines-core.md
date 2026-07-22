# Scénarios de test — domaines core

Ces scénarios servent à auditer `index.html` après extension des domaines hors météo. Ils doivent être rejoués après chaque modification profonde.

## Navigation

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `safe + dark + exposed` | rester, protéger, éviter l’errance | continuer vers une trace supposée | nuit et terrain bloquant rendent les essais dangereux |
| En cours d’étape | `safe + last + return` | revenir au dernier point certain | couper hors sentier | le retour connu est plus fort qu’une intuition |
| Inconnu | `separated` | stabiliser le groupe et organiser recherche/aide | disperser tout le monde | séparation aggrave navigation et secours |
| En cours d’étape | `gps + trail` sans danger | repartir seulement sur trajet recoupé | suivre une seule indication | deux indices minimum réduisent le faux positif |
| En cours d’étape | `safe + conflict` | reprendre les preuves avant toute direction | choisir la trace GPS par défaut | indices contradictoires rendent la décision fragile |
| En cours d’étape | `safe + offtrail` | revenir au dernier point certain ou recouper | descendre hors sentier vers une intuition | hors trace involontaire devient vite irréversible |
| Retour | `safe + blockedTrail + return` | retour connu ou détour confirmé | contourner l’obstacle hors trace | sentier barré ne valide pas l’improvisation |

## Santé

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `heatStroke` | arrêt et aide médicale | hydratation simple puis reprise | coup de chaleur possible |
| En cours d’étape | `altitude` sans `better` | ne pas monter plus haut | forcer le col | l’altitude se traite souvent par arrêt/descente |
| Retour | `better` | option facile et surveillance | objectif ambitieux | amélioration n’est pas guérison |
| En cours d’étape | `vomit` | arrêt, protection, option médicale | longue marche normale | impossibilité de boire réduit l’autonomie |
| En cours d’étape | `panic` sans `better` | réduire pression, stabiliser, options courtes | décision engagée immédiate | jugement altéré fausse l’évaluation du risque |

## Blessure

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `spine` | limiter mouvements et appeler | évacuation improvisée | risque rachis |
| Échappatoire | `walk + help + shortOption` | sortie assistée si non exposée | secours automatiques ou poursuite | aide proche peut être meilleure |
| En cours d’étape | `walk + exposed` | ne pas forcer la marche | tester encore plusieurs kilomètres | chute secondaire probable |
| En cours d’étape | `blister` | traiter le pied et réévaluer vite | attendre que ça passe en marchant | ampoule peut changer l’appui et l’allure |

## Matériel

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| Camp | `shelterLost + dark` | créer/remplacer protection | demi-tour automatique | nuit et froid peuvent rendre le retour pire |
| En cours d’étape | `nav` sans `backup` | stopper l’errance | continuer sur intuition | panne de navigation devient risque terrain |
| En cours d’étape | `boot + exposed` | réparer ou sortir du passage | poursuivre passage engagé | chaussure = appui et sécurité |
| En cours d’étape | `critical + backup` | continuer seulement après vérification | ignorer la panne | redondance doit être réelle |
| En cours d’étape | `light + dark` sans `backup` | stopper ou réduire avant pénombre | finir à la lampe du téléphone | éclairage fixe la limite réelle de l’étape |

## Nourriture

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `weak` sans `snacks` | restaurer énergie avant option longue | continuer ou rationner abstraitement | faiblesse et froid changent la sécurité immédiate |
| Camp | `lostFood + animalRisk` | sécuriser odeurs, ne pas poursuivre l’animal | courir après l’animal ou dormir avec odeurs | nourriture dispersée change le risque du camp |
| En cours d’étape | `noCook` sans `snacks` | compter seulement la nourriture mangeable maintenant | considérer les repas comme disponibles | repas sans eau/cuisson possible = réserve théorique |
| En cours d’étape | `low + far` sans `exit` | réduire objectif et recalculer | poursuivre normalement | déficit sur plusieurs jours use lucidité et chaleur |
| Échappatoire | `low + exit` | rejoindre l’option confirmée sans courir | rationner jusqu’à l’objectif initial | sortie proche réduit le risque |
| En cours d’étape | `noAppetite + snacks` | petites prises et surveillance | attendre le gros repas suivant | nourriture disponible n’est pas énergie consommée |
| En cours d’étape | `share + snacks` | redistribuer avant de rationner | laisser chacun gérer son sac | la personne faible engage tout le groupe |
| En cours d’étape | `unsafe` sans `snacks` | ne pas compter comme réserve fiable | donner à la personne fragile | nourriture suspecte peut aggraver l’état |

## Bivouac

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| Sur zone | `hazard + shelter` | refuser le site | monter vite dans la zone | abri ne corrige pas un mauvais site |
| Sur zone | `drain + shelter + water` | installer sobre et surveillé | camp confortable sans repli | météo et terrain restent vivants |
| Démontage | pas `water` | ne pas démonter | perdre l’abri avant préparation | départ non prêt |
| Camp | `threat` | déplacer ou renforcer | rester par inertie | camp déjà monté peut devenir mauvais |
| Sur zone | `animalSigns` sans `foodSecure` | refuser le couchage avec odeurs non sécurisées | dormir avec nourriture dans l’abri | nourriture et déchets changent le risque du site |
| Sur zone | `animalSigns + foodSecure` | sécuriser les odeurs avant couchage | monter le camp puis gérer plus tard | ordre des priorités important |

## Secours

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| Inconnu | `missing + position + battery` | appeler secours | attendre sans plan | personne manquante = urgence potentielle |
| En cours d’étape | `walk` | aide si marche sûre impossible | évacuation improvisée exposée | éviter accident secondaire |
| Camp | `position` sans gravité | préparer infos et surveiller | appeler par automatisme | appel utile si autonomie dépassée |
| Inconnu | pas `position` | fixer la position si possible | appel vague si pas vital | localisation améliore l’aide |
| Inconnu | `life + messenger` | activer balise ou messagerie autonome | attendre le réseau mobile | moyen d’alerte disponible malgré absence réseau |
| En cours d’étape | `noSignal` sans `messenger` | préparer l’alerte sans disperser | envoyer plusieurs personnes chercher du réseau | éviter une deuxième urgence |

## Eau

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `crossing` sans `bridge` | refuser franchissement | traverser car proche | eau rapide piège les bons marcheurs |
| En cours d’étape | `heat + none` | réduire effort et chercher sortie/source sûre | pousser vers source supposée | chaleur altère jugement |
| En cours d’étape | `overdrink` | ne pas forcer l’eau | traiter comme déshydratation simple | hyponatrémie possible |
| En cours d’étape | `source + treat` | traiter et recalculer | repartir sans boire assez | source utile seulement si marge restaurée |
| En cours d’étape | `noSource` | ne pas s’engager sans plan d’eau | continuer car il reste un peu d’eau | absence de prochain point fiable |
| En cours d’étape | `noSource + lastWater` | revenir au dernier point d’eau si retour simple | dépendre d’une cache ou source supposée | mieux vaut corriger avant rupture |
| En cours d’étape | `dryStretch` | recalculer avant section sèche | entrer dans la section par inertie | longue section sèche doit être assumée |
| En cours d’étape | `source + badWater` | considérer l’eau comme dernier recours ou traiter | la compter comme source fiable | eau visible n’est pas eau sûre |
| En cours d’étape | `none + heat + source + badWater` sans `treat` | arbitrer le moindre risque et réduire l’effort | refuser toute eau ou boire normalement | parfois aucune option n’est idéale |

## Critères d’audit vétéran

Chaque scénario doit être relu avec trois questions :

1. un randonneur expérimenté aurait-il compris la question de la même manière ;
2. l’avis proposé est-il faisable maintenant ;
3. l’avis évite-t-il de rassurer artificiellement l’utilisateur.

Une réponse qui paraît logique dans le code mais absurde sur le terrain doit être notée comme échec.

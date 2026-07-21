# Scénarios de test — domaines core

Ces scénarios servent à auditer `index.html` après extension des domaines hors météo. Ils doivent être rejoués après chaque modification profonde.

## Navigation

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `safe + dark + exposed` | rester, protéger, éviter l’errance | continuer vers une trace supposée | nuit et terrain bloquant rendent les essais dangereux |
| En cours d’étape | `safe + last + return` | revenir au dernier point certain | couper hors sentier | le retour connu est plus fort qu’une intuition |
| Inconnu | `separated` | stabiliser le groupe et organiser recherche/aide | disperser tout le monde | séparation aggrave navigation et secours |
| En cours d’étape | `gps + trail` sans danger | repartir seulement sur trajet recoupé | suivre une seule indication | deux indices minimum réduisent le faux positif |

## Santé

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `heatStroke` | arrêt et aide médicale | hydratation simple puis reprise | coup de chaleur possible |
| En cours d’étape | `altitude` sans `better` | ne pas monter plus haut | forcer le col | l’altitude se traite souvent par arrêt/descente |
| Retour | `better` | option facile et surveillance | objectif ambitieux | amélioration n’est pas guérison |
| En cours d’étape | `vomit` | arrêt, protection, option médicale | longue marche normale | impossibilité de boire réduit l’autonomie |

## Blessure

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| En cours d’étape | `spine` | limiter mouvements et appeler | évacuation improvisée | risque rachis |
| Échappatoire | `walk + help + shortOption` | sortie assistée si non exposée | secours automatiques ou poursuite | aide proche peut être meilleure |
| En cours d’étape | `walk + exposed` | ne pas forcer la marche | tester encore plusieurs kilomètres | chute secondaire probable |

## Matériel

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| Camp | `shelterLost + dark` | créer/remplacer protection | demi-tour automatique | nuit et froid peuvent rendre le retour pire |
| En cours d’étape | `nav` sans `backup` | stopper l’errance | continuer sur intuition | panne de navigation devient risque terrain |
| En cours d’étape | `boot + exposed` | réparer ou sortir du passage | poursuivre passage engagé | chaussure = appui et sécurité |
| En cours d’étape | `critical + backup` | continuer seulement après vérification | ignorer la panne | redondance doit être réelle |

## Bivouac

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| Sur zone | `hazard + shelter` | refuser le site | monter vite dans la zone | abri ne corrige pas un mauvais site |
| Sur zone | `drain + shelter + water` | installer sobre et surveillé | camp confortable sans repli | météo et terrain restent vivants |
| Démontage | pas `water` | ne pas démonter | perdre l’abri avant préparation | départ non prêt |
| Camp | `threat` | déplacer ou renforcer | rester par inertie | camp déjà monté peut devenir mauvais |

## Secours

| Contexte | Faits | Attendu | Interdit | Raison terrain |
|---|---|---|---|---|
| Inconnu | `missing + position + battery` | appeler secours | attendre sans plan | personne manquante = urgence potentielle |
| En cours d’étape | `walk` | aide si marche sûre impossible | évacuation improvisée exposée | éviter accident secondaire |
| Camp | `position` sans gravité | préparer infos et surveiller | appeler par automatisme | appel utile si autonomie dépassée |
| Inconnu | pas `position` | fixer la position si possible | appel vague si pas vital | localisation améliore l’aide |

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

## Critères d’audit vétéran

Chaque scénario doit être relu avec trois questions :

1. un randonneur expérimenté aurait-il compris la question de la même manière ;
2. l’avis proposé est-il faisable maintenant ;
3. l’avis évite-t-il de rassurer artificiellement l’utilisateur.

Une réponse qui paraît logique dans le code mais absurde sur le terrain doit être notée comme échec.

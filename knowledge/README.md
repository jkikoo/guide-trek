# Base de connaissance — Assistant de décision trek

Ce dossier est la **source de vérité éditoriale**. `index.html` ne doit afficher qu’une logique validée ici.

## Finalité

L’utilisateur peut être mouillé, fatigué, inquiet ou pressé. L’assistant doit produire une conduite faisable immédiatement, dans le bon ordre, jusqu’à une situation stable.

Il doit toujours :

1. identifier la phase du trek et l’état réel de l’abri ;
2. recueillir les dangers et les faits observables ;
3. générer plusieurs actions candidates ;
4. les classer avec le barème de `coherence.md` ;
5. supprimer toute action incompatible ou dont les préconditions manquent ;
6. afficher une décision unique et une checklist ordonnée ;
7. proposer « Je ne sais pas / aucune proposition ne convient ».

## Ordre opérationnel

1. Écarter un danger vital actif.
2. Quitter une exposition immédiate.
3. Créer ou rejoindre une protection viable.
4. Préserver la personne, le duvet, la couche sèche, la navigation et la communication.
5. Stabiliser le camp ou choisir un repli.
6. Définir quand et selon quels critères réévaluer.

Un danger prioritaire ne doit pas effacer le contexte. Exemple : orage + arrivée au bivouac + tente non montée + pluie et vent ne signifie pas « attendre ». La décision cohérente est : évaluer en quelques secondes un emplacement non inondable et non exposé, monter l’abri sans délai, protéger le couchage, entrer, se changer, isoler les vêtements mouillés, puis attendre avant toute reprise exposée.

## Fichiers

- `coherence.md` : barème, préconditions, incompatibilités et test de validation.
- `pluie.md` : décisions de progression et de repli sous pluie.
- `dangers-prioritaires.md` : orage, hypothermie, crue, terrain instable et blessure.
- `bivouac.md` : choix du site, montage, camp installé et démontage.
- `glossaire.md` : vocabulaire concret de l’interface.

## Règle d’incertitude

L’incertitude n’autorise jamais une réponse arbitraire. Elle déclenche une option prudente et réversible : arrêt sur un point stable, vérification de faits simples, confirmation de la position, recherche du dernier point sûr et refus de s’engager davantage tant qu’un danger important n’est pas exclu.

## Critères de maintenance

Toute nouvelle branche doit préciser :

- les signes observables ;
- les préconditions ;
- les contre-indications ;
- le score de priorité ;
- les actions incompatibles ;
- la checklist dans l’ordre ;
- le critère de stabilisation ;
- le moment de réévaluation.

Aucune branche ne doit être portée dans le HTML sans réussir le test de cohérence de `coherence.md`.

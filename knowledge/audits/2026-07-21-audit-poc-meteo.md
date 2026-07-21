# Audit du POC météo

Date : 2026-07-21

Version : V2, après confrontation aux retours terrain.

## Périmètre

Audit du questionnaire météo et de la fonction de recommandation embarquée dans `index.html`.

Le HTML reste l’interface unique destinée à l’usage hors réseau sur iPhone. Les fichiers Markdown servent à construire, relire et maintenir la doctrine.

## Méthode

Deux audits ont été combinés.

### 1. Audit exhaustif combinatoire

Le moteur météo a été exécuté sur toutes les combinaisons possibles :

- 8 contextes ;
- 20 réponses météo possibles ;
- 1 048 576 combinaisons par contexte ;
- 8 388 608 situations testées ;
- 22 avis distincts produits.

Cet audit vérifie la cohérence interne, les branches mortes, les contradictions et les sorties trop permissives.

### 2. Confrontation aux retours terrain

L’audit combinatoire a ensuite été confronté au rapport `2026-07-21-retours-terrain-meteo.md`, basé sur des récits et rapports NPS, AAC, NOLS, thru-hikers et trip reports.

Cette seconde passe est volontairement plus sévère. Elle vérifie si l’avis résiste à des situations où :

- aucune option n’est vraiment bonne ;
- le groupe est déjà engagé ;
- le retour est connu mais devenu plus dangereux ;
- la distance réelle change tout ;
- l’abri est perdu, insuffisant ou partagé ;
- l’amélioration d’une personne refroidie peut être trompeuse.

## Note globale révisée

**13,5 / 20**

Le POC météo est utile et raisonnablement prudent, mais il n’est pas encore assez riche pour être considéré comme un avis terrain robuste. L’ancienne note de 16 / 20 était trop généreuse : elle mesurait surtout la cohérence interne, pas la résistance au réel.

## Notes détaillées

| Critère | Note | Commentaire |
| --- | ---: | --- |
| Pertinence terrain | 3 / 5 | Les grands dangers sont bien priorisés, mais le POC manque de distance, timing et degré d’engagement. |
| Cohérence contexte | 3.5 / 5 | Les phases sont mieux séparées, mais certains contextes restent trop larges. |
| Neutralité | 3.5 / 5 | L’étape 1 est maintenant descriptive. Quelques titres restent trop impératifs. |
| Gestion du risque résiduel | 3 / 5 | Le POC reconnaît l’option imparfaite, mais pas encore assez les cas “aucune bonne solution”. |
| Clarté utilisateur | 3.5 / 5 | L’interface est lisible, mais certains badges et titres ne distinguent pas assez urgence, prudence et information insuffisante. |

## Résultats combinatoires

| Contexte | Go | Prudence | Stop | Lecture |
| --- | ---: | ---: | ---: | --- |
| En cours d’étape | 7 168 | 54 208 | 987 200 | Très conservateur, globalement acceptable. |
| Sur le trajet de retour | 0 | 16 384 | 1 032 192 | Le retour n’est validé que s’il est connu, moins exposé et sans danger prioritaire. |
| Vers une sortie possible | 0 | 16 384 | 1 032 192 | Même logique que retour : sortie confirmée seulement. |
| Proche du bivouac prévu | 7 168 | 11 200 | 1 030 208 | Bon garde-fou contre le biais d’objectif. |
| Sur zone, tente non montée | 0 | 49 152 | 999 424 | Montage autorisé seulement si site et drainage sont cochés. |
| Bivouac installé | 32 768 | 65 536 | 950 272 | Un `go` reste discutable en météo dégradée. |
| Démontage en cours | 0 | 32 768 | 1 015 808 | Bonne prudence sur la perte d’abri. |
| Situation difficile à qualifier | 0 | 131 072 | 917 504 | Aucune poursuite normale, ce qui est cohérent. |

## Notes par situation réelle

| Situation | Note | Justification |
| --- | ---: | --- |
| Crue, eau qui monte, ruissellement | 16 / 20 | Priorité bien placée. Il manque “ne pas récupérer le matériel” et la gestion de l’après-crue. |
| Hypothermie humide | 15 / 20 | Bon traitement initial. Il manque la surveillance après amélioration et la nuance léger/modéré/grave. |
| Orage en marche | 14 / 20 | Bon arrêt de la progression, mais pas assez de nuance quand attendre et descendre sont tous deux risqués. |
| Camp ou tente sous orage | 14 / 20 | Tente non présentée comme abri foudre, mais l’avis manque d’entraide, abri partagé et pis-aller. |
| Poursuite ou demi-tour en météo dégradée | 13 / 20 | Le POC évite les automatismes, mais manque “déjà engagé” et distance jusqu’au prochain point stable. |
| Perte de tente / abri insuffisant | 12 / 20 | Le cas est transversal météo/matériel et n’est pas assez capturé dans le HTML. |
| Maladie / secours | 9 / 20 | Hors météo mais important : le moteur santé/secours reste trop binaire. |

## Avis produits et notes révisées

| Avis | Note | Diagnostic |
| --- | ---: | --- |
| Quitte la zone basse avant toute autre action | 16 / 20 | Très bon premier réflexe, mais ajouter abandon du matériel et attente en hauteur. |
| Traite le refroidissement comme l’urgence principale | 15 / 20 | Bon socle, mais manque surveillance après amélioration. |
| Rejoins l’abri fermé maintenant | 17 / 20 | Très cohérent si l’abri est vraiment accessible sans nouveau danger. |
| Sors d’abord de l’exposition foudre | 14 / 20 | Bon principe, mais cas réel plus complexe si descente exposée ou terrain glissant. |
| Reviens aux faits avant de choisir une direction | 15 / 20 | Bon pour l’incertitude, mais ajouter “êtes-vous déjà sur un point stable ?”. |
| Ne pars pas en demi-tour sans preuve que le retour est praticable | 13 / 20 | Fond juste, titre à reformuler car la personne peut déjà être sur le retour. |
| Continue le retour avec points de contrôle | 13 / 20 | Correct mais manque durée, fatigue, terrain transformé. |
| Ne poursuis pas vers une échappatoire non vérifiée | 14 / 20 | Bon garde-fou, manque distance et alternative si sortie imparfaite. |
| Rejoins l’échappatoire confirmée | 14 / 20 | Pertinent mais trop simple sans durée/altitude/heure. |
| N’atteins pas le bivouac prévu à tout prix | 16 / 20 | Très bon contre le biais d’objectif. |
| Ne transforme pas ce mauvais emplacement en camp | 16 / 20 | Très bon, mais ajouter cas hypothermie où chercher longtemps aggrave le risque. |
| Change de site avant de monter quoi que ce soit | 14 / 20 | Correct mais trop absolu si froid intense ou abri déjà urgent. |
| Monte un abri fonctionnel sur ce site acceptable | 14 / 20 | Bon, mais manque risque foudre résiduel et abri partagé. |
| Prépare le déplacement du camp | 16 / 20 | Bon avis, cohérent avec camp menacé. |
| Reste bas, limite les sorties et surveille le site | 14 / 20 | Réaliste comme pis-aller, mais doit mieux dire que ce n’est pas sûr. |
| Stabilise le camp et garde une option de repli | 13 / 20 | Badge `go` parfois trop optimiste. |
| Ne perds pas l’abri avant d’être prêt à partir | 16 / 20 | Très bon principe, manque abri déjà partiellement démonté. |
| Progression possible, sous surveillance stricte | 12 / 20 | À manier prudemment : manque distance, engagement, météo attendue et fatigue. |
| Prends l’option confirmée la moins exposée | 15 / 20 | Bonne philosophie, mais nécessite durée et prochain point stable. |
| Stabilise avant tout choix d’itinéraire | 14 / 20 | Prudent mais peut être trop générique. |

## Points forts

- Les dangers majeurs interrompent bien les choix ordinaires : crue, hypothermie, foudre.
- Le demi-tour n’est plus présenté comme automatiquement sûr.
- L’échappatoire doit être confirmée et non exposée.
- Le bivouac prévu n’est plus traité comme un objectif absolu.
- L’interface expose moins la mécanique interne et ressemble davantage à un avis.
- L’étape 1 décrit mieux le contexte réel qu’une intention subjective.

## Points faibles

### 1. Pas de notion “déjà engagé”

Les témoignages montrent que la bonne décision change selon le moment. Avant un col, il faut parfois renoncer. Une fois sur une section exposée sans arrêt possible, continuer jusqu’au prochain point stable peut être moins mauvais que revenir.

### 2. Pas de distance ni durée

Retour confirmé à 20 minutes et retour confirmé à 4 heures ne sont pas équivalents. Même problème pour échappatoire, abri fermé, bivouac et point stable.

### 3. Abri perdu ou partagé absent

Les récits de tente emportée, effondrée ou partagée montrent une grosse lacune. Cette situation doit être traitée entre météo et matériel.

### 4. “Stop” mélange trop de réalités

Le même niveau couvre danger vital, information insuffisante et option non vérifiée. L’utilisateur peut recevoir une intensité émotionnelle trop forte ou mal calibrée.

### 5. Hypothermie encore trop grossière

Le POC traite bien les signes graves, mais pas les états intermédiaires : frissons contrôlables, personne humide mais lucide, amélioration temporaire, surveillance post-réchauffement.

### 6. Santé, secours et matériel restent trop faibles

Ces sections sont actives dans l’interface, mais ne sont pas au niveau météo. Elles doivent être considérées comme prototypes.

## Recommandations prioritaires

1. Ajouter un niveau `INFORMATION INSUFFISANTE` ou équivalent pour éviter que tous les refus soient des urgences.
2. Ajouter les questions : distance/durée vers retour, échappatoire, abri, prochain point stable.
3. Ajouter la question : “le groupe est-il déjà engagé dans un passage où s’arrêter ou revenir est difficile ?”.
4. Ajouter abri perdu, abri inutilisable, abri partagé possible, abri de fortune possible.
5. Ajouter dans la crue : ne pas récupérer matériel ou tente si l’eau monte.
6. Ajouter dans hypothermie : amélioration durable, surveillance, lucidité, capacité de marche après réchauffement.
7. Remplacer le badge `OPTION POSSIBLE` par `AVIS POSSIBLE` ou toujours `AVIS PRUDENT` en bivouac installé.
8. Reformuler `Ne pars pas en demi-tour...` en `Vérifie que le retour reste praticable`.
9. Ne pas considérer les sections santé, secours, matériel, navigation et blessure comme validées.

## Sections non météo

Passe exhaustive rapide sur les autres sections actives : 512 situations testées par section, en combinant 8 contextes et 6 réponses.

| Section | Avis distincts | Note | Évaluation |
| --- | ---: | ---: | --- |
| Blessure | 4 | 10 / 20 | Trop générique. Le contexte influence peu l’avis. |
| Santé | 3 | 8 / 20 | Trop binaire pour maladie stable, aggravation, isolement et secours. |
| Navigation | 4 | 11 / 20 | Prudence utile, mais manque visibilité, météo, fatigue et point stable. |
| Matériel | 3 | 7 / 20 | Insuffisant pour tente perdue, chaussures, abri, navigation, eau. |
| Secours | 2 | 7 / 20 | Beaucoup trop binaire : appeler ou préparer. |

## Conclusion

Le POC météo reste la meilleure base du projet, mais il doit être noté **13,5 / 20**, pas 16 / 20.

Il sait éviter plusieurs erreurs grossières : continuer sous foudre, traverser une crue, monter une tente dans un mauvais site, sacraliser le demi-tour ou le bivouac prévu. En revanche, il ne modélise pas encore assez le réel : timing, distance, engagement, fatigue, entraide, abri perdu, état intermédiaire d’hypothermie.

La prochaine évolution doit améliorer la compréhension de la situation avant d’ajouter de nouvelles recommandations.

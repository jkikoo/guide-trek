# Audit vétéran V2 — domaines core

Profil simulé : randonneur vétéran, trente ans de terrain, regard volontairement critique sur les questions, l’ordre des actions et les biais psychologiques.

Cet audit relit les corrections V1 et vérifie si les domaines peuvent être considérés comme intégrés en POC.

## Note globale V2

**16,5 / 20**

Le POC est maintenant cohérent pour une utilisation offline comme avis terrain. Il ne remplace pas un professionnel réel, mais il évite les principaux pièges : demi-tour automatique, appel automatique, poursuite rassurante, source supposée, descente hors trace, bivouac sur mauvais site, traversée d’eau forcée.

## Validation par domaine

| Domaine | Note V2 | Statut | Commentaire vétéran |
|---|---:|---|---|
| Navigation | 17 / 20 | Validé POC | Bon refus de l’errance et du raccourci. Le groupe séparé est bien remonté en priorité. |
| Santé | 16 / 20 | Validé POC | Meilleure distinction entre grave, récupérable, chaleur, altitude et vomissements. |
| Blessure | 16 / 20 | Validé POC | La sortie assistée proche évite l’appel réflexe ; rachis et marche instable sont correctement bloquants. |
| Matériel | 16 / 20 | Validé POC | Perte d’abri, chaussure et navigation sont bien traitées comme fonctions, pas comme objets isolés. |
| Bivouac | 16 / 20 | Validé POC | Le site prime sur l’envie de monter vite. Le démontage est mieux cadré. |
| Secours | 17 / 20 | Validé POC | L’appel est dédramatisé sans devenir automatique. L’attente et la position sont bien présentes. |
| Eau | 17 / 20 | Validé POC | Bon traitement des traversées, du manque d’eau, de l’eau douteuse et du risque de trop boire. |

## Points vérifiés

- Les questions sont regroupées par logique terrain et non plus affichées comme une liste plate.
- L’utilisateur n’est pas invité à déclarer son choix préféré.
- Les avis peuvent répondre `INFORMATION INSUFFISANTE`.
- Une option imparfaite peut être recommandée si elle est la plus adaptée.
- Les secours ne sont pas présentés comme une punition ni comme une solution magique.
- Le demi-tour est comparé au terrain réel.
- Les checklists commencent par protection, stabilisation ou réduction du danger immédiat.

## Tests rejoués

Scénarios automatisés passés :

- navigation : terrain bloquant, dernier point certain, groupe séparé, repères recoupés ;
- santé : coup de chaleur possible, altitude, vomissements, amélioration ;
- blessure : rachis, marche impossible avec aide proche, marche impossible en terrain exposé ;
- matériel : abri perdu de nuit, panne critique avec sortie proche, navigation perdue, redondance ;
- bivouac : mauvais site, bon site, démontage non prêt ;
- secours : personne manquante, absence de position hors urgence vitale ;
- eau : torrent sans alternative, alternative hors d’eau, chaleur sans eau, trop boire, source traitable.

## Réserves restantes

Ces réserves ne bloquent pas le POC, mais devront guider la prochaine itération :

- les domaines `sante` et `eau` restent liés ; une future version pourrait fusionner certains symptômes dans un module humain commun ;
- le guide n’affiche pas de numéros d’urgence locaux, par choix de prudence tant qu’une source pays fiable n’est pas intégrée ;
- le bivouac général est encore volontairement sobre ; il manque une doctrine de confort, cuisine, animaux, réglementation et impact ;
- les sources terrain sont nombreuses mais encore principalement nord-américaines et anglophones ;
- l’interface n’a pas encore de persistance locale des réponses ou d’historique de décisions, ce qui est acceptable pour le POC offline.

## Décision V2

Le POC multi-domaines est **validé pour expérimentation**.

Il est suffisamment cohérent pour simuler une utilisation en randonnée sans réseau, à condition de garder son positionnement : avis terrain prudent, pas garantie de sécurité.

# Industrialisation des domaines

Ce protocole transforme le POC météo en méthode de production pour les autres grandes thématiques du guide.

Il doit être appliqué domaine par domaine avant toute validation : bivouac, navigation, santé, matériel, secours, puis les domaines futurs.

## Sorties attendues par domaine

Chaque domaine doit produire :

1. un `README.md` doctrinal lisible ;
2. un fichier `questionnaire.md` si les questions dépassent le résumé du README ;
3. une liste de scénarios de test ;
4. un rapport de confrontation au réel dans `knowledge/audits/` ;
5. jusqu’à deux audits vétéran ;
6. les règles intégrées dans `index.html` seulement après correction des incohérences majeures.

## Cycle de travail

### 1. Cadrer le domaine

Définir les situations majeures sans demander à l’utilisateur quelle décision il veut prendre.

Exemples de cadrage :

- état actuel du groupe ;
- phase du trek ;
- terrain autour ;
- capacité de déplacement ;
- ressources critiques restantes ;
- options confirmées ;
- niveau d’incertitude.

### 2. Construire les options

Lister les actions possibles, puis préciser leurs préconditions et leurs exclusions.

Une option est crédible seulement si elle répond à trois questions :

- peut-elle être réalisée maintenant par ce groupe ;
- réduit-elle le risque principal ;
- évite-t-elle de créer un risque supérieur.

Les options classiques ne sont jamais automatiques : continuer, revenir, rejoindre une sortie, bivouaquer, réparer, attendre, demander de l’aide ou appeler les secours doivent être comparées au réel.

### 3. Pondérer sans exposer le score

La pondération reste interne à la doctrine. Elle sert à classer les options, pas à justifier l’avis devant l’utilisateur.

Facteurs à pondérer :

- danger vital ou terrain immédiat ;
- perte d’autonomie ;
- aggravation probable ;
- distance et durée réelles ;
- engagement déjà pris ;
- réversibilité ;
- abri ou protection disponible ;
- état humain ;
- capacité de communication ;
- aide proche ou entraide possible.

Une option peut gagner sans être idéale si les autres choix exposent davantage.

### 4. Confronter au réel

Avant validation, rechercher des témoignages et rapports réels.

Sources à privilégier :

- rapports de secours ;
- parcs nationaux et autorités de terrain ;
- clubs alpins ;
- écoles outdoor ;
- récits détaillés de randonneurs ;
- forums et communautés, uniquement si les décisions et contraintes sont décrites précisément.

Pour chaque source, extraire :

- situation initiale ;
- décision prise ;
- hésitation ou biais visible ;
- contrainte qui a réellement pesé ;
- issue observée ;
- leçon applicable au guide.

Le rapport doit distinguer les sources institutionnelles des témoignages communautaires.

### 5. Audit vétéran 1

Le premier audit doit être sévère. Il cherche les absurdités, pas la confirmation.

Questions d’audit :

- un randonneur expérimenté cocherait-il ces questions ;
- manque-t-il une information qui change totalement l’avis ;
- une option est-elle proposée alors qu’elle est irréaliste ;
- le demi-tour, l’appel, le bivouac ou la poursuite sont-ils utilisés par réflexe ;
- la checklist est-elle dans le bon ordre ;
- une formulation peut-elle pousser l’utilisateur vers le choix qu’il veut déjà faire.

Après cet audit, corriger la doctrine avant l’interface.

### 6. Revue de couverture formateur

Avant le second audit, appliquer `revue-couverture-formateur.md`.

Cette revue cherche les situations importantes absentes et les questions artificielles. Elle doit répondre à une question simple : un randonneur qui vit une situation courante trouve-t-il naturellement comment la décrire dans l’interface ?

Exemple : dans le domaine eau, « je suis en cours de trek et je réalise qu’il n’y a pas de point d’eau confirmé avant longtemps » doit être un cas visible, distinct de « il ne me reste presque plus d’eau ».

### 7. Audit vétéran 2

Le second audit vérifie que les corrections tiennent.

Il doit couvrir :

- scénarios simples ;
- scénarios ambigus ;
- scénarios où aucune bonne solution n’existe ;
- scénarios avec information insuffisante ;
- scénarios où l’option psychologiquement difficile est peut-être la bonne ;
- scénarios où l’option psychologiquement rassurante est dangereuse.

Le domaine est intégrable si les incohérences restantes sont mineures, explicites et documentées.

## Critères de passage

Un domaine ne peut pas être marqué prêt si :

- les questions demandent une intention plutôt qu’un fait ;
- une option positive apparaît sans préconditions ;
- l’appel aux secours est automatique hors signe grave ou blocage réel ;
- le demi-tour est traité comme toujours sûr ;
- l’attente est proposée sans protection ni critère de fin ;
- l’interface expose la mécanique de décision ;
- aucun témoignage ou rapport réel n’a été utilisé.

## Intégration HTML

`index.html` doit rester autonome et utilisable hors réseau.

L’intégration doit :

- garder les textes visibles orientés avis terrain ;
- filtrer les questions par contexte ;
- afficher une checklist actionnable ;
- inclure un état d’information insuffisante ;
- rester lisible sur iPhone ;
- ne dépendre d’aucun fichier Markdown, réseau ou ressource externe.

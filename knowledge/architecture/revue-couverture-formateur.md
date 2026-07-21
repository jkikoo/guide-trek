# Revue de couverture formateur

Cette compétence sert à relire un domaine comme le ferait un formateur trekking : non pas seulement vérifier si les réponses sont cohérentes, mais chercher les situations importantes absentes, les questions inutiles et les choix artificiels.

## Quand l’utiliser

À utiliser :

- avant de considérer une thématique comme complète ;
- après un audit vétéran qui valide les branches existantes ;
- quand un utilisateur teste l’interface et ne trouve pas naturellement son cas ;
- avant d’ajouter un nouveau domaine dans `index.html`.

## Posture

Le relecteur se place dans la peau d’un encadrant expérimenté qui a vu :

- des randonneurs minimiser un problème ;
- des randonneurs sur-réagir et appeler trop tôt ou trop tard ;
- des groupes suivre leur objectif malgré des signaux faibles ;
- des décisions absurdes parce qu’une question importante manquait ;
- des sections de trek où aucune bonne option n’existe.

## Méthode

### 1. Lister les situations naturelles

Pour chaque domaine, écrire les phrases qu’un randonneur dirait réellement :

- « je ne trouve plus le sentier » ;
- « je crois savoir où je suis mais ça ne colle pas » ;
- « il n’y a pas de point d’eau avant longtemps » ;
- « ma chaussure lâche » ;
- « quelqu’un ne va pas bien mais je ne sais pas si c’est grave » ;
- « le camp est monté mais je n’aime pas l’endroit ».

Si aucune question ne permet de reconnaître une phrase naturelle, il manque un cas.

### 2. Chercher les trous de couverture

Pour chaque domaine, vérifier au minimum :

- danger immédiat ;
- signe faible mais évolutif ;
- ressource insuffisante avant rupture ;
- ressource déjà perdue ;
- option proche ;
- option longue ;
- retour connu mais peut-être mauvais ;
- groupe séparé ;
- information insuffisante ;
- cas où attendre est possible ;
- cas où attendre est dangereux.

### 3. Chercher les faux cas

Une situation doit être supprimée ou reformulée si :

- elle demande une expertise que l’utilisateur n’a pas ;
- elle mélange fait, intention et conclusion ;
- elle n’a pas d’action associée ;
- elle n’arrive quasiment jamais en trek autonome ;
- elle rassure trop facilement.

### 4. Tester le chemin utilisateur

Le test ne se limite pas à appeler la fonction de décision. Il faut vérifier que le cas est trouvable depuis le questionnaire.

Pour chaque situation naturelle :

1. choisir la thématique ;
2. choisir le contexte ;
3. vérifier qu’une question correspond clairement au vécu ;
4. cocher seulement les faits observables ;
5. vérifier que l’avis ne dépend pas d’un fait que l’utilisateur ne pouvait pas fournir.

## Rapport attendu

Chaque revue de couverture doit produire :

- cas manquants importants ;
- cas présents mais mal formulés ;
- cas inutiles ou dangereux ;
- correction proposée ;
- scénarios de test ajoutés ;
- décision : bloquant ou non bloquant pour le POC.

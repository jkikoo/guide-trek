# Audit post-implémentation des résultats structurés v1

Date : 2026-07-23

## Changement appliqué

L'écran final ne repose plus seulement sur une phrase d'avis, trois encarts génériques et une checklist plate. Le rendu ajoute maintenant :

- les faits retenus depuis les cases cochées ;
- des blocs contextualisés selon le domaine et les réponses ;
- des alternatives quand une action peut être impossible ;
- des seuils de surveillance et de changement de décision ;
- une checklist séparée à la fin.

La logique de décision existante est conservée. La correction porte sur l'affichage et l'accompagnement de la recommandation.

## Couverture de l'audit précédent

| Recommandation précédente | Statut v1 | Preuve |
|---|---|---|
| Afficher les preuves utilisées | Fait | `selectedFacts()` + `renderFacts()` |
| Distinguer action immédiate et conditions | Fait partiel | `resultBlocks()` ajoute des blocs par niveau et domaine |
| Dire quoi faire si l'abri/protection manque | Fait | blocs météo, secours, bivouac |
| Traiter ombre/eau/source impossible | Fait | blocs eau/chaleur |
| Ajouter attente secours structurée | Fait | blocs secours "Informations à transmettre" et "Pendant l'attente" |
| Ajouter STOP navigation | Fait | bloc navigation "Protocole STOP" |
| Spécialiser matériel par fonction perdue | Fait partiel | bloc "Fonction touchée" selon boot/light/nav/shelterLost |
| Remplacer toutes les checklists plates par des checklists applicables | Partiel | la checklist originale reste affichée, mais elle est précédée de blocs conditionnels |

## Tests effectués

Les scénarios suivants ont été exécutés avec un faux DOM Node pour vérifier que la décision, les blocs attendus et le rendu HTML passent :

| Domaine | Scénario | Bloc attendu |
|---|---|---|
| Météo | personne trempée et froide, pluie, aucune protection | Si aucune protection ne tient |
| Météo | tonnerre sans abri fermé | Si aucun abri fermé n'est accessible |
| Santé | altitude avec symptômes persistants | Terrain avant déplacement |
| Secours | pas de réseau, point réseau proche, attente non protégée | Si l'attente n'est pas protégée |
| Eau | chaleur, moins d'une heure d'eau, symptômes persistants | Si aucune eau, source ou sortie n'est confirmée |
| Bivouac | personne froide sans abri | Abri de fortune |
| Matériel | chaussure, secours annoncé, réparation échouée | Fonction touchée |
| Navigation | indices contradictoires et nuit/batterie faible | Protocole STOP |
| Nourriture | faiblesse, snacks, énergie toujours basse | Inventaire commun |
| Blessure | ampoule/douleur de pied persistante | Test ou déplacement |

Contrôles techniques :

- extraction et parsing du script : OK ;
- rendu HTML des scénarios critiques : OK ;
- `git diff --check` : OK.

## Ce qui est mieux

### Météo

Le cas test de l'utilisateur est corrigé au niveau de l'affichage final. Si une personne est trempée et froide et qu'aucune protection réelle n'est cochée, le résultat ne se contente plus de dire de s'abriter. Il affiche maintenant une alternative :

- quitter seulement l'eau, le vent direct ou le sol froid si cela n'expose pas plus ;
- utiliser sacs, vêtements, sursac, poncho, tarp ou partage de couches ;
- isoler du sol ;
- préparer sortie courte, aide ou appel si le froid persiste.

### Secours

Le résultat distingue mieux :

- informations à transmettre ;
- attente ;
- absence de protection d'attente ;
- déplacement pour chercher du réseau.

### Eau/chaleur

Le résultat n'impose plus seulement "mets-toi à l'ombre" ou "cherche une source". Il ajoute :

- quoi faire si l'ombre manque ;
- quoi faire si aucune eau, source ou sortie n'est confirmée.

### Bivouac

Le résultat ajoute un vrai bloc abri de fortune et un bloc si le déplacement de camp est impossible.

### Santé, blessure, nourriture

Les options terrain non vérifiées sont maintenant rendues visibles : avant de choisir retour, sortie ou aide proche, l'utilisateur doit vérifier terrain, lumière, groupe et accès.

## Limites restantes

### 1. La checklist finale reste l'ancien format

Les blocs structurés corrigent beaucoup de situations impossibles, mais la checklist originale reste inchangée. Elle peut encore contenir une phrase directe qui devrait devenir conditionnelle.

Exemple : une checklist peut encore dire "cherche une source" ou "confirme la sortie" alors que le bloc au-dessus dit quoi faire si aucune source ou sortie n'est confirmée.

Prochaine correction possible : transformer chaque `r.s` en actions typées :

- toujours ;
- si possible ;
- à vérifier ;
- appel si ;
- ne pas faire.

### 2. Les blocs sont générés par domaine, pas par branche précise

`resultBlocks()` regarde le domaine et les cases cochées. C'est robuste et rapide, mais moins précis qu'une migration branche par branche.

Prochaine correction possible : migrer progressivement les branches critiques vers un format `R({blocks:[...]})` explicite.

### 3. Les faits retenus sont limités

Les faits affichés sont sélectionnés automatiquement avec une priorité. Cela aide déjà, mais certains scénarios complexes pourraient masquer une case secondaire utile.

Prochaine correction possible : ajouter une propriété `facts` explicite dans les branches critiques.

## Recommandations appliquées immédiatement

L'audit v1 ne révèle pas de bug bloquant dans l'implémentation actuelle. La principale recommandation restante est une amélioration de fond : migrer les checklists elles-mêmes vers un format typé.

Je recommande donc de conserver cette v1 comme socle, puis de migrer les branches critiques suivantes en `R({ ... })` explicite :

1. météo : froid/pluie sans protection ;
2. météo : orage sans abri fermé ;
3. eau : chaleur sans ombre/source/sortie ;
4. secours : attente non protégée ;
5. bivouac : froid au camp sans récupération ;
6. santé : altitude ou malaise sans option terrain vérifiée ;
7. blessure : 20 pas impossibles ;
8. navigation : groupe séparé ou point non sûr.

## Décision v1

La refonte d'affichage atteint l'objectif principal : l'écran final ne suppose plus autant que l'action idéale est possible. Il donne maintenant une conduite alternative quand une ressource manque.

La prochaine étape utile est de rendre les checklists elles-mêmes conditionnelles, mais ce n'est pas nécessaire pour valider la direction technique.

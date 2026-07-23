# Audit des recommandations finales

Date : 2026-07-23

## Objet

Cet audit porte sur les écrans de résultat affichés après le questionnaire. Le problème signalé n'est pas la logique des étapes, qui est maintenant plus cohérente, mais la qualité du guide final : certaines actions sont trop générales, pas assez contextualisées, ou supposent une possibilité que l'utilisateur n'a pas confirmée.

Méthode :

- extraction des branches `return R(...)` de `index.html` ;
- revue par domaine ;
- vérification de la cohérence entre faits cochés, titre, explication et checklist ;
- repérage des actions qui peuvent être impossibles ou insuffisamment guidées.

Inventaire extrait du code actuel :

| Domaine | Ecrans de recommandation |
|---|---:|
| Météo | 31 |
| Blessure | 8 |
| Santé | 8 |
| Navigation | 8 |
| Matériel | 13 |
| Nourriture | 12 |
| Secours | 9 |
| Bivouac | 11 |
| Eau | 17 |
| **Total** | **117** |

## Verdict global

Les résultats sont globalement justes comme orientation de décision. Ils évitent souvent les mauvais réflexes : continuer par inertie, faire demi-tour sans vérifier, chercher du réseau en créant une deuxième urgence, compter une eau douteuse comme une vraie ressource, ou traiter une personne froide comme un simple problème météo.

Mais ils ne sont pas encore assez bons comme guide terrain final.

Le défaut principal est structurel : une checklist unique ne sait pas distinguer :

- action immédiate toujours valable ;
- action conditionnelle si une ressource existe ;
- action alternative si la ressource manque ;
- critère d'abandon ;
- éléments à transmettre aux secours ;
- surveillance après stabilisation.

Résultat : certains écrans donnent une bonne intention mais peuvent demander une action impossible. Exemple typique : "mets-toi à l'abri" ou "coupe le vent et la pluie" quand aucun abri, tarp, couche sèche ou zone abritée n'est disponible. Dans ce cas, le guide doit dire quoi faire **si l'abri n'existe pas**, pas seulement répéter qu'il faut s'abriter.

## Problèmes transversaux

### 1. Les checklists mélangent action et condition

Beaucoup de phrases commencent comme des ordres directs alors qu'elles devraient être conditionnelles.

Exemples :

- "Rejoins l'abri" est acceptable seulement si `shelter` est coché.
- "Cherche une source" est acceptable seulement si le trajet est court, visible et non exposé.
- "Descends" en altitude est dangereux si la descente impose un passage exposé ou de nuit.
- "Gagne un point stable" peut être impossible si aucun point stable n'est visible.

Correction attendue : chaque résultat doit pouvoir afficher un bloc "Si c'est possible" et un bloc "Si ce n'est pas possible".

### 2. Les résultats ne récapitulent pas les preuves utilisées

L'utilisateur ne voit pas toujours pourquoi le guide propose cette action. Il voit un titre et une justification, mais pas les faits structurants.

Correction attendue : afficher 2 à 5 preuves courtes :

- "Personne trempée et froide cochée" ;
- "Aucune protection réelle cochée" ;
- "Option proche cochée" ;
- "Retour non confirmé" ;
- "Réseau absent, balise absente".

Cela aiderait aussi à repérer les erreurs de saisie.

### 3. Les résultats ne montrent pas les manques d'information

Quand une recommandation dépend d'une option non confirmée, le guide devrait le dire explicitement.

Exemple : si le résultat suggère retour, sortie ou abri alors que le domaine courant n'a pas demandé ces informations, l'écran devrait afficher "option non vérifiée" au lieu de formuler cela comme une consigne directe.

### 4. Les modules humains manquent d'options terrain

Santé, blessure et nourriture peuvent conclure à "retour", "sortie", "bivouac" ou "aide proche", mais ils ne demandent pas toujours :

- si le retour est le même chemin sans passage exposé ;
- si une sortie est localisée ;
- s'il reste assez de lumière ;
- si tout le groupe est ensemble ;
- si un point stable ou abri est réellement visible.

Deux solutions possibles :

- ajouter quelques questions contextuelles communes à ces domaines ;
- ou garder les questions courtes mais faire afficher ces options comme "à vérifier avant de bouger".

La seconde solution est probablement préférable pour ne pas alourdir tous les parcours.

### 5. Les encarts pédagogiques sont trop génériques

`tutorialFor()` ajoute trois encarts par domaine, mais ils ne connaissent pas les faits cochés. Cela donne un guidage utile mais parfois trop large.

Correction attendue : les encarts doivent être générés depuis le résultat réel et les faits cochés, pas seulement depuis le domaine.

## Audit par domaine

### Météo

Forces :

- bonne distinction entre orage, crue, froid humain, visibilité, retour, échappatoire, bivouac et démontage ;
- bonne prise en compte du fait que le demi-tour n'est pas automatiquement meilleur ;
- les nouvelles précisions froid évitent la question humaine hors contexte.

Manques ou risques :

- plusieurs checklists supposent qu'une protection peut être créée, même si `noProtect` ou absence d'abri indique le contraire ;
- "Repars vers une option courte" peut apparaître sans option courte confirmée si la personne va mieux ;
- "Gagne un point stable" ou "arrête-toi sur un point stable" peut être impossible si aucun point stable n'a été coché ;
- les cas "orage sans abri fermé" doivent mieux guider la position d'attente imparfaite, pas seulement "sortir de l'exposition".

Ajouts proposés :

- bloc "Protection disponible" : utiliser abri fermé, abri partagé, fortune, vêtements, sacs, sursac, isolation du sol ;
- bloc "Si aucune protection n'est possible" : sortir de l'eau/vent direct si possible, limiter durée d'exposition, préparer appel ou sortie courte ;
- bloc "Option courte confirmée" uniquement si `shortOption`, `returnOpen`, `escapeOpen`, `shelter` ou `shelterShared` ;
- critère d'abandon : froid qui persiste, parole lente, trébuchements, plus de point stable visible.

### Blessure

Forces :

- les signes graves et suspicion rachis sont bien priorisés ;
- le test des 20 pas et l'aggravation sont traités prudemment ;
- les douleurs de pied ont maintenant une réévaluation plus concrète.

Manques ou risques :

- "avance jusqu'à l'aide proche" doit être strictement conditionné à `help + shortOption + !exposed` ;
- les checklists devraient séparer "ne pas déplacer" et "déplacer seulement pour fuir un danger immédiat" ;
- manque d'un bloc "si la marche test échoue".

Ajouts proposés :

- bloc "Test de marche" : terrain plat, quelques pas, arrêt immédiat si appui se dégrade ;
- bloc "Si 20 pas impossibles" : stabiliser, protéger, préparer appel, ne pas tenter l'évacuation autonome ;
- bloc "Si sortie proche" : seulement avec assistance, sans passage exposé, avec arrêt possible.

### Santé

Forces :

- les signes graves sont bien traités ;
- chaleur, froid, panique et altitude sont distingués ;
- les réévaluations humaines sont maintenant plus factuelles.

Manques ou risques :

- le module santé recommande souvent retour, sortie ou bivouac sans avoir demandé si ces options existent ;
- "descends" en altitude peut être faux si la descente est exposée, nocturne ou impossible ;
- le résultat ne distingue pas assez "malaise stable" et "aucune option autonome vérifiée".

Ajouts proposés :

- afficher "Avant de bouger, vérifie : retour même chemin, sortie localisée, lumière, terrain exposé, groupe ensemble" ;
- pour altitude : "ne monte plus" comme action sûre ; "descendre" seulement si chemin simple et groupe ensemble ;
- bloc "Si aucune option simple n'est confirmée" : stabiliser, protéger, préparer appel.

### Navigation

Forces :

- très bonne logique STOP : ne pas marcher en cherchant ;
- bon refus du GPS seul, du hors-trace improvisé et du sentier barré ;
- bonne gestion du groupe séparé.

Manques ou risques :

- "arrête-toi sur un point sûr" est un objectif, mais si l'utilisateur n'est pas déjà sur un point sûr, il faut dire comment quitter uniquement le danger immédiat ;
- le résultat devrait mieux distinguer "dernier point certain connu" et "retour praticable maintenant" ;
- manque un bloc de signalisation/attente si nuit ou batterie faible.

Ajouts proposés :

- bloc "Si le point actuel n'est pas sûr" : bouger seulement de quelques mètres/minutes pour sortir crête, torrent, ravine ou passage technique ;
- bloc "Si aucune position n'est recoupée" : rester groupé, signaler, économiser batterie, préparer attente.

### Matériel

Forces :

- c'est un des domaines les plus solides ;
- la réparation ou redondance est maintenant testée avant de justifier une poursuite ;
- panne de navigation, lampe, chaussure et abri sont bien différenciées.

Manques ou risques :

- "réparer" peut encore être trop vague selon la fonction perdue ;
- il manque des micro-actions spécifiques : chaussure, lampe, navigation, abri, communication ;
- le résultat devrait rappeler la fonction critique perdue.

Ajouts proposés :

- checklist spécialisée par fonction : chaussure/appui, lampe/lumière, navigation/repères, abri/couchage, communication ;
- bloc "Si la réparation échoue" déjà logique, mais à rendre plus visible.

### Nourriture

Forces :

- bonne distinction entre nourriture disponible, mangeable maintenant, cuisson impossible, appétit, faiblesse, partage et risque animal ;
- bonne prise en compte de la personne la plus faible.

Manques ou risques :

- retour, sortie, ravitaillement et aide sont parfois suggérés sans preuve qu'ils existent ;
- la faiblesse alimentaire est liée à froid/chaleur/lucidité, mais le résultat ne sait pas toujours dans quel environnement le groupe se trouve ;
- les écrans ne distinguent pas assez "chercher de la nourriture dans les sacs" et "il n'y en a vraiment pas".

Ajouts proposés :

- bloc "Inventaire commun" : tous les sacs, nourriture sans cuisson, sel, eau nécessaire ;
- bloc "Si aucune prise ne passe" : ne pas forcer, traiter comme santé/secours ;
- bloc "Option de sortie" seulement si confirmée, sinon "à vérifier".

### Secours

Forces :

- bonne priorité des signes graves ;
- bonne distinction réseau absent, balise disponible et déplacement pour chercher le signal ;
- bon principe : ne pas créer une deuxième urgence.

Manques ou risques :

- "protège le groupe pour attendre" peut être impossible si aucune protection n'est disponible ;
- manque un guide plus complet d'attente : visibilité, bruit/lumière, économie batterie, messages réguliers, personne dédiée au vulnérable ;
- manque une fiche d'appel structurée affichée comme formulaire terrain.

Ajouts proposés :

- bloc "Informations à transmettre" : position, nombre, état, évolution, météo, terrain, accès, heure ;
- bloc "Attente" : abri, isolation, visibilité, batterie, rotation surveillance ;
- bloc "Si pas de protection d'attente" : priorité à créer protection minimale ou déplacer seulement hors danger immédiat.

### Bivouac

Forces :

- bonne logique site avant confort ;
- animaux/odeurs maintenant présents ;
- froid au camp mieux traité avec amélioration/stagnation/aggravation.

Manques ou risques :

- "cherche un autre site" peut être impossible de nuit ou en terrain engagé ;
- manque un protocole abri de fortune plus explicite ;
- manque un mode "nuit forcée sans tente" complet.

Ajouts proposés :

- bloc "Si déplacement de camp impossible" : renforcer sur place, réduire exposition, préparer signalement ;
- bloc "Abri de fortune" : couper vent, isoler du sol, garder sec critique, réduire volume exposé ;
- bloc "Surveillance nuit" : froid, eau, ancrages, odeurs, lampe/chaussures/téléphone.

### Eau

Forces :

- bonne séparation entre manque d'eau, source douteuse, traitement, section sèche et torrent ;
- bonne prudence sur eau douteuse et surchauffe ;
- bonne logique de franchissement.

Manques ou risques :

- "mets-toi à l'ombre" peut être impossible ;
- "cherche une source" ou "reviens au point d'eau" doit rester conditionnel au terrain et à la lumière ;
- manque un bloc "si aucune eau et aucune sortie confirmée".

Ajouts proposés :

- bloc "Réduction d'effort" toujours valable : arrêter, ralentir, ombre si disponible, réduire charge ;
- bloc "Si pas d'ombre" : créer ombre avec vêtement/tarp/sac, attendre heure plus fraîche si possible ;
- bloc "Si aucune eau/source/sortie" : traiter comme autonomie compromise et préparer aide.

## Proposition de restructuration technique

Ne pas continuer à enrichir `R(c,t,w,s)` avec une simple liste d'actions. Le format actuel est trop plat.

Proposition : remplacer progressivement `R(c,t,w,s)` par un résultat structuré, par exemple :

```js
R({
  level: 'stop',
  title: 'Réduis le froid avant toute option longue',
  why: '...',
  facts: ['Personne trempée et froide', 'Protection absente'],
  blocks: [
    {type: 'immediate', title: 'D’abord', items: [...]},
    {type: 'if_possible', title: 'Si une protection existe', items: [...]},
    {type: 'if_impossible', title: 'Si aucune protection ne tient', items: [...]},
    {type: 'decision', title: 'Choix ensuite', items: [...]},
    {type: 'monitor', title: 'Surveille', items: [...]},
    {type: 'call', title: 'Appelle si', items: [...]}
  ]
})
```

Affichage proposé :

1. **Avis terrain** : titre + pourquoi.
2. **Faits retenus** : cases importantes qui ont déclenché l'avis.
3. **D'abord** : actions locales toujours valables.
4. **Si c'est possible** : actions dépendantes d'une ressource cochée.
5. **Si ce n'est pas possible** : alternative ou seuil d'appel.
6. **Options à comparer** : retour, sortie, abri, bivouac, attente, appel.
7. **Surveillance / arrêt** : signes qui font changer de branche.
8. **Checklist courte** : uniquement les actions finales réellement applicables.

Avantage : on garde la logique actuelle, mais on évite de demander une action impossible. L'écran final devient un vrai guide opérationnel.

## Priorité de correction

### Priorité 1

- météo froid/pluie sans abri ;
- santé avec option terrain non vérifiée ;
- eau/chaleur sans ombre ou sans source ;
- secours sans protection d'attente ;
- bivouac sans site ou abri disponible.

### Priorité 2

- spécialiser matériel selon fonction perdue ;
- renforcer navigation de nuit/signalisation ;
- détailler abri de fortune et attente secours ;
- ajouter un vrai protocole STOP final quand aucune action n'est claire.

### Priorité 3

- enrichir le rendu visuel des résultats ;
- réduire les textes répétés ;
- ajouter des micro-guides par type d'action.

## Décision proposée

Je recommande de ne pas réécrire toutes les décisions tout de suite. La bonne prochaine étape est de modifier d'abord le modèle d'affichage des résultats, puis de migrer 5 à 8 branches critiques pour valider le format :

1. météo : personne trempée et froide sans protection ;
2. météo : orage sans abri fermé ;
3. santé : symptômes persistants sans option terrain vérifiée ;
4. secours : réseau absent et groupe non protégé ;
5. eau : chaleur persistante sans ombre/source/sortie ;
6. bivouac : froid au camp sans récupération ;
7. matériel : réparation fragile ou échouée ;
8. navigation : pas de point sûr ou groupe séparé.

Si ce format fonctionne sur ces cas difficiles, il pourra ensuite être généralisé aux 117 écrans.

## Annexe : titres audités

Cette annexe liste les titres de résultats extraits. Certains écrans ont une variante de niveau ou de titre selon une condition interne ; ils sont notés avec `/`.

### Météo

1. Traite le refroidissement comme l'urgence principale.
2. Réduis le froid avant toute option longue.
3. Repars seulement vers une option courte et contrôlée.
4. Quitte la zone basse avant toute autre action.
5. Rejoins l'abri fermé maintenant.
6. Rejoins le prochain point stable, pas forcément le point de départ.
7. Sors d'abord de l'exposition foudre.
8. Reprends les repères avant de poursuivre.
9. Utilise l'abri disponible, même imparfait.
10. Crée une protection avant de viser une sortie lointaine.
11. Change de site avant de monter quoi que ce soit.
12. Monte ou renforce l'abri comme solution imparfaite.
13. Ne transforme pas ce mauvais emplacement en camp.
14. Monte un abri fonctionnel sur ce site acceptable.
15. Prépare le déplacement du camp.
16. Reste bas, limite les sorties et surveille le site.
17. Stabilise le camp et garde une option de repli.
18. Ne perds pas l'abri avant d'être prêt à partir.
19. N'atteins pas le bivouac prévu à tout prix.
20. Continue le retour avec points de contrôle.
21. Le retour est possible mais la marge reste fragile.
22. Vérifie le retour avant d'en faire la solution.
23. Rejoins l'échappatoire confirmée.
24. L'échappatoire est possible, mais pas neutre.
25. Ne valide pas cette sortie sans accès vérifié.
26. Reprends les repères depuis ce point stable / Gagne d'abord un point stable.
27. Progression possible, sous surveillance stricte.
28. Prends l'option confirmée la moins exposée.
29. Stabilise avant tout choix d'itinéraire.

### Blessure

1. Protège, alerte et secoure.
2. Limite les mouvements et demande de l'aide.
3. Rejoins l'aide proche avec assistance / Ne force pas la marche.
4. Reprends seulement avec un test de marche court.
5. Raccourcis avant que le pied décide de l'étape.
6. Traite le pied avant qu'il décide de l'étape.
7. Traite la blessure et le froid ensemble.
8. Teste seulement une reprise très prudente / Garde l'option de sortie la plus simple.

### Santé

1. Arrête l'effort et demande une aide médicale.
2. Ne compte pas sur une reprise normale.
3. Réduis la pression avant toute décision engagée.
4. Descends ou stabilise sans monter plus haut.
5. Ne reprends pas l'objectif pour l'instant.
6. Reprends uniquement vers l'option la plus facile.

### Navigation

1. Stabilise le groupe avant de naviguer.
2. Arrête-toi d'abord sur un point sûr.
3. Contourne par le retour connu, pas par l'improvisation / Ne force pas le sentier barré.
4. Ne choisis pas une direction tant que les indices se contredisent.
5. Reviens au dernier point certain.
6. Repars seulement sur un trajet recoupé.
7. N'ajoute pas une errance dans un terrain risqué.
8. Recoupe les informations avant de repartir.

### Matériel

1. Considère la fonction comme perdue.
2. Raccourcis avec une solution fragile.
3. Continue seulement avec test vérifié.
4. Remplace la protection avant de décider la suite.
5. Ne transforme pas la panne de navigation en errance.
6. Ne continue pas sans éclairage fiable.
7. Protège l'appui avant tout passage engagé.
8. Réduis l'itinéraire avant la baisse de lumière.
9. Rejoins la sortie confirmée avant que la panne empire.
10. Considère l'étape comme compromise.
11. Répare puis teste avant de décider.
12. Continue seulement avec une redondance vérifiée.
13. Raccourcis avant que la panne décide pour toi.

### Nourriture

1. Ne traite plus cela comme une simple faim.
2. Raccourcis avant la panne d'énergie.
3. Repars lentement après amélioration visible.
4. Restaure de l'énergie avant toute option longue.
5. Sécurise les odeurs avant de penser rationnement.
6. Ne compte pas cette nourriture comme une réserve fiable.
7. Sépare la nourriture réelle de la nourriture théorique.
8. Réduis l'objectif avant que la faim décide.
9. Rejoins l'option confirmée avant le déficit.
10. Fais entrer de l'énergie par petites prises.
11. Redistribue avant de rationner.
12. Compte la nourriture réellement utile.

### Secours

1. Active le moyen d'alerte maintenant.
2. Appelle les secours maintenant.
3. Demande de l'aide si 20 pas sans trébucher sont impossibles.
4. Ne crée pas une deuxième urgence pour chercher du réseau.
5. Cherche le signal avec cadre strict.
6. Protège le groupe avant de chercher le signal.
7. Prépare l'alerte sans disperser le groupe.
8. Fixe ta position avant l'appel si possible.
9. Prépare les informations avant de décider.

### Bivouac

1. Traite le froid comme l'urgence du camp.
2. Renforce la protection avant d'attendre.
3. Ne transforme pas ce lieu en camp.
4. Ne dors pas avec les odeurs et la nourriture.
5. Sécurise les odeurs avant d'installer le couchage.
6. Ne démonte pas avant d'être prêt à partir.
7. Prépare un déplacement ou un renforcement immédiat.
8. Trouve une protection praticable avant la nuit.
9. Garde le camp simple et surveillé.
10. Installe un camp sobre et surveillé.
11. Vérifie le site avant de monter.

### Eau

1. Traite la chaleur comme l'urgence principale.
2. Réduis l'effort avant de chercher plus loin.
3. Rejoins la sortie pendant que la marge revient.
4. Reprends seulement après recalcul de l'eau et de l'ombre.
5. Prends l'alternative hors d'eau.
6. Ne force pas le franchissement.
7. Choisis le risque le moins dangereux avec cette eau.
8. Réduis l'effort avant de chercher loin.
9. Ne traite pas cette eau comme une source fiable.
10. Reviens au point d'eau connu si le retour reste simple.
11. Ne t'engage pas dans une section sèche non confirmée.
12. Recalcule avant la section sèche.
13. Ne réponds pas seulement par plus d'eau.
14. Utilise l'eau seulement après choix du risque.
15. Recharge avant de poursuivre.
16. Rejoins l'option confirmée avant la rupture.
17. Recalcule l'eau avant de décider.

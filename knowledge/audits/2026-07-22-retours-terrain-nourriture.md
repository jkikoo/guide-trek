# Retours terrain — nourriture

## Objectif

Mettre la doctrine nourriture à l’épreuve de récits et recommandations de terrain. Ce rapport ne traite pas le manque d’eau, sauf quand il rend la nourriture impossible à préparer.

## Sources utilisées

- NPS, **Hike Smart** : https://www.nps.gov/articles/hiking-safety.htm
- NPS, **About Hiking Safety** : https://www.nps.gov/thingstodo/learn-about-hiking-safety.htm
- REI, **Hiking Safety: When to Turn Back** : https://www.rei.com/learn/expert-advice/hiking-safety-when-to-bail.html
- Trail Journals, **Mad Dog’s 2022 PCT Journal — Food** : https://www.trailjournals.com/journal/entry/659588
- Thru-Hike Florida, **Food** : https://www.thruhikeflorida.com/food/
- NPS, **Bear Safety: Storing Food** : https://www.nps.gov/articles/bearsafetyfood.htm
- NPS, **Yellowstone Backcountry Safety** : https://www.nps.gov/yell/planyourvisit/backcountrysafety.htm
- NPS, **Habituated and food-conditioned black bear killed in Yellowstone** : https://www.nps.gov/yell/learn/news/25012.htm
- NPS, **The Last Bear Killed at Brooks Camp** : https://home.nps.gov/katm/blogs/the-last-bear-killed-at-brooks-camp.htm
- Backpacker, **A Bear Stole His Backpack—So This Hiker Chased It** : https://www.backpacker.com/stories/reader-essays-hold-your-fire/
- Gourmet Hiking, **Bear safety: How A Bear Played with My Food** : https://gourmethiking.com/blog-post/bear-safety/
- ABC News, **Hiker recounts surviving encounter with bears on Alaska mountain** : https://abcnews.go.com/US/hiker-recounts-surviving-encounter-bears-alaska-mountain-die/story?id=78353012

## Situations observées

### Sous-estimation des calories

Le journal PCT de Mad Dog décrit une sous-estimation forte des besoins caloriques au début du trek, avec perte de poids et difficulté à faire tenir assez de nourriture dans le volume disponible. Le retour est important parce que le problème n’est pas seulement « il reste un repas » : c’est la différence entre nourriture prévue, appétit réel, capacité à porter, volume du contenant et durée de la section.

Conséquence doctrine :

- ne pas demander seulement s’il reste de la nourriture ;
- demander si la durée jusqu’au ravitaillement est confirmée ;
- demander si le groupe peut manger assez maintenant, pas seulement survivre avec ce qui reste ;
- réduire l’objectif si le déficit couvre plusieurs repas ou plusieurs jours.

### Perte d’appétit

Thru-Hike Florida décrit la perte d’appétit fréquente au début d’un long trek et recommande de manger en petites prises régulières plutôt que de compter sur de gros repas. Ce cas explique pourquoi une personne peut avoir de la nourriture et pourtant manquer d’énergie.

Conséquence doctrine :

- distinguer nourriture disponible et nourriture réellement consommée ;
- proposer petites prises faciles, sucrées, salées ou grasses ;
- surveiller froid, jugement et fatigue ;
- ne pas forcer une personne qui vomit ou avale mal.

### Nourriture impossible à préparer

Thru-Hike Florida insiste sur l’intérêt d’avoir des aliments sans cuisson si le combustible manque, si le réchaud casse ou si la météo rend la cuisson peu réaliste. Cela transforme une réserve théorique en réserve indisponible à court terme.

Conséquence doctrine :

- ajouter une question sur repas qui demandent cuisson, eau ou combustible ;
- compter à part les aliments mangeables maintenant ;
- raccourcir ou partager si la nourriture restante n’est pas immédiatement utilisable.

### Épuisement, froid et manque d’énergie

NPS et REI relient nourriture, snacks salés, énergie, épuisement et sécurité. Dans plusieurs récits de secours déjà utilisés pour les domaines core, la nourriture intervient comme facteur de récupération ou d’aggravation : manque d’eau et nourriture, altitude, épuisement, descente accompagnée, attente.

Conséquence doctrine :

- si froid, faiblesse ou jugement inhabituel sont présents, manger peut devenir une action immédiate ;
- l’outil doit éviter la recommandation sèche « rationne » ;
- une sortie courte peut être meilleure qu’une poursuite normale même si le groupe peut encore marcher.

### Nourriture volée ou manipulée par un animal

Les pages NPS sur le stockage et les récits de Brooks Camp, Yellowstone, Backpacker et Gourmet Hiking montrent que nourriture, déchets, popote et objets odorants peuvent créer un risque humain et animal. Le cas Backpacker est particulièrement utile : poursuivre un animal par colère après vol de nourriture est une mauvaise réaction. Le récit Gourmet Hiking montre aussi qu’un contenant peut protéger la nourriture tout en provoquant une perte de matériel ou une perturbation du camp.

Conséquence doctrine :

- ne pas poursuivre l’animal ;
- sécuriser le groupe et les odeurs restantes ;
- recalculer la nourriture réellement récupérable ;
- préparer sortie, aide ou rationnement selon durée et état humain ;
- ne pas dormir dans un site où odeurs et déchets ne sont plus maîtrisés.

## Écarts du POC avant correction

Le POC traitait la nourriture comme une sous-question de matériel :

- `food` : nourriture très insuffisante ;
- branche surtout active si nuit et absence de sortie proche ;
- pas de distinction entre manque d’un repas, déficit sur plusieurs jours, perte par animal, absence d’appétit, nourriture sans cuisson, partage, nourriture souillée ou stockage.

Cette couverture était trop faible. Elle pouvait produire un avis peu pertinent parce qu’elle ne savait pas si le problème était énergétique, logistique, animalier ou médical.

## Modifications à prévoir

- créer une section HTML **Nourriture** ;
- ajouter une doctrine dédiée `knowledge/nourriture/README.md` ;
- ajouter des scénarios nourriture dans `knowledge/audits/2026-07-21-scenarios-domaines-core.md` ;
- garder la nourriture odorante dans le lien avec bivouac, mais ne pas confondre stockage et déficit calorique ;
- faire apparaître des recommandations de mini-tutoriel : compter, partager, manger maintenant, sécuriser, réduire l’objectif.

## Note formateur

Avant correction : **8 / 20**.

Après correction attendue : **16 / 20** si le HTML distingue bien les familles de problème.

La nourriture mérite son propre domaine dans le POC, car un utilisateur dira naturellement « on n’a presque plus à manger » ou « notre nourriture a disparu », pas « matériel endommagé ».

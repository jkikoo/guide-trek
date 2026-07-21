# Revue de couverture formateur — POC multi-domaines

Cette revue applique `../architecture/revue-couverture-formateur.md` au POC multi-domaines.

Objectif : vérifier si les situations courantes d’un randonneur sont naturellement trouvables dans l’interface, et pas seulement si les branches existantes répondent correctement.

## Verdict

Note de couverture avant corrections : **13 / 20**.

Note de couverture après corrections V1 : **16 / 20**.

Note de couverture après corrections V2 : **18 / 20**.

Le POC couvrait les dangers évidents, mais plusieurs situations fréquentes étaient trop implicites. Le principal défaut était de confondre un état de rupture avec un signal précoce. Exemple : l’eau traitait bien « il me reste moins d’une heure d’eau », mais pas assez clairement « je réalise avant la rupture qu’il n’y a pas de point d’eau confirmé devant ».

## Manques bloquants corrigés

### Eau : section sèche devant

Phrase naturelle :

> Je suis en cours de trek et je réalise qu’il n’y a pas de point d’eau à proximité.

Problème V1 :

- l’utilisateur pouvait cocher `none` seulement si l’eau était déjà presque épuisée ;
- `source` supposait une eau visible ;
- le cas préventif « pas de point confirmé devant » n’était pas évident.

Correction :

- ajout de `Aucun point d’eau confirmé avant plusieurs heures` ;
- ajout de `Dernier point d’eau connu atteignable par un retour praticable` ;
- ajout de `Section sèche longue devant le groupe` ;
- branches dédiées : ne pas s’engager, revenir au dernier point d’eau si praticable, recalculer avant section sèche.

### Météo : visibilité

Phrase naturelle :

> Je ne lis plus bien le terrain à cause du brouillard ou de la visibilité.

Problème V1 :

- le brouillard était mentionné dans la doctrine météo mais absent du questionnaire HTML.

Correction :

- ajout d’un fait visible sur brouillard, nuit blanche ou visibilité trop faible ;
- branche qui impose de reprendre les repères avant progression si le terrain n’est plus clairement lisible.

### Santé : réaction allergique rapide

Phrase naturelle :

> Quelqu’un gonfle, respire mal ou fait une réaction rapide.

Problème V1 :

- les signes graves généraux pouvaient couvrir le cas, mais pas naturellement ;
- un utilisateur pouvait ne pas cocher douleur thoracique ou difficulté respiratoire si le problème est identifié comme allergie.

Correction :

- ajout d’une question dédiée ;
- branche d’action prioritaire avec traitement d’urgence disponible et appel.

### Matériel : nourriture critique

Phrase naturelle :

> On n’a pas assez mangé ou presque plus de nourriture pour la durée restante.

Problème V1 :

- la nourriture était absente alors qu’elle influence lucidité, froid, moral et capacité d’effort ;
- le domaine eau couvrait une partie de l’hydratation mais pas l’énergie.

Correction :

- ajout d’une question nourriture très insuffisante ;
- branche qui réduit l’étape avant chute d’énergie si nuit et absence de sortie proche.

## Manques complémentaires corrigés en V2

Ces cas étaient classés comme limites acceptables dans la première revue. Après test mental avec un profil formateur, ils deviennent nécessaires car un randonneur les exprime naturellement avant de savoir quel domaine choisir.

### Navigation : indices contradictoires, hors sentier et sentier barré

Phrase naturelle :

> Mon GPS, le balisage et le terrain ne racontent pas la même chose.

Problème V1 :

- le POC demandait un dernier point certain ou une trace retrouvée ;
- il ne distinguait pas assez le cas où les indices se contredisent ;
- un sentier barré pouvait pousser l’utilisateur à chercher un contournement intuitif.

Correction :

- ajout de `Carte, GPS, relief ou balisage se contredisent` ;
- ajout de `Hors sentier ou trace perdue sans l’avoir choisi` ;
- ajout de `Sentier barré, noyé, fermé ou impraticable devant` ;
- branches dédiées : ne pas choisir une direction tant que les indices se contredisent, refuser le contournement hors trace non confirmé, revenir au dernier point sûr si le retour est réellement connu.

### Bivouac : animaux, nourriture et odeurs

Phrase naturelle :

> Il y a des traces ou odeurs animales près du camp et on a la nourriture avec nous.

Problème V1 :

- le POC traitait le site physique, le vent et l’eau, mais pas l’attraction créée par nourriture, déchets et objets odorants ;
- il pouvait valider un site drainant sans traiter ce risque.

Correction :

- ajout de `Traces, odeurs, restes, nourriture ouverte ou activité animale proche` ;
- ajout de `Nourriture, déchets et objets odorants peuvent être isolés du couchage` ;
- branches dédiées : refuser le couchage avec odeurs non sécurisées, sécuriser avant d’installer.

### Secours : absence de réseau et balise

Phrase naturelle :

> Il faudrait peut-être appeler, mais il n’y a pas de réseau.

Problème V1 :

- l’appel était traité comme disponible ou à préparer ;
- le cas sans réseau pouvait encourager une dispersion imprudente pour chercher du signal.

Correction :

- ajout de `Aucun réseau mobile utilisable ici` ;
- ajout de `Balise, radio ou messagerie satellite disponible` ;
- branches dédiées : activer immédiatement le moyen d’alerte autonome si l’urgence dépasse le groupe, préparer l’alerte sans disperser le groupe si aucun réseau n’est disponible.

### Matériel : éclairage

Phrase naturelle :

> La frontale ne marche plus et la nuit approche.

Problème V1 :

- l’éclairage était inclus implicitement dans les fonctions critiques ;
- il manquait une réponse spécifique sur l’heure limite, le terrain et la tentation d’utiliser le téléphone comme lampe principale.

Correction :

- ajout de `Frontale, lampe ou éclairage inutilisable` ;
- branches dédiées : ne pas continuer sans éclairage fiable si nuit ou terrain engagé approchent, réduire fortement l’itinéraire même de jour si aucune redondance n’existe.

### Santé et blessure : panique et ampoule

Phrase naturelle :

> Quelqu’un panique ou ne raisonne plus normalement.

Phrase naturelle :

> Une ampoule commence à changer l’appui.

Problème V1 :

- la santé couvrait les signes médicaux graves mais pas assez le jugement altéré sans signe vital évident ;
- la blessure couvrait l’impossibilité de marcher mais pas le signal précoce très fréquent qui finit par compromettre l’étape.

Correction :

- ajout de `Panique, anxiété forte ou jugement inhabituel` ;
- ajout de `Ampoule, frottement ou douleur de pied qui modifie l’appui` ;
- branches dédiées : réduire la pression avant décision engagée, traiter le pied avant qu’il décide de l’étape.

### Eau : eau visiblement douteuse

Phrase naturelle :

> Il y a de l’eau, mais elle est stagnante, odorante ou suspecte.

Problème V1 :

- le POC distinguait source visible et traitement disponible ;
- il ne séparait pas assez une source claire non traitée d’une eau visiblement contaminée.

Correction :

- ajout de `Eau stagnante, algues, odeur, carcasse ou contamination visible` ;
- branches dédiées : ne pas traiter cette eau comme une source fiable, choisir le risque le moins dangereux si la chaleur ou la rupture d’eau menacent maintenant.

## Cas présents mais à surveiller

### Bivouac

Le POC couvre bien mauvais site, camp menacé, protection absente, démontage non prêt, activité animale et sécurisation des odeurs.

Reste limité :

- réglementation, feu, impact environnemental ;
- confort et vie au camp.

Décision : non bloquant pour un POC d’avis difficile, mais à traiter dans une doctrine bivouac avancée.

### Secours

Le POC couvre appel, position, batterie, personne manquante, absence de réseau, balise ou messagerie satellite et attente.

Reste limité :

- stratégie pays par pays pour les numéros ;
- protocole détaillé par type de balise ou radio ;
- délégation longue d’un membre pour chercher du réseau.

Décision : non bloquant tant que l’interface ne prétend pas fournir le bon numéro local.

### Navigation

Le POC couvre arrêt, dernier point certain, recoupement, contradiction carte/GPS/relief, sentier retrouvé, sentier barré, hors trace involontaire, nuit, terrain bloquant et groupe séparé.

Reste limité :

- avalanche, glacier, neige dure, orientation fine hors sentier ;
- erreurs de trace GPS très détaillées.

Décision : non bloquant pour trek général, à traiter dans des domaines spécialisés.

## Cas qui n’ont pas de sens dans ce POC

- optimiser le confort de camp ;
- conseiller une source précise ou un itinéraire précis ;
- afficher des numéros d’urgence par pays sans source maintenue ;
- donner une posologie médicale ;
- remplacer une formation eau vive, neige, avalanche ou premiers secours.

## Scénarios ajoutés

- eau : `noSource` sans source ni sortie -> ne pas s’engager dans une section sèche non confirmée ;
- eau : `noSource + lastWater` -> revenir au point d’eau connu si retour simple ;
- eau : `dryStretch` -> recalculer avant section sèche ;
- météo : `visibility` sans terrain clair -> reprendre les repères ;
- santé : `allergy` -> action prioritaire ;
- matériel : `food + dark` sans sortie -> réduire l’étape avant chute d’énergie.
- navigation : `conflict` ou `offtrail` -> reprendre les preuves avant direction ;
- navigation : `blockedTrail + return` -> retour connu plutôt que contournement improvisé ;
- bivouac : `animalSigns` sans `foodSecure` -> ne pas dormir avec les odeurs et nourriture ;
- secours : urgence avec `messenger` -> activer le moyen d’alerte autonome ;
- secours : `noSignal` sans `messenger` -> préparer l’alerte sans disperser le groupe ;
- matériel : `light + dark` sans redondance -> ne pas continuer sans éclairage fiable ;
- santé : `panic` sans amélioration -> réduire la pression avant décision engagée ;
- blessure : `blister` -> traiter avant terrain engagé ;
- eau : `badWater + source` -> ne pas traiter comme une source fiable.

## Décision

La compétence de revue de couverture est nécessaire et doit être appliquée systématiquement après les audits vétéran.

Le POC multi-domaines reste validé pour expérimentation après corrections, mais la note de couverture doit rester séparée de la note de cohérence : une branche peut être cohérente tout en oubliant un cas courant.

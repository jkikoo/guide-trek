# Revue de couverture formateur — POC multi-domaines

Cette revue applique `../architecture/revue-couverture-formateur.md` au POC multi-domaines.

Objectif : vérifier si les situations courantes d’un randonneur sont naturellement trouvables dans l’interface, et pas seulement si les branches existantes répondent correctement.

## Verdict

Note de couverture avant corrections : **13 / 20**.

Note de couverture après corrections : **16 / 20**.

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

## Cas présents mais à surveiller

### Bivouac

Le POC couvre bien mauvais site, camp menacé, protection absente et démontage non prêt.

Reste limité :

- animaux, stockage nourriture, réglementation, feu, impact environnemental ;
- confort et vie au camp.

Décision : non bloquant pour un POC d’avis difficile, mais à traiter dans une doctrine bivouac avancée.

### Secours

Le POC couvre appel, position, batterie, personne manquante et attente.

Reste limité :

- stratégie pays par pays pour les numéros ;
- communication par SMS, radio, balise bidirectionnelle ;
- délégation d’un membre pour chercher du réseau.

Décision : non bloquant tant que l’interface ne prétend pas fournir le bon numéro local.

### Navigation

Le POC couvre arrêt, dernier point certain, recoupement, sentier retrouvé, nuit, terrain bloquant et groupe séparé.

Reste limité :

- avalanche, glacier, neige dure, orientation fine hors sentier ;
- erreurs de trace GPS trop détaillées.

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

## Décision

La compétence de revue de couverture est nécessaire et doit être appliquée systématiquement après les audits vétéran.

Le POC multi-domaines reste validé pour expérimentation après corrections, mais la note de couverture doit rester séparée de la note de cohérence : une branche peut être cohérente tout en oubliant un cas courant.

# Audit vétéran V1 — domaines core

Profil simulé : randonneur autonome, trente ans de trek, expérience bivouac, incidents météo, navigation, blessure légère et décisions de renoncement.

Objectif : chercher les absurdités avant de valider.

## Note globale V1

**14 / 20**

Le système est devenu utilisable sur tous les domaines, mais la V1 reste trop uniforme hors météo. Elle donne souvent une bonne recommandation finale, mais les questions affichées peuvent encore donner l’impression d’un formulaire générique au lieu d’un dialogue de terrain.

## Navigation

Note V1 : **15 / 20**

Solide :

- arrêt sur point sûr avant navigation ;
- retour au dernier point certain si retour connu ;
- refus de couper hors sentier ;
- personne séparée traitée comme urgence de groupe.

À corriger :

- questions non regroupées, donc l’utilisateur peut cocher trop vite sans distinguer sécurité, repères et options ;
- besoin de rappeler que descendre vers l’eau ou une vallée visible est souvent une fausse solution.

Correction appliquée :

- regroupement des questions en point de sécurité, repères, options de déplacement.

## Santé

Note V1 : **13 / 20**

Solide :

- distinction malaise simple, signe grave, chaleur et altitude ;
- refus de l’appel automatique hors signe grave ;
- reprise seulement vers option facile.

À corriger :

- chevauchement avec eau : chaleur, hydratation et hyponatrémie doivent rester cohérents ;
- une personne qui vomit ne doit pas recevoir un simple avis prudent trop léger ;
- les questions doivent séparer signe grave et causes plausibles.

Corrections appliquées :

- vomissements répétés classés en action prioritaire ;
- regroupement signe grave / contexte humain / suite de l’itinéraire.

## Blessure

Note V1 : **14 / 20**

Solide :

- rachis traité séparément ;
- sortie proche possible sans appeler automatiquement ;
- refus de marche exposée avec appui instable.

À corriger :

- ajouter explicitement l’idée qu’une évacuation autonome peut créer un deuxième accident ;
- garder le froid comme facteur aggravant, pas comme simple confort.

Correction appliquée :

- la branche marche impossible distingue aide très proche et absence de sortie prudente.

## Matériel

Note V1 : **13 / 20**

Solide :

- abri perdu non réduit au demi-tour ;
- navigation perdue traitée comme risque d’errance ;
- chaussure traitée comme sécurité d’appui.

À corriger :

- une fonction critique sans redondance mais avec sortie proche ne doit pas toujours produire action prioritaire ;
- questions non hiérarchisées.

Corrections appliquées :

- ajout d’une branche sortie confirmée avant panne aggravée ;
- regroupement fonction touchée / solution / marge.

## Bivouac

Note V1 : **13 / 20**

Solide :

- mauvais site refusé ;
- camp installé mais menacé traité comme problème actif ;
- démontage bloqué si départ non prêt.

À corriger :

- la doctrine générale du bivouac reste encore très inspirée météo ;
- besoin de mieux distinguer installer un camp, tenir un camp et démonter.

Correction appliquée :

- regroupement site / protection / camp et départ dans le HTML.

## Secours

Note V1 : **15 / 20**

Solide :

- l’appel n’est pas présenté comme échec ;
- position, batterie et protection d’attente incluses ;
- personne manquante ajoutée.

À corriger :

- un appel sans position peut rester nécessaire, mais l’interface doit ne pas retarder un signe vital ;
- le système doit rappeler que secours ne garantit pas extraction rapide.

Correction appliquée :

- branche information insuffisante quand la position manque hors urgence vitale.

## Eau

Note V1 : **14 / 20**

Solide :

- franchissement dangereux refusé ;
- manque d’eau + chaleur traité avant objectif ;
- hyponatrémie possible intégrée.

À corriger :

- si une alternative au franchissement existe, le HTML ne devait pas tomber en information insuffisante ;
- eau douteuse sans traitement doit rester un choix de risque, pas une interdiction absolue.

Correction appliquée :

- branche spécifique pont, détour ou attente hors d’eau.

## Synthèse V1

Corrections prioritaires faites :

- filtrage par groupes pour tous les domaines ;
- correction matériel critique avec sortie proche ;
- correction franchissement avec alternative ;
- durcissement vomissements / santé.

Reste à vérifier en V2 :

- cohérence des scénarios automatisés ;
- absence de vocabulaire interne dans le HTML ;
- lisibilité du fichier autonome ;
- alignement Markdown / HTML.

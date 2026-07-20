# Base de connaissance — Guide trek

Ce dossier est la **source de vérité éditoriale** du guide. `index.html` est l’interface d’exécution et ne doit contenir aucune recommandation qui contredise les fichiers Markdown.

## Architecture

### Doctrine commune

- `architecture-contexte.md` : contexte stratégique obligatoire avant toute décision.
- `coherence.md` : scores, préconditions, exclusions et ordre des actions.
- `glossaire.md` : vocabulaire affiché dans l’interface.

### Sections du guide

- `pluie/` : pluie, vent, orage et météo dégradée.
- `blessure/` : traumatisme, douleur et incapacité de marche.
- `sante/` : malaise, fatigue, froid, chaleur et sensation anormale.
- `navigation/` : perte de trace, position incertaine et errance.
- `materiel/` : matériel endommagé, perdu ou devenu inutilisable.
- `secours/` : décision d’appel, informations à transmettre et attente.

D’autres sections pourront être ajoutées : eau et ravitaillement, neige, animaux, feu, traversée de torrent, choix du bivouac et gestion du groupe.

## Principe directeur

Le premier écran choisit le **problème à traiter**. Une fois dans une section, le moteur doit toujours déterminer le contexte stratégique avant de proposer une conduite :

1. continuer l’étape ;
2. faire demi-tour ;
3. rejoindre une échappatoire ;
4. presque atteindre le bivouac ;
5. être sur la zone de bivouac sans tente montée ;
6. avoir un bivouac installé ;
7. démonter le bivouac ;
8. ne pas savoir.

Cette information commande la cohérence de toutes les propositions suivantes.

## Règles générales

- Une action locale de survie peut interrompre l’objectif, mais elle doit rester adaptée au lieu et à la phase.
- Le bivouac prévu n’est jamais un objectif à atteindre à tout prix.
- Une tente protège de la pluie et du vent, mais ne transforme pas un emplacement dangereux en emplacement sûr.
- Une réponse « je ne sais pas » doit mener à des faits observables et à l’option la plus réversible.
- Toute checklist doit se terminer par un critère de stabilisation et un point de réévaluation.

## Maintenance

Toute nouvelle branche doit préciser :

- le contexte stratégique compatible ;
- les signes observables ;
- les préconditions ;
- les exclusions et contradictions ;
- l’action numéro un ;
- la checklist ordonnée ;
- le critère de stabilisation ;
- le prochain point de réévaluation.

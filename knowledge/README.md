# Base de connaissance — Guide trek

Ce dossier est la **source de vérité éditoriale** du guide. `index.html` est l’interface d’exécution et ne doit contenir aucune recommandation qui contredise les fichiers Markdown.

## Architecture

### Doctrine commune

- `architecture/README.md` : index des règles transversales.
- `architecture/contexte.md` : contexte stratégique obligatoire avant toute décision.
- `architecture/coherence.md` : scores, préconditions, exclusions et ordre des actions.
- `architecture/glossaire.md` : vocabulaire affiché dans l’interface.
- `architecture/modele-poc.md` : méthode de reproduction du POC dans les autres domaines.

### Sections du guide

- `meteo/` : pluie, vent, orage, brouillard, froid, chaleur et météo dégradée.
- `bivouac/` : doctrine générale du bivouac.
- `navigation/` : perte de trace, position incertaine et errance.
- `sante/` : malaise, fatigue, froid, chaleur et sensation anormale.
- `materiel/` : matériel endommagé, perdu ou devenu inutilisable.
- `secours/` : décision d’appel, informations à transmettre et attente.
- `eau/` : manque d’eau, source douteuse, traitement et franchissement.

D’autres sections pourront être ajoutées : neige, feu et gestion du groupe.

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
- Le guide ne promet pas toujours une bonne solution : il peut proposer l’option la moins mauvaise, avec les précautions nécessaires.
- L’interface utilisateur doit afficher un avis terrain, pas le fonctionnement interne de la doctrine.
- Le demi-tour, les secours, l’échappatoire ou le bivouac ne sont jamais des réponses automatiques : chaque option doit être comparée au terrain et à l’état réel du groupe.
- Toute nouvelle thématique doit être confrontée à des témoignages ou rapports terrain avant d’être considérée comme validée.

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

À la racine de `knowledge/`, seul ce fichier d’index doit rester. Les contenus éditoriaux appartiennent aux sous-dossiers spécialisés.

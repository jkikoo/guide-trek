# Base de connaissance — Assistant météo trek

Ce dossier est la **source de vérité éditoriale** de l’assistant. Le fichier `index.html` est l’interface d’exécution : il doit rester cohérent avec les règles décrites ici.

## Principe directeur

L’utilisateur se trouve potentiellement sous la pluie, dans le vent, fatigué ou inquiet. Il ne doit pas interpréter une formule abstraite. L’assistant doit :

1. identifier la **phase du trek** ;
2. identifier les **signaux météo et dangers immédiats** ;
3. recueillir les **conditions concrètes** du groupe, du terrain et du matériel ;
4. choisir une décision explicite ;
5. fournir une checklist ordonnée jusqu’à une situation stable ;
6. proposer systématiquement **« Je ne sais pas / aucune réponse ne convient »**.

## Ordre de priorité

1. Danger vital ou évolutif : orage, crue, hypothermie, chute de pierres, blessure grave.
2. Sortir de l’exposition : crête, col, couloir, ravine, berge, pente où une glissade serait grave.
3. Préserver les capacités essentielles : personne, abri, duvet, couche sèche, navigation, communication.
4. Adapter l’objectif : continuer, raccourcir, rejoindre une échappatoire, bivouaquer, faire demi-tour.
5. Réévaluer après un délai ou à un point précis.

## Vocabulaire opérationnel

- **Échappatoire** : itinéraire secondaire permettant de quitter rapidement l’étape vers une route, un refuge, une vallée ou un terrain plus sûr.
- **Point sûr** : emplacement stable, hors crête, hors ravine, hors berge et sans danger de chute immédiate.
- **Passage exposé** : section où une glissade ou une erreur aurait des conséquences graves.
- **Marge** : réserve d’heure, d’énergie, de chaleur, de visibilité et d’options de repli.
- **Bivouac acceptable** : terrain plat ou légèrement bombé, drainant, hors écoulement, hors chute de pierres et suffisamment protégé du vent.

## Règle d’incertitude

Une réponse incertaine ne doit jamais être forcée. La branche « Je ne sais pas » :

- reformule la question avec des signes observables ;
- propose une évaluation prudente ;
- recommande de rejoindre le dernier point sûr si l’incertitude porte sur un danger important.

## Fichiers

- `pluie.md` : arbre principal, contexte de marche et logique de décision.
- `dangers-prioritaires.md` : orage, hypothermie, crue et terrain instable.
- `bivouac.md` : arrivée, montage, camp installé et démontage.
- `glossaire.md` : termes affichés dans l’interface.

## Maintenance

Toute nouvelle branche doit préciser :

- les signes observables ;
- la question posée ;
- les réponses possibles, dont l’incertitude ;
- la décision finale ;
- la checklist dans l’ordre ;
- le critère indiquant que la situation est stabilisée ;
- le moment de la prochaine réévaluation.
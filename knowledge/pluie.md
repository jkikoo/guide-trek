# Pluie — logique de décision

## Principe

La pluie n’impose pas à elle seule de monter la tente. La décision dépend de la phase, du terrain, de la marge, de l’état humain, de l’abri disponible et du matériel sec.

Le moteur ne choisit pas directement une branche. Il génère des actions candidates, applique le score de `coherence.md`, élimine les incompatibilités, puis ordonne la checklist.

## Phase du trek

### Début ou milieu d’étape

Actions candidates : continuer sous contrôle, revenir, rejoindre une échappatoire, attendre dans un abri sûr.

Continuer n’est autorisé que si : position certaine, terrain simple, groupe chaud, marge correcte, matériel essentiel sec et absence de danger prioritaire.

### Étape avancée ou presque arrivé

Le poids du temps, de la fatigue et du prochain passage augmente. Un bivouac anticipé devient cohérent seulement si un emplacement acceptable existe et si rester n’introduit pas un danger supérieur.

### Arrivé, tente non montée

La priorité habituelle devient : vérifier rapidement le site, monter l’abri, protéger le couchage, entrer, se changer, isoler le mouillé et stabiliser le camp.

Cette priorité est renforcée par pluie, vent, froid, nuit proche, fatigue ou risque de mouiller le duvet. Elle est annulée si le site est menacé par crue, pierres, arbre, pente ou exposition dominante.

### Camp installé

La décision porte sur drainage, ancrages, condensation, matériel sec et capacité de repli. Déplacer le camp si l’eau, les pierres, un arbre ou la déformation de la tente créent un danger supérieur.

### Démontage

Conserver l’abri jusqu’à ce que le groupe, le sac, la navigation et la destination soient prêts. Rétablir l’abri si les conditions se dégradent.

## Actions candidates et scores indicatifs

### Monter rapidement la tente

- `+500` arrivée au bivouac sans abri ;
- `+250` pluie ;
- `+200` vent ou refroidissement ;
- `+200` duvet menacé ;
- `+150` nuit proche ;
- `-1000` site inondable, instable ou exposé à un danger actif.

### Continuer

- `+250` début/milieu d’étape ;
- `+150` terrain simple et position certaine ;
- `+100` sortie proche ;
- `-500` position incertaine ;
- `-500` nuit proche et fatigue ;
- `-1000` danger prioritaire.

### Rejoindre une échappatoire

- `+300` sortie proche ;
- `+250` terrain plus difficile devant ;
- `+200` fatigue ou marge réduite ;
- `-700` échappatoire nécessitant elle-même un passage dangereux.

### Attendre

- `+200` abri réellement sûr ;
- `+150` phénomène bref et amélioration vérifiable ;
- `-500` absence d’abri sous pluie/vent/froid ;
- `-700` zone menacée ;
- `-1000` personne qui se refroidit ou eau qui monte.

## Checklists de référence

### Continuer sous contrôle

1. Protéger duvet, couche sèche, téléphone et batterie.
2. Mettre la protection pluie et régler les aérations.
3. Garder une allure régulière sans surchauffe.
4. Manger et boire avant la baisse d’énergie.
5. Fixer une réévaluation dans vingt minutes ou à un point précis.

### Raccourcir ou se replier

1. Comparer les temps réels vers retour, refuge, vallée, route et bivouac.
2. Choisir l’option la moins exposée et la plus réversible.
3. Éviter tout nouveau col, torrent ou passage engagé.
4. Garder le groupe compact et chaud.
5. Réévaluer à chaque bifurcation.

### Monter un bivouac anticipé

1. Refuser ravine, lit sec, cuvette, berge, pied de falaise, couloir de pierres et arbre menaçant.
2. Choisir un sol drainant et relativement protégé.
3. Garder duvet et couches sèches emballés.
4. Monter et fermer l’abri.
5. Rentrer le matériel critique.
6. Se changer et isoler le mouillé.
7. Vérifier drainage, ancrages et repli.

## Incohérences interdites

- proposer d’attendre à une personne sans protection qui se refroidit ;
- proposer de continuer avec position incertaine et visibilité insuffisante ;
- proposer de monter la tente dans une zone menacée ;
- proposer de sortir le duvet avant fermeture de l’abri ;
- afficher les trente minutes après le tonnerre comme première action au lieu d’un critère de reprise.

## Incertitude

S’arrêter sur un point stable, vérifier tonnerre, eau, état mental, position, lumière et abri disponible. Choisir ensuite l’action la plus prudente et réversible. L’incertitude ne conclut jamais « continuer normalement ».

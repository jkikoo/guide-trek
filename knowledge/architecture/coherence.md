# Cohérence des avis terrain

Ce fichier définit la règle de cohérence qui précède toute recommandation affichée dans `index.html`. Cette règle reste interne à la doctrine : l’interface ne doit pas exposer les scores, les filtres ou la mécanique de choix.

## Principe

L’assistant ne choisit pas une procédure uniquement à partir du danger le plus spectaculaire. Il construit d’abord l’**état réel** : phase du trek, abri disponible, terrain, état humain, météo, matériel sec et options de repli.

Chaque action candidate reçoit ensuite un score, puis passe des filtres de cohérence.

Le résultat attendu n’est pas toujours une solution sûre ou confortable. Il peut s’agir de l’option la moins mauvaise, accompagnée des précautions qui réduisent le risque sans prétendre l’annuler.

## Barème

### Gravité immédiate

- `+1000` : danger vital actif ou personne incapable de se protéger.
- `+700` : exposition directe à la foudre, crue, chute de pierres ou hypothermie probable.
- `+500` : absence d’abri sous pluie/vent/froid, couchage menacé, nuit proche.
- `+300` : terrain exposé, position incertaine, fatigue marquée, absence d’échappatoire.
- `+100` : inconfort ou dégradation encore réversible.

### Adéquation au contexte

- `+250` si l’action correspond exactement à la phase du trek.
- `+200` si elle réduit plusieurs risques à la fois.
- `+150` si elle protège une ressource critique : personne, abri, duvet, couche sèche, navigation.
- `+100` si elle reste réversible.
- `-500` si elle suppose un abri qui n’existe pas.
- `-700` si elle maintient l’utilisateur dans une zone dangereuse.
- `-1000` si elle contredit un danger vital actif.

## Préconditions obligatoires

Une action n’est affichée que si toutes ses préconditions sont vraies.

Exemples :

- **Attendre 30 minutes après le dernier tonnerre** suppose que le groupe est déjà dans la meilleure position disponible et n’a plus d’action urgente à accomplir. Cette consigne concerne la reprise d’une activité exposée ; elle ne doit jamais être la première action d’une personne sans abri sous pluie et vent.
- **Monter la tente** suppose qu’un emplacement acceptable a été trouvé. Elle est interdite dans une ravine, un lit sec, une cuvette inondable, une berge, un couloir de pierres, sous un arbre menaçant ou sur un point dominant exposé.
- **Se changer** suppose qu’un abri ou une protection suffisante existe. Les couches sèches et le duvet restent emballés jusqu’à ce que l’intérieur soit protégé.
- **Continuer** suppose une position certaine, un terrain praticable, une marge suffisante et l’absence de danger prioritaire.

## Incompatibilités

Ne jamais afficher ensemble sans ordre explicite :

- « attendre » et « monter l’abri immédiatement » ;
- « continuer » et « position incertaine » ;
- « rester dans la tente » et « camp menacé par l’eau, les pierres ou un arbre » ;
- « sortir de l’exposition » et « rester sur une crête pour observer » ;
- « ouvrir le sac de couchage » et « tente non fermée sous la pluie ».

## Séquence de sortie

La checklist est toujours ordonnée selon cinq blocs :

1. **Écarter le danger immédiat**.
2. **Créer ou rejoindre une protection viable**.
3. **Protéger la chaleur et le matériel critique**.
4. **Stabiliser le camp ou préparer le repli**.
5. **Définir le critère de réévaluation**.

## Test de cohérence obligatoire

Avant validation d’une branche, répondre oui aux questions suivantes :

1. La première action est-elle physiquement réalisable maintenant ?
2. Réduit-elle le risque le plus urgent sans en créer un supérieur ?
3. Respecte-t-elle la phase du trek et l’état de l’abri ?
4. La checklist protège-t-elle le couchage sec avant de l’exposer ?
5. Toute attente possède-t-elle un lieu et une condition de sécurité ?
6. Toute reprise possède-t-elle des critères explicites ?
7. L’option « je ne sais pas » conduit-elle à une action prudente et réversible ?
8. Si aucune bonne solution n’existe, l’avis nomme-t-il l’option la plus adaptée et les précautions associées ?
9. Le texte visible évite-t-il d’expliquer la mécanique interne ou d’influencer vers la poursuite ?

Une branche qui échoue à un seul de ces tests ne doit pas être intégrée au HTML.

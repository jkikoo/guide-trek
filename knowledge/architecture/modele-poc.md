# Modèle de reproduction du POC

Ce modèle sert à reproduire la logique météo sur les autres domaines du guide tout en gardant `index.html` autonome et utilisable hors réseau.

## Contrainte d’exécution

Le fichier `index.html` est le seul fichier destiné à être enregistré localement sur téléphone. Il doit contenir toute l’interface, toutes les questions, toutes les règles de décision et tous les textes affichés. Les fichiers Markdown de `knowledge/` servent à concevoir, relire et maintenir la doctrine, mais ils ne sont pas chargés par l’application.

L’interface utilisateur ne doit pas exposer le fonctionnement interne de la décision : pas de score, pas de filtre, pas de justification technique des branches. Elle doit afficher un avis de terrain, les faits à vérifier et les précautions à prendre.

## Posture de conseil

Le guide ne doit pas promettre une solution idéale. En randonnée, surtout sous météo dégradée, il peut ne pas exister de bonne option. Le rôle de l’outil est alors de proposer l’option la plus adaptée au réel, même si elle comporte un risque résiduel, et de rendre ce risque maniable par des précautions concrètes.

La formulation doit ressembler à l’avis d’un professionnel présent avec le groupe :

- dire ce qui paraît le plus adapté maintenant ;
- signaler quand l’option reste imparfaite ;
- nommer les précautions nécessaires ;
- éviter les formulations qui poussent implicitement à continuer ;
- éviter aussi de présenter le demi-tour comme automatiquement plus sûr ;
- ne jamais faire croire qu’une checklist supprime le danger.

Le guide doit tenir compte du fait qu’un randonneur hésite souvent à faire demi-tour parce que ce choix ressemble à un échec. L’interface ne doit pas renforcer ce biais, ni dans un sens ni dans l’autre : elle doit décrire les options sans jugement.

## Structure d’un domaine

Chaque domaine doit être construit en trois couches.

1. **Dangers immédiats** : signes qui interrompent l’arbre normal et imposent une action locale prioritaire.
2. **Contexte réel** : phase du trek, abri disponible, capacité de déplacement, options visibles.
3. **Options ouvertes** : continuer, revenir, rejoindre une échappatoire, bivouaquer, stabiliser, appeler.

Une recommandation ne doit jamais être produite à partir d’un seul symptôme spectaculaire si le contexte rend l’action impossible. À l’inverse, le système doit accepter qu’une action imparfaite puisse rester la meilleure option disponible lorsque toutes les autres exposent davantage.

Quand les informations sont trop faibles, le guide doit pouvoir répondre « information insuffisante » avec une action de stabilisation et de reprise des repères. Cette réponse est préférable à une fausse action prioritaire ou à une poursuite présentée comme possible.

## Questions minimales et filtrage

Chaque section doit recueillir :

- les signes de danger vital ou de danger terrain ;
- la phase du trek ;
- la faisabilité du retour ;
- la faisabilité d’une échappatoire ;
- l’existence d’un abri ou d’un site sûr ;
- l’état humain ;
- les ressources critiques disponibles ;
- le prochain point de réévaluation.

Les questions doivent rester observables. Éviter les formulations qui demandent une interprétation experte sans critères concrets.

Règle générale : ne jamais demander à l’utilisateur s’il est « rétabli », « capable », « en sécurité » ou s’il « maîtrise » la situation. Demander une preuve simple adaptée au sujet réel : parole normale depuis 10 minutes seulement si un état humain est déjà signalé, 20 pas sans aide ni trébuchement dans blessure/secours, chemin visible ou localisé pour navigation/échappatoire, absence de torrent/crête/passage exposé sur le retour, lumière restante estimée avec le rythme actuel du groupe, groupe entier réuni.

Les preuves de réévaluation doivent être des questions de second temps. Exemple : ne pas afficher « parle normalement depuis 10 minutes » dans le bloc météo initial ; l’afficher seulement après que l’utilisateur a coché une personne trempée et froide, un malaise, une panique ou un autre signe humain.

Toute précision conditionnelle doit proposer au moins trois issues observables : amélioration limitée, absence d’amélioration nette, aggravation ou signe rouge. Chacune de ces réponses doit être utilisée dans la décision finale ; une précision affichée à l’utilisateur ne doit jamais être une simple information décorative.

Les questions doivent aussi être filtrées par contexte. Une section ne doit pas afficher la même liste à une personne qui marche encore, qui est déjà au bivouac, qui démonte son abri ou qui ne sait plus quelle option choisir.

Une question doit être supprimée ou déplacée si :

- elle n’aide pas à décider une action possible dans le contexte choisi ;
- elle mélange plusieurs critères indépendants ;
- elle demande une conclusion experte au lieu d’un fait observable ;
- elle permet de cocher une option positive malgré une contradiction terrain.
- elle demande à l’utilisateur d’annoncer ce qu’il veut faire au lieu de décrire où il en est.

## Options qui ne sont jamais automatiques

- **Faire demi-tour** : à comparer au terrain actuel du retour, pas au souvenir du passage à l’aller.
- **Continuer** : possible seulement si la marge reste réelle et que l’objectif n’absorbe pas le jugement.
- **Rejoindre une échappatoire** : valable seulement si l’accès ne crée pas un risque supérieur.
- **Appeler les secours** : prioritaire en cas de signe grave ou d’absence d’option autonome sûre, mais pas automatique devant tout malaise.
- **Bivouaquer** : valable seulement si le lieu réduit le risque au lieu de l’installer.
- **Perte de tente** : ne conclut pas automatiquement au demi-tour ; comparer abri naturel, cabane, refuge, vallée, météo, distance et heure.
- **Point stable proche** : dans un passage déjà engagé, le meilleur choix peut être d’avancer quelques minutes vers un point stable plutôt que revenir, rester ou accélérer vers l’objectif.
- **Abri partagé ou de fortune** : solution imparfaite mais parfois meilleure qu’une marche longue sous froid humide.

## Ordre de décision

1. Traiter les dangers qui annulent les choix normaux.
2. Refuser les actions dont les préconditions ne sont pas réunies.
3. Identifier l’engagement déjà pris et le prochain point stable.
4. Comparer les options réellement ouvertes.
5. Choisir l’action la plus adaptée parmi les options réellement ouvertes, en privilégiant le réversible quand une information manque.
6. Afficher une checklist ordonnée.
7. Terminer par un critère de stabilisation ou de réévaluation.

## Textes visibles dans le HTML

Les textes affichés à l’utilisateur doivent rester orientés action. Ne pas écrire :

- « le moteur combine » ;
- « les préconditions sont réunies » ;
- « cette branche est cohérente » ;
- « le score indique » ;
- « poursuite contrôlée » comme badge général.

Préférer :

- « Avis prudent » ;
- « Option possible » ;
- « Action prioritaire » ;
- « La situation ne donne pas une option idéale » ;
- « Prends l’option confirmée la moins exposée » ;
- « Stabilise avant tout choix d’itinéraire ».

## Guidage pas à pas dans les résultats

Une recommandation ne doit pas se limiter à une phrase d’avis et une checklist sèche. L’utilisateur consulte souvent l’outil parce qu’il est fatigué, mouillé, inquiet, pressé ou moins capable de réfléchir clairement.

Chaque résultat affiché doit donc contenir plusieurs niveaux :

1. **Avis terrain** : ce qui paraît le plus adapté maintenant.
2. **Faits retenus** : les réponses principales qui ont déclenché l’avis.
3. **Actions immédiates** : ce qui reste valable même si les options idéales manquent.
4. **Conditions** : ce qui vaut seulement si une ressource ou une option existe réellement.
5. **Alternative si impossible** : quoi faire si abri, ombre, eau, réseau, point stable, retour ou sortie ne sont pas disponibles.
6. **Surveillance** : signes qui annulent l’option prévue.
7. **Checklist** : gestes ordonnés à cocher, formulés pour ne pas supposer une ressource non confirmée.

Les encarts doivent rester très courts. Ils ne remplacent pas une formation et ne doivent pas devenir un manuel. Ils servent à guider l’action immédiate :

- quoi arrêter ou ralentir ;
- quoi observer avant de bouger ;
- quoi vérifier sur la personne, le terrain ou le matériel ;
- comment éviter l’erreur classique du domaine ;
- quand réévaluer.
- quoi faire si l’action idéale n’est pas possible.

Format recommandé :

- **D’abord** ou **Avant de bouger** : action mentale et physique immédiate.
- **À observer** ou **À vérifier** : critères simples que l’utilisateur peut constater.
- **Geste pratique** ou **Point de contrôle** : mini-tutoriel de quelques mots pour appliquer correctement la checklist.
- **Si aucune protection / option / ressource n’existe** : alternative dégradée et seuil d’appel.

Les encarts ne doivent pas exposer le fonctionnement interne de la décision. Ils doivent parler comme un encadrant à côté du groupe : concret, calme, court.

Exemples :

- navigation : « Ne marche pas pendant que tu cherches. Compare au moins deux indices avant de repartir. »
- eau : « Une eau visible mais douteuse reste une option dégradée, pas une réserve normale. »
- secours : « Position, nombre de personnes, état, évolution, météo, terrain, accès possible, batterie et protection d’attente. »
- bivouac : « Garde chaussures, lampe, eau, veste et téléphone accessibles. »

## Tests de scénario

Chaque domaine doit définir des scénarios avant intégration dans le HTML.

Format recommandé :

- contexte choisi ;
- faits cochés ;
- recommandation attendue ;
- recommandation interdite ;
- raison terrain.

Exemples météo :

- `arrived + rain + wind + siteOk + siteDrain` : monter l’abri, protéger le couchage, se changer après fermeture.
- `arrived + thunder + no siteOk` : quitter l’exposition et chercher un site acceptable avant montage.
- `camp + campThreat` : préparer le déplacement du camp, pas rester dans la tente.
- `unknown + rain` : revenir aux faits, pas continuer normalement.
- `continue + thunder + committed + stablePoint` : rejoindre le point stable le moins exposant, pas imposer un demi-tour abstrait.
- `return + returnKnown + returnSafer + longOption + wetCold` : retour possible mais fragile, pas option confortable.
- `arrived + shelterLost + shelterShared` : utiliser l’abri imparfait et comparer ensuite, pas conclure automatiquement demi-tour.
- `flood + shelterLost` : quitter l’eau sans récupérer la tente ou le sac.

Une branche qui échoue à un scénario doit être corrigée avant publication.

## Confrontation au réel

Aucun domaine ne doit être considéré comme validé uniquement parce que ses scénarios théoriques passent. Avant de stabiliser une section, il faut la confronter à des retours terrain.

Méthode obligatoire :

1. choisir les situations majeures du domaine ;
2. rechercher plusieurs témoignages ou rapports par situation ;
3. privilégier les rapports de secours, parcs, clubs alpins, écoles outdoor et récits détaillés ;
4. extraire ce que les personnes ont réellement fait, ce qu’elles ont hésité à faire, et ce qui a changé l’issue ;
5. comparer ces choix avec l’avis produit par le guide ;
6. baisser les notes quand le guide ignore le timing, l’engagement déjà pris, l’état du groupe, l’entraide possible ou la distance réelle ;
7. modifier d’abord la doctrine Markdown, puis seulement le HTML.

Le rapport de confrontation doit être conservé dans `knowledge/audits/`.

Chaque rapport doit contenir :

- les sources utilisées ;
- les situations couvertes ;
- les décisions réelles observées ;
- les écarts avec le guide ;
- les modifications doctrinales à prévoir ;
- une note révisée, plus sévère que l’audit combinatoire si nécessaire.

# Audit terrain technique — 2026-07-24

## Sources consultées

- Club Alpin Suisse, légende du portail des courses et échelle T1 à T6 : https://www.sac-cas.ch/en/huts-and-tours/sac-route-portal/keys-sac-route-portal-/-sac-app/
- BPA, randonnée et randonnée en montagne : https://www.bfu.ch/fr/conseils/randonnee-et-randonnee-en-montagne
- BPA, communiqué 2025 sur le risque de chute en terrain escarpé : https://www.bfu.ch/fr/le-bpa/medias/randonner-en-securite
- National Park Service, terrain safety Glacier : https://www.nps.gov/glac/planyourvisit/terrainsafety.htm
- National Park Service, spring hiking safety Mount Rainier : https://home.nps.gov/mora/planyourvisit/spring-hiking-safety.htm
- National Park Service, safe river crossings : https://home.nps.gov/articles/safe-river-crossings.htm
- National Park Service, hiking safety Mount Rainier : https://www.nps.gov/mora/planyourvisit/hiking-safety.htm
- AltitudeRando, Mont Buet par Tré les Eaux et col des Cristaux : https://www.altituderando.com/Mont-Buet-3096m-par-Tre-les-Eaux-et-le-col-des-Cristaux
- AltitudeRando, Pointe Blanche par le passage Pellier : https://www.altituderando.com/Pointe-Blanche-2438m-par-le-passage-Pellier
- Mon GR, GR 738 Belledonne : https://www.mongr.fr/sinspirer/recits-itinerance/gr-738-belledonne-la-bien-nommee

## Situations couvertes

- Passage exposé ou pente où une chute serait grave.
- Pierrier, éboulis, blocs et dévers détritique.
- Pente herbeuse, terreuse, boueuse, dalle humide et terrain glissant.
- Névé, neige dure, pont de neige, corniche et neige masquant le sentier.
- Passage rocheux facile où les mains deviennent nécessaires.
- Câble, chaîne ou corde fixe dont l’état est inconnu.
- Couloir ou pied de paroi exposé aux chutes de pierres.
- Sentier barré, effondré, noyé, fermé ou impraticable.
- Franchissement d’eau traité comme difficulté technique de terrain.

## Décisions réelles observées

Les échelles CAS montrent que la difficulté technique monte rapidement quand le sentier devient discontinu, exposé, sans trace, mêlé de rochers, de pierriers, de pentes herbeuses raides, de névés ou de passages demandant les mains. Le BPA insiste sur le fait que les chemins de montagne peuvent être étroits et exposés, et que les chemins balisés sont prévus pour des périodes sans neige ni verglas.

Les pages NPS terrain et neige signalent des risques qui ne se voient pas toujours : ponts de neige sur cavités ou torrents, corniches, glissades incontrôlables sur neige dure, rochers ou troncs en contrebas. Les pages sur les rivières répètent que la meilleure option peut être d’attendre, contourner ou renoncer ; profondeur, vitesse, sortie aval et obstacles aval priment sur l’itinéraire prévu.

Les topos consultés décrivent des cas typiques de randonnée réelle : névés tardifs déconseillés aux marcheurs occasionnels, pierriers instables, longues traversées en dévers de terrain détritique, ressauts rocheux exposés, corde fixe usée, chutes de pierres liées au terrain, aux animaux ou aux groupes au-dessus.

## Écarts corrigés dans le guide

- Ajouter un domaine séparé : météo/eau/navigation mentionnaient déjà du terrain, mais aucun topic ne permettait de traiter le problème technique comme problème principal.
- Distinguer difficulté technique et malaise humain : le nouveau questionnaire ne demande pas si quelqu’un se sent mal, sauf sous forme de capacité technique du groupe.
- Refuser l’automatisme « demi-tour » : dans un passage déjà engagé, le guide propose d’atteindre le prochain point stable si c’est moins exposant que revenir ou attendre.
- Refuser l’automatisme « continuer » : un névé raide, une corde fixe douteuse, un contournement non visible ou un couloir de pierres bloquent la progression normale.
- Faire du contournement une option conditionnelle : visible jusqu’au retour sur sentier, sans barre, torrent, pente raide, végétation piégeuse ou brouillard.
- Ajouter une réévaluation technique : test d’appui sur névé/pente, stabilité des pierres, état du câble/chaîne, aisance réelle du groupe.

## Scénarios validés

- `continue + exposed + committed + stablePoint` : rejoindre le point stable le moins exposant, pas faire demi-tour automatiquement.
- `near + snow + no alpineGear + exposed` : ne pas franchir le névé pour atteindre le bivouac prévu.
- `return + returnKnown + returnSafer + mud + margin` : retour prudent possible, mais par petits tronçons et sans raccourci.
- `escape + escapeKnown + !escapeSafe + rockfall` : sortie non validée, car son accès crée un risque supérieur.
- `continue + blockedTrail + detourVisible + margin` : contournement possible seulement si visible jusqu’au retour sur sentier.
- `continue + fixedAidBad + hands + exposed` : ne pas s’engager sur corde/câble douteux.
- `unknown + aucun fait` : information insuffisante, stabiliser et observer.
- `continue + trailOk + margin + footwear + poles` : progression possible sous surveillance, sans badge rassurant excessif.

## Note de vétéran

Le domaine passe les scénarios principaux, mais la note reste volontairement sévère : **7,5 / 10**.

Raison : sans vraie cartographie, pente mesurée, météo en direct et niveau technique réel du groupe, un assistant local ne doit jamais « autoriser » franchement un passage technique. Le bon niveau d’ambition est de ralentir, filtrer les contradictions, empêcher les erreurs grossières et rappeler quand le renoncement ou l’aide est plus solide que l’objectif.

## Corrections intégrées

- Ajout du topic `terrain`.
- Ajout de questions observables par familles de terrain.
- Ajout de préconditions sur retour, échappatoire, contournement, marge et équipement.
- Ajout de règles spécifiques névé, pierrier, couloir, corde fixe, franchissement et passage engagé.
- Ajout d’encarts de résultat qui rappellent le passage un par un, l’espacement, le refus des traces comme preuve, et l’arrêt au prochain point stable.

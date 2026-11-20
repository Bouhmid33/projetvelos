# Simulateur Les Points Vélo — Version 4

Site statique mobile-first : ouvrir `index.html` ou déposer dans GitHub Pages.

## Nouveauté : prix complets

La V4 conserve le parcours guidé V3, la recommandation qualitative, le contact commercial `mailto:` et les statistiques nationales descriptives. Elle remplace les prix de main-d’œuvre seule par une base de **main-d’œuvre + pièces standard**. Les scénarios ne sont pas des probabilités annuelles de panne. La base est datée du **20 novembre 2026**. Toutes les valeurs sont centralisées dans l'objet `CONFIG` du script à la fin de `index.html`.

| Intervention | MO classique / VAE | Pièce classique / VAE | Total classique / VAE | Référence pièce |
|---|---:|---:|---:|---|
| Révision Sérénité | 72 / 102 | 0 / 0 | 72 / 102 | Forfait sans pièces ajoutées |
| Chambre à air, roue traditionnelle | 12 / 12 | 5,99 / 5,99 | 17,99 / 17,99 | Decathlon 700×35/45 |
| Chambre à air, roue spéciale/motorisée | 23 / 23 | 5,99 / 5,99 | 28,99 / 28,99 | Decathlon 700×35/45 (hypothèse compatibilité) |
| Plaquettes disque, paire | 15 / 15 | 7,99 / 7,99 | 22,99 / 22,99 | Shimano / compatibles entrée de gamme |
| Patins V-Brake, paire | 15 / 15 | 3,49 / 3,49 | 18,49 / 18,49 | Decathlon V-Brake 100 |
| Chaîne | 16 / 16 | 9,99 / 18,32 | 25,99 / 34,32 | Decathlon 3–8 vitesses / VAE 10 vitesses |
| Pneu ville, 1 roue | 12 / 12 | 19,99 / 19,99 | 31,99 / 31,99 | Vittoria Randonneur 700×35 |
| Câble et gaine frein, externe | 15 / 15 | 6,99 / 6,99 | 21,99 / 21,99 | Kit standard |
| Réglage frein | 12 / 12 | 0 / 0 | 12 / 12 | Sans pièce |

Ces références sont des **prix publics observés**, pas une moyenne représentative de la France et pas les prix pratiqués par Les Points Vélo. La compatibilité, les pièces de qualité différente, les opérations et les frais réels peuvent varier. Les pièces standard de sécurité sont retenues neuves.

## Double comptage de main-d'œuvre

Cycle Service Lyon indique que les révisions Sérénité comprennent la pose de **jusqu'à deux remplacements éligibles** (pneus, chambres, plaquettes, chaînes, câbles externes, etc.) sans fournir les pièces. Pour éviter de surestimer le coût à l'unité, le moteur déduit de la MO facturée jusqu'à deux poses éligibles par révision en attribuant d'abord les crédits aux poses les plus coûteuses. Un réglage de frein inclus dans une révision est également déduit une fois par révision. **Hypothèse simplificatrice** : les travaux sont regroupés lors de la même visite ; en pratique il peut y avoir des visites séparées, et donc des coûts supérieurs. Le forfait d'un autre atelier peut être différent.

Coût annuel d'un panier : somme(qté × (MO + pièce)) moins les crédits de MO éligible. Le coût sur 6 mois est une proratisation des quantités **annuelles** ; approximation explicite car les pannes sont irrégulières. Les autres frais optionnels ne sont pas ajoutés aux pièces déjà comptabilisées.

## Sources de prix (consultées le 20/11/2026)

- Main-d'œuvre et forfaits : https://cycleservice.fr/tarifs et https://cycleservice.fr/reparation-velo-lyon/revisions-velo-entretien (tarifs depuis 06/04/2026).
- Chambre : https://www.decathlon.fr/tous-les-sports/velo-cyclisme/chambre-a-air-velo (5,99 €).
- Patins : https://www.decathlon.fr/p/patins-frein-v-brake-universel-100/335/m3256737 (3,49 €).
- Plaquettes : https://www.decathlon.fr/vc/plaquettes-de-frein-shimano (7,99 €).
- Chaîne classique : https://www.decathlon.fr/p/chaine-velo-3-a-8-vitesses/331640/m8640930 (9,99 €).
- Chaîne VAE : https://www.decathlon.fr/tous-les-sports/velo-cyclisme/chaines-velo (référence 10 vitesses à 18,32 €).
- Pneu ville : https://www.decathlon.fr/p/pneu-vittoria-randonneur-700x35-37-622/X8089011/m8089011 (19,99 €).
- Kit câble + gaine : https://www.decathlon.fr/p/cable-et-gaine-de-frein/200529/m8527490 (6,99 €).

## Sources de contexte

Les autres statistiques descriptives ADEME/Ecologic/ONISR et les règles LPV sont reprises de la V3. Ne jamais les interpréter comme une probabilité individuelle de crevaison ou comme des accidents évités grâce à l'abonnement.

## Tests rapides de cohérence

- Une chambre à air traditionnelle, sans révision : 17,99 € ; avec révision, 72 + 5,99 = 77,99 € (pose déjà incluse).
- Révision classique + 2 chambres + 1 paire de plaquettes : 72 + 2×5,99 + (15 + 7,99) = 106,97 € selon la règle des deux poses comprises.
- Une année sans intervention : coût à l'unité 0 €, abonnement classique 120 € / VAE 180 €.

## Hypothèses à valider avec Les Points Vélo

Compatibilité des pièces standard selon vélos ; modèles éligibles ; périmètre des composants VAE ; regroupement des travaux dans une révision ; montants de détail exacts à Lyon ; carte de parrainage et VéloScore particuliers.

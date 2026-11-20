# Les Points Vélo — Simulateur V2

Site statique, mobile-first, sans bibliothèque et sans collecte serveur. Ouvrir `index.html` dans un navigateur.

## Mise en ligne GitHub Pages
1. Créer un dépôt public GitHub.
2. Ajouter `index.html` à la racine de la branche `main`.
3. `Settings` → `Pages` → `Deploy from a branch` → `main` / `(root)` → `Save`.
4. Partager l'adresse GitHub Pages générée.

## Choix métier
- Aucun score multicritère numérique. Recommandation qualitative à règles transparentes.
- Question sur la valeur personnelle de la tranquillité, **sans** l'ajouter aux économies financières.
- Questionnaire guidé en cinq étapes. Comparaison des coûts explicite.
- Prix : classique 10 €/mois, VAE 15 €/mois, formule 6 mois +25 %, formule 12 mois au tarif normal.
- Deux sources de dépenses : saisie ou interventions cochées au tarif indicatif de main-d'œuvre. Si saisie vide : référence 60 €/an (hypothèse startup, **pas moyenne française**).
- Trois scénarios : 0 réparation, référence, référence + réparations additionnelles avec quantités saisies.
- Les quantités représentent des hypothèses choisies par le visiteur, non des prévisions. Les scénarios ne prédisent aucune panne ni probabilité.
- Engagement nominatif pour un seul vélo, pas d'offre famille, réparation et choix des pièces par le mécanicien, sécurité neuve, accessoires neufs payants.
- CTA `mailto:` pour prise de contact, sans souscription automatique.

## Réparations et quantités
Chaque catégorie possède un compteur avec boutons − / + et une saisie directe entre 0 et 20 occurrences annuelles (modifiable dans `CONFIG.maxRepairOccurrences`). Le coût annuel est `Σ(quantité annuelle × tarif unitaire de main-d’œuvre)` ; le comparatif prorate ensuite sur 6 ou 12 mois. Dans le scénario « année plus chargée », les quantités supplémentaires s’ajoutent exclusivement au scénario chargé. Les pièces ne sont pas chiffrées.

## Formules
- `abonnement = prixMensuel × (1,25 si 6 mois sinon 1) × durée`
- `dépensesÀLUnité = dépensesAnnuelles × durée / 12`
- `économiePotentielle = dépensesÀLUnité − abonnement`
- `seuilMois = abonnement ÷ (dépensesAnnuelles / 12)` lorsque dépenses > 0. Il s'agit du délai théorique d'équivalence avec le *coût total engagé* sous une répartition linéaire des dépenses, non d'une date de rentabilité d'une mensualité.
- `annéePlusChargée = référence + somme(quantité × prix unitaire de main-d’œuvre des interventions supplémentaires) × durée / 12`.

## Sources et hypothèses
| Valeur | Source, année | Statut |
|---|---|---|
| Prix et conditions des formules | Les Points Vélo, documents remis à IAE Lyon, 2026 | Déclarations de la startup ; termes contractuels à confirmer |
| 60 €/an en dépannage ponctuel | Business plan Les Points Vélo, 2026 | Hypothèse modifiable, pas moyenne française |
| Grille de main-d'œuvre | Cycle Service Lyon, tarifs 2026, https://cycleservice.fr/tarifs | Référence locale ; montants et disponibilité à revalider |
| VéloScore en 20 points, note A à E | Plaquette Les Points Vélo, 2026 | Documenté pour entreprises ; extension particuliers à valider |
| Valeur personnelle de tranquillité | Déclaration de l'utilisateur | Préférence subjective, ne pas monétiser en gain |
| Conseil qualitatif suivant fréquence et priorités | Règles de conception du prototype, 2026 | Hypothèses modifiables ; non prédictives |

## À valider avec la startup avant déploiement
1. Tarifs complets de réparation pièces incluses et mise à jour du comparateur.
2. Portée exacte des réparations couvertes, exclusions de modèles et équipements VAE.
3. Préavis, modalités de résiliation, garantie opérationnelle de 48 heures.
4. Disponibilité du VéloScore pour les particuliers et faisabilité d'une carte de parrainage.
5. Test utilisateur comparant compréhension du contrat, conversion et satisfaction.

## Personnalisation
La constante `CONFIG` se trouve au début du JavaScript, vers la fin de `index.html`. Modifier les hypothèses de simulation sans changer les tarifs décidés par l'entreprise.

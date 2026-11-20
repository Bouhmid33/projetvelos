# Simulateur Les Points Vélo

Site statique mobile-first en HTML/CSS/JavaScript, sans dépendance ni collecte de données.

## Publier sur GitHub Pages
1. Créer un dépôt GitHub public (ou privé compatible avec votre offre GitHub).
2. Déposer `index.html` à la racine du dépôt.
3. Ouvrir `Settings` > `Pages` > `Build and deployment`.
4. Choisir `Deploy from a branch`, branche `main`, dossier `/ (root)`, puis sauvegarder.
5. Visiter l’URL GitHub Pages affichée par GitHub. Le formulaire d'e-mail utilise `mailto:`.

## Logique
- Prix 12 mois : classique 10 €/mois ; électrique 15 €/mois.
- Prix 6 mois : +25 % mensuel ; comparaison sur 6 mois.
- Mode historique : budget annuel saisi, divisé par deux pour 6 mois.
- Sans historique : 60 €/an du business plan Les Points Vélo, **non vérifié comme moyenne nationale**.
- Mode scénario : 1 intervention de chaque type sélectionné sur un an, sans prédiction de panne. Tarifs main-d’œuvre uniquement.
- Le seuil affiché en mois est le coût **total engagé** divisé par les dépenses mensuelles estimées à l’unité. Il n'est pas un gain garanti.
- En cas de faible budget de réparation, le simulateur dit explicitement que l'abonnement est moins avantageux financièrement.

## Sources
- Les Points Vélo, Mission étudiants IAE et Réponses aux étudiants (2026).
- Cycle Service Lyon, https://cycleservice.fr/tarifs (main-d’œuvre TTC au 6 avril 2026).
- ONISR, bilan définitif 2025, https://www.onisr.securite-routiere.gouv.fr/etat-de-linsecurite-routiere/bilans-annuels-de-la-securite-routiere/bilan-2025-de-la-securite-routiere
- VéloScore Les Points Vélo, document transmis (2026).

## À valider avant publication commerciale
Éligibilité détaillée des modèles, prestations couvertes (notamment composants électriques), modalités de résiliation/préavis, possibilité d'étendre VéloScore aux particuliers, format du parrainage, pertinence des hypothèses et des prix de pièces, usage des couleurs et identité de marque, URL de souscription.

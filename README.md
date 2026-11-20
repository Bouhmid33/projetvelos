# Simulateur Les Points Vélo — V3 (prototype à valider)

## Déployer

1. Décompresser l'archive.
2. Créer un dépôt public GitHub (ex. `simulateur-les-points-velo`).
3. Ajouter `index.html` à la racine du dépôt.
4. Dans **Settings → Pages**, choisir **Deploy from a branch**, **main**, dossier **/(root)**.
5. Le site sera accessible sous `https://<identifiant>.github.io/<depot>/`.

Aucune dépendance, aucun build, pas de serveur, aucune collecte de données. La prise de contact ouvre le logiciel e-mail du visiteur.

## Méthodologie

Ce prototype **n'annonce aucune probabilité de crevaison ou d'accident individuel** car les bases consultées ne contiennent pas le kilométrage des vélos suivi avec les événements mécaniques. Il comporte :

- Kilométrage annuel estimé : distance par jour × jours/semaine × semaines/an, ou valeur saisie.
- Statistiques de population : 22 % de recours à un professionnel (ADEME, estimation 2024) ; 47 € / intervention (Ecologic, prix de référence 2022 repris ADEME 2026) ; 13 971 réparations réseau Roulez Jeunesse 2025. Ces données **ne sont pas converties en taux individuel de panne**.
- Scénarios d'interventions : « calme », « avec révision », « chargée » ; **hypothèses de travail**, éditables par quantités 0–20.
- Tarifs d'intervention : main-d'œuvre seule TTC Cycle Service Lyon, 6 avril 2026. Pièces supplémentaires : saisie libre, 0 par défaut.
- Coût du scénario = (somme des quantités × tarifs de main-d'œuvre + coût de pièces déclaré) × mois/12.
- Coût abonnement = prix base (10 € classique, 15 € électrique) × (1,25 si 6 mois, sinon 1) × durée en mois.
- Comparaison = coût du scénario – coût de l'abonnement. Les préférences et la volonté de payer pour la tranquillité ne sont **jamais monétisées comme une économie**.
- Scénarios de résultats qualitatifs fondés sur proximité, usage, préférences et coût simulé. Aucune note /100.
- Accidents ONISR : 235 décès cyclistes en France métropolitaine en 2025, dont 96 sans tiers. **Ne démontre ni causalité mécanique, ni réduction des accidents par l'abonnement**.
- VéloScore : informations issues de la plaquette LPV pour entreprises. Extension aux particuliers **non confirmée**.

## Sources

- [ADEME — Impact socio-économique des usages du vélo en France (2026)](https://librairie.ademe.fr/mobilite-et-transports/9313-11108-impact-socio-economique-des-usages-du-velo-en-france.html)
- [Ecologic — Étude sur la réparation des cycles (2023)](https://www.ecologic-france.com/ressources/etude-sur-la-reparation-des-cycles)
- [Roulez Jeunesse — Bilan des pannes vélo 2025](https://blog.roulezjeunesse.com/bilan-pannes-velo-2025/)
- [Cycle Service Lyon — Tarifs appliqués depuis 6 avril 2026](https://cycleservice.fr/tarifs)
- [ONISR — Bilan définitif 2025](https://www.onisr.securite-routiere.gouv.fr/etat-de-linsecurite-routiere/bilans-annuels-de-la-securite-routiere/bilan-2025-de-la-securite-routiere)
- Documents startup 2026 : Mission étudiants, Réponses aux étudiants, VéloScore.
- Documents groupe : Benchmarking, Rapport, Rapport partie rentabilité.

## Paramètres à modifier

Dans `index.html`, chercher `const CONFIG`. S'y trouvent : tarifs de souscription, taux de population purement descriptifs, prix d'intervention, scénarios et adresse e-mail.

## Hypothèses et validation nécessaire avec LPV

1. Tarifs complets à l'unité, pièces et main-d'œuvre, avec règles de regroupement des travaux (éviter double comptage d'une révision).
2. Périmètre exact des réparations couvertes, exclusions, composants VAE, et conditions du délai de 48 h.
3. Conditions contractuelles précises du 6 mois / 12 mois, résiliation et préavis.
4. Statistiques de panne **par km** : il faut une cohorte avec kilomètres parcourus, type de vélo, durée d'observation et nombre de réparations. Sans cela, pas de modèle Poisson calibré.
5. Utilisation du VéloScore pour particuliers et carte de parrainage / diagnostic découverte.
6. Seuil qualitatif de recommandations, validation par enquête et A/B test avec des cyclistes.
7. Limites de l'offre, notamment vélo cargo, modèles rares, batterie/moteur électrique.

## Vérification technique

Fichier autonome utilisable localement ou GitHub Pages. Vérifier sur navigateur mobile réel avant publication.

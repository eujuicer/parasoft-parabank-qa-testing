# Plan de test — ParaBank

Projet final — Formation Testeur QA (BStorm) — 2026

## 1. Contexte et objectif

ParaBank est une application bancaire de démonstration développée par Parasoft, utilisée comme cible d'entraînement pour les tests logiciels (manuels, API, UI, automatisation). Elle dispose d'une interface web, d'une API REST avec authentification, d'une persistance de données et de règles métier réelles (gestion de comptes, virements, prêts, paiements de factures).

L'objectif de cette campagne est de valider les parcours critiques de l'application selon une approche basée sur les risques, et de démontrer la maîtrise de la chaîne complète d'assurance qualité : stratégie, tests manuels, tests d'API, automatisation UI, intégration continue.

## 2. Périmètre

### Inclus dans le périmètre
- Authentification (connexion, inscription)
- Ouverture de compte (Open New Account)
- Virement entre comptes (Transfer Funds)
- Paiement de factures (Bill Pay)
- Recherche de transactions (Find Transactions)
- API REST (authentification, opérations bancaires de base)

### Hors périmètre (justification : temps disponible, criticité moindre)
- Demande de prêt (Request Loan) — logique métier complexe (calcul d'éligibilité), testée en exploratoire uniquement si le temps le permet
- Mise à jour des informations de contact (Update Contact Info) — faible risque métier (pas de mouvement d'argent)
- Pages statiques / marketing (About Us, Services, Products, Locations)

## 3. Hypothèses et contraintes

- L'instance de démonstration publique (`parabank.parasoft.com`) est partagée par de nombreux utilisateurs dans le monde et présente une instabilité connue (erreurs serveur intermittentes, réinitialisations de données). **Les tests d'automatisation et le pipeline CI s'exécuteront contre l'instance locale (Docker)**, plus stable et reproductible ; l'instance publique sert uniquement à l'exploration manuelle initiale.
- Les données de test (comptes, utilisateurs) sont recréées à chaque campagne — l'application ne garantit pas la persistance sur l'instance publique.
- Travail strictement individuel, sur la durée impartie par le formateur.

## 4. Analyse de risques et priorisation (approche risk-based)

| Fonctionnalité | Impact métier | Probabilité de défaut | Niveau de risque | Priorité de test |
|---|---|---|---|---|
| Connexion / Authentification | Élevé (porte d'entrée de toute l'appli) | Moyenne | **Élevé** | Haute |
| Transfer Funds (virement) | Élevé (mouvement d'argent) | Élevée (BUG-001 déjà identifié) | **Élevé** | Haute |
| Bill Pay (paiement facture) | Élevé (mouvement d'argent) | Moyenne | **Élevé** | Haute |
| Open New Account | Moyen | Faible | Moyen | Moyenne |
| Find Transactions | Faible (lecture seule) | Faible | Faible | Moyenne |
| Request Loan | Moyen (logique d'éligibilité complexe) | Moyenne | Moyen | Basse (hors périmètre détaillé) |
| Update Contact Info | Faible | Faible | Faible | Basse (hors périmètre) |

**Justification** : les fonctionnalités impliquant un mouvement d'argent (Transfer Funds, Bill Pay) concentrent l'effort de test le plus important, car une anomalie y a un impact direct et potentiellement critique pour un utilisateur réel. La découverte de BUG-001 sur Transfer Funds dès l'exploration initiale confirme la pertinence de cette priorisation.

## 5. Techniques de conception de test utilisées

- **Partitions d'équivalence** : ex. montant de virement valide / négatif / nul / non numérique
- **Analyse aux valeurs limites** : ex. montant = solde disponible exact, solde + 0.01
- **Tests exploratoires** : navigation libre pour découvrir des comportements non spécifiés (a permis de trouver BUG-001)

## 6. Environnements de test

| Environnement | Usage |
|---|---|
| `parabank.parasoft.com` (démo publique) | Exploration manuelle initiale, capture des messages système réels |
| Instance locale via `docker-compose` (dépôt `parabank` cloné) | Tests d'automatisation (API, UI) et pipeline CI — environnement stable et reproductible |

## 7. Critères d'entrée

- Choix de l'application validé par le formateur ✅ (fait)
- Instance locale ParaBank fonctionnelle via Docker
- Accès en écriture au dépôt Git du projet

## 8. Critères de sortie

- 100 % des cas de test priorité Haute exécutés (Login, Transfer Funds, Bill Pay)
- Au moins 80 % des cas de test priorité Moyenne exécutés
- Toutes les anomalies trouvées documentées avec étapes de reproduction
- Pipeline CI exécuté avec succès (ou échec justifié) et visible dans l'historique du dépôt
- Rapport de campagne final rédigé avec métriques et recommandations

## 9. Livrables

- Ce plan de test
- Cas de test manuels (`test-cases/`)
- Rapports d'anomalie (`bugs/`)
- Collection Bruno pour les tests d'API (à venir)
- Suite PyTest automatisée (à venir)
- Framework d'automatisation UI Playwright/Selenium en Page Object Model (à venir)
- Pipeline GitHub Actions (à venir)
- Rapport de campagne final (à venir)

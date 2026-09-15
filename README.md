# Parasoft ParaBank — Projet final QA

Projet final de la formation Testeur QA (BStorm), réalisé sur l'application bancaire de démonstration [ParaBank](https://parabank.parasoft.com/parabank/index.htm) (Parasoft) — application choisie et validée par le formateur, distincte de l'application fil rouge utilisée pendant la formation.

## Objectif

Démontrer la maîtrise de la chaîne complète d'assurance qualité : stratégie de test, tests manuels, tests d'API, automatisation UI, intégration continue, jusqu'à la soutenance devant jury.

## Structure du dépôt

| Élément | Statut |
|---|---|
| [`test-plan.md`](test-plan.md) — stratégie, périmètre, analyse de risques, critères d'entrée/sortie | ✅ |
| `test-cases/` — cas de test manuels (voir [test-cases/README.md](test-cases/README.md)) | 🟡 en cours |
| `bugs/` — rapports d'anomalie, dont [BUG-001](bugs/BUG-001-transfer-empty-amount.md) | 🟡 en cours |
| Campagne Squash TM / Xray (traçabilité exigence → cas → exécution → anomalie) | ❌ à faire |
| Collection Bruno (API, auth OAuth2/JWT, scénario chaîné) | ❌ à faire |
| Suite PyTest automatisée (data-driven, JSON Schema, cas sécurité) | ❌ à faire |
| Framework UI Playwright/Selenium (Page Object Model) | ❌ à faire |
| Pipeline GitHub Actions + rapports Allure | ❌ à faire |
| Rapport de campagne final (métriques, risques résiduels, recommandations) | ❌ à faire |

## Résultats des tests manuels (à date)

- Connexion / Inscription : validées (TC-REG-01, TC-REG-02, TC-LOGIN-01)
- Bill Pay : validé (TC-BILL-01, TC-BILL-02)
- Transfer Funds : 1 anomalie trouvée (BUG-001)
- Find Transactions : validé (TC-FIND-01)
- Open New Account : validé (TC-OPEN-01)

## Environnements

- Démo publique `parabank.parasoft.com` : exploration manuelle (voir note sur son instabilité dans [test-plan.md](test-plan.md))
- Instance locale via Docker : automatisation et CI, environnement stable — voir [environment/README.md](environment/README.md) pour l'installation

## Statut

En cours — voir [test-plan.md](test-plan.md) pour le détail du périmètre et de la priorisation basée sur les risques.

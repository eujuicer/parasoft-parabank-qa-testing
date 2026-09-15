# Parasoft ParaBank — QA Testing Project

Projet de tests QA sur l'application bancaire de démonstration [ParaBank](https://parabank.parasoft.com/parabank/index.htm) (Parasoft), réalisé dans le cadre de la formation Testeur QA.

## Objectif

Valider les principaux parcours utilisateurs de ParaBank via des tests manuels structurés, avec une base prête pour l'automatisation.

## Périmètre fonctionnel

- Connexion / inscription utilisateur
- Ouverture de compte (Open New Account)
- Virement entre comptes (Transfer Funds)
- Paiement de factures (Bill Pay)
- Consultation des transactions (Find Transactions)
- Mise à jour des informations de contact (Update Contact Info)
- Demande de prêt (Request Loan)

## Structure du dépôt

- `test-cases/` — cas de test manuels, exécutés sur l'instance de démo publique (voir [test-cases/README.md](test-cases/README.md))
- `bugs/` — anomalies trouvées, dont [BUG-001](bugs/BUG-001-transfer-empty-amount.md) (erreur serveur sur Transfer Funds avec montant vide)

## Résultats

- Connexion / Inscription : validées (TC-REG-01, TC-REG-02, TC-LOGIN-01)
- Bill Pay : validé (TC-BILL-01, TC-BILL-02)
- Transfer Funds : 1 anomalie trouvée (BUG-001)
- Find Transactions : validé (TC-FIND-01)
- Open New Account : non testable pour le moment — l'instance de démo publique renvoie une erreur serveur de façon intermittente sur plusieurs pages (site partagé, connu pour son instabilité)

## Statut

En cours — cas de test rédigés et exécutés pour Login/Register, Bill Pay, Transfer Funds, Find Transactions. À compléter : Open New Account, Update Contact Info, Request Loan.

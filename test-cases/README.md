# Cas de test manuels

Un fichier Markdown par fonctionnalité, chaque cas de test suivant ce format :

- **Technique** : partition d'équivalence, analyse aux valeurs limites, ou test exploratoire
- **Priorité** : Haute / Moyenne / Basse
- **Statut** : ✅ Pass / ❌ Fail / ⬜ Not Run
- **Préconditions**, **Étapes**, **Résultat attendu**, **Résultat obtenu**

## Fichiers

- [01-connexion.md](01-connexion.md) — Connexion / Inscription
- [02-bill-pay.md](02-bill-pay.md) — Paiement de factures
- [03-transfer-funds.md](03-transfer-funds.md) — Virements entre comptes
- [04-find-transactions.md](04-find-transactions.md) — Recherche de transactions
- [05-open-account.md](05-open-account.md) — Ouverture de compte

> Ces fichiers seront importés dans Squash TM pour la campagne de gestion avec traçabilité exigence → cas → exécution → anomalie (voir [test-plan.md](../test-plan.md)).

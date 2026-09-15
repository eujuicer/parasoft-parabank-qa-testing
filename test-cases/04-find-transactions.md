# Find Transactions

## TC-FIND-01 — Recherche de transaction par montant

- **Technique** : Partition d'équivalence (classe valide)
- **Priorité** : Moyenne
- **Statut** : ✅ Pass

**Préconditions** : Utilisateur connecté, au moins une transaction existante d'un montant connu

**Étapes** :
1. Aller sur Find Transactions
2. Sélectionner le compte concerné
3. Saisir le montant exact dans Find by Amount
4. Cliquer sur Find Transactions

**Résultat attendu** : Le tableau Transaction Results affiche toutes les transactions correspondant à ce montant, avec Date, Transaction, Debit/Credit.

**Résultat obtenu** : Conforme : recherche d'un virement de 25.00 $ a bien retourné les 2 lignes liées (Funds Transfer Sent / Funds Transfer Received) avec la bonne date.

---

## TC-FIND-02 — Recherche par Transaction ID inexistant

- **Technique** : Partition d'équivalence (classe invalide)
- **Priorité** : Basse
- **Statut** : ⬜ Not Run

**Préconditions** : Utilisateur connecté

**Étapes** :
1. Aller sur Find Transactions
2. Saisir un ID de transaction qui n'existe pas
3. Cliquer sur Find Transactions

**Résultat attendu** : Un message clair indique qu'aucune transaction n'a été trouvée.

**Résultat obtenu** : —

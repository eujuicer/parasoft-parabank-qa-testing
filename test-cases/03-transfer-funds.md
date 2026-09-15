# Transfer Funds

## TC-TRANS-01 — Virement avec montant valide

- **Technique** : Partition d'équivalence (classe valide)
- **Priorité** : Haute
- **Statut** : ✅ Pass

**Préconditions** : Utilisateur connecté, au moins un compte disponible

**Étapes** :
1. Aller sur Transfer Funds
2. Saisir un montant valide dans Amount
3. Sélectionner From account # et to account #
4. Cliquer sur Transfer

**Résultat attendu** : Le virement est effectué, un message de confirmation affiche le montant et les comptes concernés.

**Résultat obtenu** : Conforme : *"Transfer Complete! $[Amount] has been transferred from account #[X] to account #[Y]."* — voir TC-TRANS-03 pour une remarque sur le cas où X = Y.

---

## TC-TRANS-02 — Virement avec le champ Amount vide

- **Technique** : Partition d'équivalence (classe invalide — valeur absente)
- **Priorité** : Haute
- **Statut** : ❌ Fail

**Préconditions** : Utilisateur connecté

**Étapes** :
1. Aller sur Transfer Funds
2. Laisser le champ Amount vide
3. Cliquer sur Transfer

**Résultat attendu** : Un message de validation clair s'affiche (ex: *"Amount is required."*), le virement n'est pas effectué.

**Résultat obtenu** : **NON CONFORME — voir [BUG-001](../bugs/BUG-001-transfer-empty-amount.md)** : une erreur serveur générique s'affiche (*"An internal error has occurred and has been logged."*) au lieu d'un message de validation.

---

## TC-TRANS-03 — Virement avec un compte source identique au compte destination

- **Technique** : Test exploratoire
- **Priorité** : Basse
- **Statut** : ⬜ Not Run (observation faite, à qualifier)

**Préconditions** : Utilisateur connecté avec un seul compte (ou From = To sélectionnés manuellement)

**Étapes** :
1. Aller sur Transfer Funds
2. Sélectionner le même compte pour From et To
3. Saisir un montant valide
4. Cliquer sur Transfer

**Résultat attendu** : Selon la spécification attendue : soit le virement est bloqué avec un message, soit il est accepté sans effet réel sur le solde.

**Résultat obtenu** : OBSERVÉ : le virement est accepté sans avertissement. Deux lignes apparaissent dans Find Transactions (*"Funds Transfer Sent"* et *"Funds Transfer Received"*) sur le même compte — à clarifier avec les exigences métier avant de qualifier ceci de bug.

---

## TC-TRANS-04 — Virement d'un montant exactement égal au solde disponible

- **Technique** : Analyse aux valeurs limites (limite haute autorisée)
- **Priorité** : Moyenne
- **Statut** : ⬜ Not Run

**Préconditions** : Utilisateur connecté, solde du compte connu et non nul

**Étapes** :
1. Noter le solde disponible du compte source
2. Aller sur Transfer Funds
3. Saisir un montant exactement égal au solde disponible
4. Cliquer sur Transfer

**Résultat attendu** : Le virement est accepté, le solde du compte source passe à 0.00 $.

**Résultat obtenu** : —

---

## TC-TRANS-05 — Virement d'un montant supérieur de 0,01 $ au solde disponible

- **Technique** : Analyse aux valeurs limites (juste au-dessus de la limite)
- **Priorité** : Moyenne
- **Statut** : ⬜ Not Run

**Préconditions** : Utilisateur connecté, solde du compte connu et non nul

**Étapes** :
1. Noter le solde disponible du compte source
2. Aller sur Transfer Funds
3. Saisir un montant égal au solde disponible + 0,01 $
4. Cliquer sur Transfer

**Résultat attendu** : Le virement est refusé avec un message indiquant un solde insuffisant.

**Résultat obtenu** : — *(à vérifier : pourrait révéler une seconde anomalie si l'erreur générique de BUG-001 apparaît à la place d'un message clair)*

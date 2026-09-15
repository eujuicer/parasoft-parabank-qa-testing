# Bill Pay

## TC-BILL-01 — Paiement de facture avec champs adresse vides

- **Technique** : Partition d'équivalence (classe invalide — champs vides)
- **Priorité** : Moyenne
- **Statut** : ✅ Pass

**Préconditions** : Utilisateur connecté, au moins un compte disponible

**Étapes** :
1. Aller sur Bill Pay
2. Saisir uniquement le Payee Name, Account #, Verify Account # et Amount
3. Laisser Address / City / State / Zip Code / Phone # vides
4. Cliquer sur Send Payment

**Résultat attendu** : Un message d'erreur s'affiche pour chaque champ obligatoire manquant, le paiement n'est pas envoyé.

**Résultat obtenu** : Conforme : messages inline (*"Address is required."*, *"City is required."*, *"State is required."*, *"Zip Code is required."*, *"Phone number is required."*)

---

## TC-BILL-02 — Paiement de facture avec toutes les données valides

- **Technique** : Partition d'équivalence (classe valide)
- **Priorité** : Haute
- **Statut** : ✅ Pass

**Préconditions** : Utilisateur connecté, solde du compte suffisant

**Étapes** :
1. Aller sur Bill Pay
2. Remplir tous les champs (Payee Name, Address, City, State, Zip Code, Phone #, Account #, Verify Account #, Amount)
3. Sélectionner le compte source (From account #)
4. Cliquer sur Send Payment

**Résultat attendu** : Le paiement est traité, un message de confirmation s'affiche avec le montant, le bénéficiaire et le compte débité.

**Résultat obtenu** : Conforme : *"Bill Payment to [Payee] in the amount of $[Amount] from account [N] was successful."*

---

## TC-BILL-03 — Paiement avec Account # différent de Verify Account #

- **Technique** : Partition d'équivalence (classe invalide — incohérence de saisie)
- **Priorité** : Moyenne
- **Statut** : ⬜ Not Run

**Préconditions** : Utilisateur connecté

**Étapes** :
1. Remplir le formulaire Bill Pay
2. Saisir des valeurs différentes dans Account # et Verify Account #
3. Cliquer sur Send Payment

**Résultat attendu** : Un message d'erreur indique que les deux comptes ne correspondent pas.

**Résultat obtenu** : —

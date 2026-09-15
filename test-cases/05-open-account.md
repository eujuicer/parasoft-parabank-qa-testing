# Open New Account

## TC-OPEN-01 — Ouverture d'un nouveau compte CHECKING

- **Technique** : Partition d'équivalence (classe valide)
- **Priorité** : Haute
- **Statut** : ✅ Pass

**Préconditions** : Utilisateur connecté, au moins un compte existant pour le dépôt initial

**Étapes** :
1. Aller sur Open New Account
2. Sélectionner le type de compte CHECKING
3. Sélectionner le compte source pour le dépôt initial
4. Cliquer sur Open New Account

**Résultat attendu** : Le nouveau compte est créé avec un numéro de compte unique, un message de confirmation s'affiche.

**Résultat obtenu** : Conforme : *"Account Opened! Congratulations, your account is now open."* + nouveau numéro de compte affiché (ex: #15564)

---

## TC-OPEN-02 — Ouverture d'un nouveau compte SAVINGS

- **Technique** : Partition d'équivalence (classe valide — variante de type de compte)
- **Priorité** : Moyenne
- **Statut** : ⬜ Not Run

**Préconditions** : Utilisateur connecté, au moins un compte existant

**Étapes** :
1. Aller sur Open New Account
2. Sélectionner le type de compte SAVINGS
3. Sélectionner le compte source
4. Cliquer sur Open New Account

**Résultat attendu** : Le nouveau compte SAVINGS est créé avec un numéro de compte unique.

**Résultat obtenu** : —

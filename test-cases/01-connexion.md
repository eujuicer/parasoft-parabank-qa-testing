# Connexion / Inscription

## TC-REG-01 — Inscription avec formulaire vide

- **Technique** : Partition d'équivalence (classe invalide — champs vides)
- **Priorité** : Haute
- **Statut** : ✅ Pass

**Préconditions** : Être sur la page Register

**Étapes** :
1. Aller sur https://parabank.parasoft.com/parabank/register.htm
2. Ne rien saisir
3. Cliquer sur Register

**Résultat attendu** : Un message d'erreur s'affiche pour chaque champ obligatoire (First Name, Last Name, Address, City, State, Zip Code, SSN, Username, Password, Confirm) — Phone # n'est pas obligatoire.

**Résultat obtenu** : Conforme : chaque champ obligatoire affiche son propre message inline (ex: *"First name is required."*)

---

## TC-REG-02 — Inscription avec toutes les données valides

- **Technique** : Partition d'équivalence (classe valide)
- **Priorité** : Haute
- **Statut** : ✅ Pass

**Préconditions** : Être sur la page Register, username non déjà utilisé

**Étapes** :
1. Remplir tous les champs avec des données valides
2. Saisir le même mot de passe dans Password et Confirm
3. Cliquer sur Register

**Résultat attendu** : Le compte est créé, l'utilisateur est automatiquement connecté et redirigé vers Account Services avec un nouveau numéro de compte.

**Résultat obtenu** : Conforme : message *"Your account was created successfully. You are now logged in."* + compte créé (ex: #13677, solde initial 515.50 $)

---

## TC-LOGIN-01 — Connexion avec identifiants invalides

- **Technique** : Partition d'équivalence (classe invalide)
- **Priorité** : Haute
- **Statut** : ✅ Pass

**Préconditions** : Un compte utilisateur existe

**Étapes** :
1. Aller sur la page de connexion
2. Saisir un nom d'utilisateur valide et un mot de passe incorrect
3. Cliquer sur Log In

**Résultat attendu** : Un message d'erreur générique s'affiche, l'utilisateur n'est pas connecté (pas de détail sur lequel des deux champs est en cause, ce qui est correct du point de vue sécurité).

**Résultat obtenu** : Conforme : message *"The username and password could not be verified."*

---

## TC-LOGIN-02 — Connexion avec identifiants valides

- **Technique** : Partition d'équivalence (classe valide)
- **Priorité** : Haute
- **Statut** : ⬜ Not Run

**Préconditions** : Un compte utilisateur existe et est actif

**Étapes** :
1. Aller sur la page de connexion
2. Saisir un nom d'utilisateur et mot de passe valides
3. Cliquer sur Log In

**Résultat attendu** : L'utilisateur est redirigé vers la page Accounts Overview / Account Services.

**Résultat obtenu** : —

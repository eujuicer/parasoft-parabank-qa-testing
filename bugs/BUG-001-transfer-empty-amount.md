# Rapport d'anomalie

**ID** : BUG-001
**Titre** : Erreur serveur générique au lieu d'un message de validation sur Transfer Funds avec un montant vide
**Date** : 2026-09-15
**Environnement** : Chrome, Windows, https://parabank.parasoft.com/parabank/transfer.htm (instance de démo publique)
**Sévérité** : Majeure
**Priorité** : Haute

## Étapes de reproduction
1. Se connecter avec un compte utilisateur valide
2. Aller sur "Transfer Funds"
3. Laisser le champ "Amount" vide
4. Sélectionner un compte source et un compte destination valides
5. Cliquer sur "Transfer"

## Résultat obtenu
Une page d'erreur générique s'affiche : *"Error! An internal error has occurred and has been logged."* — comportement reproduit de manière constante (2 tentatives).

## Résultat attendu
Un message de validation côté champ, cohérent avec le reste de l'application (ex : sur "Register" et "Bill Pay", un champ obligatoire vide affiche "X is required." sans crasher), du type "Amount is required." ou "Please enter a valid amount."

## Remarque
Les formulaires "Register" et "Bill Pay" gèrent correctement leurs champs obligatoires vides avec des messages inline. "Transfer Funds" est donc incohérent avec le reste de l'application sur ce point — probable absence de validation du champ Amount côté serveur avant conversion numérique (hypothèse : NumberFormatException non interceptée).

## Pièces jointes
(à compléter avec capture d'écran)

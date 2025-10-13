# Leçon 8 : Gérer les Erreurs Courantes (La boîte à outils de secours)

Tout le monde fait des erreurs. Un bon développeur ne se définit pas par son absence d'erreurs, mais par sa capacité à les corriger proprement. Git offre plusieurs outils pour revenir en arrière ou corriger le tir.

## Scénario 1 : "J'ai fait une faute de frappe dans mon dernier message de commit !"

C'est l'erreur la plus simple à corriger, à condition que vous n'ayez pas encore poussé votre commit sur le dépôt distant.

### La solution : `git commit --amend`

Cette commande permet de "modifier" le tout dernier commit. Elle ouvre votre éditeur de texte pour que vous puissiez changer le message. Vous pouvez aussi en profiter pour ajouter des fichiers que vous auriez oubliés.

```bash
# Oups, j'ai oublié le fichier "style.css"
git add style.css

# Ouvre l'éditeur pour corriger le message du dernier commit
# et y inclure le nouveau fichier ajouté.
git commit --amend
```

## Scénario 2 : "J'ai ajouté un fichier à la Staging Area par erreur."

Vous avez fait `git add .` mais un fichier sensible ou inutile s'est glissé dedans.

### La solution : `git reset` (pour la Staging Area)

`git reset` sans commit spécifié agit sur la Staging Area.

```bash
# Pour retirer un fichier spécifique de la Staging Area
git reset nom-du-fichier.txt

# Pour vider complètement la Staging Area
git reset
```
Vos modifications dans les fichiers ne sont pas perdues, elles sont simplement retirées de la zone de préparation.

## Scénario 3 : "Mes derniers commits locaux sont mauvais, je veux revenir en arrière."

Votre travail sur une branche locale est parti dans la mauvaise direction. Vous n'avez **pas encore poussé** ces commits.

### La solution : `git reset` (avec un commit)

`git reset` peut aussi réinitialiser votre branche à un état antérieur. `HEAD` est un pointeur vers votre position actuelle (le dernier commit).

-   `git reset --soft HEAD~1` : Annule le dernier commit, mais garde les modifications dans la Staging Area. Pratique pour refaire un commit correct.
-   `git reset --mixed HEAD~1` (comportement par défaut) : Annule le dernier commit et laisse les modifications dans votre répertoire de travail. Vous devrez les `git add` à nouveau.
-   `git reset --hard HEAD~1` : **ATTENTION, DANGEREUX**. Annule le dernier commit ET **supprime définitivement** toutes les modifications associées. À n'utiliser que si vous êtes absolument sûr de vouloir tout jeter.

## Scénario 4 : "J'ai poussé un commit qui contient un bug et il faut l'annuler."

C'est le cas le plus délicat. Le commit est public, sur le dépôt distant. Vous ne devez **JAMAIS** utiliser `git reset` sur une branche partagée, car cela réécrit l'histoire et crée le chaos pour vos collaborateurs.

### La solution : `git revert`

`git revert` est la méthode sûre pour annuler un commit public. Au lieu de supprimer le commit de l'histoire, il crée un **nouveau commit** qui fait exactement l'inverse des changements du commit problématique.

L'histoire est préservée, et l'annulation est documentée.

```bash
# Identifiez le hash (l'identifiant) du commit à annuler avec `git log`
# Par exemple : 7a8b2c9

# Crée un nouveau commit qui annule les changements de 7a8b2c9
git revert 7a8b2c9

# Il ne vous reste plus qu'à pousser ce nouveau commit d'annulation
git push
```

En résumé :
-   **Histoire locale (non poussée) ?** `git commit --amend` et `git reset` sont vos amis.
-   **Histoire publique (poussée) ?** `git revert` est la seule option sûre.

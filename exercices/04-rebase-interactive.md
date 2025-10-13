# Exercice 4 : Le Rebase Interactif pour un Historique Propre

**Objectif :** Apprendre à utiliser le rebase interactif (`rebase -i`) pour modifier, fusionner (squash) et réorganiser des commits avant de les partager.

---

### Contexte

Parfois, en développant une fonctionnalité, on a tendance à faire beaucoup de petits commits de travail ("WIP", "correction typo", "ça marche enfin"). Avant de fusionner ce travail dans une branche principale, il est bon de "nettoyer" cet historique pour le rendre plus lisible. C'est le rôle du rebase interactif.

### Étapes à réaliser

1.  **Partez d'un dépôt propre**, sur la branche `master` (vous pouvez réutiliser le projet des exercices précédents).

2.  **Créez une nouvelle branche** pour cet exercice, nommée `feature/refactoring-bio`.
    <details>
      <summary>Commande</summary>
      <pre><code>git checkout -b feature/refactoring-bio</code></pre>
    </details>

3.  Maintenant, nous allons faire une série de petits commits "brouillons". Modifiez le fichier `biographie.txt` et faites un commit **après chaque modification** :
    -   Ajoutez une ligne "Début du refactoring." -> Commit avec le message `WIP: start refactoring`.
    -   Corrigez une faute d'orthographe quelque part. -> Commit avec le message `fix: typo`.
    -   Supprimez la ligne "Début du refactoring." et ajoutez "Version finale de la biographie." -> Commit avec le message `feat: final version of bio`.

4.  **Consultez votre historique**. Vous devriez voir ces trois commits un peu désordonnés.
    <details>
      <summary>Commande</summary>
      <pre><code>git log --oneline</code></pre>
    </details>

5.  Il est temps de nettoyer ! Nous allons fusionner ces 3 derniers commits en un seul. **Lancez le rebase interactif** en lui indiquant de travailler sur les 3 derniers commits depuis votre position actuelle (`HEAD`).
    <details>
      <summary>Commande</summary>
      <pre><code>git rebase -i HEAD~3</code></pre>
    </details>

6.  **L'éditeur de texte s'ouvre**. Il vous montre la liste des commits, avec le mot `pick` devant chacun. `pick` signifie "conserver ce commit".
    ```
    pick 2d3f4a5 WIP: start refactoring
    pick 9a8b7c6 fix: typo
    pick 1e2d3f4 feat: final version of bio
    ```

7.  **Modifiez ce fichier** pour dire à Git ce que vous voulez faire. Nous allons garder le premier commit (`pick`) et fusionner les deux suivants (`squash`) dans celui-ci.
    -   Gardez la première ligne avec `pick`.
    -   Remplacez `pick` par `s` (ou `squash`) pour les deuxième et troisième lignes.
    ```
    pick 2d3f4a5 WIP: start refactoring
    s 9a8b7c6 fix: typo
    s 1e2d3f4 feat: final version of bio
    ```
    -   Enregistrez et fermez le fichier.

8.  **Un nouvel éditeur s'ouvre**. Git vous demande maintenant de rédiger le **nouveau message de commit** qui combinera les messages des trois anciens commits. Nettoyez ce texte et écrivez un seul message de commit clair et concis, par exemple : `refactor(bio): amélioration de la biographie`.

9.  Enregistrez et fermez ce deuxième fichier.

10. **Vérifiez à nouveau l'historique**. Si tout s'est bien passé, vos trois commits brouillons ont été remplacés par un seul commit propre et explicite.

---

**Bravo !** Vous avez utilisé l'un des outils les plus puissants de Git pour maintenir un historique de projet lisible et professionnel. C'est une compétence très appréciée dans le travail en équipe.

# Leçon 6 : Collaboration avec les Pull Requests

Nous savons maintenant travailler avec un dépôt distant. Mais comment collabore-t-on de manière propre et organisée sur un projet ? La réponse est : les **Pull Requests** (ou *Merge Requests* sur GitLab).

Une Pull Request (PR) est une demande formelle d'intégrer les modifications d'une de vos branches dans une autre (généralement la branche principale `master` ou `main`). C'est un espace de discussion et de revue de code avant la fusion.

## Le workflow de la Pull Request

Voici le scénario le plus courant pour un contributeur sur un projet :

1.  **Créer une branche** : Vous ne travaillez JAMAIS directement sur `master`. Pour chaque nouvelle fonctionnalité ou correctif, vous créez une branche descriptive.
    ```bash
    git checkout -b feature/nouvelle-page-incroyable
    ```

2.  **Faire des commits** : Vous travaillez sur votre branche, en faisant des commits clairs et atomiques.

3.  **Pousser la branche sur GitHub** : Une fois votre travail prêt (ou même en cours si vous voulez un avis), vous poussez votre branche sur le dépôt distant `origin`.
    ```bash
    git push origin feature/nouvelle-page-incroyable
    ```

4.  **Ouvrir la Pull Request** : Dans l'interface de GitHub, vous verrez apparaître un bouton pour créer une Pull Request à partir de la branche que vous venez de pousser. Cliquez dessus.
    -   Vous donnez un titre clair à votre PR.
    -   Vous écrivez une description expliquant ce que vous avez fait et pourquoi.
    -   Vous pouvez désigner des "reviewers" (relecteurs), des collègues qui devront approuver votre travail.

5.  **Revue de code et discussion** : C'est le cœur du processus. Vos collègues peuvent maintenant :
    -   Voir toutes les modifications que vous proposez.
    -   Laisser des commentaires sur des lignes de code spécifiques.
    -   Demander des changements.

6.  **Mettre à jour la PR** : Si des changements sont demandés, vous faites simplement de nouveaux commits sur votre branche locale (`feature/nouvelle-page-incroyable`) et vous les poussez à nouveau (`git push`). La Pull Request se mettra à jour automatiquement avec vos nouveaux commits.

7.  **Approbation et Fusion (Merge)** : Une fois que tout le monde est satisfait et que les tests automatiques (s'il y en a) passent au vert, la Pull Request est approuvée. Un mainteneur du projet peut alors cliquer sur le bouton "Merge Pull Request" directement dans GitHub.
    Votre branche est maintenant fusionnée dans `master` !

8.  **Nettoyage** : Une fois la PR fusionnée, vous pouvez (et devriez) supprimer votre branche de fonctionnalité, à la fois sur le distant (via un bouton dans GitHub) et en local.
    ```bash
    # Se remettre sur master et récupérer la version fusionnée
    git checkout master
    git pull origin master

    # Supprimer la branche locale
    git branch -d feature/nouvelle-page-incroyable
    ```

## Résolution de conflits

Parfois, pendant que vous travailliez sur votre branche, la branche `master` a évolué et les changements entrent en conflit avec les vôtres. Dans ce cas, Git ne peut pas fusionner automatiquement.

GitHub vous préviendra qu'il y a des conflits dans la PR. Pour les résoudre :

1.  Assurez-vous que votre branche `master` locale est à jour :
    `git checkout master`
    `git pull origin master`
2.  Retournez sur votre branche de fonctionnalité :
    `git checkout feature/nouvelle-page-incroyable`
3.  Essayez de fusionner `master` DANS votre branche :
    `git merge master`
4.  Git va vous indiquer les fichiers en conflit. Ouvrez-les dans votre éditeur. Vous verrez des marqueurs `<<<<<<<`, `=======`, `>>>>>>>`.
5.  **Modifiez le fichier** pour ne garder que la version finale souhaitée, en supprimant les marqueurs de Git.
6.  Une fois tous les conflits résolus, faites un nouveau commit :
    `git add .`
    `git commit -m "fix: résolution des conflits de fusion"`
7.  Poussez vos changements : `git push`. La PR sera mise à jour et les conflits devraient avoir disparu.

## Conclusion

Félicitations ! Vous avez maintenant toutes les clés en main pour utiliser Git et GitHub de manière efficace, de la création d'un projet solo à la collaboration sur un projet d'équipe. La pratique est la clé, alors n'hésitez pas à créer des projets personnels pour expérimenter.

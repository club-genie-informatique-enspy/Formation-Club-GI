# Exercice 3 : Le Conflit Inévitable

**Objectif :** Apprendre à identifier, comprendre et résoudre un conflit de fusion (merge conflict).

---

### Contexte

Les conflits de fusion se produisent lorsque deux branches ont modifié la même ligne d'un même fichier. Git ne sait pas quelle version choisir et vous demande d'intervenir. Nous allons en créer un volontairement pour nous entraîner.

### Étapes à réaliser

1.  **Repartez du projet `mon-projet-git`** à la fin de l'exercice 2. Assurez-vous d'être sur la branche `master`.

2.  **Créez une nouvelle branche** nommée `feature/titre-accrocheur`.
    <details>
      <summary>Commande</summary>
      <pre><code>git checkout -b feature/titre-accrocheur</code></pre>
    </details>

3.  Dans cette branche, **modifiez la toute première ligne** du fichier `biographie.txt` pour quelque chose comme : "Titre : La biographie d'un futur expert Git".

4.  **Ajoutez et commitez** cette modification sur la branche `feature/titre-accrocheur`.

5.  **Revenez sur la branche `master`**.
    <details>
      <summary>Commande</summary>
      <pre><code>git checkout master</code></pre>
    </details>

6.  Ici, **modifiez ÉGALEMENT la même première ligne** du fichier `biographie.txt`, mais avec un texte différent. Par exemple : "Introduction : Mon parcours avec Git".

7.  **Ajoutez et commitez** cette modification sur la branche `master`.

8.  Le moment de vérité. **Essayez de fusionner** la branche `feature/titre-accrocheur` dans `master`.
    <details>
      <summary>Commande</summary>
      <pre><code>git merge feature/titre-accrocheur</code></pre>
    </details>

9.  **Conflit !** Git devrait s'arrêter et vous afficher un message `CONFLICT (content): Merge conflict in biographie.txt`. Ouvrez le fichier `biographie.txt` dans votre éditeur.

10. **Analysez le fichier**. Vous verrez les marqueurs de conflit de Git :
    ```
    <<<<<<< HEAD
    Introduction : Mon parcours avec Git
    =======
    Titre : La biographie d'un futur expert Git
    >>>>>>> feature/titre-accrocheur
    ```

11. **Résolvez le conflit.** Modifiez le fichier pour ne garder que la version finale que vous souhaitez. Vous pouvez choisir une des deux versions, ou même écrire une toute nouvelle phrase. **Supprimez impérativement les marqueurs** `<<<<<<<`, `=======`, et `>>>>>>>`.

12. Une fois le fichier nettoyé et enregistré, **ajoutez-le à la Staging Area** pour marquer le conflit comme résolu.
    <details>
      <summary>Commande</summary>
      <pre><code>git add biographie.txt</code></pre>
    </details>

13. **Terminez la fusion** en créant le commit de fusion. Git vous proposera un message par défaut, que vous pouvez conserver.
    <details>
      <summary>Commande</summary>
      <pre><code>git commit</code></pre>
    </details>

---

**Excellent !** Vous avez survécu à votre premier conflit de fusion. C'est une compétence cruciale pour travailler en équipe.

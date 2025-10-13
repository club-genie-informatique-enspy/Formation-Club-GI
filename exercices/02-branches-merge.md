# Exercice 2 : La Vie en Branches

**Objectif :** Maîtriser le workflow de base avec les branches : créer, basculer, et fusionner.

---

### Contexte

Vous allez ajouter une nouvelle fonctionnalité à votre projet `mon-projet-git` de l'exercice précédent. Le travail se fera sur une branche dédiée pour ne pas impacter la branche principale (`master`).

### Étapes à réaliser

1.  **Repartez du projet `mon-projet-git`** de l'exercice 1. Assurez-vous d'être sur la branche `master`.

2.  **Créez une nouvelle branche** nommée `feature/competences`.
    <details>
      <summary>Commande</summary>
      <pre><code>git checkout -b feature/competences</code></pre>
    </details>

3.  **Créez un nouveau fichier** nommé `competences.txt`.

4.  **Ajoutez quelques compétences** dans ce fichier, une par ligne. Par exemple :
    -   HTML
    -   CSS
    -   JavaScript

5.  **Ajoutez et commitez** ce nouveau fichier sur votre branche `feature/competences`. Choisissez un message de commit clair.

6.  **Revenez sur la branche `master`**.
    <details>
      <summary>Commande</summary>
      <pre><code>git checkout master</code></pre>
    </details>

7.  Le fichier `competences.txt` a-t-il disparu ? (C'est normal !). **Modifiez le fichier `biographie.txt`** pour y ajouter une ligne, par exemple : "Mon objectif : devenir un expert Git."

8.  **Ajoutez et commitez** cette modification sur la branche `master`.

9.  Votre nouvelle fonctionnalité est prête. **Fusionnez (merge)** la branche `feature/competences` dans `master`.
    <details>
      <summary>Commande</summary>
      <pre><code>git merge feature/competences</code></pre>
    </details>

10. **Vérifiez l'état de votre projet**. Vous devriez maintenant voir à la fois le fichier `competences.txt` et la dernière version de `biographie.txt`.

11. **(Optionnel) Nettoyez votre dépôt** en supprimant la branche `feature/competences` qui n'est plus utile.
    <details>
      <summary>Commande</summary>
      <pre><code>git branch -d feature/competences</code></pre>
    </details>

---

**Félicitations !** Vous avez isolé le développement d'une fonctionnalité dans une branche et l'avez intégrée proprement au projet principal.

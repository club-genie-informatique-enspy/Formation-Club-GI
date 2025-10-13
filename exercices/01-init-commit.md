# Exercice 1 : Mon Premier Dépôt

**Objectif :** Se familiariser avec l'initialisation d'un dépôt, la création de commits et la consultation de l'historique.

---

### Étapes à réaliser

1.  **Créez un nouveau dossier** pour cet exercice. Nommez-le `mon-projet-git`.

2.  **Ouvrez un terminal** et naviguez à l'intérieur de ce nouveau dossier.

3.  **Initialisez un dépôt Git** ici.
    <details>
      <summary>Commande</summary>
      <pre><code>git init</code></pre>
    </details>

4.  **Créez un fichier** nommé `biographie.txt`.

5.  **Écrivez une ligne** dans ce fichier, par exemple : "Mon nom est [Votre Nom]".

6.  **Vérifiez l'état** de votre dépôt. Que vous dit Git à propos de ce nouveau fichier ?
    <details>
      <summary>Commande</summary>
      <pre><code>git status</code></pre>
    </details>

7.  **Ajoutez le fichier `biographie.txt`** à la zone de préparation (Staging Area).
    <details>
      <summary>Commande</summary>
      <pre><code>git add biographie.txt</code></pre>
    </details>

8.  **Vérifiez à nouveau l'état** du dépôt. Quelle est la différence ?

9.  **Créez votre premier commit.** Donnez-lui un message clair, par exemple : "Initial commit: ajout de la biographie".
    <details>
      <summary>Commande</summary>
      <pre><code>git commit -m "Initial commit: ajout de la biographie"</code></pre>
    </details>

10. **Modifiez le fichier `biographie.txt`** en ajoutant une nouvelle ligne, par exemple : "J'apprends à utiliser Git."

11. **Ajoutez et commitez** ces nouvelles modifications en une seule commande (ou en deux si vous préférez).

12. **Consultez l'historique** de votre projet pour voir vos deux commits.
    <details>
      <summary>Commande</summary>
      <pre><code>git log --oneline</code></pre>
    </details>

---

**Bravo !** Vous avez créé votre premier dépôt Git local et effectué plusieurs commits.

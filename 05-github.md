# Leçon 5 : Travailler avec des Dépôts Distants (GitHub)

Jusqu'à présent, tout notre travail a été local, sur notre propre machine. C'est utile, mais la vraie puissance de Git se révèle quand on collabore et qu'on partage son code. C'est le rôle des plateformes comme GitHub, GitLab ou Bitbucket.

Un dépôt distant (remote) est simplement une version de votre projet qui est hébergée sur un serveur, généralement sur Internet.

## Le workflow avec un dépôt distant

Le cycle de travail s'enrichit de quelques commandes pour synchroniser votre travail local avec le dépôt distant.

### 1. Créer un dépôt sur GitHub

Avant de pouvoir envoyer votre code, vous devez avoir un endroit où le mettre.

1.  Connectez-vous à votre compte GitHub.
2.  Cliquez sur le `+` en haut à droite et choisissez "New repository".
3.  Donnez-lui un nom (par exemple, `cours-git-demo`), une description, et choisissez s'il doit être public ou privé.
4.  **Important** : Ne cochez PAS la case "Initialize this repository with a README". Nous avons déjà un projet local, nous voulons un dépôt vide pour y pousser notre code.
5.  Cliquez sur "Create repository".

### 2. `git remote add`

Une fois le dépôt créé, GitHub vous donnera une URL (en HTTPS ou SSH). Cette URL est l'adresse de votre dépôt distant. Vous devez maintenant lier votre dépôt local à ce dépôt distant.

La commande `git remote add` crée cette connexion. On lui donne un nom (par convention, `origin`) et l'URL.

```bash
# Syntaxe : git remote add <nom-du-remote> <url-du-remote>
git remote add origin https://github.com/VOTRE_NOM_UTILISATEUR/cours-git-demo.git
```

### 3. `git push`

Maintenant que le lien est fait, vous pouvez "pousser" (push) votre travail local vers le dépôt distant. La commande `git push` envoie vos commits vers `origin`.

La première fois que vous pushez, vous devez spécifier la branche locale que vous voulez envoyer et comment elle doit s'appeler sur le distant.

```bash
# Syntaxe : git push -u <remote> <branche-locale>
git push -u origin master
```

-   `-u` (ou `--set-upstream`) crée un lien entre votre branche locale `master` et la branche `master` sur `origin`. Grâce à cela, les prochaines fois, vous n'aurez qu'à taper `git push`.

### 4. `git pull`

Si des changements ont été faits sur le dépôt distant (par un collègue, par exemple), vous devez les récupérer sur votre machine locale. C'est le rôle de `git pull`.

Cette commande va chercher les modifications sur le dépôt distant et les fusionner (merge) directement dans votre branche locale actuelle.

```bash
# Récupère les changements du distant et les fusionne
git pull origin master
```

### 5. `git clone`

Que faire si vous voulez commencer à travailler sur un projet qui existe déjà sur GitHub ? Vous n'allez pas commencer par `git init`. Vous allez le "cloner".

La commande `git clone` fait deux choses :
1.  Elle télécharge l'intégralité du projet et de son historique depuis un dépôt distant.
2.  Elle configure automatiquement le lien vers le remote `origin` pour vous.

```bash
# Clone un projet depuis GitHub
git clone https://github.com/quelquun/un-autre-projet.git
```

Ceci créera un dossier `un-autre-projet` sur votre machine, et vous serez prêt à travailler.

## Résumé des commandes

-   `git remote add origin <url>` : Lier un dépôt local à un dépôt distant.
-   `git push` : Envoyer vos commits vers le distant.
-   `git pull` : Récupérer les commits du distant et les fusionner.
-   `git clone <url>` : Télécharger un dépôt distant existant pour commencer à travailler dessus.

Dans la dernière leçon, nous aborderons la collaboration plus en détail avec les Pull Requests.
